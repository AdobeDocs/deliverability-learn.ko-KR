---
title: Verizon Media Group(Yahoo, AOL, Verizon 등)
description: '[!DNL Verizon Media Group]은(는) 일반적으로 대부분의 B2C 목록에서 상위 3개 도메인 중 하나입니다. 일반적으로 평판 문제가 발생하면 메일을 줄이거나 대량 발송하기 때문에 다소 독특하게 동작합니다.'
topics: Deliverability
jira: KT-5320
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: 43e6d3cb-23c3-4076-8026-a1a08e76bd1b
TQID: https://experienceleague.adobe.com/ycELLXdqC1E3EIxywp-I1HWnSyWayRHcwkNOzmzSBvY
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 289
ht-degree: 2%

---

# [!DNL Verizon Media Group]&#x200B;(Yahoo, AOL, Verizon 등)

[!DNL Verizon Media Group]은(는) 일반적으로 대부분의 B2C 목록에서 상위 3개 도메인 중 하나입니다. 일반적으로 평판 문제가 발생하면 메일을 줄이거나 대량 발송하기 때문에 다소 독특하게 동작합니다.

다음은 몇 가지 주요 기능입니다.

## 중요한 데이터

[!DNL Verizon Media Group]&#x200B;(VMG)은 콘텐츠 및 URL 필터링과 스팸 컴플레인을 혼합하여 고유한 스팸 필터를 빌드하고 유지 관리합니다. Gmail과 함께 ISP를 초기에 채택하여 IP 주소 및 도메인별로 이메일을 필터링합니다.

## 어떤 데이터를 사용할 수 있습니까

VMG는 발신자에게 컴플레인 정보를 피드백하는 데 사용되는 FBL을 가지고 있다. 그들은 또한 미래에 더 많은 데이터를 추가하는 것을 탐구하고 있다.

## 보낸 사람의 신뢰도

보낸 사람의 신뢰도는 IP 주소, 도메인 및 보낸 사람 주소의 조합으로 구성됩니다. 신뢰도는 컴플레인, 스팸 트랩, 비활성 또는 잘못된 주소 및 참여를 포함한 기존 구성 요소를 사용하여 계산됩니다. VMG는 스팸을 방지하기 위해 벌크 폴링과 함께 속도 제한(조절이라고도 함)을 사용합니다. 내부 필터링 시스템을 PBL, SBL 및 XBL을 포함한 일부 [!DNL Spamhaus] 블랙리스트로 보완하여 사용자를 보호합니다.

## Insights

VMG는 최근 오래된 비활성 이메일 주소에 대한 유지 관리 기간이 정기적으로 유지됩니다. 즉, 잘못된 주소 바운스가 크게 급증하여 단기간 동안 게재율에 영향을 줄 수 있습니다. 또한 보낸 사람으로부터 잘못된 주소가 반송되는 비율이 높다는 것에 민감하므로, 이로 인해 획득 또는 참여 정책을 강화해야 할 필요가 있음을 나타냅니다. 보낸 사람은 종종 약 1%의 잘못된 주소에서 부정적인 영향을 받을 수 있습니다.
