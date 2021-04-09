
## 🚀 stack
[repository🌱](https://github.com/yooooonk/hh99_clone)
- front-end : react, redux, thunk, styled-component
- back-end : spring-boot, jpa, mysql
- 개발기간 : 7일(4월 2일 ~ )
- 개발인원 : front 2명, back 2명
- 일정관리 : notion 이용
![](https://images.velog.io/images/ouo_yoonk/post/15e05ff4-9881-4371-bfab-d2cfea71b427/image.png)


## 📜상세기능
### 메인페이지
![](https://images.velog.io/images/ouo_yoonk/post/38ab1bae-edb1-4d47-b0e6-3e86f0be83bc/v_main.gif)
- 전체 목록조회
- 트렌딩, 최신 포스트 조회

### 상세페이지
![](https://images.velog.io/images/ouo_yoonk/post/20be1575-a695-44f7-b58a-d29aa0af6853/detail2.gif)

- scroll에 따라 고정되는 사이드바 구현
- 수정삭제 권한 체크



### 로그인, 회원가입
![](https://images.velog.io/images/ouo_yoonk/post/fb39d42f-af0e-4a76-be36-fb877e597eb2/v_login.gif)

- 로그인 여부에 따라 헤더 변경
- jwt 이용
- 로그인 성공하면 jwt 발급 - header에 토큰 셋팅 + jwt로 유저정보 가져오기 + store에 유저정보 저장
``` javascript
const loginAPI = (id, pw) => {
  return function (dispatch, getState, { history }) {
    const API = 'http://localhost:8080/api/authenticate';

    axios({
      url: 'http://localhost:8080/api/authenticate',
      method: 'post',
      data: { username: id, password: pw },
      withCredentials: true
    })
      .then((res) => {
        console.log('로그인', res.data.token);
        axios.defaults.headers.common[
          'Authorization'
        ] = `Bearer ${res.data.token}`;

        dispatch(getUserInfo());
      })
      .catch((err) => {
        console.error(err);
        alert('로그인에 실패했습니다');
      });
  };
};

const getUserInfo = () => {
  return function (dispatch, getState, { history }) {
    axios.get('/api/user').then((res) => {
      console.log('getUserInfo', res);
      dispatch(
        setUser({ username: res.data.username, nickname: res.data.nickname })
      );
      history.replace('/');
    });
  };
};
```

### 글쓰기, 수정, 삭제
- toast editor 사용
![](https://images.velog.io/images/ouo_yoonk/post/ea49d5f6-fcb6-4f2b-9fc2-5b62d4b69656/v_write.gif)

![](https://images.velog.io/images/ouo_yoonk/post/b407834d-b8b8-457c-91e7-77e72996a90f/v_ud.gif)
- 내가 쓴 글만 수정, 삭제 가능

### 댓글 달기, 수정, 삭제
![](https://images.velog.io/images/ouo_yoonk/post/c866e4ca-f4da-4d3c-93a9-87cd3a8366df/v_comment.gif)

### 반응형
![](https://images.velog.io/images/ouo_yoonk/post/9df2b531-1e94-488a-8a29-5ae4842223ad/response.gif)


## 🌈회고
항해 다 섯번쨰 프로젝트로 클론코딩을 했다. 우리 조는 벨로그를 선택했고, 메인페이지, 상세페이지, 로그인, 글쓰기까지 구현했다. feat. toast editor

### 첫 팀 프로젝트
지금까지 만든 모든 프로젝트는 혼자 프론트와 서버를 다 개발했는데 ~~k풀스택~~ 이번에 처음으로 서버 개발자 분들과 협업을 했다. 팀원분들이 실력과 열정과 배려를 모두 갖춘 분들이라 소통에 어려움은 없었다. 초반에 백엔드와 속도차이가 나서 미안한 마음만 가득했다. 초반에는 노션으로 진행 상황을 정리했고, 주로 gather나 slack으로 그때그때 회의를 하면서 프로젝트를 진행했다. 팀원분들의 열정과 배려심에 감화되어서 나도 기술적으로도 인간적으로도 더 많이 배우고, 즐겁게 작업할 수 있었다.

### git
가장 고생한건 역시 git이었다. _충돌이야말로 git의 정수_라고 했는데 어느 순간부터 main에 merge하면 자꾸 내 작업물이 날아가서 멘붕이 왔다. git스럽게 해결하고 싶었는데 결국 사라진 파일을 수동으로 복붙하는 수 밖에 없었다. ㅠㅠ. 내가 한 커밋이 main에 포함되어있고, 그 이후에 내 작업물이 덮어써진 채로 새로운 커밋이 생기면 그럴 수 있다고 한다. 깃의 단점이라고 하는데 더 파봐야할것 같다. 

### 새로 배운것 / 시도해본 것
`styled-component`를 익숙해지는 시간이었다. css 변수도 사용할 수 있고, props도 공통으로 사용할 수 있어서 flex속성이나, 반응형 사이즈 같은 것을 저장해서 편하게 갖다썼다. 그리고 `box-sizing` 속성을 처음으로 사용했다. padding을 주면 그 사이즈만큼 전체 크기가 커져서 안맞는 경우가 있었는데, box-sizing:border-size 속성으로 해결했다.
``` javascript

const size = {
  mobile: '767px',
  tablet: '1024px',
  desktop: '1025px'
};

const theme = {
  velog_green: '#12b886',
  velog_green_h: 'rgb(18,184,134,0.7)',
  mobile: `(max-width: ${size.mobile})`,
  tablet: `(max-width: ${size.tablet})`,
  desktop: `(min-width: ${size.desktop})`,
  flex_column:
    'display: flex; flex-direction:column; align-items: center; justify-content: space-between; ',
  flex_row:
    'display: flex; align-items: center; justify-content: space-between;',
  default_width:
    'width:100vw; max-width:768px; box-sizing:border-box; padding:0 1rem',
  max_width: `max-width:768px`,
  border_box: `box-sizing:border-box`,

  responsiveContainer: `
  @media (max-width: 1919px) {
    width: 1376px;
  }
  @media (max-width: 1440px) {
    width: 1280px;
  }
  @media (max-width: 1312px) {
    width: 912px;
  }
  @media (max-width: 944px) {
    width: calc(100% - 2rem);
  }
  @media (max-width: 767px) {
    width: calc(100% - 2rem);
  }
  width: 1728px;
  margin-left: auto;
  margin-right: auto;
  `,
};
```

스크롤에 따라 위치가 고정되는 사이즈바를 상세페이지에 만들었다. useRef를 사용해 scroll높이에 따라 style에 top 속성을 줘 고정을 했다. addEventListener를 사용했을 때는 꼭 removeEventListener를 해줄것! 이번에는 스크롤이벤트를 발생하는대로 다 받았는데, 메모리에 부담이 가는 것 같아서 다른 프로젝트에 setTimeout이나 throttle을 이용해 구현할 예정이다.


### 아쉬운 것
클론코딩이다보니 아무래도 css에 시간을 많이 썼다. 리액트 기능이나 성능에 대한 공부나 시도를 못 해봤다. 

그리고 시간이 부족해 좋아요 기능과  이전페이지, 다음페이지를 결국 구현 못했다. 프론트쪽에서는 버튼 한번의 단순한 이벤트인데, 서버쪽에서 db 설계를 다시 하거나 쿼리를 만드는게 어려운 것 같았다. 

개인적으로는 목차 기능을 구현 못한게 아쉽다. toast editor를 사용하면 md형식과 html 형식 모두를 얻을 수 있기때문에 그 데이터를 이용해 목차를 만들고, a tag로 이동을 하면되겠다고 생각을 했는데, 생각만 했다....초반에 detail 페이지에 작업에 시간을 많이 썼고, 마지막에 로그인 관련해서 처리를 하느라 후순위였던 목차를 결국 구현하지 못했다. 


