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
source-wordcount: '549'
ht-degree: 6%

---

# 새 플랫폼 시작 {#starting-new-platform}

Adobe Campaign에서 사용할 새 플랫폼을 설정할 때 도메인과 IP 주소 평판을 유지해야 합니다.

## 민감한 단계

플랫폼에는 사용 기록이 없고 전송 IP를 이 용도로 사용한 적이 없기 때문에 새 플랫폼에서 이메일을 보내기 시작할 때는 매우 주의해야 합니다.

ISP는 이메일 전송에 사용된 적이 없고 갑자기 대량의 이메일 트래픽을 보내기 시작하는 IP 주소를 의심하게 됩니다. 차단 목록에 추가하다 실제로, 탐지하기 전에 가장 많은 메시지를 전송하기 위해 일반적으로 &quot;알 수 없는&quot; IP 주소(스패머에 저장된 적이 없는 주소)를 사용합니다.

생산 단계의 시작 시점에 출력 측면에서 작동 속도에 도달할 것으로 기대할 수는 없다. 또한 ISP가 전송 주소를 차단하고 나머지 시작 단계를 심각하게 손상시킬 수 있으므로 이 속도로 메시지를 전송하려고 시도해서는 안 됩니다.

## 주요 원칙

다음은 새 플랫폼을 시작할 때 따라야 할 주요 원칙입니다.

* Adobe에서 보낸 이메일 캠페인에 고유한 전용 하위 도메인을 구성합니다.

* 이 정보가 있으면 **잘못된 주소를 격리 테이블로 가져오기**하십시오.
플랫폼 시작은 종종 처음으로 주소 목록을 사용할 때 발생하며 완전히 정규화되지 않을 수 있습니다. 잘못된 주소나 허니팟 주소로 전송하는 경우 플랫폼의 평판이 떨어집니다.

   * 잘못된 주소 목록이 있는 경우 처음 보내기 전에 격리 테이블로 해당 목록을 가져오는 것이 가장 좋습니다. 격리 테이블은 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**(Campaign Classic) 및 **[!UICONTROL Administration > Channels > Quarantines > Addresses]**(Campaign Standard) 메뉴를 통해 사용할 수 있습니다.

   * 모두 동일하게 잘못된 주소를 다시 확인하려는 경우, 플랫폼의 평판이 설정되고 조금씩 나누어 시간이 지남에 따라 잘못된 주소의 사용을 &quot;희석&quot;하기 위해 이 작업을 수행하는 것이 훨씬 좋습니다.

* 일치 항목 수를 제한하여 **처리량 속도를 제한**&#x200B;합니다. 이러한 기술 설정을 조정하는 방법에 대한 자세한 내용은 Adobe Campaign 관리자에게 문의하십시오.

* **스팸으로 표시되지 않도록 보낸 볼륨을 점진적으로 늘립니다**. 처음부터 전체 데이터베이스를 대상으로 하지 말고 전송할 때마다 목록의 일부를 더 추가합니다. 이렇게 하면 각 단계에서 볼륨을 높이면서 잘못된 주소의 전체 비율을 줄일 수 있습니다. 시작 단계의 원활한 개발을 위해 웨이브를 사용할 수 있습니다.

* **정기적으로 보내기**. 산발적으로 큰 캠페인보다는 소량 촬영물을 정기적으로 보내는 것이 어느 정도 좋다.
* **게재 보고서에 주의하십시오**. 오류 표시기가 높으면 기술 설정이 잘못 구성되었음을 의미할 수 있습니다.

## 추가 리소스

위에 나열된 원칙과 Adobe Campaign을 사용한 구현에 대한 자세한 내용은 다음 섹션을 참조하십시오.

* [IP warming으로 이메일 신뢰도 향상](../../help/additional-resources/increase-reputation-with-ip-warming.md)
* [스팸 트랩에 대한 모든 정보](../../help/additional-resources/all-about-spam-traps.md)

**Adobe Campaign Classic**

* [격리를 통해 게재 최적화](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [플랫폼 전체에 대해 격리된 주소 확인](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#identifying-quarantined-addresses-for-the-entire-platform)
* [예약된 일괄 처리를 사용하여 보내기](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves)
* [게재 모니터링](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html?lang=ko#sending-messages)

**Adobe Campaign Standard**

* [격리를 통해 게재 최적화](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [플랫폼 전체에 대해 격리된 주소 확인](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)
* [게재 모니터링](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html?lang=ko)
