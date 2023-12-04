---
title: 메시지 식별을 위한 Gmail의 브랜드 지표 구현(BIMI)
description: BIMI 구현 방법 알아보기
topics: Deliverability
role: Admin
level: Beginner
jira: KT-14079
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
source-git-commit: b96539608acd51ce76ef5bdaf5afd07b5a4208b7
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 0%

---

# 구현 [!DNL Brand Indicators for Message Identification] (BIMI)

[!DNL Brand Indicators for Message Identification] (BIMI)는 참여 플랫폼에서 발신자의 이메일 옆에 승인된 로고가 나타날 수 있는 업계 표준입니다.

이 표준을 사용하면 브랜드는 사서함 공급자의 받은 편지함에 표시해야 하는 로고를 결정할 수 있습니다. BIMI DNS(Domain Name System) 레코드에 게시되면 사서함 공급자는 특정 기준을 충족할 경우 이 로고를 선택하여 받은 편지함에 표시할 수 있습니다.

공급업체마다 다른 구현을 수행하지만, 받은 편지함에 서서 신뢰를 구축하고 표시되는 내용을 제어할 수 있다는 이점이 명확합니다.

BIMI는 전달성이나 평판을 직접적으로 향상시키지 않습니다. 이렇게 하면 수신자와 더 많은 신뢰를 구축하여 더 많은 참여를 이끌어 낼 수 있습니다.

## 어때 보여?

