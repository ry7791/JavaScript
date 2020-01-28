## 객체



- 메서드

```javascript
            let school = {
                name : 'Multicampus',
                capacity: [30,30,30],
                grade:'3',
                event: function(month, eventName){
                    console.log(this.name+','+month+"달에"+eventName+"행사가 있습니다.");
                }
            }
            school.event("1월","졸업식");
```



- with 키워드

```javascript
            let student = {};
            student.name = "정욱";
            student.kor = 100;
            student.mat = 90;
            student.eng = 80;

            let sum = 0; // 총점
            let avg = 0; // 평균

            with(student){
                sum = kor + mat + eng;
                avg = sum/3;
            }

            // 총점과 평균 출력
            console.log("총점 : ", sum);
            console.log("평균 : ", avg)
```



- 배열에 데이터 추가

```javascript
 let students = [];
            students.push({이름:'AAA',국어:90,수학:70,영어:90});
            students.push({이름:'BBB',국어:85,수학:75,영어:85});
            students.push({이름:'CCC',국어:80,수학:80,영어:80});
            students.push({이름:'DDD',국어:75,수학:85,영어:75});
            students.push({이름:'EEE',국어:70,수학:90,영어:70});

           
            for (let i in students){
                console.log(students[i].이름);
                // students[i].sum =    students[i].국어+
                //                      students[i].수학+
                //                      students[i].영어;
                // students[i].avg =   students[i].sum/3;
                // 학생별 총점/평균, 전체 평균
                students[i].sum= function(){
                    return this.국어+this.수학+this.영어;
                };
                students[i].avg= function(){
                    return this.sum()/3;
                };
            }
            for (let i in students){
                with(students[i]){
                console.log(이름 + " : " +sum()+"/"+ avg());
                }
            }
            //전체 평균
            var TotalSum=0;
            var TotalAvg=0;
            for (let i in students){
                TotalSum+=students[i].sum();
            }
            TotalAvg=TotalSum/students.length;
            console.log(TotalAvg);
```



## 생성자 함수

NEW 를 이용한 객체를 인스턴스화



- 메소드 생성

```javascript
            function student(name, kor, eng, mat, sci){
                //속성
                this.이름 = name;
                this.국어 = kor;
                this.영어 = eng;
                this.수학 = mat;
                this.과학 = sci;

				// 메소드
                this.sum = function(){
                    return this.국어+this.영어+this.수학+this.과학;
                };
                this.avg = function(){
                    return this.sum()/4;
                }
            }
            let student1 = new student("A, 100, 90, 80, 70)
            let student2 = new student("B, 90, 90, 80, 70)
            console.log(student1.sum()+"/"+ student1.avg());
            console.log(student2.sum()+"/"+ student2.avg());
```



- 생성자 함수를 사용한 객체 배열 생성

```JS
function student(name, kor, eng, mat, sci){
                //속성
                this.이름 = name;
                this.국어 = kor;
                this.영어 = eng;
                this.수학 = mat;


				// 메소드
                this.sum = function(){
                    return this.국어+this.영어+this.수학;
                };
                this.avg = function(){
                    return this.sum()/3;
                }
            }
            let students=[];
            students.push(new student('AAA',90,70,90));
            students.push(new student('BBB',80,70,90));
            students.push(new student('CCC',60,70,90));
            students.push(new student('DDD',70,70,90));
           
            for (let i in students){
                with(students[i]){
                console.log(이름 + " : " +sum()+"/"+ avg());
                }
            }

```



## 기본 내장 객체



- 기본 자료형과 객체



- Number 

```js
let primtiviNumber = 273; // 속성, 메소드 추가 x
            let objectNumber = new Number(273); // 속성, 메소드 추가
            Number.prototype.method = function(){
                return "Method on Prototype";
            }

            console.log("Primitive: " + primtiviNumber);
            console.log("Object: " + objectNumber+"/"+objectNumber.method());
```



- toString()

  ```js
  // toString() 재정의 (overriding, 함수의 내용을 재정의)  
  let student = {
                  name : '정욱',
                  grade: "1학년",
                  toString: function(){
                      return this.name + "/" + this.grade;
                  }
              }
  
              console.log("Student:"+ student); //Student:정욱/1학년
  			console.log("Student:"+ student.toString()); //Student:정욱/1학년
  ```



### String 객체의 메서드

- charAt(position)  : position에 위치하는 문자를 리턴
- concat(args) : 매개변수로 입력한 문자열을 이어서 리턴
- indexOf(searchString, position) : 앞에서부터 일치하는 문자열의 위치를 리턴
- lastIndexOf(searchString, position) : 뒤에서부터 일치하는 문자열의 위치를 리턴
- match(regExp) : 문자열 안게 regExp가 있는지 확인
- split(separator, limit) : separator로 문자열을 잘라서 배열을 리턴
- substr(star,count) : start부터 count만큼 문자열을 잘라서 리턴
- substring(start,end): start부터 end까지 문자열을 잘라서 리턴 

```js
         let str1 = 'Hello World!';

         console.log(str1.length);  // 12
         console.log(str1.charAt(4)); // o
         console.log(str1.concat(" hi, there!")); // Hello World! hi, there!
         console.log(str1.indexOf("World")); //6 
         console.log(str1.lastIndexOf("World")); //6

         let ipaddress = "58.29.12.24";
         let values = ipaddress.split('.');
         console.log(typeof values); //object
         console.log(values[0]); //58
         console.log(ipaddress.substr(0,3)); //58.
         console.log(ipaddress.substring(4,6)); // 9.
```





