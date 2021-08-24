---
title: 재참여 모범 사례
description: 재참여 전략을 통해 게재 능력을 향상시키는 방법을 알아봅니다.
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
exl-id: 30118706-d4c0-4bd8-8c9b-50c26b8374ef
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 1%

---

# 재참여 모범 사례 {#re-engagement}

게재 능력을 구현하는 동안, 일부 우수 사례는 건강한 구독자 기반을 유지하고 재참여(또는 재방문) 전략을 통해 게재 능력을 향상하려고 하는 데 있습니다.

* 건강한 가입자 기반을 유지하는 것은 선하고 일관된 전달을 보장하는 주요 측면 중 하나이다. 게재 가능성 문제는 데이터 모범 사례 및 유지 관리가 취약하여 발생합니다.
* 마케터가 오늘날 직면하는 가장 일반적인 문제 중 하나는 이메일 게재와 낮은 ROI에 부정적인 영향을 줄 수 있는 비활성 가입자 활동(낮음 또는 비참여라고도 함)입니다.

>[!NOTE]
>
>재참여 캠페인 전략 및 Adobe의 Deliverability 서비스에 대한 자세한 내용은 Deliverability 컨설턴트에게 문의하거나 Adobe 영업 담당자에게 문의하십시오.

## ISP는 비참여 활동을 어떻게 표시합니까? {#how-do-isps-view-non-engagement-activity-}

수년 동안 ISP는 사용자의 참여 피드백 지표를 사용하여 메시지를 보낼 위치 또는 메시지를 제공해야 하는지 여부를 판별했습니다. 사용자 [참여](/help/engagement.md)는 양수 및 음수 피드백과 ISP 모니터로 모두 일정하게 구성됩니다. 관여가 없는 것은 아마도 부정적인 참여의 주요 기여자 중 하나일 것이다. 게재 가능성 관점에서 참여를 보이지 않는 사용자에게 캠페인을 일관되게 전송하는 것은 IP 주소 및 도메인의 전반적인 평판을 낮출 수도 있습니다.

Gmail, Microsoft 및 OATH와 같은 ISP는 비참여를 원치 않는 이메일로 보고, 메시지를 스팸 폴더로 리디렉션하기 시작합니다. 또한 이러한 구독자는 더 이상 이메일 계정을 소유하지 않을 수 있으며 이 계정은 &quot;재활용&quot; 스팸 트랩으로 사용할 수 있습니다. 즉, 주소가 잠시 동안 유효하지 않으며 모든 메시지가 거부됩니다. 가입자 관리 시스템에서 &quot;하드 바운스된&quot; 주소를 제거하지 않는 경우 심각한 게재 문제를 야기할 수 있는 스팸 트랩으로 이메일을 보낼 가능성이 높습니다.

## 활동을 하지 않게 하려면 어떻게 해야 합니까? {#how-should-you-approach-inactivity-}

Adobe 플랫폼을 사용하는 고객은 열린 을 검토하고 세그먼트에 따른 데이터를 클릭하여 인스턴스 내에서 비활동을 볼 수 있습니다. 비참여를 통해 전달을 저해할 수 있으므로, 먼저 데이터베이스에서 구독자를 제거하는 것이 될 수 있습니다. 하지만, 이것은 때때로 잘못된 선택인 것으로 입증될 수 있습니다. 따라서, 재참여(Win-Back이라고도 함) 전략은 우편 수신에 관심이 있는 가입자를 유지하고 더 이상 활동을 보이지 않는 가입자를 단계적으로 배제하는 것이 가장 좋습니다.

## 재참여 캠페인이 실제로 작동합니까? {#do-re-engagement-campaigns-really-work-}

리턴 경로 연구에 따르면, 재참여 캠페인의 결과는 일반 캠페인의 평균 14%와 비교하여 12%의 공개 비율로 나타났습니다. 비록 구독자의 24%만이 재참여 캠페인을 읽었지만, 약 45%가 후속 메시지를 읽었다.

![](../../help/assets/deliverability_implementation_1.png)

