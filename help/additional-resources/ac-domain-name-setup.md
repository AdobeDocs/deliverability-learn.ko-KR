---
title: 도메인 이름 설정
description: 하위 도메인을 Adobe Campaign에 위임하는 방법을 알아봅니다.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4d52d197-d20e-450c-bfcf-e4541c474be4
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '2028'
ht-degree: 2%

---

# 도메인 이름 설정

이 문서에서는 도메인 이름 설정 및 위임에 대한 비즈니스 및 기술 요구 사항에 대해 설명합니다. 사용 중인 Adobe 플랫폼에 대한 웹 구성 요소(랜딩 페이지, 옵트아웃 페이지)를 호스팅하려면 전자 메일 전송 하위 도메인 및 선택적으로 외부에서 제공되는 하위 도메인을 선택해야 합니다.

>[!NOTE]
>
>Campaign 컨트롤 패널(베타로 사용 가능)를 사용하여 새 하위 도메인을 설정할 수도 있습니다. 자세한 내용은 [이 섹션](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html#must-read)을 참조하십시오.

## 하위 도메인

Adobe을 통해 디지털 마케팅은 브랜드의 고객 참여 마케팅 프로그램을 지원하는 컨텍스트 엔진이 될 수 있습니다.  이메일은 디지털 마케팅 프로그램의 기초로 유지됩니다. 그러나 받은 편지함에 도달하는 것이 그 어느 때보다 더 어려워졌다.

이메일 캠페인용 하위 도메인을 만들면 브랜드의 다양한 트래픽 유형(예: 마케팅과 기업)을 특정 IP 풀 및 특정 도메인으로 분리하여 [IP 준비 프로세스](../../help/additional-resources/increase-reputation-with-ip-warming.md)를 빠르게 수행하고 전체적으로 게재 능력을 향상시킬 수 있습니다. 도메인을 공유하는데 도메인을 차단하거나 차단 목록에 추가하면 회사 메일 게재에 영향을 줄 수 있습니다. 그러나 이메일 마케팅 커뮤니케이션과 관련된 도메인의 평판 문제 또는 블록은 해당 이메일 흐름에 영향을 줍니다.  기본 도메인을 발신자로 사용하거나 여러 메일 스트림에 대한 &#39;보낸 사람&#39; 주소로 사용하면 이메일 인증이 중단되어 메시지가 스팸 폴더에 저장되거나 차단될 수 있습니다.

### 위임

도메인 이름 위임은 도메인 이름의 소유자를 허용하는 메서드입니다(기술적으로 DNS 영역)에서 하위 집합을 위임(기술적 의미상: 하위 영역이라고 할 수 있는 DNS 영역을 다른 엔터티에 추가합니다. 기본적으로 고객이 &quot;example.com&quot; 영역을 처리하는 경우 하위 영역 &quot;marketing.example.com&quot;을 Adobe Campaign에 위임할 수 있습니다.

즉, Adobe Campaign의 DNS 서버는 최상위 도메인이 아니라 해당 영역에만 전체 권한을 갖습니다. Adobe Campaign의 DNS 서버는 &quot;t.marketing.example.com&quot; 자체와 같이 해당 영역의 도메인 이름에 대한 질의에 대한 권위 있는 답변을 제공하지만 &quot;www.example.com&quot; 은 제공하지 않습니다.

Adobe Campaign에서 사용할 하위 도메인을 위임함으로써 클라이언트는 Adobe을 사용하여 전자 메일 마케팅 전송 도메인에 대한 업계 표준 게재 기능 요구 사항을 충족하는 데 필요한 DNS 인프라를 유지 관리하는 동시에 내부 전자 메일 도메인에 대한 DNS를 유지 및 제어할 수 있습니다.  하위 도메인을 위임하면 다음을 수행할 수 있습니다.

클라이언트는 도메인 이름과 함께 DNS 별칭을 사용하여 브랜드 이미지를 유지합니다
전자 메일 전송 중에 게재 능력을 완전히 최적화하기 위해 모든 기술 모범 사례를 자체적으로 구현하는 Adobe

## DNS 설정 옵션

클라우드 기반 관리 서비스를 제공하기 위해 Adobe은 Adobe Campaign을 배포할 때 클라이언트가 하위 도메인 위임을 사용하도록 강력히 권장합니다.  그러나 Adobe은 DNS 구성을 위한 대체 옵션인 CNAME 설정을 클라이언트에 제공합니다.

| 옵션 | 설명 | Adobe 책임 | 클라이언트 권한 |
|--- |------- |--- |--- |
| Adobe Campaign에 하위 도메인 위임 | 클라이언트가 Adobe에 하위 도메인(email.example.com)을 위임합니다. 이 시나리오에서 Adobe은 이메일 캠페인 게재, 렌더링 및 추적에 필요한 DNS의 모든 측면을 제어하고 유지 관리하여 Campaign을 관리 서비스로 제공할 수 있습니다. | Adobe Campaign에 필요한 하위 도메인 및 모든 DNS 레코드를 완벽하게 관리합니다. | Adobe에 하위 도메인의 적절한 위임 |
| CNAME 사용 | 클라이언트는 하위 도메인을 만들고 CNAME을 사용하여 Adobe 관련 레코드를 가리킵니다.  이 설정을 사용하는 경우 Adobe와 고객이 DNS 유지 관리를 공동으로 수행합니다. | Adobe Campaign에 필요한 DNS 레코드 관리 | Adobe Campaign에 필요한 하위 도메인을 만들고 제어하고 CNAME 레코드를 만들고/관리합니다. |

## 필수 DNS 레코드

| 레코드 유형 | 용도 | 레코드/컨텐츠 예 |
|--- |--- |--- |
| MX | 수신 메시지의 메일 서버 지정 | <i>email.example.com</i></br><i>10 inbound.email.example.com</i> |
| SPF(TXT) | 보낸 사람 정책 프레임워크 | <i>email.example.com</i></br> &quot;v=spf1 redirect=__spf.campaign.adobe.com&quot; |
| DKIM(TXT) | 식별된 메일 도메인 키 | <i>클라이언트._domainkey.email.example.com</i></br>&quot;v=DKIM1; k=rsa;&quot; &quot;DKIMPUBLICKEY HERE&quot; |
| DMARC(TXT) | 도메인 기반 메시지 인증 | 보고 및 적합성 | _dmarc.email.example.com</br>&quot;v=DMARC1; p=없음; rua=mailto:mailauth-reports@myemail.com&quot; |
| 호스트 레코드 (A) | 미러 페이지, 이미지 호스팅 및 추적 링크, 모든 전송 도메인 | m.email.example.com 123.111.100.99</br>t.email.example.com IN 123.111.100.98</br>email.example.com IN A 123.111.100.97 |
| 역방향 DNS(PTR) | 클라이언트 IP 주소를 클라이언트 브랜드 호스트 이름에 매핑합니다 | 18.101.100.192.in-addr.arpa 도메인 이름 포인터 r18.email.example.com |
| CNAME | 다른 도메인 이름에 별칭을 제공합니다. | t1.email.example.com의 별칭은 | t1.email.example.campaign.adobe.com |

## 설치 요구 사항

### 하위 도메인 위임

이렇게 하려면 클라이언트가 DNS 서버에서 하위 도메인을 만들고 이 하위 도메인의 이름 서버를 Adobe에서 유지 관리하는 도메인으로 정의해야 합니다.  예를 들어 기본 도메인 이름이 &quot;example.com&quot;이고 전자 메일 게재에 대한 Adobe에 &quot;marketing.example.com&quot;의 관리를 위임하려는 클라이언트는 다음 유형 레코드를 해당 DNS에 추가하려면 이 위임을 구체화해야 합니다.

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

도메인 이름을 위임하는 것은 이 도메인이 Adobe Campaign 플랫폼을 통해 이메일을 전달하는 데 전용되므로 다른 수단(예: 다른 이메일 인프라에서 이메일 보내기)에 사용할 수 없음을 의미합니다.

설정 프로세스 중에 Adobe은 이러한 도메인(MX 유형 DNS 레코드 구성)으로 돌아오는 리바운드 이메일을 관리하고 처리하기 위해 Adobe 수신 전자 메일 인프라에 도메인이 연결되었는지 확인합니다.

### CNAME 사용

클라이언트가 Adobe에 하위 도메인을 위임하지 않고 CNAME을 사용하도록 선택하는 경우 설정 단계 동안 Adobe은 클라이언트 DNS 서버에 배치할 레코드를 제공하고 Adobe Campaign DNS 서버에서 해당 값을 구성합니다.

## 배포에 대한 일반 요구 사항

새 엔터프라이즈 마케팅 솔루션을 구현할 때 외부에서 제공되는 구성 요소에 대한 요구 사항이 있습니다.  여기에는 랜딩 페이지 및 웹 양식 호스팅, 추적할 링크 및 웹 페이지 설정, 미러 페이지 표시 및 옵트아웃 페이지 구성 등이 포함됩니다.

이러한 요구 사항은 Adobe과 고객이 모두 호스팅하는 구성 요소를 통해 관리되지만 전자 메일의 수신자가 볼 수 있는 URL이 포함됩니다.  기본 기술 솔루션 또는 호스팅 공급자를 나타내는 URL이 없는 것을 방지하기 위해 하위 도메인을 설정하여 전자 메일 수신자에게 이를 투명하게 할 수 있습니다.  예를 들어 http://www.customer.com/과 같은 URL을 볼 때 도메인은 &quot;www.customer.com&quot;입니다.  이 페이지의 하위 도메인은 &quot;www&quot;입니다.

### 하위 도메인 요구 사항

Adobe Campaign 애플리케이션에서 브랜드 URL(미러 페이지 및 추적 URL)에 사용할 하위 도메인을 결정합니다.  또한 이메일 게재의 각 하위 도메인에 대해 &quot;보낸 사람 주소&quot;, &quot;보낸 사람 이름&quot; 및 &quot;회신 주소&quot;를 결정할 수 있습니다.

아래 표를 완성합니다. 첫 번째 줄은 예일 뿐입니다.

| 하위 도메인 | 보낸 사람 주소 | 이름 | 회신 주소 |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | Customer | customercare@customer.com |
| </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* 회신 주소 필드의 목적은 수신자가 &quot;보낸 사람 주소&quot;가 아닌 다른 주소로 회신하도록 하는 것입니다.  필수 필드는 아니지만 Adobe은 &quot;회신 주소&quot;가 유효하고 모니터링되는 사서함에 연결되도록 강력히 권장합니다.  이 사서함은 고객이 호스트해야 합니다.  예를 들어 customercare@customer.com에서 이메일을 읽고 응답하는 지원 사서함일 수 있습니다.
>* 고객이 &quot;회신 주소&quot;를 선택하지 않은 경우 기본 주소는 항상 `<tenant>-<type>-<env>@<subdomain>`입니다.
>* 이렇게 &quot;회신 주소&quot;가 설정되면 응답이 모니터링되지 않는 사서함으로 전송됩니다.
>* Adobe Campaign에서 전자 메일을 보낼 때 &quot;보낸 사람 주소&quot; 사서함은 모니터링되지 않으며 마케팅 사용자가 이 사서함에 액세스할 수 없습니다. 또한 Adobe Campaign은 이 사서함에서 받은 자동 회신 또는 자동 전송 전자 메일을 제공할 수 없습니다.
>* 캠페인 보낸 사람/보낸 사람 주소 및 오류 주소는 &quot;남용&quot; 또는 &quot;postmaster&quot;일 수 없습니다.


## 하위 도메인 위임

Adobe Campaign 플랫폼에 사용하기 위해 선택한 하위 도메인은 4개의 NS(이름 서버) 레코드를 만들어 위임해야 합니다.  이렇게 하면 하위 도메인을 Adobe에 제대로 위임할 수 있습니다.  다음은 하위 도메인 위임 및 각 DNS 명령의 예입니다.  위임할 하위 도메인으로 &#39;email.customer.com&#39;을 대체하십시오.  하위 도메인은 고유해야 하며 다른 사용자(예: 기존 ESP 또는 MSP)가 이미 사용 중이면 안 됩니다.

| 위임된 하위 도메인 | DNS 지침 |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com  </br> `<subdomain>` NS b.ns.campaign.adobe.com  </br> `<subdomain>` NS c.ns.campaign.adobe.com  </br> `<subdomain>` NS d.ns.campaign.adobe.com |

## 추적, 미러 페이지, 리소스

전자 메일 전송 하위 도메인이 Adobe Campaign에 올바르게 위임되면 Adobe TechOps 팀에서 추적 및 미러 페이지를 독립적으로 관리할 두 개 이상의 하위 수준 도메인을 만듭니다.

| 유형 | 도메인 |
|--- |--- |
| 미러 페이지 | m.`<subdomain>` |
| 추적 | t.`<subdomain>` |
| 리소스 | res`<subdomain>` |

## 클라우드 배포(선택 사항)

이 기능은 Adobe Campaign Classic이 Adobe에 의해 클라우드에서 완전히 호스팅되는 경우에만 적용됩니다.  이는 선택적 구성입니다.

개발할 모든 설문 조사, 웹 양식 및 랜딩 페이지는 클라우드에서 완전히 호스팅되는 Adobe Campaign을 통해 관리됩니다.  필요한 경우 도구 내의 웹 구성 요소에 사용할 추가 하위 도메인을 Adobe(예: web.customer.com)에 위임할 수 있습니다.  하위 도메인은 고유해야 하며 다른 사용자(예: 기존 ESP 또는 MSP)가 사용할 수 없습니다.

| 위임된 하위 도메인 | DNS 지침 |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com</br>`<subdomain>` NS b.ns.campaign.adobe.com</br>`<subdomain>` NS c.ns.campaign.adobe.com</br>`<subdomain>` NS d.ns.campaign.adobe.com |

>[!NOTE]
>
>기본적으로 도구의 모든 웹 구성 요소는 이메일에 사용되도록 위임된 초기 하위 도메인을 사용합니다.

## 클라우드 메시징 배포(선택 사항)

Adobe Campaign Classic 마케팅 인스턴스가 고객에게 전후에 호스팅되는 경우 고객이 추가 기술 구성을 수행해야 합니다.

개발할 모든 설문 조사, 웹 양식 및 랜딩 페이지는 수신자 레코드가 존재하는 Adobe Campaign 마케팅 인스턴스를 통해 관리됩니다.

Adobe Campaign 마케팅 인스턴스에서 호스팅하는 외부에서 보는 웹 구성 요소를 배포하려면 추가 CNAME DNS 구성이 필요합니다.  이렇게 하면 웹 구성 요소(예: web.customer.com)가 인터넷에 공개적으로 액세스하고 고객 도메인으로 브랜딩될 수 있습니다.

이러한 웹 구성 요소를 호스팅하는 Adobe Campaign 마케팅 인스턴스(포트 80 또는 443)에 액세스할 수 있도록 방화벽을 구성해야 합니다.

**우수 사례 Recommendations:**

웹 구성 요소를 호스팅하는 하위 도메인은 고객에게 표시되므로 제대로 브랜드를 지정하고 수동으로 입력해야 할 수 있으므로 쉽게 기억하십시오. 예: https://web.customer.com
보안 페이지(HTTPS)에서 양식을 호스팅해야 하는 경우 아래 설명된 대로 추가 기술 구성이 필요합니다.

| 위임된 하위 도메인 | DNS 지침 |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME  `<internal customer server>` |

## 렌더링된 서비스

이러한 위임 이후에, Adobe에 의해 배치된 인프라에서는 위임된 도메인 또는 CNAME 기반 전송 도메인에 대해 다음 서비스가 수행되도록 합니다.

* Postmaster@ 만들기 및 Inbox 남용@
* 위임된 도메인에 대한 피드백 루프 설정
* 요청 시 Adobe은 지정된 대로 DMARC 레코드도 구성합니다. 게재 기능 컨설턴트는 장기 DMARC 정책 및 전송 도메인을 위한 계획을 수립하는 데 도움을 줄 수 있습니다.
Adobe에서 설정한 매개 변수는 위임을 완료한 다음 Adobe에서 확인한 후에만 유효하며 작동합니다.  모든 Adobe Campaign Cloud 오퍼에는 표준으로 도메인 이름 위임이 포함됩니다.

## 청구 및 구현 조건

* 초기 계약 및 선택된 패키지의 유형에 따라 이 초기 위임 이외의 표준으로 포함된 다른 위임도 포함될 수 있습니다.
* 포함된 위임 외에 추가 위임은 청구됩니다
* 이러한 추가 위임에 대한 청구 방법은 초기 계약에 명시된 대로 추가 월별 비용으로 제공됩니다.

이 위임은 CLIENT가 Adobe Campaign 도구를 통해 게재 전용인 관련 도메인 이름을 선택하고 관련 문서에 자세히 설명된 위임 사전 요구 사항이 올바르게 구현되도록 하는 경우 수락됩니다.

## 서비스 중단

언제든지 클라이언트가 위임 서비스를 더 이상 사용하지 않고 필요한 DNS 구성을 직접 수행할 수 있도록 서면 요청을 수행할 수 있습니다.

이러한 상황이 발생할 경우 Adobe은 비 도메인 위임 모드로 돌아가는 데 필요한 서비스 일 수를 자세히 설명하는 예측을 고객에게 제공합니다.

고객이 위에서 정한 약속을 준수하지 않을 경우 Adobe은 위의 게재능력율에 대한 책임을 면합니다.

Marketing Cloud 서비스를 종료하면 자동으로 도메인 위임이 종료되고 Adobe에 의한 해당 도메인에 대한 DNS 유지 관리가 종료됩니다.

## Campaign 컨트롤 패널을 사용하여 하위 도메인 모니터링

인스턴스에 대해 하위 도메인이 구성되면 Campaign 컨트롤 패널을 사용하여 모니터링할 수 있습니다.

이렇게 하면 Adobe Campaign에 위임한 모든 하위 도메인을 확인하고 SSL 인증서 갱신을 요청할 수 있습니다.

자세한 내용은 [전용 설명서](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html#subdomains-and-certificates)를 참조하십시오.

>[!NOTE]
>
>[Adobe ](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko) Managed Services를 사용하는 고객만 컨트롤 패널을 사용할 수 있습니다.
