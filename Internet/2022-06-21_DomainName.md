# 2022-06-21 

# Domain Name

**전제 조건**: 먼저 [인터넷이 작동하는 방식 과](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work) [URL이 무엇인지](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL) 이해해야 합니다 .

## 요약

도메인 이름은 인터넷 인프라의 핵심 부분입니다. 그들은 인터넷에서 사용할 수 있는 모든 웹 서버에 대해 사람이 읽을 수 있는 주소를 제공합니다.

인터넷에 연결된 모든 컴퓨터 는 IPv4 주소(예: ) 또는 IPv6 주소(예 : )와 같은 공용 IP 주소 를 통해 연결할 수 있습니다 .`173.194.121.32``2027:0da8:8b73:0000:0000:8a2e:0370:1337`

컴퓨터는 이러한 주소를 쉽게 처리할 수 있지만 사람들은 누가 서버를 운영하는지 또는 웹사이트에서 어떤 서비스를 제공하는지 찾기가 어렵습니다. IP 주소는 기억하기 어렵고 시간이 지남에 따라 변경될 수 있습니다.

이러한 모든 문제를 해결하기 위해 우리는 도메인 이름이라는 사람이 읽을 수 있는 주소를 사용합니다.

## [도메인 이름의 구조](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_domain_name#structure_of_domain_names "도메인 이름 구조에 대한 퍼머링크")

**도메인 이름은 점으로 구분되고 오른쪽에서 왼쪽으로 읽는** 여러 부분(한 부분, 두 부분, 세 부분...)으로 구성된 간단한 구조를 가지고 있습니다 .

![MDN 도메인 이름 분석](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_domain_name/structure.png)

각 부분은 전체 도메인 이름에 대한 특정 정보를 제공합니다.

[TLD](https://developer.mozilla.org/en-US/docs/Glossary/TLD) (최상위 도메인).

TLD는 사용자에게 도메인 이름 뒤에 있는 서비스의 일반적인 목적을 알려줍니다. 가장 일반적인 TLD( `.com`, `.org`, `.net`)는 웹 서비스가 특정 기준을 충족할 것을 요구하지 않지만 일부 TLD는 더 엄격한 정책을 적용하여 목적이 무엇인지 더 명확하게 합니다. 예를 들어:

-   `.us`, `.fr`또는 같은 로컬 TLD `.se`는 서비스가 특정 언어로 제공되거나 특정 국가에서 호스팅되도록 요구할 수 있습니다. 특정 언어 또는 국가의 리소스를 나타내야 합니다.
-   포함된 TLD `.gov`는 정부 부서에서만 사용할 수 있습니다.
-   TLD 는 `.edu`교육 및 학술 기관에서만 사용할 수 있습니다.

TLD에는 특수 문자와 라틴 문자가 포함될 수 있습니다. TLD의 최대 길이는 63자이지만 대부분은 약 2-3자입니다.

TLD의 전체 목록은 [ICANN](https://www.icann.org/resources/pages/tlds-2012-02-25-en) 에서 관리합니다 .


## [도메인 이름 구매](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_domain_name#buying_a_domain_name "도메인 이름 구매에 대한 퍼머링크")

### 누가 도메인 이름을 소유합니까?

"도메인 이름을 구입"할 수 없습니다. 이는 사용하지 않은 도메인 이름이 결국 다른 사람이 다시 사용할 수 있도록 하기 위한 것입니다. 모든 도메인 이름을 구입한 경우 웹은 잠겨 있어 아무도 사용할 수 없는 사용하지 않는 도메인 이름으로 빠르게 채워집니다.

대신 1년 이상 도메인 이름을 사용할 수 있는 권한에 대해 비용을 지불합니다. 권리를 갱신할 수 있으며 갱신은 다른 사람의 신청보다 우선합니다. 그러나 귀하는 도메인 이름을 소유한 적이 없습니다.

레지스트라라는 회사는 도메인 이름 레지스트리를 사용하여 귀하를 도메인 이름에 연결하는 기술 및 관리 정보를 추적합니다.

### 도메인 이름을 선택하는 방법

Verisign의 최신 업계 보고서에 따르면 [모든 최상위 도메인에 걸쳐 3억 6,600만 개의 도메인 이름이 등록](https://www.verisign.com/en_US/domain-names/dnib/index.xhtml)되어 있으며, 매일 수천 개 이상의 도메인 이름이 등록됩니다. 이것은 가장 좋은 도메인 이름은 이미 사용되고 있다는 것을 의미할 뿐만 아니라 내가 갖고 있는 모든 아이디어를 다른 사람이 사용하기까지 남은 시간이 얼마 없다는 것을 의미합니다.

## DNS 새로 고침

DNS 데이터베이스는 전 세계의 모든 DNS 서버에 저장되며 이 모든 서버는 "권한 있는 이름 서버" 또는 "최상위 수준 DNS 서버"라는 몇 가지 특수 서버를 나타냅니다. — 이들은 시스템을 관리하는 보스 서버와 같습니다.

등록 대행자가 주어진 도메인에 대한 정보를 생성하거나 업데이트할 때마다 모든 DNS 데이터베이스에서 정보를 새로 고쳐야 합니다. 주어진 도메인에 대해 알고 있는 각 DNS 서버는 정보가 자동으로 무효화되고 새로 고쳐지기 전에 일정 시간 동안 정보를 저장합니다(DNS 서버는 권한 있는 서버에 쿼리하여 업데이트된 정보를 가져옴). 따라서 이 도메인 이름을 알고 있는 DNS 서버가 최신 정보를 얻는 데 시간이 걸립니다.

## REFERENCE
[WixBlog](https://ko.wix.com/blog/post/what-is-a-domain)   
   
[mdn web docs](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_domain_name#buying_a_domain_name)
