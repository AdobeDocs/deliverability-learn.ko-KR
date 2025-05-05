---
title: 중복 항목
description: 중복을 식별하고 제한하여 게재 가능성을 개선하는 방법을 알아봅니다.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: f89dbb38-a8d4-4294-b017-6fed72591593
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 5%

---

# 중복 항목 {#duplicates}

이메일 주소가 중복되면 여러 가지 결과가 발생할 수 있습니다.

* 동일한 메시지가 두 번 이상 전송됩니다. Adobe이 전송 전에 기본적으로 중복 제거 절차를 수행하더라도 대상이 분할될 때 동일한 콘텐츠를 갖는 다른 작업에 의해 동일한 메시지가 전송되는 것을 막을 수 없습니다.
* 구독 취소 요청이 허용되지 않습니다. 메시지를 받은 후 수신자가 구독을 취소하는 경우 중복 프로필은 여전히 향후 메시지를 받을 수 있습니다.

이러한 옵트인 절차의 사이드 스테핑 외에도 이러한 상황은 사용자가 메시지를 스팸으로 간주하고 ISP에서 차단 목록에 추가하다 절차를 트리거하도록 할 수 있습니다.

데이터베이스에서 작업을 수행할 때는 특히 신중해야 합니다.

* 가져오기는 특히 조정 키를 선택할 때 세심하게 구성해야 합니다.
* 변경된 이메일 주소도 중복 소스일 수 있습니다. 특히, 회사가 이름을 변경하고 특정 시간 동안 이전 도메인을 유지한 경우(예: joe.doe@amce-co.com 및 joe.doe@acme-rebranded.com)와 같이 다른 도메인을 가진 두 주소가 동일한 사서함으로 라우팅될 수 있습니다.
* 자동 가져오기는 목록이든 다른 데이터베이스에서든 프로필 관리 시 고려해야 할 요소입니다. 다른 파티션에서 프로필을 삭제하거나 이동하면 어떻게 됩니까? 초기 분할 영역에서 자동 가져오기로 다시 생성할 수 있습니다(예: 구매 발주가 있는 경우).
* 다른 폴더에 프로필을 저장하는 것은 파티션이 아닌 보기를 사용하여 구현할 수 있습니다. 이러한 방식으로 프로필이 동일한 물리적 파티션에 있는지 확인하는 동시에 적절한 권한을 표시하고 관리할 수 있습니다.

서로 다른 파티션 간에 중복이 일반적인 경우도 있습니다. 예를 들어 서드파티 또는 다른 회사 엔티티용으로 보낼 때 동일한 사람이 다른 이유로 수신자가 되는 것은 논리적입니다. 그러나 동일한 파티션 내에서 중복을 찾는 것은 일반적이지 않습니다.

## 제품별 리소스

주소 중복을 제거하면 전송 평판이 보호되며 격리도 잘 관리됩니다. 자세한 내용은 다음 제품 설명서 섹션을 참조하세요.

**Adobe Campaign Classic**

* [중복 제거 활동](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/deduplication.html?lang=ko)
* [중복 제거 활동의 병합 기능 사용](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html?lang=ko)

**Adobe Campaign Standard**

* [가져온 파일에서 데이터 중복 제거](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-use-case/data-management/deduplicating-data-imported-file.html?lang=ko)
