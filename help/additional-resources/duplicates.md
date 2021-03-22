---
title: 중복 항목
description: 복제를 식별하고 제한하는 방법을 통해 제공 능력을 향상시키는 방법을 살펴볼 수 있습니다.
feature: Journey Orchestration용
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 3%

---


# {#duplicates} 복제

이메일 주소가 중복되면 다음과 같은 여러 결과가 발생할 수 있습니다.

* 두 번 이상 전송되는 동일한 메시지입니다. Adobe에서 데이터 중복 제거 절차를 기본적으로 수행하는 경우에도 대상이 분할될 때 동일한 컨텐츠를 갖는 다른 작업에 의해 전송되는 동일한 메시지를 중단할 필요가 없습니다.
* 구독 취소 요청이 승인되지 않았습니다. 수신자가 메시지를 받은 후 구독을 취소하는 경우 해당 중복 프로필은 계속 향후 메시지에 사용할 수 있습니다.

이러한 사전 동의 절차를 단계별로 밟는 것 외에, 이러한 상황으로 인해 사용자는 메시지를 스팸으로 간주하여 ISP에서 차단 목록 절차를 시작할 수 있습니다.

데이터베이스에서 작업을 수행할 때는 특히 신중해야 합니다.

* 가져오기 작업은 특히 조정 키를 선택할 때 섬세하게 구성해야 합니다.
* 변경된 이메일 주소는 중복 소스일 수도 있습니다. 특히 도메인이 다른 두 개의 주소는 같은 사서함으로 라우팅될 수 있습니다. 예를 들어 회사가 이름을 변경했고 특정 시간 동안 이전 도메인을 유지한 경우:joe.doe@amce-co.com 및 joe.doe@acme-rebranded.com을 참조하십시오.
* 목록 또는 다른 데이터베이스의 자동 가져오기는 프로파일을 관리할 때 고려해야 할 요소입니다. 다른 파티션에서 프로파일을 삭제하거나 이동하면 어떻게 됩니까? 예를 들어, 구매 발주를 배치할 때 자동 가져오기를 통해 초기 파티션에서 다시 만들 수 있습니다.
* 여러 폴더에 프로파일을 저장하는 방법은 파티션이 아닌 뷰를 사용하여 구현할 수 있습니다. 이러한 방식으로 프로파일은 표시 및 관리할 적절한 권한이 있는 상태에서 동일한 물리적 분할 영역에 있습니다.

다른 파티션 간에 중복되는 경우도 모두 동일하며, 예를 들어 제3자 또는 다른 회사 엔티티용으로 보낼 때 서로 다른 이유로 동일한 사람이 수신자가 되는 것이 논리적입니다. 그러나 동일한 파티션 내에서 복제본을 찾는 것은 거의 정상적이지 않습니다.

## 제품별 리소스

중복 제거 주소는 전송 명성을 보호하고 안전한 격리 관리를 보장합니다. 다음 제품 문서 섹션에서 자세한 내용을 살펴보십시오.

**Adobe Campaign Classic**

* [데이터 중복 제거 작업](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/deduplication.html)
* [데이터 중복 제거 작업의 병합 기능 사용](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html)

**Adobe Campaign Standard**

* [가져온 파일에서 데이터 중복 제거](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-use-case/data-management/deduplicating-data-imported-file.html)