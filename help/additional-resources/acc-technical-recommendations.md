---
title: Campaign Classic - 기술 추천
description: Adobe Campaign Classic을 통해 전달률을 향상시키는 데 사용할 수 있는 기법, 구성 및 툴을 살펴볼 수 있습니다.
feature: 연습
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 1e539b5df54250a5927701009e7a9c84e5d73fae
workflow-type: tm+mt
source-wordcount: '1579'
ht-degree: 1%

---


# Campaign Classic - 기술 권장 사항 {#technical-recommendations}

Adobe Campaign Classic을 사용할 때 배달 속도를 향상시키는 데 사용할 수 있는 몇 가지 기법, 구성 및 도구가 아래에 나와 있습니다.

## 구성 {#configuration}

### 역방향 DNS {#reverse-dns}

Adobe Campaign은 IP 주소에 대해 역 DNS가 제공되었는지 그리고 이것이 IP를 올바르게 가리키는지 확인합니다.

네트워크 구성의 중요한 점은 보내는 메시지의 각 IP 주소에 대해 올바른 역방향 DNS가 정의되어 있는지 확인합니다. 즉, 지정된 IP 주소의 경우 일치하는 DNS(A 레코드)가 초기 IP 주소로 다시 루핑되는 PTR 레코드(역방향 DNS 레코드)가 있습니다.

