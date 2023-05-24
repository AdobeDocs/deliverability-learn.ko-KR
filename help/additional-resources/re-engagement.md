---
title: 재참여 모범 사례
description: 재참여 전략을 통해 전달성을 향상시키는 방법을 알아봅니다.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 30118706-d4c0-4bd8-8c9b-50c26b8374ef
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 1%

---

# 재참여 모범 사례 {#re-engagement}

전달성을 구현하는 동안 몇 가지 모범 사례는 건강한 구독자 기반을 유지하고 재참여(또는 Win-back) 전략을 통해 전달성을 개선하는 것으로 구성되어 있습니다.

* 양호한 가입자 기반을 유지하는 것은 좋은 지속적 전달을 보장하기 위한 주요 측면 중 하나이다. 잘못된 데이터 사례 및 유지 관리로 인해 많은 전달성 문제가 발생합니다.
* 마케터가 현재 직면한 가장 일반적인 문제 중 하나는 이메일 배달 및 낮은 ROI에 부정적인 영향을 줄 수 있는 비활성 구독자 활동(낮음 또는 미참여)입니다.

>[!NOTE]
>
>재참여 캠페인 전략 및 Adobe의 전달성 서비스에 대한 자세한 내용은 전달성 컨설턴트에게 문의하거나 Adobe 영업 담당자에게 문의하십시오.

## ISP는 비참여 활동을 어떻게 보습니까? {#how-do-isps-view-non-engagement-activity-}

수년간 ISP는 사용자의 참여 피드백 지표를 사용하여 메시지를 배치할 위치나 메시지를 전달해야 하는 사항을 결정해 왔습니다. 사용자 [참여](/help/engagement.md) 양수 및 음수 피드백 모두로 구성되며 ISP는 둘 다 지속적으로 모니터링합니다. 약혼을 하지 않는 것은 아마도 부정적 관여의 주요 원인 중 하나일 것이다. 전달성의 관점에서 볼 때, 참여가 없는 사용자에게 캠페인을 일관되게 보내면 IP 주소 및 도메인의 전체 신뢰도가 낮아질 수도 있습니다.

Gmail, Microsoft® 및 OATH와 같은 ISP는 미참여를 원하지 않는 이메일로 보고 메시지를 스팸 폴더로 리디렉션하기 시작합니다. 또한 이러한 구독자는 더 이상 이메일 계정을 소유하지 않을 수 있으며 이를 &quot;재활용된&quot; 스팸 트랩으로 사용할 수 있습니다. 즉, 주소가 잠시 동안 유효하지 않으며 모든 메시지가 거부됩니다. 구독자 관리 시스템이 &quot;하드 바운스된&quot; 주소를 제거하지 않는 경우 심각한 게재 문제를 일으킬 수 있는 스팸 트랩으로 메일링이 전달될 수 있습니다.

## 활동이 없는 경우 어떻게 접근해야 합니까? {#how-should-you-approach-inactivity-}

Adobe 플랫폼을 사용하는 고객은 세그먼트에 따라 열기 및 클릭 데이터를 검토하여 인스턴스 내에서 비활성 상태를 볼 수 있습니다. 비참여는 전달을 방해할 수 있기 때문에, 첫 번째 생각은 데이터베이스에서 가입자를 제거하는 것일 수 있다. 그러나, 이것은 때때로 잘못된 선택으로 입증될 수 있습니다. 따라서 메일 수신에 관심이 있는 구독자를 유지하고, 더 이상 활동을 표시하지 않는 구독자를 단계적으로 제외하는 재참여(일명, 윈-백) 전략이 가장 좋습니다.

## 재참여 캠페인이 실제로 작동합니까? {#do-re-engagement-campaigns-really-work-}

재참여 경로 연구에 따르면 일반 캠페인의 평균 14%에 비해 재참여 캠페인은 12%의 열람률로 나타났다. 비록 24%의 구독자만이 재참여 캠페인을 읽었지만, 약 45%의 구독자가 후속 메시지를 읽었다.

![](../../help/assets/deliverability_implementation_1.png)

