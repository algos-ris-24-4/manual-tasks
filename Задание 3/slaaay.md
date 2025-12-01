# Решение задачи (Вариант 3)

## 1) 

\[
\Delta_n = p \cdot (-1)^{n+1} \cdot \Delta_{n-1} + 2 \cdot (-1)^{n+1} \cdot 
\begin{vmatrix}
  -1 & -2 & 0 & \cdots & 0 & 0 \\
  1 & -1 & -2 & \cdots & 0 & 0 \\
  0 & 1 & -1 & \cdots & 0 & 0 \\
  \vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
  0 & 0 & 0 & \cdots & -1 & -2 \\
  0 & 0 & 0 & \cdots & 1 & -1
\end{vmatrix}
\]

\[
= p \cdot \Delta_{n-1} + 2 \cdot 1 \cdot \Delta_{n-2} = -\Delta_{n-1} + 2 \cdot \Delta_{n-2}
\]

Получаем рекуррентное соотношение.

## 2) Составляем уравнение

\[
\Delta_n \to \lambda^n 
\]

\[
\lambda^n = -\lambda^{n-1} + 2 \cdot \lambda^{n-2} \quad | : \lambda^{n-2}
\]

\[
\lambda^2 = -\lambda + 2 
\]

\[
\lambda^2 + \lambda - 2 = 0 
\]

Вычисляем по Виету:

\[
\lambda_1 = -2, \quad \lambda_2 = 1
\]

## 3) Проверка корней на равенство

\[
\lambda_1 \ne \lambda_2 
\]

Тогда:

\[
\Delta_n = C_1 \cdot \lambda_1^n + C_2 \cdot \lambda_2^n 
\]

\[
\Delta_n = C_1 \cdot (1)^n + C_2 \cdot (-2)^n
\]

Посчитаем определители \(\Delta_1\) и \(\Delta_2\):

\[
\Delta_1 = -1, \quad \Delta_2 = -1 \cdot (1) - 1 \cdot (-2) = -1 + 2 = 3 
\]

Подставляем значения для системы уравнений:

\[
\begin{cases}
\Delta_1 = C_1 - 2C_2 = -1 \\
\Delta_2 = C_1 + 4C_2 = 3
\end{cases}
\]

Решаем систему:

\[
\begin{aligned}
6C_2 &= 4 \\
C_2 &= \frac{4}{6} = \frac{2}{3} \\
C_1 &= 3 - 4 \cdot \frac{2}{3} = 3 - \frac{8}{3} = \frac{1}{3}
\end{aligned}
\]

\[
C_1 = \frac{1}{3}, \quad C_2 = \frac{2}{3}
\]

\[
\Delta_n = C_1 + C_2 \cdot (-2)^n = \frac{1}{3} + \frac{2}{3} \cdot (-2)^n
\]

## 4) Подставим \(n = 12\)

\[
\begin{aligned}
\Delta_{12} &= \frac{1}{3} + \frac{2}{3} \cdot (-2)^{12} \\
&= \frac{1}{3} + \frac{2}{3} \cdot 4096 \\
&= \frac{1 + 8192}{3} \\
&= \frac{8193}{3} = 2731
\end{aligned}
\]

**Ответ:** 2731