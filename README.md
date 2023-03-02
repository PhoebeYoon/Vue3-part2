##### :cactus: Vue3 -part2

## Slots(슬록) 
이것은 단순히 스트링, 불리언, 배열의 내용을 전달하기 위해서가 아니라 템플릿을 재사용 가능한 컴포넌트에 전달하는 것에 사용됩니다.

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

