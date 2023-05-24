---
title: 볼륨 - 원활하게 전환하는 방법에 대한 팁
description: 보내는 메일의 양은 긍정적인 평판을 구축하는 데 매우 중요합니다. 원활하게 전환하기 위해 수행할 수 있는 작업에 대해 알아봅니다.
topics: Deliverability
kt: 7055
thumbnail: kt7055.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 1bc56061-0c64-4033-b49c-66618916bca6
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 1%

---

# 볼륨

보내는 메일의 양은 긍정적인 평판을 구축하는 데 매우 중요합니다. ISP의 입장에서 생각해 보십시오. 여러분이 모르는 사람으로부터 엄청난 양의 트래픽을 보기 시작한다면, 그것은 놀라운 일일 것입니다. 대량의 메일을 즉시 보내는 것은 위험하며 종종 해결하기가 어려운 신뢰도 문제를 일으킬 수 있습니다. 너무 빨리 보내는 것으로 인해 발생하는 잘못된 평판과 벌킹 및 차단 문제를 파고드는 것은 좌절스럽고 시간이 많이 소요되며 비용이 많이 들 수 있습니다.

볼륨 임계값은 ISP에 따라 다르며 평균 참여 지표에 따라 달라질 수 있습니다. 일부 발신자는 매우 낮고 느린 볼륨 램프를 필요로 하는 반면, 다른 발신자는 더 가파른 볼륨 램프를 허용할 수 있습니다. Adobe 전달성 컨설턴트와 같은 전문가와 협력하여 맞춤화된 볼륨 플랜을 개발하는 것이 좋습니다.

다음은 원활하게 전환하는 방법에 대한 힌트 및 팁 목록입니다.

* **권한** 은 성공적인 이메일 프로그램의 기초입니다.
* **낮고 느림** — 전송 볼륨이 낮은 상태에서 시작하여 보낸 사람의 신뢰도가 높아집니다.
* A **탠덤 메일링 전략** 이메일 일정을 중단하지 않고 현재 ESP를 사용하는 동안 Campaign에서 볼륨을 증가시킬 수 있습니다.
* **참여 문제** — 정기적으로 이메일을 열고 클릭하는 구독자부터 시작합니다.
* **플랜 준수** — 당사의 권장 사항이 수백 명의 Campaign 고객이 이메일 프로그램을 성공적으로 확장하는 데 도움이 되었습니다.
* **회신 이메일 계정 모니터링**. 고객이 noreply@xyz.com 을 사용하거나 응답하지 않는 것은 좋지 않은 경험입니다.
* 비활성 주소는 전달성에 부정적인 영향을 미칠 수 있습니다. **현재 플랫폼에서 재활성화 및 재권한**, 새 IP가 아닙니다.
* **도메인** — 회사 실제 도메인의 하위 도메인인 전송 도메인 사용
   * 예를 들어 회사 도메인이 xyz.com이면 email.xyz.com 은 xyzemail.com 보다 ISP에 더 많은 신뢰도를 제공합니다.
* **투명도** — 이메일 도메인의 등록 세부 정보는 공개적으로 사용할 수 있어야 하며 비공개가 아니어야 합니다.

많은 상황에서 트랜잭션 메일은 기존의 프로모션 준비 방식을 따르지 않습니다. 일반적으로 이메일 터치를 트리거하려면 사용자 상호 작용이 필요하기 때문에 트랜잭션 메일의 볼륨을 제어하는 것은 그 특성으로 인해 어렵습니다. 어떤 경우에는, 거래 메일을 단순히 공식적인 계획 없이 전환할 수 있다. 다른 경우에는 시간이 지남에 따라 각 메시지 유형을 전환하여 볼륨을 천천히 늘리는 것이 좋습니다. 예를 들어 다음과 같이 전환할 수 있습니다.

1. 구매 확인 — 일반적으로 높은 참여도
2. 장바구니 포기—보통 - 높은 참여도
3. 환영 이메일 — 참여도가 높지만 목록 수집 방법에 따라 잘못된 주소를 포함할 수 있음
4. Winback 이메일 — 일반적으로 참여도가 낮음

## 제품별 리소스

**Campaign**

* 에서 Adobe Campaign으로 새 플랫폼을 시작할 때 게재 기능 관리에 대해 자세히 알아봅니다. [이 섹션](/help/additional-resources/ac-starting-new-platform.md).
* 에서 Adobe Campaign Classic과 함께 여러 웨이브를 사용하여 를 전송하는 방법에 대해 알아봅니다. [이 섹션](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves).
* 에서 하위 도메인을 Adobe Campaign Classic 또는 Standard에 완전히 위임하는 방법을 알아봅니다. [이 섹션](/help/additional-resources/ac-domain-name-setup.md).
* [Campaign 컨트롤 패널: 전체 하위 도메인 위임(튜토리얼)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *하위 도메인을 Adobe Campaign Classic에 완전히 위임하는 방법을 알아봅니다.*
* [Campaign 컨트롤 패널: 전체 하위 도메인 위임(튜토리얼)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *하위 도메인을 Adobe Campaign Standard에 완전히 위임하는 방법을 알아봅니다.*

## 추가 리소스

* 에서 IP warming으로 이메일 평판을 높이는 방법에 대해 자세히 알아보기 [이 섹션](/help/additional-resources/increase-reputation-with-ip-warming.md).
