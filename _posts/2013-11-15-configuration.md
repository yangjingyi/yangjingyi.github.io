---
layout: post
title: C--Introduction and programming examples
categories: [general, setup, demo]
tags: [C--, C#, Digital Image Processing]
fullview: true
---

# 简介C--及下载
首先介绍一下C--， 这是基于C#的一种语言，可以简单的导入图片并进行处理，下载exe文件链接：
[pan.baidu.com/s/1i34Ksqp](http://pan.baidu.com/s/1i34Ksqp)
# 简单程序实现
### C--导入图片
只用一小段程序就能实现导入图片啦~
'void main(){
	byte[,] f = LoadImg();
	ShowImg("f",f);
}'
### C--实现图像的算术运算
#### Addition
'byte[,] add(byte[,] f1, byte[,] f2){
	int w = f1.GetLength(0);
	int h = f1.GetLength(1);
	byte[,] g = new byte[w,h];
	for(int y = 0; y<h;y++)
	    for(int x = 0;x<w;x++){
		g[x,y] = (byte)(f1[x,y] + f2[x,y]);
	}
	return g;
}
void main(){
	byte[,] f1 = LoadImg();
	byte[,] f2 = LoadImg();
	ShowImg("f1",f1);
	ShowImg("f2",f2);
	ShowImg("Addition",add(f1,f2));
}'
其中尤其*byte*不能少，因为要强制转换类型double到byte


#### Subtraction
'byte[,] sub(byte[,] f1, byte[,] f2){
	int w = f1.GetLength(0);
	int h = f1.GetLength(1);
	byte[,] g = new byte[w,h];
	for(int y = 0; y<h;y++)
	    for(int x = 0;x<w;x++){
		g[x,y] = (byte)(f1[x,y] - f2[x,y]);
	}
	return g;
}
void main(){
	byte[,] f1 = LoadImg();
	byte[,] f2 = LoadImg();
	ShowImg("f1",f1);
	ShowImg("f2",f2);
	ShowImg("Subtraction",sub(f1,f2));
}'
#### Multiplition
'byte[,] mul(byte[,] f1, byte[,] f2){
	int w = f1.GetLength(0);
	int h = f2.GetLength(1);

	byte[,] g = new byte[w,h];

	for(int y = 0;y<h;y++)
		for(int x = 0;x<w;x++)
			g[x,y] = (byte)(f1[x,y] * f2[x,y] / 255);
	return g;
}

void testMul(){
	byte[,] f1 = LoadImg();
	byte[,] f2 = LoadImg();
	ShowImg("f1",f1);
	ShowImg("f2",f2);
	ShowImg("f1*f2",mul(f1,f2));
}

void main(){
	testMul();
}'
#### Division
'byte[,] div(byte[,] f1, byte[,] f2){
	int w = f1.GetLength(0);
	int h = f2.GetLength(1);

	byte[,] g = new byte[w,h];

	for(int y = 0;y<h;y++)
		for(int x = 0;x<w;x++)
			g[x,y] = (byte)(f1[x,y] * f2[x,y] / 255);
	return g;
}

void testDiv(){
	byte[,] f1 = LoadImg();
	byte[,] f2 = LoadImg();
	ShowImg("f1",f1);
	ShowImg("f2",f2);
	ShowImg("f1/f2",div(f1,f2));
}

void main(){
	testDiv();
}'
#### Effect
'byte[,] createLightEffect(int w,int h){
	byte[,] g = new byte[w,h];

	for(int y = 0;y<h;y++)
		for(int x = 0;x<w;x++){
			double d = Sqrt((x-w/2)*(x-w/2) + (y-h/2)*(y-h/2));
			g[x,y] = S((255-d/(w/2)*127));
	}
	return g;
}

byte S(double v){
	if(v>255) return 255;
	if(v<0) return 0;
	else return (byte)(v);
}

void testEffect(){
	ShowImg("Effect",createLightEffect(256,256));
}'
