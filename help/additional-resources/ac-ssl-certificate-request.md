---
title: SSL 인증서 요청 프로세스
description: Adobe에게 위임한 하위 도메인에 SSL 인증서를 설치하는 방법을 배웁니다.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 8a78abd3-afba-49a7-a2ae-8b2c75326749
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '2265'
ht-degree: 1%

---

# SSL 인증서 요청 프로세스

전자 메일 전송을 위해 Adobe에 도메인을 위임하면( [도메인 이름 설정](/help/additional-resources/ac-domain-name-setup.md)). Adobe은 특정 기능을 위해 특정 하위 도메인을 만들고 사용합니다.

예를 들어, *email.example.com* 전자 메일 전송을 위해 Adobe은 다음과 같은 하위 도메인을 만듭니다.
* *t.email.example.com* - 추적 링크:
* *m.email.example.com* - 미러 페이지의 경우
* *res.email.example.com* - 호스팅된 리소스(예: 이미지)

권장 사항 **ssl(HTTPS)을 통해 이러한 도메인 보안**. 실제로, 보안되지 않은 링크(HTTP)는 차단에 취약하며 최신 브라우저에서 경고에 플래그를 지정합니다.

이러한 하위 도메인에 SSL 인증서를 설치하려면 CSR 파일을 요청한 다음, 나중에 Adobe이 설치 또는 갱신할 수 있도록 SSL 인증서를 구매해야 합니다.

