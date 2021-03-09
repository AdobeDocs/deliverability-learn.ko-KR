---
title: 인프라
description: '이메일 인프라를 적절하게 구축하는 데 필요한 사항을 알아봅니다. '
feature: 전환 프로세스
topics: Deliverability
kt: 7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: d42a8c3b06308fca0cf3e9db8d634a767fc0cdc6
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 0%

---


# 인프라

성공적으로 배달할 수 있으려면 강력한 기반이 필요합니다. 이메일 인프라가 핵심 요소입니다. 적절히 구성된 이메일 인프라에는 도메인 및 IP 주소 등 여러 구성 요소가 포함됩니다. 이러한 구성 요소는 사용자가 보내는 이메일의 뒤에 있는 기계와 비슷하며, 종종 명성을 보내는 것의 기준이 됩니다. 제공 컨설턴트는 구현 중에 이러한 요소가 올바르게 설정되도록 보장하지만, 평판 요소 때문에 이러한 기본적인 이해를 가지는 것이 중요합니다.

## 도메인 설정 및 전략

시간이 변경되었으며, 일부 ISP(예: Gmail 및 Yahoo)는 이제 발신자에게 이메일 명성을 첨부하는 것에 대해 도메인 명성을 추가한다. 도메인 명성은 IP 주소 대신 전송 도메인을 기반으로 합니다. 이는 ISP 필터링 결정에 있어서 브랜드가 우선함을 의미합니다.

Adobe 플랫폼에서 새 보낸 사람을 위한 온보딩 프로세스의 일부에는 전송 도메인 설정과 인프라가 제대로 설정되었는지 확인하는 것이 포함됩니다. 장기적으로 사용하려는 도메인에 대해 전문가와 함께 작업해야 합니다. 다음은 좋은 도메인 전략을 만드는 몇 가지 팁입니다.

* 사용자가 메일을 스팸으로 잘못 식별하지 않도록 선택한 도메인에 대해 최대한 브랜드를 명확히 반사해야 합니다. 일부 예로는 newsletter.foo.com, incluts.foo.com 등이 있습니다.
* 조직의 메일 전달에 영향을 줄 수 있으므로 부모 또는 회사 도메인을 사용하면 안 됩니다.
* 전송 도메인을 합법화하기 위해 부모 도메인의 하위 도메인을 사용하는 것이 좋습니다.
* 거래 및 마케팅 메시지 카테고리에 대한 하위 도메인을 구분합니다. 이 방법은 ISP가 이 전송 방법을 찾는 것으로, 잘 알려진 이메일 모범 사례이며 권장하는 이메일 트래픽이 보다 안정적임을 입증하는 데 도움이 됩니다.

## IP 전략

긍정적인 명성을 확립하는 데 도움이 되도록 잘 짜여진 IP 전략을 세우는 것이 중요합니다. IP 및 설정 수는 비즈니스 모델 및 마케팅 목표에 따라 다릅니다. 전문가와 협력하여 적합한 전략을 수립합니다. 다음 사항을 고려해야 합니다.

* **너무 많은** IPscan은 스팸메일 발송을 최대화하기 위해 많은 IP에 트래픽이  **분산되어 있는 스파머가 사용하는 일반적인**&#x200B;스노슈트전술이므로 명성에 문제가 생깁니다. 스팸 사용자가 아니더라도 너무 많은 IP를 사용하는 경우처럼 보일 수 있습니다. 특히 해당 IP에 이전 트래픽이 없는 경우입니다.
* **처리** 문제로 인한 IPscan이 너무 적어서 잠재적인 평판 문제를 유발합니다. 처리량은 ISP에 따라 다릅니다. ISP가 기꺼이 받아들이고자 하는 양과 속도는 일반적으로 해당 인프라를 기반으로, 평판 기준을 보내는 것입니다.
* 메시징 유형에 대한 트래픽 분리가 중요합니다. 별도의 IP 풀에 마케팅 및 트랜잭션 메일을 최소 단위로 구분하는 것이 중요합니다.
* 메일 전략에 따라 명성과 크게 다른 경우 다른 제품 또는 마케팅 스트림을 다른 IP 풀에 따로 두는 것이 좋습니다. 일부 마케터는 지역별로 세그먼트화할 수도 있습니다. 낮은 평판이 있는 트래픽의 IP를 구분하면 평판 문제가 해결되지 않지만, &quot;정상적인&quot; 평판 이메일 전달과 관련된 문제가 발생하지 않습니다. 결국, 여러분은 더 위험 부담이 큰 사람들을 위해 좋은 청중을 희생하고 싶지 않습니다.

## 피드백 루프

백그라운드에서 Adobe 플랫폼은 바운스, 불만, 구독 취소 등과 관련된 데이터를 처리하고 있습니다. 이러한 피드백 루프의 설정은 전달하기에 중요한 측면입니다. 불만 사항은 명성을 손상시킬 수 있으므로 타겟 고객으로부터 불만 사항을 등록하는 이메일 주소를 입력해야 합니다. Gmail이 이 데이터를 다시 제공하지 않는다는 점에 주목해야 합니다. 목록 구독 취소 헤더 및 참여 필터링은 가입자 데이터베이스의 대부분을 구성하는 Gmail 가입자에게 특히 중요합니다.

## 인증

인증은 ISP가 보낸 사람의 ID를 확인하는 데 사용하는 프로세스입니다. 가장 일반적인 두 개의 인증 프로토콜은 [!DNL Sender Policy Framework](SPF) 및 [!DNL DomainKeys Identified Mail](DKIM)입니다. 이러한 항목은 최종 사용자가 볼 수 없지만 ISP가 확인된 보낸 사람의 이메일을 필터링하는 데 도움이 됩니다. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC)는 모든 ISP가 자사의 평판 시스템에 아직 통합하지 않았지만, 이러한 정책은 인기를 얻고 있다.

### SPF

[!DNL Sender Policy Framework] (SPF)는 도메인 소유자가 해당 도메인에서 메일을 보내는 데 사용하는 메일 서버를 지정할 수 있는 인증 방법입니다.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM)은 위조 발신자 주소(일반적으로 스푸핑)를 감지하는 데 사용되는 인증 방법입니다. DKIM이 활성화되어 있으면 수신자는 보낸 사람이 해당 도메인에서 메일을 보낼 수 있는지 확인할 수 있습니다.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC)는 도메인 소유자가 권한 없는 사용으로부터 도메인을 보호할 수 있는 인증 방법입니다. DMARC는 SPF 또는 DKIM 또는 둘 다를 사용하여 도메인 소유자가 인증에 실패한 메일에 발생하는 상황을 제어할 수 있도록 합니다.전달, 격리 또는 거부됨

## 제품별 리소스

**Campaign Standard**

* [Campaign 컨트롤 패널:전체 하위 도메인 위임(자습서)](https://experienceleague.corp.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html): *하위 도메인을 Adobe Campaign Standard에 완전히 위임하는 방법을 알아봅니다.*

**Campaign Classic**

* [Campaign 컨트롤 패널:전체 하위 도메인 위임(자습서)](https://experienceleague.corp.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html): *하위 도메인을 Adobe Campaign Classic에 완전히 위임하는 방법을 알아봅니다.*
