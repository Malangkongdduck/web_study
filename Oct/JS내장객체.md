# JS 내장 객체

| Object 객체 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| String 객체 | length | indexOf() | indexOf() | slice() | substring() | substr() | replace() | toUpperCase(), toLowerCase() | concat() | trim() | padStart(), 
padEnd() | charAt() | charCodeAt() | split() | startsWith(),
endsWith() |
| Nuber 객체 | toSrting() | toExponential() | toFixed() | toPercision() | parseInt() | parseFloat() | 프로퍼티 |  |  |  |  |  |  |  |  |
| Array 객체 | toString() | join() | pop() | push() | shift() | unshift() | 배열 요소 변경 | splice() | concat() | slice() | sort() | filter() | map() | reduce() |  |
| Date 객체 | Date 생성자 | Get 함수 | Set 함수 |  |  |  |  |  |  |  |  |  |  |  |  |
| Set 객체 | Set 생성자 | add() | has() | delete() | clear() | forEach() |  |  |  |  |  |  |  |  |  |
| Map 객체 | Map 생성자 | set() | get() | has() | delete() | clear() | forEach() |  |  |  |  |  |  |  |  |
| Math 객체 | Math.round() | Math.ceil() | Math.floor() | Math.trunc() | Math.sign() | Math.pow() | Math.sqrt() | Math.abs() | Math.min(),
Math.max() | Math.random() |  |  |  |  |  |
| JSON 객체 | JSON.stringfy | JSON.parse |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Window 객체 | alert() | confirm() | prompt() | window.open() | setTimeout(),
clearTimeout() | setInterval(),
clearInterval() |  |  |  |  |  |  |  |  |  |
| Symbol |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |

---

---

# 자바스크립트 내장 객체

- 내장 객체 : 브라우저의 자바스크립트 엔진에 내장된 객체

## Object 객체

Object 객체는 모든 자바스크립트 객체의 루트 객체

```jsx
// 빈 객체 생성
let person = new Object();

// 멤버 설정
person.firstName = "Jinny";
person.lastName = "Lee";
person.age = 23;
person.getFullName = function () {
  return `${this.firstName} ${this.lastName}`;
};

console.log(person.getFullName());
```

---

## String 객체

자바스크립트에서 문자열을 다루기 위한 객첵로 문자열을 다룰 때 유용한 프로퍼티와 함수를 제공

### length

문자열의 길이를 반환하는 함수

```jsx
let txt = 'ABCDEFGHIGKLNMOPQRSTUVWXYZ';
let sln = txt.length;
```

- 실무 사례
    - 회원가입 시 비밀번호 생성 규칙을 두는 경우 - lengh 함수를 통해 길이를 알 수 있음
    - 주민번호 앞자리 6자리가 제대로 입력되었는지 알 수 있음

### indexOf()

문자열 안에 특정 문자열이 존재하는지 찾고, 있다면 문자열이 시작되는 인덱스를 없다면 -1을 반환

```jsx
let str = "Please locate where 'locate' occurs!";
let pos = str.indexOf('locate');    //7
```

- 실무 사례
전화 번호 입력 시 -이 있는지 검사

### lastIndexOf()

찾고자하는 문자열이 둘 이상 발견되면 제일 마지막에 발견된 문자열의 index를 반환

```jsx
let str = "Please locate where 'locate' occurs!";
let pos = str.indexOf('locate');    //21
```

 

두 번째 파라미터에는 문자열을 찾기 시작할 위치의 인덱스를 줄 수 있음

```jsx
let str = "Please locate where 'locate' occurs!";
let pos = str.indexOf('locate', 15);    //21
```

### slice()

파라미터로 시작 위치와 종료 위치를 주면 문자열에서 해당 부분은 잘라내서 반환

두 번째 파라미터(종료 인덱스 번호)를 생략하면 마지막 위치까지 자름

첫 번째 파라미터(시작 인덱스)를 음수로 주면 문자열의 끝에서부터 거꾸로 읽음

```jsx
let str = 'apple, banana, kiwi';
let res = str.slice(7, 13); //banana

res = str.slice(7); //banana, kiwi

res str.slice(-12); //banana, kiwi
```

- substring() - slice() 함수와 동일하나 파라미터로 음수를 허용하지 않음
- substr() - slice() 함수와 유사하나 두 번째 파라미터는 시작 위치에서 잘라낼 문자의 길이 (음수 허용)

### replace()

문자열 내의 특정 문자열을 지정한 문자열로 바꿈 (대소문자 구분 - js 정규식을 사용해 구분X)

→ 바꾸려는 문자열이 하나 이상 있더라도 처음 발견된 문자열만 바꿈 (js 정규식을 사용해 해결 가능)

```jsx
let str = 'Please visit Seoul and Seoul!';
let n = str.replace('Seoul', 'Jeju');
// Please visit Jeju and Seoul!

let n2 = str.replace(/seoul/i, 'Jeju');
// Please visit Jeju and Seoul!

let n3 = str.replace(/Seoul/g, 'Jeju');
// Please visit Jeju and Jeju!
```

### toUpperCase(), toLowerCase()

- **toUpperCase()** - 문자열을 모두 대문자로 변경
    
    ```jsx
    let text1 = 'Hello World!';
    let text2 = text1.toUpperCase();
    // HELLO WORLD!
    ```
    

