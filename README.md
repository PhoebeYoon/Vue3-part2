##### :cactus: Vue3 -part2
### 파일들의 상호관계를 파악하고 어떻게 작동하는지 알기 위해 파일의 내용을 간단하게 만들겠습니다.

1.App.vue를 찾아 아래와 같이 수정합니다
```html
<template>
  <HelloWorld msg="Welcome First Application"/>
</template>

``` 
2. HelloWorld.vue
```html
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

```
변경한 후에 브라우저에서 내용을 확인해보자.

### 이제 App.vue의 내용을 바꿔서 실행해보겠습니다.
```html
<template>
  <h1>{{  title  }}</h1>
</template>
<script>
export default {
  name :'App',
  data() {
    return {
      title :'My Frist Vue App'
    }
  }
}
</script>
``` 
실행해서 결과를 확인해 보세요. 위의 내용은 \components\HelloWorld.vue 를 불러오지 않고 App.vue의 내용 변경만으로 브라우저에 출력한 것입니다. 그러니까 \components 폴더는 필요에 의해 컴포넌트를 만들어서 삽입해 사용하면 되는 것입니다. 물론 컴포넌트를 만들어서 사용할 것입니다. 

### 스타일을 변경해보자  
App.vue 파일안에서 
``` css
h1 { border-bottom: 2px dashed #000; 
  padding-bottom:10px;}
```
를 삽입한 다음에 브라우저에서 확인해 보면, 
브라우저 개발자도구 > 엘리먼트탭에 보면,   
App.vue에 있던 style 내용이 삽입되어 있는것을 확인할 수 있다.


 
