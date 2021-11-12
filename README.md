# PICO-8-Joystick
Joystick + Pico8 + HTML

*using google translate*
![alt text](https://www.lexaloffle.com/bbs/files/35039/Screenshot_2019-02-24-10-51-30.png)

I received a lot of feedback from the previous project, regarding whether it is possible to add a joystick so I got down to work to see if we can do this and not die trying.

What do we need:
- Read the awesome article by Eugene Andruszczenko(https://github.com/32teeth/html5-plugin-canvas-gamepad).
- Your PICO-8 html cartridge (html and js).

Now a quick lesson of what we are doing:

- 1) Adding the buttons (I add the info on .js of the game):

`YOUR_GAME.js`

```
CanvasGamepad.setup({
	start:false,
	buttons:[
		{name:"jump"}
	]
});
```

- 2) Mapping our controller detection on the game.js (you can found the complete code at the end of this article).
This is the line that make the magic:

`game.js`

```
//buttons

                if(map["a"] == 1){SimulateKey(90);}
		if(map["b"] == 1){SimulateKey(88);}
		if(map["x"] == 1){SimulateKey(88);}
		if(map["y"] == 1){SimulateKey(90);}

//joystick
		if(x == 0 && y == 0){
		SimulateKeyUp(37);SimulateKeyUp(38);SimulateKeyUp(39);SimulateKeyUp(40);
		}
		if(x == -1 && y == 0){
			SimulateKey(37);//btn-left
		SimulateKeyUp(38);SimulateKeyUp(39);SimulateKeyUp(40);
		}
		if(x == 1 && y == 0){
			SimulateKey(39);//btn-right
		SimulateKeyUp(37);SimulateKeyUp(38);SimulateKeyUp(40);
		}
		if(x == 0 && y == -1){
			SimulateKey(38);//btn-down 
		SimulateKeyUp(37);SimulateKeyUp(40);SimulateKeyUp(39);
		}
		if(x == 0 && y == 1){
			SimulateKey(40);//btn-up
		SimulateKeyUp(37);SimulateKeyUp(39);SimulateKeyUp(38);
		}
		if(x == -1 && y == 1){
			
		SimulateKey(37);//btn-left
		SimulateKey(40);//btn-down
		
		SimulateKeyUp(38);SimulateKeyUp(39);
		}
		if(x == -1 && y == -1){
			
		SimulateKey(37);//btn-left
		SimulateKey(38);//btn-down
		
		SimulateKeyUp(39);SimulateKeyUp(40);
		}
		if(x == 1 && y == 1){
			
		SimulateKey(39);//btn-right
		SimulateKey(40);//btn-up
		
		
		SimulateKeyUp(37);SimulateKeyUp(38);
		}
		if(x == 1 && y == -1){
			
		SimulateKey(39);//btn-right
		SimulateKey(38);//btn-down
		
		SimulateKeyUp(37);SimulateKeyUp(40);
		}
```
 
- 3) calling some extra buttons (START button):

```
if(map["start"] == 1 && banner == false)
		{
			banner = true;
			Module.pico8TogglePaused();
			
                        //I sent a signal to my "Android" app to show an ad.
                        //Android.startRewardVideoAndroidFunction("");
			
		}

```

You.- Dude, i´m really don't care about this chit chat.
Me .- Ok, ok, I leave my code so you can steal it [![ko-fi](https://www.ko-fi.com/img/donate_sm.png)](https://ko-fi.com/V7V1R1YJ)
(you only need to changes your YOUR_GAME.js and read step one on this article only to be sure you get it).



Let me know what you think!!!!!!
