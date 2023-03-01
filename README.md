##### :cactus: Vue3 -part2

## 정렬에 대해 알아봅시다
정렬을 해주는 함수 sort()가 있습니다. 문자는 아스키코드값이 각 문자에 매칭되어 있기 때문에 sort()만 적으면 되는데, 숫자의 경우에는 좀 생각을 해야 합니다.   
왜냐하면 숫자, 1,2,10 이 있을때 우리는 당연히 2가 앞에 나오고 10이 그 뒤에라고 생각하지만 숫자 10의 첫자 '1'이 숫자 '2'보다 적은 숫자라고 판단하여 1,10,2 로 정렬됩니다. 그래서 이것을 해결하는 방법이 몇개 있지만 우리는 수식을 사용하여 해결해보고자 합니다.    
그리고 'https://developer.mozilla.org/'의 설명을 따르면 정렬에 사용되는 문자코드는 'UTF-16' 입니다. 


우선 자바스크립트로만 실행해 보겠습니다.
```javascript
const months = ['March', 'Jan', 'Feb', 'Dec']; 
months.sort();
console.log(months);// 결과는 ["Dec", "Feb", "Jan", "March"]
```
여기서 순차정렬이 기본이라고 했는데 왜 'Jan'이 첫번째가 아니고 'Dec'가 첫번째로 나오지? 하시는 분을 위해.   
정렬을 사람의 방식대로 한다면 'J' 가 첫번째여야 하지만 컴퓨터는 정렬할때 코드값(예, 아스키) 를 사용합니다.   
이 아스키코드에 따르면 " M(77),J(74),F(70),D(68) " 으로 'D'가 가장 작은 숫자입니다. 그래서 'Dec' 이 가장 앞에 있는 것입니다.


이제 숫자에 적용해보겠습니다.
```javascript
const numbers= [3,5,2,1,8]
const numbers2= [3,5,2,1,18]
numbers.sort();
numbers2.sort();
console.log(numbers);  //(5) [1, 2, 3, 5, 8]
console.log(numbers2); //(5) [1, 18, 2, 3, 5]

```
18이 2보다 앞에 나온것을 확인할 수 있습니다. 위에서 설명했던대로 입니다. 그래서 이번에는 아주 간단한 수식을 사용해서 해결해 보겠습니다.
이제 뺄셈을 이용하여 sort()의 개념을 살펴보자

```html
<script>
const numbers2= [3,5,2,1,18]
console.log(numbers2)
b=100;
 numbers2.forEach(function(a){
    console.log('a :',a,'b:',b, "-> ", 100-a)
 })
</script>
```
입력된 숫자 중에서 큰값과 작은 값을 가려내는 것인데, 단순히 100에서 입력값을 뺀 후   
결과값이 크며 입력된 숫자는 작은 숫자이고,   
결과값이 작으면 입력된 숫자는 큰 숫자일것이다.


<img width="191" alt="스크린샷 2023-03-01 오전 11 03 48" src="https://user-images.githubusercontent.com/48478079/222025789-efb85b74-40e8-4f11-9d91-908a716b447a.png">

위의 결과처럼 말이다. 이 결과값을 가지고 정렬을 하면 제대로된 정렬이 될것이다.

```html
<script>
  const numbers2= [3,5,2,1,18]
  numbers2.sort(function(a,b) { return a-b })
  console.log(numbers2)
</script>

```

종합해서 아래와 같이 사용할 수 있다.   

```html
<h1>배열연습</h1>
<div id="app">
<ul>
  <li v-for="number in numbers">{{ number }}</li>
</ul>
<button v-on:click="sortData(numbers)">정렬하기</button>
</div>
<script>
Vue.createApp({
data(){
  return {
    numbers:[1,4,19,8,6]
     }
  },
methods:{
  sortData: function(x){
    x.sort(function(a,b) { return a-b })
  }
}
}).mount('#app');
</script>

```
정렬 알고리즘에 대해 전혀 모른다면 위의 코드에서 return 문 앞에 console.log(a, b, a-b) 로 찍어보면 이해가 될 것이다.

