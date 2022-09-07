# 04 반복문
## 04-1 배열
`배열`은 여러 자료를 묶어서 활용할 수 있는 특수한 자료입니다.

### 배열 만들기
`배열`은 여러 개의 변수를 한 번에 선언해 다룰 수 있는 자료형입니다.

```
> const array = [273, 'String', true, function(){}, {}, [273, 103]]
> undefined

> array
> (6) [273, 'String', true, function(){}, {}, [273, 103]]
```

### 배열 요소에 접근하기
각각의 요소에 접근하려면 배열 바로 뒤에 대괄호 `[...]`를 입력하고 그 안에 숫자를 넣습니다.
맨 처음 요소는 `(0)` 부터 시작됩니다.

### 배열 요소 개수 확인하기
배열 내부에 들어 있는 요소의 개수를 확인할 때는 배열의 `length` 속성을 사용합니다.

### 배열 뒷부분에 요소 추가하기
#### `push()` 메소드를 사용해 배열 뒷부분에 요소 추가하기
배열 뒷부분에 요소를 추가할 때는 `push()` 메소드를 사용합니다.

```
> const todos = ['우유 구매', '메일 확인', '운동']
> undefined

> todos
> (3) ['우유 구매', '메일 확인', '운동']

> todos.push('저녁 약속')
> 4

> todos.push('명상')
> 5

> todos
> (5) ['우유 구매', '메일 확인', '운동', '저녁 약속', '명상']
```

#### 인덱스를 사용해 배열 뒷부분에 요소 추가하기
자바스크립트의 배열의 길이는 고정이 아닙니다. 만약 배열이, 1~3번째까지 있는 경우 강제로 10번째 인덱스에 요소를 강제로 추가할 수 있습니다.

이때, 4~9번째까지의 인덱스는 empty가 됩니다.

인덱스로 요소를 추가하는 방법을 활용하면 아래와 같이 lengh 속성을 사용하여 배열의 마지막 위치에 요소를 추가할 수 있습니다.
```
> const fruitsB = ['사과', '배', '바나나']
> undefined

> fruitsB[fuitsB.length] = '귤'
> "귤"

> fruitsB
> (4) ["사과", "배", "바나나", "귤"]
```

### 배열 요소 제거하기
배열에 요소를 제거하는 방법은 2가지 입니다.

- 첫째, 인덱스를 기반으로 제거하는 경우
- 둘째, 값을 기반으로 제거하는 경우

#### 인덱스로 요소 제거하기
배열의 특정 인덱스에 있는 요소를 제거할 때는 `splice()` 메소드를 사용합니다.
`splice`는 `접합`의 의미로 다양하게 활용된다.

일부를 제거하는 경우에도 사용되지만, 중간에 다른 요소를 `접합` 즉, 중간에 요소를 추가할때에도 사용됩니다.

```
배열.splice(인덱스, 제거할 요소의 개수)
```

```
> const fruitsB = ['사과', '배', '바나나']
> undefined

> fruitsB.splice(2, 1) >> 인덱스 2번부터 1개를 제거한다. (인덱스 2 = 바나나)
> ["바나나"]

> fruitsB
> ["사과", "배"]
```

#### 값으로 요소 제거하기
값을 기반으로 요소를 제거할 때는 배열 내부에서 특정 값의 위치를 찾는 `indexof()` 메소드를 사용해서 값의 위치를 추출한 뒤 `splice()` 메소드를 사용해 제거한다.

```
const 인덱스 = 배열.indexOf(요소)
배열.splice(인덱스, 1)
```

`indexOf()`메소드는 배열 내부에 요소가 있는 경우에 인덱스를 리턴합니다.
만약, 배열 내부에 요소가 없는 경우 `-1`을 리턴합니다.

```
> const items = ['사과', '배', '바나나']
> undefined

> const index = items.indexOf('바나나')
> undefined

> index
> ["바나나"]

> items
> (2) ["사과", "배"]

> items.indexOf('바나나')
> -1
```

### 배열의 특정 위치에 요소 추가하기
배열의 특정위치에 요소를 추가하는 코드는 자주 사용하지 않지만, 간혹 사용되지 알아보자.

`splice()`메소드를 사용합니다. `splice()` 메소드의 2번째 매개변수에 0을 입력하면, `splice()` 메소드는 아무 것도 제거하지 않으며, 3번째 매개변수에 추가하고 싶은 요소를 입력합니다.

```
배열.splice(인덱스, 0, 요소)
```