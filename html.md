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

  

  



