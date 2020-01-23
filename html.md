# html

- width : 간격
- border: 선의 굵기 
- <th> </th> : 데이터 글자 진하게
- <td></td> : 테이블 데이터

- <td colspan="2"></td> : 컬럼 두개 병합
- <td> rowspan="2"></td>: row 두개 병합



- 이력서 양식

  ```HTML
  <!DOCTYPE html>
  <html>
      <head>
          <script>
          </script>
          <style type='text/css'>
          #ff{
              font-family:"맑은고딕";
              text-align: right;
          }
          </style>
      </head>
      <body>
          <table width="500" border="1"> <!-- border 선의 굵기-->
              
              <tr>
                  <td rowspan="4">사 진</td>
                  <td colspan="4">이 력 서</td>
              </tr>
  
              <tr>
  
                  <td rowspan="2">성 명</td>
                  <td rowspan="2" colspan="2" id="ff">               (인)</td>
                  <td>주민등록번호</td>
  
              </tr>
  
              <tr>
                  <td height="20"></td>
              </tr>
  
              <tr>
                  <td>생년월일</td>
                  <td colspan="3">19   년  월       일생 (만 세)</td>
              </tr>
  
              <tr>
                  <td>주소</td>
                  <td colspan="4"></td>
              </tr>
  
              <tr>
                  <td>호적관계</td>
                  <td width="100" height="10"></td>
                  <td width="100" ></td>
                  <td width="100"></td>
                  <td width="100"></td>
              </tr>
  
          </table>
      </body>
  
  
  </html>
  ```

  



- form 생성

  ```html
  <!Doctype html>
  <html>
  <head>
  
  </head>
  
  <body> <!-- post/get 
              post -> 사용자가 입력한 내용을 서버에 전달(가입, 저장)
              get -> 사용자가 서버의 resource를 요청
  					ex) 웹 브라우저 -> URL 요청
  					get은 데이터를 보낼때 내용이 노출될 수 있음 
  				
      -->
      <form action="regist.html" method="POST">
          이름 : <input type="text" placeholder="이름을 입력하세요"><br/>
          아이디: <input type="txt" placeholder="아이디를 입력하세요"><br/>
          비밀번호: <input type="password" placeholder="비밀번호를 입력하세요"><br>
          남성: <input type="radio" name="gender">
          여성: <input type="radio" name="gender"><br/>
          사용하는 sns:
          <input type="checkbox"> Facebook
          <input type="checkbox"> Twitter
          <input type="checkbox"> Instagram
          <input type="checkbox"> Google+
          연령
          <select>
              <option>10대</option>
              <option>20대</option>
              <option>30대</option>
              <option>40대</option>
          </select><br/>
          사진:
          <input type="file"><br/>
          자기소개:
          <textarea cols="40" rows="5"></textarea>
          <input type="submit" value="회원가입"> <!-- 제출하면 저장은 action쪽으로 전송-->
          <input type="reset" value="초기화">
          <input type="button" value="임시저장">
      </form>    
  </body>
  
  
  </html>
  
  
  ```

  

  - method : 폼을 전송할 방식을 선택하는 속성으로, 사용할 수 있는 값은 get과 post입니다. get은 256~4096바이트의 정보만 서버로 넘길 수 있지만, post는 사용자의 입력 내용의 길이에 제한을 받지 않습니다. 대개의 경우 post를 사용합니다get방식의 경우 query string을 url에 붙여 서버측으로 전송하기도 합니다.
  - name : 한 문서 안에 여러개의 폼이 있을 수 있기 때문에 폼을 식별하기 위한 폼의 이름입니다.
  - action: 폼을 전송할 서버 쪽의 스크립트 파일을 지정합니다. action 속성을 이용하지 않고 onsubmit 이벤트를 이용해 스크립트로 처리할 수도 있습니다.
  - target: action에서 지정한 스크립트 파일을 현재 창이 아닌 다른 위치에 열도록 지정합니다.<fieldset> , <legend> 태그는 폼 요소들을 보기 쉽게 그룹으로 묶어주는 태그입니다. 예를들어 쇼핑몰 사이트에서 주문서를 작성하는 폼에서 사용자 정보와 배송정보를 따로 나누어 표시하면 사용자가 정보를 입력하기에도 편리하고 화면도 깔끔하게 정리할 수 있습니다.이렇게 하나의 폼 안에서 여러 구역을 나눠 표시하려고 할때

