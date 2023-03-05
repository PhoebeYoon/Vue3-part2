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

#### 설치가 완료된 후 확인해보자 
1. package.json 파일을 열고 "vue-router": "^4.0.3" 항목이 있는지 확인만 하자.  
2. :file_folder:src :file_folder:rounter 폴더가 있는지 확인해보자
3. :open_file_folder:rounter 안에는 index.js 파일이 있다. 이 index.js 파일안에 모든 라우터에 대한 내용이 들어간다 기억하자.
4. index.js 파일을 열어보면 rountes=[ ]가 있는데, 각 오브젝트는 개별적인 라우터를 대표하며, 각 오브젝트는 3개의 속성( path, name, component ) 을 가진다. ( each object represents a single route so each object has these different properties- path, name, component )
- path : 루트로부터의 url 
- name: 라우터의 이름 (식별해주는)
- component : 우리가 사용한 컴포넌트    



#### 설치된 대로 일단 실행해보자
터미널을 실행한 후에 ``` > npm run serve ``` 브라우저에서 페이지가 정상적으로 작동하는것을 먼저 확인해보자

#### index.js 내용을 아래와 같이 수정하고 정상적으로 작동하는지 확인해 보자 
[ index.js ] 
``` javascript
import { createRouter, createWebHistory } from 'vue-router'
import Home from '../views/HomeView.vue'
import About from '../views/AboutView.vue'

const routes = [
  {
    path: '/',
    name: 'home',
    component: Home
  },
  {
    path: '/about',
    name: 'about',
    component: About
  }
]

```  
:file_folder: views 안에 AboutView.vue, HomeView.vue 라는 파일명을 따라 작성한것이다.


이렇게해서 간단한 라우터를 연습해보았다. 다음 강의에서 계속이어집니다 




## Multiple components 
 ``` App.vue ```  (Root component)    
     |  
      
 ``` Header.vue  ```  
 
 ``` Article.vue (parent 컴포넌트) ```  ---  ``` Content.vue ``` (child 컴포넌트)
                                      \  ``` Comments.vue ``` (child 컴포넌트)

``` Footer.vue  ```   


컴포넌트 트리는 아래와 같다
