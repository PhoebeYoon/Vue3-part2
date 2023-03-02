##### :cactus: Vue3 -part2

##### :star: vue_cli_실행5에 이어지는 내용입니다.

## 아래의 이미지처럼 작동하도록 만들어보자.  
<img width="250" alt="스크린샷 2023-03-02 오후 2 05 01" src="https://user-images.githubusercontent.com/48478079/222336145-fd1afcdb-0049-4809-a738-58d9c8892b65.png"> 

<img width="250" alt="스크린샷 2023-03-02 오후 1 53 41" src="https://user-images.githubusercontent.com/48478079/222334595-a2d0484a-e95a-410a-b709-0f0f703d7a5f.png"> <img width="250" alt="스크린샷 2023-03-02 오후 1 53 41" src="https://user-images.githubusercontent.com/48478079/222335270-cb9fa327-862a-4adb-b2d2-bdc2600fb38d.png">   
<img width="250" alt="스크린샷 2023-03-02 오후 2 05 19" src="https://user-images.githubusercontent.com/48478079/222336190-489fa534-1985-44be-bf28-19b15e7a07c7.png">

1. 팝업창 보기를 클릭하면 모달창이 나타나게하기 위해  
[ App.vue ]
```
1) <template>안에 모달창을 보기/감춤을 다루기 위해 <div> 태그를 만들고 <Modal>를 자식노드로 만든다. 
   그리고 <div> 안에 v-if문을 추가하여 true/false에 따라 보이거나 감추도록 설정한다
2) 1)을 지정했으니 v-if문에서 값인 showModal의 속성값을 data()의 return문에 디폴트값을 
   false로 지정하여 추가한다.
3) 그리고 <button>팝업창보기</button> 를 만들고 클릭이벤트를 지정한다. 이벤트이름을 showModal로 하고 
    methods:에서 showModal의 값을 반대로 지정하도록 ( !showModal )한다.
4) 여기까지 하면 팝업창보기 버튼을 클릭했을때 모달창이 실행된다. 문제는 이것의 z-index값이 '팝업창보기' 버튼보다 
   높아서 이 버튼을 다시 클릭하지 못한다는 것이다 그래서 z-index값을 바꾸는 대신 모달창의 빈곳(검정색배경)을 
   클릭하면 모달창이 닫히도록 만드는 것이다.
5) Modal.vue 에 methods:{ } 안에 toggleWin() 함수를 정의하여 값을 반대로 지정하도록 했다 
   (!this.showModal)

<div v-if="showModal">
      <Modal :comments="comments" :text ="text" theme="sale" />
    </div>
</templage>
<button @click="toggleWin">팝업창보기</button>

data(){
    return {
      title :"My First Vue Application",
      comments:"회원가입 | 로그인",
      text:'가입혜택이 있습니다',
      showModal : false
    }
  },
  methods:{
    toggleWin() {
      this.showModal=!this.showModal
    }
  }
```  
그런데 여기서 모달창의 검정색 배경을 클릭하는 부분에서 이 검정색배경은 Modal.vue에 속한 부분이라,  
[ Modal.vue ]
```
<template>
  <div class="backdrop" @click="closeModal">  으로 변경하고
 
<script>
export default {
  props:[ 'comments','text', 'theme'],
  methods:{ closeModal(){ 
    this.$emit('close')
     <!--          
       여기서 부모컴포넌트 (App.vue)에 정의된 toggleWin() 함수를 실행시켜야 합니다
       자식컴포넌트에서 부모 컴포넌트의 데이터를 가져올때 사용하는 $emit()을 사용합니다
       $emit의 값으로는 'emit하고 싶은 이벤트의 이름'를 적는데
       사용자이벤트로 close라는 이벤트를 새로 만듭니다 (close이벤트라는 것은 없습니다 
       사용자이벤트로 만든것입니다)
       그럼 이 'close'라는 이벤트를 받는 뭔가가 있어야 하는데, 그게 어디에 있냐면 
       바로 부모 컴포넌트에 있습니다
       그럼 이 'close'라는 이벤트를 받는 뭔가가 있어야 하는데, 어디에 있어야 하냐면
       바로 부모컴포넌트에 있어야 
       -->
    }}
}
</script>
``` 
[ App.vue ]

```
Modal태그에 @close 이벤트를 추가한다. 아래처럼.
<div v-if="showModal">
      <Modal :comments="comments" :text ="text" theme="sale" @close=""/>
</div>
그리고 @close 이벤트는 결국은 showModal의 값을 바꿔야하기 때문에 showModal의 값을 바꾸는
toggelWin()함수를 부르면 되는 것이다
```
결국 $emit(사용자이벤트)의 역할은 자식 컴포넌트와 부모컴포넌트에 동일한 이벤트를 추가하여 
서로 연결시켜주는 것이다. 마치 플러그와 소켓처럼  

<img width="425" alt="스크린샷 2023-03-02 오후 2 45 15" src="https://user-images.githubusercontent.com/48478079/222341795-b0d42ecc-1f86-4c4b-878f-c4bfd9a316a2.png">

## Event Modifiers를 삽입해보자  
이것이 왜 필요한지 먼저 살펴보자.  위에 있는 결과에서 검정색배경을 클릭하면 모달창이 닫히는 것을 구현했다. 
하지만 검정색 배경이 아닌 곳 예를 들어 빨간색안쪽를 클릭해도 모달창이 닫힌다.  
그래서 이번에는 검정색배경부분을 클릭했을때만 모달창이 닫히도록 만들어보자 아주 간단하다.  
[ Modal.vue ]
```
 <div class="backdrop" @click.self="closeModal">  처럼 @click.self 를 추가해주면 된다
```






