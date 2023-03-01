##### :cactus: Vue3 -part2

## 배열에 데이터를 추가,삭제해보자
splice()메소드는 배열의 기존 요소를 삭제 또는 교체하거나 새 요소를 추가하여 배열의 내용을 변경합니다.

array.splice(<b>배열의 변경을 시작할 인덱스</b>, _제거할 요소의 갯수_ , 추가할 요소)

```
array.push(나는추가된다) - 앞에 아무것도 없으니 다짜고짜 들어간다고 생각하세요
array.splice(지정위치,0, 추가되는데이터) 
         - 중간에 삽입되기때문에 어떤얘뒤에 들어갈지 알려주고,몇개인지는 '0'으로 적고, 삽입할 얘를 적습니다   
         그리고 여기서의 위치는 인덱스번호입니다
array.splice(지정위치, 1) - 어떤얘뒤에서부터 1개를 선택하니까, 삭제한다는 얘기입니다. 여기서의 위치는 인덱스번호 입니다
```
Vue에서는 자바스크립트의 문법을 사용합니다 문법이 다른것은 아니지만 Vue가 잘 인지할 수 있는 형식을 따로 있다고 생각하십시오.

```html
<h1>배열연습</h1>
<div id="app">
  <ul>
    <li v-for="item in items">{{ item }}</li>
  </ul>
  <button v-on:click="add">추가</button>
  <button v-on:click="insert">사과다음에 삽입</button>
  <button v-on:click="del">키위삭제</button>
</div>
<script>
Vue.createApp({
data(){
  return {
    items:['🍎','🍋','🥝','🍒','🥥']
     }},
  methods:{
    add:function(){
      this.items.push('🍓')
    },
    insert:function(){
      this.items.splice(1,0,'🍍')
    },
    del:function(){
      this.items.splice(2,1)
    }
  }
}).mount('#app');
</script>

```
