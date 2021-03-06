# 2022-06-12

## DNS란?

DNS(Domain Name System)는 인터넷 전화번호부입니다. 인간 은 nytimes.com 또는 espn.com과 같은 [도메인 이름 을 통해 온라인으로 정보에 액세스합니다.](https://www.cloudflare.com/learning/dns/glossary/what-is-a-domain-name/) 웹 브라우저는 [인터넷 프로토콜(IP)](https://www.cloudflare.com/learning/network-layer/internet-protocol/) 주소를 통해 상호 작용합니다. DNS는 브라우저가 인터넷 리소스를 로드할 수 있도록 도메인 이름을 [IP 주소 로 변환합니다.](https://www.cloudflare.com/learning/dns/glossary/what-is-my-ip-address/)

인터넷에 연결된 각 장치에는 다른 기계가 장치를 찾는 데 사용하는 고유한 IP 주소가 있습니다. DNS 서버는 192.168.1.1(IPv4)과 같은 IP 주소나 2400:cb00:2048:1::c629:d7a2(IPv6)와 같은 더 복잡한 영숫자 IP 주소를 기억할 필요가 없습니다.

## DNS 기본 사항

스마트폰이나 노트북부터 대규모 소매 웹 사이트의 콘텐츠를 서비스하는 서버에 이르기까지 인터넷상의 모든 컴퓨터는 숫자를 사용하여 서로를 찾고 통신합니다. 이러한 숫자를  **IP 주소**라고 합니다. 웹 브라우저를 열고 웹 사이트로 이동할 때는 긴 숫자를 기억해 입력할 필요가 없습니다. 그 대신 example.com과 같은  **도메인 이름**을 입력해도 원하는 웹 사이트로 갈 수 있습니다.   
www.example.com과 같이 사람이 읽을 수 있는 이름을 192.0.2.1과 같은 숫자 IP 주소로 변환하여 컴퓨터가 서로 통신할 수 있도록 합니다. 인터넷의 DNS 시스템은 이름과 숫자 간의 매핑을 관리하여 마치 전화번호부와 같은 기능을 합니다. DNS 서버는 이름을 IP 주소로 변환하여 도메인 이름을 웹 브라우저에 입력할 때 최종 사용자를 어떤 서버에 연결할 것인지를 제어합니다. 이 요청을 **쿼리**라고 부릅니다.

DNS 확인 이면의 프로세스를 이해하려면 DNS 쿼리가 통과해야 하는 다양한 하드웨어 구성 요소에 대해 배우는 것이 중요합니다. 웹 브라우저의 경우 DNS 조회는 "뒤에서" 발생하며 초기 요청 외에는 사용자 컴퓨터와의 상호 작용이 필요하지 않습니다.

## DNS 서비스 유형

**신뢰할 수 있는 DNS:**  **신뢰할 수 있는 DNS**  서비스는 개발자가 퍼블릭 DNS 이름을 관리하는 데 사용하는 업데이트 메커니즘을 제공합니다. 이 메커니즘을 통해 DNS 시스템은 DNS 쿼리에 응답하고 도메인 이름을 IP 주소로 변환합니다. 그러면 컴퓨터가 서로 통신할 수 있게 됩니다. 신뢰할 수 있는 DNS는 도메인에 대해 최종 권한이 있으며  **재귀적 DNS**  서버에 IP 주소 정보가 담긴 답을 제공할 책임이 있습니다.   
   
**재귀적 DNS:** 대개 클라이언트는 신뢰할 수 있는 DNS 서비스에 직접 쿼리를 수행하지 않습니다. 대신에 **해석기** 또는 **재귀적 DNS** 서비스라고 알려진 다른 유형의 DNS 서비스에 연결하는 경우가 일반적입니다. 재귀적 DNS 서비스는 호텔 컨시어지와 같은 역할을 합니다. DNS 레코드를 소유하고 있지 않지만 사용자를 대신해서 DNS 정보를 가져올 수 있는 중간자의 역할을 합니다. 재귀적 DNS가 일정 기간 **캐시된** 또는 저장된 DNS 참조를 가지고 있는 경우, 소스 또는 IP 정보를 제공하여 DNS 쿼리에 답을 합니다. 그렇지 않다면, 해당 정보를 찾기 위해 쿼리를 하나 이상의 신뢰할 수 있는 DNS 서버에 전달합니다.

## DNS는 트래픽을 웹 애플리케이션에 어떻게 라우팅합니까?

다음 다이어그램은 재귀적 DNS 서비스와 신뢰할 수 있는 DNS 서비스가 서로 연계하여 최종 사용자를 웹 사이트 또는 애플리케이션으로 라우팅하는 방법에 대한 개요를 보여줍니다.  

![how-route-53-routes-traffic](https://d1.awsstatic.com/Route53/how-route-53-routes-traffic.8d313c7da075c3c7303aaef32e89b5d0b7885e7c.png "how-route-53-routes-traffic")

1.  사용자가 웹 브라우저를 열어 주소 표시줄에 www.example.com을 입력하고 Enter 키를 누릅니다.
2.  www.example.com에 대한 요청은 일반적으로 케이블 인터넷 공급업체, DSL 광대역 공급업체 또는 기업 네트워크 같은 인터넷 서비스 제공업체(ISP)가 관리하는 DNS 해석기로 라우팅됩니다.
3.  ISP의 DNS 해석기는 www.example.com에 대한 요청을 DNS 루트 이름 서버에 전달합니다.
4.  ISP의 DNS 해석기는 www.example.com에 대한 요청을 이번에는 .com 도메인의 TLD 이름 서버 중 하나에 다시 전달합니다. .com 도메인의 이름 서버는 example.com 도메인과 연관된 4개의 Amazon Route 53 이름 서버의 이름을 사용하여 요청에 응답합니다.
5.  ISP의 DNS 해석기는 Amazon Route 53 이름 서버 하나를 선택해 www.example.com에 대한 요청을 해당 이름 서버에 전달합니다.
6.  Amazon Route 53 이름 서버는 example.com 호스팅 영역에서 www.example.com 레코드를 찾아 웹 서버의 IP 주소 192.0.2.44 등 연관된 값을 받고 이 IP 주소를 DNS 해석기로 반환합니다.
7.  ISP의 DNS 해석기가 마침내 사용자에게 필요한 IP 주소를 확보하게 됩니다. 해석기는 이 값을 웹 브라우저로 반환합니다. 또한, DNS 해석기는 다음에 누군가가 example.com을 탐색할 때 좀 더 빠르게 응답할 수 있도록 사용자가 지정하는 일정 기간 example.com의 IP 주소를 캐싱(저장)합니다. 자세한 내용은 Time to Live(TTL)를 참조하세요.
8.  웹 브라우저는 DNS 해석기로부터 얻은 IP 주소로 www.example.com에 대한 요청을 전송합니다. 여기가 콘텐츠가 있는 곳으로, 예를 들어 웹 사이트 엔드포인트로 구성된 Amazon S3 버킷 또는 Amazon EC2 인스턴스에서 실행되는 웹 서버입니다.
9.  192.0.2.44에 있는 웹 서버 또는 그 밖의 리소스는 www.example.com의 웹 페이지를 웹 브라우저로 반환하고, 웹 브라우저는 이 페이지를 표시합니다.
## REFERENCE
[CLOUDFLARE](https://www.cloudflare.com/en-gb/learning/dns/what-is-dns/)   
   
[AWS](https://aws.amazon.com/ko/route53/what-is-dns/)
