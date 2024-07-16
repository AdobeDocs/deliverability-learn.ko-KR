---
title: 컴플레인
description: 사용자가 이메일을 원하지 않거나 예상치 않은 경우 등록되는 컴플레인에 대해 알아봅니다.
topics: Deliverability
jira: KT-7048
thumbnail: kt7048.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 0343820d-f5af-4b8a-bcab-dbb47ae7aecb
source-git-commit: 9444f8601f2f349398ee5deb9d5f4d4f7abb44f5
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 100%

---

# 컴플레인

사용자가 이메일을 원하지 않거나 예기치 않은 경우 컴플레인이 등록됩니다. 이 구독자 작업은 일반적으로 구독자가 스팸 버튼을 누를 때 또는 서드파티 스팸 보고 시스템을 통해 구독자의 이메일클라이언트로 기록됩니다.

## ISP 컴플레인

대부분의 Tier 1 및 일부 Tier 2 ISP는 옵트아웃 및 구독 취소 프로세스가 이전에 이메일 주소를 확인하기 위한 악의적인 방식으로 사용되었기 때문에 사용자에게 스팸 보고 방법을 제공합니다. Adobe Campaign은 ISP FBL을 통해 이러한 컴플레인을 받습니다. 이는 FBL을 제공하는 모든 ISP의 설정 프로세스 중에 설정되며 Adobe Campaign은 이를 통해 제거를 위한 격리 테이블로 컴플레인을 등록한 이메일 주소를 자동으로 추가할 수 있습니다. ISP 컴플레인의 스파이크는 낮은 목록 품질, 최적에 미치지 못하는 목록 수집 방법 또는 약한 참여 정책의 지표가 될 수 있습니다. 콘텐츠가 관련성이 없는 경우에도 종종 언급됩니다.

## 서드파티 컴플레인

스팸 보고를 광범위한 수준으로 허용하는 여러 개의 스팸 방지 그룹이 있습니다. 이러한 서드파티가 사용하는 컴플레인 지표는 이메일 콘텐츠에 태그를 지정하여 스팸 이메일을 식별하는 데 사용됩니다. 이 과정을 핑거프린팅이라고도 합니다. 이러한 서드파티 컴플레인 방법의 사용자는 일반적으로 이메일에 대한 지식이 풍부하기 때문에 답변을 하지 않을 경우 다른 컴플레인에 비해 더 많은 영향을 미칠 수 있습니다.

>[!NOTE]
>
>ISP는 컴플레인을 수집하고 이를 사용하여 보낸 사람의 전반적인 신뢰도를 파악합니다. 모든 컴플레인은 제거되어야 하며, 가능한 빨리 그리고 지역 법률과 규정에 따라 더 이상 발생하지 말아야 합니다.

## 제품별 리소스

**Adobe Campaign Classic**

* [지표 추적](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html?lang=ko#tracking-indicators)

**Adobe Campaign Standard**

* [불만 사항 보고서](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/complaints.html?lang=ko#reporting)
