##### :cactus: Vue3 -part2

## Slots(슬롯) 
이것은 단순히 스트링, 불리언, 배열의 내용을 전달하기 위해서가 아니라 템플릿을 재사용 가능한 컴포넌트에 전달하는 것에 사용됩니다.

### 1. 기초사용법  

[부모 컴포넌트]
```
<template>
 <자식컴포넌트>
    내용
 </자식컴포넌트>
</template>

```

[자식 컴포넌트]
```html
<template>
  <slot></slot>
</template>
```

우리가 했던 vue-cli-실행6의 내용을 갖고 변경해보면,  
[App.vue]의 내용을 아래와 같이 변경합니다. ``` <Modal /> ``` 를 ``` <Modal> </Modal> ``` 즉 여는 태그와 닫는 태그로 나눠서 사용해야 합니다.  

```html
<div v-if="showModal"  >
      <Modal  theme="sale"  @close="toggleWin">
        <h2>UVC</h2>
        <p>Learing font-end-developer course</p>
      </Modal>
    </div>

```
[Modal.vue]

```html
template>
  <div class="backdrop" @click.self="closeModal"> 
    <div class="modal" :class="{sale: theme =='sale'}">
      <slot></slot>
    </div>
  </div>
</template>

```
이렇게만 변경하고 실행해 보면,   
<img width="300" alt="스크린샷 2023-03-02 오후 6 18 53" src="https://user-images.githubusercontent.com/48478079/222385591-9d0ffc46-14d6-4663-9756-64b27dbf8e4e.png">  
와 같으면 검정배경을 클릭하면 모달창이 닫힙니다.  

### 2. v-slot 사용법  
새로운 템플릿을 만들고 v-slot를 사용해보겠습니다. v-slot을 사용할 때, 무조건 template 태그로 감싸고 그 컴포넌트 안에서 v-slot를 사용해야 합니다. 

[App.vue]
```html
<template>
  <h1>{{ title }}</h1>
  <p>created by Vue3</p>
    <div v-if="showModal"  >
      <Modal  theme="sale"  @close="toggleWin">
        <h2>UVC</h2>
        <p>Learing font-end-developer course</p>
        <template v-slot:links>   
          <a href="#">아이디 찾기</a> | 
          <a href="#">비번 찾기</a>
        </template>
      </Modal>
    </div>
    <button @click="toggleWin">팝업창보기</button>
</template>
```
template 태그가 2개 있다 바깥쪽에 안쪽에, 그리고 안쪽에 새로 만든 슬롯의 이름은 'links'정했다. 바깥쪽것은 이름이 없다.    
[Modal.vue]
```html
<template>
  <div class="backdrop" @click.self="closeModal"> 
    <div class="modal" :class="{sale: theme =='sale'}">
      <slot></slot>
      <div class="actions">
        <slot></slot>
      </div>
    </div>
  </div>
</template>
```    
Modal.vue에 보면 slot이 두군데 언급되어 있다. 이 상태에서 실행해보면 아래 이미지와 같이 출력된다.  
<img width="260" alt="스크린샷 2023-03-02 오후 6 33 44" src="https://user-images.githubusercontent.com/48478079/222389208-efa37795-30a8-4955-a231-82db91aa2bc8.png">
디폴트인 슬롯이 반복된 것을 확인할 수 있다. 그래서 새로 안쪽에 만든 슬롯에 이름을 지정해주어야 한다. 
Modal.vue의 내용을 이렇게 변경한다.  
```html
 <div class="actions">
        <slot name="links"></slot>
 </div>
```

정리하자면  
부모 컴포넌트에는 ``` <template v-slot:이름> 내용 </template>   ```   
자식 컴포넌트에는 ``` <slot name="이름"></slot>   ``` 

<img width="260" alt="스크린샷 2023-03-02 오후 6 38 25" src="https://user-images.githubusercontent.com/48478079/222391400-97ea8c7e-2e2f-462c-af0e-092b5379a4f4.png">  


## 참고로 알아두자. 

[App.vue] 에서 아래의 내용을 주석처리하고 
```html
<h2>UVC</h2>
<p>Learing font-end-developer course</p>
```  
[App.vue]에서 
```html
<div class="modal" :class="{sale: theme =='sale'}">
<slot>이 내용은 부모컴포넌트에서 여기에 들어갔던 디폴트 slot의 내용이 사라질때만 보입니다</slot>
```   



### 아래의 이미지와 같은 결과를 만들어보세요 스타일을 변경하시면 됩니다.


<img width="280" alt="스크린샷 2023-03-02 오후 8 58 00" src="https://user-images.githubusercontent.com/48478079/222422522-9bb529db-acc4-419c-9d43-6bbdd8648c02.png">   


<b>To complete this project , make it out like this image.
Try it first and reference it down below  later! Okay? :smile: </b>



```style

<style>
.modal {
  width:400px; padding:20px; margin:30% auto;
  background: white;
  border-radius: 10px;
}
.modal p { color:#fff; font-size: 120%; }
.backdrop{ top:0; position: fixed;
  background: rgba(0,0,0,0.5);
  width: 100%;  height: 100%;}
.modal.sale { background:crimson; color:#fff }
.modal.sale h1 { color: #fff;}
.modal .actions{
  text-align: center; margin:30px 0 10px 10px;
}
.modal .actions a{ color:#333; padding: 8px; 
  border:1px solid #eee; border-radius: 4px; 
  text-decoration: none; margin: 10px;}
.modal.sale .actions a{
  color:white
}
</style>

```
