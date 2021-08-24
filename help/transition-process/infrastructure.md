---
title: 인프라
description: '이메일 인프라를 올바르게 구성하는 데 필요한 사항을 알아봅니다. '
topics: Deliverability
kt: 7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 4025d95c-cc77-4e0c-9904-aaf60019b18c
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 2%

---

# 인프라

게재의 성공 여부는 강력한 기반에 따라 다릅니다. 이메일 인프라는 핵심 요소입니다. 올바르게 구성된 이메일 인프라에는 도메인 및 IP 주소 등 여러 구성 요소가 포함됩니다. 이러한 구성 요소는 사용자가 보내는 이메일의 배후에 있는 기계와 비슷하며 때로는 평판 발송의 매개체가 됩니다. 게재 가능성 컨설턴트는 구현 중에 이러한 요소가 제대로 설정되도록 하지만 평판 요소 때문에 이러한 기본적인 이해를 하는 것이 중요합니다.

## 도메인 설정 및 전략 {#domain-setup-and-strategy}

시간이 변경되었으며, 일부 ISP(Gmail 및 Yahoo 등)는 이제 보낸 사람에게 전자 메일 신뢰도를 첨부하는 측면에서 도메인 평판을 추가 포인트로 통합합니다. 도메인 평판은 IP 주소 대신 전송 도메인을 기반으로 합니다. 이는 ISP 필터링 결정 시 브랜드가 우선함을 의미합니다.

Adobe 플랫폼에서 새 보낸 사람을 위한 온보딩 프로세스의 일부에는 전송 도메인을 설정하고 인프라가 제대로 설정되도록 하는 것이 포함됩니다. 장기적으로 사용할 도메인 관련 전문가와 협력해야 합니다. 다음은 좋은 도메인 전략을 만드는 몇 가지 팁입니다.

* 사용자가 메일을 스팸으로 잘못 식별하지 않도록 선택한 도메인으로 브랜드를 최대한 명확하고 반영하십시오. 예를 들면 newsletter.foo.com, receivts.foo.com 등이 있습니다.
* 조직의 메일 배달에 영향을 줄 수 있으므로 상위 또는 회사 도메인을 사용하면 안 됩니다.
* 전송 도메인을 정당화하려면 상위 도메인의 하위 도메인을 사용하는 것이 좋습니다.
* 트랜잭션 및 마케팅 메시지 카테고리의 하위 도메인을 구분합니다. 이 방법은 ISP가 이 전송 방법을 찾는 만큼 신뢰할 수 있는 이메일 트래픽 흐름을 도울 수 있습니다. 이 전송 방법은 알려진 이메일 우수 사례이며, 적극 권장합니다.

## IP 전략 {#ip-strategy}

IP 전략을 잘 짜서 긍정적인 평판을 얻는 것이 중요합니다. IP 및 설정 수는 비즈니스 모델 및 마케팅 목표에 따라 다릅니다. 전문가와 함께 올바른 출발을 위한 명확한 전략을 개발하세요. 주목할 중요한 다음 사항을 고려하십시오.

* **너무 많은** IPscan은  **스노우슈에 스팸을 보내는 사람이 흔히 쓰는 전술이므로 평판 문제를 야기합니다. 이 전략은 스팸 메일의 전달을 최대화하기 위해 많은 IP에 트래픽이 분산되는 스파머가 사용하는 전략입니다**. 사용자가 분기가 아니더라도 너무 많은 IP를 사용하는 경우, 특히 해당 IP에 이전 트래픽이 없는 경우 그럴 수 있습니다.
* **너무 적은** IPscan으로 인해 처리량 문제가 발생하고 잠재적으로 평판 문제가 발생할 수 있습니다. 처리량은 ISP별로 다릅니다. ISP가 수락하는 시간과 속도는 일반적으로 해당 인프라를 기반으로 하며 평판 기준을 보냅니다.
* 메시징 유형에 대한 트래픽 분리가 키입니다. 따라서 별도의 IP 풀에서 최소한의 마케팅 및 트랜잭션 메일을 별도의 IP 풀로 배치하는 것이 중요합니다.
* 메일 전략에 따라 평판이 완전히 다른 경우 다른 IP 풀에서 다른 제품이나 마케팅 스트림을 구분하는 것이 좋습니다. 일부 마케터는 지역별 세그먼트도 제공합니다. 평판이 낮은 트래픽에 대해 IP를 분리하면 평판 문제가 해결되지 않지만, &quot;평판&quot;으로 간주되는 이메일 게재에 문제가 발생하지 않습니다. 결국, 여러분은 더 위험한 대상을 위해 여러분의 좋은 청중을 희생하고 싶지 않을 거예요.

