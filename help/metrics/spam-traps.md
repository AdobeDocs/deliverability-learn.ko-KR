---
title: 스팸 트랩
description: 다양한 유형의 스팸 트랩에 대해 자세히 알아보십시오.
feature: 지표
topics: Deliverability
kt: 7050
thumbnail: kt7050.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 550821608eb7049f739a156536dd31b6b2faa2fa
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 2%

---


# 스팸 트랩

스팸 트랩은 부정 발송자 또는 이메일 모범 사례를 따르지 않는 사람의 메일을 식별하는 데 도움이 됩니다. 스팸성 트랩 이메일 주소는 일반적으로 공개되지 않으며, 식별이 거의 불가능합니다. 스팸성 트랩으로 이메일을 전달하면 트랩 유형과 ISP에 따라 심각도가 달라질 수 있습니다. 다음 섹션에서 다양한 유형의 스팸 트랩에 대해 자세히 알아보십시오.

## 재활용

재활용 스팸 트랩은 한 번 유효했지만 더 이상 사용되지 않는 주소입니다. 목록을 최대한 깔끔하게 유지하는 가장 중요한 방법은 전체 목록에 이메일을 정기적으로 보내고 바운스된 이메일을 적절히 억제하는 것입니다. 이렇게 하면 중단된 이메일 주소를 격리하고 더 이상 사용하지 못하도록 할 수 있습니다.

어떤 경우에는 주소를 30일 이내에 재활용할 수 있다. 정기적으로 비활동적인 사용자를 억제할 수 있을 뿐만 아니라, 규칙적으로 보내는 것은 좋은 목록 위생의 중요한 측면이다. **재참여** 캠페인은 일반적으로 정교한 이메일 마케팅 프로그램의 일부입니다. 이 캠페인 스타일을 사용하면 발신자가 더 이상 이메일로 전송되지 않을 사용자를 다시 확보할 수 있습니다.

## 오타

오타 스팸 트랩은 철자 오류 또는 잘못된 정보가 포함된 주소입니다. 이러한 문제는 종종 Gmail과 같은 주요 도메인의 알려진 철자 오류가 발생하는 경우가 있습니다(예:gmial은 일반적인 오타). ISP와 기타 차단 목록에 추가하다 연산자는 스팸 게시자를 식별하고 발신자의 상태를 측정하기 위해 스팸 트랩으로 사용되는 알려진 잘못된 도메인을 등록합니다. 오타 스팸 트랩을 방지하는 가장 좋은 방법은 목록 컬렉션에 **이중 옵트인 프로세스**&#x200B;를 사용하는 것입니다.

## 본래 그대로의 상태

본래 스팸 트랩은 최종 사용자가 없고 최종 사용자가 없는 주소입니다. 스팸성 이메일을 식별하기 위해 만들어진 주소입니다. 이는 거의 식별할 수 없고 목록에서 정리하는 데 많은 노력이 필요하므로 가장 영향력 있는 유형의 스팸 트랩입니다. 대부분의 차단 목록은 본래 스팸 트랩을 사용하여 신뢰할 수 없는 전송자를 나열합니다. 광범위한 마케팅 이메일 목록을 감염시키지 않는 본래 스팸 트랩을 피하는 유일한 방법은 목록 수집을 위해 **이중 옵트인 프로세스**&#x200B;를 이용하는 것입니다.

## Journey Orchestration용

* [이 섹션](/help/additional-resources/all-about-spam-traps.md)에서 스팸 트랩을 식별하고 피하는 방법에 대해 자세히 알아보십시오.
* [이 섹션](/help/additional-resources/re-engagement.md)에서 재참여 전략을 통해 제공 능력을 향상시키는 방법에 대해 자세히 알아보십시오.

## 제품별 리소스

**Adobe Campaign Classic**

* [SpamAssassin](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/deliverability-management/spamassassin.html?lang=en#using-spamassassin)
* [이중 옵트인 구독 양식 만들기](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=en#create-a-subscription--form-with-double-opt-in)

**Adobe Campaign Standard**

* [이메일 및 스팸 방지 분석 미리 보기](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/designing-content/email-designer/preview-your-email.html#designing-content)
* [이중 옵트인 프로세스](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=en#communication-channels)

