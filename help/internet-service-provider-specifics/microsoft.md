---
title: Microsoft(Hotmail, Outlook, Windows Live 등)
description: Microsoft은 일반적으로 목록의 구성에 따라 2위 또는 3위의 공급업체이며 다른 ISP와 약간 다른 트래픽을 처리합니다.
topics: Deliverability
jira: KT-5319
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: d706cb90-828a-4ab3-8f93-c9bd71553d63
TQID: https://experienceleague.adobe.com/pbp5vbHUIHSL9zL9gQf4LpIhEYZI1umEesy3czbJx-4
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: ea90ebee-5c84-42d9-8b21-006bdabc95a3
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 335
ht-degree: 1%

---

# [!DNL Microsoft]&#x200B;([!DNL Hotmail], [!DNL Outlook], [!DNL Windows Live] 등)

[!DNL Microsoft]은(는) 일반적으로 목록의 구성에 따라 두 번째 또는 세 번째로 큰 공급자이며 다른 ISP와 약간 다른 트래픽을 처리합니다.

다음은 몇 가지 주요 기능입니다.

## 중요한 데이터

[!DNL Microsoft]은(는) 보낸 사람의 신뢰도, 컴플레인, 사용자 참여 및 피드백을 위해 폴링하는 신뢰할 수 있는 사용자 그룹(보낸 사람의 신뢰도 데이터 또는 SRD라고도 함)에 중점을 둡니다.

## 어떤 데이터를 사용할 수 있습니까

[!DNL Microsoft]의 고유 발신자 보고 도구인 [!DNL Smart Network Data Services]&#x200B;(SNDS)을 사용하면 전송 중인 메일 수와 허용되는 메일 수와 컴플레인 및 스팸 트랩에 대한 지표를 볼 수 있습니다. 공유된 데이터는 샘플이며 정확한 숫자를 반영하지 않지만 [!DNL Microsoft]이(가) 보낸 사람으로 귀하를 보는 방식을 가장 잘 나타냅니다. [!DNL Microsoft]은(는) 신뢰할 수 있는 사용자 그룹에 대한 정보를 공개적으로 제공하지 않지만 해당 데이터는 [!DNL Return Path Certification] 프로그램을 통해 추가 비용으로 사용할 수 있습니다.

## 보낸 사람의 신뢰도

[!DNL Microsoft]은(는) 일반적으로 평판 평가 및 필터링 결정에 IP를 전송하는 데 중점을 둡니다. 전송 도메인 기능도 적극적으로 확장하고 있습니다. 둘 다 주로 컴플레인 및 스팸 트랩과 같은 전통적인 평판 인플루언서에 의해 주도됩니다. 전달성은 또한 특정 양적 및 질적 프로그램 요구 사항이 있는 Return Path Certification 프로그램의 영향을 크게 받을 수 있습니다.

## Insights

[!DNL Microsoft]은(는) 수신 도메인을 모두 결합하여 전송 평판을 설정하고 추적합니다. 여기에는 [!DNL Hotmail], [!DNL Outlook], MSN, [!DNL Windows Live] 등과 회사 Office 365 호스팅 전자 메일이 포함됩니다. [!DNL Microsoft]은(는) 볼륨 변화에 특히 민감할 수 있으므로 볼륨 기반 갑작스러운 변경을 허용하는 것과 반대로 큰 전송에서 램프 업 및 램프 다운하는 특정 전략을 적용하는 것이 좋습니다.

또한 [!DNL Microsoft]은(는) IP 준비 초기 기간 동안 특히 엄격하며, 이는 일반적으로 대부분의 메일이 처음에 필터링됨을 의미합니다. 대부분의 ISP는 유죄가 입증될 때까지 발신자를 무죄로 간주합니다. [!DNL Microsoft]은(는) 반대이며 자신의 무죄를 입증할 때까지 유죄로 간주합니다.