## 피드백 루프 {#feedback-loops}

뒤에서 Adobe 플랫폼은 바운스, 불만, 구독 취소 등과 관련된 데이터를 처리하고 있습니다. 이러한 피드백 루프의 설정은 게재 능력에 중요한 측면입니다. 불만 사항은 평판에 영향을 줄 수 있으므로, 타겟 대상의 불만 사항을 등록하는 이메일 주소를 사용해야 합니다. Gmail이 이 데이터를 다시 제공하지 않는다는 점에 유의해야 합니다. 목록 가입 해지 헤더 및 참여 필터링은 현재 대부분의 가입자 데이터베이스를 구성하는 Gmail 가입자에게 특히 중요합니다.

## 인증 {#authentication}

인증은 ISP가 보낸 사람의 ID를 확인하는 데 사용하는 프로세스입니다. 가장 일반적인 두 인증 프로토콜은 [!DNL Sender Policy Framework] (SPF) 및 [!DNL DomainKeys Identified Mail] (DKIM)입니다. 최종 사용자에게는 표시되지 않지만 ISP가 확인된 보낸 사람의 이메일을 필터링하는 데 도움이 됩니다. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC)는 해당 정책이 아직 모든 ISP가 자체 평판 시스템에 통합하지는 않았지만, 인기를 얻고 있습니다.

### SPF

[!DNL Sender Policy Framework] (SPF)는 도메인 소유자가 해당 도메인에서 메일을 보내는 데 사용하는 메일 서버를 지정할 수 있도록 하는 인증 방법입니다.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM)은 위조된 발신자 주소(일반적으로 스푸핑이라고 함)를 감지하는 데 사용되는 인증 방법입니다. DKIM이 활성화되어 있으면 수신자가 해당 도메인에서 메일을 보낼 수 있는 권한이 있는지 확인할 수 있습니다.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC)는 도메인 소유자가 권한 없는 사용으로부터 도메인을 보호할 수 있도록 해주는 인증 방법입니다. DMARC는 SPF 또는 DKIM 또는 둘 다 사용하여 도메인 소유자가 인증에 실패한 메일에 대해 발생하는 내용을 제어할 수 있도록 합니다. 전달, 격리 또는 거부됨.

## 제품별 리소스

**Campaign**

* [이 섹션에서 하위 도메인을 Adobe Campaign Classic 또는 Standard에 완전히 위임하는 방법을 알아봅니다.](/help/additional-resources/ac-domain-name-setup.md)
* [Campaign 컨트롤 패널: 전체 하위 도메인 위임(자습서)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html)  -  *하위 도메인을 Adobe Campaign Classic에 완전히 위임하는 방법을 알아봅니다.*
* [Campaign 컨트롤 패널: 전체 하위 도메인 위임(자습서)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html)  -  *하위 도메인을 Adobe Campaign Standard에 완전히 위임하는 방법을 알아봅니다.*
* [이 섹션](/help/additional-resources/acc-technical-recommendations.md#feedback-loop-acc)에서 Campaign Classic 인스턴스에 대한 피드백 루프 구현에 대해 자세히 알아보십시오.

## 추가 리소스

* [이 섹션](/help/additional-resources/authentication.md)에서 SPF, DKIM 및 DMARC 인증 방법에 대해 자세히 알아보십시오.
* [이 섹션](/help/additional-resources/increase-reputation-with-ip-warming.md)에서 IP 온난화를 통해 전자 메일 신뢰도를 높이는 방법에 대해 자세히 알아보십시오.
