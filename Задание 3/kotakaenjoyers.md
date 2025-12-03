# Решение варианта 4 командой kotakaenjoers

$$
A_n = 
\begin{pmatrix}
3 & -1 & 0 & \cdots & 0 & 0 \\
-2 & 3 & -1 & \cdots & 0 & 0 \\
0 & -2 & 3 & \cdots & 0 & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
0 & 0 & 0 & \cdots & 3 & -1 \\
0 & 0 & 0 & \cdots & -2 & 3
\end{pmatrix}
$$

Найти $\Delta_7$

## 1. Вывод рекуррентной формулы

Разложим определитель $\Delta_n$ по первой строке:

$$
\Delta_n = 3 \cdot \Delta_{n-1} + (-1) \cdot (-1) \cdot 
\left|
\begin{matrix}
-2 & -1 & 0 & \cdots & 0 \\
0 & 3 & -1 & \cdots & 0 \\
0 & -2 & 3 & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & 3
\end{matrix}
\right|
$$

Второй определитель можно разложить по первому столбцу:

$$
= 3 \cdot \Delta_{n-1} + 1 \cdot (-2) \cdot 
\left|
\begin{matrix}
3 & -1 & 0 & \cdots & 0 \\
-2 & 3 & -1 & \cdots & 0 \\
0 & -2 & 3 & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & 3
\end{matrix}
\right|
= 3 \cdot \Delta_{n-1} - 2 \cdot \Delta_{n-2}
$$

Полученное рекуррентное соотношение:
$$\Delta_n = 3\Delta_{n-1} - 2\Delta_{n-2}$$

---

## 2. Решение характеристического уравнения
Пусть $\Delta_n = \lambda^n$. Подставляем в рекуррентное соотношение:

$$
\lambda^n = 3 \lambda^{n-1} - 2 \lambda^{n-2}
$$

Делим на $\lambda^{n-2}$:

$$
\lambda^2 - 3\lambda + 2 = 0
$$

Находим корни:

$$
\lambda_{1,2} = \frac{3 \pm \sqrt{9 - 8}}{2} = \frac{3 \pm 1}{2}
$$
$$
\lambda_1 = 2, \quad \lambda_2 = 1
$$

Так как $\lambda_1 \mathrel{\not=} \lambda_2$, общее решение имеет вид:

$$
\Delta_n = C_1 \cdot 2^n + C_2 \cdot 1^n = C_1 \cdot 2^n + C_2
$$

---

## 3. Нахождение констант $C_1$ и $C_2$

Вычислим определители 1-го и 2-го порядка:

- $\Delta_1 = 3$
- $\Delta_2 = 3 \cdot 3 - (-1) \cdot (-2) = 9 - 2 = 7$ 

Подставляем в общее решение:

$$
\begin{cases}
\Delta_1 = C_1 \cdot 2^1 + C_2 = 2C_1 + C_2 = 3 \\
\Delta_2 = C_1 \cdot 2^2 + C_2 = 4C_1 + C_2 = 7
\end{cases}
$$

$$
\begin{cases}
3 = 2C_1 + C_2 \\
7 = 4C_1 + C_2
\end{cases}
$$

Вычитаем первое уравнение из второго:

$$
(4C_1 + C_2) - (2C_1 + C_2) = 7 - 3
$$
$$
2C_1 = 4
$$
$$
C_1 = 2
$$

Подставляем $C_1 = 2$ в первое уравнение:

$$
2 \cdot 2 + C_2 = 3
$$
$$
C_2 = 3 - 4 = -1
$$

Таким образом, частное решение:

$$
\boxed{\Delta_n = 2 \cdot 2^n - 1 = 2^{n+1} - 1}
$$

---

## 4. Вычисление $\Delta_7$

$$
\Delta_7 = 2^{7+1} - 1 = 2^8 - 1 = 256 - 1 = \boxed{255}
$$
