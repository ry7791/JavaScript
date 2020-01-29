## 브라우저 객체 모델



### open메서드

```js
<!doctype html>
<html>
    <head>
        <script>
            window.open("https://www.naver.com", "myNaver", "width=800 height=700", true);
          function myOpen(url){
            window.open(url);
          }

        </script>
    </head>
    <body>
      <ul>
        <li><a href="https://www.google.com">Google</a></li>
        <li><a onclick="window.open('https://www.google.com')">Google</a></li>
        <li><a onclick="myOpen('https://www.google.com')">Google</a></li>
        <li><button onclick="myOpen('https://www.google.com')">Google</button></li>
      </ul>

    </body>
</html>
```



### onload 

- window 객체가 로드가 완료되고 자동으로 할당한 함수를 마지막으로 실행

```js
<!doctype html>
<html>
<head>
    <script>
        console.log('Process - 0');
        
        window.onload= function(){
            console.log('Process - 3');
        }
        
    </script>
</head>
<body>
    <h1>Process - 1</h1>
    <script>alert("Process - 1");</script>
    <h1>Process - 2</h1>
    <script>alert("Process - 2");</script>

</body>
</html>
```





## 문서 객체 모델



### 객체 노드 - 동적생성 제거

```js
<!doctype html>
<html>
<head>

    <script>
       

window.onload = function(){
    	// 객체의 노드 생성 메서드
        let ul_tag = document.createElement("ul"); //요소노드 
        let li_tag1 = document.createElement("li");
        let li_tag2 = document.createElement("li");
        let Naver_text = document.createTextNode("Naver"); //텍스트노드
        let Daum_text = document.createTextNode("Daum");
       
        li_tag1.appendChild(Naver_text);
        li_tag2.appendChild(Daum_text);

        ul_tag.appendChild(li_tag1);
        ul_tag.appendChild(li_tag2);

        document.body.appendChild(ul_tag); //객체 연결 메서드

    
        let myImg = document.createElement("img");
        myImg.src = "캡처.PNG";
        myImg.width = 1915;
        myImg.height = 955;

        document.body.appendChild(myImg);

        // document.body.innerHTML= "<h1 style='color:blue;'>Hello, junguk. hi, there</h1>";

        let div1 = document.getElementById("myDiv1"); //아이디를 사용해 객체를 선택
        div1.innerHTML ="<h1 style='color:blue;'>Hello, junguk. hi, there</h1>";
    	document.body.removeChild(document.getElementById("myh1")); //제거
};
        
    </script>
</head>
<body>
    <h1>hello, dom</h1>

</body>
</html>
```





### 날씨 api 이용하기

- api 키값 받자

![image-20200129134029876](C:\Users\HPE\AppData\Roaming\Typora\typora-user-images\image-20200129134029876.png)

- api 불러보자

![image-20200129134308111](C:\Users\HPE\AppData\Roaming\Typora\typora-user-images\image-20200129134308111.png)

- 서울날씨

![
](C:\Users\HPE\AppData\Roaming\Typora\typora-user-images\image-20200129135056429.png)

- api를 이용해서 weather.html 파일을 만들어보자

```js
<!DOCTYPE html>
<html>
    <head>
        <script>
        let weather_json = `
        {
         "weather": [{
            "main": "Clouds","description": "overcast clouds",
            "icon": "04d"
            }
            ],
            "main": {
            "temp": 9.27,
            "temp_min": 9,
            "temp_max": 10,
            "humidity": 45
            },
            "wind": {
            "speed": 1.5
            },
            "clouds": {
            "all": 90
            },
            "dt": 1580273107
        }`;
        window.onload = function(){
        let _img = document.getElementById("_img");
        let _temp = document.getElementById("_temp");
        let _temp_min = document.getElementById("_temp_min");
        let _temp_max = document.getElementById("_temp_max");
        let _wind = document.getElementById("_wind");

        // json 파일의 값을 각 tag 값에 지정
        // createElement(), createTextNode(),
        // innerHTML, innerText
        // appendChild()

        let parsedJson = JSON.parse(weather_json);
        let _image = document.createElement("img");
        

        _image.src= "https://openweathermap.org/img/wn/" + parsedJson.weather[0].icon+"@2x.png";
        _img.appendChild(_image);

        _temp.innerText = "현재온도: " + parsedJson.main.temp + "도 "+ parsedJson.weather[0].main;
        _temp_min.innerText =parsedJson.main.temp_min;
        _temp_max.innerText =+parsedJson.main.temp_max;
        _wind.innerText = "풍속" + parsedJson.wind.speed + ", 습도" + parsedJson.main.humidity;
        }


        </script>
    </head>
    <body>
        <table>
            <tr>
                <td rowspan="2" id="_img"></td>
                <td colspan="2" id="_temp"></td>

            </tr>
            <tr>
                <td>
                    <span>최저온도 : </span>
                    <span id="_temp_min" style='color:blue;'></span>
                    <span>최고온도 : </span>
                    <span id="_temp_max" style='color:red;'></span>
                </td>
                <td id="_wind">풍량...</td>
            </tr>
        </table>
        
    </body>
</html>
```



