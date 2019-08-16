% Machine Learning, Deep Learning and Reinforcement Learning
<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[常用算法](https://www.atatech.org/articles/86277)  
[500 Questions](https://github.com/scutan90/DeepLearning-500-questions)  
[Reinforcement Learning](https://github.com/dennybritz/reinforcement-learning)  
[UCL Course on RL](http://www0.cs.ucl.ac.uk/staff/d.silver/web/Teaching.html)  
[Reinforcement Introduction](http://incompleteideas.net/book/RLbook2018.pdf)


# Machine Learning Topics #

## 定义 ##

> A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance
> on T, as measured by P, improves with experience E.
> by Tom Mitchell

## 数学基础 ##

### 机器学习基础 ###
机器学习的分类与一般思路

### 微积分基础 ###
泰勒公式，导数与梯度

### 概率与统计基础 ###
概率公式，常见分布，常见统计量

### 线性代数基础 ###
矩阵乘法的几何意义

## Libs & Frameworks ##

1. NumPy (Numerical Python)
   Belongs to [SciPy Stack].

2. SciPy

3. Pandas

4. Matplotlib

5. Seaborn

6. Bokeh

7. Plotly

* Machine Learning
1. SckKit-Learn

* Deep Learning
1. Keras
2. TensorFlow
3. PyTorch
4. FastAI
5. Theano
   I think I say roughly /θi.ˈæ.noʊ/ (using the international phonetic alphabet), or /te.ˈaː.no/ when
   speaking Dutch, which is my native language. I guess the latter is actually closer to the original Greek pronunciation :)
   维基发音：
   Theano (/θɪˈænoʊ/; Greek: Θεανώ; fl. 6th-century BC), or Theano of Crotone,[1] is the name given to perhaps two Pythagorean philosophers.

## Keras ##



# octave #

## move data ##

``` octave
who  % print all the variables in the current context
whos % print all the variables and values in the current context
clear [var name]%
save hello.txt v -ascii

matrix(row, col)
matrix(:, col)  % all the elements of col
matrix(row, :)  % all the elements of row
A = [A [101; 102; 103]] % append column vector into matrix A
matrix(:) % print all elements of A into a single vector

A = [1 2 ; 3 4 ; 5 6]
B = [11 12 ; 13 14 ; 15 16]
C = [A B]
D = [A ; B]
```

## compute data ##

``` octave
A = [1 2; 3 4; 5 6]
B = [11 12; 13 14; 15 16]
C = [1 1; 2 2]

A * C
A .* B
A .^ 2

V = [1; 2; 3]
V + ones(3, 1)
A' % transpose

a = [3 15 2 0.5]
max(a)
[val ind] = max(a)
a < 3

find(a < 3)

A = magic(3)
[r, c] = find(A >= 7)
sum(a)
prod(a) % product
floor(a)
ceil(a)

A = rand(3)
B = rand(3)
max(A, B)

max(A, [], 1) % take the column-wise maximum
max(A, [], 2) % take the row-wise maximum
max(max(A))
max(A(:))

flipud(eye(9)) % flip array up side down
```

``` octave
t = [0:0.01:0.98];
y1 = sin(2*pi*4*t);
y2 = cos(2*pi*4*t);
plot(t, y1)
plot(t, y2)
hold on;

xlabel('time')
ylabel('value')
legend('sin', 'cos')
title('my plot')
cd ~/Downloads; print -dpng 'myPlot.png'


figure(1); plot(t, y1);
figure(2); plot(t, y2);

subplot(1, 2, 2); % divides plot a 1x2 grid access first element

imagesc(magic(15))
```

## control flow ##

``` octave
for i=1:10
    v(i) = 2^i;
end;

i = 1;
while i <= 5,
    v(i) = 100;
    i = i+1;
    if i == 6,
        break;
    end;
end;

if v(1) == 1,
    disp('The value is one');
elseif v(1) == 2,
    disp('The value is two');
else
    disp('The value is not one or two');
end;

```

## vectorization ##

[Machine Learning Road Map](https://github.com/clone95/Virgilio)
