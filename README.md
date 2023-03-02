##### :cactus: Vue3 -part2


프로젝트가 생성되면 ``` <div id="app"> ```안에 모든 내용이 들어가게된다. 모달창, 로그인창, 팝업창 등등. 그러면 이런 것들은 기존에 있던것들 위 즉 최상위로 올라와야 하는데 구조가 복잡해지면 모달을 띄우기가 쉽지 않을 것이다. 그래서 이런것을 해결해주는 것이 teleport이다. 이것은 React에서 다루는 portal과 동일한 기능이다.  

## teleport란
텔레포트는 index.html 안에 ```<div id="app">```과 같은 레벨의 별개의 div를 만드는 것이다.

[index.html] 
```html
<div id="app"></div>
<div class="modal"></div>

```
