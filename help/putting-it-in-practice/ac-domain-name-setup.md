---
title: 도메인 이름 설정
description: 하위 도메인을 Adobe Campaign에 위임하는 방법을 알아봅니다.
feature: 연습
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '2032'
ht-degree: 1%

---


# 도메인 이름 설정

이 문서에서는 도메인 이름 설정 및 위임에 대한 비즈니스 및 기술 요구 사항에 대해 설명합니다. 사용 중인 Adobe 플랫폼에 대한 웹 구성 요소(랜딩 페이지, 옵트아웃 페이지)를 호스팅하려면 하위 도메인을 보내는 이메일을 선택하고, 필요에 따라 외부 대상 하위 도메인을 선택해야 합니다.

>[!NOTE]
>
>Campaign 컨트롤 패널(베타로 사용 가능)를 사용하여 새 하위 도메인을 설정할 수도 있습니다. [이 섹션](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html#must-read)에서 자세히 알아보십시오.

## 하위 도메인

Adobe을 통해 디지털 마케팅은 브랜드 고객의 참여 마케팅 프로그램을 지원하는 컨텍스트 기반의 엔진이 될 수 있습니다.  이메일은 디지털 마케팅 프로그램의 토대가 됩니다. 하지만 받은 편지함에 도착하는 것이 점점 더 어려워지고 있다.

이메일 캠페인에 대한 하위 도메인을 만들면 다양한 유형의 트래픽(예: 마케팅 및 기업)을 특정 IP 풀과 특정 도메인으로 분리하여, [IP 온난화 프로세스](../../help/additional-resources/increase-reputation-with-ip-warming.md)를 가속화하고 전체적으로 배달 능력을 향상시킬 수 있습니다. 도메인을 공유하면 해당 도메인이 차단되거나 차단 목록에 추가되면 회사 메일 배달에 영향을 줄 수 있습니다. 그러나 이메일 마케팅 커뮤니케이션과 관련된 도메인의 평판 문제나 블록은 이메일 흐름에 영향을 미칩니다.  여러 메일 스트림의 보낸 사람 또는 &#39;보낸 사람&#39; 주소로 기본 도메인을 사용하는 경우에도 이메일 인증이 중단되어 메시지가 차단되거나 스팸 폴더에 저장될 수 있습니다.

### 위임

도메인 이름 위임은 도메인 이름의 소유자를 허용하는 메서드입니다(기술적으로:DNS 영역)을 사용하여 세분화(즉,하위 영역이라고 할 수 있는 DNS 영역을 다른 엔티티에 추가합니다. 기본적으로 고객이 &quot;example.com&quot; 영역을 처리하는 경우 하위 영역 &quot;marketing.example.com&quot;을 Adobe Campaign에 위임할 수 있습니다.

즉, Adobe Campaign의 DNS 서버는 최상위 도메인이 아닌 해당 영역에만 모든 권한을 가집니다. Adobe Campaign의 DNS 서버는 &quot;t.marketing.example.com&quot; 자체와 같이 해당 영역의 도메인 이름에 대한 쿼리에 대한 신뢰할 수 있는 답변을 제공하지만 &quot;www.example.com&quot;은 제공하지 않습니다.

Adobe Campaign에서 사용할 수 있도록 하위 도메인을 위임함으로써 클라이언트는 Adobe에 의존하여 이메일 마케팅 전송 도메인의 업계 표준 제공 요구 사항을 충족하는 데 필요한 DNS 인프라를 유지 관리하면서 내부 이메일 도메인에 대한 DNS를 계속 유지 관리하고 제어할 수 있습니다.  하위 도메인 위임을 통해 다음을 수행할 수 있습니다.

도메인 이름의 DNS 별칭을 사용하여 브랜드 이미지를 유지할 클라이언트
이메일 전송 중 전달 능력을 완벽하게 최적화하기 위해 모든 기술 모범 사례를 자동으로 구현하는 Adobe

## DNS 설정 옵션

클라우드 기반의 관리 서비스를 제공하기 위해 Adobe은 클라이언트가 Adobe Campaign을 배포할 때 하위 도메인 위임을 사용하도록 적극 권장합니다.  그러나 Adobe은 DNS를 구성하기 위한 대체 옵션(CNAME 설정)을 고객에게 제공합니다.

| 옵션 | 설명 | Adobe 책임 | 클라이언트 책임 |
|--- |------- |--- |--- |
| Adobe Campaign에 대한 하위 도메인 위임 | 클라이언트는 하위 도메인(email.example.com)을 Adobe에 위임합니다. 이 시나리오에서 Adobe은 이메일 캠페인을 제공, 렌더링 및 추적하는 데 필요한 모든 DNS 측면을 제어하고 유지 관리함으로써 캠페인을 관리 서비스로 제공할 수 있습니다. | Adobe Campaign에 필요한 하위 도메인 및 모든 DNS 레코드를 완벽하게 관리합니다. | Adobe에 대한 하위 도메인의 적절한 위임 |
| CNAME 사용 | 클라이언트는 하위 도메인을 만들고 CNAME을 사용하여 Adobe 특정 레코드를 가리킵니다.  이 설정을 사용하는 경우 Adobe와 고객이 DNS 유지 관리를 공동으로 수행합니다. | Adobe Campaign에 필요한 DNS 레코드 관리 | Adobe Campaign에 필요한 하위 도메인의 생성 및 제어 및 CNAME 레코드 생성/관리 |

## 필요한 DNS 레코드

| 레코드 유형 | 용도 | 레코드/컨텐츠 예 |
|--- |--- |--- |
| MX | 수신 메시지에 대한 메일 서버 지정 | <i>email.example.com</i></br><i>10 inbound.email.example.com</i> |
| SPF(TXT) | 보낸 사람 정책 프레임워크 | <i>email.example.com</i></br>&quot;v=spf1 redirect=__spf.campaign.adobe.com&quot; |
| DKIM(TXT) | 도메인 키 식별된 메일 | <i>client._domainkey.email.example.com</i></br>&quot;v=DKIM1;k=rsa;&quot; &quot;DKIMPUBLICKEY HERE&quot; |
| DMARC(TXT) | 도메인 기반 메시지 인증 | 보고 및 적합성 | _dmarc.email.example.com</br>&quot;v=DMARC1;p=none;rua=mailto:mailauth-reports@myemail.com&quot; |
| 호스트 레코드 (A) | 페이지, 이미지 호스팅 및 추적 링크, 모든 전송 도메인 | m.email.example.com IN 123.111.100.99</br>t.email.example.com IN 123.111.100.98</br>email.example.com IN 123.111.100.97 |
| DNS 역방향(PTR) | 클라이언트 IP 주소를 클라이언트 브랜드 호스트 이름으로 매핑합니다. | 18.101.100.192.in-addr.arpa 도메인 이름 포인터 r18.email.example.com |
| CNAME | 다른 도메인 이름에 별칭을 제공합니다. | t1.email.example.com은 | t1.email.example.campaign.adobe.com |

## 설정 요구 사항

### 하위 도메인 위임

이를 위해서는 클라이언트가 DNS 서버에 하위 도메인을 만들고 이 하위 도메인의 이름 서버를 Adobe에서 유지 관리하는 서버로 정의해야 합니다.  예를 들어 기본 도메인 이름이 &quot;example.com&quot;이고 이메일 전달을 위해 &quot;marketing.example.com&quot;의 관리를 Adobe에 위임하려는 클라이언트는 다음 유형 레코드를 DNS에 추가하려면 이 위임을 구체화해야 합니다.

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

도메인 이름의 위임은 이 도메인이 Adobe Campaign 플랫폼을 통해 이메일 전달에만 사용되므로 다른 방법(예: 다른 이메일 인프라에서 이메일 보내기)에 사용할 수 없음을 의미합니다.

설정 프로세스 동안 Adobe은 도메인으로 돌아오는 리바운드 이메일을 관리하고 처리하기 위해 수신 전자 메일 인프라에 도메인이 연결되었는지 확인합니다(MX 유형 DNS 레코드 구성).

### CNAME 사용

클라이언트가 Adobe에 하위 도메인을 위임하지 않고 CNAME을 사용하도록 선택하면 설정 단계 동안 Adobe은 클라이언트 DNS 서버에 배치할 레코드를 제공하며 Adobe Campaign DNS 서버에서 해당 값을 구성합니다.

## 배포용 일반 요구 사항

새로운 엔터프라이즈 마케팅 솔루션을 구현할 때 외부에서 만나는 구성 요소에 대한 요구 사항이 있습니다.  여기에는 랜딩 페이지 및 웹 양식 호스팅, 추적할 링크 및 웹 페이지 설정, 미러 페이지 표시, 옵트아웃 페이지 구성 등이 포함됩니다.

이러한 요구 사항은 Adobe과 고객이 모두 호스팅하는 구성 요소를 통해 관리되지만, 해당 요구 사항에는 이메일 수신자가 볼 수 있는 URL이 포함됩니다.  기본 기술 솔루션 또는 호스팅 제공업체를 나타내는 URL이 없는 것을 방지하기 위해 하위 도메인을 설정하여 이메일 수신자에게 이 항목을 투명하게 만들 수 있습니다.  예를 들어 http://www.customer.com/과 같은 URL을 볼 때 도메인은 &quot;www.customer.com&quot;입니다.  이 도메인의 하위 도메인은 &quot;www&quot;입니다.

### 하위 도메인 요구 사항

Adobe Campaign 애플리케이션에서 브랜드 URL(미러 페이지 및 추적 URL)에 사용할 하위 도메인을 결정합니다.  또한 이메일 배달의 각 하위 도메인에 대해 &quot;보낸 사람 주소&quot;, &quot;보낸 사람 이름&quot; 및 &quot;회신 주소&quot;를 결정할 수 있습니다.

아래 표를 완성하십시오. 첫 번째 줄이 예일 뿐입니다.

| 하위 도메인 | 보낸 사람 주소 | 이름 | 회신 주소 |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | 고객 | customercare@customer.com |
| </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* &quot;회신 주소&quot; 필드의 목적은 수신자가 &quot;보낸 사람 주소&quot;와 다른 주소로 회신하도록 하는 것입니다.  필수 필드는 아니지만 Adobe은 &quot;회신 주소&quot;가 유효하고 모니터링되는 사서함에 연결되도록 적극 권장합니다.  이 사서함은 고객이 호스트해야 합니다.  e-메일을 읽고 응답하는 지원 사서함(예: customercare@customer.com)일 수 있습니다.
>* 고객이 &quot;회신 주소&quot;를 선택하지 않은 경우 기본 주소는 항상 `<tenant>-<type>-<env>@<subdomain>`입니다.
>* 이렇게 &quot;회신 주소&quot;를 설정하면 응답이 모니터링되지 않는 사서함으로 전송됩니다.
>* Adobe Campaign에서 이메일을 보낼 때 &quot;보낸 사람 주소&quot; 사서함은 모니터링되지 않으며 마케팅 사용자가 이 사서함에 액세스할 수 없습니다. Adobe Campaign은 이 사서함에서 받은 자동 회신 또는 자동 전달 기능도 제공하지 않습니다.
>* 캠페인 보낸 사람/보낸 사람 주소 및 오류 주소는 &quot;남용&quot; 또는 &quot;포스트마스터&quot;일 수 없습니다.


## 하위 도메인 위임

Adobe Campaign 플랫폼에 사용하기 위해 선택한 하위 도메인은 4개의 NS(이름 서버) 레코드를 만들어 위임해야 합니다.  이렇게 하면 하위 도메인을 Adobe에 제대로 위임할 수 있습니다.  다음은 하위 도메인 위임 및 각 DNS 명령의 예입니다.  위임할 하위 도메인으로 &#39;email.customer.com&#39;을 대체하십시오.  하위 도메인은 고유해야 하며 다른 당사자가 이미 사용 중일 수 없습니다(예: 기존 ESP 또는 MSP).

| 위임된 하위 도메인 | DNS 지침 |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.cacampaign.adobe.com을 참조하십시오.  </br> `<subdomain>` NS b.ns.cacampaign.adobe.com을 참조하십시오.  </br> `<subdomain>` NS c.ns.cacampaign.adobe.com을 참조하십시오.  </br> `<subdomain>` NS d.ns.cacampaign.adobe.com을 참조하십시오. |

## 추적, 미러 페이지, 리소스

하위 도메인을 보내는 이메일이 Adobe Campaign에 적절하게 위임되면, Adobe TechOps 팀은 추적 및 페이지를 독립적으로 미러링하기 위해 두 개 이상의 하위 수준 도메인을 만듭니다.

| 유형 | 도메인 |
|--- |--- |
| 페이지 미러 | m.`<subdomain>` |
| 추적 | t.`<subdomain>` |
| 리소스 | res`<subdomain>` |

## 클라우드 배포(선택 사항)

이는 Adobe Campaign Classic이 Adobe에 의해 클라우드에서 완전히 호스팅되는 경우에만 적용됩니다.  선택적 구성입니다.

개발되는 모든 설문 조사, 웹 양식 및 랜딩 페이지는 클라우드에서 완벽하게 호스팅되는 Adobe Campaign을 통해 관리됩니다.  필요한 경우 도구 내의 모든 웹 구성 요소에 사용할 추가 하위 도메인을 Adobe(예: web.customer.com)에 위임할 수 있습니다.  하위 도메인은 고유해야 하며 다른 사용자(예: 기존 ESP 또는 MSP)에 사용할 수 없습니다.

| 위임된 하위 도메인 | DNS 지침 |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.cacampaign.adobe.com을 참조하십시오.</br>`<subdomain>` NS b.ns.cacampaign.adobe.com을 참조하십시오.</br>`<subdomain>` NS c.ns.cacampaign.adobe.com을 참조하십시오.</br>`<subdomain>` NS d.ns.cacampaign.adobe.com을 참조하십시오. |

>[!NOTE]
>
>기본적으로 도구의 모든 웹 구성 요소는 이메일에 사용되도록 위임된 초기 하위 도메인을 사용합니다.

## 클라우드 메시지 배포(선택 사항)

Adobe Campaign Classic 마케팅 인스턴스가 고객에게 사내 호스팅되는 경우 고객이 추가 기술 구성을 수행해야 합니다.

개발할 모든 설문 조사, 웹 양식 및 랜딩 페이지는 수신자 레코드가 존재하는 Adobe Campaign 마케팅 인스턴스를 통해 관리됩니다.

Adobe Campaign 마케팅 인스턴스에서 호스팅하는 외부에서 직접 대면하는 웹 구성 요소를 배포하려면 추가 CNAME DNS 구성이 필요합니다.  이렇게 하면 웹 구성 요소(예: web.customer.com)가 인터넷에 공개적으로 액세스하고 고객의 도메인으로 브랜드화할 수 있습니다.

또한 이러한 웹 구성 요소를 호스팅하는 Adobe Campaign 마케팅 인스턴스에 대한 액세스를 허용하도록 방화벽을 구성해야 합니다(포트 80 또는 443).

**모범 사례 Recommendations:**

웹 구성 요소를 호스팅하는 하위 도메인은 고객에게 표시되므로 적절하게 브랜드화하고 수동으로 입력해야 하는 것처럼 기억하기 쉬운 것이어야 합니다. 예를 들어,https://web.customer.com을 참조하십시오.
보안 페이지(HTTPS)에서 양식을 호스팅해야 하는 경우 아래 설명된 바와 같이 추가 기술 구성이 필요합니다.

| 위임된 하위 도메인 | DNS 지침 |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME  `<internal customer server>` |

## 렌더링된 서비스

이러한 위임 후, Adobe에 의해 지정된 인프라에서는 위임 또는 CNAME 기반 전송 도메인에 대해 다음 서비스가 수행되도록 합니다.

* postmaster@ 및 inbox 남용@ 만들기
* 위임된 도메인에 대한 피드백 루프 설정
* 요청 시 Adobe은 지정된 대로 DMARC 레코드도 구성합니다. 배달성 컨설턴트는 장기 DMARC 정책 설계 및 전송 도메인을 계획하는 데 도움을 줄 수 있습니다.
Adobe에 의해 설정된 매개 변수는 위임을 완료하고 Adobe에 의해 확인되는 시점에서만 유효하며 기능성이 유지됩니다.  모든 Adobe Campaign Cloud 오퍼에는 표준으로 도메인 이름 위임이 포함됩니다.

## 청구 및 구현 조건

* 초기 계약 및 선택된 패키지의 유형에 따라, 이 초기 위임 이후 표준으로 포함된 위임 외에 다른 위임 포함,
* 이러한 위임 외에도 추가 위임 비용이 청구되고
* 이러한 추가 사원에게 대한 청구 방법은 초기 계약에 명시된 대로 추가 월별 비용으로 제공됩니다.

CLIENT가 Adobe Campaign 도구를 통해 배달을 위한 전용 관련 도메인 이름을 선택하고 관련 문서에 자세히 설명된 위임 사전 요구 사항이 올바르게 구현되는 경우에 이러한 위임이 허용됩니다.

## 서비스 중단

언제든지 클라이언트는 위임 서비스를 더 이상 이용할 수 없고 필요한 DNS 구성을 직접 사용할 수 있도록 서면 요구를 할 수 있습니다.

이러한 문제가 발생하면 Adobe은 CLIENT에 도메인 위임 모드가 아닌 모드로 돌아가는 데 필요한 서비스 일 수를 자세히 설명하는 견적을 제공합니다.

고객이 상기에 명시된 약속을 이행하지 않을 경우, Adobe은 전술한 산출률(Deliverability Rate)의 참여에 대한 책임을 면합니다.

Marketing Cloud 서비스를 종료하면 도메인 위임이 자동으로 종료되고 Adobe에 따라 해당 도메인에 대한 DNS 유지 관리가 수행됩니다.

## Campaign 컨트롤 패널을 사용하여 하위 도메인 모니터링

인스턴스에 대해 하위 도메인이 구성되면 Campaign 컨트롤 패널을 사용하여 해당 하위 도메인을 모니터링할 수 있습니다.

이렇게 하면 Adobe Campaign에 위임한 모든 하위 도메인을 볼 수 있을 뿐만 아니라 SSL 인증서 갱신을 요청할 수 있습니다.

자세한 내용은 [전용 설명서](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html#subdomains-and-certificates)를 참조하십시오.

>[!NOTE]
>
>[제어 패널](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html) 은 Adobe Managed Services를 사용하는 고객에게만 제공됩니다.