# yipl-frontend-challenge

//1.start page

<!DOCTYPE html>
<html>
<head>
	<title>NEWA CAFE</title>

  <style>
    h2
    {
      
    }
    body
    {
       background-image: url("img.jpg");
      /*background-color: #2E2E2E;*/
      box-sizing: border-box;
    
    }

    input
    {
      width: 200px;
      height: 80px;
      background-color:green; 
      border-radius:5px;
      border: 0px;
      color: white;
      margin: 5px;
      
    }


    fieldset
    {
      width: 240px;
      height: 210px;
      border-radius:5px;
      color: white;
      font-family: Papyrus;
    }
    img
    {
      margin:20px;
    }
  
  </style>
	
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
 
</head>



<body>

 <center><img  src="logo.png"></center> <br><br><br>

<center>
<div class="startoptnbtn">

<fieldset>

  <legend>Choose your position</legend>
   <form action="loginadmn.php">
    <input class="btnadmn" type="submit" name="admin" " value="Admin">
 </form>

<form action="loginworker.php">
  <input class="btnworker" type="submit" name="worker" " value="Worker">
</form>

</fieldset>

  
  </div>
</center>
</body>
</html>


//2.loginpage

<?php
if (isset($_POST['btnlogin'])){
  $err=[];
  echo "this is working";
  
  if (isset($_POST['username']) && !empty($_POST['username']) && 
  trim($_POST['username'])){
    $username=$_POST['username'];
   
  }else{
    
    $err['username'] ='Please enter username';
  }

  echo $username. "string";
  if (isset($_POST['password']) && !empty($_POST['password']) && 
  trim($_POST['password'])){
   // $password=md5($_POST['password']);//user bata pass lyo and md5 ma convert gareko


     $password=($_POST['password']);
  }else{
    
    $err['password'] ='Please enter Password';
  }
print_r($err);
echo $username.$password. "string1";

if(count($err)==0)
{
require_once 'connect1admn.php';
//camocase
$queryForLogin="SELECT * FROM register WHERE username='$username' AND password='$password'";
$resultFromLoginQuery = $connection->query($queryForLogin); //data base ma pathako

print_r($resultFromLoginQuery);
if ($resultFromLoginQuery->num_rows==1) 
{//users has verified and procide to adminoption

header('location:admnoption.php');
}

else
{
//users has not verified -- in valid passwrod or username
}

}
else
{

}

  /*
  if(count($err)==0){
    require_once 'connect1admn.php';
       $sql = "SELECT aid,password FROM register WHERE aid='$aid' AND password='$enctypted_password' AND status=1";
     $result = $connection ->query($sql);
     if($result ->num_rows ==1){
       $row= $result->fetch_assoc();
        session_start();
        $_SESSION['aid'] = $row['aid'];
        $_SESSION['password'] = $row['password'];
        
        header('location:admnoption.html');
     } else {
      $msg = 'id & password not match' ;
     }
     
  }
  */
}

?>








<style>
body{
  background-image: url("img.jpg");
/*  background-color : #2E2E2E;*/
  background-size: cover;
  background-attachment: fixed;
}
.homebtn
{
  color: white;


  
  border-radius:5px;
  border: 0px;
  background-color: green;
  width: 100px;
  height: 30px;
  
 
  
}


.btn
{
  position: relative;top: 40px;
  color: white;
  background-color: green;
  width: 100px;
  height: 30px;
  border: none;
  border-radius: 15px;
}

.register
{
  color: white;
  background-color: green;
  width: 100px;
  height: 30px;
  border: none;
  border-radius: 15px;}


  .input
  {
     border-radius: 15px;
        border: none;
  }
  #password{
    position: relative;top: 20px;
  }
  #reset
  {
    position: relative;top: 50px;
  }
h1
    {
      position: relative;bottom: 1px;
      
    }
    .hformcover
    {
      position: relative;bottom: 70px;
    }

    img
    {
      margin: 20px;
      
    }

</style>








<!DOCTYPE html>
<html>
<head>
      <title>login page</title>
    
</head>
<body>




 

<center><img  src="logo.png"></center><br><br>


<center><button class="homebtn"  onclick="window.location.href='startpage.html';">
    Home
    </button></center>
<center><br><br><br><br><br><br>

  <div class="hformcover"><!--hole form cover-->
<form action="" method="post" id="login_form">
  <fieldset
   style="
    width: 200px;
    height: 260px;
    border-radius:15px; 
    color: white;
    font-size: 20px;
    font-family: Papyrus;

    ">
  <legend> Login form</legend><br>

  <div class="form-group">

    <input class="input" type="text" name="username" id="username" placeholder="Enter Username Here" autocomplete="off">
    
  </div>
  <div class="form-group">
      
    <input class="input" type="password" name="password" id="password" placeholder="Enter password" autocomplete="off">
   
  </div>
  <div class="form-group">
    <input class="btn" type="submit" name="btnlogin" id="login" value="Login">

    <form>
    <button class="btn" id="reset" onclick="window.location.href='loginadmn.php';">
      reset
    </button>
    </form>

  
  </div>
  <?php if (isset($msg)) { ?>
      <p class="error"> <?php echo $msg ?></P>
   <?php } ?>
   
   <?php if (isset($_GET['err']) && $_GET['err'] == 1) { ?>
      <p class="error">please login to continue</P>
   <?php } ?>
  </fieldset>