- 대문자 변환

```js
   var string = 'abcdefg';
        string = string.toUpperCase();
        console.log(string);
```



- sort()

```js
 students.sort(function(left, right){
                return right.국어 - left.국어;
            });
```



### Math 객체의 메서드

- abs(x) : x의 절대값 리턴
- ceil(x) : x보다 크거나 같은 가장 작은 정수를 리턴
- 







- Date()

```js
            let now = new Date();
            console.log(now);
            for (let i=0; i<100000000; i++){
                ;
            }
            let now2 = new Date('Tue Jan 28 2020 14:20:12');
            console.log(now2);
            console.log(now - now2);
```



- forEach()

```js
        let array = [50,203,227,2,158,34 ,23, 6, 256, 10];
         let newArray = [];
            array.forEach(function(element){
                if(element %2 == 1)
                    newArray.push(element);

            });

            newArray.forEach(function(element){

                console.log(element);
            });

```

```js
         let array = [50,203,227,2,158,34 ,23, 6, 256, 10];
         let newArray = [];



            let grade = array.map(function(element){
                if(element>=90)
                    return "A";
                else if (element>=80)
                    return "B";
                else if (element>=70)
                    return "C";
                else if (element>=60)
                    return "D";
                else
                    return "F";

            });

            grade.forEach(function (element,index,grade) {
              console.log(array[index]+" => "+element);

             } );
```



- filter()

```js
            let jumsu = [90, 99, 50]; //, 60, 70, 58, 88, 72 , 40, 89

            function myFilter(element,index, array){
                return element>=60;
            }

                jumsu = jumsu.filter(myFilter);
            // jumsu = jumsu.filter(function(element,index,array){
            //         return element>=60;
            // });
                

            
            jumsu.forEach(function(element){
                console.log(element);
            });
```

- filter()

```js
            let students = [];
            students.push({이름:'AAA',국어:90,수학:70,영어:90});
            students.push({이름:'BBB',국어:85,수학:75,영어:85});
            students.push({이름:'CCC',국어:80,수학:80,영어:80});
            students.push({이름:'DDD',국어:75,수학:85,영어:75});
            students.push({이름:'EEE',국어:70,수학:90,영어:70});
            
            for (let i in students){
                students[i].sum= function(){
                    return this.국어+this.수학+this.영어;
                };
                students[i].avg= function(){
                    return this.sum()/3;
                };
            }

            function myFilter(element, index, array){
                return element.sum() >= 240;
            }
            
            let highGroup = students.filter(myFilter);
            highGroup.forEach(function(element){
                console.log(element.이름 + "/" + element.sum());
            });
```



- reduce()

```js
            let jumsu = [1,2,3,4,5];

           let result = jumsu.reduce(function(preValue, curValue, index, array){
                 console.log(preValue);
                 console.log(curValue);
                 console.log(index);
                 console.log(array);
                 console.log("----------");
                return preValue+curValue;
            });

            console.log(result);
```



- JSON 객체
  - parse:  string을 object로 바꿔줌

```js
            let json = `{
                "id": 12345,
                "accountNumber": "123-345-5665",
                "name": "정욱",
                "balance": 1000,
                "LastTxDate": "2020-01-22"
            }`;
            let parsedJson = JSON.parse(json);

            console.log(JSON.parse(json));
            console.log(typeof JSON.parse(json));
            console.log(parsedJson.name + "/" + parsedJson.balance);
```
- stringify : object를 string으로 바꿔줌

```js
let json = {
                "id": 12345,
                "accountNumber": "123-345-5665",
                "name": "정욱",
                "balance": 1000,
                "LastTxDate": "2020-01-22"
            };
            let stringJson = JSON.stringify(json);

            console.log(stringJson);

```



- 날씨 api에서 데이터 추출

```js
            let openapi= `{
                "coord": { "lon": 139,"lat": 35},
  "weather": [
    {
      "id": 800,
      "main": "Clear",
      "description": "clear sky",
      "icon": "01n"
    }
  ],
  "base": "stations",
  "main": {
    "temp": 281.52,
    "feels_like": 278.99,
    "temp_min": 280.15,
    "temp_max": 283.71,
    "pressure": 1016,
    "humidity": 93
  },
  "wind": {
    "speed": 0.47,
    "deg": 107.538
  },
  "clouds": {
    "all": 2
  },
  "dt": 1560350192,
  "sys": {
    "type": 3,
    "id": 2019346,
    "message": 0.0065,
    "country": "JP",
    "sunrise": 1560281377,
    "sunset": 1560333478
  },
  "timezone": 32400,
  "id": 1851632,
  "name": "Shuzenji",
  "cod": 200
}`;
console.log(openapi);
console.log(typeof openapi);
// Javascript object로 변경
// 현재 온도, 최고, 최저 온도 출력
let parsedJson = JSON.parse(openapi);
console.log("현재날씨:"+parsedJson.weather[0].main);
console.log("현재온도:" +parsedJson.main.temp);
console.log("최고온도:"+parsedJson.main.temp_max);
console.log("최저온도:"+parsedJson.main.temp_min);

```

