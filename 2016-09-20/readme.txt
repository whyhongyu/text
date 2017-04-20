笔记
============================================================
	变形
		操作的都是画布。
		原点永远都是画布的左上角



		rotate(弧度) 					旋转
		translate(x,y)				平移
		scale(x,y) 					缩放


		gd.save() 				保存画布当前状态
		gd.restore() 			还原到保存的状态

		流程：
			gd.save()
				操作
				画图
			gd.restore()

============================================================
	导出图片
		var result = oC.toDataURL(Mime-Type);
									image/png 		默认
									image/jpeg
		result 		Base64

	背景平铺
		var cp = gd.createPattern(oImg,平铺方式);
								repeat
								repeat-x
								repeat-y
								no-repeat

	导入外部图片
		gd.drawImage(
			oImg,
			dx,dy,dw,dh
		);

		gd.drawImage(
			oImg,
			sx,sy,sw,sh ,
			dx,dy,dw,dh
		);

	像素级操作
		计算机图形学
		非常耗费性能
		需要放在服务器环境下

		var result = gd.getImageData(x,y,w,h);
		result.data 		所有的像素的数组
			四个为一组
				r 		g 		b 		a

		gd.putImageData(result,0,0);

	效果
		复古效果：
		    d[i]=(r*0.393)+(g*0.769)+(b*0.189); 	// red
		    d[i+1]=(r*0.349)+(g*0.686)+(b*0.168); 	// green
		    d[i+2]=(r*0.272)+(g*0.534)+(b*0.131); 	// blue
		红色蒙版效果：
		    d[i]=(r+g+b)/3;        // 红色通道取平均值
		    d[i+1]=d[i+2]=0;  		// 绿色通道和蓝色通道都设为0

		图片曝光(高亮效果)：
		    d[i]+=200;
		    d[i+1]+=200;
		    d[i+2]+=200;
		颜色反转：
		    d[i]=255-d[i];
		    d[i+1]=255-d[i+1];
		    d[i+2]=255-d[i+2];
=======================================================
	像素级操作尽量少来，是在太耗性能。
=======================================================
	捕鱼达人
		*面向对象
		*canvas的玩法
=======================================================
	面向对象
		继承
			属性
				父类.call(this,arg,arg,....);
				或
				父类.apply(this,arguments);
			方法
				子类.prototype = new 父类();
				子类.prototype.constructor = 子类;
=======================================================
	游戏
		运营+策划
		UI
=======================================================
	





















