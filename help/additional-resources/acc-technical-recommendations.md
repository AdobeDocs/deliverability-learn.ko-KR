---
title: Campaign Classic - 기술 추천
description: Adobe Campaign Classic을 사용하여 게재 가능성을 향상시키는 데 사용할 수 있는 기술, 구성 및 도구를 살펴봅니다.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 39ed3773-18bf-4653-93b6-ffc64546406b
source-git-commit: 3dc1d2f352346fa2ef7b5c883da6a3e243cb32c0
workflow-type: tm+mt
source-wordcount: '1858'
ht-degree: 1%

---

# Campaign Classic - 기술 추천 {#technical-recommendations}

Adobe Campaign Classic 사용 시 게재 능력을 향상시키는 데 사용할 수 있는 몇 가지 기술, 구성 및 도구가 아래에 나와 있습니다.

## 구성 {#configuration}

### 역방향 DNS {#reverse-dns}

Adobe Campaign은 IP 주소에 대해 역방향 DNS가 지정되었는지 확인하고, 이것이 IP를 올바르게 다시 가리키는지 확인합니다.

네트워크 구성의 중요한 점은 보내는 메시지의 각 IP 주소에 대해 올바른 역방향 DNS가 정의되어 있는지 확인하는 것입니다. 즉, 지정된 IP 주소의 경우 초기 IP 주소로 다시 루프백되는 일치하는 DNS(A 레코드)와 역방향 DNS 레코드(PTR 레코드)가 있습니다.

