# jsclock
simple js clock 
The clock is simple and very handy to integrate on your page.
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Clock in JS  </title>
</head>
<body>

    <div class="datetime">
        <i class="fas fa-clock"></i>
        <span class="time">
            <span class="time-hours">01</span><span class="time-colon">:</span><span class="time-minutes">41</span> 
            <span class="time-format">PM</span>
        </span>
        <span class="date">Wednesday, 10 February 2016</span>
    </div>
    <script>

        var dateContainer = document.querySelector('.date');

        function getDayInName(number = null) {
            var d = new Date();
            var week = new Array();
            week[1] = "Dushanba";
            week[2] = "Seshanba";
            week[3] = "Chorshanba";
            week[4] = "Payshanba";
            week[5] = "Juma";
            week[6] = "Shanba";
            week[7] = "Yakshanba";
            if(number === null)
                return week[d.getDay()];
            else return week[number];
        }
        function getMonthInNumber(number = null) {
            var d = new Date();
            var month = new Array();
            month[0] = "Yanvar";
            month[1] = "Fevral";
            month[2] = "Mart";
            month[3] = "Aprel";
            month[4] = "May";
            month[5] = "Iyun";
            month[6] = "Iyul";
            month[7] = "Avgust";
            month[8] = "Sentabr";
            month[9] = "Oktabr";
            month[10] = "Noyabr";
            month[11] = "Dekabr";
            if(number === null)
                return month[d.getMonth()];
            else return month[number];
        }
        
        dateContainer.textContent = `${getDayInName(new Date().getDay())}, ${new Date().getDate()} ${getMonthInNumber()}` 
        
        var clockContainer = document.querySelector('.time');
        setInterval(() => {
            clockContainer.querySelector('.time-colon').style.opacity = '0';
        }, 500);

        setInterval(() => {
            
            clockContainer.querySelector('.time-minutes').textContent = new Date().getMinutes();
            if (new Date().getMinutes() < 10) {
                clockContainer.querySelector('.time-minutes').textContent = `0${new Date().getMinutes()}`;
            }
            
            if (new Date().getHours() > 12) {
                if ((new Date().getHours() - 12) < 10) {
                    // console.log(new Date().getHours() - 12);
                    
                    clockContainer.querySelector('.time-hours').textContent = `0${new Date().getHours() - 12}`;    
                }else{
                    clockContainer.querySelector('.time-hours').textContent = new Date().getHours() - 12;    
                }
                

                clockContainer.querySelector('.time-format').textContent = 'PM';
            }else{
                clockContainer.querySelector('.time-format').textContent = 'AM';
            }
            clockContainer.querySelector('.time-colon').style.opacity = '1';
        }, 1000);
        
     
    </script>
</body>
</html>
```
