# 함수
## 05-1 함수의 기본 형태
### 용어정리
1. 함수호출 : 함수를 사용하는 것
2. 매개변수 : 함수를 호출할 때는 괄호 내부에 여러가지 자료를 넣는데, 이러한 자료를 의미 한다.
3. 리턴값 : 함수를 호출해서 최종적으로 나오는 결과

### 익명 함수
```
function(){}
```

함수를 코드의 집합이라고 말하는 이유는 중괄호 내부에 코드를 넣기 때문입니다.

> 함수의 장점
- 반복되는 코드를 한 번만 정의해놓고 필요할 때마다 호출하므로 반복 작업을 피할 수 있다.
- 긴 프로그램을 기능별로 나눠 여러 함수로 나누어 작성하며 모듈화로 전체 코드의 가독성이 좋다.
- 기능별(함수별)로 수정이 가능하므로 유지보수가 쉽다.

```
// 익명함수 선언하기
<script>
// 변수를 생성합니다.
const 함수 = function () {
	console.log('함수 내부의 코드입니다 ...1')
    console.log('함수 내부의 코드입니다 ...2')
    console.log('함수 내부의 코드입니다 ...3')
    console.log('')
}

// 함수를 호출합니다.
함수()
함수()

//출력합니다.
console.log(typeof 함수)
console.log(함수)
</script>
```

![](https://velog.velcdn.com/images/planic324/post/97bcbd1c-1cd4-4513-b2e4-fda717a5333d/image.png)

함수는 코드의 집합입니다. 그래서 함수를 실행하면 여러 코드를 한 번에 묶어서 실행할 수 있으며, 필요할 때마다 호출을 반복적으로 사용할 수도 있습니다.

함수의 자료형은 `function`이며 현재 코드에서 함수를 출력하면 `f(){}`라고 출력됩니다. 이때 `f`는 함수를 의미합니다.

이처럼 이름이 붙어있지 않는 함수를 `익명 함수`라고 표현합니다.

### 선언적 함수
이름이 있는 함수를 `선언적 함수`라고 한다.

```
function 함수 () {}
```

```
<script>
    // 변수를 생성합니다.
    function 함수 () {
        console.log('함수 내부의 코드입니다 ... 1')
        console.log('함수 내부의 코드입니다 ... 2')
        console.log('함수 내부의 코드입니다 ... 3')
        console.log('')
    }

    함수()
    함수()

    // 출력
    console.log(typeof 함수)
    console.log(함수)
    
</script>
```

실행결과는 익명 함수와 큰 차이는 없다. 한가지 차이점은 함수를 출력햇을때 `이름`이 붙어있는 것뿐입니다.

### 매개변수와 리턴값
> 매개변수 : 함수를 호출할 때 괄호 안에 적는 것
> 리턴값 : 함수의 최종 결과

```
<script>
// 기본  형태의 함수 만들기
	// 함수를 선언합니다.
	function f(x){
    	return x * x
    }
    
    // 함수를 호출합니다.
    console.log(f(3))
    
    //실행결과 : 9
</script>
```

## 기본적인 함수 예제
### 윤년을 확인하는 함수 만들기
> - 4로 나눠 떨어지는 해는 윤년이다.
> - 하지만 100으로 나누어 떨어지는 해는 윤년이 아니다.
> - 하지만 400으로 나누어 떨어지는 해는 윤년이다.

```
<script>
    function isLeapYear(year) {
        return (year % 4 === 0) && (year % 100 !== 0) || (year % 400 === 0)
    }

    console.log(`2020년은 윤달일까? === ${isLeapYear(2020)}`)
    console.log(`2010년은 윤달일까? === ${isLeapYear(2010)}`)
    console.log(`2000년은 윤달일까? === ${isLeapYear(2000)}`)
    console.log(`1990년은 윤달일까? === ${isLeapYear(1990)}`)
    
</script>
```
### A부터 B까지 더하는 함수 만들기
```
<script>
    function sumAll(a, b){
        let output = 0;
        for (let i = a; i <= b; i++){
            output += i
        }
        return output;
    }

    console.log(`1부터 100까지 합은 : ${sumAll(1, 100)}`);
    console.log(`1부터 500까지 합은 : ${sumAll(1, 500)}`);
    
</script>
```

## 나머지 매개변수
> 가변 매개변수 함수 : 호출할 때 매개변수의 개수가 고정적이지 않은 함수

자바스크립트에서는 이러한 함수를 구현할 때는 `나머지 매개변수`라는 특이한 형태의 문법을 사용한다.

```
<script>
	function 함수이름(...나머지 매개변수) {}
</script>
```

함수의 매개변수 앞에 마침표 (...)를 입력하면 매개변수들이 `배열`로 들어옵니다.

```
<script>
    function min(...items){
        let output = items[0];
        // 매개변수 items는 배열처럼 사용한다.
        for (const item of items){
            if (output > item){
                output = item
            }
        }
        return output
    }

    // 함수호출하기
    console.log('min(52, 273, 32, 103, 275, 24, 57)');
    console.log(`= ${min(52, 273, 32, 103, 275, 24, 57)}`)
    
</script>
```
![](https://velog.velcdn.com/images/planic324/post/2b33798f-c1fd-4ce2-8b60-2787c641d593/image.png)

## 기본 매개변수
함수의 매개변수로 항상 비슷한 값을 입력하는 경우가 있다. 항상 같은 매개변수를 여러 번 반복해서 입력하는 것이 귀찮게 느껴질 수 있다. 이러한 경우에 매개변수에 기본값을 지정하는 `기본 매개변수`를 사용합니다.

```
<script>
	function 함수이름(매개변수, 매개변수=기본값, 매개변수=기본값)
</script>
```
매개변수는 왼쪽부터입력하므로 다음과 같이 함수를 작성하면 기본 매개변수의 의미가 없습니다. b(2번째) 값을 전달하기 위해선 a(1번째)값을 채워야 하기 때문입니다.

```
<script>
	function 함수이름(a=매개변수, b) {}
</script>
```

### 급여계산기 만들어보기
```
<script>
    function earnings (name, wage=8560, hours=40){
        console.log(`# ${name}님의 급여정보`)
        console.log(`- 시급: ${wage}원`)
        console.log(`- 근무시간: ${hours}시간`)
        console.log(`- 급여: ${wage * hours}원`)
        console.log('')
    }

    earnings('구름')

    earnings('별', 10000)

    earnings('인성', 10000, 52)
    
</script>
```