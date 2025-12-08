# Решение варианта 2 командой *travis*

$$
A_n =
\begin{pmatrix}
-1 & 1 & 0 & \cdots & 0 & 0 \\
-2 & -1 & 1 & \cdots & 0 & 0 \\
0 & -2 & -1 & \cdots & 0 & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & 0 & 0 & \cdots & -1 & 1 \\
0 & 0 & 0 & \cdots & -2 & -1
\end{pmatrix}
$$

Найти $\Delta_{10}$

---

## 1. Вывод рекуррентной формулы

Разложим определитель $\Delta_n$ по первой строке:

$$
\Delta_n = -1 \cdot \Delta_{n-1} + (-1)\cdot(-1)\cdot
\left|
\begin{matrix}
-2 & -1 & 0 & \cdots & 0 \\
0 & -1 & 1 & \cdots & 0 \\
0 & -2 & -1 & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & -1
\end{matrix}
\right|
$$

Второй определитель разложим по первому столбцу:

$$
= -\Delta_{n-1} + 1 \cdot (-2) \cdot 
\left|
\begin{matrix}
-1 & 1 & 0 & \cdots & 0 \\
-2 & -1 & 1 & \cdots & 0 \\
0 & -2 & -1 & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & -1
\end{matrix}
\right|
= -\Delta_{n-1} + 2 \Delta_{n-2}
$$

Полученное рекуррентное соотношение:

$$
\Delta_n = -\Delta_{n-1} + 2\Delta_{n-2}
$$

---

## 2. Решение характеристического уравнения

Пусть $\Delta_n = \lambda^n$. Подставляем:

$$
\lambda^n = -\lambda^{n-1} + 2\lambda^{n-2}
$$

Делим на $\lambda^{n-2}$:

$$
\lambda^2 + \lambda - 2 = 0
$$

Находим корни:

$$
\lambda_{1,2} = \frac{-1 \pm \sqrt{1 + 8}}{2}
= \frac{-1 \pm 3}{2}
$$

$$
\lambda_1 = 1, \quad \lambda_2 = -2
$$

Так как $\lambda_1 \ne \lambda_2$, общее решение имеет вид:

$$
\Delta_n = C_1 \cdot 1^n + C_2 \cdot (-2)^n = C_1 + C_2(-2)^n
$$

---

## 3. Нахождение констант $C_1$ и $C_2$

Вычислим определители малых порядков:

- $\Delta_1 = -1$
- $\Delta_2 = 
\begin{vmatrix}
-1 & 1\\
-2 & -1
\end{vmatrix}
= 3$

Подставляем:

$$
\begin{cases}
C_1 - 2C_2 = -1 \\
C_1 + 4C_2 = 3
\end{cases}
$$

Вычитаем:

$$
6C_2 = 4
$$

$$
C_2 = \frac{2}{3}
$$

Находим $C_1$:

$$
C_1 = -1 + 2C_2 = -1 + \frac{4}{3} = \frac{1}{3}
$$

Итак, общее решение:

$$
\boxed{\Delta_n = \frac{1 + 2(-2)^n}{3}}
$$

---

## 4. Вычисление $\Delta_{10}$

$$
(-2)^{10} = 1024
$$

$$
\Delta_{10} = \frac{1 + 2\cdot1024}{3}
= \frac{2049}{3}
= 683
$$

---

## Ответ

$$
\boxed{\Delta_{10} = 683}
$$
