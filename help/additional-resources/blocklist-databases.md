---
title: 실시간 블랙홀 목록
description: 관리자가 사용할 수 있는 IP 주소 및 도메인 목록을 관리하는 조직에 대해 알아봅니다.
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

일부 조직에서는 스파머가 사용한다고 알려진 IP 주소와 도메인의 데이터베이스를 유지 관리합니다. 이러한 사이트를 컨설팅하면 특정 메시지가 스팸으로 거부된 이유를 이해하는 데 유용합니다. 일반적으로 이러한 목록에 잘못 추가된 주소의 제거를 요청할 수 있습니다.

이러한 데이터베이스는 RBL(실시간 블랙홀 목록)이라고 하며 DNS 메커니즘을 통해 상담됩니다. 다음 세 가지 유형의 RBL이 있습니다.

* IP 주소별: 는 스팸을 보내거나 스팸을 보낼 가능성이 있는 IP 주소를 나열합니다.
* 보낸 사람 도메인: 스팸 또는 잘못 구성된 발신자 도메인(바운스 메일 주소의 전체 도메인)을 나열합니다.
* 웹 도메인별: 는 스팸 컨텐츠에 포함된 링크 및 이미지의 URL에 있는 도메인(등록자와 함께 등록된 상위 수준 도메인)을 나열합니다. Adobe 솔루션에서 고려할 도메인은 일반적으로 추적에 사용되는 주소입니다.

다음은 가장 널리 사용되는 RBL 목록입니다. 보다 포괄적인 목록이 필요하면 [https://www.dnsstuff.com/](https://tools.dnsstuff.com/).

* **스팜하우스**

   을(를) 참조하십시오. [https://www.spamhaus.org/](https://www.spamhaus.org/)

   데이터베이스가 더 중요합니다. 이 목록에 분류된 것은 일반적으로 심각한 상황이다. 이러한 경우 즉시 조치를 취해 상업 서비스, 게재 가능성 및 경고 메시지를 보내야 합니다 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SpamCop**

   을(를) 참조하십시오. [https://www.spamcop.net/](https://www.spamcop.net/)

   가장 유명한 데이터베이스 중 하나입니다. IP 주소 중 하나가 이 목록에 배치되면 일반적으로 SpamCop 사용자가 메시지를 스팸으로 선언했거나 메시지를 SpamHonepot에 보냈음을 의미합니다.

* **URIBL**

   을(를) 참조하십시오. [https://www.uribl.com/](https://www.uribl.com/)

   이 목록은 스팸으로 선언된 메시지에 정기적으로 나타나는 도메인을 식별합니다. 도메인이 이 목록에 표시되면 게재 기능에 큰 영향을 줄 수 있습니다. 게재 가능성 서비스 및 [고객 지원 Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 즉시 작동합니다.

* **SURBL**

   을(를) 참조하십시오. [https://surbl.org/](https://surbl.org/)

   SURBL은 스팸에 정기적으로 나타나는 웹 사이트를 식별합니다. 도메인이 이 목록에 표시되면 게재 기능에 큰 영향을 줄 수 있습니다. 게재 가능성 서비스 및 [고객 지원 Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 즉시 작동합니다.

* **iX 마니투**

   이것은 IP 목록이며 독일에서 널리 사용되고 있습니다. 을(를) 참조하십시오. [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->
