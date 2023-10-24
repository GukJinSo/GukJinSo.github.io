# https://gukjinso.github.io

영화 및 배우 정보와 트레일러를 제공하는 영화 사이트입니다.
주요 기능은 영화 검색이며 관리자의 경우 권한 검사를 통해 Create Update Delete가 가능합니다.
사이트에서 보여주는 데이터는 TMDB API를 크롤링해서 만들었습니다.

API 명세서와 다르게 프론트에서 실제로 구현하지 못한 미흡한 부분은 따로 기재하겠습니다. 감사합니다.

# https://github.com/GukJinSo/guckflix-backend

백엔드

스프링 부트 2.7.6 버전 + JPA를 사용중입니다.
스프링 시큐리티를 사용하여 인증 인가를 진행하며, Session 쿠키 방식을 사용하고 있습니다. 구글 Oauth2 로그인이 가능합니다.
AWS RDS Mysql과 EC2에 배포하여 사용하고, 로드밸런서를 통해 http로 요청하더라도 https로 리다이렉트 되도록 설정했습니다.
SSL은 AWS에서 간편하게 제공하는 무료 인증서를 사용했습니다.

# https://github.com/GukJinSo/guckflix-frontend

프론트엔드

리액트 기반에 Redux를 사용하여 prop을 관리하고 있습니다.
배포는 github.io를 통해 하고 있습니다.

