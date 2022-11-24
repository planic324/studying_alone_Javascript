# 09. 클래스
## 09-1. 클래스의 기본 기능
C 언어를 제외한 프로그래밍 언어는 `객체 지향`이라는 패러다임을 기반으로 만들어진 프로그래밍 언어입니다.
`객체 지향 페러다임`이란 객체를 우선적으로 생각해서 프로그램을 만든다는 방법론 입니다.

객체 지향 프로그래밍 언어들은 `클래스`라는 문법으로 `객체`를 효율적이고 안전하게 만들어 객체 지향 패러다임을 쉽게 프로그래밍에 적용할 수 있도록 도와준다.

### 추상화
프로그램에 필요한 요소만 사용해서 객체를 표현 하는 것을 `추상화`라고 한다.

### 같은 형태의 객체 만들기
학생 성적 관리 프로그램을 만들때 추상화를 적용해 보자

#### 객체를 처리하는 함수 만들기(성적표 만들기)
1. 객체를 이용하지 않는 경우.

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            const students = []
            students.push({이름: '구름', 국어: 88, 영어: 83, 수학: 100, 과학: 12})
            students.push({이름: '별이', 국어: 82, 영어: 83, 수학: 10, 과학: 65})
            students.push({이름: '겨울', 국어: 84, 영어: 82, 수학: 40, 과학: 61})
            students.push({이름: '바다', 국어: 81, 영어: 23, 수학: 54, 과학: 62})
            students.push({이름: '하늘', 국어: 83, 영어: 63, 수학: 66, 과학: 65})

            let outPut = '이름\t총점\t평균\n'
            for (const s of students){
                const sum = s.국어 + s.영어 + s.수학 + s.과학
                const average = sum/4
                outPut += `${(s.이름)}\t${sum}점\t${average}점\n`
            }
            console.log(outPut)
        </script>
    </head>
    <body>
        
    </body>
</html>
```

2. 객체를 이용하는 경우
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            const students = []
            students.push({이름: '구름', 국어: 88, 영어: 83, 수학: 100, 과학: 12})
            students.push({이름: '별이', 국어: 82, 영어: 83, 수학: 10, 과학: 65})
            students.push({이름: '겨울', 국어: 84, 영어: 82, 수학: 40, 과학: 61})
            students.push({이름: '바다', 국어: 81, 영어: 23, 수학: 54, 과학: 62})
            students.push({이름: '하늘', 국어: 83, 영어: 63, 수학: 66, 과학: 65})

            // 객체를 처리하는 함수를 선언합니다.
            function getSumOf(student){
                return student.국어 + student.영어 + student.수학 + student.과학
            }

            function getAverageOf(student){
                return getSumOf(student)/4
            }

            // 출력
            let outPut = '이름\t총점\t평균\n'
            for (const s of students){
                outPut += `${(s.이름)}\t${getSumOf(s)}점\t${getAverageOf(s)}점\n`
            }
            console.log(outPut)
        </script>
    </head>
    <body>
        
    </body>
</html>
```

1번 보다 2번의 경우 전체적인 코드의 줄이 길어지는 것을 느낄수 있다.
하지만, 2번의 경우 function 함수(객체)로 만들어 코드를 수정하는데 유리한 것을 확인 할 수 있다.
이러한 것을 코드에 확장성이 좋다고 표현을 한다.

### 객체의 기능을 메소드로 추가하기
객체의 수가 늘어나면 함수 이름 충돌이 발생할 수 있다. 또한 매개변수에 어떤 종류의 객체를 넣을지 몰라 함수를 사용하는데 혼동이 있을 수 있다. 그래서 개발자들은 함수를 메소드로써 객체 내부에 넣어 활용하는 방법을 사용하기 시작하였다.

아래의 코드를 확인해보자.
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            const students = []
            students.push({이름: '구름', 국어: 88, 영어: 83, 수학: 100, 과학: 12})
            students.push({이름: '별이', 국어: 82, 영어: 83, 수학: 10, 과학: 65})
            students.push({이름: '겨울', 국어: 84, 영어: 82, 수학: 40, 과학: 61})
            students.push({이름: '바다', 국어: 81, 영어: 23, 수학: 54, 과학: 62})
            students.push({이름: '하늘', 국어: 83, 영어: 63, 수학: 66, 과학: 65})

            // 객체를 처리하는 함수를 선언합니다.
            for(const student of students){
                student.getSum = function(){
                return this.국어 + this.영어 + this.수학 + this.과학
            }

                student.getAverage = function(){
                    return this.getSum() / 4
                }
            }
            

            // 출력
            let outPut = '이름\t총점\t평균\n'
            for (const s of students){
                outPut += `${(s.이름)}\t${s.getSum()}점\t${s.getAverage()}점\n`
            }
            console.log(outPut)
        </script>
    </head>
    <body>
        
    </body>
</html>
```
이렇게 코드를 작성핳면 함수 이름 충돌도 발생하지 않고, 함수를 잘못 사용하는 경우도 줄일  수 있다.

위의 코드의 경우에는 개체의 키와 값을 하나하나 모두 입력하여 생성을 하였다. 다음으로는 함수를 사용해서 객체를 찍어내는 방법을 해보자.

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            function creatStudent(이름, 국어, 영어, 수학, 과학) {
                return{
                    이름: 이름,
                    국어: 국어,
                    영어: 영어,
                    수학: 수학,
                    과학: 과학,
                    
                    // 메소드 선택
                    getSum() {
                        return this.국어 + this.영어 + this.수학 + this.과학
                    },
                    getAverage(){
                        return this.getSum() / 4
                    },
                    toString(){
                        return `${this.이름}\t${this.getSum()}점\t${this.getAverage()}점\n`
                    }
                }
                
            }
            // 객체선언
            const students = []
            students.push(creatStudent('구름', 88, 83, 100, 12))
            students.push(creatStudent('하늘', 88, 83, 100, 12))
            students.push(creatStudent('별', 88, 83, 100, 12))
            students.push(creatStudent('바다', 88, 83, 100, 12))
            students.push(creatStudent('태양', 88, 83, 100, 12))

            // 출력
            let outPut = '이름\t총점\t평균\n'
            for (const s of students){
                outPut += s.toString()
            }
            console.log(outPut)
        </script>
    </head>
    <body>
        
    </body>
</html>
```

이와 같이 코딩을 하는 경우 여러가지 이득을 취할수 있다.
1. 오탈자의 위험이 줄어듭니다.
2. 코드를 입력하는 양이 크게 줄어듭니다.
3. 속성과 메소드를 한 함수 내부에서 관리할 수있으므로 객체를 더 손쉽게 유지보수 할 수 잇습니다.

### 클래스 선언하기
#### 클래스와 프로토타입
클래스 : 객체를 만들 때 수많은 지원을 하는 대신 많은 제한을 거는 문법
프로토타입 : 제한을 많이 하지 않지만, 대신 지원도 별도 하지 않는 문법

클래스를 기반으로 만든 객체는 전문 용어로 `인스턴스`라고 부릅니다.

```
new 클래스이름()
```

클래스를 붕어빵의 전체적인 틀이라고 한다면, 인스턴스는 붕어빵을 하나 만들기 위한 틀이라고 보면 쉽다.

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <script>
            class Student{

            }
            // 학생을 선언한다.
            const student = new Student()

            // 학생 리스트를 선언한다.
            const students = [
                new students(),
                new students(),
                new students(),
                new students(),
                new students(),
                new students()
            ]
        </script>
    </head>
    <body>
        
    </body>
</html>
```

`클래스 이륾`은 첫 글자를 대문자로 지정하는 것이 개발자들의 약속이다.