- **toLowerCase()** - 문자열을 모두 소문자로 변경
    
    ```jsx
    let text1 = 'Hello World!';
    let text2 = text1.toLowerCase();
    // hello world!
    ```
    

- 실무 사례
    - 여권, 항공권, 신용카드에서는 모두 대문자로 이름을 관리 - 사용자가 이름을 입력하면 모두 대문자로 변경해 서버로 데이터를 전송
    - 검색 키워드를 대소문자 구분 없이 검색할 때

### concat()

2개 이상의 문자열을 하나의 문자열로 합치는 함수

```jsx
let text1 = 'Hello';
let text2 = 'World';
let text3 = text1.concat(' ', text2);
let text4 = 'Hello' + ' ' + 'World!
let text5 = 'Hello'.concat(' ', 'World');
```

```jsx
let txt1 = 'Jinyi';
let txt2 = 'Lee';

let fullName = txt2.concat(txt1);

console.log(fullName);
```

- 실무 사례
    
    ```jsx
    firstName.concat(' ', middleName, ' ', lastName);
    ```
    

### trim()

문자열의 앞, 뒤 공백을 모두 제거하는 함수

```jsx
let str = '    Hello World!';
console.log(str.trim());
// Hello World!
```

### padStart(), padEnd()

- **padSrtart()** : 문자열 앞에 지정된 문자를 지정된 길이만큼 추가하는 함수
    
    (문자열의 총 길이, 추가할 문자)
    
- **padEnd()** : 문자열 뒤에 지정된 문자를 지정된 길이만큼 추가하는 함수
    
    (문자열의 총 길이, 추가할 문자)
    

```jsx
let str = '5';
str = str.padStart(4,0);
// 0005
```

- 실무 사례
    - 순번 체계에서 자릿 수 0으로 채울 때
    - 년(4자리)-월(2자리)-일(2자리) 형식으로 날짜를 구하는 프로그램을 구현할 때 (Date는 10 이전에는 한자리로 값을 가져옴)
    

### charAt()

문자열에서 특정 인덱스에 해당하는 문자 하나를 반환

```jsx
let str = 'Hello World!'
str.charAt(0);
//H
```

- **charCodeAt()**
    
     문자열에서 특정 인덱스에 해당하는 문자 하나의 유니코드 값을 반환
    

### split()

문자열 내의 특정 구분자를 기준으로 문자열을 분리해서 배열로 반환

```jsx
let birthday = '1999-05-29';
let arr = birsthday.split('-');    / -을 기준으로 문자열을 분리해 배열로 반환

console.log(arr);
// ['1999', '05', '29']
```

### startsWith(), endsWith()

- **startsWith()** : 문자열의 시작이 파라미터로 전달된 문자열로 시작되는지를 확인

```jsx
let url = 'https://2jin2.tistory.com/';

if(url.startsWith('https://') || url.startsWith('http://')) {
	console.log('올바른 형식의 url');
} else {
	console.log('잘못된 형식의 url');
}
```

- **endsWith()** : 문자열의 시작이 파라미터로 전달된 문자열로 시작되는지를 확인

```jsx
let file = 'image.jpg';

if(file.endsWith('.jpg') || url.endsWith('.jpg')) {
	console.log('jpg 파일');
} else {
	console.log('jpg 파일');
}
```

---

## Number 객체

숫자를 다룰 때 유용한 프로퍼디와 함수를 제공하는 래퍼(wrapper) 객체

JS에서는 정수와 실수를 따로 구분하지 않고 모든 수를 실수 하나로 표현

- 래퍼 객체 : 원시 타입의 값을 감싸는 형태의 객체

### toString()

숫자형 데이터를 문자형 데이터로 반환

→ Number 객체보다 String 객체가 더 다양한 내장 함수를 갖고 있음

```jsx
let x = 123;
x.toString();
(123).toString();
```

- 실무 사례
    
    Date 객체의 getMonth() 함수를 호출하면 월에 해당하는 값을 숫자로 반환
    
    1월 → 0
    
    ```jsx
    let now = new Date();
    let year = now.getFullYear();  // 현재 년도
    let month = new.getMonth() + 1;
    let day = now.getDate();  // 현재 일
    
    console.log(year + '-' + month.toSring().padStart(2,0) + '-' + day.toString().padStart(2.0));
    // 오늘이 2022년10월6일 인 경우 2022-10-06 출력
    ```
    

### toExponential()

숫자를 지수형ㅇ로 반환해주는 함수

```jsx
let x = 10.656;
x.toExponential(2);    // 10.66e+0
x.toExponential(4);    // 10.656e+0
x.toExponential(6);    // 10.656000e+0
```

### toFixed()

소수점 몇 번째 자리까지 보여줄지를 결정하는 함수

파라미터로 소수점 자릿수를 사용

지정되니 소수점 자릿수에 대한 반올림 값을 반환

```jsx
let x = 10.656;
x.toFixed(0);   // 11
x.toFixed(2);   // 10.66
x.toFixed(4);   // 10.6560
```

---

## Array 객체

### map()

배열의 데이터가 Object형일 때, 배열에 담긴 Object를 새로운 형태의 Object로 변환해서 배열로 반환

