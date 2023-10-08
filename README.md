# 🎨DrawingGuessMachine

KNN 알고리즘을 통해 그린 물체와 가장 유사한 class가 무엇인지 판별하는 AI를 다뤄보자

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
