# 03 if 조건문
## if 조건문
불 표현식의 값이 `true`면 중괄호 안의 문장을 실행, `false`면 문장을 무시.

```
<script>
// 변수 선언
const date = new Date()
const hour = date.getHours()

// if 조건문
if (hour < 12){
    alert('오전입니다')
} else{
    alert('오후입니다.')
}
</script>
```

## 중첩 조건문
조건문 안에 조건문을 중첩하여 사용하는 것을 `중첩 조건문`이라 한다.
여러번 중첩하여 사용도 가능하다.

```
<script>
// 변수 선언
const date = new Date()
const hour = date.getHours()

// if 조건문
if (hour < 12){
    alert('아침먹을 시간입니다')
} else{
	if(hour < 15){
    	alert('점심먹을 시간입니다.')
    } else{
        alert('저녁먹을 시간입니다.')
    }
}
</script>
```

## if else if 조건문
중첩 조건문에서 중괄호를 생략한 형태가 `if else if` 조건문입니다.

```
<script>
// 변수 선언
const date = new Date()
const hour = date.getHours()

// if 조건문
if(hour < 12){
	alert('아침먹을 시간입니다')	
} else if (hour < 15){
    alert('점심먹을 시간입니다.')
} else{
    alert('저녁먹을 시간입니다.')
}
</script>
```

# 03-2 switch 조건문과 짧은 조건문
## switch 조건문
### 홀수/짝수를 구분하는 예제 코드로 확인하기
```
<script>
// 변수 선언
const input = Number(prompt('숫자를 입력하세요.', '숫자'))

// 조건문
switch (input % 2){
    case 0:
        alert('짝수입니다.')
        break
    case 1:
        alert('홀수입니다.')
        break
    default:
        alert('숫자가 아닙니다.')
        break
}
</script>
```

`break` switch 조건문이나 반복문을 빠져나가기 위해 사용하는 키워드
switch 조건문의 괄호 안에는 비교할 값을 입력합니다. 이때 입력한 값을 기준으로 특정 코드를 실행합니다.
만약 입력한 표현식과 case 키워드 옆의 표현식이 같다면 case 키워드 바로 다음에 오는 문장을 실행합니다. 중괄호는 사용하지 않아도 됩니다.

## 조건부 연산자
자바스크립트에는 조건문과 비슷한 역할을 하는 연산자가 있습니다. 바로 `조건부 연산자`이고, 기본 형태는 다음과 같습니다.

```
불 표현식 ? 참일 때의 결과 : 거짓일 때의 결과
```
항을 3개 갖는 연산자는 조건부 연산자가 유일해서 `삼항 연산자`라고 부르기도 합니다.

```
<script>
// 변수
const input = prompt('숫자를 입력해주세요.', '')
const number = Number(input)

// 조건문
const resullt = (number >= 0) ? '0 이상의 숫자입니다.' : '0보다 작은 숫자입니다.'
alert(result)
</script>
```

0 이상인 경우는 (:)의 앞 조건이 노출이 되고, 0 이하인 경우에는 (:)의 뒷 조건이 노출이 된다

## 짧은 조건문
### 논리합 연산자를 사용한 짧은 조건문
아래의 `논리합 연산자`를 사용한 표현식은 뒤에 어떠한 값이 들어가도 항상 참입니다.
```
true || ooo
```
자바스크립트는 이처럼 참이 확실할 때 추가 연산을 진행하지 않습니다.
즉, 노리합 연산자의 좌변이 참이면 우변을 실행하지 않습니다.

```
> true || console.log('실행될까요?')
> true

> false || console.log('실행될까요?')
> 실행될까요?
> undefined
```

### 논리곱 연산자를 사용한 짧은 조건문
논리곱 연산자는 양변이 모두 참일 때만 참이기 때문에 아래의 표현식은 항상 거짓입니다.
```
false && ooo
```
따라서 논리곱 연산자는 좌변이 거짓이면 우변을 실행하지 않습니다.
