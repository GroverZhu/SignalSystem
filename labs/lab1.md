# 信号与系统

## 1.2 离散时间正弦信号   

>基本题(a)(b)(c)   

(a) $M=4$, 基波周期为3   
```m
n=[0:23];
N=12;
M=4;
x=sin(2*pi*n*M/N);
stem(n,x);
title('x=sin(2*pi*M*n/N),M=4');
xlabel('n(samples)');
ylabel('x[n]')
```

$M=5$,基波周期为12   
```m
n=[0:23];
N=12;
M=5;
x=sin(2*pi*n*M/N);
stem(n,x);
title('x=sin(2*pi*M*n/N),M=5');
xlabel('n(samples)');
ylabel('x[n]')
```

$M=7$,基波周期为12   
```m
n=[0:23];
N=12;
M=7;
x=sin(2*pi*n*M/N);
stem(n,x);
title('x=sin(2*pi*M*n/N),M=7');
xlabel('n(samples)');
ylabel('x[n]')
```

$M=10$，基波周期为6   
```m
n=[0:23];
N=12;
M=10;
x=sin(2*pi*n*M/N);
stem(n,x);
title('x=sin(2*pi*M*n/N),M=7');
xlabel('n(samples)');
ylabel('x[n]')
```

对于任意的$M,N$的值，首先令$M'=M%N$，之后求出$M$与$N$的最小公倍数$K$，那么基波周期$T=K/M'$。当$M$大于$N$且最大公约数为$N$时，基波周期为1.

(b)   
```m
n=[1:8];
i=1;
for k=[1 2 4 6]
    x=sin(2*pi*k*n/5);
    subplot(2,2,i);
    stem(n,x,'fill')
    title(['x=sin(2*pi*k*n/5),k=',num2str(k)]);
    xlabel('n(samples)');
    ylabel('x[n]');
    i=i+1;
end;
```

其中$K=1$和$K=6$的信号图像相同，$K=2$和$K=4$的图像信号唯一。$K=1$和$K=6$的信号图像相同的原因是因为$K$的值相差5之后，两信号有了$\pi$的相位差，而在振幅和周期上一致，成为了完全相同的信号。

(c)
信号$x_1 [n]$是周期的，周期为$12$   
```m
n=[0:24];
x1=cos(2*pi*n/6)+2*cos(3*pi*n/6);
stem(n,x1);
title('x1[n]=cos(2*pi*n/6)+2*cos(3*pi*n/6)');
xlabel('n(samples)');
ylabel('x[n]');
```

信号$x_2 [n]$不是周期的，因为$\frac{2\pi}{1/3}$是无理数   
```m
n=[0:24];
x2=2*cos(2*n/6)+cos(3*n/6);
stem(n,x2);
title('x1[n]=2*cos(2*n/6)+cos(3*n/6)');
xlabel('n(samples)');
ylabel('x[n]');
    
```
信号$x_3[n]$是周期的，周期为24


```m
n=[0:48];
x3=cos(2*pi*n/6)+3*cos(5*pi*n/12);
stem(n,x3);
title('x3=cos(2*pi*n/6)+3*cos(5*pi*n/12)');
xlabel('n(samples)');
ylabel('x[n]');
```
可以得出：当$\frac{2\pi}{\omega_0}$ 为无理数时，该信号不是周期的。

## 1.3 离散时间信号时间变量的变换   

>基本题(a)(b)(c)   

(a)
```m
n=[-3:7];
x=zeros(1,11);
x(4)=2;
x(6)=1;
x(7)=-1;
x(8)=3;
stem(n,x);
xlabel('n')
ylabel('x[n]')
```
(b)
```m
n=[-3:7];
x=zeros(1,11);
x(4)=2;
x(6)=1;
x(7)=-1;
x(8)=3;
stem(n,x);
xlabel('n');
ylabel('x[n]');
n1=n-2;
n2=n+1;
n3=-n;
n4=-n+1;
```

(c)
```m
n=[-3:7];
x=zeros(1,11);
x(4)=2;
x(6)=1;
x(7)=-1;
x(8)=3;
n1=n-2;
n2=n+1;
n3=-n;
n4=-n+1;
stem(n1,x);
%stem(n2,x);
%stem(n3,x);
%stem(n4,x);
title('y1[n]=x[n-2]')
xlabel('n')
ylabel('y1[n]')
```

1. $y_1 [n]$信号是$x[n]$信号的延时2；
2. $y_2 [n]$信号是$x[n]$信号的超前1；
3. $y_3 [n]$信号是$x[n]$信号的倒置；
4. $y_4 [n]$信号是$x[n]$信号的超前1后倒置。

## 1.4 离散时间系统性质   

>基本题(a)(b)   

(a)

