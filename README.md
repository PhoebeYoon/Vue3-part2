##### :cactus: Vue3 -part2

## Vue Router에 대해 알아보자
여러 컴포넌트가 함께 있는 페이지를 만들려면 vue router를 이용해야 한다. vue rounter란 vue.js에서 페이지간 이동을 위한 라이브러리이다. 페이지를 변경할때 경로가 변경되면 변경된 요소의 영역에 컴포넌트를 생성하는 역할을 한다.

## Vue Rounter 설치
사용하기 위해 vue rounter를 설치해야한다. 새로운 프로젝트를 만들고 실습해보자
 
```  터미널에서 > vue create rounter-project   ```   
:ballot_box_with_check: ```  Manually select features  ```  
:ballot_box_with_check: ``` Rounter 선택 ```
:black_square_button: ``` Linter / Formatter```   
``` 3.x   ```  
``` Use history mode for router? Y  ```   
```In dedicated config files ```  
```Save this as a preset for future projects? N ```    
``` > cd rounter-project 엔터 ```  
```code . ```

#### 설치가 완료되고나면 package.json 파일을 열고 "vue-router": "^4.0.3" 항목이 있는지 확인만 하자.  





## Multiple components 
 ``` App.vue ```  (Root component)    
     |  
      
 ``` Header.vue  ```  
 
 ``` Article.vue (parent 컴포넌트) ```  ---  ``` Content.vue ``` (child 컴포넌트)
                                      \  ``` Comments.vue ``` (child 컴포넌트)

``` Footer.vue  ```   


컴포넌트 트리는 아래와 같다
