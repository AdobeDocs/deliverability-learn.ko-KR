---
title: 실시간 블랙홀 목록
description: 회원이 사용할 수 있는 IP 주소 및 도메인 목록을 유지 관리하는 조직에 대해 알아봅니다.
feature: Journey Orchestration용
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# 실시간 블랙홀 목록

일부 조직은 스팸자가 사용한다고 알려진 IP 주소와 도메인의 데이터베이스를 유지 관리합니다. 이러한 사이트를 상담하면 특정 메시지가 스팸으로 거부된 이유를 이해하는 데 유용합니다. 일반적으로 이러한 목록에 잘못 추가된 주소의 제거를 요청할 수 있습니다.

이러한 데이터베이스를 RBL(실시간 블랙홀 목록)이라고 하며 DNS 메커니즘을 통해 이러한 데이터베이스를 확인합니다. RBL에는 다음과 같은 3가지 유형이 있습니다.

* IP 주소별:는 스팸 전송 또는 스팸 재전송 가능성이 있는 IP 주소를 나열합니다.
* 보낸 사람 도메인별:스팸 전송 또는 잘못 구성된 보낸 사람 도메인(바운스 메일 주소의 전체 도메인)을 나열합니다.
* 웹 도메인별:는 링크 URL에 있는 도메인(등록자에 등록된 고급 도메인)과 스팸 컨텐츠에 포함된 이미지를 나열합니다. Adobe 솔루션에서 고려할 도메인은 일반적으로 추적에 사용되는 주소입니다.

다음은 가장 널리 사용되는 RBL 목록입니다. 보다 포괄적인 목록을 보려면 [https://www.dnsstuff.com/](https://tools.dnsstuff.com/)을(를) 참조하십시오.

* **스팜하우스**

   [https://www.spamhaus.org/](https://www.spamhaus.org/)을 참조하십시오.

   데이터베이스가 더 중요합니다. 이 목록에 분류되는 것은 일반적으로 심각한 상황이다. 이러한 경우 즉시 조치를 취하고 상업용 서비스, 전달 가능성 및 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 대해 경고해야 합니다.

* **SpamCop**

   [https://www.spamcop.net/](https://www.spamcop.net/)을 참조하십시오.

   가장 유명한 데이터베이스 중 하나입니다. IP 주소 중 하나가 이 목록에 있는 경우, 이는 일반적으로 SpamCop 사용자가 메시지를 스팸으로 선언했거나 메시지를 SpamHoneycop에 전송했음을 의미합니다.

* **URIBL**

   [https://www.uribl.com/](https://www.uribl.com/)을 참조하십시오.

   이 목록은 스팸으로 선언된 메시지에 정기적으로 나타나는 도메인을 식별합니다. 도메인이 이 목록에 표시되는 경우 배달 능력에 큰 영향을 줄 수 있습니다. 배달 가능 서비스와 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 즉시 알려야 합니다.

* **SURBL**

   [http://www.surbl.org/](http://www.surbl.org/)을 참조하십시오.

   SURBL은 스팸에 정기적으로 나타나는 웹 사이트를 식별합니다. 도메인이 이 목록에 표시되는 경우 배달 능력에 큰 영향을 줄 수 있습니다. 배달 가능 서비스와 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 즉시 알려야 합니다.

* **iX Manitu**

   이것은 IP 목록으로, 독일에서 널리 사용되고 있습니다. [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)을 참조하십시오.

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->
