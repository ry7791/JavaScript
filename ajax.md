# ajax



- api 데이터 차트로 나타내기

```js
<!DOCTYPE html>
<html>
<head> 
  <meta charset="UTF-8"> 
  <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
  <meta http-equiv="X-UA-Compatible" content="ie=edge"> 
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous"> 
  <!-- 차트 링크 --> 
  <script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script> 
  <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script> 
  <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script> 
  <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script> 
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>

  <script>
    $(document).ready(function() {

        $.ajax({
                                url: "https://poloniex.com/public",
                                type: "GET",
                                data: {
                                    'command':"returnChartData",
                                    'currencyPair':"USDT_BTC",
                                    'start':"1577843804",
                                    'end':"9999999999",
                                    'period':"86400"
                                },
                                

                                success: function(data){  
                                    let dateArray = [];       
                                    let highArray = [];
                                    let lowArray = [];
                                    for(let i=0;i<data.length;i++){
                                        let timestamp = data[i].date*1000;
                                        var date = new Date(timestamp);
                                        
                                        dateArray.push(date.getMonth()+1+"/"+date.getDate());
                                        console.log(dateArray[i]);
                                    }
                                    
                                    for(let i=0;i<data.length;i++){
                                        
                                        
                                        highArray.push(data[i].high);
                                        console.log(highArray[i]);
                                    }
                                    
                                    for(let i=0;i<data.length;i++){
                                        
                                        
                                        lowArray.push(data[i].low);
                                        console.log(lowArray[i]);
                                    }
                                    // drawChart(lowArray,low);

      let ctx = document.getElementById('myChart').getContext('2d'); 
      let chart = new Chart(ctx, { 
        type: 'line', 
        data: { 
          labels: dateArray, 
          datasets: [{ 
            label: 'My First dataset', 
            backgroundColor: 'transparent', 
            borderColor: 'red', 
            data: highArray
          },
          {
            label: 'My First dataset', 
            backgroundColor: 'transparent', 
            borderColor: 'blue', 
            data: lowArray

          }] 
        }, 
        options: {
          legend: { 
            display: false 
          }
        } 
      }); 
   
        },
        error: function(data){
             console.log("ERROR:"+err);
                                }
        });                  
    });

    // function drawChart(array,item){
    //     for(let i=0;i<data.length;i++){                                                        
    //         array.push(data[i].item);
    //         console.log(array[i]);
    //     }
    // }
  </script>
</head> 
<body> 
  <div class="container"> 
    <canvas id="myChart"></canvas> 
  </div> 
</body>
</html>
```



- 코인데이터 api

```js
<!DOCTYPE html>
<html>
<head>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>

  <script>
        $(document).ready(function(){

       
            

         
                            $.ajax({
                                url: "https://poloniex.com/public",
                                type: "GET",
                                data: {
                                    'command':"returnChartData",
                                    'currencyPair':"USDT_BTC",
                                    'start':"1577843804",
                                    'end':"9999999999",
                                    'period':"86400"
                                },
                                
                              


                                success: function(data){
                                  
                                    
                                        $.each(data, function(index, item) {
                                            
                                            let timestamp = item.date*1000;
                                            let date = new Date(timestamp);
                                            let high = item.high;
                                            let low = item.low;
                                            let volume = item.volume;



                                            let div = document.createElement("div");
                                            let html = "";
                                            html += "<span >"+ date + "</span>";
                                            html += "<span style='color:red;'>"+ high + "</span>";
                                            html += "<span style='color:blue;'>"+ low + "</span>";
                                            html += "<span>"+ volume + "</span>";

                                            // let span1= document.createElement("span");
                                            // span1.innerHTML = date;

                                            // let span2= document.createElement("span");
                                            // span2.innerHTML = high;
                                        
                                            // let span3= document.createElement("span");
                                            // span3.innerHTML = low;
                                            // let span4= document.createElement("span");
                                            // span4.innerHTML = volume;


                                            // div.appendChild(span1);
                                            // div.appendChild(span2);
                                            // div.appendChild(span3);
                                            // div.appendChild(span4);
                                            div.innerHTML = html;

                                            $('#contents').append(div);

                                        });

                                },

                                error: function(data){
                                    console.log("ERROR:"+err);
                                }

                            });
                


            


            

     


        });
  </script>
</head>
<body>
    <h1 id='contents' > </h1>

    
    



</body>  
</html>
```



- 날씨api 를 이용한 선택한 도시 날씨 나타내기

```js
<!DOCTYPE html>
<html>
<head>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
  <script>
        $(document).ready(function(){

       
            
            $('#btnSubmit').on('click',function(){
                //let city = $("#city > option:selected").val();
                  
                    let city = $('#city > option:selected').val();
                            $.ajax({
                                url: "http://api.openweathermap.org/data/2.5/forecast",
                                type: "GET",
                                data: {
                                    q: city,
                                    APPID:"68eb759e76f0322e86acf10160c55c66",
                                    units:"metric"
                                },
                                
                                


                                success: function(data){
                                
                                   //$('#contents').empty();
                                    
                                        // 1. PARSING -> string -> object
                                       //let parsedForecast = JSON.parse(data);

                                       $('#contents').empty();
                                        $.each(data.list, function(index, item) {
                                        let _image = document.createElement("img");
                                        _image.src = "http://openweathermap.org/img/wn/"
                                            + item.weather[0].icon +"@2x.png";

                                        let _divhtml = item.dt_txt;
                                        _divhtml += ", 온도:" + item.main.temp;
                                        _divhtml += " <span style='color:blue;'>" + item.main.temp_min + "</span>";
                                        _divhtml += "/<span style='color:red;'>" + item.main.temp_max + "</span>";
                                        _divhtml += ", " + item.weather[0].description;

                                        let imageSpan = document.createElement("span");
                                        imageSpan.appendChild(_image);
                                        let infoSpan = document.createElement("span");
                                        infoSpan.innerHTML = _divhtml;

                                        let div = document.createElement("div");
                                        div.appendChild(imageSpan);
                                        div.appendChild(infoSpan);

                                        $('#contents').append(div);
                                        });

                                },

                                error: function(data){
                                    console.log("ERROR:"+err);
                                }

                            });
                

            });
            


            

     


        });
  </script>
</head>
<body>
        <select id="city">
            <option value="seoul">서울</option>
            <option value="london">런던</option>
            <option value="tokyo">도쿄</option>
        </select>
        <!-- <input type="text" name="city" placeholder="도시를 입력하세요.">  -->
        <button id="btnSubmit">검색</button>
        <div id="contents">



</body>  
</html>
```