```m
n=[0:15];
x1=[1 zeros(1,15)];
x2=2*[1 zeros(1,15)];
y1=sin((pi/2)*x1);
y2=sin((pi/2)*x2);
x3=x1+x2;
y3=sin((pi/2)*x3);
y4=y1+y2;
%stem(n,y3);
%title('y3=sin(pi/2*x3)');
stem(n,y4);
title('y4=sin(pi/2*x4)')
xlabel('n');
ylabel('y');
```

如果系统是线性的，那么$y_3$与$y_4$两个信号所显示的图应该是完全相同的，所以该系统不是线性。   

(b)   
```m
x=[zeros(1,5) ones(1,10)];
x0=[zeros(1,4) ones(1,11)];
n1=[-5:9];
n2=[-6:9];
x1=[0 x];
x2=[0 x0];
y=x1+x2;
%stem(n1,x);
%title('x[n]')
%stem(n1,x0);
%title('x[n+1]');
stem(n2,y);
title('y[n]=x[n]+x[n+1]');
xlabel('x');
ylabel('x[n]');
```

由上图可知，当$n=-1$时，$y[n]=1$，其值由$x[-1]$和$x[0]$共同决定，故该系统违反了因果性，为非因果系统。

## 1.6 连续时间复指数信号   

>基本题(a)(b)   

(a)   
```m
x=sym('sin(2*pi*t/T)');
x5=subs(x,'T',5);
ezplot(x5,[0,10]);
```

(b)   
```m
x=sym('cos(2*pi*t/T)');
y=sym('2*pi*t/T');
z=x*y;
z4=subs(x,'T',4);
z8=subs(x,'T',8);
z16=subs(x,'T',16);
subplot(2,2,1);
ezplot(z4,[0,32]);
title('T=4');
subplot(2,2,2);
ezplot(z8,[0,32]);
title('T=8');
subplot(2,2,3);
ezplot(z16,[0,32]);
title('T=16');
```

因为$x(t)$是正弦信号，周期$T$增大，频率$f$减小，所以信号变稀疏。$x(t)$的基波周期是$T/2$。

## 1.7 连续时间信号时间变量的变换   

>基本题(a)(b)   

(a)   
```m
syms f t;
f=t*(heaviside(t)-heaviside(t-2));
ezplot(f,[-4,4]);
title('f(t)=t*(u(t)-u(t-2))');
xlabel('t');
ylabel('f(t)');
```

(b)   
```m
syms f t;
f=t*(heaviside(t)-heaviside(t-2));
g1=subs(f,'t','-t');
g2=subs(f,'t','t+1');
g3=subs(f,'t','t-3');
g4=subs(f,'t','-t+1');
g5=subs(f,'t','-2*t+1');
subplot(3,2,1);
ezplot(f,[-4,4]);
title('f(t)=t*(u(t)-u(t-2))');
subplot(3,2,2);
ezplot(g1,[-4,4]);
title('g1(t)=f(-t)');
subplot(3,2,3);
ezplot(g2,[-4,4]);
title('g2(t)=f(t+1)');
subplot(3,2,4);
ezplot(g3,[-4,4]);
title('g3(t)=f(t-3)');
subplot(3,2,5);
ezplot(g4,[-4,4]);
title('g4(t)=f(-t+1)');
subplot(3,2,6);
ezplot(g5,[-4,4]);
title('g5(t)=f(-2*t+1)');
```

1. $g_1 (t)$是$f(t)$以$t=0$为轴反转得到的；
2. $g_2 (t)$是$f(t)$超前1得到的；
3. $g_3 (t)$是$f(t)$延时3得到的；
4. $g_4 (t)$是$f(t)$先超前1后以t=0为轴反转得到的；
5. $g_5 (t)$是$f(t)$先超前1后以t=0为轴反转最后压缩为原来的$1/2$得到的。


## 1.8 连续时间信号的能量和功率   

>基本题(a)(b)   

(a)
```m
x1=sym('cos(pi*t/5)');
x2=sym('sin(pi*t/5)');
x3=sym('(exp(2*pi*t*i/3)+exp(i*pi*t))');
```

(b)
```m
x1=sym('cos(pi*t/5)');
x2=sym('sin(pi*t/5)');
x3=sym('(exp(2*pi*t*i/3)+exp(i*pi*t))');
subplot(2,2,1);
ezplot(x1,[0,20]);
title('x1(t)=cos(pi*t/5)');
xlabel('0<=t<=20');
ylabel('x1(t)');
subplot(2,2,2);
ezplot(x2,[0,20]);
title('x2(t)=sin(pi*t/5)');
subplot(2,2,3);
ezplot(real(x3),[0,12]);
title('real(x3(t))=real(exp(2*pi*t*i/3)+exp(i*pi*t))');
xlabel('0<=t<=12');
ylabel('real(x3(t))');
subplot(2,2,4);
ezplot(imag(x3),[0,12]);
title('imag(x3(t))=imag(exp(2*pi*t*i/3)+exp(i*pi*t))');
xlabel('0<=t<=12');
ylabel('imag(x3(t))');
```