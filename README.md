
## Velog 클론코딩
항해99 Chapter 4 클론코딩
- 개발 기간 : 2021.04.02 - 2021.04.09
- 팀 프로젝트 : front 2명, back 2명
- Front-end : React, Redux, Thunk, Styled-component
- Back-end : Spring-boot, jpa, mysql
- 일정관리 : Notion 이용

### 구성
#### [메인페이지]
- 전체 목록조회
- 트렌딩, 최신 포스트 조회
![](https://images.velog.io/images/ouo_yoonk/post/38ab1bae-edb1-4d47-b0e6-3e86f0be83bc/v_main.gif)

#### [상세 페이지]
- 스크롤 시 고정되는 사이드바 
- 수정, 삭제 권한 체크
![](https://images.velog.io/images/ouo_yoonk/post/20be1575-a695-44f7-b58a-d29aa0af6853/detail2.gif)

#### [로그인 / 회원가입]
- 로그인 여부에 따라 헤더 변경
- jwt 이용
![](https://images.velog.io/images/ouo_yoonk/post/fb39d42f-af0e-4a76-be36-fb877e597eb2/v_login.gif)

#### [글쓰기 페이지]
- toast editor 사용
- 수정, 삭제
![](https://images.velog.io/images/ouo_yoonk/post/ea49d5f6-fcb6-4f2b-9fc2-5b62d4b69656/v_write.gif)

![](https://images.velog.io/images/ouo_yoonk/post/b407834d-b8b8-457c-91e7-77e72996a90f/v_ud.gif)
- 내가 쓴 글만 수정, 삭제 가능

#### [댓글 달기, 수정, 삭제]
![](https://images.velog.io/images/ouo_yoonk/post/c866e4ca-f4da-4d3c-93a9-87cd3a8366df/v_comment.gif)

#### [반응형]
![](https://images.velog.io/images/ouo_yoonk/post/9df2b531-1e94-488a-8a29-5ae4842223ad/response.gif)


#### 회고
항해99 Chapter4 클론코딩 프로젝트로 저희 조는 개발자 블로그인 'velog'를 선택했고, 로그인/회원가입, 메인페이지, 상세페이지, 글쓰기 페이지를 구현했습니다.
프론트개발자로써 백엔드 개발자와 공식적으로 협업한 첫 프로젝트로 API를 설계하는법, axios, fetch를 이용해 해당 API를 호출하는 법 등 백엔드와 협업하는 법을 많이 배웠습니다. 
노션으로 진행 상황을 정리했고, 주로 gather나 slack으로 그때그때 회의를 하면서 프로젝트를 진행했습니다. 
마지막으로, 팀원분들의 열정과 배려심 덕분에 개발에 대한 이해를 한단계 높일 수 있었고, 저 또한 사람들과 지식을 나누고 공유할 줄 아는 좋은 개발자가 되어야겠다고 다짐한 프로젝트 였습니다.

#### 새롭게 시도해 본 부분
- axios, fetch 통신하기
- jwt 토큰을 이용한 로그인 구현
- 상세페이지의 작성자에 따라 헤더 변경하기
- Card List로 나열하기
- CSS: transition, animation 효과

#### 아쉬운 부분
로그인/회원가입, 메인페이지를 구현하며 jwt 토큰에 대해 알 수 있어서 좋았지만 CRUD 연습은 많이 하지 못한 것 같아 아쉬웠습니다. 다음 프로젝트에서는 CRUD 파트를 메인으로 담당해 공부해보고 싶습니다.


