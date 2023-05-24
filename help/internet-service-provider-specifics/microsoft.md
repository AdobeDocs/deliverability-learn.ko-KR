---
title: Microsoft(Hotmail, Outlook, Windows Live 등)
description: Microsoft은 일반적으로 목록의 구성에 따라 2위 또는 3위의 공급업체이며 다른 ISP와 약간 다른 트래픽을 처리합니다.
topics: Deliverability
kt: 5319
doc-type: article
activity: understand
team: TM
exl-id: d706cb90-828a-4ab3-8f93-c9bd71553d63
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 2%

---

# [!DNL Microsoft] ([!DNL Hotmail], [!DNL Outlook], [!DNL Windows Live]등)

[!DNL Microsoft] 는 일반적으로 목록의 구성에 따라 두 번째 또는 세 번째로 큰 공급자이며 다른 ISP와 약간 다른 트래픽을 처리합니다.

다음은 몇 가지 주요 기능입니다.

## 중요한 데이터

[!DNL Microsoft] 는 보낸 사람의 신뢰도, 컴플레인, 사용자 참여 및 피드백을 위해 폴링하는 신뢰할 수 있는 사용자 그룹(보낸 사람의 신뢰도 데이터 또는 SRD라고도 함)에 중점을 둡니다.

## 어떤 데이터를 사용할 수 있습니까

[!DNL Microsoft]의 독점적 발신자 보고 도구, [!DNL Smart Network Data Services] (SNDS)를 사용하면 전송 중인 메일 수와 허용되는 메일 수에 대한 지표와 컴플레인 및 스팸 트랩을 볼 수 있습니다. 공유된 데이터는 샘플이며 정확한 숫자를 반영하지 않지만 그 방법을 가장 잘 나타냅니다 [!DNL Microsoft] 을(를) 보낸 사람으로 표시합니다. [!DNL Microsoft] 는 신뢰할 수 있는 사용자 그룹에 대한 정보를 공개적으로 제공하지 않지만, 해당 데이터는 [!DNL Return Path Certification] 프로그램 추가 요금.

## 보낸 사람의 신뢰도

[!DNL Microsoft] 는 일반적으로 평판 평가 및 필터링 의사 결정에서 IP를 전송하는 데 중점을 둡니다. 전송 도메인 기능도 적극적으로 확장하고 있습니다. 둘 다 주로 컴플레인 및 스팸 트랩과 같은 전통적인 평판 인플루언서에 의해 주도됩니다. 전달성은 또한 특정 양적 및 질적 프로그램 요구 사항이 있는 Return Path Certification 프로그램의 영향을 크게 받을 수 있습니다.

## Insights

[!DNL Microsoft] 는 모든 수신 도메인을 결합하여 전송 평판을 설정하고 추적합니다. 여기에는 다음이 포함됩니다 [!DNL Hotmail], [!DNL Outlook], MSN [!DNL Windows Live]회사 Office 365에서 호스팅하는 모든 전자 메일 등을 포함합니다. [!DNL Microsoft] 볼륨 변동에 특히 민감할 수 있으므로 볼륨 기반 갑작스러운 변경을 허용하는 것과 대조적으로 대규모 전송에서 램프 업 및 램프 다운하는 특정 전략을 적용하는 것이 좋습니다.

[!DNL Microsoft] 는 또한 IP 준비 시작 며칠 동안 특히 엄격하며, 일반적으로 대부분의 메일이 처음에 필터링됩니다. 대부분의 ISP는 유죄가 입증될 때까지 발신자를 무죄로 간주합니다. [!DNL Microsoft] 그 반대야. 그리고 네가 결백하다는 것을 증명할 때까지 너를 유죄라고 생각해.
