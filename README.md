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
index.js 의 마지막 줄 ```export default rounter ```는 다른 파일의 내용을 참조해오기 위한 설정으로 일단 알아두시면 될듯합니다. 

그리고 기억해야할 한가지는 index.js에 있던 ``` export default rounter ``` 가 main.js 파일의에서 사용된다는 것입니다. 

<img width="628" alt="스크린샷 2023-03-05 오후 6 00 53" src="https://user-images.githubusercontent.com/48478079/222951469-6f899a3d-6a99-4b0e-9dbd-e5322b7a8bd1.png">

여기에서 main.js에 있는 내용 중 
``` import router from './router ``` 는 ``` import router from './router/index.js' ``` 와 같습니다. html에서 폴더이름을 언급하면 자동적으로 해당폴더의 index파일을 읽어보는 원리와 같이 작동하여 따로 index.js을 언급하지 않는것입니다.  
그리고, 
``` import router from './router ```에서 불러온 후 ``` createApp(App).use(router).mount('#app') ```에 등록해서 사용하는 것입니다. 

또한 App.vue 파일을 열어보면 template 태그안에 ``` <router-view/> ``` 가 있는데 이것은 vue router를 위한 특별한 태그라고 보시면 되며, url에 따른 컴포넌트가 화면에 그려지는 영역이기도 합니다. 

index.js파일에서 만약 페이지가 '/' 를 방문하게 되면 ``` component:Home ``` 컴포넌트 전체가 App.vue에 있는 ```  <router-view/>  ``` 에 삽입된다고 생각하시면 됩니다  이미지로 표현해보면 아래와 같습니다.  

<img width="621" alt="스크린샷 2023-03-05 오후 6 21 48" src="https://user-images.githubusercontent.com/48478079/222952456-cb42dcf0-05b2-4989-b3f9-0b35488ba3e8.png">   

또한 ```<router-link to="경로"> ```로 되어 있는 부분은  컴파일 시, ``` <a> ``` 태그로 변환됩니다.   
1) to 속성 값에는 '경로'를 지정하고,    
2) v-bind와 함께 사용하여 동적으로 경로를 만들 수 있습니다.  
   예) :to="{name :'About' }"  
   <- index.js에서 ``` { path:'/about', name:about, component: About } ```  
3) to="test/path" 처럼 붙이면 현재 url에 이 path가 지정되고,   
4) to="/test/detail" 처럼 붙이면 default url에 해당 경로가 추가됩니다.  


이제까지 라우터에 대한 기본적인 내용을 살펴보았습니다.   
다음 수업을 위해    
1) components 폴더에서 ' HelloWorld.vue '를 삭제합니다.   
2) HomeView.vue 파일에서  
``` javascript
<template>
  <div class="home">
   <h1>This is Home page</h1>
   <p> Router를 활용한 예</p>
  </div>
</template>
<script>
export default {
  name: 'HomeView',
  components: {
  }
}
</script>
``` 
로 변경합니다 

<img width="284" alt="스크린샷 2023-03-05 오후 9 11 56" src="https://user-images.githubusercontent.com/48478079/222959748-df25c78f-2160-4ed0-b021-bbece14235e7.png"><img width="284" alt="스크린샷 2023-03-05 오후 9 12 03" src="https://user-images.githubusercontent.com/48478079/222959763-79b052d1-8c54-4212-8eef-0392f67117f2.png">


다음 수업에서는 메뉴를 변경한 컴포넌트를 만들어보겠습니다. 

