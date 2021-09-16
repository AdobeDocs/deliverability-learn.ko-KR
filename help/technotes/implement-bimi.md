---
title: BIMI(메시지 식별)를 위한 Gmail 브랜드 지표 구현
description: BIMI 구현 방법 알아보기
topics: Deliverability
hide: true
hidefromtoc: true
source-git-commit: ab1595bac7ef136eb001609b9017950a2d01cbb4
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---


# BIMI(메시지 식별)를 위한 Gmail 브랜드 지표 구현

Gmail은 최근에 BIMI](https://cloud.google.com/blog/products/identity-security/bringing-bimi-to-gmail-in-google-workspace)에 대한 일반적인 지원을 제공하는 [이라고 발표했습니다. 다음 사항을 포함하여 이 기능을 활용하려면 먼저 처리해야 하는 항목이 많습니다. 검증된 마크 인증서, 상표 로고, 올바른 형식의 로고, DMARC 설정 및 BIMI 레코드를 DNS에 게시합니다. 이 문서에서 이러한 단계를 모두 검토하십시오.

BIMI(메시지 식별 브랜드 지표)는 참여하는 플랫폼에서 보낸 사람의 이메일 옆에 승인된 로고를 표시할 수 있는 업계 표준입니다. 이 눈이 사람을 더 쉽게 참여를 높일 수 있을 뿐만 아니라, 발신자의 진위를 확인하는 데 도움이 되므로 피싱과 다른 스팸 술에도 대한 위험을 줄일 수 있습니다.

## 확인 표시 인증서

Gmail의 BIMI 프로그램의 주요 구성 요소 중 하나는 보낸 사람이 유효한 인증 기관에서 발급한 VMC(Verified Mark Certificate)를 가지고 있어야 하는 요구 사항입니다. 현재 이러한 VMC는 Entrust 및 DigiCert에서만 사용할 수 있지만, Gmail의 발표 이후 공급업체 목록이 늘어날 가능성이 있습니다.

VMC는 어떤 면에서 SSL 인증서와 비슷합니다. 표시하려는 각 로고에 대해 하나의 VMC가 필요하므로 많은 브랜드가 있는 경우 여러 VMC를 필요로 할 계획을 세워야 합니다. 다중 SAN VMC가 있는 경우 여러 도메인에서 각 VMC가 유효할 수 있습니다. 따라서 여러 전송 도메인에 하나의 로고가 표시되도록 하려면 하나의 VMC만 있으면 됩니다.

## 로고 상표

VMC를 가져오려면 먼저 완료해야 하는 다른 주요 단계가 있습니다. VMC를 얻으려면 표시하려는 로고가 8개의 승인된 글로벌 상표 및 특허 사무소 중 하나에 등록되어야 합니다.

* 미국 특허 및 상표 사무소(USPTO)
* 캐나다 지적재산권 사무소
* 유럽 연합 지적재산권 사무소
* 영국 지적재산권 사무소
* Deutsches 특허 - 운드 Markenamt
* 일본 상표청
* 스페인 특허 및 상표 사무소 O.A.
* IP 오스트레일리아

표시하려는 로고가 등록되지 않았거나 이러한 8개 조직 중 하나에 등록되지 않은 경우, VMC에 신청하기 전에 법률 팀과 협력하여 해당 사항을 해결해야 합니다.

## 로고 이미지 형식

또한 형식에 대한 BIMI 로고 요구 사항을 로고로 충족하는지 확인하는 것도 좋습니다. SVG 형식이어야 하며 SVG Portable/Secure(SVG-P/S) 프로필을 준수해야 합니다. 방법 지침은 [BIMI 작업 그룹](https://bimigroup.org/svg-conversion-tools-released)에서 확인할 수 있습니다.

## DMARC

BIMI에서 사용할 수 있는 전송 도메인에 DMARC가 완전히 구성되어 있는지 확인해야 합니다.

여기에는 P=가 격리 또는 거부로 설정되어 있는지 확인하는 작업이 포함됩니다. DMARC에서 P=None을 사용하는 경우에는 BIMI에 적합하지 않습니다. P=없음 설정은 도메인에서 나가는 메일을 알고 &quot;격리&quot; 또는 &quot;거부&quot;로 변경한 경우 아무 것도 실수로 차단되지 않도록 하려면 테스트 및 정보 수집 단계로 간주하는 것이 좋습니다. BIMI가 이용되기 전에, 당신은 그것을 넘어 집행으로 옮겨야 할 필요가 있습니다.

## DNS 항목

모든 것이 마침내 연결되었고 갈 준비가 되었으니 이제 BIMI로 DNS 항목을 업데이트할 차례입니다.

다음과 같은 간단한 항목입니다.

```
default._bimi.[domain] IN TXT “v=BIMI1; l=[SVG URL] 
```

해당 항목에 대한 세부 정보를 얻을 수 있으며 [BIMI 작업 그룹 사이트](https://bimigroup.org/implementation-guide)에서 무료 BIMI 검사기를 사용할 수도 있습니다.


## 주요 사항

Adobe Campaign 또는 Marketo 클라이언트인 경우 Adobe을 통해 BIMI DNS 업데이트를 만들 수 있습니다. 고객 지원 센터에 문의하여 요청을 받으십시오. Adobe이 BIMI가 제대로 작동하지 않는 경우 문제 해결에 도움을 줄 수도 있습니다.

상표 또는 검증된 마크 인증서에 대한 도움말은 법률 팀 및 승인된 VMC 공급업체와 함께 하십시오.

Gmail에 대한 BIMI 설정을 가져오는 것은 빠른 프로세스가 아니지만 마케팅 및 보안 관점에서 볼 때 상당한 이점을 얻을 수 있습니다.