## 재참여 캠페인을 만드는 방법 {#how-do-you-create-a-re-engagement-campaign-}

### 단계 1 {#phase-1}

* 첫 번째 단계는 열기 또는 클릭 활동이 거의 없는 가입자를 식별하는 것이며, 따라서 설정된 시간대를 기반으로 이 그룹을 세그먼트화합니다. 경험칙은 지난 90일 이내에 이메일을 열거나 클릭하지 않은 구독자를 검토하는 것입니다. 하지만 이는 비즈니스 특성(예: 계절별 전송)에 따라 다릅니다.
* 시간대를 정의하는 동안 유념해야 할 또 다른 점은 ISP와 차단 목록 회사가 참여를 1.5년에서 1.8년 사이로 간주한다는 것입니다. 또한 구매 및 웹 사이트 활동과 같은 행동 활동 또는 등록 단계 또는 첫 번째 연락 지점 동안의 환경 설정과 같은 기타 터치 포인트입니다.

### 단계 2 {#phase-2}

* 세그먼트가 정의되면 다음 단계는 식별된 지표에 따라 구독자에게 맞는 재참여 캠페인을 만드는 것입니다. 제목 줄을 만들면 구독자의 흥미를 높이는 데 도움이 됩니다. 반환 경로 연구에 따르면 &quot;We miss you&quot;를 나타내는 제목란과 콘텐츠는 &quot;We want you back&quot;보다 높은 응답률을 생성합니다.
* 이메일 재참여를 위한 인센티브도 제공할 수 있습니다. 할인이 적용된 오퍼를 고려할 때 달러 금액 대 백분율을 사용하는 것이 가장 좋습니다. 또한 Return Path는 응답률이 높아지므로 이 작업을 수행하는 것을 제안합니다. 마지막으로 A/B 분할 테스트를 수행하여 응답 및 성공률을 검토하는 것도 유용한 옵션입니다.

### 단계 3 {#phase-3}

다음 단계는 재참여 캠페인의 빈도를 결정하는 것입니다. 재확인 메시지와 달리 재참여 캠페인은 시간에 따른 일련의 이메일을 통해 구독자를 다시 확보하는 것입니다. 다음 예제는 빈도의 예를 제공합니다.

![](../../help/assets/deliverability_implementation_2.png)

열기 또는 클릭 활동을 따라 캠페인에 참여하는 구독자는 참여 구독자 목록에 다시 추가됩니다.

### 4단계 {#phase-4}

* 다음 단계는 활동이 지속적으로 표시되지 않는 구독자를 식별하고 일정 기간 동안 구독자에 대한 이메일 전송을 점차 줄이는 것입니다. 지난 1년 내에 활동이 없다면 구독자의 이메일 구독을 보류하는 것이 좋습니다. 이메일 콘텐츠에 관심을 보이지 않았지만, 1회 재확인 캠페인을 보내어 구독을 다시 활성화시킬 수 있는 마지막 기회가 항상 있습니다.
* 재확인 캠페인은 오랫동안 활동이 없는 가입자에게 구독 목록에 남아 있기를 원하는 경우 묻는 좋은 방법입니다. 캠페인을 생성할 때 작업을 확인하고 주소를 확인할 수 있도록 &quot;여기를 클릭&quot; 링크를 추가하는 것이 좋습니다. 이렇게 하면 작업을 데이터베이스에 기록할 수 있습니다. 다음은 재확인 이메일의 예입니다.

   ![](../../help/assets/deliverability_implementation_3.png)

   가입자가 조치를 취하면 재가입 확정이 포함된 랜딩 페이지를 제공할 수 있습니다. 다음은 랜딩 페이지의 예입니다.

   ![](../../help/assets/deliverability_implementation_4.png)

## 제품별 리소스

**Adobe Campaign**

* [Campaign Classic의 추적 로그](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html#tracking-logs)
* [Campaign Standard의 추적 로그](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/sending-and-tracking-messages/tracking-messages.html#tracking-logs)

**Adobe 고객 여정 관리**

* [메시지 추적](https://experienceleague.adobe.com/docs/journey-optimizer/using/reporting/message-tracking.html?lang=ko)
