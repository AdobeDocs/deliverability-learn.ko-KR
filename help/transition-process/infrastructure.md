---
title: 인프라
description: 이메일 인프라를 올바르게 구성하는 데 필요한 사항을 알아봅니다.
topics: Deliverability
jira: KT-7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
role: Admin, Leader
level: Beginner
team: ACS
exl-id: 4025d95c-cc77-4e0c-9904-aaf60019b18c
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 2%

---

# 인프라

전달성의 성공은 튼튼한 기반에 달려 있습니다. 이메일 인프라는 핵심 요소입니다. 올바르게 구성된 이메일 인프라에는 여러 구성 요소, 즉 도메인과 IP 주소가 포함됩니다. 이러한 구성 요소는 보내는 이메일 뒤의 장비와 유사하며 종종 평판 보내기의 앵커입니다. 게재 가능성 컨설턴트는 구현 중에 이러한 요소가 제대로 설정되었는지 확인하지만, 평판 요소 때문에 이러한 기본 사항을 이해하는 것이 중요합니다.

## 도메인 설정 및 전략 {#domain-setup-and-strategy}

시대가 변경되었으며 일부 ISP(예: Gmail 및 Yahoo)는 이제 보낸 사람에게 전자 메일 신뢰도를 첨부할 때 추가 지점으로 도메인 신뢰도를 통합합니다. 도메인 명성은 IP 주소 대신 보내는 도메인을 기반으로 합니다. 즉, ISP 필터링 결정과 관련하여 브랜드가 우선합니다.

Adobe 플랫폼에서 새 보낸 사람을 위한 온보딩 프로세스의 일부에는 전송 도메인을 설정하고 인프라가 제대로 설정되었는지 확인하는 작업이 포함됩니다. 장기적으로 사용할 도메인에 대해 전문가와 협력해야 합니다. 다음은 좋은 도메인 전략을 형성하는 몇 가지 팁입니다.

* 사용자가 메일을 스팸으로 잘못 식별하지 않도록 선택한 도메인을 사용하여 브랜드를 최대한 명확하게 반영하십시오. newsletter.foo.com, receipts.foo.com 등의 예제가 있습니다.
* 상위 또는 회사 도메인은 조직에서 ISP로의 메일 게재에 영향을 줄 수 있으므로 사용하면 안 됩니다.
* 상위 도메인의 하위 도메인을 사용하여 전송 도메인을 합법화하는 것이 좋습니다.
* 트랜잭션 메시지 범주와 마케팅 메시지 범주를 위해 하위 도메인을 구분합니다. 이렇게 하면 ISP가 알려진 이메일 모범 사례이며 권장 사항인 이 전송 방법을 찾기 때문에 이메일 트래픽 흐름을 보다 안정적으로 유지하는 데 도움이 됩니다.

## IP 전략 {#ip-strategy}

긍정적인 평판을 구축하는 데 도움이 되도록 잘 구조화된 IP 전략을 구성하는 것이 중요하다. IP 및 설정 수는 비즈니스 모델 및 마케팅 목표에 따라 달라집니다. 전문가와 협력하여 올바른 시작을 위한 명확한 전략을 개발하십시오. 다음 사항에 주의하십시오.

* **너무 많은 IP**&#x200B;은(는) 스팸 메일 배달을 최대화하기 위해 트래픽이 여러 IP로 확산되는 스팸 발송자가 사용하는 일반적인 **snowshoe** 스팸의 전술이므로 신뢰도 문제를 일으킬 수 있습니다. 스패머가 아니더라도 IP를 너무 많이 사용하는 경우, 특히 해당 IP에 이전 트래픽이 없는 경우 스패머가 될 수 있습니다.
* **IP가 너무 적음**&#x200B;으로 인해 처리량 문제가 발생하고 평판 문제가 발생할 수 있습니다. 처리량은 ISP마다 다릅니다. ISP가 수락할 의향과 속도는 일반적으로 인프라 및 전송 신뢰도 임계값을 기반으로 합니다.
* 메시징 유형에 대한 트래픽 분리가 중요합니다. 최소한 마케팅 및 트랜잭션 메일을 별도의 IP 풀로 분리하는 것이 중요합니다.
* 메일 전략에 따라 고객의 평판이 크게 다른 경우 다른 IP 풀에서 다른 제품 또는 마케팅 스트림을 구분하는 것이 좋습니다. 일부 마케터는 지역별로 세그먼트화하기도 합니다. 평판이 낮은 트래픽에 대해 IP를 분리하면 평판 문제는 수정되지 않지만 &quot;양호한&quot; 평판 이메일 게재 문제를 방지할 수 있습니다. 결국, 더 위험한 것을 위해 좋은 청중을 희생하고 싶지 않을 것이다.

