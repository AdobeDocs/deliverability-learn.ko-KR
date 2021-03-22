---
title: 재참여 모범 사례
description: 재참여 전략을 통해 전달 능력을 향상시키는 방법을 살펴볼 수 있습니다.
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
source-wordcount: '928'
ht-degree: 1%

---


# 재참여 모범 사례 {#re-engagement}

제공 기능을 구현하는 동안, 우수 사례 중 일부는 건강한 구독자를 유지하고 재참여(또는 재구독) 전략을 통해 제공 능력을 향상시키고자 하는 데 사용됩니다.

* 가입자의 건강을 유지하는 것은 선하고 일관된 전달을 보장하는 주요 측면 중 하나입니다. 데이터 모범 사례 및 유지 관리가 취약하여 발생하는 여러 문제가 있습니다.
* 오늘날 마케터가 당면하고 있는 가장 일반적인 문제 중 하나는 이메일 전달과 낮은 ROI에 부정적인 영향을 미칠 수 있는 비활성 구독자 활동(즉, 낮은 참여도 또는 비참여도)입니다.

>[!NOTE]
>
>재참여 캠페인 전략 및 Adobe의 배달 가능성 서비스에 대한 자세한 내용은 고객 제공 능력 컨설턴트에게 문의하거나 Adobe 영업 담당자에게 문의하십시오.

## ISP는 비참여 활동을 어떻게 볼 수 있습니까?{#how-do-isps-view-non-engagement-activity-}

수년 동안 ISP는 사용자의 참여 피드백 지표를 사용하여 메시지를 배치할 위치 또는 메시지를 제공해야 할지 여부를 결정합니다. 사용자 [관여](/help/engagement.md)는 긍정적 피드백과 부정적 피드백과 ISP 모니터로 모두 일정하게 구성됩니다. 참여가 없는 것은 아마도 부정적인 참여의 주요 기여자 중 하나일 것이다. 전달 가능성 관점에서 볼 때 참여가 없는 사용자에게 캠페인을 일관되게 전송하는 것은 IP 주소와 도메인의 전체적인 명성을 떨어뜨릴 수도 있습니다.

Gmail, Microsoft 및 OATH와 같은 ISP는 비참여를 원하지 않는 이메일로 보고 메시지를 스팸 폴더로 리디렉션하기 시작합니다. 또한 이러한 가입자는 더 이상 이메일 계정을 소유하고 있지 않을 수 있으며, 이것은 &quot;재활용&quot; 스팸 트랩으로 사용될 수 있습니다. 이는 얼마 동안 주소가 유효하지 않아 모든 메시지가 거부됨을 의미합니다. 구독자 관리 시스템에서 &quot;하드 바운스된&quot; 주소를 제거하지 않는 경우 중요한 배포 문제를 초래할 수 있는 스팸성 트랩으로 보낼 가능성이 높습니다.

## 활동하지 않는 데 어떻게 접근해야 합니까?{#how-should-you-approach-inactivity-}

Adobe 플랫폼을 사용하는 고객은 열려 있는 항목을 검토하고 세그먼트에 따라 데이터를 클릭하여 인스턴스 내에서 비활동 상태를 볼 수 있습니다. 비관여는 전달에 지장을 줄 수 있으므로 우선 데이터베이스에서 가입자를 제거하는 것이 좋습니다. 하지만, 이것은 때때로 잘못된 선택인 것으로 판명될 수 있습니다. 따라서 재참여(재참여라고도 함) 전략은 메일을 받는 데 관심이 있는 가입자를 유지하고 더 이상 활동을 보이지 않는 가입자를 단계적으로 제외하는 것이 가장 좋습니다.

## 재참여 캠페인이 실제로 작동합니까?{#do-re-engagement-campaigns-really-work-}

재방문 경로 연구에 따르면, 재참여 캠페인의 결과는 일반 캠페인의 평균 14%와 비교하여 12%의 공개 비율을 보인 것으로 나타났습니다. 구독자 중 24%만이 재참여 캠페인을 읽었지만 약 45%가 후속 메시지를 읽었습니다.

![](../../help/assets/deliverability_implementation_1.png)

