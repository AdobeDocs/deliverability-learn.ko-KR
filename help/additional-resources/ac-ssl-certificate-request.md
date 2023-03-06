---
title: SSL 인증서 요청 프로세스
description: Adobe을 위임한 하위 도메인에 SSL 인증서를 설치하는 방법을 배웁니다.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 8a78abd3-afba-49a7-a2ae-8b2c75326749
source-git-commit: 57016f89df54d5c74755a6a108a92db45153ec18
workflow-type: tm+mt
source-wordcount: '2252'
ht-degree: 3%

---

# SSL 인증서 요청 프로세스

이메일 전송을 위해 Adobe에게 도메인을 위임한 후( 참조) [도메인 이름 설정](/help/additional-resources/ac-domain-name-setup.md)), Adobe은 특정 기능을 위해 특정 하위 도메인을 만들고 사용합니다.

예를 들어 을 위임한 경우 *email.example.com* 이메일 전송을 Adobe 하기 위해 Adobe은 다음과 같은 하위 도메인을 만듭니다.
* *t.email.example.com* - 링크 추적
* *m.email.example.com* - 미러 페이지의 경우
* *res.email.example.com* - 호스팅된 리소스(예: 이미지)

권장 사항: **ssl(HTTPS)을 통해 이러한 도메인 보안**. 실제로 보안되지 않은 링크(HTTP)는 차단에 취약하며 최신 브라우저에 경고를 표시합니다.

이러한 하위 도메인에 SSL 인증서를 설치하려면 CSR 파일을 요청한 다음 Adobe이 설치하거나 갱신할 SSL 인증서를 구매해야 합니다.

>[!CAUTION]
>
>SSL 인증서를 설치하기 전에에 나열된 사전 요구 사항을 알고 있는지 확인하십시오. [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renew-ssl/renewing-subdomain-certificate.html?lang=ko).
>
>Adobe은 최대 2048비트 인증서만 지원합니다. 4096비트 인증서는 아직 지원되지 않습니다.

## 용어집

| 용어 | 설명 |
|--- |--- |
| CA(인증 기관) | DigiCert, Symantec 등과 같이 조직 또는 개인의 ID를 확인한 후 해당 조직 또는 개인에게 디지털 인증서를 발급하는 SSL 인증서 공급자입니다.<ul><li>신뢰할 수 있는 CA는 일반적으로 루트 인증서를 발급하는 서드파티 CA로 간주됩니다.</li><li>인증서를 사용하는 동일한 조직/회사에서 인증서에 서명하는 경우 자체 서명된 인증서와 같은 SSL 인증서인 경우에도 신뢰할 수 없는 CA로 분류됩니다.</li></ul> |
| 체인 인증서 | 루트 인증서와 하나 이상의 중간 인증서를 포함하는 인증서를 체인(또는 체인) 인증서라고 합니다. |
| CSR(인증서 서명 요청) | SSL 인증서를 신청할 때 인증 기관에 제공되는 인코딩된 텍스트 블록입니다. 일반적으로 인증서가 설치된 서버에서 생성됩니다. |
| DER(구별된 인코딩 규칙) | 인증서 확장 유형입니다. .der 확장은 이진 DER로 인코딩된 인증서에 사용됩니다. 이러한 파일은 .cer 또는 .crt 확장명을 지원할 수도 있습니다. |
| EV(확장 유효성 검사) 인증서 | EV 인증서는 피싱 공격을 방지하도록 설계된 새로운 유형의 인증서이다. 비즈니스 및 인증서를 주문하는 사람에 대한 확장 유효성 검사가 필요합니다. |
| 높은 품질 보증 인증서 | CA는 도메인 이름의 소유권 및 유효한 사업자 등록을 확인한 후 높은 보증 인증서를 발행합니다. |
| 중간 CA | 체인 인증서에 포함된 중간 인증서의 인증 기관. |
| 중간 인증서 | 인증 기관은 트리 구조의 형태로 인증서를 발급합니다. 루트 인증서는 트리의 최상위 인증서입니다. 인증서와 루트 인증서 사이의 모든 인증서를 체인 또는 중간 인증서라고 합니다. |
| 낮은 보증 인증서 | 도메인 확인 인증서라고도 하는 낮은 보증 인증서는 인증서에 도메인 이름만 포함하고 비즈니스/조직 이름은 포함하지 않습니다. |
| PEM(Privacy Enhanced Mail) | ASCII(Base64) 데이터가 포함된 확장명이 .pem인 인증서입니다. 이러한 인증서는 &quot; - - - - - - - BEGIN CERTIFICATE - - - -&quot; 줄로 시작합니다. |
| 루트 인증서 | 인증 기관은 트리 구조의 형태로 인증서를 발급합니다. 루트 인증서는 트리의 최상위 인증서입니다. |
| SAN(주체 대체 이름) | 주체 대체 이름은 추가 호스트 이름(사이트, IP 주소, 일반 이름 등)입니다. 단일 SSL 인증서의 일부로 서명해야 합니다. |
| 자체 서명된 인증서 | 신뢰할 수 있는 인증 기관이 아니라 인증서를 만드는 사람이 서명한 인증서. 자체 서명된 인증서는 CA에서 서명한 인증서와 동일한 수준의 암호화를 활성화할 수 있지만 두 가지 주요 단점이 있습니다.<ul><li>방문자의 연결이 하이재킹될 수 있으므로 공격자는 전송된 모든 데이터를 볼 수 있습니다(따라서 연결 암호화의 목적 상실)</li><li> 신뢰할 수 있는 인증서처럼 인증서를 해지할 수 없습니다.</li></ul> |
| SSL(보안 소켓 레이어) | 웹 서버와 브라우저 간에 암호화된 링크를 설정하는 표준 보안 기술입니다. |
| 와일드카드 인증서 | 와일드카드 인증서는 *.adobe.com과 같은 단일 도메인 이름에서 무제한으로 첫 번째 수준 하위 도메인을 보호할 수 있습니다. |

