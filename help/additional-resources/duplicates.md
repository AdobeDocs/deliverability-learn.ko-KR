---
title: 중복 항목
description: 중복 항목을 식별하고 제한하는 방법을 사용하여 게재 능력을 향상시키는 방법을 알아봅니다.
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
exl-id: f89dbb38-a8d4-4294-b017-6fed72591593
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 6%

---

# 중복 항목 {#duplicates}

이메일 주소가 중복되면 다음과 같은 여러 결과가 발생할 수 있습니다.

* 동일한 메시지가 두 번 이상 전송됩니다. Adobe이 기본적으로 전송 전에 중복 제거 절차를 수행하더라도 대상이 분할될 때 콘텐츠가 동일한 다른 작업에서 동일한 메시지가 전송되는 것을 중단할 수 없습니다.
* 구독 취소 요청이 적용되지 않았습니다. 수신자가 메시지를 받은 후 구독을 취소하는 경우 중복 프로필은 계속 향후 메시지에 적합합니다.

이러한 옵트인 절차를 단계별로 수행하는 것 외에도, 이 경우 사용자는 메시지를 스팸으로 간주하여 ISP에서 절차를 차단 목록 트리거할 수 있습니다.

데이터베이스에서 작업을 수행할 때는 특히 신중해야 합니다.

* 가져오기 작업은 특히 조정 키를 선택할 때 신중하게 구성해야 합니다.
* 변경된 이메일 주소는 중복 소스일 수도 있습니다. 특히 도메인이 다른 두 주소는 동일한 사서함으로 라우팅될 수 있습니다. 예를 들어 회사가 이름을 변경하고 특정 시간 동안 이전 도메인을 유지한 경우: joe.doe@amce-co.com 및 joe.doe@acme-rebranded.com에서 확인하십시오.
* 목록 또는 다른 데이터베이스에서 자동 가져오기는 프로필을 관리할 때 고려되는 요소입니다. 다른 파티션에서 프로필을 삭제하거나 이동하면 어떻게 됩니까? 예를 들어 구매 발주가 배치되는 경우와 같이 자동 가져오기로 초기 파티션에 다시 생성될 수 있습니다.
* 서로 다른 폴더에 프로파일을 저장하는 것은 파티션이 아닌 뷰를 사용하여 구현할 수 있습니다. 이러한 방식으로 프로필이 동일한 물리적 파티션에 있을 뿐 아니라 표시 및 관리를 위한 적절한 권한을 활성화합니다.

서로 다른 파티션 간의 중복이 정상인 경우도 모두 동일합니다. 예를 들어 서드파티 또는 다른 회사 엔티티에 대해 보낼 때 서로 다른 이유로 동일한 사람이 수신자가 되는 것이 논리적입니다. 그러나 동일한 파티션 내에서 중복을 찾는 것은 거의 일반적이지 않습니다.

## 제품별 리소스

중복 제거 주소는 전송 평판을 보호하고 격리 관리를 잘 해줍니다. 자세한 내용은 다음 제품 설명서 섹션을 참조하십시오.

**Adobe Campaign Classic**

* [중복 제거 활동](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/deduplication.html)
* [중복 제거 활동의 병합 기능 사용](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html?lang=ko)

**Adobe Campaign Standard**

* [가져온 파일에서 데이터 중복 제거](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-use-case/data-management/deduplicating-data-imported-file.html)
