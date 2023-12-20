## 프론트엔드로 구현된 사이트
### https://gukjinso.github.io

영화 및 배우 정보와 트레일러를 제공하는 영화 사이트입니다. <br>
주요 기능은 영화 검색이며 관리자의 경우 권한 검사를 통해 Create Update Delete가 가능합니다. <br>
보여주는 데이터는 TMDB API의 영화 1000건을 크롤링했습니다. <br>

학업을 병행하는 1인 작업이다 보니 API 명세서와 다르게 뷰 단에서는 구현하지 못한 미흡한 부분이 있습니다. <br>
계속 업데이트 하겠습니다. 감사합니다. <br>


## 백엔드 API 명세 (스웨거)
### https://api.guckflix.site/swagger-ui.html


## 백엔드 깃허브
### https://github.com/GukJinSo/guckflix-backend

스프링 부트 2.7.6 + 간단한 쿼리에 JPA, 복잡한 쿼리는 querydsl를 사용합니다. <br>
운영 DB와 로컬 DB는 각각 mysql, h2입니다.
크롤링 초기 데이터는 JdbcTemplate를 통해 배치 방식으로 저장했습니다. <br>
스프링 시큐리티에 Session 쿠키 방식으로 인증 인가를 관리합니다. <br>
구글 Oauth2 로그인이 가능합니다. <br>
AWS RDS Mysql과 EC2에 배포하여 사용했습니다. <br>
AWS에서 제공하는 로드밸런서를 통해 http로 요청하더라도 https로 리다이렉트 되도록 설정했습니다. <br>
SSL은 AWS에서 간편하게 제공하는 무료 인증서를 사용했습니다. <br>

#### 프로젝트 기능 및 개발 방식

##### 기능

영화 CRUD : /controller/MovieController <br>
출연 정보 CRUD /controller/MovieController <br>
배우 CRUD : /controller/ActorController <br>

스프링 시큐리티, CORS 관련 : /security/SecurityConfig <br>
일반 로그인 / oauth2 : /security/authen/PrincipalDetailsService, PrincipalOauth2UserService <br>
ExceptionHandler : /exception/ApiExceptionHandler <br>
ETag 이미지 캐시 : /controller/ImageController <br>
페이징 용도 클래스 : /dto/paging/PagingT, SliceT <br>
커스텀 ArgumentResolver : /config/PagingRequestArgumentResolver <br>
커스텀 날짜 검증기 : /annotation/DateRange <br>
파일 업로드 : /file/FileUploader <br>

##### 개발 방식
NestedDto : /dto/* <br>
빌더 패턴 : /entity/* <br>
상수관리 : /file/FileConst <br>
환경별 설정 : /resources/application.yml, application-prod.yml <br>
UnModifiable Collection : /config/GenreCached <br>
추상 클래스 : /entity/base/TimeDateBaseEntity <br>

## 프론트엔드 깃허브
### https://github.com/GukJinSo/guckflix-frontend

CRA로 만들어진 리액트 어플리케이션과 Redux 구성입니다. <br>
이미지를 담은 카드 형태인 VideoSlider 컴포넌트를 여러 페이지에서 재사용해보았습니다. <br>
인증 인가에 따라 권한에 따른 라우팅을 지원합니다. <br>
소스맵을 읽지 못하도록 난독화했습니다. <br>

## 학습 과정
### https://pond-teeth-62a.notion.site/a4dc5d6b60a94e1fa797e83ea823b947?v=42b5b9a6501d42f88dc978a1f8edc377