## 피드백 루프 {#feedback-loops}

그 이면에는 바운스, 컴플레인, 구독 취소 등에 관한 데이터를 처리하는 Adobe 플랫폼이 있습니다. 이러한 피드백 루프 설정은 전달성에 중요한 측면이다. 컴플레인은 평판을 손상시킬 수 있으므로 타겟 대상의 컴플레인을 등록하는 이메일 주소를 사용해야 합니다. Gmail은 이 데이터를 다시 제공하지 않습니다. 목록 구독 취소 헤더와 참여 필터링은 현재 대부분의 구독자 데이터베이스를 구성하는 Gmail 구독자에게 특히 중요합니다.

## 인증 {#authentication}

인증은 ISP가 보낸 사람의 ID를 확인하기 위해 사용하는 프로세스입니다. 가장 일반적인 두 인증 프로토콜은 [!DNL Sender Policy Framework] (SPF)과 [!DNL DomainKeys Identified Mail] (DKIM)입니다. 최종 사용자는 볼 수 없지만 ISP가 확인된 발신자의 이메일을 필터링할 수 있도록 지원합니다. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC)이(가) 평판 시스템의 모든 ISP에 의해 아직 통합되지 않았지만 인기를 얻고 있습니다.

### SPF

[!DNL Sender Policy Framework] (SPF)은 도메인 소유자가 해당 도메인에서 메일을 보내는 데 사용하는 메일 서버를 지정할 수 있는 인증 방법입니다.

### D김

[!DNL Domain Keys Identified Mail] (DKIM)은 위조된 보낸 사람 주소(일반적으로 스푸핑이라고 함)를 검색하는 데 사용되는 인증 방법입니다. DKIM이 활성화되면 수신자는 보낸 사람이 해당 도메인에서 메일을 보낼 수 있는 권한이 있는지 확인할 수 있습니다.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC)는 도메인 소유자가 도메인을 무단 사용으로부터 보호할 수 있는 인증 방법입니다. DMARC는 도메인 소유자가 게재됨, 격리됨 또는 거부됨 등 인증에 실패한 메일에 대한 상황을 제어할 수 있도록 SPF나 DKIM 또는 두 가지 모두를 사용합니다.

## 제품별 리소스

**Campaign**

* [이 섹션](/help/additional-resources/ac-domain-name-setup.md)에서 하위 도메인을 Adobe Campaign Classic 또는 Standard에 완전히 위임하는 방법을 알아보세요.
* [Campaign 컨트롤 패널: 전체 하위 도메인 위임(튜토리얼)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *하위 도메인을 Adobe Campaign Classic에 완전히 위임하는 방법을 알아봅니다.*
* [Campaign 컨트롤 패널: 전체 하위 도메인 위임(튜토리얼)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *하위 도메인을 Adobe Campaign Standard에 완전히 위임하는 방법을 알아봅니다.*
* [이 섹션](/help/additional-resources/acc-technical-recommendations.md#feedback-loop-acc)에서 Campaign Classic 인스턴스에 대한 피드백 루프를 구현하는 방법에 대해 자세히 알아보세요.

## 추가 리소스

* [이 섹션](/help/additional-resources/authentication.md)에서 SPF, DKIM 및 DMARC 인증 방법에 대해 자세히 알아보세요.
* [이 섹션](/help/additional-resources/increase-reputation-with-ip-warming.md)에서 IP warming으로 전자 메일 평판을 높이는 방법에 대해 자세히 알아보세요.