</form>

 <fieldset 
style="
width: 200px;
height: 90;
 border-radius: 15px;
  color: white;
  font-size: 15px;
  font-family: Papyrus;
  ">
  <legend>Register to creat account </legend>
   <h1 class="registergroup">

            


             <form action="signupadmn.html">

             <input class="register" type="submit" value="register">

             </form>

          </h1>
</fieldset>

</div><!--hole form cover-->
</center>
</body>
</html>

3.menu and bill 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        h1{
            text-align: right;
        }

        img
        {
          margin: 20px;
        }
        button
        {
          color: white;
          border-radius:5px;
          border: 0px;
          background-color: green;
          width: 100px;
          height: 30px;
          margin: 5px;
  
        }
    </style>
</head>





<body>
<center><img  src="logo.png"></center><br><br>
 
<center><button
class="homebtn"  
onclick="window.location.href='startpage.html';"
>
    Home
    </button>
   
   <button
class="homebtn"  
onclick="window.location.href='admnoption.php';"
>
    Back
    </button>
</center>
      

<div class="container-fluid">
    <div class="container">
        <div class="part1">



            <fieldset>
                <legend>Bill Info</legend>
              Bill no: <input class="pinp" type="text" id="billno"> <br/>
               
              Date: <input class="pinp" type="text" id="date"  placeholder="mm/dd/yy"> <br/>
               
            </fieldset>

            <fieldset>
                <legend>Admin Information</legend>
              Admin id: <input class="pinp" type="text" id="namea"> <br/>

               
            </fieldset>

            <fieldset>
                <legend>Customer Information</legend>
                Full Name: <input class="pinp" type="text" id="name"> <br/>

                Your Email: <input class="pinp" type="text" id="email">
            </fieldset>
        </div>


        <div class="part2">
            <fieldset>
                <legend>Menu</legend>
                <img class="mnuimg" src="coffee.jpg">

                <h3 style="text-decoration: 
                underline;">HOT DRINKS</h3><br>

                Tea (Rs. 50): <input type="text" id="tea"> <br>

                Chocolate Milk Shake (Rs. 150): <input type="text" id="cms"> <br>

                Coffee (Rs. 100): <input type="text" id="coffee"> <br>

                Iced Coffee (Rs. 110): <input type="text" id="icedcoffee"> <br>

                expresso (Rs. 122): <input type="text" id="expresso"><br>

                Hot chocolate (Rs. 160): <input type="text" id="hotchocolate"><br>

                Latte (Rs. 90): <input type="text" id="latte"><br>


                <img class="mnuimg" src="pza.jpg">


                <h3 style="text-decoration: 
                underline;">PIZZA</h3><br>

                (small)Chicken Pizza (Rs. 350): <input type="text" id="scp"> <br/>
                (large)Chicken Pizza (Rs. 600): <input type="text" id="lcp"> <br/>
                (small)Buff Pizza (Rs. 450): <input type="text" id="sbp"> <br/>
                (large)Buff Pizza (Rs. 700): <input type="text" id="lbp"> <br/>

                 
                 <img class="mnuimg" src="cake.jpg">

                 <h3 style="text-decoration: 
                underline;">CAKE</h3><br>

                 White/Black Forest (Rs. 350 per pound): <input type="text" id="wbf"> <br/>

                  Cupcake (Rs. 30): <input type="text" id="cp"> <br/>


                  <img class="mnuimg" src="dnot.jpg">

                   <h3 style="text-decoration: 
                underline;">DONUT</h3><br>

                Chocolate Donut (Rs. 50): <input type="text" id="cd"> <br/>

                White chocolate donot (Rs. 70): <input type="text" id="wcd"> <br/>

                

                <img class="mnuimg" src="cdrink.jpg">

                  <h3 style="text-decoration: 
                underline;">COLD DRINKS</h3><br>

                 Coke/Dew/Spride/Slice (Rs. 50): <input type="text" id="cld"> <br/>

                  

            </fieldset>
        </div>
        
    </div>


    
<!--bill print garne code-->
    <style>
      @media print{
        /*hide every other body elemnts*/
        body *
        {
          visibility: hidden;
        }
        /*display print containner element*/
        .print-container, .print-container * {
          visibility: visible;
        }
        /*adjustion position*/
        .print-container{
          position: absolute;left:230px;top:0px;

      }

        }
        
    </style>


