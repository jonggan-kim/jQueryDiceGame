# jQueryDiceGame
Dice game using jQuery
<!DOCTYPE html>
<html>
  <head>
    <title>jQuery Dice Game</title>
    <style>
      .box1 {
        border-radius: 10px;
        border: 2px solid #73ad21;
        background-color: #73ad21;
        padding: 10px;
        margin: 10px;
        width: 400px;
        height: 20px;
        color: white;
        text-align: center;
      }

      .box2 {
        width: 400px;
        height: 300px;
        margin: 10px;
        padding: 10px;
        text-align: center;
        border: 2px solid grey;
        float: left;
      }

      #bt1 {
        background-color: greenyellow;
      }

      #msgimg {
        width: 420px;
        margin-top: 350px;
        margin-left: 10px;
        padding-top: 10px;
        height: 150px;
        border: 2px solid black;
        background-color: yellow;
        text-align: center;
        float: both clear;
      }

      #msg {
        background-color: greenyellow;
        padding-top: 20px;
        margin-top: 10px;
        margin-left: 10px;
        width: 420px;
        height: 80px;
        border: 2px solid black;
        text-align: center;
      }
    </style>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
    <script>
      var clickCnt = 0;
      var winCnt = 0;
      $(document).ready(function () {
        $('p>img').click(function () {
          clickCnt++;
          // take out the number that's clicked on one of the dice
          var n = $(this).attr('src');
          n = n.replace('./dice/', '');
          n = n.replace('.png', '');
          n = parseInt(n.replace('.png', ''));
          // generate a random number among 1 and 6
          var com = Math.floor(Math.random() * 6) + 1;
          /* put a corresponding picture using jQuery and replacing src attribute
          in id = img1, img2 */
          $('#img1').attr('src', './dice/' + n + '.png');
          $('#img2').attr('src', './dice/r' + com + '.png');

          /* if the one user click is same as the one generated randomly, 
          show "you got right", otherwise, "you got wrong"
          count the total trial number and the number you got right
          */
          var str = '';
          if (n == com) {
            str = str + 'You got right !' + '<br>';
            winCnt++;
          } else {
            str = str + 'You got wrong !' + '<br>';
          }

          str = str + 'Number of Trial: ' + clickCnt + ',  ';
          str = str + 'Correct Number: ' + winCnt;
          $('#msg').html(str);
        });
        /*  redo will reset the dice chosen by user and randomly selected 
        and the statement(you got wrong or you got wrong) and the score  
        */
        $('input[type=button]').click(function () {
          $('#img1').attr('src', './dice/q.png');
          $('#img2').attr('src', './dice/q.png');
          $('#msg').html('');
          clickCnt = 0;
          winCnt = 0;
        });
      });
    </script>
  </head>

  <body>
    <form name="form1">
      <div class="box1">jQuery Dice Game</div>
      <div class="box2">
        <p>
          <img width="100" src="./dice/1.png" />
          <img width="100" src="./dice/2.png" />
          <img width="100" src="./dice/3.png" />
        </p>
        <p>
          <img width="100" src="./dice/4.png" />
          <img width="100" src="./dice/5.png" />
          <img width="100" src="./dice/6.png" />
        </p>
        <p>
          <input type="button" value="Redo" id="bt1" />
        </p>
      </div>
      <div id="msgimg">
        <img width="100" src="./dice/q.png" id="img1" />
        <img width="100" src="./dice/vs.png" />
        <img width="100" src="./dice/q.png" id="img2" />
      </div>

      <div id="msg"></div>
    </form>
  </body>
</html>
