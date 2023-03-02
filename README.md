##### :cactus: Vue3 -part2

## Multiple components 
 ``` App.vue ```  (Root component)    
     |  
      
 ``` Header.vue  ```  
 
 ``` Article.vue (parent 컴포넌트) ```  ---  ``` Content.vue ``` (child 컴포넌트)
                                      \  ``` Comments.vue ``` (child 컴포넌트)

``` Footer.vue  ```   


컴포넌트 트리는 아래와 같다
 
 
## 부모 --> 자식 데이터 전달 
부모 컴포넌트로부터 자식 컴포넌트로 어떤 속성의 값을 전달하려고 할때 어떻게 할까?  2가지 방법의 차이를 살펴보자.  

1. props로 데이터 전달 :모든 컴포넌트 인스턴스에는 각자의 범위(scope)가 있다. 상위 컴포넌트가 하위 컴포넌트로 데이타를 전달하고자 할때 <b>props</b> 라는것을 이용한다. 반대로 하위 컴포넌트에서 상위 컴포넌트로 데이터를 전달하고자 할때는 <b>Emit</b>라는 것을 사용한다. 잘 기억해두자. 
<img width="240" alt="스크린샷 2023-03-02 오전 10 57 22" src="https://user-images.githubusercontent.com/48478079/222311016-9ad2c66f-15be-4520-b16b-196be1c3099d.png">

a. 일반 vue객체에서 데이터를 전달하는 방식(우리가 실습하면서 많이 했던 방식)과  
b. 컴포넌트 내에서 데이터의 전달방식이 어떻게 다른지  

앞에서 했던 정렬에 사용했던 내용이다 이것이 a.에 속한 방식이다. 아마 익숙할 것이다  
``` javascript
Vue.createApp({
data(){
  return {
    numbers:[1,4,19,8,6]
     }
  },
~ ~
```
그럼 b.에 속한 방식은 어떤 모양일까  
```javascript 
export default{
props : [ 'Kebab-case'로 작성하고 배열로 표현 ],
data(){
     
   }
```  
일단 모양을 익혀두자. 좀더 언급해야 할것이 있지만 나중에 다시 살펴보자.
2. 이제 a. , b.의 방식으로 살펴보자


``` <Modal/>. ```

