# 5월 10일 과제

## 마크업

1. picture요소를 사용하여 svg를 지원하지 않는 웹브라우저에서는 png 형식으로 보여지도록 구현하였습니다

```html
<picture>
  <source srcset="./logo.svg" type="image/svg" />
  <img src="./logo.png" alt="네이버 png 로고" />
</picture>
```

2. 컴포넌트 방식으로 기존 코드를 가져왔습니다.

```html
<fieldset>
  <legend class="sr-only">회원 로그인 폼</legend>
  <!-- 아이디 입력 서식 -->
  <div class="form-input-group">
    <div role="group" class="form-input">
      <label for="userEmail" class="sr-only">아이디</label>
      <input
        type="email"
        id="userEmail"
        required
        placeholder="아이디(이메일)"
        name="userEmail"
      />
    </div>
    <!-- 비밀번호 입력 서식 -->
    <div role="group" class="form-input">
      <label for="userPwd" class="sr-only">비밀번호</label>
      <input
        type="password"
        id="userPwd"
        required
        placeholder="비밀번호"
        name="userPwd"
      />
    </div>
  </div>
</fieldset>
```

3. 버튼 밑 login-sign을 ul요소로 바꿔 리스트화 시키고 input과 a태그로 만들었습니다

```html
<ul class="login-sign">
  <li>
    <input type="checkbox" id="saveLogin" name="saveLogin" />
    <label for="saveLogin">로그인 상태유지</label>
  </li>
  <li>
    <a href="./ip_security.html" target="_blank" class="icon-link">IP 보안</a
    ><span tabindex="0" aria-label="IP 보안상태">ON</span>
  </li>
</ul>
```

## CSS

1. 기본 스타일 정의

```css
/* 기본 스타일 */
*,
*::after,
*::before {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

:root {
  --base-font-family: "SUIT Variable", sans-serif;
  --base-font-color: #181818;
}

body {
  font-family: var(--base-font-family);
  line-height: 1.15;
}

a {
  text-decoration: none;
  color: var(--base-font-color);
}
```

2. 모바일 퍼스트 환경을 만들기위해 media를 사용하였습니다

```css
@media (min-width: 768px) {
  .login {
    /* 로그인 폼 */
    .login-form {
      width: 500px;
      inline-size: 500px;
      margin: auto;
    }

    .login-sign {
      justify-content: space-between;

      .icon-link {
        display: block;
        float: left;
        margin-right: 5px;
      }
      span {
        display: inline;
      }
    }
  }
}
```
