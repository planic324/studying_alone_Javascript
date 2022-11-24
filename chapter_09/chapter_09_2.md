# 09. 클래스
## 09-2. 클래스의 고급 기능
### 상속
클래스를 분리하는 것이 클래스 활용하는 쪽에서는 편리하겠지만, 분리하면 클래스 선언 부분이 복잡해지는 문제가 발생합니다. 이러한 문제를 해결하기 위해 상속이라느 개념을 사용합니다.

- 상속의 기본적인 형태
```
class 클래스이름 extends 부모클래스 이름 {

}
```

상속은 어떤 클래스가 가지고 있는 속성과 메소드를 다른 클래스에게 공유 하는 형태로 사용합니다.

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            class Ractangle {
                constructor (width, height){
                    this.width = width
                    this.height = height
                }

                // 둘레를 구하는 메소드
                getPerimeter () {
                    return 2 * (this.width + this.height)
                }

                // 넓이를 구하는 메소드
                getArea () {
                    return this.width * this.height
                }
            }

            // 정사각형 클래스
            class Sqare extends Ractangle {
                constructor (length){
                    super(length, length)
                }
            }

            // 클래스 사용하기
            const sqare = new Sqare(10, 20)
            console.log(`둘레 ${sqare.getPerimeter()}`)
            console.log(`넓이 ${sqare.getArea()}`)
        </script>
    </head>
    <body>
        
    </body>
</html>
```

`Sqare` 클래스에는 `getPerimeter()`와 `getArea()`를 선언하지 않았습니다. 하지만, 상속기능을 이용하여 `Rectangle` 클래스에서 선언한 것을 가지고 와서 사용하였습니다.

여기서 주목해야될 것은 상속 시 속성을 선언하는 방법입니다.

```
super(legnth, length)
```

`super()` 함수는 부모의 생성자를 나타내는 함수입니다. 따라서 이경우 `whidt`와 `height`가 됩니다.

### private 속성과 메소드

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            class Ractangle {
                constructor (width, height){
                    this.width = width
                    this.height = height
                }

                // 둘레를 구하는 메소드
                getPerimeter () {
                    return 2 * (this.width + this.height)
                }

                // 넓이를 구하는 메소드
                getArea () {
                    return this.width * this.height
                }
            }

            // 정사각형 클래스
            class Sqare extends Ractangle {
                constructor (length){
                    super(length, length)
                }
            }

            // 클래스 사용하기
            const sqare = new Sqare(-10)
            console.log(`둘레 ${sqare.getPerimeter()}`)
            console.log(`넓이 ${sqare.getArea()}`)
        </script>
    </head>
    <body>
        
    </body>
</html>
```

위의 코드에서는 -10 '음수' 이므로 길이가 음수가 나올 수 없으므로 코드상 오류는 일어나지 않지만, 원하는 값이 제대로 나오지는 않습니다.

이러한 경우 예외처리를 해야되는데 다음과 같은 방법으로 예외처리를 한다.

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            class Ractangle {
                constructor (width, height){
                    this.width = width
                    this.height = height
                }

                // 둘레를 구하는 메소드
                getPerimeter () {
                    return 2 * (this.width + this.height)
                }

                // 넓이를 구하는 메소드
                getArea () {
                    return this.width * this.height
                }
            }

            // 정사각형 클래스
            class Sqare extends Ractangle {
                constructor (length){
                    if(length <= 0){
                        throw '길이는 0보다 커야됩니다.'
                    }
                    this.length = length
                }
            }

            // 클래스 사용하기
            const sqare = new Sqare(-10)
            console.log(`둘레 ${sqare.getPerimeter()}`)
            console.log(`넓이 ${sqare.getArea()}`)
        </script>
    </head>
    <body>
        
    </body>
</html>
```

이렇게 if 문을 이용하여 예외처리를 할 수 잇지만,
정말 다양한 사용자가 있어 아래와 같이 사용하는 경우가 있습니다.

```
// 클래스 사용하기
const sqare = new Sqare(-10)
sqare = -10
console.log(`둘레 ${sqare.getPerimeter()}`)
console.log(`넓이 ${sqare.getArea()}`)
```

이와 같이 사용하면 막을 수가 위의 예외처리로는 막을 수 없습니다.
이러한 경우가 존재하기 때문에 `previate`를 사용합니다.

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            class Ractangle {
                constructor (width, height){
                    this.width = width
                    this.height = height
                }

                // 둘레를 구하는 메소드
                getPerimeter () {
                    return 2 * (this.width + this.height)
                }

                // 넓이를 구하는 메소드
                getArea () {
                    return this.width * this.height
                }
            }

            // 정사각형 클래스
            class Sqare extends Ractangle {
                #length // 이 위치에 해당 속성을 prviate 속성으로 사용하겠다고 미리 선언합니다.
            
                constructor (length){
                    if(length <= 0){
                        throw '길이는 0보다 커야됩니다.'
                    }
                    this.length = length
                }
            }

            // 클래스 사용하기
            const sqare = new Sqare(-10)
            sqare#length = -10
            console.log(`둘레 ${sqare.getPerimeter()}`)
            console.log(`넓이 ${sqare.getArea()}`)
        </script>
    </head>
    <body>
        
    </body>
</html>
```

### get/set
prviate 속성을 사용하면 외부에서는 #length 속성에 아예 접근을 할 수 없는 문제가 발생한다.
이러한 문제를 해결하기 위해서 get/set을 메소드를 만들었다.

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            // 정사각형 만들기
            class Sqare {
                #length

                constructor (length){
                    this.setLength (length)
                }

                setLength (value){
                    if(value <= 0){
                        throw '길이는 0보다 큰 숫자여야 됩니다.'
                    }
                    this.#length = value
                }

                getLength (value){
                    return this.#length
                }

                getPerimeter () {return 4 * this.#length}
                getArea () {return this.#length * this.#length}
            }

            // 클래스 사용하기
            const sqare = new Sqare(10)
            console.log(`둘레 ${sqare.getPerimeter()}`)
            console.log(`넓이 ${sqare.getArea()}`)

            sqare.setLength(-10)
        </script>
    </head>
    <body>
        
    </body>
</html>
```

- get() : 속성 값을 확인할 때 사용하는 메소드를 게터라고 한다
- set() : 속성 값을 지정할 때 사용하는 것을 세터라고 한다

처음 게터와 세터를 배우면 모든 private 속성에 게터와 세터르르 붙이려고 하는 경우가 있다.
하지만, 필요한 경우만 사용하면 된다.

아래의 코드는 get키워드와 set 키워드 조합을 한 코드이다.
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            // 정사각형 만들기
            class Square {
                #length

                constructor (length){
                    this.setLength = length
                }

                get length() {
                    return this.#length
                }
                
                get getPerimeter() {
                    return this.#length *4
                }

                get area() {
                    return this.#length * this.#length
                }

                set length (length){
                    if (length <= 0) {
                        throw '0 이상 숫자를 입력하세요'
                    } 
                    this.#length = length
                }
            }

            // 클래스 사용하기
            const SquareA = new Square(10)
            console.log(`한변길이 ${SquareA.length}`)
            console.log(`둘레 ${SquareA.getPerimeter}`)

            // const sqareB = new Sqare(-10)
        </script>
    </head>
    <body>
        
    </body>
</html>
```