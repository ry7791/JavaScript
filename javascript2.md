## 

- 함수

  - var 함수 = function() {};

    ```javascript
    let func= function(a){
                let output = prompt(a+"님 숫자를 입력해 주세요.");
                alert(output);
    
            }
    ```

  - function 함수() {};

    ```javascript
    function func2(name){
                return "hello"+name;
    
            }
    ```

    



- 배열

  - 고정배열

  ```javascript
  let myArray1 = ["apple", "banana"];
  
  ```

  - 가변배열

  ```javascript
    let maArray2 = new Array();
  ```



- 타이머 함수

  - 1초마다 실행

  ```javascript
  setInterval( function al(){
               console.log(Math.random());
              },1000);
   // 종료는 clearInterval(id)
  ```

  

  - 1초 후에 한번 실행

    ```javascript
    setTimeout( function al(){
                    console.log(Math.random());
                },1000);
    // 종료는 clearTimeout(id)
    ```



- 코드 실행 함수 

  - eval(string) : string을 자바스크립트 코드로 실행

  ```javascript
        let willEval = "";
              willEval += "var number=10;";
              willEval += "console.log(number);";
  
              eval(willEval);
  ```

  

- 숫자 변환 함수

  ```javascript
  let a = parseInt("123");
  let b = parseFloat("3.14");
  console.log(typeof a); // => number
  console.log(typeof b); // => number
  // Number()는 경우에따라 NaN이 뜸 parse 쓰자
  
  let won = "1000원";
  let dollar = "1.5$";
  console.log(parseInt(won) + "/" + parseFloat(dollar)); // => 1000/1.5
  
  console.log(Number(won) + "/" + Number(dollar)); // => NaN/NaN
  ```

  

- 화살표 함수

```javascript
let func1 = function(){ console.log("hello");  }
let func2 = () => { console.log("hello");  }     // 둘이 같은 표현
```



- arguments를 이용한 제곱 , 곱셈

```javascript
            function power(){
                if(arguments.length ==1){
                    console.log(arguments[0]*arguments[0]);
                }
                else if(arguments.length ==2){
                    console.log(arguments[0]**arguments[1]);
                }
            }
            function multiply(){
                let result =1;
                for (let i=0; i<arguments.length; i++){
                    result =result * arguments[i];
                }
                console.log(result);
            }
            power(3);
            power(3,4); 
            multiply(1,2,3,4,5);
```

