![image](https://github.com/rimgosu/simkoong/assets/120752098/ddf88b71-4315-4f10-9c22-24a13ce39bf5)

# simkoong


## 개요
유저 선호 이미지 기반으로 이성을 추천해주는 소개팅 플랫폼으로 추천 시스템을 이용하여 추천기능과 채팅기능을 구현하였습니다.

##### 기간: 2023.10.25 ~ 2023.12.03 (약 1달)

##### PPT 및 발표자료:

* ppt: <https://www.canva.com/design/DAF4-Q-cn4Q/k38TjeVmAsG-sRHA_-MK6g/edit>
* 시연 영상: <https://www.youtube.com/watch?v=Yo0dPi7MKPc>
* 아키텍처: <https://app.diagrams.net/#Hrimgosu%2FProjectResources%2Fmaster%2F%EC%84%9C%EB%B9%84%EC%8A%A4%EC%95%84%ED%82%A4%ED%85%8D%EC%B3%90.drawio>
* 카산드라 DB설계: <https://app.diagrams.net/#Hrimgosu%2FProjectResources%2Fmaster%2F%EC%B9%B4%EC%82%B0%EB%93%9C%EB%9D%BCDB%EC%84%A4%EA%B3%84.drawio>

## 시연
- 다음 프로젝트는 아래 링크를 통해 접속해 볼 수 있습니다.
- [Babe-베이브](http://15.164.48.247:8081/)
- 테스트 아이디
   - id : gaheun@gmail.com
   - pw : 1234


## 개선사항(느낀점)

## 문제

- Cassandra DB에 대한 지식이 부족하여 사용하기 어려움을 겪음
- VGG16과 KNN을 이용하여 추천 알고리즘 시스템을 구현하기에 시간과 데이터가 부족함
- 구글링을 통해 OAuth2.0을 이용한 소셜 로그인 기능을 구현하기 위해 구글과 카카오에서 OAuth2 앱을 생성하였으나 서술된 구현 과정이 spring boot버전도 다르고 Maven이 아닌 Gradle 프로젝트였으며 Spring Security와도 충돌이 일어났음
- 이미지 용량이 크고 회원 정보 데이터도 많아 페이지 로딩 시간이 길어지는 현상 발생

## 해결

- Cassandra 공식 문서와 논문을 받아 팀원들과 기초 지식을 쌓고 NoSQL에 대한 지식을 쌓음
그래서 간단한 회원정보는 MySQL로 사용하고 카산드라로는 이미지 유사도와 같은 대용량 데이터를 keyspaces를 이용하여 담았다.
- VGG16과 KNN을 이용한 추천 알고리즘 시스템은 멘토님의 도움으로 인물 사진들을 모아
선택한 이미지와 유사한 이미지를 분류하도록 학습 시키는 과정을 거침
- Spring 공식문서에서 OAuth2를 찾아보았다. Gradle, Maven과 Java, Kotlin 코드까지 전부 볼 수 있었고 JWT 토큰과 Spring Security 사용자 설정을 건드려 줘야 한다는 내용이 있었다.
보안 토큰은 CSRF만 다루어 봐서 JWT에 대한 관련 문서도 찾아 보았다. 아무래도 보안 관련이라
권한 설정과 리소스 접근을 위한 엑세스 토큰등 구성해줘야 할 부분들이 많았다.
- AWS S3를 이용하여 이미지등 대용량 데이터 저장
- 비용 최적화를 자동으로 처리해줌
- 지연 시간을 줄이고 데이터가 늘어나도 S3의 확장성덕에 자동으로 확장
- IAM과 버킷을 사용하여 접근 권한 설정으로 보안수준도 높음

## 깨달은 점

- **Github branch** 활용의 중요성
- 공식문서 위주로 찾아보기
- JPA로 Mapping 하는 법
- NoSQL의 장점 (대규모 데이터를 다루는데 용이함)
- 스프링 WebSocket으로 실시간 채팅기능을 구현 하는 법
- AWS EC2를 사용하여 배포 하는 법



 



