##### :cactus: Vue3 -part2

이전 내용을 이어갑니다.  
index.js파일 아래쪽에 있던 
``` javascript 
const router = createRouter({
  history: createWebHistory(process.env.BASE_URL),
  routes
})
```
는 실제 라우터 인스턴스를 셋팅하는 곳입니다. 실제 앱을 위한 라우터를 생성합니다.  


<img width="401" alt="스크린샷 2023-03-05 오후 5 40 49" src="https://user-images.githubusercontent.com/48478079/222950632-a66e4ba0-799b-4353-b92e-f4ede8b077e8.png">

이미지에서 아래쪽에 있는 ' createRouter() '는 위에 있는 from 'vue-router ' 패키지로부터 import 됩니다
여기 createRouter()안에 있는 history 항목은 url의 히스토리를 기억해서 우리가 브라우저에서 이전페이지, 다음페이지로 이동하도록 도와줍니다 또한 웹 해시를 기억하고 있습니다. 그리고 ' process.env.BASE_URL ' 는 우리 프로젝트의 기본 url를 전달해줍니다
그리고 createRouter()안의 마지막 항목인 'routes' 는 라우터자신을 말합니다. 
