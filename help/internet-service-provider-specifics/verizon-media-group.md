---
title: Verizon Media Group(Yahoo, AOL, Verizon 등)
description: '[!DNL Verizon Media Group] 는 일반적으로 대부분의 B2C 목록에 대한 상위 3개 도메인 중 하나입니다. 평판 문제가 발생하면 일반적으로 쓰라리거나 대량 메일을 보내므로 그들은 약간 고유하게 행동한다.'
topics: Deliverability
kt: 5320
doc-type: article
activity: understand
team: TM
exl-id: 43e6d3cb-23c3-4076-8026-a1a08e76bd1b
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 2%

---

# [!DNL Verizon Media Group] (Yahoo, AOL, Verizon 등)

[!DNL Verizon Media Group] 는 일반적으로 대부분의 B2C 목록에 대한 상위 3개 도메인 중 하나입니다. 평판 문제가 발생하면 일반적으로 쓰라리거나 대량 메일을 보내므로 그들은 약간 고유하게 행동한다.

다음은 몇 가지 주요 사항입니다.

## 중요한 데이터

[!DNL Verizon Media Group] (VMG)는 컨텐츠와 URL 필터링 및 스팸 불만 사항을 혼합하여 자체 전용 스팸 필터를 구축 및 유지 관리합니다. Gmail과 함께 IP 주소뿐만 아니라 도메인별로 이메일을 필터링하는 초기 도입 ISP 중 하나입니다.

## 사용 가능한 데이터 제공

VMG에는 수신 거부 정보를 보낸 사람에게 다시 제공하는 데 사용되는 FBL이 있습니다. 그들은 또한 미래에 더 많은 데이터를 추가하는 것을 탐구하고 있습니다.

## 보낸 사람 평판

보낸 사람의 평판은 IP 주소, 도메인 및 보낸 사람 주소의 조합으로 구성됩니다. 불만, 스팸 트랩, 비활성 또는 잘못된 형식의 주소, 참여 등 기존 구성 요소를 사용하여 평판이 계산됩니다. VMG는 스팸으로부터 방어하기 위해 일괄 폴딩과 함께 비율 제한(전송률 조절이라고도 함)을 사용합니다. 일부 기능을 사용하여 내부 필터링 시스템을 보완합니다 [!DNL Spamhaus] 사용자를 보호하기 위해 PBL, SBL 및 XBL을 포함한 블랙 리스트

## Insights

VMG는 최근 사용되지 않는 오래된 이메일 주소에 대해 정기적으로 유지 보수 기간을 제공합니다. 즉, 짧은 시간 동안 배달된 비율에 영향을 줄 수 있는 잘못된 주소 바운스의 상당한 증가를 관찰하는 것이 일반적입니다. 또한, 발신자의 잘못된 주소 반송 비율이 높은 것에 민감하며, 이는 획득 또는 참여 정책을 강화할 필요성을 나타냅니다. 보낸 사람은 대개 잘못된 주소 약 1%에서 부정적인 영향을 받을 수 있습니다.
