---
title: 전달성 문제 해결
description: 게재 가능성 문제를 식별하고 해결하는 방법을 알아봅니다.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4cc85124-e7e4-4cd5-99a9-23d2d8cf08fe
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 0%

---

# 전달성 문제 해결 {#troubleshooting}

다음은 게재 가능성 문제를 식별하고 해결하는 데 도움이 되는 몇 가지 모범 사례입니다.

## 전달성 문제 식별 {#identify-deliverability-issue}

가능한 문제를 확인하기 위해 [해당 페이지](/help/ongoing-monitoring.md)에 나열된 요소에 주의를 기울일 수 있습니다.

<!--
Mailing or campaign metrics: unsubscribe, abuse complaint and/or bounce rates are higher than usual.
Subscriber activity: opens, clicks and/or transactions are lower than usual.
Seed accounts show filtered or non-delivered mailings.
-->

## 잠재적 원인 가설 {#potential-causes}

전달성 문제에 대한 가능한 원인을 파악하려면 다음 질문을 하십시오.

* 목록 세분화에 최근 변경 사항이 있습니까?
* 새로운 데이터 소스를 획득했습니까?
* 제가 실수로 격리 파일을 보냈나요?
* 내 메시지 내용 때문에 문제가 발생할 수 있습니까?
* 따뜻한 IP를 유지할 수 있을 만큼 자주 메일을 보내나요?
* 활동/참여별로 메일링을 세그먼트화하고 있습니까, 아니면 전체 파일을 보내고 있습니까?
* 최근 사용 시 내 파일의 &#39;안전한&#39; 세그먼트는 무엇입니까?
* 안전한 것으로 정의되지 않은 세그먼트에 대한 재활성화 및 재확인 전략이 있습니까?

## 문제 해결 {#address-issue}

### 컴플레인

[컴플레인](/help/metrics/complaints.md)은(는) 받은 편지함에서 해당 단추를 눌러 이메일을 스팸으로 보고하는 구독자에 의해 정의됩니다.

게재 문제가 고객 불만으로 인해 발생한 경우:
* 수신자가 불평하는 이유를 파악해야 합니다.
* 구독 취소 링크를 이메일 맨 위로 이동하는 것도 고려해 볼 수 있습니다. 이렇게 하면 구독자가 스팸 버튼을 신고하는 대신 구독을 취소할 수 있습니다.

보낸 사람은 [피드백 루프](/help/transition-process/infrastructure.md#feedback-loops) 컴플레인으로 인해 풍부한 정보를 수집할 수 있습니다.
* 데이터를 버킷팅하고 옵트인 소스, 주소가 구독한 기간 또는 특정 행동 인구 통계와 같은 항목의 패턴을 찾는 것이 중요합니다.
* 컴플레인은 종종 파일 내에서 위험한 데이터 소스 또는 세그먼트를 식별할 수 있습니다. 위험 요소는 불평 가능성이 가장 높은 것으로 정의되고, 이는 평판을 손상시킬 수 있으며, 결과적으로 받은 편지함 비율을 손상시킬 수 있다.

불만은 또한 더 이상 이메일을 받고 싶어하지 않는 구독자들로부터 생겨났다:
* 이는 종종 오버메시징, 메시지에 대한 구독자의 인식, 메시지를 예상하지 못하거나 옵트인을 회수하지 못하기 때문일 수 있습니다.
* 또한 모든 수집 지점이 명확하고, 획득 지점에 사전 선택된 상자가 없는지 확인하기 위해 감사를 실행하는 것이 중요합니다.
* 구독자가 신호음을 설정하고 구독자가 귀하로부터 이메일을 받을 것으로 예상되는 빈도를 설명하도록 옵트인할 때도 환영 이메일을 보내야 합니다.

### 데이터 유효성

ISP의 **전달할 수 없는 주소**&#x200B;로 보낼 때 **하드 바운스**&#x200B;가 발생합니다. 다음과 같은 여러 가지 이유로 주소를 전달할 수 없습니다.
* 철자가 잘못된 주소. 이 문제는 실시간 데이터 유효성 검사 서비스를 사용하거나 해당 주소로 마케팅 이메일을 보내기 전에 확인된 옵트인을 요구하여 해결할 수 있습니다.
* 잘못된 목록 또는 데이터 소스. 새 소스에서 가져온 경우에는 주소 수집 방법을 검토하고 권한이 있는지 확인하십시오.
* 한 번에 활성 상태였지만 비활성 기간 후에 닫히거나 종료된 주소로 메일링.

### 참여

컴플레인 및 데이터 유효성 검사 외에도 ISP는 게재 결정을 내리는 데 **긍정적인 참여**&#x200B;에 더욱 집중하고 있습니다. 구독자가 이메일을 여는지, 읽지 않고 삭제하는지 여부를 검토 중입니다. 발신자와 이 데이터를 공유하지 않으므로 제공된 정보를 사용하고 열기/클릭/거래를 계약으로 변환해야 합니다.

지속적인 신뢰도 유지 관리의 일환으로, 구독자의 목록 참여도를 파악하고 각 파일의 구독자에 대해 **최신성 위험 계층 구조**&#x200B;를 개발하는 것이 중요합니다. 최신성은 마지막 열기/클릭/트랜잭션 또는 등록 일자로 정의됩니다. 이 시간 프레임은 수직에 따라 다를 수 있습니다. 방법은 다음과 같습니다.

1. 각 수직에 대한 활성(&#39;안전한&#39;) 세그먼트를 결정합니다. 이는 일반적으로 지난 3~6개월 내에 활성 상태인 구독자입니다.
1. 비활성화 빈도를 줄입니다.
1. 중간 위험 수준의 비활성화를 위해 [재참여](/help/additional-resources/re-engagement.md) 시리즈를 만드십시오. 일반적으로 6~9개월의 약정이 없는 기간입니다.
1. 더 높은 위험 요소를 위한 재확인 캠페인을 개발합니다. 일반적으로 9~12개월 동안 이메일에 관여하지 않은 구독자입니다.
1. 마지막으로, 드롭오프 규칙을 설정하고 &#39;x&#39;개월 동안 이메일을 열지 않은 구독자를 제거합니다. 일반적으로 12개월 이상이 권장되지만, 이는 판매 및 구매 주기에 따라 다를 수 있습니다.
