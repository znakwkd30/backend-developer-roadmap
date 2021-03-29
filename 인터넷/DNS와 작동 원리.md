# DNS와 작동 원리

## DNS 란?
도메인 네임 시스템(Domain Name System, DNS)은 호스트의 도메인 네임(www.example.com)을 네트워크 주소(192. ...)로 변환하거나, 그 반대의 역할을 수행하는 시스템이다.  

예를 들면 우리가 자주 접하는 `naver.com`, `google.com` 모두 DNS를 가진 DN(Domain Name)이라고 할 수 있다.  

- `DNS` 시스템은 이름과 숫자 간의 매핑을 관리하여 마치 전화번호부와 같은 기능을 한다
- `DNS` 서버는 사용자가 도메인 이름을 브라우저에 입력하면, 사용자를 어떤 서버와 연결할 것인지 제어한다. 이러한 요청을 쿼리라고 한다.

## DNS 서비스 유형

### ① 신뢰할 수 있는 DNS
- 개발자가 public `DNS` 이름을 관리하는데 사용하는 업데이트 매커니즘을 제공한다.
- 이를 통해 `DNS` 쿼리에 응답하여 도메인 이름을 IP 주소로 변환한다.
- 신뢰할 수 있는 `DNS` 도메인에 대해 최종 권한이 있다.
- 재귀적 `DNS` 서버에 IP 주소 정보가 담긴 답을 제공할 책임이 있다.

### ② 재귀적 DNS
- 보통 클라이언트는 신뢰할 수 있는 DNS 서비스에 직접 쿼리를 수행하지 않음.
- 해석기 또는 재귀적 DNS 서비스라고 알려진 다른 유형의 DNS 서비스에 연결하는 경우가 일반적임
- 재귀적 DNS 서비스는 호텔 컨시어지와 같은 역할을 한다.
- DNS 레코드를 소유하고 있지 않지만 사용자를 대신해서 DNS 정보를 가져올 수 있는 중간자의 역할을 한다.
- 일정 기간 동안 캐시된 또는 저장된 DNS 레퍼런스를 가지고 있는 경우, 소스 또는 IP 정보를 제공하여 DNS 쿼리에 답을 하거나, 해당 정보를 찾기 위해 쿼리를 하나 이상의 신뢰할 수 있는 DNS 서버에 전달한다.

## DNS의 작동 원리
![image](https://media.vlpt.us/images/goban/post/5717ceb7-79f2-41d3-86e5-7e48bfd6ac58/DNSLogic.png)  

1. 웹 브라우저에 `www.naver.com`을 입력하면 먼저 Local DNS에게 `www.naver.com` 이라는 hostname에 대한 IP 주소를 질의하여 Local DNS에 없으면 다른 DNS Name 서버 정보를 받음(Root DNS 정보 전달 받음)
2. Root DNS 서버에 `www.naver.com` 질의

```
Root DNS (루트 네임 서버) 는 인터넷의 도메인 네임 시스템의 루트 존이다. 루트 존의 레코드의 요청에 직접 응답하고 적절한 최상위 도메인에 대해 권한이 있는 네임 서버 목록을 반환함으로써 다른 요청에 응답한다. 전세계에 961개의 루트 DNS가 운영되고 있다.
```
3. Root DNS 서버로 부터 `com 도메인`을 관리하는 TLD(Top-Level Domain) 이름 서버 정보 전달 받음
4. TLD에 `www.naver.com` 질의
5. TLD에서 `name.com` 관리하는 DNS 정보 전달
6. `naver.com` 도메인을 관리하는 DNS 서버에 `www.naver.com` 호스트 네임에 대한 IP 주소 질의
7. Local DNS 서버에게 `www.naver.com`에 대한 IP 주소 응답
8. Local DNS 는 `www.naver.com`에 대한 IP 주소를 캐싱하고 IP 주소 전달

```
Local DNS 서버가 여러 DNS 서버에 차례대로 (Root DNS 서버 -> com DNS 서버 -> naver.com DNS 서버) 요청하여 그 답을 찾는 과정을 Recursive Query 라고 부른다
```

## 참고 자료📚
[DNS와 작동원리 velog](https://velog.io/@goban/DNS%EC%99%80-%EC%9E%91%EB%8F%99%EC%9B%90%EB%A6%AC)  
[DNS? 작동원리 velog](https://velog.io/@doomchit_3/Internet-DNS-%EC%9E%91%EB%8F%99%EC%9B%90%EB%A6%AC-IMBETPY)
