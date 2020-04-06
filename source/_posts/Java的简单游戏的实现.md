---
title: Java的简单游戏的实现
top: false
toc: true
cover: false
tags: [Java, Game]
mathjax: false
date: 2020-04-04 13:39:09
categories: Java
summary: 一次对于Java的愉快体验
urlname: java-new-game
---

## 游戏开始
代码如下：
```java
import java.awt.*;
import javax.swing.*;

public class BallGame extends JFrame {
	Image ball = Toolkit.getDefaultToolkit().getImage("images/ball.png");
	Image desk = Toolkit.getDefaultToolkit().getImage("images/table.jpg");
	
	double x = 200;
	double y = 200;
	double digree = 3.14/3;
	
	//绘画
	public void paint(Graphics g){
		System.out.println("Graphic is ready!!!");
		g.drawImage(desk,0,0,null);
		g.drawImage(ball,(int)x,(int)y,null);
		//用到数学知识的地方
		x = x + 10 * Math.cos(digree);
		y = y + 10 * Math.sin(digree);
		
		//碰到上下左右边界
		if (y > 501-40-30 || y < 40+40) {
			digree = -digree;
		}
		if (x>856-40-30 || x < 40) {
			digree = 3.14 - digree;
		}
	}
	
	//创建窗口
	void launchFrame(){
		setSize(856,501);
		setLocation(100,100);
		setVisible(true);
		
		//实现动画，每秒绘制25次
		while (true) {
			repaint();
			try {
				Thread.sleep(40);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}  //1s=1000ms,大约1秒绘制1000/40=25
		}
	}
	
	public static void main(String args[]){
		System.out.println("Game is on!!!");
		
		BallGame game = new BallGame();
		game.launchFrame();
	}
}
```
大家尽量手敲代码哦~

## 后记
需要的图片：
![ball.png](https://hanhantuanblogimages.oss-cn-beijing.aliyuncs.com/blog_img/ball.png)
![table.jpg](https://hanhantuanblogimages.oss-cn-beijing.aliyuncs.com/blog_img/table.jpg)
程序参考：<https://www.sxt.cn/Java_jQuery_in_action/Billiards_Games.html>