本文件使用了Matlab Simscape工具.

**理论基础**：线性控制器设计

对倒立摆建模如下：
$$
\ddot\Phi - \frac{g}{L}\Phi + \frac{1}{L}\ddot\delta = 0
$$
令$x_1=\Phi$, $x_2 = \dot\Phi$,$u = \frac{1}{L}\ddot\delta$，

那么，$x_2 = \ddot\Phi = \frac{g}{L}x_1-u$，

状态空间方程(State Space Function)为：
$$
\left[
\begin{matrix}
\dot{x_1} \\
\dot{x_2}
\end{matrix}
\right]
= 
\left[
\begin{matrix}
0 & 1 \\
\frac{g}{L} & 0
\end{matrix}
\right]
\left[
\begin{matrix}
x_1 \\
x_2
\end{matrix}
\right]
+
\left[
\begin{matrix}
0 \\
-1
\end{matrix}
\right]
u
$$
$u = -\left[\begin{matrix}k_1 & k_2 \end{matrix}\right]\left[\begin{matrix}x_1 \\x_2\end{matrix}\right]$

令$e = x_{1d}-x_1,\dot{e}=\dot{x_{1d}}-\dot{x_1}$，目标为当t->∞时e ->0

令目标$x_{1d}=\dot{x_{1d}} = 0$，那么$\dot{e} = -\dot{x_1}$，误差状态空间方程为：
$$
\begin{bmatrix}
\dot{e} \\
\dot{x_2}
\end{bmatrix}
=
\begin{bmatrix}
0 & -1 \\
-\frac{g}{L} & 0
\end{bmatrix}
\begin{bmatrix}
e\\
x_2
\end{bmatrix}
+
\begin{bmatrix}
0 \\
-1
\end{bmatrix}
u
+\begin{bmatrix}
0 \\
\frac{g}{L}x_{1d}
\end{bmatrix}
$$
令$u = -\left[\begin{matrix}k_1 & k_2 \end{matrix}\right]\left[\begin{matrix}e \\x_2\end{matrix}\right] + \frac{g}{L}x_{1d}$

则
$$
\begin{bmatrix}
\dot{e} \\
\dot{x_2}
\end{bmatrix}
=
\begin{bmatrix}
0 & -1 \\
-\frac{g}{L} & 0
\end{bmatrix}
\begin{bmatrix}
e\\
x_2
\end{bmatrix}
+
\begin{bmatrix}
0 & 0\\
k_1 & k_2
\end{bmatrix}
\begin{bmatrix}
e \\
x_2
\end{bmatrix}
= 
\begin{bmatrix}
0 & -1 \\
k_1 - \frac{g}{L} & k_2
\end{bmatrix}
\begin{bmatrix}
e \\
x_2
\end{bmatrix}
$$
设计$k_1，k_2$使$\lambda_1 < 0，\lambda_2 < 0$
$$
|\lambda I-A_{cl}|=
\begin{bmatrix}
\lambda & 1 \\
\frac{g}{L}-k1 & \lambda-k_2
\end{bmatrix}
= \lambda^2-k_2\lambda-\frac{g}{L}+k_1 = \lambda^2+10\lambda+25 = 0
$$
系数对应相等求出$k_1、k_2$的解，进一步代入$u$.