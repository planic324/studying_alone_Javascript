# 07. 문서 객체 모델
## 07-1. 문서 객체 조작하기

- HTML = 요소
- Javascript = 문서 객체 (Document Object)

### DOMContentLoaded 이벤트

문서 객체를 조작할 때는 DOMContentLoaded 이벤트를 사용합니다.
`<body>` 태그가 생성되기 이전에 `<head>` 태그에서 `<body>`태그에 무언가 출력하려고 하면 아래와 같은 문제가 발생한다.

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            // HTML 태그를 쉽게 만들 수 있는 콜백 함수를 선언합니다.
            const h1 = (text) => `<h1>$(text)<h1>`
        </script>
        <script>
            document.body.innerHTML += h1('1번째 script 태그')
        </script>
    </head>
    <body>
        <script>
            document.body.innerHTML += h1('2번째 script 태그')
        </script>
        <h1>1번째 h1태그</h1>
        <script>
            document.body.innerHTML += h1('3번째 script 태그')
        </script>
        <h1>2번째 h1태그</h1>
    </body>
</html>
```

기본적으로 `<head>` 태그 내부에 script 태그를 배치하면 `<body>` 태그에 있는 문서 객체(요소)에 접근할 수 없습니다.
  
DOMContentLoaded 이벤트는 웹 브라우저가 문서 객체를 모두 읽고 나서 실행하는 이벤트 입니다.
  
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            document.addEventListener('DOMContentLoaded', () =>{
                const h1 = (text) => `<h1>${text}<h1>`
                    document.body.innerHTML += h1(`DOMcontentLoaded 이벤트 발생`)
            })
        </script>
    </head>
    <body>
        
    </body>
</html>
```

### 문서 객체 가져오기

선택자에 접근하는 메소드는 다음과 같다.

```
document.querySelector(선택자)
document.querySelectorAll(선택자)
```

### 글자 조작하기
예제들을 통해 innerHTML 속성과 textContent 속성을 사용하여 문서 객체 내부의 글자를 조작하였습니다.

- 문서객체.textContent : 입력된 문자열을 그대로 넣습니다.
- 문서객체.innerHTML : 입력된 문자열을 HTML 형식으로 넣습니다.

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            document.addEventListener('DOMContentLoaded', () => {
                const a = document.querySelector('#a')
                const b = document.querySelector('#b')

                a.textContent = '<h1>textContent 속성</h1>'
                b.innerHTML = '<h1>innerHTML 속성</h1>'
            })
        </script>
    </head>
    <body>
        <div id="a"></div>
        <div id="b"></div>
        
    </body>
</html>
```

### 속성 조작하기

- 문서객체.setAttribute(속성 이름, 값) : 특성 속성에 값을 지정합니다.
- 문서객체.getAttribute(속성 이름) : 특정 속성을 추출합니다.

getAttribute() 메소드를 사용하지 않고도 '온점(.)'을 찍고 속성을 바로 읽어들이거나 지정할 수 있다.

### 스타일 조작하기

객체는 다음과 같은 방법으로 스타일을 조정할 수 있습니다.

```
h1.style.backgroundColor
h1.style['backgroundColor]
h1.style['background-color']
```

### 문서 객체 생성하기
문서 객체를 생성하기 위해서는 document.createElement() 메소드를 사용한다.

```
document.createElement(문서 객체 이름)
```

문서를 어떤 문서에 아래에 추가 할지를 지정 해줘야 한다. 이러한 그림을 프로그래밍에선 `트리`라고 부른다. 어떤 문서 객체가 있을때 위의 있는 것을 `부모`라고 하고 아래에 있는 것을 `자식`이라고 부릅니다.

문서 객체에는 `appendChild()` 메소드가 있으며, 이를 활용하면 어떤 부모 객체 아래에 자식 객체를 추가할 수 있습니다.

```
부모객체.appendChild(자식객체)
```

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            document.addEventListener('DOMContentLoaded', () => {
                const header = document.createElement('h1')

                header.textContent = '문서 객체 동적으로 생성하기'
                header.setAttribute('data-custom', '사용자 정의 속성')
                header.style.color = 'white'
                header.style.backgroundColor = 'black'

                document.body.appendChild(header)
            })
        </script>
    </head>
    <body>
        
    </body>
</html>
```

### 문서 객체 이동하기
`appendChild()` 메소드는 문서 객체를 이동할 때도 사용할 수 있습니다. 문서 객체의 부모는 언제나 하나여야 합니다. 따라서 문서 객체를 다른 문서 객체에 추가하면 문서 객체가 이동합니다.

### 문서 객체 제거하기
문서 객체를 제거할 때는 `removeChild()` 메소드를 사용한다.

```
부모객체.removeChild(자식객체)
```

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            document.addEventListener('DOMContentLoaded', () => {
                setTimeout(() => {
                    const h1 = document.querySelector('h1')

                    h1.parentNode.removeChild(h1)
                    // document.body.removeChild(h1)
                }, 3000)
            })
        </script>
    </head>
    <body>
        <hr>
        <h1>제거 대상 문서 객체</h1>
        <hr>
    </body>
</html>
```

### 이벤트 설정하기

```
document.addEventListener('DOMContentLoaded', () =>{})
```
위의 형태는 'document라는 문서 객체의 DOMContentLoaded 이벤트가 발생했을 때, 매게변수로 지정한 콜백 함수를 실행하라' 라는 의미이다.

이벤트를 발생하기 위해서는
```
문서객체.addEventListener(이벤트 이름, 콜백 함수)
```