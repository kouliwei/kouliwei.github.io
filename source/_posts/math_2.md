---
title: 线性方程组的求解问题
date: 2019-04-11 09:12:57
categories: 
- 数学相关
tags:
- 方程组求解
mathjax: true
---

线性方程组的求解是试图找到向量$x_{n\times 1}$ 使其满足 $A_{m\times n}x_{n\times1}=b_{n\times1}$。根据$b$ 是否为零向量。将线性方程组分为两类：齐次线性方程组（$b=0$）和非齐次线性方程组 ($b \neq 0$)。下面分别给予讨论。

# 齐次线性方程组

由公式可知，齐次线性方程组肯定有解为$0_{n\times1}$, 那么在什么样的情况下它具有非零的解呢。

（1）如果r(A) = n, A矩阵列向量线性无关，方程组只有$0_{n\times1}$; 

（2）如果r(A) < n, A矩阵列向量线性相关，方程组有非零解，而且有无数的非零解。



# 非齐次线性方程组

非齐次线性方程组可能存在无解，唯一解和无穷多解得情况。一般引入增广矩阵来判定方程组的解。

（1）如果 r(A)  = n < r (A | b);  方程组不相容，意味着独立的约束条件> 方程组的个数，方程组无解。

（2）如果 r(A)  = r(A | b) = n; 方程组相容；独立的约束条件= 方程组的个数,方程组有唯一解。

（2）如果 r(A)  = r(A | b) < n; 方程组相容；独立的约束条件< 方程组的个数,方程组有无穷解。



对于（1），尽管方程组无解，但我们还是希望能够找到一组解，使得$||Ax-b||^2 $尽可能的小。这样的解称为最小二乘解。求解过程如下：

令$J=(Ax-b)^T(Ax-b)​$, 相对$x​$的偏导可得：

​                                                    $\dfrac{\partial J }{\partial x}=\dfrac{\partial }{\partial x}((Ax-b)^T(Ax-b))​$ 

​                                                            $=\dfrac{\partial }{\partial x}(x^TA^TAx-x^TA^Tb-b^TAx+b^Tb)​$ 

​                                                           $=\dfrac{\partial }{\partial x}tr(x^TA^TAx-x^TA^Tb-b^TAx+b^Tb)​$ 

​                                                           $=\dfrac{\partial }{\partial x}tr(x^TA^TAx)-                                                      \dfrac{\partial }{\partial x}tr(x^TA^Tb)-\dfrac{\partial }{\partial x}tr(b^TAx)​$

​                                                           $=A^TAx + (x^TA^TA)^T-A^Tb-(b^TA)^T​$

​                                                           $=2(A^TAx -A^Tb)​$

令其等于0，可得$x=(A^TA)^{-1}A^T$. 该式为超定方程的最小二乘解。（备注，其实最小二乘解有无穷多个，这个是范数最小的最小二乘解，称之为极小范数最小二乘解）。







对于（3），尽管方程组有无数解，但我们希望能够找到一组解，使得$\dfrac{1}{2}||x||^2$尽可能的小。这样的解称为极小范数解。求解过程如下：

首先这是一个包含等式约束$Ax=b$ 的优化问题，构造拉格朗日方程，变成无约束优化问题。

令$L=\dfrac{1}{2}x^Tx+\lambda^T(Ax-b)$, 分别对$x$和$\lambda$求偏导可得：

​                                                    $\dfrac{\partial L }{\partial x}=x+A^T\lambda​$=0 (1),    $\dfrac{\partial L }{\partial \lambda}=Ax-b​$=0 (2)

由 (1) 得$x=-A^T\lambda$, 代入 (2) 得$\lambda=-(AA^T)^{-1}b$, 再回代到 (1) 得$x=A^T(AA^T)^{-1}b$, 该式为欠定方程的极小范数解。



------



相关数学技巧：矩阵的微分可以引入矩阵的迹来方便计算。对于方阵$A_{n\times n}$，矩阵的迹定义为对角元素的和，即为：$tr(A)=\Sigma a_{ii}$.  

**矩阵的迹相关公式有**：

（1） $tr(AB)=tr(BA)​$;

（2）$tr(ABC)=tr(BCA)=tr(CAB)$;

（3）$tr(A)=tr(A^T)$;

（4）$tr(aA+bB)=atr(A)+btr(B)​$;

**矩阵求导的相关公式有：**

（1）$\dfrac{\partial }{\partial A}tr(AB)= B^T$;

（2）$\dfrac{\partial }{\partial A^T}tr(AB)= B$;

（3）$\dfrac{\partial }{\partial A}tr(A^TA)=2A $;

（4）$\dfrac{\partial }{\partial A^T}tr(A^TA)=2A^T ​$;

（5）$\dfrac{\partial }{\partial A }tr(ABA^TC)=CAB + (BA^TC)^T=CAB + C^TAB^T$;

（5）$\dfrac{\partial }{\partial A}tr(ABCA^TD)=DABC + (BCA^TD)^T=DABC + D^TAC^TB^T$;



（计算技巧，若求相对于A的偏导，结果有两部分：

第一部分从$A^T$后一项往后写，结束后再从第一项写起，一直写到$A^T$的前一项为止；

第二部分从A的后一项往后写，结束后再从第一项写起，一直写到$A$的前一项为止，然后再对其转置.

（计算技巧，若求相对于$A^T$的偏导，结果有两部分：

第一部分从$A$后一项往后写，结束后再从第一项写起，一直写到$A$的前一项为止；

第二部分从$A^T$ 的后一项往后写，结束后再从第一项写起，一直写到​$A^T$ 的前一项为止，然后再对其转置.）；


