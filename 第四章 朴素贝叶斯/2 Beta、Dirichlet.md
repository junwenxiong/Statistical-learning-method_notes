# Beta、Dirichlet


## 1、$\Gamma$函数
$\Gamma$函数是阶乘在实数上的推广，定义为：

$$\Gamma(x) = \int_{0}^{+\infty} t^{x-1} e^{-t} \ dt$$
$\Gamma$函数的性质：

$$\Gamma(x+1) = x \Gamma(x)$$
$$\Gamma(n) = (n-1)!$$

## 2、Gamma分布
根据$\Gamma$函数的定义有：

$$\large{\int_{0}^{+\infty} \frac{x^{\alpha-1}e^{-x}}{\Gamma(\alpha)}\ dx = 1 \ \ \ \ \ \ (*)}$$

若将公式($*$)中的$x$替换为$\beta t$，则有下式成立：

$$\large{\int_{0}^{+\infty} \frac{(\beta t)^{\alpha-1}e^{-\beta t}}{\Gamma(\alpha)}\ d(\beta t) = 1}$$

等价于：

$$\large{\int_{0}^{+\infty} \frac{\beta^{\alpha} t^{\alpha-1}e^{-\beta t}}{\Gamma(\alpha)}\ dt = 1 \ \ \ \ \ \ 
(**)}$$

取上式积分中的函数作为概率密度，于是就得到了Gamma分布一般的形式，概率密度函数为：

$$\large{Gamma(t|\alpha,\beta) = \frac{\beta^{\alpha} t^{\alpha-1}e^{-\beta t}}{\Gamma(\alpha)}}$$


其中，$\alpha$为Gamma分布的shape parameter，主要决定了曲线的形状；而$\beta$为Gamma分布的rate parameter，主要决定了曲线有多陡。**Gamma分布的归一化常数为$\Gamma$函数在点$\alpha$处的值$\Gamma(\alpha)$**。


![](_v_images/20200212110541334_14826.png =822x)


Gamma分布的**期望，方差：**

$$\large{E(t) =  \int_0^{\infty}t \frac{\beta^{\alpha}}{\Gamma(\alpha)} t^{\alpha-1} e^{- \beta t} dt }$$
$$\large  { = \frac{\beta^\alpha}{\Gamma(\alpha)} {\int_0^{\infty}t^{\alpha}e^{- \beta t}dt}}$$
$$\large { = {\frac{\beta^{\alpha}}{\Gamma(\alpha)}\frac{\Gamma(\alpha +1)}{\beta^{\alpha +1}}} \underbrace{\int_0^{\infty}\frac{\beta^{\alpha +1}}{\Gamma(\alpha +1)} t^{\alpha} e^{- \beta t} dt   }_{\color{#F00}{1}}   }$$

$$\large { = \frac{\beta ^{\alpha}}{\Gamma(\alpha)} \frac{\alpha +1}{\beta ^ {\alpha +1}}  }$$
$$\large { = \frac {\alpha}{\beta} }$$
<br>

$$\large{D(t)= \frac{\alpha}{\beta^2}} $$


## 3、Beta函数
Beta函数的定义：
<br>

$$\large{ B(\alpha, \beta) = \int_0^1 x^{\alpha-1}(1-x)^{\beta -1} dx}$$

其中$\alpha,\beta >0$

Beta函数的性质：

1.对称性

$$\large{B(\alpha,\beta)=B(\beta,\alpha)}$$

2.与$\Gamma$函数的关系

$$\large{B(\alpha,\beta)=\frac{\Gamma(\alpha) \Gamma(\beta)}{\Gamma(\alpha+\beta)}}$$

## 4.Beta分布（从二项分布到Beta分布）
根据Beta函数的定义有：

$$\large{\int_{0}^{1}\frac{p^{\alpha-1}  (1-p)^{\beta-1}}{B(\alpha,\beta)} \ dp = 1}$$

取上式积分中的函数作为概率函数，就得到了Beta分布：

$$\large{B(p|\alpha,\beta)=\frac{p^{\alpha-1}  (1-p)^{\beta-1}}{B(\alpha,\beta)}}$$

**Beta分布的归一化常数为Beta函数在$(\alpha,\beta)$处的值**

Beta分布的期望，方差：
    
$$\large{\begin{split}
\mathbb E(p)=&\int_0^1 p\frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}p^{a-1}(1-p)^{b-1}dp\\
=&\frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}\int_0^1p{a+1-1}(1-p)^{b-1}dp\\
=&\frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}\frac{\Gamma(a+1)\Gamma(b)}{\Gamma(a+1+b)}\\
=&\frac{a}{a+b}
\end{split}}$$
计算方差之前，首先计算二阶矩：

$$\large{\mathbb E(p^2)=\frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}\frac{\Gamma(a+2)\Gamma(b)}{\Gamma(a+2+b)}=\frac{a(a+1)}{(a+b)(a+b+1)}}$$

<br>

$$\large{\text{var}[p]=\mathbb E(p^2)-\mathbb E^2(p)=\frac{ab}{(a+b)^2(a+b+1)}}$$


![](_v_images/20200212132323612_2629.png =637x)


### 5.Dirichlet分布（从多项分布到Dirichlet分布）
Dirichlet可以看做是将Beta分布推广到多分类的情形。概率密度函数定义如下：

$$\large{Dir(\vec p|\vec \alpha) = \frac{1}{B(\vec \alpha)} \prod_{k=1}^{K}p_{k}^{\alpha_{k}-1} \ \ \ \ \ (*)}$$

其中，$\vec \alpha = (\alpha_{1},\alpha_{2},\ldots,\alpha_{K})$为Dirichlet分布的参数。满足：

$$\large{\alpha_{1},\alpha_{2},\dots,\alpha_{K} > 0}$$

$B(\vec\alpha)$表示Dirichlet分布的归一化常数：

$$\large{B(\vec\alpha) = \frac{\prod_{k=1}^{K}\Gamma(\alpha_{k})}{\Gamma(\sum_{k=1}^{K}\alpha_{k})}}$$

由于加和的限制，$\{p\}$空间上的分布被限制在$K$-1维的单纯型当中。

$$\large{p_{1},p_{2},\ldots,p_{K}>0}$$
$$\large{p_{1}+p_{2}+\ldots+p_{K} = 1}$$


Dirichlet分布的期望为：

$$\large{E(\vec p) = (\frac{\alpha_{1}}{\sum_{k=1}^{K}\alpha_{k}},\frac{\alpha_{2}}{\sum_{k=1}^{K}\alpha_{k}},\ldots,\frac{\alpha_{K}}{\sum_{k=1}^{K}\alpha_{k}})}$$


**引用**

    https://blog.csdn.net/chenshulong/article/details/79027103
    模式识别与机器学习（PRML）