## 재참여 캠페인을 만들려면 어떻게 해야 합니까?{#how-do-you-create-a-re-engagement-campaign-}

### 1단계 {#phase-1}

* 첫 번째 단계는 열려 있거나 클릭하는 활동이 거의 없는 가입자를 식별하고 그에 따라 지정된 기간 동안 이 그룹을 세그먼트화하는 것입니다. 어림잡아 90일 이내에 이메일을 열거나 클릭하지 않은 가입자를 검토할 수 있습니다. 하지만 비즈니스 특성(예: 계절 보내기)에 따라 다릅니다.
* 시간대를 정의하면서 기억해야 할 또 다른 점은 ISP와 차단 목록 회사가 참여도를 1.5년에서 1.8년 사이 어느 곳이라고 고려하는 것입니다. 또한 구매 및 웹 사이트 활동과 같은 행동 활동이나 등록 단계 또는 첫 번째 접촉 시 환경 설정과 같은 기타 접촉 지점.

### 2단계 {#phase-2}

* 세그먼트가 정의된 후 다음 단계는 식별된 지표에 따라 가입자에게 제공되는 재참여 캠페인을 만드는 것입니다. 제목 줄을 만들면 가입자의 관심을 높이는 데 도움이 됩니다. 리턴 경로 연구에 따르면 &quot;We missing you&quot;를 나타내는 주제 라인 및 컨텐츠는 &quot;We want you back&quot;보다 응답률이 더 높습니다.
* 이메일을 다시 이용하려면 인센티브를 제공할 수도 있습니다. 할인이 있는 오퍼를 고려할 때, 달러 금액 대 백분율 값을 사용하는 것이 가장 좋습니다. 반환 경로는 응답률이 높기 때문에 이 작업을 수행하는 것을 제안합니다. 마지막으로 응답 및 성공률을 검토하기 위해 A/B 분할 테스트를 수행하는 것도 유용한 옵션입니다.

### 3단계 {#phase-3}

다음 단계는 재참여 캠페인의 빈도를 결정하는 것입니다. 재확인 메시지와 달리 재참여 캠페인은 시간이 지남에 따라 여러 개의 이메일을 사용하여 구독자에게 다시 돌아오는 것을 목표로 합니다. 다음 예제에서는 주파수 예제를 제공합니다.

![](../../help/assets/deliverability_implementation_2.png)

공개 또는 클릭 활동을 팔로우하여 캠페인에 참여하는 가입자는 참여한 구독자 목록에 다시 추가됩니다.

### 4단계 {#phase-4}

* 다음 단계는 지속적으로 아무런 활동을 보이지 않는 가입자를 식별하고 일정 기간 동안 해당 가입자에게 이메일을 보내는 것을 점진적으로 줄이는 것입니다. 지난 1년 이내에 활동이 없는 경우, 구독자에게 이메일 구독을 잠시 중단시키는 것이 좋습니다. 이메일 컨텐츠에 관심이 없더라도 일회성 다시 확인 캠페인을 보내 구독을 다시 활성화할 수 있는 마지막 기회가 항상 있습니다.
* 다시 확인 캠페인은 가입 목록에 오래 동안 비활성 상태인 가입자에게 계속 유지할지 여부를 묻는 좋은 방법입니다. 캠페인을 만들 때 작업을 확인하고 주소를 확인할 수 있도록 &quot;여기를 클릭&quot; 링크를 추가하는 것이 좋습니다. 이렇게 하면 액션을 데이터베이스에 기록할 수 있습니다. 다음은 재확인 이메일의 예입니다.

   ![](../../help/assets/deliverability_implementation_3.png)

   가입자가 조치를 취하면 재가입이 확인되는 랜딩 페이지를 제공할 수 있다. 다음은 랜딩 페이지의 예입니다.

   ![](../../help/assets/deliverability_implementation_4.png)

## 제품별 리소스

**Adobe Campaign**

* [Campaign Classic의 추적 로그](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html#tracking-logs)
* [Campaign Standard의 추적 로그](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/sending-and-tracking-messages/tracking-messages.html#tracking-logs)

**Adobe 고객 여정 관리**

* [메시지 추적](https://experienceleague.adobe.com/docs/customer-journey-management/using/reporting/message-tracking.html)