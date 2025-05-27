# 📘 Resumen de Dinámica de Sistemas

Autor: *Nombre del estudiante*  
Curso: Sexto semestre - Ingeniería  
Profesor: Ing. Jorge Eduardo Cote Ballesteros  
Año: 2025

---

## Índice

1. [Sistemas Hidráulicos y Térmicos](#1-sistemas-hidráulicos-y-térmicos)
2. [Función de Transferencia](#2-función-de-transferencia)
3. [Modelamiento con Diagramas de Bloques](#3-modelamiento-con-diagramas-de-bloques)
4. [Álgebra de Bloques](#4-álgebra-de-bloques)
5. [Diagramas de Flujo de Señal](#5-diagramas-de-flujo-de-señal)
6. [Sistemas de Primer Orden](#6-sistemas-de-primer-orden)
7. [Sistemas de Segundo Orden](#7-sistemas-de-segundo-orden)

---

## 1. Sistemas Hidráulicos y Térmicos

### 🔹 Sistemas Hidráulicos

**Tanque simple:**
\[
A_1 \frac{dh_1}{dt} = q_i - \frac{h_1}{R_1}
\]

**Dos tanques interconectados:**
\[
\begin{cases}
A_1 \frac{dh_1}{dt} = q_i - \frac{h_1 - h_2}{R_1} \\
A_2 \frac{dh_2}{dt} = \frac{h_1 - h_2}{R_1} - \frac{h_2}{R_2}
\end{cases}
\]

### 🔹 Sistemas Térmicos

**Modelo general (energía):**
\[
Q_{in} - Q_{out} = C \frac{dT}{dt}
\]

---

## 2. Función de Transferencia

### 🔹 Definición

\[
G(s) = \frac{Y(s)}{U(s)}
\]

Condiciones iniciales = 0 (para modelos de control).

### 🔹 Clasificación

- **Propia**: \( \deg N(s) \leq \deg D(s) \)
- **Impropia**: \( \deg N(s) > \deg D(s) \)

### 🔹 Polos y Ceros

- **Ceros**: raíces del numerador \( N(s) = 0 \)
- **Polos**: raíces del denominador \( D(s) = 0 \)

**Ejemplo:**
\[
G(s) = \frac{3s - 1}{s^2 + 3s + 2} \Rightarrow \text{Cero: } \frac{1}{3}, \text{Polos: } -1, -2
\]

---

## 3. Modelamiento con Diagramas de Bloques

- Usan bloques con funciones de transferencia interconectadas.
- Permite representar modelos complejos como motores, sistemas térmicos o hidráulicos.

**Ejemplo:**
Motor DC con entrada \( V_a \) y salida \( \theta(t) \)

---

## 4. Álgebra de Bloques

### 🔹 Reglas básicas

- **Cascada**: \( G_{total}(s) = G_1(s) \cdot G_2(s) \)
- **Paralelo**: \( G_{total}(s) = G_1(s) + G_2(s) \)
- **Realimentación negativa**:
\[
T(s) = \frac{G(s)}{1 + G(s)H(s)}
\]

---

## 5. Diagramas de Flujo de Señal

- Representación de sistemas con **nodos** y **flechas**.
- Se usa la **fórmula de Mason**:

\[
T(s) = \frac{\sum P_k \Delta_k}{\Delta}
\]

Donde:
- \( P_k \): ganancia del camino directo,
- \( \Delta \): determinante considerando lazos.

---

## 6. Sistemas de Primer Orden

### 🔹 Forma general:

\[
G(s) = \frac{K}{\tau s + 1}
\]

- \( K \): ganancia estática
- \( \tau \): constante de tiempo

### 🔹 Respuesta al escalón

\[
y(t) = AK(1 - e^{-t/\tau})
\]

---

## 7. Sistemas de Segundo Orden

### 🔹 Forma canónica:

\[
G(s) = \frac{K \omega_n^2}{s^2 + 2\zeta\omega_n s + \omega_n^2}
\]

- \( \omega_n \): frecuencia natural
- \( \zeta \): factor de amortiguamiento

### 🔹 Casos

- **Subamortiguado** (\( \zeta < 1 \)): oscilatorio
- **Críticamente amortiguado** (\( \zeta = 1 \))
- **Sobreamortiguado** (\( \zeta > 1 \))

### 🔹 Respuesta típica (subamortiguado):

\[
y(t) = K A \left(1 - e^{-\zeta \omega_n t} \left[ \cos(\omega_d t) + \frac{\zeta}{\sqrt{1 - \zeta^2}} \sin(\omega_d t) \right] \right)
\]

---

## ✍️ Notas Finales

Este resumen fue elaborado con base en las presentaciones del curso de Dinámica de Sistemas, utilizando referencias como Ogata, C. Chen, R. Hernández y N. Nise.
