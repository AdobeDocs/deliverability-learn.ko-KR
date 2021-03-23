---
title: 인증
description: SPF, DKIM 및 DMARC 인증 방법에 대한 자세한 내용을 살펴보십시오.
feature: Journey Orchestration용
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 1e539b5df54250a5927701009e7a9c84e5d73fae
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---


# 인증

## SPF {#spf}

SPF(Sender Policy Framework)는 도메인 소유자가 해당 도메인을 대신하여 이메일을 보낼 수 있는 이메일 서버를 지정할 수 있도록 하는 이메일 인증 표준입니다. 이 표준은 이메일의 &quot;반환 경로&quot; 헤더에 있는 도메인을 사용합니다(&quot;편지 봉투 보낸 사람&quot; 주소라고도 함).

>[!NOTE]
>
>[이 외부 도구](https://www.kitterman.com/spf/validate.html)를 사용하여 SPF 레코드를 확인할 수 있습니다.

SPF는 이메일에 사용된 도메인 이름이 위조되지 않도록 어느 정도 할 수 있는 기술입니다. 도메인에서 메시지를 받으면 도메인의 DNS 서버를 쿼리합니다. 이 응답은 이 도메인에서 이메일을 보낼 수 있도록 허가된 서버를 자세히 설명하는 짧은 레코드(SPF 레코드)입니다. 도메인 소유자만 이 레코드를 변경할 수 있는 수단을 가지고 있다고 가정할 경우, 적어도 &quot;@&quot; 오른쪽의 부분이 아닌 보낸 사람 주소를 위조할 수 없습니다.

최종 [RFC 4408 사양](https://www.rfc-editor.org/info/rfc4408)에서 메시지 요소 두 개를 사용하여 보낸 사람으로 간주되는 도메인을 결정합니다.SMTP &quot;HELO&quot;(또는 &quot;ELO&quot;) 명령으로 지정된 도메인과 &quot;반환 경로&quot;(또는 &quot;MAIL FROM&quot;) 헤더의 주소로 지정된 도메인(바운스 주소)도 지정합니다. 서로 다른 고려 사항을 사용하면 이러한 값 중 하나만 고려할 수 있습니다.두 소스 모두 동일한 도메인을 지정하도록 하는 것이 좋습니다.

SPF를 검사하면 보낸 사람 도메인의 유효성을 평가할 수 있습니다.

* **없음**:평가를 수행할 수 없습니다.
* **중립**:쿼리된 도메인이 평가를 활성화하지 않습니다.
* **통과**:도메인이 인증된 도메인으로 간주됩니다.
* **실패**:도메인이 위조되어 메시지가 거부되어야 합니다.
* **소프트 실패**:도메인은 위조된 것일 수 있지만 이러한 결과에 근거하여 메시지가 거부되어서는 안 됩니다.
* **임시 오류**:일시적인 오류가 평가를 중지했습니다. 메시지는 거부할 수 있습니다.
* **PermError**:도메인의 SPF 레코드가 잘못되었습니다.

DNS 서버 수준에서 수행된 기록을 고려하는 데 최대 48시간이 걸릴 수 있다는 점을 주목하십시오. 이 지연은 수신 서버의 DNS 캐시가 새로 고쳐지는 빈도에 따라 다릅니다.

## DKIM {#dkim}

DKIM(DomainKeys Identified Mail) 인증은 SPF의 후속 작업입니다. 이 기능은 받는 이메일 서버가 보낸 것이라고 주장하는 사람 또는 엔티티에 의해 메시지를 실제로 보냈는지, 메시지 컨텐츠가 원래 전송된 시간(및 DKIM &quot;signed&quot;) 및 수신한 시간 사이에 변경되었는지 여부를 확인하는 공개 키 암호화를 사용합니다. 이 표준은 일반적으로 &quot;보낸 사람&quot; 또는 &quot;보낸 사람&quot; 헤더의 도메인을 사용합니다.

DKIM은 DomainKeys, Yahoo! 및 Cisco Identified Internet Mail 인증 원칙을 준수하고 발신자 도메인의 신뢰성을 확인하고 메시지의 무결성을 보장하는 데 사용됩니다.

DKIM은 **DomainKeys** 인증을 대체했습니다.

DKIM을 사용하려면 몇 가지 전제 조건이 필요합니다.

* **보안**:암호화는 DKIM의 핵심 요소입니다. DKIM의 보안 수준을 보장하기 위해 권장되는 최적의 암호화 크기는 1024b입니다. DKIM 키가 낮으면 대부분의 액세스 공급자가 유효한 것으로 간주하지 않습니다.
* **평판**:명성은 IP 및/또는 도메인을 기반으로 하지만 덜 투명한 DKIM 선택기도 고려해야 할 핵심 요소입니다. 선택기를 선택하는 것은 중요합니다.누구나 사용할 수 있고 따라서 평판이 좋지 않은 &quot;기본값&quot;을 유지하지 마십시오. **유지 vs. 획득 통신** 및 인증에 대해 다른 선택기를 구현해야 합니다.

[이 섹션](/help/additional-resources/acc-technical-recommendations.md#dkim-acc)에서 Campaign Classic을 사용할 때 DKIM 사전 요구 사항에 대해 자세히 알아보십시오.

## DMARC {#dmarc}

DMARC(도메인 기반 메시지 인증, 보고 및 준수)는 가장 최신 이메일 인증 양식이며, SPF 및 DKIM 인증을 통해 이메일 전달 여부를 확인합니다. DMARC는 다음과 같은 두 가지 중요한 방법으로 독특하고 강력합니다.

* 적합성 - 발신자가 인증하지 못하는 메시지를 사용하여 수행할 작업을 ISP에 지시할 수 있도록 해줍니다(예:동의하지 마십시오.)
* 보고 - &quot;보낸 사람&quot; 도메인 및 각 항목에 사용되는 IP 주소와 함께 DMARC 인증에 실패한 모든 메시지를 표시하는 자세한 보고서를 전송자에게 제공합니다. 이를 통해 회사는 인증이 실패하고 있고 일부 유형의 &quot;수정&quot;(예: SPF 레코드에 IP 주소 추가) 및 이메일 도메인에서 피싱 시도 소인과 출현을 필요로 하는 정당한 이메일을 식별할 수 있습니다.

>[!NOTE]
>
>DMARC는 [250ok](https://250ok.com/)에서 생성된 보고서를 활용할 수 있습니다.