## 주요 단계

1. CSR(인증서 서명 요청) 파일을 요청하고 필요한 정보(국가, 주, 도시, 조직 이름, 조직 단위 이름 등)를 제공합니다. Adobe.
1. Adobe으로 생성된 CSR 파일의 유효성을 확인하고 제공한 모든 정보가 올바른지 확인하십시오.
1. CSR 세부 정보를 사용하여 신뢰할 수 있는 인증 기관에서 서명한 인증서를 생성합니다<!--taking care of asking for using the subjectAltName SSL extension (SAN) if it is for several domain names, and get/purchase the resulting certificate (ideally) in PEM format for Apache server-->.
1. SSL 인증서의 유효성을 검사하고 CSR과 일치하는지 확인합니다.
1. SSL 인증서를 설치할 Adobe에게 제공합니다.
1. 각 보안 하위 도메인에 대해 SSL 인증서가 성공적으로 설치되었는지 테스트합니다.
1. SSL 인증서 유효 기간을 모니터링합니다.
1. Adobe Campaign에서 특정 구성을 업데이트합니다.

## 세부 프로세스

### 전제 조건

도메인 이름과 함수(추적, 미러 페이지, 웹 앱 등)를 식별해야 합니다. 보안을 위해.
>[!NOTE]
>
>Adobe은 포함할 도메인 이름 및 함수를 정의하는 데 도움이 될 수 있습니다. 자세한 내용은 Adobe 계정 팀에 문의하십시오.

### 1단계 - CSR 파일 가져오기

CSR(인증서 서명 요청) 파일을 가져오려면 아래 단계를 수행합니다.