## 재참여 캠페인을 만들려면 어떻게 합니까? {#how-do-you-create-a-re-engagement-campaign-}

### 1단계 {#phase-1}

* 첫 번째 단계는 열기 또는 클릭 활동이 거의 없는 가입자를 식별하고 그에 따라 이 그룹을 설정된 시간 프레임을 기반으로 세그먼트화하는 것입니다. 경험상 지난 90일 내에 이메일을 열지 또는 클릭하지 않은 가입자를 검토하는 것이 원칙입니다. 하지만 비즈니스 특성에 따라(예: 계절별 전송) 다릅니다.
* 타임프레임을 정의하면서 기억해야 할 또 다른 점은 ISP와 차단 목록 회사가 참여를 1.5년에서 1.8년 사이의 범위로 고려하는 것입니다. 또한 구매 및 웹 사이트 활동과 같은 행동 활동이나 등록 단계 또는 첫 번째 연락 지점 동안 환경 설정과 같은 기타 터치 포인트.

### 2단계 {#phase-2}

* 세그먼트가 정의되면 다음 단계는 식별된 지표에 따라 가입자를 만족시키는 재참여 캠페인을 만드는 것입니다. 제목란을 만들면 가입자의 흥미를 높일 수 있습니다. Return Path 연구에 따르면 &quot;We missing you&quot;라는 제목 줄과 컨텐츠는 &quot;We want you back&quot;보다 더 높은 응답률을 생성합니다.
* 이메일을 다시 사용할 때 인센티브를 제공할 수도 있습니다. 할인이 있는 오퍼를 고려할 때, 달러 금액 대 백분율을 사용하는 것이 가장 좋습니다. 또한 반환 경로에서 더 높은 응답률을 발생하므로 이를 수행하는 것이 좋습니다. 마지막으로, A/B 분할 테스트를 수행하여 응답과 성공률을 검토하는 것도 유용한 옵션입니다.

### 3단계 {#phase-3}

다음 단계는 재참여 캠페인의 빈도를 결정하는 것입니다. 재확인 메시지와 달리, 재참여 캠페인은 시간이 지남에 따라 일련의 이메일을 사용하여 구독자를 되찾기 위한 것입니다. 다음 예는 빈도의 예를 제공합니다.

![](../../help/assets/deliverability_implementation_2.png)

열기 또는 클릭 활동을 따라 캠페인에 참여하는 구독자는 다시 구독자 목록에 추가됩니다.

### 4단계 {#phase-4}

* 다음 단계는 계속해서 활동을 표시하지 않고 일정 기간 동안 점진적으로 전자 메일을 보내는 구독자를 식별하는 것입니다. 지난 1년 내에 활동이 없으면 구독자 이메일 구독을 유지하는 것이 좋습니다. 이메일 콘텐츠에 관심이 없는 사용자에게는 항상 일회성 재확인 캠페인을 보내어 구독을 다시 활성화할 수 있는 마지막 기회가 있습니다.
* 재확인 캠페인은 오랫동안 비활성 상태인 구독자에게 구독 목록에 남아 있기를 바란다면 묻는 좋은 방법입니다. 캠페인을 만들 때 작업을 확인하고 주소를 확인할 수 있도록 &quot;여기 클릭&quot; 링크를 추가하는 것이 좋습니다. 이렇게 하면 작업을 데이터베이스에 기록할 수 있습니다. 다음은 재확인 이메일의 예입니다.

   ![](../../help/assets/deliverability_implementation_3.png)

   가입자가 작업을 하면 재구독 확인이 포함된 랜딩 페이지가 제공될 수 있습니다. 다음은 랜딩 페이지의 예입니다.

   ![](../../help/assets/deliverability_implementation_4.png)

## 제품별 리소스

**Adobe Campaign**

* [Campaign Classic의 추적 로그](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html#tracking-logs)
* [Campaign Standard의 추적 로그](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/sending-and-tracking-messages/tracking-messages.html#tracking-logs)

**고객 여정 관리 Adobe**

* [메시지 추적](https://experienceleague.adobe.com/docs/customer-journey-management/using/reporting/message-tracking.html)
