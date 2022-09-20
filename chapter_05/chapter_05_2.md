# 함수
## 05-2 함수 고급

### 콜백 함수
매개변수로 전달하는 함수를 `콜백 함수`라고 한다.

```
<script>
    // 함수를 선언합니다.
    function callThreeTimes (callback) {
        for (let i = 0; i < 3; i++){
            callback(i);
        }
    }

    function print (i) {
        console.log(`${i}번째 함수 호출`)
    }

    // 함수를 호출합니다.
    callThreeTimes(print)
</script>
```

`callThreeTimes()` 함수는 함수를 매개변수로 받아 해당 함수를 3번 호출합니다. 매개변수로 전달했던 `print()` 함수가 `print(0)`,`print(1)`,`print(2)`로 차례대로 호출되어 실행 결과와 같은 결과를 나타냅니다.

익명함수를 사용할때는 다음과 같습니다.

```
<script>
    // 함수를 선언합니다.
    function callThreeTimes (callback) {
        for (let i = 0; i < 3; i++){
            callback(i);
        }
    }

    callThreeTimes(function (i){
        console.log(`${i}번째 함수 호출`)
    })
</script>
```

#### 콜백 함수를 활용하는 함수 : forEach()
`forEach()`메소드는 배열이 갖고 있는 함수로써 단순하게 배열 내부의 요소를 사용하여 콜백 함수를 호출해줍니다.

```
// 배열의 forEach() 메소드
<script>
    const numbers = [273, 52, 103, 32, 57]

    numbers.forEach(function (value, index, array){
        console.log(`${index}번째 요소: ${value}`);
    })
</script>
```

#### 콜백 함수를 활요한 함수 : filter()
`filter()` 메소드도 배열이 갖고 있는 함수입니다. `filter()` 메소드는 콜백 함수에서 리턴하는 값이 `ture`인 것들만 모아서 새로운 배열을 만드는 함수입니다.

```
<script>
    const numbers = [273, 52, 103, 32, 57]
    const evenNumbers = numbers.filter(function(value) {
        return value % 2 === 0
    })

    console.log(`원래의 배열 : ${numbers}`)
    console.log(`짝수만 추출 : ${evenNumbers}`)
</script>
```

### 즉시 호출 함수