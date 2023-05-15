---
title: BIMI(메시지 식별)를 위한 Gmail 브랜드 지표 구현
description: BIMI 구현 방법 알아보기
topics: Deliverability
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
source-git-commit: 7b8fbb09883b34b66c2729b6b5cfa1292ae1814e
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 0%

---

# 구현 [!DNL Brand Indicators for Message Identification] (비미)

[!DNL Brand Indicators for Message Identification] (BIMI)는 참여하는 플랫폼에서 보낸 사람의 이메일 옆에 승인된 로고를 표시할 수 있는 업계 표준입니다.

이 표준을 사용하면 브랜드가 사서함 공급자의 받은 편지함에 표시되어야 하는 로고를 결정할 수 있습니다. 소위 BIMI DNS(Domain Name System) 레코드에 게시되면 사서함 공급자가 이 로고를 선택하고 특정 기준이 충족되면 받은 편지함에 표시할 수 있습니다.

공급자는 구현마다 다르지만 그 이점은 분명합니다. 받은 편지함에 서서, 신뢰를 쌓고 보여지는 것을 통제한다.

BIMI는 게재 능력이나 명성을 직접적으로 향상시키지 않습니다. 이를 통해 수신자와 더 많은 신뢰를 얻을 수 있으므로 더 많은 참여를 유도할 수 있습니다.

## 어떻게 생겼나요?

