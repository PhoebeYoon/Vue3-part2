##### :cactus: Vue3-part2

### lesson20의 이벤트 파일에 이어서 진행됩니다 

아래의 이미지를 참조로 직접 코드를 만들어보세요.   
<img width="283" alt="스크린샷 2023-02-28 오후 9 07 12" src="https://user-images.githubusercontent.com/48478079/221851212-8de730d1-23ca-44c6-b3b3-a0927b4b4d10.png"> <img width="270" alt="스크린샷 2023-02-28 오후 9 08 55" src="https://user-images.githubusercontent.com/48478079/221851274-496a6286-b6af-43f5-9919-973a87184bab.png">   

<img width="250" alt="스크린샷 2023-02-28 오후 9 17 17" src="https://user-images.githubusercontent.com/48478079/221852235-eb53d1d5-9121-4911-bfdf-035a13158888.png">


```html
 books:[
      {title :'구름빵'  , author: 'J. R. R. 톨킨', img:'./img/3.jpg', isFav:true},
      {title :'알사탕' , author: "J.K. 롤링", img:'./img/2.jpg',isFav:false},
      {title : '이상한 엄마' , author: '백희나', img:'./img/1.jpg',isFav:false}
    ]
``` 
를 사용했고, li태그를 사용했습니다. li태그 토글하면 색상이 바뀝니다. 그리고 아래쪽 버튼을 클릭하면 책 목록이 출력되거나 사라집니다

```html
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<style>
body{ background: #eee; max-width:80%; margin: 20px auto; }
p, h3, ul{ margin: 0; padding: 0 }
li{list-style-type: none; background: #fff;
  margin: 20px auto; padding: 10px 20px;
  border-radius: 10px; display: flex;
  align-items: center; justify-content: space-between;}
li.fav{  background:#6495ED; color: white;}
img { width: 100px; height: auto;}
</style>
</head>
<body>
<h1>올해의 책 선정</h1>
<div id="app">
<div v-if=showBook>
  <ul>
    <li v-for="book in books" :class="{ fav: book.isFav }" @click="toggleFav(book)">
      <img :src="book.img"  :alt="book.title" >
      <h3>{{book.title}}</h3>
      <p>{{ book.author}}</p></li>
  </ul>
</div>
<div v-else>
<p>아래버튼을 클릭해서 책보기</p>
</div>
<button v-on:click="toggleShowBook">
<span v-if="showBook">Hide books</span>
<span v-else>Show books</span>
</button>
</div>
 
<script>
Vue.createApp({
data(){
  return {
    showBook :true,
    books:[
      {title :'구름빵'  , author: 'J. R. R. 톨킨', img:'./img/3.jpg', isFav:true},
      {title :'알사탕' , author: "J.K. 롤링", img:'./img/2.jpg',isFav:false},
      {title : '이상한 엄마' , author: '백희나', img:'./img/1.jpg',isFav:false}
    ]
    }
},
methods :{
  toggleShowBook(){
    this.showBook = !this.showBook
  },
  toggleFav(selectedItem){
    console.log(selectedItem);
    selectedItem.isFav = !selectedItem.isFav
  }
}
}).mount('#app');
</script>
</body>
</html>

```