<div class="row print-container">
    <div class="container">
        <fieldset>
            <legend>Customer Bill</legend>
            <h3>Date:<span id="date1"></span></h3>
               <h3>Bill no:<span id="billno1"></span></h3>
              <h3>Admin id:<span id="namea3"></span></h3>
            <h3>Customer Name:<span id="name2"></span></h3>
            <h3>Customer Email: <span id="email2"></span></h3>
            <table border="1" >
                <thead>
                    <tr><th>Menu</th><th>Price</th><th>Quantity</th><th>Amout</th></tr>

                     
                </thead>

                <tbody id="bill">
               
                </tbody>

                
              
            </table>
             <p>Total Amout: Rs. <span id="amount">0</span></p><br>

         <div class="thankyou">
             <p style="font-size: 9px; color: red;">Thank you for visiting Newa Cafe</p>
               Phone : 9840353338/5538265
              <p><img style="width: 20px; height: 20px;" src="fb.png"> newacafe</p>   
              <p><img style="width: 20px; height: 20px;" src="ig.png"> newacafe123</p>
         </div>
            </fieldset>
           <CENTER><button onclick="window.print();">print bill</button></CENTER>
            
    </div>
    </div>
</div>



<script>
var cld = 30 , wcd = 30 , cp = 30 , cd = 50 , wbf = 350 , lbp = 700 , sbp = 450 , lcp = 600 ,  scp = 350 ,  coffee = 100 , cms = 50 , tea = 50 , icedcoffee = 110, expresso = 122, hotchocolate = 160, latte = 90;
var cld_q=0, wcd_q=0, cp_q=0,cd_q=0,   wbf_q=0,  lbp_q=0,  sbp_q=0, lcp_q=0, scp_q=0, coffee_q=0, cms_q=0, tea_q=0, icedcoffee_q=0, expresso_q=0, hotchocolate_q=0, latte_q=0;

var  name = "", email="",namea="",billno="",date="";

var cldBill="", wcdBill="", cdBill="", cpBill="",wbfBill="", lbpBill="", sbpBill="", lcpBill="", scpBill="", coffeeBill="", cmsBill="", teaBill="",icedcoffeeBill="",expressoBill="",hotchocolateBill="",latteBill="";

var total_amount=0;





document.getElementById("name").addEventListener("keyup",function(){
    
    
    document.getElementById("name2").innerHTML=this.value;
});

document.getElementById("email").addEventListener("keyup",function(){
   
    
    document.getElementById("email2").innerHTML=this.value;
});

document.getElementById("namea").addEventListener("keyup",function(){
    
    
    document.getElementById("namea3").innerHTML=this.value;
});

document.getElementById("billno").addEventListener("keyup",function(){
    
    
    document.getElementById("billno1").innerHTML=this.value;
});

document.getElementById("date").addEventListener("keyup",function(){
    
    
    document.getElementById("date1").innerHTML=this.value;
});

//setup garne parts

document.getElementById("cld").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    cldBill="";
    cld_q=0;
    showBill();
}else{
 cld_q=this.value;
  cldBill="<tr><td>(Coke/Dew/Spride/Slice)</td><td>Rs. "+cld+"</td><td>"+cld_q+"</td><td>"+cld+"x"+cld_q+" = "+cld*cld_q+"</td></tr>";
    showBill();

}
});

document.getElementById("wcd").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    wcdBill="";
   wcd_q=0;
    showBill();
}else{
 wcd_q=this.value;
   wcdBill="<tr><td>(White Chocolate Donut)</td><td>Rs. "+wcd+"</td><td>"+wcd_q+"</td><td>"+wcd+"x"+wcd_q+" = "+wcd*wcd_q+"</td></tr>";
    showBill();

}
});

document.getElementById("cd").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    cdBill="";
   cd_q=0;
    showBill();
}else{
 cd_q=this.value;
   cdBill="<tr><td>(Chocolate Donut)</td><td>Rs. "+cd+"</td><td>"+cd_q+"</td><td>"+cd+"x"+cd_q+" = "+cd*cd_q+"</td></tr>";
    showBill();

}
});

document.getElementById("wbf").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    wbfBill="";
   wbf_q=0;
    showBill();
}else{
  wbf_q=this.value;
   wbfBill="<tr><td>(Black/White Forest)</td><td>Rs. "+wbf+"</td><td>"+wbf_q+"</td><td>"+wbf+"x"+wbf_q+" = "+wbf*wbf_q+"</td></tr>";
    showBill();

}
});


document.getElementById("cp").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    cpBill="";
  cpp_q=0;
    showBill();
}else{
   cp_q=this.value;
   cpBill="<tr><td>(Cup Cake)</td><td>Rs. "+cp+"</td><td>"+cp_q+"</td><td>"+cp+"x"+cp_q+" = "+cp*cp_q+"</td></tr>";
    showBill();

}
});


document.getElementById("lbp").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    lbpBill="";
   lbp_q=0;
    showBill();
}else{
   lbp_q=this.value;
   lbpBill="<tr><td>(Large Buff Pizza)</td><td>Rs. "+lbp+"</td><td>"+lbp_q+"</td><td>"+lbp+"x"+lbp_q+" = "+lbp*lbp_q+"</td></tr>";
    showBill();

}
});


document.getElementById("sbp").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    sbpBill="";
   sbp_q=0;
    showBill();
}else{
   sbp_q=this.value;
   sbpBill="<tr><td>(Small Buff Pizza)</td><td>Rs. "+sbp+"</td><td>"+sbp_q+"</td><td>"+sbp+"x"+sbp_q+" = "+sbp*sbp_q+"</td></tr>";
    showBill();

}
});

