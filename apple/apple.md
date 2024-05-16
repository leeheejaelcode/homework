# 5월 16일 과제

![GIFMaker_me](https://github.com/leeheejaelcode/homework/assets/138003632/6a2df940-1ebc-4f82-890b-32649e6fdbb8)


## 마크업

1.  h2를 제목, .explanation을 부제목, .release-date를 출시일로
    클래스명을 지정하였으며
    밝은배경과 어두운배경의 디자인을 달리하기위해
    dark-box, white-box로 클래스를 나누었습니다

```html
<div class="box dark-box">
  <article class="card ipad-pro">
    <h2>iPad Pro</h2>
    <p class="explanation" aria-label="ipad-pro 제품 설명">
      놀라우리만치 얇다.<br class="lg-none" />
      엄청나게 강력하다.
    </p>
    <p class="release-date" aria-label="출시일 추후 공개">출시일 추후 공개</p>
    <ul>
      <li><a href="/" class="link more">더 알아보기</a></li>
      <li><a href="/" class="link price">가격 보기</a></li>
    </ul>
  </article>
</div>
```

2. grid 컴포넌트를 사용해야하는 부분에는 div grid-container로 감싼후 grid를 사용하고
   cols 클래스를 이용하여
   반응형 레이아웃 처리를 하였습니다

```html
<!-- grid container 시작 -->
<div class="grid-container">
  <div class="box dark-box cols-12 lg-cols-6">
    <article class="card airpods-pro">
      <h2>airPods Pro</h2>
      <p class="explanation" aria-label="airPods Pro 제품 설명">
        전에 없던 청취 경험.<br class="lg-none" />
        적응형 오디오.
      </p>
      <ul>
        <li><a href="/" class="link more">더 알아보기</a></li>
        <li><a href="/" class="link price">가격 보기</a></li>
      </ul>
    </article>
  </div>
</div>
<!-- grid container 끝 -->
```

3. 데스크탑 화면에서 보여지지않는 br 태그는 class를 주어 화면에 보여지지 않게 하였습니다

## css

1. 컴포넌트와 스타일을 구분 짓기위해 레이아웃 위주의 코드를
   card-component.css에 담고 변수를 사용하였습니다

```css
.card {
  --card-height: var(--size);
  --sm-padding-top: var(--large-spacing);
  --lg-padding-top: var(--extra-large-spacing);

  /* 레이아웃 */
  display: flex;
  flex-flow: column nowrap;
  align-items: center;

  height: var(--card-height);
  padding-top: var(--large-spacing);
  row-gap: var(--small-spacing);
  /* 카드의 배경 이미지 */
  /* 현재 카드들의 공통적인 백그라운드 속성을 컴포넌트 안에 넣었습니다 */
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;

  ul {
    display: flex;
    flex-flow: row wrap;
    gap: var(--base-spacing);

    .link {
      padding: var(--x-small-spacing);
    }
  }
}

.grid-container {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
}

.cols-12 {
  grid-column: span 12;
}

@media (min-width: 1024px) {
  .card {
    /* padding-top: var(--extra-large-spacing); */
    /* 선생님이 주신 theme.css에서는 데스크탑 환경에서 주는게
    맞다고 생각이 드는데 적용을 하게 되면 가격보기와 배경이 겹쳐서 잘 보이지 않는 현상이 있습니다 그래서 일단 주석처리를 해놨습니다. */
  }
  .grid-container {
    column-gap: 1rem;
  }

  .lg-cols-6 {
    grid-column: span 6;
  }

  .lg-none {
    display: none;
  }
}
```

2. apple.css를 통하여 디자인 구조를 만들고 .box의 공통적인 디자인을 만들었습니다.

```css
/* box 공통 속성 */
.box {
  margin-top: 1rem;
  h2 {
    font-size: var(--sm-main-title);
    font-weight: 700;
  }

  .explanation {
    font-size: var(--sm-sub-title);
    font-weight: 600;
    text-align: center;
    margin-bottom: var(--x-small-spacing);
  }

  .release-date {
    font-size: var(--release-date-text);
    color: var(--gray-text);
  }

  ul {
    .link {
      display: inline-block;
      border-radius: 2rem;
      font-size: var(--sm-button-text);
      transition: ease all 0.5s;
    }

    .more {
      color: var(--white-text);
    }
  }
}
```

3. 밝은배경과 어두운 배경을 각각 다르게 디자인하였습니다

```css
/* 어두운 테마 */
.dark-box {
  h2,
  .explanation {
    color: var(--white-text);
  }

  ul {
    .link {
      background-color: transparent;
      border: 1px solid var(--blue-100);

      &:hover {
        box-shadow: 0px 0px 15px 1px var(--white-text);
      }
    }

    .more {
      background-color: var(--blue-100);
    }

    .price {
      color: var(--blue-100);
    }
  }
}
/* 밝은 테마 */
.white-box {
  h2,
  .explanation {
    color: var(--black-text);
  }

  ul {
    .link {
      border: 1px solid var(--black-text);
      background-color: transparent;

      &:hover {
        box-shadow: 0px 0px 15px 1px rgba(0, 0, 0, 70%);
      }
    }

    .more {
      background-color: var(--black-text);
    }

    .price {
      color: var(--black-text);
    }
  }
}
```

4. cols 클래스를 사용하여 반응형으로 만들기 위해
   grid.css를 활용하였습니다

```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
}

.cols-12 {
  grid-column: span 12;
}

@media (min-width: 1024px) {
  .grid-container {
    column-gap: 1rem;
  }

  .lg-cols-6 {
    grid-column: span 6;
  }

  .lg-none {
    display: none;
  }
}
```

5. lg-none클래스를 사용하여 데스크탑 사이즈에서는 br태그를 숨기고 줄 바꿈이 일어나지 않게 하였습니다.

```css
@media (min-width: 1024px) {
  .lg-none {
    display: none;
  }
}
```

6. 각각의 card의 클래스를 주고 배경을 바꾸었고 image-set을 통하여 고해상도 이미지를 렌더링할 수 있게 하였습니다.

```css
.ipad-pro {
  background-image: image-set(
    url(../products/ipad_pro.jpeg),
    url(../products/ipad_pro_2x.jpeg)
  );
}

.ipad-air {
  background-image: image-set(
    url(../products/ipad_air.jpeg),
    url(../products/ipad_air_2x.jpeg)
  );
}

.iphone-15pro {
  background-image: image-set(
    url(../products/iphone15_pro.jpeg),
    url(../products/iphone15_pro_2x.jpeg)
  );
}

.iphone-15 {
  background-image: image-set(
    url(../products/iphone15.jpeg),
    url(../products/iphone15.jpeg)
  );
}

.watch {
  background-image: image-set(
    url(../products/apple_watch.jpeg),
    url(../products/apple_watch_2x.jpeg)
  );
}

.macbook-air {
  background-image: image-set(
    url(../products/macbook_air.jpeg),
    url(../products/macbook_air_2x.jpeg)
  );
}

.airpods-pro {
  background-image: image-set(
    url(../products/airpods_pro.jpeg),
    url(../products/airpods_pro_2x.jpeg)
  );
}
```

---

## 어려웠던 점

아직까진 레이아웃과 디자인을 어떻게 나눠야하는지 잘 모르겠습니다.
레이아웃 관련된 css속성은 레이아웃으로
디자인 관련된 css속성은 디자인으로 나눠야 하는건지
정확한 기준이 없는것 같아서 어려웠습니다 ㅠㅠ..

변수에 대한 장점을 알고있지만
어느 부분에서 변수를 적극적으로 활용을 해야하는 것인지
아직까진 감이 잘 오지않습니다.

그렇지만 grid와 card를 컴포넌트화 해서 만든 덕분에
어렵지 않게 마크업과 레이아웃 작업을 해나아갔습니다.

중간에 link:hover 효과도 줘서 심심하지 않은 애니메이션을 만들어봤습니다..
(가격보기 주변에 그림자 효과)
![image](https://github.com/leeheejaelcode/homework/assets/138003632/28c3a21f-2f82-40df-9dfc-7eec6f0f1250)

부트스트랩과 테일윈드와 비슷한 방향으로 cols 클래스를 사용하다보니
다음에 배울 부트스트랩과 테일윈드에서도 어렵지않게 사용할 수 있을것 같습니다.

## 결과
**데스크탑 버전**
![데스크탑 버전](https://github.com/leeheejaelcode/homework/assets/138003632/98b1f78d-167e-421f-b4bb-5460eba44603)
**모바일 버전**
![모바일 버전](https://github.com/leeheejaelcode/homework/assets/138003632/50905348-4a8c-4ea2-a85d-7e9ae306dfbb)

