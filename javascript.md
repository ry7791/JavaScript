# javascript

- 비교연산자

  - 값과 데이터타입이 다 같은지 비교 하는 연산자 : === , !==

  ```javascript
  var a = 10;
  var b = "10";
  console.log(a==b);    => true
  console.log(a===b);   => false
  ```

  

- 함수

  - alert() : 경고창

  - confirm() : 확인 취소버튼

  - prompt() : 입력창

    - 홀수 짝수 판별

    ```javascript
    var check1 =confirm("홀수 짝수 판별");{
                
                if(check1==true){
                    var userVal = prompt("값을 입력하세요.");
                    if(userVal%2===0){
                        console.log(userVal+" 당신이 입력한 값은 짝수입니다");
                }   else{
                    console.log(userVal+" 당신이 입력한 값은 홀수입니다");
                }
            }
                else ;
            }
    ```

    

- 변수

  - var : 선언한 값은 언제든지 다시 바꿀 수 있기에  - 권장 안함

    

  - let : 로컬변수, 중복 선언 불가

  - const  :  상수변수 , 중복 선언 불가



- 복합 대입 연산자

  ```javascript
  <script>
          window.onload = function(){
              var list='';
  
              list+='<ul>';
              list+='     <li>Hello</li>';
              list+='     <li>JavaScript..!</li>';
              list+='</ul>';
  
              document.body.innerHTML = list;
              
          }
              </script>
  ```

- window.onload : 웹페이지가 보여지면서 최초 1회 실행되는 이벤트



- 자료형 검사

  - typeof : 자료형 확인

    ```javascript
    
    let a= 10;
    let b= "10";
    console.log(typeof a); => number
    console.log(typeof b); => string
    console.log(a === b);  => false
    ```

- if문 예제

  ```javascript
  <!DOCTYPE html>
  <html>
  <head>
      <script>
        
        let korean= Number(prompt("값을 입력하시오"));
        let math= Number(prompt("값을 입력하시오"));
        let english= Number(prompt("값을 입력하시오"));
    
        let avg= (korean+math+english)/3;
        console.log(avg);
  
        if(avg>=90){
              var grade = "A";
              console.log("A "+avg);}
  
             else if(avg>=80){
            var grade = "B";
              console.log("B "+avg);}
  
              else if(avg>=70){
             var grade = "C";
              console.log("C "+avg);}
  
              else if(avg>=60){
              var grade = "D";
              console.log("D "+avg);
               }
  
              else{
              var grade ="F";
              console.log("F "+avg);
              }
              
              alert("당신의 성적은"+grade+"입니다\t"+"점수는"+avg+"입니다");
        
      </script>
  </head>
  <body>
  </body>
  
  </html>
  ```

- swithch문 예제

```javascript
<!DOCTYPE html>
<html>
<head>
    <script>
      
      let korean= Number(prompt("값을 입력하시오"));
      let math= Number(prompt("값을 입력하시오"));
      let english= Number(prompt("값을 입력하시오"));
  
      let avg= (korean+math+english)/3;
      console.log(avg);


          switch (avg){
            case avg>90:
              console.log("A");
              break;
              case avg>80:
              console.log("B");
              break;
              case avg>70:
              console.log("C");
              break;
              case avg>60:
              console.log("D");
              break;
              default:
                console.log("F");
                break;
          }
      
    </script>
</head>
<body>
</body>

</html>
```



- indexOf 함수

  ```javascript
  let sayHello = "안녕하세요.";
  console.log(sayHello);
  console.log(sayHello.indexOf("안녕")); //0 인덱스 안의 내용이 sayhello에 몇 번째에 위치에 있는지 알려줌
  console.log(sayHello.indexOf("하세요")); // =>2
  ```

  