document.getElementById("lcp").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    lcpBill="";
   lcp_q=0;
    showBill();
}else{
   lcp_q=this.value;
    lcpBill="<tr><td>(Large Chicken Pizza)</td><td>Rs. "+lcp+"</td><td>"+lcp_q+"</td><td>"+lcp+"x"+lcp_q+" = "+lcp*lcp_q+"</td></tr>";
    showBill();

}
});

document.getElementById("scp").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    scpBill="";
   scp_q=0;
    showBill();
}else{
   scp_q=this.value;
    scpBill="<tr><td>(Small Chicken Pizza)</td><td>Rs. "+scp+"</td><td>"+scp_q+"</td><td>"+scp+"x"+scp_q+" = "+scp*scp_q+"</td></tr>";
    showBill();

}
});



document.getElementById("coffee").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    coffeeBill="";
    coffee_q=0;
    showBill();
}else{
   coffee_q=this.value;
    coffeeBill="<tr><td>Coffee</td><td>Rs. "+coffee+"</td><td>"+coffee_q+"</td><td>"+coffee+"x"+coffee_q+" = "+coffee*coffee_q+"</td></tr>";
    showBill();

}
});


document.getElementById("tea").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    teaBill="";
    tea_q=0;
    showBill();
}else{
    tea_q=this.value;
    teaBill="<tr><td>Tea</td><td>Rs. "+tea+"</td><td>"+tea_q+"</td><td>"+tea+"x"+tea_q+" = "+tea*tea_q+"</td></tr>";
    showBill();

}
});

document.getElementById("cms").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    cmsBill="";
    cms_q=0;
    showBill();
}else{
   cms_q=this.value;
    cmsBill="<tr><td>Chocolate Milk Shake</td><td>Rs. "+cms+"</td><td>"+cms_q+"</td><td>"+cms+"x"+cms_q+" = "+cms*cms_q+"</td></tr>";
    showBill();

}
});


document.getElementById("tea").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    teaBill="";
    tea_q=0;
    showBill();
}else{
    tea_q=this.value;
    teaBill="<tr><td>Tea</td><td>Rs. "+tea+"</td><td>"+tea_q+"</td><td>"+tea+"x"+tea_q+" = "+tea*tea_q+"</td></tr>";
    showBill();

}
});

document.getElementById("icedcoffee").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    icedcoffeeBill="";
    icedcoffee_q=0;
    showBill();
}else{
    icedcoffee_q=this.value;
    icedcoffeeBill="<tr><td>Icedcoffee</td><td>Rs. "+icedcoffee+"</td><td>"+icedcoffee_q+"</td><td>"+icedcoffee+"x"+icedcoffee_q+" = "+icedcoffee*icedcoffee_q+"</td></tr>";
    showBill();

}
});

document.getElementById("expresso").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    expressoBill="";
    expresso_q=0;
    showBill();

}else{
    expresso_q=this.value;
   expressoBill="<tr><td>Expresso</td><td>Rs. "+expresso+"</td><td>"+expresso_q+"</td><td>"+expresso+"x"+expresso_q+" = "+expresso*expresso_q+"</td></tr>";
    showBill();
}
});

document.getElementById("hotchocolate").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    hotchocolateBill="";
    hotchocolate_q=0;
    showBill();

}else{
   hotchocolate_q=this.value;
    hotchocolateBill="<tr><td>Hotchocolate</td><td>Rs. "+hotchocolate+"</td><td>"+hotchocolate_q+"</td><td>"+hotchocolate+"x"+hotchocolate_q+" = "+hotchocolate*hotchocolate_q+"</td></tr>";
    showBill();
}
});

document.getElementById("latte").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    latteBill="";
    latte_q=0;
    showBill();

}else{
    latte_q=this.value;
    latteBill="<tr><td>Latte</td><td>Rs. "+latte+"</td><td>"+latte_q+"</td><td>"+latte+"x"+latte_q+" = "+latte*latte_q+"</td></tr>";
    showBill();
}
});

//function patr

function showBill(){
    document.getElementById("bill").innerHTML= cldBill+ wcdBill+ cdBill+  cpBill+  wbfBill+ lbpBill+ sbpBill+ lcpBill+  scpBill+ coffeeBill+ cmsBill+teaBill+icedcoffeeBill+expressoBill+hotchocolateBill+latteBill; //table statement

    document.getElementById("amount").innerHTML = wcd*wcd_q+ wcd*wcd_q+ cd*cd_q+ cp*cp_q+ wbf*wbf_q+ lbp*lbp_q+ sbp*sbp_q+ lcp*lcp_q+ scp*scp_q+  coffee*coffee_q+ cms*cms_q+ tea*tea_q+ icedcoffee*icedcoffee_q+expresso*expresso_q+hotchocolate*hotchocolate_q+latte*latte_q; // total amount
}
</script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="css/style.css">
    <style>
        h1{
            text-align: right;
        }

        img
        {
          margin: 20px;
        }
        button
        {
          color: white;
          border-radius:5px;
          border: 0px;
          background-color: green;
          width: 100px;
          height: 30px;
          margin: 5px;
  
        }
    </style>