- clock

```js
<!doctype html>
<html>
    <head>
        <script>
            window.onload= ()=>{
                let clock = document.getElementById("clock");

                setInterval(function(){
                    clock.innerHTML = new Date().toString();
                }, 1000);
                let count=0;
                clock.onclick = function(){
                    count++;
                    if(count%2==0)
                    clock.style = "color: blue;";
                    else
                    clock.style = "color: green;";
                    clock.style.backgroundColor= "red";
                };
            }
        </script>

    </head>
    <body>
        <h1 id="clock"></h1>
    </body>


</html>
```



- event    -버튼 누르기

```js
<!doctype html>
<html>
    <head>
        <script>
            
            
            window.onload=()=>{
                let count=0;
                let counter = document.getElementById("counter");
                let plusBtn = document.getElementById("plus");
                let minusBtn= document.getElementById("minus");

             


                plusBtn.onclick = function(){
                    counter.innerText=++count;
                }
               
                minusBtn.onclick = function(){
                    counter.innerText=--count;
                }
            
            }
        </script>

    </head>
    <body>
        <h1 id="counter">0</h1>
       
        <button id="plus">+</button>
        <button id="minus">-</button>
   
    </body>


</html>
```





- event 이용한 아이디생성

```js
<!Doctype html>
<html>
<head>
    <script>
        function saveTemporary(){
            let uncheck=1;
            let selectedSns = document.getElementsByName("sns");
            for(let i=0; i< selectedSns.length;i++){
                if(selectedSns[i].checked){
                    console.log(selectedSns[i].value);
                    let uncheck=0;
                }
                
            }
            if(uncheck==1) {alert("sns 선택은 필수 사항입니다");}

            let inputs = document.getElementsByName('input');
            for(let i=0; i< inputs.length;i++)
                console.log(inputs[i]);
        }

        window.onload = function(){
            let btnNext= document.getElementById("btnNext");
            btnNext.onclick = function(){
                let name = document.getElementById("txtName");
                let id = document.getElementById("txtId");
                let pwd = document.getElementById("txtPwd");
                

                if(name.value == ""){
                    alert("이름은 필수 입력입니다");
                    return;
                }

                if(id.value == ""){
                    alert("아이디는 필수 입력입니다");
                    return;
                }
                if(pwd.value == ""){
                    alert("비밀번호는 필수 입력입니다");
                    return;
                }
                // 다음 단계
                let  frm = document.getElementById("registForm");
                frm.action = "next.html";
                frm.submit();



            }





        }
    </script>
</head>

<body> <!-- post/get 
            post -> 사용자가 입력한 내용을 서버에 전달(가입, 저장)
            get -> 사용자가 서버의 resource를 요청
					ex) 웹 브라우저 -> URL 요청

    -->
    <form action="regist.html" method="GET" id="registForm">
        이름 : <input type="text" id="txtName" name="name" placeholder="이름을 입력하세요"><br/>
        아이디: <input type="txt" id="txtId" name="id" placeholder="아이디를 입력하세요"><br/>
        비밀번호: <input type="password" id="txtPwd" name="password" placeholder="비밀번호를 입력하세요"><br>
        남성: <input type="radio" name="gender">
        여성: <input type="radio" name="gender"><br/>
        사용하는 sns:
        <input type="checkbox" name="sns" value="facebook"> Facebook
        <input type="checkbox" name="sns" value="twitter"> Twitter
        <input type="checkbox" name="sns" value="instargram"> Instagram
        <input type="checkbox" name="sns" value="google"> Google+
        연령
        <select name="age">
            <option value="10">10대</option>
            <option value="20">20대</option>
            <option value="30">30대</option>
            <option value="40">40대</option>
        </select><br/>
        사진:
        <input type="file" name="file"><br/>
        자기소개:
        <textarea cols="40" rows="5"></textarea>
        <input type="submit" value="회원가입"> <!-- 제출하면 저장은 action쪽으로 전송-->
        <input type="button" value="다음단계" id="btnNext">
        <input type="button" value="임시저장" onclick="saveTemporary()">
    </form>    
</body>


</html>


```