역 DNS에 대한 도메인 선택은 특정 ISP를 처리할 때 영향을 줍니다. 특히 AOL은 역방향 DNS와 동일한 도메인에 주소가 있는 피드백 루프만 허용합니다([피드백 루프](#feedback-loop) 참조).

>[!NOTE]
>
>[이 외부 도구](https://mxtoolbox.com/SuperTool.aspx)를 사용하여 도메인의 구성을 확인할 수 있습니다.

### MX 규칙 {#mx-rules}

MX 규칙(메일 교환기)은 전송 서버와 수신 서버 간의 통신을 관리하는 규칙입니다.

보다 정확하게 Adobe Campaign MTA(메시지 전송 에이전트)가 각 개별 이메일 도메인 또는 ISP(예: hotmail.com, comcast.net)로 이메일을 보내는 속도를 제어하는 데 사용됩니다. 이러한 규칙은 일반적으로 ISP가 게시한 제한을 기준으로 합니다(예: 각 SMTP 연결당 20개 이상의 메시지를 포함하지 않음).

>[!NOTE]
>
>Adobe Campaign Classic의 MX 관리에 대한 자세한 내용은 [이 섹션](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/email-deliverability.html#mx-configuration)을 참조하십시오.

### TLS {#tls}

TLS(전송 레이어 보안)는 두 이메일 서버 간의 연결을 보호하고 대상 받는 사람 이외의 다른 사람이 이메일 컨텐츠를 읽지 못하도록 보호하는 데 사용할 수 있는 암호화 프로토콜입니다.

### 보낸 사람의 도메인 {#sender-domain}

HELO 명령에 사용되는 도메인을 정의하려면 인스턴스의 구성 파일(conf/config-instance.xml)을 편집하고 &quot;localDomain&quot; 속성을 다음과 같이 정의합니다.

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

MAIL FROM 도메인은 기술 바운스 메시지에 사용되는 도메인입니다. 이 주소는 배포 마법사나 NmsEmail_DefaultErrorAddr 옵션을 통해 정의됩니다.

### SPF 레코드 {#dns-configuration}

SPF 레코드는 현재 DNS 서버에 TXT 유형 레코드(코드 16) 또는 SPF 유형 레코드(코드 99)로 정의할 수 있습니다. SPF 레코드는 문자열 형태를 취합니다. 예:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

도메인에 대한 이메일을 보낼 수 있는 권한을 가진 2개의 IP 주소 12.34.56.78 및 12.34.56.79을 정의합니다. **~** all은 다른 모든 주소를 SoftFail로 해석해야 함을 의미합니다.

SPF 레코드 정의를 위한 Recommendations:

* 마지막으로 **~all**(SoftFail) 또는 **-all**(실패)을 추가하여 정의된 서버 이외의 모든 서버를 거부합니다. 이렇게 하지 않으면 서버는 중립 평가를 통해 이 도메인을 위조할 수 있습니다.
* **ptr**(openspf.org는 이 값이 비싸고 신뢰할 수 없는 것으로 권장)을 추가하지 마십시오.

>[!NOTE]
>
>[이 섹션](/help/additional-resources/authentication.md#spf)의 SPF에 대해 자세히 알아보십시오.

## 인증

>[!NOTE]
>
>[이 섹션](/help/additional-resources/authentication.md)의 다양한 이메일 인증 양식에 대해 자세히 알아보십시오.

### DKIM {#dkim-acc}

>[!NOTE]
>
>호스팅 또는 하이브리드 설치의 경우, [향상된 MTA](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/sending-with-enhanced-mta.html#sending-messages)로 업그레이드한 경우 모든 도메인의 모든 메시지에 대해 향상된 MTA가 DKIM 이메일 인증 서명을 수행합니다.

Adobe Campaign Classic에서 [DKIM](/help/additional-resources/authentication.md#dkim)을 사용하려면 다음 전제 조건이 필요합니다.

**Adobe Campaign 옵션 선언**:Adobe Campaign에서 DKIM 개인 키는 DKIM 선택기 및 도메인을 기반으로 합니다. 현재 선택기가 다른 동일한 도메인/하위 도메인에 대해 여러 개의 개인 키를 만들 수 없습니다. 플랫폼 또는 이메일에서 인증에 어느 선택기 도메인/하위 도메인을 사용해야 하는지를 정의할 수 없습니다. 플랫폼에서 개인 키 중 하나를 선택할 수도 있습니다. 즉, 인증이 실패할 가능성이 높습니다.

* Adobe Campaign 인스턴스에 대해 DomainKeys를 구성한 경우 [도메인 관리 규칙](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#email-management-rules)에서 **dkim**&#x200B;을 선택하기만 하면 됩니다. 그렇지 않은 경우 DomainKeys(DKIM 대신)와 동일한 구성 단계(개인/공개 키)를 따릅니다.
* DKIM과 동일한 도메인에 대해 DomainKeys와 DKIM을 모두 사용할 필요는 없습니다. 이는 DomainKeys의 향상된 버전입니다.
* 다음 도메인은 현재 DKIM의 유효성을 검사합니다.AOL, Gmail.

## 피드백 루프 {#feedback-loop-acc}

피드백 루프는 메시지를 전송하는 데 사용되는 IP 주소 범위에 대해 ISP 수준에서 지정된 이메일 주소를 선언하여 작동합니다. ISP는 이 사서함에 바운스 메시지에 대해 수행되는 작업과 유사한 방법으로 받는 사람이 스팸으로 보고한 메시지를 보냅니다. 불만 사항이 있는 사용자에 대한 향후 제공을 차단하도록 플랫폼을 구성해야 합니다. 적절한 옵트아웃 링크를 사용하지 않더라도 더 이상 연락하지 않는 것이 중요합니다. ISP가 IP 주소를 해당에 추가할 것이라는 이러한 불만 사항을 바탕으로 차단 목록 합니다. ISP에 따라, 약 1%의 불만 비율은 IP 주소를 차단하게 됩니다.

현재 피드백 루프 메시지의 형식을 정의하기 위해 표준을 작성하고 있습니다.[ARF(피드백 보고 형식)](https://tools.ietf.org/html/rfc6650).

인스턴스에 대한 피드백 루프를 구현하려면 다음이 필요합니다.

* 인스턴스 전용 사서함(바운스 사서함)입니다.
* 인스턴스에 전용 IP 전송 주소

Adobe Campaign에서 단순 피드백 루프를 구현하면 바운스 메시지 기능이 사용됩니다. 피드백 루프 사서함은 바운스 사서함으로 사용되고 이러한 메시지를 감지하는 규칙이 정의됩니다. 메시지를 스팸으로 보고한 수신자의 이메일 주소가 격리 목록에 추가됩니다.

* **거부됨** 및 **하드** 유형으로 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;에 바운스 메일 규칙 **Feedback_loop**&#x200B;을 만들거나 수정합니다.
* 피드백 루프를 위해 사서함이 특별히 정의된 경우 **[!UICONTROL Administration > Platform > External accounts]**&#x200B;에 새 외부 바운스 메일 계정을 만들어 액세스할 매개 변수를 정의합니다.

이 메커니즘은 불만 알림을 처리하는 즉시 작동합니다. 이 규칙이 제대로 작동하는지 확인하려면 계정을 일시적으로 비활성화하여 이러한 메시지를 수집하지 않도록 한 다음 피드백 루프 사서함의 내용을 수동으로 확인할 수 있습니다. 서버에서 다음 명령을 실행합니다.

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

여러 인스턴스에 대해 하나의 피드백 루프 주소를 사용해야 하는 경우 다음을 수행해야 합니다.

* 인스턴스가 있는 수만큼 사서함에서 받은 메시지를 복제합니다.
* 각 우편함을 한 번의 인스턴스씩 가져와야 합니다
* 관련 메시지만 처리하도록 인스턴스를 구성합니다.인스턴스 정보는 Adobe Campaign에서 보낸 메시지의 메시지 ID 헤더에 포함되므로 피드백 루프 메시지도 찾을 수 있습니다. 인스턴스 구성 파일에서 **checkInstanceName** 매개 변수를 지정하기만 하면 됩니다(기본적으로 인스턴스가 확인되지 않으며 이로 인해 특정 주소가 잘못 격리될 수 있음).

   ```
   <serverConf>
     <inMail checkInstanceName="true"/>
   </serverConf>
   ```

Adobe Campaign의 Deliverability Service는 다음 ISP에 대한 피드백 루프 서비스 구독을 관리합니다.AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, OpenQ, RoadRunner, Synacor, Telarry, UnitedOnline, USA, XS ALL, Yahoo, Yandex, Zoho

## 목록-가입 해지 {#list-unsubscribe}

### 목록-가입 해지 정보 {#about-list-unsubscribe}

최적의 배달 가능성 관리를 위해 **List-Unsubscribe**&#x200B;라는 SMTP 헤더를 추가해야 합니다.

이 헤더를 &quot;스팸으로 신고&quot; 아이콘의 대안으로 사용할 수 있습니다. 이메일 인터페이스에 구독 취소 링크로 표시됩니다.

이 기능을 사용하면 평판이 보호되고 피드백은 구독이 없는 것으로 실행됩니다.

목록-가입 해지를 사용하려면 다음과 유사한 명령줄을 입력해야 합니다.

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

>[!CAUTION]
>
>위의 예는 수신자 테이블을 기반으로 합니다. 다른 테이블에서 데이터베이스 구현이 수행된 경우 올바른 정보로 명령줄을 다시 표기해야 합니다.

다음 명령줄을 사용하여 동적 **List-Unsubscribe**&#x200B;을 만들 수 있습니다.

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail, Outlook.com 및 Microsoft Outlook에서 이 방법을 지원하며 인터페이스에서 바로 구독 취소 단추를 사용할 수 있습니다. 이 방법은 불만 사항을 줄여줍니다.

다음 방법 중 하나를 사용하여 **List-Unsubscribe**&#x200B;을(를) 구현할 수 있습니다.

* 배달 템플릿](#adding-a-command-line-in-a-delivery-template)에 명령행 추가[
* [유형화 규칙 만들기](#creating-a-typology-rule)

### 배달 템플릿 {#adding-a-command-line-in-a-delivery-template}에 명령줄 추가

이메일의 SMTP 헤더의 추가 섹션에 명령줄을 추가해야 합니다.

이 추가 작업은 각 이메일 또는 기존 배달 템플릿에서 수행할 수 있습니다. 이 기능을 포함하는 새 배달 템플릿을 만들 수도 있습니다.

### 유형화 규칙 만들기 {#creating-a-typology-rule}

규칙에는 명령줄을 생성하는 스크립트가 포함되어야 하며 이 스크립트는 이메일 헤더에 포함되어야 합니다.

>[!NOTE]
>
>다음과 같은 유형 규칙을 만드는 것이 좋습니다.목록 구독 취소 기능은 각 이메일에 자동으로 추가됩니다.

1. 목록 구독 취소:&lt;mailto:unsubscribe@domain.com>

   **가입 해지** 링크를 클릭하면 사용자의 기본 이메일 클라이언트가 열립니다. 이 유형 규칙을 이메일을 만드는 데 사용되는 유형 분석에 추가해야 합니다.

1. 목록 구독 취소:`<https://domain.com/unsubscribe.jsp>`

   **가입 해지** 링크를 클릭하면 사용자가 구독 취소 양식으로 리디렉션됩니다.

   예:

   ![](../assets/s_tn_del_unsubscribe_param.png)

>[!NOTE]
>
>[이 섹션](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/campaign-optimization/about-campaign-typologies.html#typology-rules)에서 Adobe Campaign Classic에서 분류 규칙을 만드는 방법을 알아봅니다.

## 이메일 최적화 {#email-optimization}

### SMTP {#smtp}

SMTP(Simple mail transfer protocol)는 이메일 전송을 위한 인터넷 표준입니다.

규칙에서 검사하지 않는 SMTP 오류는 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]** 폴더에 나열됩니다. 이러한 오류 메시지는 기본적으로 연결할 수 없는 소프트 오류로 해석됩니다.

SMTP 서버의 피드백을 올바르게 검증하려면 가장 일반적인 오류를 식별하고 해당 규칙을 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]**&#x200B;에 추가해야 합니다. 이 옵션을 사용하지 않으면 플랫폼에서 불필요한 재시도를 하거나(알 수 없는 사용자의 경우) 지정된 테스트 수 이후에 특정 받는 사람을 격리 대상으로 잘못 지정합니다.

### 전용 IP {#dedicated-ips}

Adobe은 명성을 구축하고 전달 성능을 최적화하기 위해 각 고객에게 구현 IP를 제공하는 전용 IP 전략을 제공합니다.
