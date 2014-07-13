##碰撞检测
1：用间距进行检测
2：用像素进行检测
![hit](http://cssbird.github.io/images/hit.png)

```js
c.clearRect(0,0,canvas.width,canvas.height);
				c.globalCompositeOperation = 'xor';
				SpriteA.draw();
				SpriteB.draw();

				var data = c.getImageData(SpriteB.x,SpriteB.y,SpriteB.w,SpriteB.h).data;

				c.clearRect(0,0,canvas.width,canvas.height);
				c.globalCompositeOperation = 'source-over';
				SpriteB.draw();

				var data2 = c.getImageData(SpriteB.x,SpriteB.y,SpriteB.w,SpriteB.h).data;
				//c.globalCompositeOperation = 'source-over';
				//c.clearRect(0,0,canvas.width,canvas.height);
				SpriteA.draw();
				//SpriteB.draw();
				for(var i = 3; i < data.length; i += 4){
					c.clearRect(100,100,90,90);
					//c.fillText(data[i],110,150);
					if(data[i]==0&&data2[i]>0){
						c.fillText("hit",110,150);
						break;
					}
				}
```