</head>





<body>
<center><img  src="logo.png"></center><br><br>
 
<center><button
class="homebtn"  
onclick="window.location.href='startpage.html';"
>
    Home
    </button>
   
   <button
class="homebtn"  
onclick="window.location.href='admnoption.php';"
>
    Back
    </button>
</center>
      

<div class="container-fluid">
    <div class="container">
        <div class="part1">



            <fieldset>
                <legend>Bill Info</legend>
              Bill no: <input class="pinp" type="text" id="billno"> <br/>
               
              Date: <input class="pinp" type="text" id="date"  placeholder="mm/dd/yy"> <br/>
               
            </fieldset>

            <fieldset>
                <legend>Admin Information</legend>
              Admin id: <input class="pinp" type="text" id="namea"> <br/>

               
            </fieldset>

            <fieldset>
                <legend>Customer Information</legend>
                Full Name: <input class="pinp" type="text" id="name"> <br/>

                Your Email: <input class="pinp" type="text" id="email">
            </fieldset>
        </div>


        <div class="part2">
            <fieldset>
                <legend>Menu</legend>
                <img class="mnuimg" src="coffee.jpg">

                <h3 style="text-decoration: 
                underline;">HOT DRINKS</h3><br>

                Tea (Rs. 50): <input type="text" id="tea"> <br>

                Chocolate Milk Shake (Rs. 150): <input type="text" id="cms"> <br>

                Coffee (Rs. 100): <input type="text" id="coffee"> <br>

                Iced Coffee (Rs. 110): <input type="text" id="icedcoffee"> <br>

                expresso (Rs. 122): <input type="text" id="expresso"><br>

                Hot chocolate (Rs. 160): <input type="text" id="hotchocolate"><br>

                Latte (Rs. 90): <input type="text" id="latte"><br>


                <img class="mnuimg" src="pza.jpg">


                <h3 style="text-decoration: 
                underline;">PIZZA</h3><br>

                (small)Chicken Pizza (Rs. 350): <input type="text" id="scp"> <br/>
                (large)Chicken Pizza (Rs. 600): <input type="text" id="lcp"> <br/>
                (small)Buff Pizza (Rs. 450): <input type="text" id="sbp"> <br/>
                (large)Buff Pizza (Rs. 700): <input type="text" id="lbp"> <br/>

                 
                 <img class="mnuimg" src="cake.jpg">

                 <h3 style="text-decoration: 
                underline;">CAKE</h3><br>

                 White/Black Forest (Rs. 350 per pound): <input type="text" id="wbf"> <br/>

                  Cupcake (Rs. 30): <input type="text" id="cp"> <br/>


                  <img class="mnuimg" src="dnot.jpg">

                   <h3 style="text-decoration: 
                underline;">DONUT</h3><br>

                Chocolate Donut (Rs. 50): <input type="text" id="cd"> <br/>

                White chocolate donot (Rs. 70): <input type="text" id="wcd"> <br/>

                

                <img class="mnuimg" src="cdrink.jpg">

                  <h3 style="text-decoration: 
                underline;">COLD DRINKS</h3><br>

                 Coke/Dew/Spride/Slice (Rs. 50): <input type="text" id="cld"> <br/>

                  

            </fieldset>
        </div>
        
    </div>


    
<!--bill print garne code-->
    <style>
      @media print{
        /*hide every other body elemnts*/
        body *
        {
          visibility: hidden;
        }
        /*display print containner element*/
        .print-container, .print-container * {
          visibility: visible;
        }
        /*adjustion position*/
        .print-container{
          position: absolute;left:230px;top:0px;

      }

        }
        
    </style>


<div class="row print-container">
    <div class="container">
        <fieldset>
            <legend>Customer Bill</legend>
            <h3>Date:<span id="date1"></span></h3>
               <h3>Bill no:<span id="billno1"></span></h3>
              <h3>Admin id:<span id="namea3"></span></h3>
            <h3>Customer Name:<span id="name2"></span></h3>
            <h3>Customer Email: <span id="email2"></span></h3>
            <table border="1" >
                <thead>
                    <tr><th>Menu</th><th>Price</th><th>Quantity</th><th>Amout</th></tr>

                     
                </thead>

                <tbody id="bill">
               
                </tbody>

                
              
            </table>
             <p>Total Amout: Rs. <span id="amount">0</span></p><br>

         <div class="thankyou">
             <p style="font-size: 9px; color: red;">Thank you for visiting Newa Cafe</p>
               Phone : 9840353338/5538265
              <p><img style="width: 20px; height: 20px;" src="fb.png"> newacafe</p>   
              <p><img style="width: 20px; height: 20px;" src="ig.png"> newacafe123</p>
         </div>
            </fieldset>
           <CENTER><button onclick="window.print();">print bill</button></CENTER>
            
    </div>
    </div>
</div>



