---
title: Microsoft(Hotmail, Outlook, Windows Live 등)
description: Microsoft은 일반적으로 목록의 구성에 따라 두 번째 또는 세 번째로 큰 공급자이며, 다른 ISP와 약간 다른 트래픽을 처리합니다.
topics: Deliverability
kt: 5319
doc-type: article
activity: understand
team: TM
exl-id: d706cb90-828a-4ab3-8f93-c9bd71553d63
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---

# [!DNL Microsoft] ([!DNL Hotmail], [!DNL Outlook], [!DNL Windows Live]등)

[!DNL Microsoft] 는 일반적으로 목록의 구성에 따라 두 번째 또는 세 번째로 큰 공급자이며, 다른 ISP와 약간 다른 트래픽을 처리합니다.

다음은 몇 가지 주요 사항입니다.

## 중요한 데이터

[!DNL Microsoft] 보낸 사람의 평판, 불만, 사용자 참여 및 피드백을 위해 폴링하는 신뢰할 수 있는 사용자 그룹(보낸 사람 평판 데이터 또는 SRD라고도 함)에 중점을 둡니다.

## 사용 가능한 데이터 제공

[!DNL Microsoft]&#39;독점 발신자 보고 도구&#39; [!DNL Smart Network Data Services] (SNDS)를 사용하면 전송 중인 메일 양 및 수신 허용 횟수에 대한 지표와 불만 및 스팸 트랩을 볼 수 있습니다. 공유된 데이터는 샘플이며 정확한 숫자를 반영하지 않지만, 해당 데이터가 어떻게 표시되는지 가장 잘 나타냅니다 [!DNL Microsoft] 보낸 사람으로 봅니다. [!DNL Microsoft] 는 신뢰할 수 있는 사용자 그룹에 대한 정보를 공개적으로 제공하지 않지만, 이 데이터는 [!DNL Return Path Certification] 추가 비용 프로그램.

## 보낸 사람 평판

[!DNL Microsoft] 은 일반적으로 평판 평가 및 필터링 결정에서 IP를 전송하는 데 중점을 두고 있습니다. 또한 전송 도메인 기능을 확장하는 데에도 적극적으로 노력하고 있습니다. 이들은 불만과 스팸 트랩과 같은 전통적인 명성에 영향을 미치는 영향 담당자들에 의해 크게 좌우된다. 게재 능력은 Return Path Certification 프로그램의 영향을 많이 받을 수 있으며, 이 프로그램은 특정 정량적이고 정성적인 프로그램 요구 사항을 가지고 있습니다.

## Insights

[!DNL Microsoft] 는 모든 수신 도메인을 결합하여 전송 평판을 설정하고 추적합니다. 여기에는 다음이 포함됩니다 [!DNL Hotmail], [!DNL Outlook], MSN, [!DNL Windows Live]기타 사항 및 기업 Office 365에서 호스팅된 전자 메일 [!DNL Microsoft] 볼륨 변화에 특히 민감할 수 있으므로 대량 전송에서 상하로 이동할 특정 전략을 적용하여 볼륨 기반 갑작스런 변경을 허용하는 것과 대조적으로 고려해 보십시오.

[!DNL Microsoft] 또한 IP 온난화의 초기 기간 동안 특히 엄격하며 일반적으로 대부분의 메일이 처음에 필터링된다는 것을 의미합니다. 대부분의 ISP는 유죄가 증명될 때까지 보낸 사람을 무죄로 간주합니다. [!DNL Microsoft] 그것은 그 반대이고, 자신이 무죄라는 것을 증명하기 전까지 여러분을 유죄로 간주합니다.
