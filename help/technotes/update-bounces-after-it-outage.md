---
title: Italia 온라인 중단 후 반송 자격 업데이트
description: Italia Online 중단 후 반송 조건을 업데이트하는 방법을 알아봅니다.
feature: Deliverability
exl-id: a11e88cf-bf37-42cc-9c09-1d58360459b7
hide: true
hidefromtoc: true
source-git-commit: aca77fb9326e34455a6fec7ffc9a7ad8e1750467
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 1%

---

# Italia Online 중단 후 잘못된 하드 바운스 업데이트 {#update-bounce-italia}

## 컨텍스트{#outage-context}

1월 22일(현지 시간)부터 Italia Online이 서비스 중단으로 인해 몇 가지 지연과 거부된 이메일이 발생했습니다. 서비스가 시작된 것은 제한된 용량의 1월 26일이었다.

영향을 받는 도메인은 다음과 같습니다. **라이베로.it**, **virgilio.it**, **inwind.it**, **iol.it**, 및 **blu.it**.

이 문제는 1/22/2023에서 1/26/2023으로 발생했지만, 대부분의 잘못된 격리가 1월 26일에 일어났다.

공식 통신에서 자세히 알아보기 [여기](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## 영향{#outage-impact}

대부분의 경우, 인터넷 서비스 공급자(ISP)가 중단될 때, Campaign이나 Journey Optimizer을 통해 보낸 일부 이메일이 바운스로 잘못 표시되었습니다. 이는 Adobe에 영향을 줄 뿐만 아니라 중단 기간 동안 Italia Online으로 이메일을 전달하려고 시도하는 모든 사용자에게도 영향을 주었습니다.

증상으로는

* **소프트 바운스** 메시지 사용 `452 requested action aborted: try again later` - 이러한 작업은 자동으로 다시 시도되며 필요한 작업이 없습니다.

* **하드 바운스 수** 메시지 사용 `550 <email address> recipient rejected` 은(는) 보낸 사람이 서버를 계속 오버로드하지 않도록 하기 위해 1월 26일 오전 8시~오후 2시(현지 시간) 사이에 ISP에 의해 반환되었습니다. Italia Online Postmaster에서 확인한 바와 같이, 실제 하드 바운스는 아니므로, 해당 메시지로 인해 2023년 1월 26일에 제외된 모든 이메일 주소는 격리하지 않는 것이 좋습니다.

## 업데이트할 프로세스{#outage-update}

### Adobe Campaign{#ac-update}

표준 바운스 처리 논리에 따라 Adobe Campaign은 이러한 수신자를 **[!UICONTROL Status]** 설정 **[!UICONTROL Quarantine]**. 이 문제를 해결하려면 이러한 수신자를 찾아 제거하거나 수신자를 변경하여 Campaign에서 격리 테이블을 업데이트해야 합니다 **[!UICONTROL Status]** to **[!UICONTROL Valid]** 야간 정리 워크플로우가 해당 워크플로우가 제거합니다.

이 문제의 영향을 받은 수신자를 찾거나 다른 ISP에서 이 문제가 다시 발생하는 경우 아래 지침을 참조하십시오.

* Campaign Classic v7 및 Campaign v8의 경우 다음을 참조하십시오 [이 페이지](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.
* Campaign Standard에 대해서는 [이 페이지](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.

### Adobe Journey Optimizer{#ajo-update}

표준 바운스 처리 로직에 따라 Adobe Journey Optimizer은 이러한 이메일 주소를 **[!UICONTROL Reason]** 설정 **[!UICONTROL Invalid Recipient]**. 이 문제를 해결하려면 이러한 이메일 주소를 찾아 제거하여 제외 목록을 업데이트해야 합니다.

식별되면 다음을 사용하여 제외 목록에서 이러한 주소를 수동으로 제거할 수 있습니다 **[!UICONTROL Delete]** 버튼을 클릭합니다. 그런 다음 이러한 주소를 향후 이메일 캠페인에 포함할 수 있습니다.

추가 정보 [이 섹션](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list.html#remove-from-suppression-list){_blank}.