<script>
var cld = 30 , wcd = 30 , cp = 30 , cd = 50 , wbf = 350 , lbp = 700 , sbp = 450 , lcp = 600 ,  scp = 350 ,  coffee = 100 , cms = 50 , tea = 50 , icedcoffee = 110, expresso = 122, hotchocolate = 160, latte = 90;
var cld_q=0, wcd_q=0, cp_q=0,cd_q=0,   wbf_q=0,  lbp_q=0,  sbp_q=0, lcp_q=0, scp_q=0, coffee_q=0, cms_q=0, tea_q=0, icedcoffee_q=0, expresso_q=0, hotchocolate_q=0, latte_q=0;

var  name = "", email="",namea="",billno="",date="";

var cldBill="", wcdBill="", cdBill="", cpBill="",wbfBill="", lbpBill="", sbpBill="", lcpBill="", scpBill="", coffeeBill="", cmsBill="", teaBill="",icedcoffeeBill="",expressoBill="",hotchocolateBill="",latteBill="";

var total_amount=0;





document.getElementById("name").addEventListener("keyup",function(){
    
    
    document.getElementById("name2").innerHTML=this.value;
});

document.getElementById("email").addEventListener("keyup",function(){
   
    
    document.getElementById("email2").innerHTML=this.value;
});

document.getElementById("namea").addEventListener("keyup",function(){
    
    
    document.getElementById("namea3").innerHTML=this.value;
});

document.getElementById("billno").addEventListener("keyup",function(){
    
    
    document.getElementById("billno1").innerHTML=this.value;
});

document.getElementById("date").addEventListener("keyup",function(){
    
    
    document.getElementById("date1").innerHTML=this.value;
});

//setup garne parts

document.getElementById("cld").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    cldBill="";
    cld_q=0;
    showBill();
}else{
 cld_q=this.value;
  cldBill="<tr><td>(Coke/Dew/Spride/Slice)</td><td>Rs. "+cld+"</td><td>"+cld_q+"</td><td>"+cld+"x"+cld_q+" = "+cld*cld_q+"</td></tr>";
    showBill();

}
});

document.getElementById("wcd").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    wcdBill="";
   wcd_q=0;
    showBill();
}else{
 wcd_q=this.value;
   wcdBill="<tr><td>(White Chocolate Donut)</td><td>Rs. "+wcd+"</td><td>"+wcd_q+"</td><td>"+wcd+"x"+wcd_q+" = "+wcd*wcd_q+"</td></tr>";
    showBill();

}
});

document.getElementById("cd").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    cdBill="";
   cd_q=0;
    showBill();
}else{
 cd_q=this.value;
   cdBill="<tr><td>(Chocolate Donut)</td><td>Rs. "+cd+"</td><td>"+cd_q+"</td><td>"+cd+"x"+cd_q+" = "+cd*cd_q+"</td></tr>";
    showBill();

}
});

document.getElementById("wbf").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    wbfBill="";
   wbf_q=0;
    showBill();
}else{
  wbf_q=this.value;
   wbfBill="<tr><td>(Black/White Forest)</td><td>Rs. "+wbf+"</td><td>"+wbf_q+"</td><td>"+wbf+"x"+wbf_q+" = "+wbf*wbf_q+"</td></tr>";
    showBill();

}
});


document.getElementById("cp").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    cpBill="";
  cpp_q=0;
    showBill();
}else{
   cp_q=this.value;
   cpBill="<tr><td>(Cup Cake)</td><td>Rs. "+cp+"</td><td>"+cp_q+"</td><td>"+cp+"x"+cp_q+" = "+cp*cp_q+"</td></tr>";
    showBill();

}
});


document.getElementById("lbp").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    lbpBill="";
   lbp_q=0;
    showBill();
}else{
   lbp_q=this.value;
   lbpBill="<tr><td>(Large Buff Pizza)</td><td>Rs. "+lbp+"</td><td>"+lbp_q+"</td><td>"+lbp+"x"+lbp_q+" = "+lbp*lbp_q+"</td></tr>";
    showBill();

}
});


document.getElementById("sbp").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    sbpBill="";
   sbp_q=0;
    showBill();
}else{
   sbp_q=this.value;
   sbpBill="<tr><td>(Small Buff Pizza)</td><td>Rs. "+sbp+"</td><td>"+sbp_q+"</td><td>"+sbp+"x"+sbp_q+" = "+sbp*sbp_q+"</td></tr>";
    showBill();

}
});

document.getElementById("lcp").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    lcpBill="";
   lcp_q=0;
    showBill();
}else{
   lcp_q=this.value;
    lcpBill="<tr><td>(Large Chicken Pizza)</td><td>Rs. "+lcp+"</td><td>"+lcp_q+"</td><td>"+lcp+"x"+lcp_q+" = "+lcp*lcp_q+"</td></tr>";
    showBill();

}
});

document.getElementById("scp").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    scpBill="";
   scp_q=0;
    showBill();
}else{
   scp_q=this.value;
    scpBill="<tr><td>(Small Chicken Pizza)</td><td>Rs. "+scp+"</td><td>"+scp_q+"</td><td>"+scp+"x"+scp_q+" = "+scp*scp_q+"</td></tr>";
    showBill();

}
});



