##### :cactus: Vue3 -part2


## 이제 Vue CLI로 웹사이트를 만들어보자
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

5. cd vue-first 엔터 > code .  (엔터) : 이 단계에서 package.json 파일의 내용을 좀 바꿔야한다.  
6. 

