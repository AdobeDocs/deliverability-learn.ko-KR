---
source-git-commit: 5de602d6b75e524dac8688e40db0e96bdbafceba
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 7%

---
### 원클릭 목록 구독 취소를 지원하는 유형화 규칙 만들기:

**1. 새 유형화 규칙을 만듭니다.**

* 탐색 트리에서 &quot;새로 만들기&quot;를 클릭하여 새 유형화를 만듭니다


![이미지](/help/assets/CreatingTypologyRules1.png)



**2. 유형화 규칙을 계속 구성합니다.**

* 규칙 유형: 제어
* 단계: 타겟팅 시작 시
* 채널: 이메일
* 레벨: 원하는 대로
* 활성


![이미지](/help/assets/CreatingTypologyRules2.png)


**유형화 규칙의 Javascript를 코딩합니다.**


>[!NOTE]
>
>아래에 설명된 코드는 예시로서 참조되어야 한다.
>이 예에서는 다음 방법을 자세히 설명합니다.
>* URL 목록 구독 취소를 구성하고 헤더를 추가하거나 기존 mailto: 매개 변수를 추가하고 다음으로 바꿉니다. &lt;mailto..>>, https://...
>* List-Unsubscribe-Post 헤더에 추가
>게시물 URL 예제는 var headerUnsubUrl = &quot;https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=&lt;%= recipient.cryptedId %>&quot;를 사용합니다÷
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
var headerUnsubUrl = "https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=<%= recipient.cryptedId %>"; 
  
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



**3. 이메일에 유형화에 새 규칙을 추가합니다(기본 유형화는 정상).**

![이미지](/help/assets/CreatingTypologyRules4.png)



**4. 새 게재 준비(게재 속성의 추가 SMTP 헤더가 비어 있는지 확인)**

![이미지](/help/assets/CreatingTypologyRules5.png)



**5. 게재를 준비하는 동안 새 유형화 규칙이 적용되는지 확인합니다.**

![이미지](/help/assets/CreatingTypologyRules6.png)



**6. 목록 구독 취소가 있는지 확인합니다.**

![이미지](/help/assets/CreatingTypologyRules7.png)
