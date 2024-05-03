# Homework

## 5월 3일 과제

### 마크업

1. 작은 단위의 마크업을 먼저 진행하였습니다
   이미지위에 접속중 표시를 겹쳐야하기 때문에
   image와 span을 figure로 감쌌습니다.

```html
<figure>
  <img
    class="image image1"
    src="../images/faces/face1.jpg"
    alt="여자 연예인 얼굴"
  />
  <span class="off"></span>
</figure>
```

2. figure의 정렬이 바뀌기 때문에 figure를 div로 감쌌습니다.

```html
<div class="image-container image-container1">코드 생략...</div>
```

3. span의 접속중 표시로 on/off를 컨트롤하기 위해 .off를 추가했습니다

```html
<span class="off"></span>
```

### CSS

#### float

1. 가장 작은 단위인 figure를 먼저 float으로 띄었습니다

```css
figure {
  float: left;
}
```

2. figure의 부모요소인 image-container에 `display: flow-root;`를 적용하여
   figure의 컨텐츠만큼 높이를 차지하게 하였습니다

```css
.image-container {
  display: flow-root;
}
```

#### position

3. image,span을 디자인하고
   span을 이미지 위에하기 위해 span의 position을 absolute로 설정하고
   이미지를 figure의 고정하기위해 figure의 position을 relative로 설정했습니다

```css
span {
  position: absolute;
}

figure {
  float: left;
  position: relative;
}
```

4. 접속중이지 않는 사용자의 배경색을 CSS와 class로 컨트롤 하였습니다

```css
span.off {
  background-color: #dbdbdb;
}
```

#### flex

5. display: flex가 적용되는 브라우저에서는 flex가 적용되게 하였습니다

```css
@supports (display: flex) {
  figure {
    float: left;
    clear: both;
  }
  main {
    display: flex;
    flex-direction: column-reverse;
  }

  .image-container {
    display: flex;
  }
}
```