다른 공급자의 몇 가지 구현 예와 어떤 공급자에서에 로고를 표시하는지에 대한 자세한 내용을 확인할 수 있습니다. [BIMI 그룹의 페이지](https://bimigroup.org/where-is-my-bimi-logo-displayed/){target="_blank"}.

## BIMI Group이 누구죠?

BIMI 그룹은 로고뿐만 아니라 기술적, 법적 및 규정 준수 요구 사항까지 포괄하기 때문에 BIMI를 개발하는 실무 그룹입니다.

BIMI Group은 Google, Yahoo, Fastmail, Proofpoint, Mailchimp, Sendgrid, Valimail, Validity 등 업계의 다양한 영역에서 온 여러 이해 관계자로 구성됩니다.

## BIMI를 지원하는 사람은 누구입니까?

BIMI를 지원하는 메일박스 공급자들의 명단은 꾸준히 증가하고 있다. 최신 목록을 찾을 수 있습니다. [여기](https://bimigroup.org/bimi-infographic/){target="_blank"} 지원 제공자는 물론 BIMI를 고려 중인 제공자의 경우.

2023년 4월 현재, 이 목록에는 Gmail, Yahoo, La Poste, Fastmail, Onet.pl 및 Zone, 스팸 방지 어플라이언스로서의 Proofpoint 및 Apple Mail(iOS 16 이상)이 포함되어 있습니다.

그 목록에서 가장 두드러진 이름은 명백히 야후, Gmail 그리고 한 최근 입양자입니다: Apple with iOS 16. Apple은 사서함 공급자가 아니므로 혼합에 특별한 역할을 하지만 기본 메일 앱에 BIMI 지원을 추가했습니다. BIMI를 준수하는 메일은 브랜드에 대한 신뢰를 높이는 &quot;디지털 인증 이메일&quot;로 표시됩니다.

## 구현

BIMI 구현은 몇 가지 단계로 이루어집니다.

1. 전송 도메인 및 해당 조직 도메인 모두에 대한 적용 수준에 대한 DMARC(도메인 기반 메시지 인증, 보고 및 적합성) 구현 - [자세히 알아보기](#dmarc)

1. SVG TinyPS 형식으로 브랜드 로고 만들기 - [자세히 알아보기](#create-brand-logo)

1. 확인된 표시 인증서에 등록(일부 공급자만 필요) - [자세히 알아보기](#vmc)

1. 로고 및 인증서가 포함된 BIMI DNS 레코드 게시 - [자세히 알아보기](#publish-bimi-record)

1. 평판이 좋음 - [자세히 알아보기](#good-reputation)

>[!NOTE]
>
>모든 단계는 선택 취소해야 합니다.


### DMARC {#dmarc}

DMARC는 실패하는 전자 메일에 대해 사서함 공급자가 수행해야 하는 작업을 브랜드가 결정할 수 있는 표준입니다 [인증](../additional-resources/authentication.md). 소위 정책은 &quot;없음&quot;에서 &quot;격리&quot;(스팸 폴더 배치)부터 &quot;거부&quot;(이메일 전면 차단)까지 다양합니다. 후자의 두 정책만 &quot;시행&quot;이라고 하며 BIMI에 대한 자격이 있습니다. SPF(Sender Policy Framework) 및 DKIM(Domain Keys Identified Mail)이 기본적으로 설정되어 있으므로 Adobe에서 보낸 메일이 인증을 통과하고 있습니다. Adobe이 요청 시 전송 도메인에서 DMARC를 설정하고 있습니다.

전송 도메인의 DMARC 외에도 조직 도메인의 적용 수준에도 DMARC를 사용해야 합니다(전송 도메인이 news.example.com인 경우 example.com이 조직 도메인).

### 브랜드 로고 생성 {#create-brand-logo}

로고 생성은 100%에 대한 요구 사항을 준수해야 합니다. 항상 을(를) 참조하십시오 [BIMI Group의 지침](https://bimigroup.org/creating-bimi-svg-logo-files/){target="_blank"}.

CDN(콘텐츠 전달 네트워크)이 사용되는 경우 사서함 공급자가 로고를 받지 못하게 하는 보호(예: 보트 보호)가 사용되지 않도록 하려면 로고를 보안 위치(HTTPS)에 저장해야 합니다.

기술적 요구 사항 외에도 사각형 로고, 배경색으로 단색 및 기타 같은 실용적인 권장 사항이 있습니다. 이러한 권장 사항은 최상의 시각화를 위한 것입니다. 일부 공급자는 BIMI 작업 그룹에 의한 요구 사항에 추가 자체 요구 사항을 가지고 있습니다. [Gmail](https://support.google.com/a/answer/10911027?sjid=903725605955621707-EU){target="_blank"} 예를 들어 로고는 96 x 96픽셀 이상이어야 합니다.
준수하지 않으면 로고가 표시되지 않을 수 있습니다.

### 확인된 마크 인증서(VMC) {#vmc}

VMC(Verified Mark Certificate)는 Gmail 및 Apple과 같은 일부 사서함 공급자에만 필요하므로 선택 사항입니다. BIMI를 활용하려면 VMC를 사용하는 것이 좋습니다.

확인된 마크 인증서는 브랜드가 로고를 사용할 수 있다는 법적 확인입니다. 인증 기관은 브랜드 로고가 등록된 상표관리소를 통해 이를 확인할 예정이다. 이 프로세스에는 몇 가지 법적 검증과 확인이 포함되며 시간이 걸릴 수 있습니다. 현재 두 개의 CA(인증 기관)가 VMC를 발행하고 있습니다(Digicert 및 Entrust). 첫 번째 상표 사무소 세트는 미국, 캐나다, EU, 영국, 독일, 일본, 호주, 스페인이다.

일반적으로 로고당 하나의 VMC가 필요합니다. 조직 도메인에 대한 VMC가 있으면 하위 도메인이 포함되며 기능이 추가되면 다른 도메인도 포함됩니다. 로고가 다른 경우 두 개 이상의 VMC가 필요합니다. 함께 작업하도록 선택한 인증 기관 또는 파트너가 이 설정을 지원합니다.

>[!NOTE]
>
>VMC는 연간 수수료가 있습니다.

### BIMI 레코드 게시 {#publish-bimi-record}

다른 단계가 완료되면 BIMI DNS 레코드를 게시할 수 있습니다. 레코드는 다음과 같습니다.

```
default._bimi.[domain] IN TXT "v=BIMI1; l=[SVG URL]; a=[PEM URL]
```

&quot;PEM URL&quot;은 확인된 표시 인증서의 파일 위치입니다.

전송 도메인의 경우 Adobe으로 수행해야 합니다.

### 좋은 평판 {#good-reputation}

BIMI의 핵심은 신뢰입니다. 사용자는 사서함 공급자를 신뢰하여 합법적인 보낸 사람에 대한 로고만 표시하므로 사서함 공급자는 브랜드를 신뢰해야 하며, 이는 보낸 사람의 신뢰도에 의해 수행됩니다. 평판이 좋으면 다 좋은데, 그렇지 않으면 로고가 안 나온다. 안타깝게도, 평판이 충분히 높은지 파악하기 위해 우리가 살펴볼 수 있는 정보나 지표가 없다.

VMC를 위한 노력과 비용을 거쳐도 이 부분은 사라지지 않습니다. 사서함 공급자가 브랜드를 신뢰하지 않는 경우 로고가 표시되지 않습니다.

## 팁과 트릭

* BIMI Group은 BIMI를 위한 편리한 검증 도구를 제공합니다. 모든 것이 설정되고 준비되었는지 다시 확인하려는 경우 또는 로고가 호환되는지 확인하려는 경우 [이 링크](https://bimigroup.org/bimi-generator/){target="_blank"}. 후자의 경우 **[!UICONTROL Generate BIMI]** 올바른 로고 URL이 아닌 자리 표시자 도메인을 입력합니다. 검사자가 로고가 규정을 준수하는지 여부를 알려줍니다.

* VMC 없이 안전하게 시작할 수 있으며, BIMI 레코드에 VMC URL이 포함되어 있지 않은 경우 평판에 해가 없지만 Yahoo에 로고가 이미 표시될 수 있습니다.

* 조직 수준에서 DMARC를 구현하는 것은 큰 작업입니다. 일부 회사는 브랜드가 완전한 DMARC 채택을 달성하는 데 도움이 되도록 전문화되어 있습니다.

* 광범위한 FAQ 목록이 게시됩니다 [여기](https://bimigroup.org/faqs-for-senders-esps/){target="_blank"}.
