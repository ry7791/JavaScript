## jQuery





```js
<!DOCTYPE html>
<html>
    <head>
        <script src="../jquery/jquery.js"></script>
        <!-- <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script> -->
        <script>
            $(document).ready(function(){
                
                $("#btnRed").on('click',function(){                 
                    $("#myH1").css('color', 'red');
                });

                $("#btnBlue").on('click',function(){
                    $("#myH1").css('color', 'blue');
                });
            });
        </script>
    </head>
    <body>
        <h1 id="myH1">Hello, jQuery</h1>
        <button id="btnRed">RED</button>
        <button id="btnBlue">BLUE</button>
    </body>
</html>
```

