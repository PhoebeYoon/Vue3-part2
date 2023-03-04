##### :cactus: Vue3 -part2

### form-project 설정하기
1. ``` 터미널창 > vue create form-project ``` :open_file_folder: 
``` Manually select features ```  	:open_file_folder:  ``` 기본선택 해제 (Linter /Formatter)  ``` :open_file_folder: ``` 3.x ``` :open_file_folder: ```In dedicated config files ```  :open_file_folder:  ``` n ```

2. ``` 터미널창 >cd  form-project ```  :open_file_folder: ``` form-project > code .  ``` 
3. :open_file_folder: components 폴더를 찾아 HelloWorld.vue 파일을 삭제한다 
4. App.vue 파일을 열고  
   ```  import HelloWorld from './components/HelloWorld.vue'  ``` 삭제   
   ```  <template>  안에 있는 내용 삭제 </template>  ```  
   ```  components: { HelloWorld 요거만 삭제 }  ```    
5. :open_file_folder: components > SignUp.vue 파일 생성 > 파일안에서 <b>'vue'</b> 엔터 ( 자동완성으로 기본태그들이 삽입된다)
6. 아래와 같이 내용을 수정한다 [ SignUp.vue ]
``` html

<template>
  <form>
    <label>Email : </label>
    <input type="email" required>
  </form>
</template>
<style>
form {
  max-width: 420px; margin: 30px auto;
  background: white; text-align: left;
  padding: 40px; border-radius: 10px;
}
label {
  color: #aaa; display: inline-block;
  margin: 25px 0 15px; font-size: 0.6em;
  text-transform: uppercase; letter-spacing: 1px;
  font-weight: bold;
}
input, select {
  display: block; padding: 10px 6px;
  width: 100%; box-sizing: border-box;
  border: none; color: #555;
  border-bottom: 1px solid #ddd;
}
</style>
```
[ App.vue ]

```html
<template>
  <SignUp></SignUp>
</template>
<script>
import SignUp from './components/SignUp.vue'

export default {
  name: 'App',
  components: { 
    SignUp
  }
}
</script>

```  
7. 이제 터미널창에서 ``` > npm run serve 엔터 ```  하고 브라우저에서 확인해 보자. 

<img width="361" alt="스크린샷 2023-03-04 오후 12 05 06" src="https://user-images.githubusercontent.com/48478079/222872763-a1ff9752-4b76-4a86-b082-0c3cc8d661a7.png">
