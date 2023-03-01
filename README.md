##### :cactus: Vue3 -part2


## 이제 Vue CLI로 웹사이트를 만들어보겠습니다 
Vue CLI는 터미널/명령줄에서 Vue로 작업하는 데 사용되는 도구 키트입니다

1. node.js사이트로 이동해서 node.js 를 다운로드 후 설치하자
2. 윈도우의 'cmd' 명령어를 실행한 후 ``` node -v ```엔터  ``` v18.14.2  ```(설치시점에 따라 나오는 숫자는 다릅니다) 나오면 잘 설치된 것이다. 
3. vue/cli 설치방법 : 
  - 맥에서   
    a) ```npm install -g @vue/cli ```  
       ( 혹시 permission 어쩌구 하면서 errno: -13, code: 'EACCES' 등 에러가 난다면 아래것으로 시도)   
    b) ``` sudo npm install -g @vue/cli ``` --> 패스워드 입력
  - 윈도우에서 ``` npm install -g @vue/cli ```
4. 프로젝트 생성하기
  - 원하는 폴더로 이동 ( 터미널에서 cd 폴더명 )
  -``` vue create 프로젝트명 (예, vue-first) ```
  - 이후에 여러가지를 물어보는데 
<img width="370" alt="스크린샷 2023-03-01 오후 5 35 20" src="https://user-images.githubusercontent.com/48478079/222087200-2414864b-fb8f-4378-ae40-2f084bb6c64e.png"> 
<img width="370" alt="스크린샷 2023-03-01 오후 5 36 31" src="https://user-images.githubusercontent.com/48478079/222087216-a60f4f8f-0beb-4e4e-9857-7cca1bc943a8.png">
<img width="297" alt="스크린샷 2023-03-01 오후 5 36 51" src="https://user-images.githubusercontent.com/48478079/222087339-ab68e7ae-7b1d-468f-a055-c61b697fd398.png">
<img width="350" alt="스크린샷 2023-03-01 오후 5 37 35" src="https://user-images.githubusercontent.com/48478079/222087357-1d858234-1d28-4cc2-b17d-c1b925287e0c.png">
<img width="500" alt="스크린샷 2023-03-01 오후 5 37 56" src="https://user-images.githubusercontent.com/48478079/222087377-e40b7e51-7b5f-4464-8c14-db2480d06efb.png">  

모든 설치가 잘 되었다면  
<img width="375" alt="스크린샷 2023-03-01 오후 6 00 00" src="https://user-images.githubusercontent.com/48478079/222092111-d07d32e6-93b5-4281-8bf5-9151ba36d38c.png">  
이런 화면이 나올 것이다.   
이제 이미지의 내용 중 마지막에 있는 것처럼 실행해보자

5. cd vue-first 엔터 > 폴더의 내용을 보면 아래처럼 여러개의 폴더와 파일이 보일 것이다.

<img width="193" alt="스크린샷 2023-03-01 오후 6 03 59" src="https://user-images.githubusercontent.com/48478079/222093037-668f7565-c908-4c39-bc74-33fa8fc0d54e.png">

6. code .  ( vs code 실행) 

### 설치된 내용 설명
1. <b>node_modules</b> : package.json에 명시된 library나 dependency들이 설치되어 있는 폴더이면서 라이브러리들이 몽땅 들어가 있는 폴더입니다 그래서 git에 프로젝트를 업로드할때 이 폴더는 제외시키곤 합니다.(용량이 크니까요) 이 폴더에 있는 내용은 수정하는 것이 아닙니다.
2. <b>\public 폴더</b>에는 index.html 파일이 있습니다. 그리고 우리가 이제까지 공부할때 사용했던 그 id='app'이 들어가 있습니다. 브라우저에서 이 index.html 파일을 불러옵니다 파일을 열어보시면 내용이 비어있고 ``` <div id='app'></div> 만 달랑 들어있습니다. 여기에 들어갈 내용은 어디있을까요? 
3. <b> \src폴더 <b>에는
     ```
    \src
     ⎿\assets
     ⎿\components
       main.js
       App.vue
  
  ```
