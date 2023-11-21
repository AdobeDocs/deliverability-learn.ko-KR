---
title: 의 발표된 변경 내용에 대한 지침 [!DNL Google] 및 [!DNL Yahoo]
description: 의 발표된 변경 내용에 대한 지침 [!DNL Google] 및 [!DNL Yahoo]
role: Admin
level: Experienced
doc-type: Article
last-substantial-update: 2023-11-06T00:00:00Z
jira: KT-14320
thumbnail: KT-14320.jpeg
source-git-commit: 0aeff034f6ca2a3dce065240384d1b0e7922fa31
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 0%

---


# 의 발표된 변경 내용에 대한 지침 [!DNL Google] 및 [!DNL Yahoo]

10월 3일에 [!DNL Google] 및 [!DNL Yahoo] 그들은 그들의 블로그를 통해 계획된 변경 사항들을 공동으로 발표했습니다. 이러한 변경 사항은 2024년 2월부터 새로운 요구 사항으로 몇 가지 일반적인 업계 모범 사례를 적용하여 사용자를 안전하게 보호하고 더 나은 이메일 경험을 제공하기 위해 설계되었습니다.

[https://blog.google/products/gmail/gmail-security-authentication-spam-protection/](https://blog.google/products/gmail/gmail-security-authentication-spam-protection/){target="_blank"}

![[!DNL Google] 공지](/help/assets/Gmail.png)

[https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam](https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam){target="_blank"}

![[!DNL Yahoo] 공지](/help/assets/Yahoo.png)

Adobe의 이메일 전달성 전문가는 이러한 블로그 게시물과 모든 링크된 설명서를 읽어봄으로써 번거롭게 하지 않아도 됩니다. 여기 주요 지침이 있습니다.

## 그래서, 정확히 어떤 게 [!DNL Google] 및 [!DNL Yahoo] 뭐하는 거야?

이메일의 세계에는 법적 요구 사항, 실질적 요구 사항 및 일반적인 모범 사례가 있습니다. 법적 요건은 장소마다 매우 다르며 이 주제에서는 다루지 않습니다. 대신, [!DNL Google] 및 [!DNL Yahoo] 는 모범 사례를 취하여 실용적인 요구 사항으로 만들고 있습니다. 항목 없음 [!DNL Google] 및 [!DNL Yahoo] 2월부터 새로운 도입 요구 사항이 시작될 예정이며, 몇 년 동안 모범 사례 권장 사항인 경우가 많았지만, 채택이 업계에서 느리고 고르지 못했습니다. 이 은(는) [!DNL Google] 및 [!DNL Yahoo]&#39; 사용자에게 이메일을 배포하려는 경우(지역 및 업종에 따라 이메일 목록의 상당한 부분을 차지하며, 경우에 따라 70%까지) 이러한 작업을 수행해야 합니다.&#39;라고 말하며 채택 프로세스를 진행하는 데 도움이 되는 방법.

## 세부 사항은 무엇입니까?

Adobe 고객인 경우 요구 사항의 대부분이 이미 설정의 일부이지만 기술적으로 선택 사항인 몇 가지 주요 항목이 있습니다. 또한 2024년 2월 이전에 조직에서 이 항목을 채택하고 올바르게 설정했는지 확인해야 합니다.

## DMARC:

[!DNL Google] 및 [!DNL Yahoo] 은(는) 둘 다 귀하에게 이메일을 전송하는 데 사용하는 모든 도메인에 대한 DMARC 레코드를 보유해야 합니다. 현재 p=reject 또는 p=quarantine 설정이 필요하지 않으므로 일반적으로 &quot;모니터링&quot; 설정이라고 하는 p=none 설정을 완벽하게 사용할 수 있습니다. 이렇게 해도 이메일의 처리 방식은 변경되지 않으며, DMARC 없이 일반적으로 수행하는 작업을 수행합니다. 이 설정을 수행하는 것은 DMARC로 자신을 보호하는 첫 번째 단계이며 이메일 전송을 통한 새로운 이점 또한 제공합니다. [!DNL Google] 및 [!DNL Yahoo] 또한 이메일 에코 시스템 내 어디에나 인증 문제가 있는지 확인하는 데 도움이 될 수 있습니다.
DMARC는 현재 Adobe에서 완전히 지원되지만 필수는 아닙니다. 무료 DMARC 검사기를 사용하여 하위 도메인에 대한 DMARC 설정이 있는지 확인하고, 설정되지 않은 경우 Adobe 지원 팀에 문의하여 해당 설정을 가져오는 방법을 확인하십시오. 또한 DMARC와 구현 방법에 대한 자세한 내용을 확인할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=ko){target="_blank"} for Adobe Campaign and Adobe Journey Optimizer Adobe or [here](https://experienceleague.adobe.com/docs/marketo/using/getting-started-with-marketo/setup/configure-protocols-for-marketo.html){target="_blank"} Marketo Engage.

## 1번 클릭(목록) 구독 취소:

당황하지 마세요. [!DNL Google] 및 [!DNL Yahoo] 보안 봇이 단순히 작업을 수행하거나 실수로 클릭할 수 있는 이메일 본문 또는 바닥글의 구독 취소 링크에 대해 이야기하고 있지 않습니다. 즉, &quot;mailto&quot; 또는 &quot;http/URL&quot; 버전에 대한 목록 구독 취소 헤더 기능이 있습니다. 이것은 다음 내의 함수입니다 [!DNL Yahoo] 및 사용자가 구독 취소를 클릭할 수 있는 Gmail UI입니다. Gmail은 &quot;스팸 보고&quot;를 클릭하는 사용자에게 대신 구독 취소가 의도되었는지 확인하도록 메시지를 표시하기도 합니다. 이렇게 하면 대신 구독 취소로 전환하여(평판에 손상을 주는 컴플레인이) 받는 컴플레인의 수를 줄일 수 있습니다(평판에 손상을 주지 않음).
주의할 점은 다음과 같습니다 [!DNL Google] 및 [!DNL Yahoo] 은 둘 다 &quot;1-Click&quot; 이라는 이름으로 &quot;http/URL&quot; 옵션을 참조하며 이는 의도적인 것입니다. 기술적으로 원래 &quot;http/URL&quot; 옵션을 사용하면 수신자를 웹 사이트로 리디렉션할 수 있습니다. 그것은 의 초점이 아니다 [!DNL Yahoo] 및 [!DNL Google], 두 사람 모두 웹 사이트 대신 HTTPS POST 요청을 통해 구독 취소를 처리하는 데 중점을 둔 업데이트된 RFC8058을 참조하여 &quot;1-클릭&quot;으로 만듭니다.
Marketo Engage의 경우 Adobe이 이미 &quot;mailto&quot; 옵션을 활성화했으며 현재 &quot;http/URL&quot; 옵션을 지원하지 않습니다. 향후 추가 업데이트가 있을 예정입니다.
Adobe Campaign 및 Adobe Journey Optimizer Adobe의 경우 &quot;mailto&quot;와 &quot;1-클릭&quot; 옵션을 모두 사용하는 것이 좋습니다.
목록 구독 취소 구현 방법에 대한 자세한 내용이 필요한 경우 다음을 확인하십시오. [여기] (https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html?lang=en#list-unsubscribe){target="_blank"} for Adobe Campaign Classic, [here] (https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-14778.html?lang=en){target="_blank"} for Adobe Campaign Standard, and [here] (https://experienceleague.adobe.com/docs/journey-optimizer/using/email/email-opt-out.html?lang=en){target="_blank"} Adobe Journey Optimizer의 경우 언제든지 Adobe 고객 지원 팀에 문의하십시오.
목록 구독 취소 헤더에 대한 필요는 트랜잭션 이메일에는 적용되지 않습니다. 구독자가 생성하지 않는 포기한 장바구니 및 유사한 통신과 같은 트리거된 메시지는 다음과 같은 사서함 공급자의 마케팅으로 간주됩니다 [!DNL Google] 및 [!DNL Yahoo] 그리고 그들은 목록-구독 취소가 필요할 것입니다.
![image](https://git.corp.adobe.com/storage/user/38257/files/a2da6bdb-524d-46a7-b765-718c1fe407b0)

## 2일 이내에 구독 취소 처리:

이 모범 사례는 한동안 권장된 모범 사례로, 구독을 취소한 사용자에게 배포하는 모든 이메일은 일반적으로 스팸 불만을 야기하므로 이메일을 더 빨리 보내지 않는 것이 좋습니다. 다시 말하지만, 법적 요건은 경우에 따라 훨씬 더 길어질 수 있지만, [!DNL Google] 및 [!DNL Yahoo] 목록 구독 취소를 통해 사용자의 구독을 취소했으며 3일에도 여전히 이메일을 보내고 있으며, 그러한 발신자가 사용자에게 이메일을 계속 보내는 것을 허용하지 않는다고 명시했음을 알 수 있습니다.
이 2일 요구 사항은 다양한 목록 구독 취소 방법을 통한 모든 구독 취소를 위한 것입니다. 일부 경우(&quot;mailto&quot; 등)에는 Adobe에서 이를 처리함을 의미합니다. Adobe은 요청을 받으면 즉시 2일 제한 내에서 모든 구독 취소 요청을 처리합니다. 다른 경우에는 이러한 작업을 처리 중일 수 있습니다. 이러한 요청을 처리하는 경우 이 2일 타임라인을 충족하도록 나중에 변경해야 할 수 있습니다.

## 고객 불만 비율:

낮은 불만율을 0.2% 미만으로 유지하는 것이 오랜 기간 동안 모범 사례였습니다. [!DNL Google] 은 연장된 기간 동안 0.3%로 바를 높게 설정하지만 0.1% 미만으로 유지하는 것의 이점이 있음을 분명히 명시했습니다. 다음은 이들이 공유한 세부 정보입니다.
* 스팸 비율을 0.10% 미만으로 유지하는 것을 목표로 하십시오.
* 특히 지속 기간 동안 0.30% 이상의 스팸 비율을 피하십시오.
* 낮은 스팸 속도를 유지하면 발신자는 사용자 피드백의 가끔씩 급증하는 것에 더 탄력적으로 대응할 수 있습니다.
* 마찬가지로, 높은 스팸 비율을 유지하면 스팸 분류가 늘어납니다. 스팸 분류에 긍정적으로 반영되도록 스팸 비율 개선에 시간이 걸릴 수 있다.
  [!DNL Yahoo] 그들의 불만 문턱은 또한 0.30%대에 있을 것이라고 말했다.
고객 불만 비율을 모니터링하는 데 도움이 필요하거나 고객 불만 감소 전략에 도움이 필요한 경우 Adobe 전달성 컨설턴트와 상담하거나 아직 전달성 컨설턴트가 없는 경우 계정 팀에 문의하여 전달성 컨설턴트 추가에 대해 알아보십시오.

## 이 경우 마케터로서 나에게 어떤 영향을 미칩니까?

Gmail 및 [!DNL Yahoo] 은 이메일이 스팸 폴더로 도달하거나 차단됩니다(즉, 이메일이 게재되지 않았음을 나타내는 바운스를 MBP에서 다시 얻음).
따라서 Adobe은 위에 설명된 변경 사항을 살펴보고 가능한 한 빨리 준수하도록 권장합니다. 지금이 바로 벤치마킹을 시작할 수 있는 좋은 시기이기도 합니다. [!DNL Yahoo] 및 [!DNL Google] 지표에 대한 중요한 변경 사항이 있는지 확인하려면 2월을 방문하십시오.
도움을 드리고자 합니다. 질문이 있거나 지원이 필요한 경우 Adobe 전달성 컨설턴트와 상담하거나 아직 전달성 컨설턴트가 없는 경우 계정 팀에 문의하여 전달성 컨설턴트를 추가해 주십시오.

## 이 근처에 다른 방법이 있나요?

항상 이러한 문제가 제기되지만 이러한 변경 사항은 최종 사용자에게 의미가 있습니다. [!DNL Google] 및 [!DNL Yahoo]의 플랫폼입니다. 이러한 규칙은 이러한 규칙을 적용하려는 사용자의 기대를 기반으로 합니다. 이러한 변경 사항을 피하려고 하지 말고 한 걸음 물러나서 이러한 변경 사항을 어떻게 수용할 것인지 생각해 보십시오.
