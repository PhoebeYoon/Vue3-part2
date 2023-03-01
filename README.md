##### :cactus: Vue3 -part2

## 컴포넌트란
컴포넌트에 대한 여러 설명이 있지만 우리는 '독립적이고 재사용 가능한 블록'이라고만 일단 이해하자.  
<img width="500" alt="스크린샷 2023-03-01 오후 3 05 49" src="https://user-images.githubusercontent.com/48478079/222058461-95eed3d6-8ebc-4e83-ad8d-ba7bb1e0c69c.png">

여기서 ``` Header ```,``` Content ```,``` Footer ```,``` Aside ```,``` List ```를 독립적인 재사용가능한 컴포넌트로 생각하면 된다.


### 컴포넌트 생성하기
```
Vue.component('컴포넌트이름', { 컴포넌트 내용 }); 
```
여기서, 컴포넌트이름은 template속성에서 사용할 html 사용자정의 태그이다. 그러니까 이제까지 이미 만들어져있는 태그들만 사용했다면 이제는 본인이 태그를 만든다고 생각하면 좋을 듯하다.

### 컴포넌트 해부
```
Vue.component('my-component',{
 1) components: {
    ProductComponent, ReviewComponent (template에서 사용될 컴포넌트이름 )
  },
 2) props: {
    message: String,
    product: Object,
    email: {
        type: String,
        required: true,
        default: 'none'
        validator: function (value) { ... }
        }
    },
3) data: function(){  return { ...  } },
4) computed: { fullName: function(){ ...  } },
5) watch :{ firstName: function(value, oldvalue) { ... } },
6) methods: { ... },
7) template : '<span> {{ message }} </span> '

}

```
이렇게 7개로 구성되어 있다

### 컴포넌트이름은 대문자로 시작하며 '의미있는 이름'으로 하는 것이 좋다.   
### 컴포넌트 불러올때는  'import 컴포넌트이름 from '경로/파일이름.vue';


### 컴포넌트간 통신
1. 상위(부모) --> 하위(자식) 컴포넌트 간의 데이터 전달
2. 부모 -->  자식으로 데이터 전달시 props라는 속성사용
3. 자식 -->부모로 데이터 전달시 events로만 전달함
4. 상위 --> 하위 컴포넌트로 데이터 전달가능
5. 하위컴포넌트는 상위컴포넌트 값을 직접참조하지 못함
