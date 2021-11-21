---
title: 새 플랫폼 시작
description: Adobe Campaign으로 새 플랫폼을 시작할 때 게재 기능 관리에 대해 자세히 알아보십시오.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 6c9ade01-3052-4311-af80-888294820024
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 8%

---

# 새 플랫폼 시작 {#starting-new-platform}

Adobe Campaign에서 사용할 새 플랫폼을 설정할 때 도메인 및 IP 주소 평판 유지 관리가 중요합니다.

## 중요한 단계

플랫폼에 사용 내역이 없으며 전송 IP가 이 용도로 사용된 적이 없는 경우 신뢰성이 없으므로 새 플랫폼에서 전자 메일을 보낼 때는 매우 신중해야 합니다.

ISP는 원래 이메일을 보내는 데 사용된 적이 없는 IP 주소를 의심하기 때문에 갑자기 대량의 이메일 트래픽을 보내기 시작합니다. 실제로 스팸은 일반적으로 &quot;알 수 없는&quot; IP 주소(에 있었던 적이 없는 차단 목록 주소)를 사용하여 탐지하기 전에 가능한 가장 많은 수의 메시지를 보냅니다.

생산 단계의 시작 시점에 출력 측면에서 운영 속도에 도달하는 것을 기대할 수 없습니다. 또한, ISP가 전송 주소를 차단하고 나머지 시작 단계를 심각하게 손상시킬 수 있으므로 이 속도로 메시지를 보내려는 것은 안 됩니다.

## 주요 원칙

다음은 새 플랫폼을 시작할 때 따라야 할 주요 원칙은 다음과 같습니다.

* Adobe에서 전송된 이메일 캠페인에 고유한 전용 하위 도메인을 구성합니다.

* 이 정보가 있으면, **잘못된 주소를 격리 테이블에 가져오기**.
플랫폼 시작은 처음 주소 목록을 사용할 때 발생하고 자격이 완전히 상실될 수 있습니다. 잘못된 주소나 허니포트 주소로 보내면 플랫폼의 평판을 낮추는 데 도움이 됩니다.

   * 잘못된 주소 목록이 있는 경우 처음 보내기 전에 격리 테이블로 가져오는 것이 가장 좋습니다. 격리 테이블은 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** (Campaign Classic) 및 **[!UICONTROL Administration > Channels > Quarantines > Addresses]** (Campaign Standard) 메뉴 아래의 제품에서 사용할 수 있습니다.

   * 동일한 주소로 잘못된 주소를 요청하려는 경우, 플랫폼의 명성이 설정되고 시간이 지남에 따라 잘못된 주소의 사용을 &quot;희석&quot;하기 위해 비트별로 비트 단위로 구성한 후에는 이 방법을 사용하는 것이 훨씬 좋습니다.

* **처리량 비율 제한** 최대 개수 제한 이러한 기술 설정을 조정하는 방법에 대한 자세한 내용은 Adobe Campaign 관리자에게 문의하십시오.

* **전송되는 볼륨을 점진적으로 늘립니다** 스팸으로 표시되지 않도록 합니다. 처음부터 전체 데이터베이스를 타겟팅하지 말고 전송할 때마다 목록의 일부를 추가합니다. 따라서 각 단계에서 볼륨을 증가시키고 잘못된 주소의 전체 비율을 줄일 수 있습니다. 시작 단계의 원활한 개발을 위해 웨이브를 사용할 수 있습니다.

* **정기적으로 보내기**. 산발적으로 큰 캠페인보다는 정기적으로 작은 샷을 보내는 것이 좋다.
* **게재 보고서에 주의 사항**. 오류 표시기가 높으면 기술 설정이 잘못 구성되었음을 의미합니다.

## 추가 리소스

위에 나열된 원칙 및 Adobe Campaign을 사용한 구현에 대한 자세한 내용은 다음 섹션을 참조하십시오.

* [IP warming으로 이메일 신뢰도 향상](../../help/additional-resources/increase-reputation-with-ip-warming.md)
* [스팸 트랩에 대한 모든 정보](../../help/additional-resources/all-about-spam-traps.md)

**Adobe Campaign Classic**

* [격리를 통한 게재 최적화](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [플랫폼 전체에 대해 격리된 주소 확인](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#identifying-quarantined-addresses-for-the-entire-platform)
* [여러 웨이브를 사용하여 보내기](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves)
* [게재 모니터링](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html?lang=ko)

**Adobe Campaign Standard**

* [격리를 통한 게재 최적화](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [플랫폼 전체에 대해 격리된 주소 확인](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)
* [게재 모니터링](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html)