>[!CAUTION]
>
>SSL 인증서를 설치하기 전에 다음에 나열된 사전 요구 사항을 알고 있는지 확인하십시오. [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#installing-ssl-certificate).
>
>Adobe은 최대 2048비트 인증서만 지원합니다. 4096비트 인증서는 아직 지원되지 않습니다.

## 용어집

| 용어 | 설명 |
|--- |--- |
| CA(인증 기관) | DigiCert, Symantec 등과 같이 조직 또는 개인에게 디지털 인증서를 발급한 SSL 인증서 공급자입니다.<ul><li>신뢰할 수 있는 CA는 일반적으로 루트 인증서를 발급하는 타사 CA로 간주됩니다.</li><li>인증서를 사용하는 동일한 조직/회사에서 인증서로 서명하는 경우 자체 서명된 인증서와 같은 SSL 인증서인 경우에도 신뢰할 수 없는 CA로 분류됩니다.</li></ul> |
| 체인 인증서 | 루트 인증서와 하나 이상의 중간 인증서를 포함하는 인증서를 체인(또는 체인) 인증서라고 합니다. |
| CSR(인증서 서명 요청) | SSL 인증서를 적용할 때 인증 기관에 제공되는 인코딩된 텍스트 블록입니다. 일반적으로 인증서가 설치된 서버에서 생성됩니다. |
| DER(식별 인코딩 규칙) | 인증서 확장 유형입니다. .der 확장은 이진 DER 인코딩 인증서에 사용됩니다. 이러한 파일은 .cer 또는 .crt 확장명을 지원할 수도 있습니다. |
| EV(확장 유효성 검사) 인증서 | EV 인증서는 피싱 공격을 방지하기 위해 고안된 새로운 유형의 인증서입니다. 비즈니스 및 인증서를 주문하는 사람의 확장 유효성 검사가 필요합니다. |
| 높은 보증 인증서 | 도메인 이름의 소유권 및 유효한 비즈니스 등록을 확인한 후 CA에서 높은 보증 인증서를 발행합니다. |
| 중간 CA | 체인 인증서에 포함된 중간 인증서의 인증 기관 |
| 중간 인증서 | 인증 기관은 트리 구조의 형태로 인증서를 발행합니다. 루트 인증서는 트리의 맨 위에 있는 인증서입니다. 인증서와 루트 인증서 사이의 모든 인증서를 체인 또는 중간 인증서라고 합니다. |
| 낮은 보증 인증서 | 도메인 유효성 검사된 인증서라고도 하는 낮은 보증 인증서는 인증서에 도메인 이름만 포함되며, 비즈니스/조직 이름은 포함되지 않습니다. |
| PEM(개인 정보 보호 Enhanced Mail) | ASCII(Base64) 데이터를 포함하는 .pem 확장명의 인증서입니다. 이러한 인증서는 &quot; - - - - - - - BEGIN CERTIFICATE - - - - -&quot; 줄로 시작합니다. |
| 루트 인증서 | 인증 기관은 트리 구조의 형태로 인증서를 발행합니다. 루트 인증서는 트리의 맨 위에 있는 인증서입니다. |
| SAN(주체 대체 이름) | 주체 대체 이름은 추가 호스트 이름(사이트, IP 주소, 일반 이름 등)입니다. 단일 SSL 인증서의 일부로 서명해야 합니다. |
| 자체 서명된 인증서 | 신뢰할 수 있는 인증 기관이 아닌 인증서를 만드는 사람이 서명한 인증서입니다. 자체 서명된 인증서는 CA에서 서명한 인증서와 동일한 수준의 암호화를 활성화할 수 있지만 다음과 같은 두 가지 주요 단점이 있습니다.<ul><li>방문자의 연결이 해킹될 수 있으므로 공격자가 보낸 모든 데이터를 볼 수 있습니다(따라서 연결 암호화 목적을 달성할 수 없음)</li><li> 신뢰할 수 있는 인증서처럼 인증서를 취소할 수 없습니다.</li></ul> |
| SSL(Secure Sockets Layer) | 웹 서버와 브라우저 간에 암호화된 링크를 설정하는 표준 보안 기술. |
| 와일드카드 인증서 | 와일드카드 인증서는 *.adobe.com과 같은 단일 도메인 이름으로 첫째 수준 하위 도메인을 무제한으로 보호할 수 있습니다. |

## 주요 단계

1. CSR(인증서 서명 요청) 파일을 요청하고 필요한 정보(국가, 상태, 도시, 조직 이름, 조직 단위 이름 등)를 제공합니다. Adobe에 연결할 수도 있습니다.
1. Adobe에서 생성한 CSR 파일의 유효성을 확인하고 제공한 모든 정보가 올바른지 확인합니다.
1. CSR 세부 정보를 사용하여 신뢰할 수 있는 인증 기관에서 서명한 인증서를 생성합니다<!--taking care of asking for using the subjectAltName SSL extension (SAN) if it is for several domain names, and get/purchase the resulting certificate (ideally) in PEM format for Apache server-->.
1. SSL 인증서의 유효성을 확인하고 CSR과 일치하는지 확인합니다.
1. Adobe에 SSL 인증서를 제공합니다. 이 인증서는 설치할 것입니다.
1. 각 보안 하위 도메인에 대해 SSL 인증서가 성공적으로 설치되었는지 테스트합니다.
1. SSL 인증서 유효 기간을 모니터링합니다.
1. Adobe Campaign에서 특정 구성을 업데이트합니다.

## 자세한 프로세스

### 전제 조건

도메인 이름과 함수(추적, 미러 페이지, 웹 앱 등)를 보안
>[!NOTE]
>
>Adobe은 포함할 도메인 이름 및 함수를 정의하는 데 도움이 될 수 있습니다. 자세한 내용은 Adobe 고객 성공 관리자에게 문의하십시오.

### 1단계 - CSR 파일 가져오기

CSR(인증서 서명 요청) 파일을 가져오려면 아래 단계를 따르십시오.

* 액세스 권한이 있는 경우 [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko-KR)의 지침을 따르십시오. [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#subdomains-and-certificates) Campaign 컨트롤 패널에서 CSR 파일을 생성하여 다운로드할 수 있습니다.

* 그렇지 않으면 https://adminconsole.adobe.com/ 를 통해 지원 티켓을 만들어 필요한 하위 도메인에 대한 Adobe 고객 지원 센터에서 CSR 파일을 받으십시오.

다음은 따라야 할 몇 가지 모범 사례입니다.

* 위임된 하위 도메인당 한 개의 요청을 수행합니다.
* 여러 하위 도메인을 하나의 CSR 요청으로 결합할 수 있지만, 동일한 환경 내에서만 결합할 수 있습니다. 예를 들어 Campaign Classic에서 마케팅 서버는 [중간 소싱 서버](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/mid-sourcing-server.html), 및 [실행 인스턴스](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/configure-transactional-messaging/configuring-instances.html#execution-instance) 는 세 개의 분리된 환경입니다.
* SSL 인증서를 갱신하려면 먼저 새 CSR을 받아야 합니다. 1년 이상의 이전 CSR 파일을 사용하지 마십시오.

다음 정보를 제공해야 합니다.

>[!CAUTION]
>
>아래 표에 표시된 모든 필드를 입력해야 합니다. 그렇지 않으면 CSR 요청을 처리할 수 없습니다.

**Adobe 팀의 지원을 제공하는 정보:**

| 제공할 정보 | 예제 값 | 참고 |
|--- |--- |--- |
| 클라이언트 이름 | 우리 회사 | 조직의 이름입니다. 이 필드는 요청 추적을 위해 Adobe에서 사용합니다(CSR/SSL 인증서에 포함되지 않음). |
| Adobe Campaign 환경 URL | https://client-mid-prod1.campaign.adobe.com | Adobe Campaign 인스턴스 URL. |
| 일반 이름 [CN] | t.subdomain.customer.com | 이는 관련 도메인 중 하나일 수 있지만 일반적으로 추적 도메인일 수 있습니다. |
| 제목 대체 이름 [SAN] | t.subdomain.customer.com | 추적 하위 도메인을 SAN으로 포함해야 합니다. |
| 제목 대체 이름 [SAN] | m.subdomain.customer.com |
| 제목 대체 이름 [SAN] | res.subdomain.customer.com |

**IT/SSL 내부 팀이 제공하는 정보:**

| 제공할 정보 | 예제 값 | 참고 |
|--- |--- |--- |
| 국가 [C] | 미국 | 두 문자 코드여야 합니다. 전체 국가 목록 액세스 [여기](https://www.ssl.com/csrs/country_codes/).</br>*참고: 영국에서는 GB(영국 아님)를 사용합니다.* |
| 시/도 이름 [ST] | 일리노이 | 해당되는 경우 값은 약식 이름이 아니라 전체 이름이어야 합니다. |
| 구/군/시 이름 [L] | 시카고 |
| 조직 이름 [O] | ACME |
| 조직 단위 이름 [OU] | IT |

>[!NOTE]
>
>&quot;subdomain.customer.com&quot;을 위임된 하위 도메인으로 바꾸고, 다른 예제 값을 적절한 값으로 바꿉니다.

### 2단계 - CSR 파일의 유효성 검사

Adobe이 관련 정보를 사용하여 요청을 제출한 후 CSR(인증서 서명 요청) 파일을 생성하여 제공합니다.

결과 CSR 파일의 텍스트는 **&quot;—인증서 요청 시작—&quot;**.

Adobe에서 CSR 파일을 받은 후에는 아래 단계를 수행하십시오.

1. CSR 파일 텍스트를 복사하여 https://www.sslshopper.com/csr-decoder.html, <!--https://www.certlogik.com/decoder/,--> 또는 https://www.entrust.net/ssl-technical/csr-viewer.cfm
또는, *OpenSSL* Linux 시스템에서 로컬로 명령 자세한 내용은 [이 외부 페이지](https://www.question-defense.com/2009/09/22/use-openssl-to-verify-the-contents-of-a-csr-before-submitting-for-a-ssl-certificate).
1. 모든 검사가 성공했는지 확인합니다.
1. 올바른 매개 변수와 도메인 이름이 포함되어 있는지 확인합니다.
1. 다른 모든 데이터가 요청 제출 시 제공한 세부 정보와 일치하는지 확인합니다.

### 3단계 - SSL 인증서 생성

CSR 파일이 제공되면 CSR 파일을 사용하여 해당 도메인에 대한 SSL 인증서를 구매하고 생성해야 합니다.

* SSL 인증서:
   * 는 Apache PEM 형식이어야 합니다.
   * 2048비트 이하여야 합니다.
   * 유효한 CA(인증 기관)에 의해 서명해야 합니다.
   * CSR 파일에 언급된 모든 SAN(주체 대체 이름)을 포함해야 합니다.
* 중간 인증서가 하나 이상 있는 경우 루트 인증서와 모든 중간 인증서를 Adobe에 제공해야 합니다.
* 모든 인증서 유효 기간을 설정할 수 있지만 Adobe은 충분히 오래(예: 2년) 선택할 것을 권장합니다.

>[!NOTE]
>
>자체 내부 도구 또는 CA에서 제공하는 포털을 사용하여 인증서를 요청하는 경우 인증서 생성 프로세스의 지연이나 불일치를 방지하기 위해 CSR 요청에 제공된 것과 동일한 세부 정보를 사용해야 합니다.

### 4단계 - SSL 인증서 유효성 검사

SSL 인증서가 생성되면 Adobe으로 보내기 전에 유효성을 검사해야 합니다. 이렇게 하려면 아래 절차를 따르십시오.

1. 인증서에 .pem 확장명이 있는지 확인합니다. 그렇지 않은 경우 PEM 형식으로 변환합니다. 을 사용하여 전환을 만들 수 있습니다 *OpenSSL*.
1. 인증서가 **&quot;—BEGIN CERTIFICATE—&quot;**.
1. 인증서 텍스트를 https://www.sslshopper.com/certificate-decoder.html 또는 https://www.entrust.net/ssl-technical/csr-viewer.cfm 등의 온라인 디코더에 복사합니다.
또는, *OpenSSL* Linux 시스템에서 로컬로 명령 자세한 내용은 [이 외부 페이지](https://www.shellhacks.com/decode-ssl-certificate/).
1. 공통 이름, SAN, 발급자 및 유효 기간을 포함하여 인증서가 올바르게 확인되는지 확인하십시오.
1. SSL 인증서 확인이 성공하면 인증서가 를 사용하여 CSR과 일치하는지 확인합니다 [이 웹 사이트](https://www.sslshopper.com/certificate-key-matcher.html): 선택 **CSR과 인증서가 일치하는지 확인**&#x200B;를 입력하고 해당 필드에 인증서 및 CSR을 입력합니다. 그들은 일치해야 합니다.

### 5단계 - SSL 인증서 설치 요청

* 액세스 권한이 있는 경우 [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)의 지침을 따르십시오. [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#installing-ssl-certificate) 인증서를 Campaign 컨트롤 패널에 업로드합니다.

* 그렇지 않으면 https://adminconsole.adobe.com/ 을 통해 다른 지원 티켓을 만들어 Adobe 서버에 인증서를 설치하기 위한 Adobe을 요청하십시오.

다음을 제공해야 합니다.

* 인증서 파일, 루트 인증서 및 모든 중간 인증서(티켓에 첨부됨)이며, 바람직하게는 Apache PEM 형식입니다.
* CSR에 대해 발생한 이전 지원 티켓 수입니다.
* CSR 티켓에 대해 제공된 것과 동일한 데이터(일반 이름, 인스턴스 URL, 주/구/군/시, 조직 이름, 조직 단위 이름 등).

### 6단계 - SSL 인증서 설치 테스트

SSL 인증서가 설치 및 고객 지원 센터에서 확인되면 모든 URL에 대해 성공적으로 설치되었는지 확인하십시오.

SSL 설치 티켓을 닫기 전에 아래 테스트를 수행합니다. 또한 가 지시하는 대로 특정 구성을 업데이트해야 합니다. [이 섹션](#update-configuration).

브라우저에서 다음 URL로 이동합니다(&quot;subdomain.customer.com&quot;을 하위 도메인으로 바꾸기).

* https://subdomain.customer.com/r/test (용 [웹 애플리케이션](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/about-web-applications.html) 하위 도메인만 해당 - 전자 메일 하위 도메인에 적용되지 않음)
* https://t.subdomain.customer.com/r/test
* https://m.subdomain.customer.com/r/test
* https://res.subdomain.customer.com/r/test

성공하면 환경 정보가 표시되고 URL의 주소 표시줄은 연결이 안전함을 나타냅니다. 예를 들어 Google Chrome에서 다음 메시지를 볼 수 있습니다.

![](../../help/assets/ssl-google-successful-result.png)

SSL 인증서가 제대로 설치되지 않으면 다음 경고가 표시됩니다.

![](../../help/assets/ssl-google-unsuccessful-result.png)

### 7단계 - 인증서 유효 기간 확인

브라우저에서 인증서의 유효 기간을 확인할 수 있습니다. 예를 들어 Google Chrome에서 **보안** > **인증서**.

유효기간을 확인하는 것은 귀하의 책임입니다. Adobe은 인증서 만료를 모니터링하는 프로세스를 구현하는 것이 좋습니다. SSL 인증서가 곧 만료될 때 발생하는 작업에 대해 자세히 알아보십시오 [이 문서](https://www.thesslstore.com/blog/what-happens-when-your-ssl-certificate-expires/).

* 인증서 만료 날짜 최소 2주 전에 업데이트된 인증서를 요청하려면 지원 티켓을 만듭니다. CSR 세부 사항이 변경되지 않는 한 추가 CSR을 요청할 필요가 없습니다.

* 액세스 권한이 있는 경우 [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html), 그리고 환경이 AWS 환경에서 Adobe으로 호스팅되는 경우 Campaign 컨트롤 패널을 사용하여 인증서가 만료되기 전에 인증서를 갱신할 수 있습니다. 추가 정보 [이 섹션](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-ssl-certificates.html#monitoring-certificates).

### 8단계 - 특정 구성 업데이트 {#update-configuration}

요청한 SSL 인증서가 제대로 설치되면 Adobe Campaign의 모든 참조를 HTTP에서 HTTPS로 업데이트할 수 있습니다.

>[!NOTE]
>
>Campaign Classic의 경우 업데이트할 URL은 주로 [배포 마법사](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/initial-configuration/deploying-an-instance.html#deployment-wizard) 그리고 [외부 계정](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/accessing-external-database/external-accounts.html) (추적, 미러 페이지 및 공용 리소스 도메인) Campaign Standard에 대해서는 [브랜딩 구성](https://experienceleague.adobe.com/docs/campaign-standard/using/administrating/application-settings/branding.html#about-brand-identity).

구성이 업데이트되면 HTTP가 아닌 HTTPS URL을 사용하여 새 이메일이 전송됩니다. 이제 URL이 안전한지 확인하려면 다음 테스트를 신속하게 수행할 수 있습니다.

* Adobe Campaign에서 이미지를 업로드합니다. 이미지가 업로드되면 반환되는 URL은 HTTPS여야 합니다.
* 미러 페이지 링크, 일부 이미지, 텍스트 및 구독 취소 링크를 포함하는 테스트 이메일 게재를 만듭니다. 외부 이메일 ID(예: Gmail 주소)로 이메일을 전송합니다. 수신되면 이메일을 열고 SSL 인증서 경고나 오류 없이 이메일 내의 모든 링크를 HTTPS 양식(HTTP 아님)에서 올바르게 열는지 확인합니다.

## 제품별 리소스

**Campaign Classic**

* [Campaign 컨트롤 패널: SSL 인증서 추가(튜토리얼)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html) - 하위 도메인 보안을 위해 SSL 인증서를 추가하는 방법을 알아봅니다.

**Campaign Standard**

* [Campaign 컨트롤 패널: SSL 인증서 추가(튜토리얼)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html) - 하위 도메인 보안을 위해 SSL 인증서를 추가하는 방법을 알아봅니다.