역방향 DNS에 대한 도메인 선택은 특정 ISP를 처리할 때 영향을 줍니다. 특히 AOL은 역방향 DNS와 동일한 도메인에 있는 주소가 있는 피드백 루프만 허용합니다(참조) [피드백 루프](#feedback-loop)).

>[!NOTE]
>
>다음을 사용할 수 있습니다. [이 외부 도구](https://mxtoolbox.com/SuperTool.aspx) 을 클릭하여 도메인의 구성을 확인합니다.

### MX 규칙 {#mx-rules}

MX 규칙(Mail eXchanger)은 보내는 서버와 받는 서버 간의 통신을 관리하는 규칙입니다.

보다 정확하게는 Adobe Campaign MTA(메시지 전송 에이전트)가 각 개별 이메일 도메인 또는 ISP(예: hotmail.com, comcast.net)로 이메일을 보내는 속도를 제어하는 데 사용됩니다. 이러한 규칙은 일반적으로 ISP에 의해 게시된 제한을 기반으로 합니다(예를 들어 각 SMTP 연결당 20개 이상의 메시지를 포함하지 않음).

>[!NOTE]
>
>Adobe Campaign Classic의 MX 관리에 대한 자세한 내용은 [이 섹션](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/email-deliverability.html#mx-configuration).

### TLS {#tls}

TLS(전송 계층 보안)는 두 이메일 서버 간 연결을 보호하고 이메일 콘텐츠를 의도한 수신자가 아닌 다른 사람이 읽지 못하도록 보호하는 데 사용할 수 있는 암호화 프로토콜입니다.

### 보낸 사람의 도메인 {#sender-domain}

HELO 명령에 사용되는 도메인을 정의하려면 인스턴스의 구성 파일(conf/config-instance.xml)을 편집하고 다음과 같이 &quot;localDomain&quot; 속성을 정의합니다.

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

MAIL FROM 도메인은 기술 바운스 메시지에 사용되는 도메인입니다. 이 주소는 배포 마법사나 NmsEmail_DefaultErrorAddr 옵션을 통해 정의됩니다.

### SPF 레코드 {#dns-configuration}

SPF 레코드는 현재 DNS 서버에서 TXT 유형 레코드(코드 16) 또는 SPF 유형 레코드(코드 99)로 정의할 수 있습니다. SPF 레코드는 문자열의 형태를 취합니다. 예:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

도메인에 대한 이메일을 보내도록 승인된 두 개의 IP 주소인 12.34.56.78과 12.34.56.79를 정의합니다. **~all** 는 다른 주소는 SoftFail로 해석해야 함을 의미합니다.

SPF 레코드를 정의하는 Recommendations:

* 추가 **~all** (소프트 실패) 또는 **-all** (실패) 끝에 정의된 서버 이외의 모든 서버를 거부합니다. 이 기능이 없으면 서버는 중립 평가와 함께 이 도메인을 생성할 수 있습니다.
* 추가하지 않음 **ptr** (openspf.org에서는 비용이 많이 들고 신뢰할 수 없는 것으로 간주하여 이를 방지할 것을 권장합니다.)

>[!NOTE]
>
>에서 SPF에 대해 자세히 알아보기 [이 섹션](/help/additional-resources/authentication.md#spf).

## 인증

>[!NOTE]
>
>에서 다양한 형식의 이메일 인증에 대해 자세히 알아보십시오. [이 섹션](/help/additional-resources/authentication.md).

### D김 {#dkim-acc}

>[!NOTE]
>
>호스팅 또는 하이브리드 설치의 경우 를 로 업그레이드한 경우 [향상된 MTA](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/sending-with-enhanced-mta.html#sending-messages), DKIM 전자 메일 인증 서명은 모든 도메인이 있는 모든 메시지에 대해 Enhanced MTA에서 수행합니다.

사용 [D김](/help/additional-resources/authentication.md#dkim) Adobe Campaign Classic을 사용하려면 다음 전제 조건이 필요합니다.

**Adobe Campaign 옵션 선언**: Adobe Campaign에서 DKIM 개인 키는 DKIM 선택기와 도메인을 기반으로 합니다. 현재 선택기가 다른 동일한 도메인/하위 도메인에 대해 여러 개의 개인 키를 만들 수 없습니다. 플랫폼 또는 이메일에서 인증에 사용해야 하는 선택기 도메인/하위 도메인을 정의할 수는 없습니다. 플랫폼은 개인 키 중 하나를 선택할 수 있으며, 이는 인증이 실패할 가능성이 높다는 것을 의미합니다.

* Adobe Campaign 인스턴스에 대해 DomainKeys를 구성한 경우 **dkim** 다음에서 [도메인 관리 규칙](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#email-management-rules). 그렇지 않으면 DKIM을 대체한 도메인 키와 동일한 구성 단계(개인/공개 키)를 따릅니다.
* 향상된 버전의 DomainKeys인 DKIM과 동일한 도메인에 대해 DomainKeys 및 DKIM을 모두 활성화할 필요는 없습니다.
* 현재 DKIM의 유효성을 검사하는 도메인은 AOL, Gmail입니다.

## 피드백 루프 {#feedback-loop-acc}

피드백 루프는 ISP 수준에서 메시지를 보내는 데 사용되는 IP 주소 범위에 대해 지정된 이메일 주소를 선언함으로써 작동합니다. ISP는 바운스 메시지에 대해 수행되는 작업과 유사한 방식으로 이 사서함에 전송하며, 이 메시지는 수신자가 스팸으로 보고합니다. 불만을 제기한 사용자에게 향후 게재를 차단하도록 플랫폼을 구성해야 합니다. 적절한 옵트아웃 링크를 사용하지 않았더라도 더 이상 연락하지 않는 것이 중요합니다. ISP가 IP 주소를 차단 목록에 추가하다에 추가한다는 이러한 컴플레인에 기반합니다. ISP에 따라 1% 안팎의 컴플레인이 발생하면 IP 주소가 차단된다.

피드백 루프 메시지 형식을 정의하는 표준이 현재 작성 중입니다. [ARF(Abuse Feedback Reporting Format)](https://tools.ietf.org/html/rfc6650).

인스턴스에 대한 피드백 루프를 구현하려면 다음이 필요합니다.

* 인스턴스 전용 사서함(바운스 사서함일 수 있음)
* 인스턴스 전용 IP 전송 주소

Adobe Campaign에서 간단한 피드백 루프를 구현하면 바운스 메시지 기능이 사용됩니다. 피드백 루프 사서함은 바운스 사서함으로 사용되며 이러한 메시지를 검색하기 위한 규칙이 정의됩니다. 메시지를 스팸으로 보고한 수신자의 이메일 주소가 격리 목록에 추가됩니다.

* 바운스 메일 규칙 만들기 또는 수정, **Feedback_loop**, 위치 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 를 이유로 **거부됨** 및 유형 **하드**.
* 특별히 피드백 루프에 대해 사서함이 정의된 경우 새 외부 바운스 메일 계정을 만들어 사서함에 액세스할 매개 변수를 정의합니다 **[!UICONTROL Administration > Platform > External accounts]**.

컴플레인 알림을 처리하기 위해 메커니즘이 즉시 작동합니다. 이 규칙이 올바르게 작동하는지 확인하려면 이러한 메시지가 수집되지 않도록 계정을 일시적으로 비활성화한 다음 피드백 루프 사서함의 내용을 수동으로 확인할 수 있습니다. 서버에서 다음 명령을 실행합니다.

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

여러 인스턴스에 대해 하나의 피드백 루프 주소를 사용해야 하는 경우 다음을 수행해야 합니다.

* 받은 메시지를 인스턴스가 있는 수만큼 사서함에 복제합니다.
* 각 사서함을 하나의 인스턴스로 가져와서
* 인스턴스 정보가 Adobe Campaign에서 보낸 메시지의 Message-ID 헤더에 포함되므로 피드백 루프 메시지에도 배치되도록 인스턴스를 구성합니다. 간단히 **checkInstanceName** 인스턴스 구성 파일의 매개 변수(기본적으로 인스턴스는 확인되지 않으며 이로 인해 특정 주소가 잘못 격리될 수 있음):

  ```
  <serverConf>
    <inMail checkInstanceName="true"/>
  </serverConf>
  ```

Adobe Campaign의 Deliverability Service는 AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho 등의 ISP에 대한 피드백 루프 서비스 구독을 관리합니다.

## 목록-구독 취소 {#list-unsubscribe}

### 목록 구독 취소 정보 {#about-list-unsubscribe}

이름이 인 SMTP 헤더 추가 **목록-구독 취소** 는 최적의 전달성 관리를 위해 필수입니다.2024년 6월 1일부터 Yahoo 및 Gmail은 보낸 사람이 원클릭 목록 구독 취소를 준수하도록 요구합니다. 원클릭 목록 구독 취소를 구성하는 방법을 이해하려면 아래를 참조하십시오.


이 헤더는 &quot;스팸으로 보고&quot; 아이콘 대신 사용할 수 있습니다. 이메일 인터페이스에 구독 취소 링크로 표시됩니다.

이 기능을 사용하면 평판을 보호할 수 있으며 구독이 취소되면 피드백이 실행됩니다.

목록 구독 취소를 사용하려면 다음과 유사한 명령줄을 입력해야 합니다.

```
List-Unsubscribe: <mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe>
```

>[!CAUTION]
>
>위의 예는 수신자 테이블을 기반으로 합니다. 다른 테이블에서 데이터베이스를 구현한 경우에는 명령줄에 올바른 정보를 다시 입력해야 합니다.

다음 명령줄을 사용하여 다이내믹을 만들 수 있습니다 **목록-구독 취소**:

```
List-Unsubscribe: <mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%>
```

Gmail, Outlook.com 및 Microsoft Outlook은 이 메서드를 지원하며 구독 취소 버튼은 인터페이스에서 직접 사용할 수 있습니다. 이 기법은 불만율을 낮춥니다.

다음을 구현할 수 있습니다. **목록-구독 취소** 다음 중 하나를 통해:

* 직접 [게재 템플릿에 명령줄 추가](#adding-a-command-line-in-a-delivery-template)
* [유형화 규칙 만들기](#creating-a-typology-rule)

### 게재 템플릿에 명령줄 추가 {#adding-a-command-line-in-a-delivery-template}

전자 메일 SMTP 헤더의 추가 섹션에 명령줄을 추가해야 합니다.

이 추가는 각 이메일 또는 기존 게재 템플릿에서 수행할 수 있습니다. 이 기능을 포함하는 새 게재 템플릿을 만들 수도 있습니다.

* 목록 구독 취소: <mailto:unsubscribe@domain.com>
구독 취소 링크를 클릭하면 사용자의 기본 이메일 클라이언트가 열립니다. 이 유형화 규칙은 이메일을 만드는 데 사용되는 유형화에 추가해야 합니다.

* 목록 구독 취소: <https://domain.com/unsubscribe.jsp>
구독 취소 링크를 클릭하면 사용자가 구독 취소 양식으로 리디렉션됩니다.
  ![이미지](/help/assets/UTF-8-1.png)


### 유형화 규칙 만들기 {#creating-a-typology-rule}

규칙에는 명령줄을 생성하는 스크립트가 포함되어야 하며 이메일 헤더에 포함되어야 합니다.

>[!NOTE]
>
>유형화 규칙을 만드는 것이 좋습니다. 목록 구독 취소 기능은 각 이메일에 자동으로 추가됩니다.

>[!NOTE]
>
>에서 Adobe Campaign Classic에서 유형화 규칙을 만드는 방법을 알아봅니다. [이 섹션](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/campaign-optimization/about-campaign-typologies.html#typology-rules).

### 원클릭 목록 구독 취소

2024년 6월 1일부터 Yahoo 및 Gmail은 보낸 사람이 원클릭 목록 구독 취소를 준수하도록 요구합니다. One-Click List-Unsubscribe 요구 사항 발송자를 준수하려면 다음 작업을 수행해야 합니다.

* List-Unsubscribe-Post: List-Unsubscribe=One-Click에 추가
* URI 구독 취소 링크 포함
* Adobe Campaign에서 지원하는 수신자의 HTTP POST 응답 수신을 지원합니다.

원클릭 목록 구독 취소를 직접 구성하려면 다음을 수행합니다.

* 다음 &quot;수신자 비클릭&quot; 웹 애플리케이션에 추가 
   1. 리소스 -> 온라인 -> 웹 응용 프로그램으로 이동
   2. &quot;구독 취소 수신자 클릭 없음&quot; 업로드 [XML](/help/assets/WebAppUnsubNoClick.xml.zip)
* 목록 구독 취소 및 목록 구독 취소 게시물 구성
   1. 게재 속성의 SMTP 섹션으로 이동합니다.
   2. 추가 SMTP 헤더 아래에서 명령줄에 을 입력합니다(각 헤더는 별도의 줄에 있어야 함).

```
List-Unsubscribe-Post: List-Unsubscribe=One-Click
List-Unsubscribe: <https//domain.com/webApp/unsubNoClick?id=<%= recipient.cryptidcamp %>>, <mailto: %=errorAddress%?
subject=unsubscribe%=message.mimeMessageId%>
```

위의 예에서는 원클릭을 지원하는 ISP에 대해 원클릭 목록 구독 취소를 활성화하면서도 URL 목록 구독 취소를 지원하지 않는 수신자는 이메일을 통해 여전히 구독 취소를 요청할 수 있습니다.


### 원클릭 목록 구독 취소를 지원하는 유형화 규칙 만들기:

새 유형화 규칙을 만듭니다.

* 탐색 트리에서 &quot;새로 만들기&quot;를 클릭하여 새 유형화를 만듭니다

![이미지](/help/assets/CreatingTypologyRules1.png)

유형화 규칙을 계속 구성합니다.

* 규칙 유형 : 제어
* 채널: 이메일
* 단계 : 개인화 시작 시
* 레벨 : 원하는 대로
* 활성

![이미지](/help/assets/CreatingTypologyRules2.png)

유형화 규칙의 Javascript를 코딩합니다.

>[!NOTE]
>
>아래에 설명된 코드는 예시로서 참조되어야 한다.
>이 예에서는 다음 방법을 자세히 설명합니다.
>* URL 목록 구독 취소를 구성하고 헤더를 추가하거나 기존 mailto: 매개 변수를 추가하고 다음으로 바꿉니다. &lt;mailto..>, <http://…>
>* List-Unsubscribe-Post 헤더에 추가
>게시물 URL 예제는 var headerUnsubUrl = &quot;http://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=&lt;%= recipient.cryptedId %>&quot;를 사용합니다.
>* 다른 매개 변수를 추가할 수 있습니다(&amp;service = ...)
>


```
// Function to add or replace a header in the provided headers 
function addHeader(headers, header, value)  { 
    
  // Create the new header line 
  var headerLine = header + ": " + value; 
    
  // Create a regular expression to find the specified header 
  var regExp = new RegExp(header + ":(.*)$", "i") 
    
  // Split the headers into individual lines 
  var headerLines = headers.split("\n"); 
    
  // Loop through each line 
  for (var i=0; i < headerLines.length; i++) { 
      
    // Check if the specified header exists 
    var match = headerLines[i].match(regExp) 
      
    // If it exists 
    if ( match != null ) { 
        
      // Replace the existing header line 
      headerLines[i] = headerLine; 
        
      // Return the modified headers 
      return headerLines.join("\n"); 
    } 
  } 
    
  // If the header does not exist, add the new header line 
  headerLines.push(headerLine); 
    
  // Return the modified headers 
  return headerLines.join("\n"); 
} 
  
// Function to get the value of a specified header from the provided headers 
function getHeader(headers, header) { 
    
  // Create a regular expression to find the specified header 
  var regExp = new RegExp(header + ":(.*)$", "i") 
    
  // Split the headers into individual lines 
  var headerLines = headers.split("\n"); 
    
  // Loop each line 
  for each (line in headerLines) { 
      
    // Check if the specified header exists 
    var match = line.match(regExp); 
      
    // If it exists 
    if ( match != null ) { 
        
      // Return the header value, removing leading whitespace 
      return match[1].replace(/^\s*/, ""); 
    } 
  } 
    
  // If the header does not exist, return an empty string 
  return ""; 
} 
  
  
// Define the unsubscribe URL 
var headerUnsubUrl = "http://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=<%= recipient.cryptedId %>"; 
  
// Get the value of the List-Unsubscribe header 
var headerUnsub = getHeader(delivery.mailParameters.headers, "List-Unsubscribe"); 
  
// If the List-Unsubscribe header does not exist 
if ( headerUnsub === "" ) { 
  // Add the List-Unsubscribe header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe", "<"+headerUnsubUrl+">"); 
} 
// If the List-Unsubscribe header exists and contains 'mailto' 
else if(headerUnsub.search('mailto')){ 
  // Replace the existing List-Unsubscribe header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe", "<"+headerUnsubUrl+">"); 
} 
  
// Get the value of the List-Unsubscribe-Post header 
var headerUnsubPost = getHeader(delivery.mailParameters.headers, "List-Unsubscribe-Post"); 
  
// If the List-Unsubscribe-Post header does not exist 
if ( headerUnsubPost === "" ) { 
  // Add the List-Unsubscribe-Post header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe-Post", "List-Unsubscribe=One-Click"); 
} 
  
// Return true to indicate success 
return true; 
```

![이미지](/help/assets/CreatingTypologyRules3.png)

이메일에 유형화에 새 규칙을 추가합니다(기본 유형화는 정상).

![이미지](/help/assets/CreatingTypologyRules4.png)

새 게재 준비(게재 속성의 추가 SMTP 헤더가 비어 있는지 확인)

![이미지](/help/assets/CreatingTypologyRules5.png)

게재를 준비하는 동안 새 유형화 규칙이 적용되는지 확인합니다.

![이미지](/help/assets/CreatingTypologyRules6.png)

목록 구독 취소가 있는지 확인합니다.

![이미지](/help/assets/CreatingTypologyRules7.png)

## 이메일 최적화 {#email-optimization}

### SMTP {#smtp}

SMTP(Simple Mail Transfer Protocol)는 이메일 전송을 위한 인터넷 표준입니다.

규칙에 의해 확인되지 않은 SMTP 오류는 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]** 폴더를 삭제합니다. 이러한 오류 메시지는 기본적으로 연결할 수 없는 소프트 오류로 해석됩니다.

가장 일반적인 오류를 식별하고에 해당 규칙을 추가해야 합니다. **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]** smtp 서버의 피드백을 올바르게 확인하려면 다음을 수행하십시오. 이렇게 하지 않으면 플랫폼은 지정된 테스트 횟수 후에 불필요한 재시도(알 수 없는 사용자의 경우)를 수행하거나 특정 수신자를 잘못 격리합니다.

### 전용 IP {#dedicated-ips}

Adobe은 명성을 구축하고 게재 성능을 최적화하기 위해 상향 IP를 통해 각 고객을 위한 전용 IP 전략을 제공합니다.
