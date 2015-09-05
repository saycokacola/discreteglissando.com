---
layout: post
title: "ASUS RT-AC87U 설치와 LG U+ IPTV 설정"
date: 2015-08-08 21:45:24 +0900
comments: true
categories: technology
---

{% img /images/asus_rt-ac87u.jpg %}

[LG U+](http://www.uplus.co.kr/)에서 기본적으로 제공하는 [네트워크 공유기](https://en.wikipedia.org/wiki/network_router)는 그 기능이 좋지 않아서 [와이파이](https://en.wikipedia.org/wiki/Wifi)를 연결하였을 때 중간에 연결이 끊기거나 잘 연결이 되지 않는 등의 문제가 자주 발생한다. 문제를 해결해보고자 [ipTime](http://iptime.com/iptime/) 공유기로 교체를 해보았었는데, 그럴 경우에는 네트워크가 끊기는 문제는 일어나지 않았지만 [IPTV](https://en.wikipedia.org/wiki/IPTV)의 시청이 원활하지 않고 자주 끊기는 문제가 발생하였다. 그렇기에 어쩔 수 없이 기존의 공유기를 계속해서 쓰고있던 중, [ASUS](http://www.asus.com/)의 [RT-AC87U](https://www.asus.com/kr/Networking/RTAC87U/)에 대해서 알게되었다.

<!--more-->

RT-AC87U는 '끝판왕'이라 불리는 공유기로, 2334Mbps 듀얼 밴드 지원, 802.11ac 와이파이 라우터, 세계 최초 4x4 MU-MIMO 안테나 디자인 등의 스펙을 자랑하고, USB 2.0 포트 또는 USB 3.0 포트에 외장 하드디스크를 연결하여 [NAS](https://en.wikipedia.org/wiki/Network_access_server) 서버로 사용하는 것도 가능하다. 또한 공유기의 MAC 주소를 변경할 수 있고 IPTV와 관련된 기능들을 지원한다. 듀얼 밴드와 IPTV 지원은 비교적 더 저렴한 ipTime 최신 공유기들에도 있는 기능들이지만, 여러 리뷰와 포스트에서 RT-AC87U의 성능과 와이파이 커버 영역에 대한 호평을 읽을 수 있었기 때문에 조금 더 값을 지불하더라도 RT-AC87U를 구입하게 되었다.

일반적인 네트워크 공유기와 똑같이 설치를 마친 후에 나의 맥북 프로에서 DHCP 임대 갱신을 하려 했더니 네트워크에 제대로 접속이 되지 않았다. 반면에 [아버지](http://www.partialrecall.net/)의 맥 미니는 정상적으로 연결이 되었다. 왜 그런 문제가 일어나는지 확인하기 위해 공유기의 포트를 다시 확인하니 `teaming port`라고 명시가 되어있는 포트에 연결한 [허브](https://en.wikipedia.org/wiki/Ethernet_hub)만 정상적으로 동작하고 있는 것이었다. 우리 집에서 현재 사용하고 있는 허브들은 [teaming](https://en.wikipedia.org/wiki/Link_aggregation)을 지원하지 않기에 굳이 `teaming port`가 아니더라도 장상적으로 동작을 해야할 것 같지만, 우선은 `teaming port`에 연결해 놓았다. 이 부분에 대해서는 추가적인 조사가 필요하다.

공유기의 설치를 끝낸 후에는 네트워크에 연결하고 [192.168.1.1](192.168.1.1)에 접속하여 네트워크 설정을 진행하였다. RT-AC87U를 LG U+ IPTV와 함께 사용할 때 가장 중요한 설정사항은 처음에 관리자 아이디와 비밀번호, 네트워크 이름 등의 기본적인 설정을 할 때 공유기의 MAC 주소를 LG U+ 공유기의 MAC 주소로 지정을 하는 것이다. 그 다음에는 `고급 설정>LAN>IPTV`로 이동하여 `멀티캐스트 라우팅 사용 (IGMP Proxy)`와 `효과적인 멀티 캐스트 전달 활성화 (IGMP Snooping)`를 둘 다 `사용`으로 설정하면 된다.[^1] 설정 후 실험을 한 결과, 2.4GHz와 5GHz 무선 네트워크, 유선 네트워크, IPTV가 모두 아무런 이상없이 잘 동작한다.

[^1]: 설정이 적용되지 않을 경우에는 공유기의 펌웨어를 업데이트하면 된다.