---
title: 게재 기능 문제 해결
description: 게재 가능성 문제를 식별하고 해결하는 방법을 알아봅니다.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4cc85124-e7e4-4cd5-99a9-23d2d8cf08fe
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 0%

---

# 게재 기능 문제 해결 {#troubleshooting}

다음은 게재 가능성 문제를 식별하고 해결하는 데 도움이 되는 몇 가지 모범 사례입니다.

## 게재 가능성 문제 식별 {#identify-deliverability-issue}

가능한 문제를 식별하려면 [해당 페이지](/help/ongoing-monitoring.md) 주의를 끌지도 모른다.

<!--
Mailing or campaign metrics: unsubscribe, abuse complaint and/or bounce rates are higher than usual.
Subscriber activity: opens, clicks and/or transactions are lower than usual.
Seed accounts show filtered or non-delivered mailings.
-->

## 잠재적 원인 가설 {#potential-causes}

게재 가능성 문제의 가능한 원인을 식별하려면 다음 질문을 스스로에게 하십시오.

* 목록 세그먼테이션에서 최근 변경 사항이 있습니까?
* 새로운 데이터 소스를 얻었습니까?
* 내가 실수로 격리 파일을 보냈나요?
* 메시지 내용 때문에 문제가 발생할 수 있습니까?
* 따뜻한 IP를 유지할 만큼 자주 메일을 보내나요?
* 활동/참여별 또는 전체 파일을 전송하여 메일링을 세그먼트화합니까?
* 최신성 측면에서 내 파일에서 &#39;안전&#39; 세그먼트는 무엇입니까?
* 안전한 것으로 정의되지 않은 세그먼트에 대해 재활성화 및 재확인 전략이 적용됩니까?

## 문제 해결 {#address-issue}

### 컴플레인

[불만](/help/metrics/complaints.md) 은 받은 편지함에서 해당 단추를 눌러 이메일을 스팸으로 보고하는 가입자에 의해 정의됩니다.

불만사항으로 인해 게재 문제가 발생한 경우:
* 수신자가 불평하는 이유를 파악해야 합니다.
* 구독 취소 링크를 이메일 맨 위로 이동하는 것을 고려해 볼 수도 있습니다. 이를 통해 구독자는 스팸 버튼에 대해 불평하지 않고 구독을 취소할 수 있습니다.

보낸 사람은 자신의 정보로부터 많은 정보를 얻을 수 있습니다 [피드백 루프](/help/transition-process/infrastructure.md#feedback-loops) 불만:
* 데이터를 버킷하고 옵트인 소스, 주소가 구독한 시간 또는 특정 행동 인구 통계학적 요소와 같은 것에서 패턴을 찾는 것이 중요합니다.
* 불만 사항은 종종 파일 내에 위험한 데이터 소스 또는 세그먼트를 식별할 수 있습니다. 위험성은 불평할 가능성이 가장 큰 것으로 정의되는데, 이는 명성에 해를 줄 수 있고, 결과적으로 받은 편지함에도 피해를 줍니다.

더 이상 이메일을 받지 않으려는 가입자의 불만 사항도 있습니다.
* 이는 종종 과메시징이나, 구독자가 메시지에 대해 인식하는 것, 메시지를 예상하지 않았거나, 옵트인을 취소하지 않기 때문일 수 있습니다.
* 또한 모든 수집 포인트가 명확하고 획득 포인트에 사전 체크 박스가 없는지 확인하기 위해 감사를 실행하는 것이 중요합니다.
* 또한 구독자가 톤 설정을 위해 옵트인하면 환영 이메일을 전송하고 구독자가 사용자로부터 이메일을 받는 빈도를 설명해야 합니다.

### 데이터 유효성

**하드 바운스 수** 에 보낼 때 발생합니다 **배달할 수 없는 주소** ISP에서 주소는 다음과 같은 많은 이유로 배달할 수 없습니다.
* 철자가 잘못된 주소입니다. 이 문제는 실시간 데이터 유효성 검사 서비스를 통해 해결하거나 마케팅 이메일을 해당 주소로 보내기 전에 확인 옵트인을 필요로 할 수 있습니다.
* 잘못된 목록 또는 데이터 소스입니다. 새 소스에서 온 경우 주소가 수집된 방식을 검토하고 권한이 있는지 확인하십시오.
* 한 번 활성화되었지만 비활성 기간 후 닫되었거나 종료된 주소로 메일을 보냅니다.

### 참여

불만 사항과 데이터 유효성 외에도, ISP는 그 어느 때보다 집중하기 시작했습니다 **긍정적인 참여** 게재의 결정을 내리는 데 사용됩니다. 구독자가 이메일을 열지 또는 읽지 않고 삭제할지 여부를 확인하고 있습니다. 보낸 사람과 이 데이터를 공유하지 않으므로 사용할 수 있는 정보를 사용하고 열기/클릭/트랜잭션을 계약으로 변환해야 합니다.

지속적인 평판 유지 관리의 일환으로 구독자가 목록에 얼마나 참여하는지 이해하고 **최신성 위험 계층** 각 파일의 구독자에 대해 최신성은 마지막 열기/클릭/트랜잭션 또는 등록 날짜로 정의됩니다. 이 시간 프레임은 세로로 다를 수 있습니다. 다음을 수행하십시오.

1. 각 세로에 대해 활성(&#39;안전&#39;) 세그먼트를 결정합니다. 일반적으로 지난 3~6개월 내에 활성 상태인 가입자입니다.
1. 빈도를 비활성 상태로 줄입니다.
1. 만들기 [재참여](/help/additional-resources/re-engagement.md) 적절한 위험 요소를 위한 시리즈 일반적으로 6~9개월 동안 계약이 없습니다.
1. 더 높은 위험 요소를 위한 재확인 캠페인을 개발하십시오. 일반적으로 9~12개월 동안 이메일에 참여하지 않은 구독자입니다.
1. 마지막으로, 드롭다운 규칙을 설정하고 &#39;x&#39;개월 내에 이메일을 열지 않은 구독자를 제거합니다. 일반적으로 12개월 이상을 사용하는 것이 좋지만 판매 및 구매 주기에 따라 다를 수 있습니다.
