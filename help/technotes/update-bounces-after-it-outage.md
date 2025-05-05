---
title: Italia Online 중단 후 바운스 자격 업데이트
description: Italia Online 중단 후 바운스 자격을 업데이트하는 방법을 알아봅니다.
feature: Deliverability
exl-id: a11e88cf-bf37-42cc-9c09-1d58360459b7
hide: true
hidefromtoc: true
role: Admin
level: Beginner
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 3%

---

# Italia Online 중단 후 잘못된 하드 바운스 업데이트 {#update-bounce-italia}

## 컨텍스트{#outage-context}

1월 22일(현지 시간)부터 Italia Online이 중단되어 여러 건의 지연 및 이메일 거부가 발생했습니다. 서비스는 1월 26일부터 제한된 용량으로 재개되기 시작했다.

영향을 받는 도메인은 **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** 및 **blu.it**&#x200B;입니다.

이 문제는 2023년 1월 22일부터 2023년 1월 26일까지 발생했지만, 대부분의 잘못된 격리 조치는 1월 26일에 발생했습니다.

공식 커뮤니케이션 [여기](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}에서 자세히 알아보세요.


## 영향{#outage-impact}

인터넷 서비스 공급자(ISP) 가동이 중단된 대부분의 경우와 마찬가지로 Campaign이나 Journey Optimizer을 통해 보낸 일부 이메일이 바운스로 잘못 표시됐다. 이는 Adobe에 영향을 미칠 뿐만 아니라 중단 기간 동안 Italia Online으로 이메일을 전송하려는 모든 사용자에게 영향을 미쳤습니다.

증상은 다음과 같습니다.

* **소프트 바운스**(메시지 `452 requested action aborted: try again later`) - 자동으로 다시 시도되었으며 작업이 필요하지 않습니다.

* ISP가 1월 26일 오전 8시~오후 2시(현지 시간 기준) 사이에 보낸 사람이 서버를 계속 오버로드할 수 없도록 **하드 바운스**(메시지 `550 <email address> recipient rejected`)를 반환했습니다. Italia Online Postmaster에서 확인한 바와 같이, 이는 실제 하드 바운스가 아니므로 해당 메시지로 인해 2023년 1월 26일에 제외된 모든 이메일 주소를 격리 해제하는 것을 권장합니다.

## 업데이트할 프로세스{#outage-update}

### Adobe Campaign{#ac-update}

표준 바운스 처리 논리에 따라 Adobe Campaign은 **[!UICONTROL Status]** 설정이 **[!UICONTROL Quarantine]**&#x200B;인 격리 목록에 이 수신자를 자동으로 추가했습니다. 이 문제를 해결하려면 야간 정리 워크플로우에서 해당 수신자를 찾아 제거하거나 **[!UICONTROL Status]**&#x200B;을(를) **[!UICONTROL Valid]**(으)로 변경하여 Campaign에서 격리 테이블을 업데이트해야 합니다.

이 문제의 영향을 받은 수신자를 찾으려면 또는 다른 ISP에서 이 문제가 다시 발생하는 경우 아래 지침을 참조하십시오.

* Campaign Classic v7 및 Campaign v8의 경우 [이 페이지](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=ko#unquarantine-bulk){_blank}를 참조하세요.
* Campaign Standard은 [이 페이지](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=ko#unquarantine-bulk){_blank}를 참조하세요.

### Adobe Journey Optimizer{#ajo-update}

표준 바운스 처리 논리에 따라 Adobe Journey Optimizer은 **[!UICONTROL Reason]** 설정이 **[!UICONTROL Invalid Recipient]**&#x200B;인 비표시 목록에 이러한 이메일 주소를 자동으로 추가했습니다. 이 문제를 해결하려면 이러한 이메일 주소를 찾아 제거하여 제외 목록을 업데이트해야 합니다.

식별되면 **[!UICONTROL Delete]** 단추를 사용하여 제외 목록에서 이러한 주소를 수동으로 제거할 수 있습니다. 이후 이메일 캠페인에 이러한 주소를 포함할 수 있습니다.

자세한 내용은 [이 섹션](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list.html?lang=ko#remove-from-suppression-list){_blank}을 참조하세요.

