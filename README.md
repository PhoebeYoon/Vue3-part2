##### :cactus: Vue3 -part2

## Multiple components 
 ``` App.vue ```  (Root component)    
     |  
      
 ``` Header.vue  ```  
 
 ``` Article.vue (parent 컴포넌트) ```  ---  ``` Content.vue ``` (child 컴포넌트)
                                      \  ``` Comments.vue ``` (child 컴포넌트)

``` Footer.vue  ```   


컴포넌트 트리는 아래와 같다
 
 이제 간단한 컴포턴트를 등록하고 사용해보자.
 [ App.vue ]
 ```html
<template>
  <h1>{{ title }}</h1>
  <Modal />
</template>

<script>
import Modal from './components/Modal.vue'
// Modal.vue 삽입하고
export default {
  name :'App',
  components :{ Modal}, 
  data(){
    return {
       title :"My First Vue Application"
    }
  }
}
</script>
```
 
1) import Modal from './components/Modal.vue' 컴포넌트를 불러오고,  
2) components :{ Modal},  컴포넌트를 등록하고,   
3) <Modal />  컴포넌트를  태그처럼 사용
  