* 다음에 대한 액세스 권한이 있는 경우: [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko-KR)의 지침을 따르십시오. [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#subdomains-and-certificates) Campaign 컨트롤 패널에서 CSR 파일을 생성하여 다운로드합니다.

* 그렇지 않으면 https://adminconsole.adobe.com/ 을 통해 지원 티켓을 만들어 Adobe 고객 지원 센터에서 필요한 하위 도메인에 대한 CSR 파일을 가져옵니다.

다음은 따라야 할 몇 가지 모범 사례입니다.

* 위임된 하위 도메인당 요청을 한 개 발생시킵니다.
* 여러 하위 도메인을 단일 CSR 요청으로 결합할 수 있지만 동일한 환경 내에서만 가능합니다. 예를 들어 Campaign Classic에서 마케팅 서버는 [중간 소싱 서버](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/mid-sourcing-server.html)및 [실행 인스턴스](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/configure-transactional-messaging/configuring-instances.html#execution-instance) 는 세 개의 개별 환경입니다.
* SSL 인증서 갱신 전에 새 CSR을 받아야 합니다. 1년 이상 전의 이전 CSR 파일을 사용하지 마십시오.

다음 정보를 제공해야 합니다.

>[!CAUTION]
>
>아래 표에 표시된 필드를 모두 채워야 합니다. 그렇지 않으면 CSR 요청을 처리할 수 없습니다.

**Adobe 팀의 도움을 받기 위한 정보:**

| 제공할 정보 | 예제 값 | 참고 |
|--- |--- |--- |
| 클라이언트 이름 | 내 회사 | 조직의 이름입니다. 이 필드는 Adobe이 요청을 추적하는 데 사용됩니다(CSR/SSL 인증서의 일부가 아님). |
| Adobe Campaign 환경 URL | https://client-mid-prod1.campaign.adobe.com | Adobe Campaign 인스턴스 URL. |
| 일반 이름 [CN] | t.subdomain.customer.com | 관련 도메인이 될 수 있지만 일반적으로 추적 도메인입니다. |
| 주체 대체 이름 [SAN] | t.subdomain.customer.com | 반드시 추적 하위 도메인을 SAN으로 포함하십시오. |
| 주체 대체 이름 [SAN] | m.subdomain.customer.com |
| 주체 대체 이름 [SAN] | res.subdomain.customer.com |

**IT/SSL 내부 팀에서 제공하는 정보:**

| 제공할 정보 | 예제 값 | 참고 |
|--- |--- |--- |
| 국가 [C] | US | 두 글자로 된 코드여야 합니다. 전체 국가 목록 액세스 [여기](https://www.ssl.com/csrs/country_codes/).</br>*참고: 영국의 경우 GB(영국 아님)를 사용합니다.* |
| 시/도 이름 [ST] | 일리노이 | 해당하는 경우. 값은 약어가 아닌 전체 이름이어야 합니다. |
| 구/군/시 이름 [L] | 시카고 |
| 조직 이름 [O] | ACME |
| 조직 단위 이름 [OU] | IT |

>[!NOTE]
>
>&quot;subdomain.customer.com&quot;을 위임된 하위 도메인으로 바꾸고 다른 예제 값을 적절한 값으로 바꿉니다.

### 2단계 - CSR 파일 유효성 검사

관련 정보를 사용하여 요청을 제출하면 Adobe에서 인증서 서명 요청(CSR) 파일을 생성하여 제공합니다.

결과 CSR 파일의 텍스트는 **&quot;-----인증서 요청 시작-----&quot;**.

Adobe에서 CSR 파일을 받으면 아래 단계를 수행합니다.

1. CSR 파일 텍스트를 복사하여 https://www.sslshopper.com/csr-decoder.html과 같은 온라인 디코더에 붙여 넣습니다. <!--https://www.certlogik.com/decoder/,--> 또는 https://www.entrust.net/ssl-technical/csr-viewer.cfm을 참조하십시오.
또는 *Openssl* linux 시스템에서 로컬로 명령을 실행합니다.
1. 모든 검사가 성공했는지 확인합니다.
1. 올바른 매개 변수와 도메인 이름이 포함되어 있는지 확인합니다.
1. 다른 모든 데이터는 요청을 제출할 때 제공한 세부 정보와 일치하는지 확인하십시오.

### 3단계 - SSL 인증서 생성

CSR 파일이 제공되면 CSR 파일을 사용하여 해당 도메인에 대한 SSL 인증서를 구매하고 생성해야 합니다.

* SSL 인증서:
   * 은(는) Apache PEM 형식이어야 합니다.
   * 은(는) 2048비트를 초과할 수 없습니다.
   * 은(는) 유효한 CA(인증 기관)의 서명이 있어야 합니다.
   * 는 CSR 파일에 언급된 대로 모든 SAN(주체 대체 이름)을 포함해야 합니다.
* 중간 인증서가 하나 이상 있는 경우 루트 인증서와 모든 중간 인증서를 Adobe에 제공해야 합니다.
* Adobe 모든 인증서 유효 기간을 설정할 수 있지만 충분히 길게(예: 2년) 선택하는 것이 좋습니다.

>[!NOTE]
>
>자체 내부 도구 또는 CA에서 제공한 포털을 사용하여 인증서를 요청하는 경우 CSR 요청에 제공된 것과 동일한 세부 정보를 사용하여 인증서 생성 프로세스가 지연되거나 일치하지 않도록 해야 합니다.

### 4단계 - SSL 인증서 유효성 검사

SSL 인증서가 생성되면 Adobe으로 보내기 전에 유효성을 검사해야 합니다. 이렇게 하려면 아래 절차를 따르십시오.

1. 인증서의 확장명이 .pem인지 확인합니다. 그렇지 않은 경우 PEM 형식으로 변환합니다. 다음을 사용하여 변환할 수 있습니다. *Openssl*.
1. 인증서가 다음으로 시작하는지 확인 **&quot;-----인증서 시작-----&quot;**.
1. 인증서 텍스트를 https://www.sslshopper.com/certificate-decoder.html 또는 https://www.entrust.net/ssl-technical/csr-viewer.cfm과 같은 온라인 디코더에 복사합니다.
또는 *Openssl* linux 시스템에서 로컬로 명령을 실행합니다. 자세한 내용은 다음을 참조하십시오. [이 외부 페이지](https://www.shellhacks.com/decode-ssl-certificate/).
1. 인증서가 일반 이름, SAN, 발급자 및 유효 기간을 포함하여 올바르게 확인되는지 확인하십시오.
1. SSL 인증서 확인에 성공하면 을 사용하여 인증서가 CSR과 일치하는지 확인합니다. [이 웹 사이트](https://www.sslshopper.com/certificate-key-matcher.html): 선택 **CSR과 인증서가 일치하는지 확인**&#x200B;을 클릭하고 해당 필드에 인증서와 CSR을 입력합니다. 서로 일치해야 합니다.

### 5단계 - SSL 인증서 설치 요청

* 다음에 대한 액세스 권한이 있는 경우: [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko-KR)의 지침을 따르십시오. [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renew-ssl/renewing-subdomain-certificate.html?lang=ko) 인증서를 Campaign 컨트롤 패널에 업로드합니다.

* 그렇지 않으면 https://adminconsole.adobe.com/ 을 통해 다른 지원 티켓을 만들어 Adobe 서버에 인증서를 설치하기 위한 Adobe을 요청합니다.

다음을 제공해야 합니다.

* 인증서 파일, 루트 인증서 및 중간 인증서(티켓에 첨부됨), 바람직하게는 Apache PEM 형식입니다.
* CSR에 대해 제기된 이전 지원 티켓 수입니다.
* CSR 티켓에 제공된 것과 동일한 데이터(일반 이름, 인스턴스 URL, 시/도, 도시/지역, 조직 이름, 조직 단위 이름 등).

### 6단계 - SSL 인증서 설치 테스트

Adobe 고객 지원 센터에서 SSL 인증서를 설치하고 확인했으면 모든 URL에 대해 SSL 인증서가 성공적으로 설치되었는지 확인합니다.

SSL 설치 티켓을 닫기 전에 아래 테스트를 수행하십시오. 또한 의 지침에 따라 특정 구성을 업데이트해야 합니다. [이 섹션](#update-configuration).

브라우저에서 다음 URL로 이동합니다(&quot;subdomain.customer.com&quot; 을 하위 도메인으로 바꾸기).

* https://subdomain.customer.com/r/test (용 [웹 애플리케이션](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/about-web-applications.html) 하위 도메인만 해당 - 이메일 하위 도메인에는 적용되지 않음)
* https://t.subdomain.customer.com/r/test
* https://m.subdomain.customer.com/r/test
* https://res.subdomain.customer.com/r/test

성공적인 결과는 환경 정보를 제공하며 URL의 주소 표시줄은 연결이 안전함을 나타냅니다. 예를 들어 Google Chrome에서 다음 메시지를 볼 수 있습니다.

![](../../help/assets/ssl-google-successful-result.png)

SSL 인증서가 제대로 설치되지 않은 경우 다음 경고가 표시됩니다.

![](../../help/assets/ssl-google-unsuccessful-result.png)

### 7단계 - 인증서 유효 기간 확인

브라우저에서 인증서의 유효 기간을 확인할 수 있습니다. 예를 들어 Google Chrome에서 **보안** > **인증서**.

유효기간을 확인하는 것은 당신의 책임입니다. Adobe은 인증서 만료를 모니터링하는 프로세스를 구현할 것을 권장합니다. SSL 인증서가 다음 기간 후에 만료되는 사항에 대해 자세히 알아보기 [이 문서](https://www.thesslstore.com/blog/what-happens-when-your-ssl-certificate-expires/).

* 인증서 만료일 최소 2주 전에 업데이트된 인증서를 요청하려면 지원 티켓을 만드십시오. CSR 세부 사항이 변경되지 않은 경우에는 추가 CSR을 요청할 필요가 없습니다.

* 다음에 대한 액세스 권한이 있는 경우: [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko-KR), 그리고 환경이 AWS 환경에서 Adobe에 의해 호스팅되는 경우 만료되기 전에 Campaign 컨트롤 패널을 사용하여 인증서를 갱신할 수 있습니다. 자세한 내용은 [이 섹션](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-ssl-certificates.html#monitoring-certificates)을 참조하십시오.

### 8단계 - 특정 구성 업데이트 {#update-configuration}

요청한 SSL 인증서가 제대로 설치되었으면 Adobe Campaign의 모든 참조를 HTTP에서 HTTPS로 업데이트할 수 있습니다.

>[!NOTE]
>
>Campaign Classic의 경우 업데이트할 URL은 주로 [배포 마법사](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/initial-configuration/deploying-an-instance.html#deployment-wizard) 및 [외부 계정](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/accessing-external-database/external-accounts.html) (추적, 미러 페이지 및 공개 리소스 도메인). Campaign Standard은 다음을 참조하십시오. [브랜딩 구성](https://experienceleague.adobe.com/docs/campaign-standard/using/administrating/application-settings/branding.html#about-brand-identity).

구성이 업데이트되면 새 이메일이 HTTP가 아닌 HTTPS URL을 통해 전송됩니다. 이제 URL이 안전한지 확인하기 위해 다음 테스트를 빠르게 수행할 수 있습니다.

* Adobe Campaign에서 이미지를 업로드합니다. 이미지가 업로드되면 반환되는 URL은 HTTPS여야 합니다.
* 미러 페이지 링크, 일부 이미지, 텍스트 및 구독 취소 링크를 포함하는 테스트 이메일 게재를 만듭니다. 외부 이메일 ID(예: Gmail 주소)로 이메일을 발송합니다. 수신 후, 이메일을 열고 이메일에 포함된 모든 링크가 HTTP가 아닌 HTTPS 양식에서 올바르게 열리는지 확인합니다. SSL 인증서 경고나 오류가 발생하지 않습니다.

## 제품별 리소스

**Campaign Classic**

* [Campaign 컨트롤 패널: SSL 인증서 추가(튜토리얼)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html) - 하위 도메인 보안을 위해 SSL 인증서를 추가하는 방법을 알아봅니다.

**Campaign Standard**

* [Campaign 컨트롤 패널: SSL 인증서 추가(튜토리얼)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html) - 하위 도메인 보안을 위해 SSL 인증서를 추가하는 방법을 알아봅니다.
