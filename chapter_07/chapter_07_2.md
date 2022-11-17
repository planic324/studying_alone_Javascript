# 07. 문서 객체 모델
## 07-2. 이벤트 활용

### 이벤트 모델

- 이벤트를 연결하는 방법을 `이벤트 모델`이라고 부릅니다.
- `addEventListener()`는 표준 이벤트 모델이다.
- `onOO`는 고전 이벤트 모델이다.
- HTML요소에 직접 넣어서 이벤트를 연결하는 것을 인라인 이벤트 모델이라 한다.

### 키보드 이벤트

- keydown : 키가 눌릴 때 실행
- keypress : 키가 입력 되었을 때 실행
- keyup : 키보드에서 키가 떨어질 때 실행

'keydown', 'keypress' 이벤터는 웹 브라우저에 따라서 아시아권의 문자를 제대로 처리하지 못하는 문제가 있어 'keyup' 이벤트를 사용

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            document.addEventListener('DOMCotnetLoaded', () => {
                const textarea = document.querySelector('textarea')
                const h1 = document.querySelector('h1')

                textarea.addEventListener('keyup', (event) => {
                    const length = textarea.value.length
                    h1.textContent = `글자 수: ${length}`
                })
            })    
        </script>
        
    </head>
    <body>
        <h1></h1>
        <textarea></textarea>
    </body>
</html>
```

#### 키보드 키 코드 사용하기
키보드 이벤트가 발생할 때는 이벤트 객체로 어떤 키를 눌렀는지와 곤련된 속성들이 따라옵니다.

- code : 입력한 키
- keyCode : 입력한 키를 나타내는 숫자
- altKey : `Alt`키를 눌렀는지
- ctrlKey : `Ctrl`키를 눌렀는지
- shiftKey : `Shift`키를 눌렀는지

### 이벤트 발생 객체
상황에 따라서는 이벤트 리스너 내부에서 그러한 변수에 접급할 수 없는 경우가 생긴다. 이럴경우 2가지 방법을 통해 외부의 변수에 접근한다.

- 1. event.currentTarget 속성을 사용한다.
이는 () =>{}와 function() {} 형태 모두 사용 가능
- 2. this 키워드를 사용
function() {} 형태에서만 사용 가능

### 글자 입력 양식 이벤트

입력 양식을 기반으로 inch를 cm단위로 변환하는 프로그램
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
                const input = document.querySelector('input')
                const button = document.querySelector('button')
                const p = document.querySelector('p')

                button.addEventListener('click', ()=> {
                    const inch = Number(input.value)

                    if(isNaN(inch)){
                        p.textContent = '숫자를 입력하세요'
                        return
                    }

                    const cm = inch * 2.54
                    p.textContent = `${cm}cm`
                })
            })
        </script>
        
    </head>
    <body>
        <input type="text"> inch<br>
        <button>계산</button>
        <p></p>
    </body>
</html>
```

#### 드롭다운 목록 활용하기
드롭다운 목록은 기본적으로 select 태그로 구현합니다. select 태그는 사용 방법이 조금 특이하다.

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
                const select = document.querySelector('select')
                const p = document.querySelector('p')

                select.addEventListener('change', (event) => {
                    const options = event.currentTarget.options
                    const index = event.currentTarget.options.selectedIndex

                    p.textContent = `선택: ${options[index].textContent}`
                })
            })
        </script>
        
    </head>
    <body>
        <select name="" id="">
            <option value="">떡볶이</option>
            <option value="">김밥</option>
            <option value="">튀김</option>
            <option value="">순대</option>
        </select>
        <p>선택: 떡볶이</p>
    </body>
</html>
```

코드를 실행하고 드롭다운 목록에서 항목을 선택하면 `options[index]`에서 선택한 `option` 태그가 출력이된다.

select 태그에 nultiple 속성을 부여하면 Ctrl 또는 Shift키를 누르고 여러 항목을 선택할 수 있다.

multiple select 손코딩 해보기
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
                const select = document.querySelector('select')
                const p = document.querySelector('p')

                select.addEventListener('change', (event) => {
                    const options = event.currentTarget.options
                    const list = []

                    for (const option of options){
                        if (option.selected){
                            list.push(option.textContent)
                        }
                    }

                    p.textContent = `선택: ${list.join(',')}`
                })
            })
        </script>
        
    </head>
    <body>
        <select multiple>
            <option value="">떡볶이</option>
            <option value="">김밥</option>
            <option value="">튀김</option>
            <option value="">순대</option>
        </select>
        <p>선택: 떡볶이</p>
    </body>
</html>
```

