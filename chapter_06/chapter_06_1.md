# 06-1 객체의 기본
> 객체 : 실제로 존재하는 사물
> '이름과 값으로 구성'된 속성(Property)을 가진 자바스크립트의 기본 데이터 타입이다.

## 객체
 - 자바스크립트에서 여러 자료를 다룰 때는 객체를 사용.
 - '배열'도 여러 자료를 다룰 수 있다. (배열 = 객체)
 - 배열을 typeof로 실행 시 object라는 문자열로 출력
 - 'object' = 객체

### 객체의 선언
```
<script>
    const product  = {
        제품명 : '7D 건조 망고',
        유형 : '당절임',
        성분 : '망고, 설탕, 메타중아황상나트륨, 치자황색서',
        원산지 : '필리핀'
    }
</script>
```

객체에 접근하는 방법
```
// 방법 1)
product['제품명'] // '7D 건조망고'
// 방법 2)
product.제품명 // '7D 건조망고'
```

'온점'을 사용하면 보조 기능을 활용할 수 있어 더 많이 사용합니다.

## 속성과 메소드
 - 배열 내부에 있는 값을 '요소'라고 한다.
 - 객체 내부에 있는 값은 '속성'이라고 한다.
 - 배열의 요소와 마찬가지로 객체의 속성에도 모든 형태의 자료형을 가질 수 있다.
 
### 속성과 메소드 구분하기
객체의 속성 중 함수 자료형인 속성을 특별히 `메소드`라고 부른다.
다음 코드에서 객체 person은 name 속성과 eat속성을 가지고 있는데, eat 속성처럼 입력값을 받아 무언가 한 다음 결과를 도출해내는 함수 자료형을 특별히 eat() 메소드라고 부릅니다.
  
```
<script>
    const pet = {
        name: '구름',
        eat: function(food){ }
    }

    // 메소드 호출
    pet.eat()
</script>
```

#### 메소드 내부에서 this 키워드 사용하기
- 자기 자신이 가진 속성이라는 것을 표시할 때 `this`키워드를 사용한다.

```
<script>
    // 변수를 지정한다.
    const pet = {
        name: '구름',
        eat: function(food){
            alert(this.name + '은/는' + food + '을/를 먹습니다.')
        }        
    }
    pet.eat('밥')
</script>
```

### 동적으로 객체 속성 추가/제거
객체를 처음 생성한 후에 속성을 추가하거나 제거하는 것을 '동적으로 속성을 추가한다' 또는 '동적으로 속성을 제거한다'라고 표현

#### 동적으로 객체 속성 추가하기
```
<script>
    // 객체를 선언합니다.
    const student = {}
    student.이름 = '노은찬',
    student.악기 = '피아노',
    student.장래희망 = '대통령'

    console.log(JSON.stringify(student, null, 2))
</script>
```

#### 동적으로 객체 속성 제거하기
객체의 속성을 제거할 때는 `delete` 키워드를 사용
```
<script>
    // 객체를 선언합니다.
    const student = {}
    student.이름 = '노은찬',
    student.악기 = '피아노',
    student.장래희망 = '대통령'

    delete student.장래희망

    console.log(JSON.stringify(student, null, 2))
</script>
```

 
