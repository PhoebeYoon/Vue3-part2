##### :cactus: Vue3-part2

### lesson20의 이벤트 파일에 이어서 진행됩니다 

```html
<div v-if=showBook>
    <ul v-for="book in books">
      <li>
        <h3>{{book.title}}</h3>
        {{ book.author}}</li>
    </ul>
  </div>
  
  
   books:[
      {title :'The Load of Rings'  , author: 'J. R. R. 톨킨'},
      {title :'Harry Potter' , author: "J.K. 롤링"},
      {title : '이상한 엄마' , author: '백희나'}
    ]
    }

```
