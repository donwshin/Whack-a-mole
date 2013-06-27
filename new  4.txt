<!DOCTYPE HTML>
<html>
  <head>
	<title>Paul</title>
</head>
    <style>
      body {
        margin: 0px;
        padding: 0px;
      }
    </style>
  </head>
  <body>
    <canvas id="myCanvas" width="480" height="800" style="border:1px solid #000000;"></canvas>
    <script>
	
      var canvas = document.getElementById('myCanvas');
      var context = canvas.getContext('2d');
	  setInterval(loop,1000/60);//run loop fnctn every 1000/60 ms
      var imgBG = new Image();
	  var imgMole = new Image();
	  var imgipad = new Image();
	  var imgsofa = new Image();
	
      imgBG.onload = function() {
        context.drawImage(imgBG, 0, 0, 480, 800);
        //context.drawImage(imgMole, 100, 100, 80, 80);
      };
      imgBG.src = 'http://fotobg.ru/upload/img1347871094.jpg';
	 imgipad.src = 'ipad.jpg';
      imgMole.src = 'Mole.png';
	  imgsofa.src = 'sofa.jpg';
	  
	  

			
	var Items=function (images) {
		this.img = images;
		this.x = (Math.random()*(390)+90);//parameter for x
		this.y = (Math.random()*(770)+30);//parameter for y
		this.t = Math.random()*(50);
		this.update = function() {
			this.t -= 1;
		};
		this.draw = function() {
			context.drawImage(this.img,this.x,this.y);
		};
	}
	
	//randomly move the icon
	  var Moles=new Array(); 
			Moles[0]= new Items(imgipad);       
			Moles[1]= new Items(imgMole);
			Moles[2]= new Items(imgsofa);
	
	var test = new Items();
	
	function update()
	{
		for(var i = 0; i <= 2; i++)
		{
			Moles[i].update();
			if (Moles[i].t < 0)
				Moles[i] = new Items(Moles[i].img);
		}
	}
	
	//moves the icon randomly across the screen
	function draw()
	{
		context.clearRect(0,0,480, 800);
		context.drawImage(imgBG, 0, 0, 480, 800);
		
		Moles[0].draw();
		Moles[1].draw();
		Moles[2].draw();
	}
	function loop(){
		update();
		draw();	
	}


	  //http://fotobg.ru/upload/img1347871094.jpg in game background
//http://wallpapers-diq.org/wallpapers/12/Industrial_Octane_8.jpg 
//http://us.123rf.com/400wm/400/400/arquiplay77/arquiplay770904/arquiplay77090400071/4767327-grunge-background-of-an-interior-concrete-room.jpg	  
//http://modblackmoon.narod.ru/wallp/MB-Sector712_HD.jpg -->
	

    </script>
  </body>
</html>
