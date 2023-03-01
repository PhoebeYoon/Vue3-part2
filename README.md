##### :cactus: Vue3 -part2

#### 이전에 했던 내용을 확인하고 진행합시다.
1. \src폴더에는 어떤 파일이 있었나요?
2. App.vue파일에 있던 3가지 주요한 태그를 기억하시나요?
3. mount()가 있던 파일의 이름은 뭐죠?

질문에 답하기 어렵다면 이전 내용을 다시 보고 오시길...

이전 'vue_cli_설치'에 package.json 파일의 내용을 열어보면 ```  "serve": "vue-cli-service serve" ``` 가 있는데 이것은  브라우저가 우리가 만든 vue 어플리케이션을 미리 볼수있도록 로컬개발서버를 지원한다는 내용입니다.
그래서 이제 다음과 같이 실습해 보겠습니다.   
1. vs code에서 새 터미널을 실행합니다.
2. 프로젝트폴더인지 확인하십시요. 예) vue-first>
3. ```vue-first > npm run serve ``` vue_cli_설치 브랜치에서 vue셋팅이 끝난 뒤 나왔던 파란색 명령어입니다.
4. 아래와 같은 내용이 나옵니다. 
<img width="300" alt="스크린샷 2023-03-01 오후 8 30 53" src="https://user-images.githubusercontent.com/48478079/222127357-c3bc9a01-1958-4720-aca4-299a36f11d7e.png">   
url를 클릭하면 로컬서버가 실행되면서 우리의 어플리케이션의 내용이 반영되어 나옵니다   

5. \components폴더에 있는 App.vue를 열어보면 
6. ```<HelloWorld msg="Welcome to ~"/>``` 가 있는데 여기 msg 는 어디있을까요?  
   ```import HelloWorld from './components/HelloWorld.vue' ```의 내용을 따라 컴포넌트 폴더내의 HelloWorld.vue파일을 열어봅니다.
7. ``` <h1> {{ msg }} </h1> ```이 보입니다. 


### 이제 더 자세한 내용을 살펴보기 전에 App.vue 파일에는 3개의 주요부분을 한번 더 짚고 넘어가겠습니다.
template 태그 , script 태그, style 태그입니다. 그리고 script 태그에는 <b>import 컴포넌트, export default </b> 가 있다.