document.getElementById("coffee").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    coffeeBill="";
    coffee_q=0;
    showBill();
}else{
   coffee_q=this.value;
    coffeeBill="<tr><td>Coffee</td><td>Rs. "+coffee+"</td><td>"+coffee_q+"</td><td>"+coffee+"x"+coffee_q+" = "+coffee*coffee_q+"</td></tr>";
    showBill();

}
});


document.getElementById("tea").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    teaBill="";
    tea_q=0;
    showBill();
}else{
    tea_q=this.value;
    teaBill="<tr><td>Tea</td><td>Rs. "+tea+"</td><td>"+tea_q+"</td><td>"+tea+"x"+tea_q+" = "+tea*tea_q+"</td></tr>";
    showBill();

}
});

document.getElementById("cms").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    cmsBill="";
    cms_q=0;
    showBill();
}else{
   cms_q=this.value;
    cmsBill="<tr><td>Chocolate Milk Shake</td><td>Rs. "+cms+"</td><td>"+cms_q+"</td><td>"+cms+"x"+cms_q+" = "+cms*cms_q+"</td></tr>";
    showBill();

}
});


document.getElementById("tea").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    teaBill="";
    tea_q=0;
    showBill();
}else{
    tea_q=this.value;
    teaBill="<tr><td>Tea</td><td>Rs. "+tea+"</td><td>"+tea_q+"</td><td>"+tea+"x"+tea_q+" = "+tea*tea_q+"</td></tr>";
    showBill();

}
});

document.getElementById("icedcoffee").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    icedcoffeeBill="";
    icedcoffee_q=0;
    showBill();
}else{
    icedcoffee_q=this.value;
    icedcoffeeBill="<tr><td>Icedcoffee</td><td>Rs. "+icedcoffee+"</td><td>"+icedcoffee_q+"</td><td>"+icedcoffee+"x"+icedcoffee_q+" = "+icedcoffee*icedcoffee_q+"</td></tr>";
    showBill();

}
});

document.getElementById("expresso").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    expressoBill="";
    expresso_q=0;
    showBill();

}else{
    expresso_q=this.value;
   expressoBill="<tr><td>Expresso</td><td>Rs. "+expresso+"</td><td>"+expresso_q+"</td><td>"+expresso+"x"+expresso_q+" = "+expresso*expresso_q+"</td></tr>";
    showBill();
}
});

document.getElementById("hotchocolate").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    hotchocolateBill="";
    hotchocolate_q=0;
    showBill();

}else{
   hotchocolate_q=this.value;
    hotchocolateBill="<tr><td>Hotchocolate</td><td>Rs. "+hotchocolate+"</td><td>"+hotchocolate_q+"</td><td>"+hotchocolate+"x"+hotchocolate_q+" = "+hotchocolate*hotchocolate_q+"</td></tr>";
    showBill();
}
});

document.getElementById("latte").addEventListener("keyup",function(){
if(this.value==""||this.value==0){
    latteBill="";
    latte_q=0;
    showBill();

}else{
    latte_q=this.value;
    latteBill="<tr><td>Latte</td><td>Rs. "+latte+"</td><td>"+latte_q+"</td><td>"+latte+"x"+latte_q+" = "+latte*latte_q+"</td></tr>";
    showBill();
}
});

//function patr

function showBill(){
    document.getElementById("bill").innerHTML= cldBill+ wcdBill+ cdBill+  cpBill+  wbfBill+ lbpBill+ sbpBill+ lcpBill+  scpBill+ coffeeBill+ cmsBill+teaBill+icedcoffeeBill+expressoBill+hotchocolateBill+latteBill; //table statement

    document.getElementById("amount").innerHTML = wcd*wcd_q+ wcd*wcd_q+ cd*cd_q+ cp*cp_q+ wbf*wbf_q+ lbp*lbp_q+ sbp*sbp_q+ lcp*lcp_q+ scp*scp_q+  coffee*coffee_q+ cms*cms_q+ tea*tea_q+ icedcoffee*icedcoffee_q+expresso*expresso_q+hotchocolate*hotchocolate_q+latte*latte_q; // total amount
}
</script>
</body>
</html>

3.Admin list

<!DOCTYPE html>
<html>
<head>
	<style>
        body
        {
        	
        	
          background-image: url("img.jpg");
          
        }
        a
        {
          color: white;
        }

		table
		{
			margin-left: auto;
      margin-right: auto; 
		}

th {
  padding: 8px;
  text-align: left;
  border-bottom: 1px solid white;
  font-family: arial;

}
tr
{
  font-family: arial;
}
img
{
  margin: 20px;
}
button{
  color: white;

  
  border-radius:5px;
  border: 0px;
  background-color: green;
  width: 100px;
  height: 30px;
  margin: 5px;
}

 .fieldset1/*inner*/
    {
      width: 240px;
      height: 210px;
      border-radius:5px;
      color: white;
      font-family: Papyrus;
      border: none;
      opacity: 100;

    }
    fieldset/*outer*/
    {
      width: 240px;
      height: 250px;
      border-radius:5px;
      color: white;
      font-family: Papyrus;
      background-color: black;
      opacity: 0.7;
      border: 0px ;
    }
     
     legend
     {
      text-align: center;
     }
    .tbl_bckclr
    {
      background-color: black;
      width: 500px;
      height: 500px;
    }
	
	</style>
