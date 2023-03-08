###### :cactus: Vue.js 

# Vue3-part2

#### Vue3의 part1를 먼저 실습한 이후에 이어서 학습하세요

## 이 과정을 통해 여러분은
1. v-for의 사용법을 익히게 될 것입니다.
2. 배열에 대해 배우며 배열에 사용되는 함수들에 대해 익히게 될 것이다
3. 정렬(sort)의 기본 개념과 순차정렬, 역순으로 정렬하는 원리를 배우게 될것입니다.
4. 컴포넌트가 무엇이며 어떻게 생성하고 다루는지 알게 될 것입니다.
5. slot이 무엇이고 왜 사용하는지, 어떻게 사용하는지 알게 될 것입니다
6. teleport이 무엇이고 왜 사용하는지, 어떻게 사용하는지 알게 될 것입니다 
7. 



### 컴포넌트의 기본구조를 vs code에 셋팅하기 
-  vs code > file > preference > User snippets, 검색창에서 vue 엔터 > vue 선택
``` 
"Generate Basic Vue Code":{
	"prefix":"vue-start",
	"body": [
 "<template>\n<div></div>\n</template>\n<script>\n\nexport default{ 
  \n\tname:'',\n\tcomponents:{},\n\tdata(){\n\t\treturn{\n\t\t\tsampleData:''\n\t\t};\n\t},
  \n\tsetup(){},\n\tcreated(){},\n\tmounted(){},\n\tunmounted(){},\n\tmethods:{}\n}\n</script>"
	],
	"description": "Generate Basic Vue Code"
}
```
이렇게 설정하고
📁임의의파일.vue 를 만들고 빈화면에서 그냥 'vue' 라는 글자를 적으면 'vue-start' 팝업으로 나타난다. 이것을 선택하면 자동완성으로 기본태그들이 쭈욱 나타난다. 아래와 같이.  

```
<template>
<div></div>
</template>
<script>

export default{ 
  name:'',
  components:{},
  data(){
    return{
      sampleData:''
    };
  },
  setup(){},
  created(){},
  mounted(){},
  unmounted(){},
  methods:{}
}
</script>
```
