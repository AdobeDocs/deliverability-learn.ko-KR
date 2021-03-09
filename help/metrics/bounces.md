---
title: 바운스 수
description: 다양한 유형의 바운스에 대해 알아보기
feature: 지표
topics: Deliverability
kt: 7047
thumbnail: kt7047.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: d42a8c3b06308fca0cf3e9db8d634a767fc0cdc6
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 2%

---


# 바운스 수

바운스는 ISP가 백 실패 알림을 제공하는 배달 시도 및 실패의 결과입니다. 바운스 처리 처리는 목록 위생의 중요한 부분입니다. 지정된 이메일이 여러 번 연속적으로 바운스된 후 이 프로세스는 해당 이메일에 대해 억제 플래그를 지정합니다. 억제를 트리거하는 데 필요한 바운스 수와 유형은 시스템마다 다릅니다. 이 프로세스를 수행하면 시스템이 잘못된 이메일 주소를 계속 보내지 못합니다. 바운스는 ISP가 IP 명성을 확인하는 데 사용하는 주요 데이터 중 하나입니다. 이 지표에 주목하는 것은 매우 중요합니다. &quot;배달됨&quot;과 &quot;바운스됨&quot;은 마케팅 메시지 전달을 측정하는 가장 일반적인 방법입니다.배달 비율이 높을수록 좋습니다.

우리는 두 가지 다른 종류의 바운스를 파볼것이다.

## 하드 바운스

하드 바운스는 ISP에서 배달할 수 없는 가입자 주소에 대한 메일링 시도를 결정한 후 생성된 영구 오류입니다. Adobe Campaign 내에서, 배달할 수 없는 것으로 분류되는 하드 바운스가 격리 기관에 추가되므로 다시 시도하지 않을 수 있습니다. 실패 원인을 알 수 없는 경우 하드 바운스가 무시되는 경우가 있습니다.
다음은 하드 바운스의 일반적인 예입니다.

* 주소가 없습니다.
* 계정이 비활성화됨
* 잘못된 구문
* 잘못된 도메인

## 소프트 바운스

소프트 바운스는 ISP가 메일을 배달하기 어려울 때 생성하는 일시적인 실패입니다. 소프트 실패는 성공적인 배달을 시도하기 위해 여러 번(사용자 지정 또는 기본 배달 설정의 사용에 따라 달라짐) 다시 시도합니다. 최대 재시도 횟수를 시도하기 전까지(설정에 따라 다시 달라짐) 계속 소프트 바운스를 지속하는 주소는 격리에 추가되지 않습니다. 소프트 바운스의 몇 가지 일반적인 원인은 다음과 같습니다.

* 사서함 전체
* 이메일 서버 작동 중지 수신 중
* 보낸 사람의 평판 문제

![바운스 유형](../assets/bounce-types.png)

>[!NOTE]
>
>바운스는 잘못된 데이터 소스(하드 바운스)나 ISP(소프트 바운스)의 평판 문제를 강조 표시할 수 있으므로 평판 문제를 나타내는 주요 지표입니다.
>
>소프트 바운스는 종종 이메일 전송의 일부로서 발생하며, 실제 배달 가능 문제로 간주하기 전에 재시도 처리 중에 해결할 수 있어야 합니다. 소프트 바운스 비율이 단일 ISP의 경우 30% 이상이고 24시간 이내에 해결되지 않는 경우 Adobe Campaign 제공 컨설턴트에게 문제를 문의하는 것이 좋습니다.

## 제품별 리소스

**Adobe Campaign Standard**

* [보고서 목록 - 바운스 요약(제품 설명서)](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/bounce-summary.html?lang=en#reporting)
* [배달 오류 이해(제품 설명서)](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html?lang=en#about-delivery-failures)

**Adobe Campaign Classic**

* [배달 오류 이해(제품 설명서)](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html?lang=en#sending-messages)