</head>



<body>
<center><img  src="logo.png"></center>

<center><br><br>
  
  <button
class="homebtn"  
onclick="window.location.href='startpage.html';">
    Home
    </button>

    <button
class="homebtn"  
onclick="window.location.href='admnoption.php';">
    Back
    </button>
</center><br><br>



<center>
  <fieldset><legend>Admin List</legend>
<fieldset class="fieldset1">
  
	<table   cellspacing="20">
		
		<tr>
	<th >aid  </th>
	<th>email  </th>
	<th> phone </th>
	<th> username </th>
	<th>password  </th>
  <th colspan="2">option</th>
       </tr>
     <?php
     
     $conn = mysqli_connect("localhost","root","","admn");
     if ($conn-> connect_error) {

     	die("connection failed:" . $conn-> connect_error);

     }

       $sql = "SELECT aid,email,phone,username,password from register" ;
       $result = $conn-> query($sql);
       if($result-> num_rows > 0)
       {
         while($row = $result-> fetch_assoc())
         {
         	echo "<tr>
          <td>".$row["aid"]."</td>
          <td>" .$row["email"]."</td>
          <td>" .$row["phone"]."</td>
          <td>" . $row["username"]."</td>
          <td>" .$row["password"]."</td>

        
          <td><a  href='editadmn.php?aid=$row[aid] & email=$row[email] & phone=$row[phone]& username=$row[username] '>edit</td>

          <td><a href='delet1.php?aid=$row[aid]'>delete</td>
          </tr> 

          ";
        
         }
         echo "</table>";
       }
       	  
       	  else
       	  {
       	  	echo "o result";

       	  }

       	  $conn-> close();
     ?>

	</table>
  </fieldset>
  </fieldset>
  
</center>
</body>
</html>


4.edit page

<html>
<head>
<style type="text/css">
	
body{
  background-image: url("img.jpg");
/*  background-color : #2E2E2E;*/
  background-size: cover;
  background-attachment: fixed;
}

input
  {
     border-radius: 15px;
        border: none;
        margin: 8px;
        width: 200px;
        height: 30px;
        text-align: center;
  }

  fieldset
    {
      width: 240px;
      height: 420px;
      border-radius:5px;
      color: white;
      font-family: Papyrus;
    }
  .edit
  {
  	width: 60px;
  	border-radius: 5px;
  	background-color: green;
  	color: white;
  }

  button
  {
  	color: white;

  
  border-radius:5px;
  border: 0px;
  background-color: green;
  width: 100px;
  height: 30px;
  margin: 5px;
  }

</style>

</head>
<body>


<?php
include("connect1admn.php");
error_reporting();
$aid=$_GET['aid'];
$email=$_GET['email'];
$phone=$_GET['phone'];
$username=$_GET['username'];
$password=$_GET['password'];
//matiko code chai workerlist ko value edit page ma launako lagi banako


?>


<center><img  src="logo.png"></center><br><br>

<center><button
class="homebtn"  
onclick="window.location.href='startpage.html';">
    Home
    </button>

    <button
class="homebtn"  
onclick="window.location.href='admnlist.php';">
    Back
    </button></center><br>

<CENTER>
  <fieldset>
    <legend>Update/Edit Admin</legend>
  
   <form method="GET" >

ID:<br><input type="text" name="aid" value="<?php echo $aid; ?>"><br>

Email:<input type="text" name="email" value="<?php echo $email; ?>"><br>

Phone:<input type="text" name="phone" value="<?php echo $phone; ?>"><br>

Username:<input type="text" name="username" value="<?php echo $username; ?>"><br>
 password:<input type="text" name="password" value="<?php echo $password; ?>"><br>           
<input type="submit" name="edit" class="edit" value="Done"> 


      


       </form>
</fieldset></CENTER>
</body>
</html>


<?php
#databaseconnection for conn
$db_host = 'localhost';
   $db_user = "root";
   $db_password = "";
   $db_databasename = "admn";

   $conn = new mysqli($db_host,$db_user,$db_password,$db_databasename);
      
#edit page ko value worker list ma apthaunako lagi code
if($_GET['aid'])
{
  $aid=$_GET['aid'];
$email=$_GET['email'];
$phone=$_GET['phone'];
$username=$_GET['username'];
$password=$_GET['password'];
$query = "UPDATE register SET aid='$aid',email='$email',phone='$phone',username='$username',password='$password' WHERE aid='$aid'";


$data = mysqli_query($conn,$query);

if ($data) {
	echo "<script>alert('record updated')</script>";
}
else
{
	echo "<script>alert('fail to update record ')</script>";
}
}
?>

5.Delet button 
<?php
  
  include("connect_a_list.php");
  error_reporting(0);
  $aid = $_GET['aid'];
  echo $query = "DELETE FROM register WHERE AID = '$aid'";
  $data = mysqli_query($conn,$query);

  if($data)
  {
  	echo "record deleted";
  }

  else
  {
  	echo "faild to delet record";
  }

?>

<a href="admnlist.php"> Adminlist</a>

