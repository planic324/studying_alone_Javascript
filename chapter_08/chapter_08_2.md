# 08. 예외 처리
## 08-2. 예외 처리 고급
- 예외 객체 : 프로그래밍 언어에서도 예외가 발생하면 예외아 발생된 정보를 확인할 수 있게 해주는 것

자바스크립트는 유연한 언어이므로 예외가 잘 발생하지 않는다. 그렇기 때문에 강제로 예외를 발생 시킬 때 `throw` 키워드를 사용한다.

### 예외 강제 발생
상황에 따라서 예외를 강제로 발생시켜야 하는 경우가 있다. 이럴때 `throw` 키워드를 사용한다.

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            function divide(a, b){
                if (b===0) {
                    throw '0으로 나눌 수 없습니다.'
                }
                return a/b
            }
            console.log(divide(10,2))
            console.log(divide(10,0))
        </script>
    </head>
    <body>
        
    </body>
</html>
```