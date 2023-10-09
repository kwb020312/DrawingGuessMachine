# 🎨DrawingGuessMachine

KNN 알고리즘을 통해 그린 물체와 가장 유사한 class가 무엇인지 판별하는 AI를 다뤄보자
가장 알아보고 싶었던 것은, 어째서 AI 개발이 Python으로 이루어지는가? 에 대한 궁금증

---

### 😁데이터 출처

[freeCodeCamp gniziemazity Radu Mariescu-Istodor](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbmY3X1Riakg0ZHFDcnoxbjlJWXpNcWhzQkhfZ3xBQ3Jtc0trZFFkOWlOWlF5Q1U1S2R1UkRXSkR6OE9xZWhSX1pPMFN6UlpDWWNNRFdKWTVFazlKTVpibkFXSXU2blMyUGJYM1JUX1gtLUphaWhTR0p0S3d3WlBGd242czlCcEp2c09pdWZ3NHJhWGc2WHdiaUlWYw&q=https%3A%2F%2Fgithub.com%2Fgniziemazity%2Fdrawing-data&v=3wwiOSxDAmg)

---

### 😀실행방법

```
// root
cd node && npm install
```

---

### 😂Minimum Rectangle Algorithm

즉 그릴 수 있는 가장 작은 box를 Object 윤곽에 두르는 알고리즘이다.

주요 개념은 방향이 dir이고 A점을 통과하는 직선과 방향이 dir에 수직이고 B점을 통과하는 직선의 교점을 반환한다는 것

모양이 비슷한 그림의 경우 구분이 필요해서 도입되었음

![mragif](https://blog.kakaocdn.net/dn/zmuGo/btq0do1k1T3/kEJd8P5vLknmTeVc2hHV70/img.gif)

---

### 🤣Measure Roundeness

```javascript
function circularity(x) {
  (4 * Math.PI * area(x)) / Math.sqrt(perimeter(x));
}
```

그림이 어느 정도의 진원도를 갖고있는지 파악하기 위한 알고리즘. 즉 판단하기 어려운 물체는 둥근 정도에 따라 물체를 구분한다는 것이다.

해당 프로젝트에서는 진원도에 따른 물체 구분을 위해

```javascript
const R = 255 - Math.floor(roundness ** 5 * 255);
const G = 255 - 0;
const B = 255 - Math.floor((1 - roundness ** 5) * 255);
const color = `rgb(${R},${G},${B})`;
```

다음 로직으로 색상을 구분하였음

---

### 😃Why?

파이썬을 AI 개발 언어로 사용하는 이유를 해당 레파지토리를 통한 공부 중 알게되었음.
복잡한 수식이 필요한 과학 계산이 필요하며 Python에 유명 라이브러리의 기능들이 직접 구현하기 어려움
만약 해당 기능들을 라이브러리로 구현한다 하더라도, 머신러닝이나 딥러닝을 하기 위해 AI 프레임워크를 사용해야하는데, GPU에서 지원하는 프레임워크는 Python이 기본 베이스인 경우가 대부분임
