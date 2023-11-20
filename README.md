## 프론트엔드로 구현된 사이트
### https://gukjinso.github.io

영화 및 배우 정보와 트레일러를 제공하는 영화 사이트입니다. <br>
주요 기능은 영화 검색이며 관리자의 경우 권한 검사를 통해 Create Update Delete가 가능합니다. <br>
사이트에서 보여주는 데이터는 TMDB API의 인기 영화 1000건을 크롤링해서 만들었습니다. <br>

학업을 병행하는 1인 작업이다 보니 API 명세서와 다르게 뷰 단에서는 구현하지 못한 미흡한 부분이 많습니다. 계속 업데이트 하겠습니다. <br>
감사합니다. <br>


## 백엔드 API 명세 (스웨거)
### https://api.guckflix.site/swagger-ui.html


## 백엔드 깃허브
### https://github.com/GukJinSo/guckflix-backend

스프링 부트 2.7.6 버전 + JPA와 querydsl을 사용중입니다. <br>
스프링 시큐리티를 사용하여 인증 인가를 진행하며, Session 쿠키 방식을 사용하고 있습니다. 구글 Oauth2 로그인이 가능합니다. <br>
AWS RDS Mysql과 EC2에 배포하여 사용하고, 로드밸런서를 통해 http로 요청하더라도 https로 리다이렉트 되도록 설정했습니다. <br>
SSL은 AWS에서 간편하게 제공하는 무료 인증서를 사용했습니다. <br>

중점적으로 보시면 좋을 클래스는 다음과 같습니다. <br>

ImageController : 이미지 재차 요청 시 캐시 사용하도록 유도 <br>
DateRangeValidator, @DateRange : 날짜 유효 검사용 커스텀 밸리데이터와 어노테이션 <br>
GenreCached : 지속적으로 쿼리되면서 변경 가능성이 없는 테이블(장르)을 미리 쿼리하여 Bean에 올려두고 사용합니다. <br>
PagingRequestArgumentResolver : 페이징 처리를 위한 ArguemntResolver <br>
Paging, Slice : 각각 페이징 객체, 무한스크롤용 응답 객체 <br>
ApiExceptionHandler : 익셉션 관리 객체. 스프링 에러 전파에 따라 의도하지 않는 응답을 막기 위함 <br>
DTO 패키지 : 관리 편의상 기능별 한 개의 dto를 만들고 하위 스태틱 이너 클래스를 작성하여 api 명세와 valid 어노테이션 기재 <br>
SecurityConfig.corsFilter() : CORS 필터. addAllowedOrigin()에 환경변수를 사용하고 201 응답을 위한 location 헤더만 addExposedHeader() 적용했습니다. <br>


## 프론트엔드 깃허브
### https://github.com/GukJinSo/guckflix-frontend

리액트 기반에 Redux를 사용하여 prop을 관리하고 있습니다. <br>


## 학습 과정
### https://pond-teeth-62a.notion.site/a4dc5d6b60a94e1fa797e83ea823b947?v=42b5b9a6501d42f88dc978a1f8edc377

