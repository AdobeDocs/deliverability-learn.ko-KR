---
title: 실시간 블랙홀 목록
description: 스패머가 사용할 수 있는 IP 주소 및 도메인 목록을 유지 관리하는 조직에 대해 알아봅니다.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4155b89f-a636-404c-8951-563c1b4d0289
source-git-commit: e7427d6109f3201affa58decde36294d1631bf5b
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 6%

---

# 실시간 블랙홀 목록

여러 조직에서는 스패머가 사용하는 것으로 알려진 IP 주소 및 도메인의 데이터베이스를 유지 관리합니다. 이러한 사이트를 컨설팅하는 것은 특정 메시지가 스팸으로 거부된 이유를 이해하는 데 유용합니다. 일반적으로 이러한 목록에 잘못 추가된 주소의 제거를 요청할 수 있습니다.

이러한 데이터베이스는 RBL(실시간 블랙홀 목록)이라고 하며 DNS 메커니즘을 통해 확인됩니다. RBL에는 세 가지 유형이 있습니다.

* IP 주소별: 스팸을 전송하거나 스팸을 중계할 IP 주소를 나열합니다.
* 보낸 사람 도메인별: 스팸을 보내거나 잘못 구성된 보낸 사람 도메인(바운스 메일 주소의 전체 도메인)을 나열합니다.
* 웹 도메인별: 스팸 콘텐츠에 포함된 링크 및 이미지의 URL에 있는 도메인(등록자에 등록된 상위 수준 도메인)을 나열합니다. Adobe 솔루션에서 고려할 도메인은 일반적으로 추적에 사용되는 주소입니다.

다음은 가장 널리 사용되는 RBL 목록입니다. 보다 포괄적인 목록이 필요하면 다음을 참조하십시오. [https://www.dnsstuff.com/](https://tools.dnsstuff.com/).

* **스팸하우스**

   을(를) 참조하십시오 [https://www.spamhaus.org/](https://www.spamhaus.org/)

   데이터베이스가 더 중요합니다. 이 리스트에 분류되는 것은 일반적으로 심각한 상황이다. 이러한 경우 즉시 조치를 취하고 상업적 서비스, 전달성 및 경고 메시지를 표시해야 합니다. [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SpamCop**

   을(를) 참조하십시오 [https://www.spamcop.net/](https://www.spamcop.net/)

   그것은 가장 유명한 데이터베이스 중 하나입니다. IP 주소 중 하나가 이 목록에 있으면 일반적으로 SpamCop 사용자가 메시지를 스팸으로 선언했거나 SpamCop 허니팟에 메시지를 보냈다는 의미입니다.

* **URIBL**

   을(를) 참조하십시오 [https://www.uribl.com/](https://www.uribl.com/)

   이 목록은 스팸으로 선언된 메시지에 정기적으로 나타나는 도메인을 식별합니다. 도메인이 이 목록에 표시되는 경우 전달성에 상당한 영향을 줄 수 있습니다. 게재 기능 서비스 및 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 즉시.

* **SURBL**

   을(를) 참조하십시오 [https://surbl.org/](https://surbl.org/)

   SURBL은 스팸에 정기적으로 나타나는 웹 사이트를 식별합니다. 도메인이 이 목록에 표시되는 경우 전달성에 상당한 영향을 줄 수 있습니다. 게재 기능 서비스 및 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 즉시.

* **매니투**

   이것은 IP 목록이며 독일에서 널리 사용되고 있습니다. 을(를) 참조하십시오 [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->
