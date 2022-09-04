## 04-2 반복문
### for in 반복문
배열과 함께 사용할 수 잇는 반복문은 `for in` 반복문 입니다.
배열 요소를 하나하나 꺼내서 특정 문장을 실행할 때 사용합니다.

```
<script>
for (const 반복변수 in 배열 또는 객체) {
	문장
}
</script>
```

```
<script>
//변수 지정
const todos = ['우유 구매', '업무 매일할일', '필라테스 수업']

//for in 반복문
for (const i in todos) {
	console.log(`$(i)번째 할일 ${todos[i]}`)
}
</script>

```

`for in` 반복문은 구문 자체로 코드의양이 어느 정도 있어서 코드를 하나하나 입려하는 것이 힘들 수 있습니다. 이럴 때 `코드 블록`을 사용해주세요.

> `for in` 반복문은 안정적으로 쓰기위해선 추가로 코드를 입력해야된다. 가장 기초적인 반복문이라 알아보았지만, 이후 설명 하는 `for of`반복문과 `for` 반복문을 활용하는 것이 좋다.

### for of 반복문
`for in` 반복문의 안정성을 위해 나온 반복문이다.

```
<script>
for (const 반복 변수 of 배열 또는 객체) {
	문장
}
// for in 문과 다르게 반복변수에 요소의 값이 들어갑니다.
</script>
```

예시를 보게되면,
```
<script>
//변수 지정
const todos = ['우유 구매', '업무 매일할일', '필라테스 수업']

for (const todo of todos) {
	console.log(`오늘의 할 일: ${todo}`) 
}
</script>
```

### for 반복문
일반적으로 `for` 반복문은 특정회수만큼 반복하고 싶을때 사용하는 범용적인 반복문이다.
```
<script>
for (let i = 0; i < 반복 횟수; i++){
	문장
}
</script>
```

#### 배열을 사용하는 경우
일반적으로 배열을 사용하는 경우는 배열의 `length` 메소드를 이용한다.
```
<script>
//변수 지정
const todos = ['우유 구매', '업무 매일할일', '필라테스 수업']

for (let i = 0; i < todos.length; i++ ) {
	console.log(`오늘의 할 일: ${todo}`) 
}
</script>
```

### while 반복문
`while` 반복문은 `if 조건문`과 형태가 매우 비슷한 반복문입니다. `if 조건문`과 다른 점은 문장을 한 번 만 실하고 끝나는 것이 아니라 불 표현식에서 `true`면 계속해서 문장을 실행한다는 것입니다.

```
while (불 표현식){
	문장
}
```

while 반복문의 경우 조건이 변하지 않는다면 무한루프에 빠질 수 있다.
때문에 아래와 같이 기본을 지키면서 사용해야된다.
```
<script>
let i = 0
while (confirm('계속 진행하시겠습니까?'){
	alert(`${i}번째 반복입니다.`)
    i = i + 1
}
</script>
```

`confirm`에서 확인 버튼을 누르는 경우 >> `true`로 되어 반복
`confirm`에서 취소 버튼을 누르는 경우 >> `false`로 되어 정지


### break 키워드
`break` 키워드는 `switch 조건문`에서와 같이 반복문을 벗어날 때 사용하는 키워드입니다.
`while` 반복문은 `무한루프`에 빠질수 있는데, `break`를 통해 `무한루프`를 빠져나올 수 있습니다.
```
<script>
while (true){
	문장
} break
</script>
```

### continue 키워드
`continue` 키워드는 반복문 안의 반복 작업을 멈추고 반복문의 처음으로 돌아가 `다음` 반복 잡업을 진행합니다.
```
<script>

// 변수를 선언합니다.
let output = 0;

// 반복문
for( let i = 0; i <= 10; i++){
	continue
    alert(i)
}
</script>
```
코드가 실행되면, 경고창이 출력되지 않는다. `continue` 키워드로 인해 다시 다음 반복문이 실행이 된다.


