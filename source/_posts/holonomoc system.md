---
title: nonholonomic constraints
date: 2019-02-24 12:12:57
categories: 
- 数学相关
tags:
- nonholonomic constraints
mathjax: true
---



In the note, the term *holonomic* is synonymous with the *completely integrable*, and *nonintegrable* is synonymous with *nonholomonic* [1]

(备注：完整约束就是完全可积约束，非完整约束就是不可积约束)







# 完整约束（holonomic constraint）：

A constraint is said to be holonomic if it restricts the motion of a system to a smooth hypersurface of the configuration space. It will be convenient to adopt some language and notation from differential geometry, so we call this smooth hypersurface a manifold. Locally, a holonomic constraint can be represented as a set of algebraic constraints on the configuration space.

$h_i(q)=0$, $i=1,...,k$

The dimension of the manifold on which the motion of the system evolves is $n-k$

(备注：由上可知，完整约束会影响系统的自由度)





# 普法夫约束（Pfaffian constraints）

A set of $k$ Pfaffian constraints are of the form $w_i(q)\dot q=0$, $i=1,...,k$ where the $w_i$ are linearly independent row vectors and $\dot q $ is a column vector.



给定一个普法夫约束，如何判断它是否可积呢？如果存在函数 $h_i: R^n \rightarrow R$, $i=1,...,k$ 有 $h_i(q(t))=0$  $\Leftrightarrow$  $w_i(q(t))\dot q=0$  $i=1,...,k$  那么这个普法夫约束就是完整约束，也就是可积约束。但是这样的$h_i$ 很多情况下不易找出，如何在不找 $h_i$ 的情况下判别约束的可积性呢？Frobenius theoreom （弗贝尼斯定理）给出了基于李代数的充要条件，然而，即使通过弗贝尼斯定理判断出该系统是完整系统，该理论不能找到$h_i$ . 因此我们需要注意：该约束可积不意味着你可以把约束积分成 $h_i=0$ 这样的形式。 



# 弗贝尼斯定理(Frobenius Theorem)

If the system is smooth and the distribution is nonsingular, the the Frobenius theorem immediately characterizes integralibity: *A system is completely integral if and only if it is involutive*. 

involutive : every Lie bracket can be expressed as a linear combination of the system vector fields.





[1] Planning Algorithm, 2006