다양한 공급자에서 구현의 몇 가지 예를 볼 수 있으며, 어떤 공급자가 [BIMI 그룹의 페이지](https://bimigroup.org/where-is-my-bimi-logo-displayed/){target="_blank"}.

## 비미 그룹은 누구인가요?

BIMI 그룹은 로고뿐만 아니라 기술, 법률 및 규정 준수 요구 사항도 포함하여 BIMI를 개발하는 작업 그룹입니다.

BIMI 그룹은 다음과 같은 업계 여러 분야의 이해 당사자들로 구성되어 있습니다. Google, Yahoo, Fastmail, Profpoint, Mailchimp, Sendgrid, Valimail 및 Validity입니다.

## 누가 BIMI를 지지합니까?

BIMI를 지원하는 사서함 공급자들의 목록이 꾸준히 증가하고 있다. 최신 목록을 찾을 수 있습니다 [여기](https://bimigroup.org/bimi-infographic/){target="_blank"} BIMI를 고려할 뿐만 아니라 지원 제공자에게도 해당됩니다.

2023년 4월 현재 이 목록에는 Gmail, Yahoo, La Poste, Fastmail, Onet.pl 및 Zone, Profpoint를 스팸 방지 기기로서의 Gmail 및 Apple Mail(iOS 16 이상에서)이 포함되어 있습니다.

그 목록에서 가장 유명한 이름들은 명백히 야후, Gmail 그리고 최근 입양인입니다. Apple과 iOS 16. Apple은 사서함 공급자가 아니므로 Mix에서 특수 역할을 맡지만, 네이티브 메일 앱에 BIMI 지원을 추가했습니다. BIMI를 준수하는 메일은 &quot;디지털 인증 이메일&quot;로 표시되어 브랜드 신뢰도를 높일 수 있습니다.

## 구현

BIMI를 구현하는 절차는 몇 가지 입니다.

1. 전송 도메인과 해당 조직 도메인 모두에 대한 집행 수준에서 DMARC(도메인 기반 메시지 인증, 보고 및 적합성) 구현 - [추가 정보](#dmarc)

1. SVG TilyPS 형식으로 브랜드 로고 만들기 - [추가 정보](#create-brand-logo)

1. 확인된 표시 인증서 등록(일부 공급자에만 필요) - [추가 정보](#vmc)

1. 로고 및 인증서로 BIMI DNS 레코드 게시 - [추가 정보](#publish-bimi-record)

1. 좋은 평판 - [추가 정보](#good-reputation)

>[!NOTE]
>
>모든 단계는 체크 오프해야 합니다.


### DMARC {#dmarc}

DMARC는 브랜드가 사서함 공급자가 실패하는 전자 메일로 수행할 작업을 결정할 수 있도록 하는 표준입니다 [인증](../additional-resources/authentication.md). 소위 정책이라는 범위는 &quot;격리&quot;(스팸 폴더 배치)보다 &quot;없음&quot;부터 &quot;거부&quot;(메일을 완전히 차단)입니다. BIMI는 다음 두 정책 중 유일하게 &#39;시행&#39;이며 이용 자격이 있다. SPF(Sender Policy Framework) 및 DKIM(Domain Keys Identified Mail)이 기본적으로 설정되어 있으므로 Adobe이 보낸 메일은 인증을 전달합니다. Adobe이 요청 시 전송 도메인에서 DMARC를 설정하고 있습니다.

전송 도메인에서 DMARC 외에도 조직 도메인의 적용 수준에도 DMARC를 사용해야 합니다(전송 도메인이 news.example.com이면 example.com이 조직 도메인임).

### 브랜드 로고 만들기 {#create-brand-logo}

로고 생성은 요구 사항을 100%까지 따라야 합니다. 항상 을(를) 참조하십시오. [BIMI 그룹의 지침](https://bimigroup.org/creating-bimi-svg-logo-files/){target="_blank"}.

기술 요구 사항 외에 정사각형 로고, 배경색과 같은 단색 및 기타 다양한 실용적인 권장 사항이 있습니다. 이러한 권장 사항은 최상의 시각화를 위한 것입니다.
규정 준수 사항으로 인해 로고가 표시되지 않을 수 있습니다.

### 확인 표시 인증서(VMC) {#vmc}

VMC(Verified Mark Certificate)는 Gmail 및 Apple과 같은 일부 사서함 공급자만 필요하며, 따라서 선택 사항입니다. BIMI를 실제로 활용하려면 VMC를 구입하는 것이 좋습니다.

확인된 표시 인증서는 브랜드가 로고를 사용할 수 있는 법적 유효성 확인입니다. 인증 기관은 브랜드 로고가 등록된 상표 사무소를 통해 이를 확인할 것입니다. 이 프로세스에는 몇 가지 법적 유효성 검사와 검사가 포함되며 시간이 걸릴 수 있습니다. 현재 두 개의 CA(인증 기관)에서 VMC를 발급하고 있습니다. Digicert와 Entrust. 첫 번째 상표권 사무소는 미국, 캐나다, EU, 영국, 독일, 일본, 호주 그리고 스페인이다.

경험상 로고당 VMC가 1개 필요합니다. 조직 도메인용 VMC가 있으면 하위 도메인이 포함되고, 기능이 추가되면 다른 도메인이 포함됩니다. 다른 로고가 있는 경우 두 개 이상의 VMC가 필요합니다. 함께 작업하도록 선택한 인증 기관 또는 파트너는 이 설정을 설정하는 데 도움이 됩니다.

>[!NOTE]
>
>VMC에는 연간 요금이 있습니다.

### BIMI 레코드 게시 {#publish-bimi-record}

다른 단계를 완료하면 BIMI DNS 레코드를 게시할 수 있습니다. 기록은 다음과 같습니다.

```
default._bimi.[domain] IN TXT "v=BIMI1; l=[SVG URL]; a=[PEM URL]
```

&quot;PEM URL&quot;은 확인된 표시 인증서의 파일 위치입니다.

전송 도메인의 경우 Adobe에서 이를 수행해야 합니다.

### 평판 {#good-reputation}

BIMI의 핵심은 신뢰입니다. 사용자는 사서함 공급자를 신뢰하여 적합한 보낸 사람의 로고만 표시하도록 하므로 사서함 공급자는 브랜드를 신뢰해야 하며 이는 보낸 사람의 평판에 의해 수행됩니다. 평판이 높으면 모두 좋지만 그렇지 않으면 로고가 표시되지 않습니다. 불행히도, 평판이 충분히 높은지 알아내기 위해 우리가 살펴볼 수 있는 정보나 지표는 없습니다.

VMC를 위한 노력과 비용을 거치해도 이 부분은 지워지지 않습니다. 사서함 공급자가 브랜드를 신뢰하지 않으면 로고가 표시되지 않습니다.

## 팁 및 요령

* BIMI Group은 BIMI를 위한 편리한 유효성 검사 도구를 제공합니다. 모든 것이 설정되어 있는지 다시 확인하고 싶거나 로고가 호환되는지 확인하려면 다음 위치로 이동하십시오. [이 링크](https://bimigroup.org/bimi-generator/){target="_blank"}. 후자의 경우 **[!UICONTROL Generate BIMI]** 자리 표시자 도메인을 입력하고 올바른 로고 URL을 입력합니다. 검사관이 로고의 준수 여부를 알려준다.

* VMC 없이 안전하게 시작할 수 있으며, BIMI 레코드에 VMC URL이 포함되지 않은 경우 평판에 아무런 영향을 주지 않지만, 해당 로고는 이미 Yahoo에 표시될 수 있습니다.

* 조직 차원에서 DMARC를 구현하는 것은 큰 일입니다. 일부 회사들은 브랜드들이 완전 DMARC 채택을 할 수 있도록 지원하기 위해 전문화되어 있다.

* FAQ 목록이 게시되었습니다 [여기](https://bimigroup.org/faqs-for-senders-esps/){target="_blank"}.
