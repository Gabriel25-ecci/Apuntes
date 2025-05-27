# Clase: Sistemas de Primer Orden

Los sistemas de primer orden son fundamentales en el estudio de la dinámica de sistemas, ya que representan el comportamiento de muchos procesos físicos reales como tanques hidráulicos, circuitos eléctricos RC o sistemas térmicos simples. En esta clase aprenderemos a identificar su ecuación característica, hallar su función de transferencia, y analizar su comportamiento temporal frente a diferentes tipos de entrada.

---

## 1. Estructura y forma general

### 1.1 Ecuación diferencial general

🔑 > *Ecuación de primer orden*: Ecuación que relaciona la derivada de una variable dependiente con ella misma y una entrada forzada. Su forma general es:
<p align="center"><img src="https://latex.codecogs.com/png.image?\dpi{110}&space;a\frac{dy(t)}{dt}+by(t)=cu(t)" /></p>


### 1.2 Función de transferencia

🔑 > *Función de transferencia*: Relación entre la salida y entrada de un sistema en el dominio de Laplace con condiciones iniciales cero.
$$
G(s) = \frac{Y(s)}{U(s)} = \frac{c}{as + b}
$$

### 1.3 Forma canónica

🔑 > *Forma canónica*: Forma estándar de una función de transferencia que permite identificar claramente la ganancia estática y la constante de tiempo:
$$
G(s) = \frac{K}{\tau s + 1}, \quad K = \frac{c}{b}, \quad \tau = \frac{a}{b}
$$

---

## 2. Respuesta a entradas

### 2.1 Entrada escalón

💡Ejemplo 1:
Sea un sistema cuya función de transferencia es:
$$
G(s) = \frac{5}{2s + 16}
$$
Convirtiéndola a forma canónica:
$$
G(s) = \frac{0.3125}{0.125s + 1}
$$
Donde \( K = 0.3125 \), \( \tau = 0.125 \)

🔑 > *Respuesta al escalón*:
$$
y(t) = AK \left(1 - e^{-\frac{t}{\tau}}\right)
$$

### 2.2 Entrada rampa

💡Ejemplo 2:
$$
Y(s) = \frac{AK}{s^2(\tau s + 1)} \Rightarrow y(t) = AK \left(t - \tau + \tau e^{-t/\tau} \right)
$$

---

## 3. Representación gráfica

![Curva de respuesta escalón](imagenes/respuesta_orden1.png)  
**Figura 1.** Curva típica de respuesta escalón en un sistema de primer orden

---

## 4. Tabla de identificación

💡Ejemplo 3:

| Parámetro | Valor     |
|-----------|-----------|
| \( K \)   | 0.3125    |
| \( \tau \)| 0.125 s   |
| Tipo de entrada | Escalón unitario |
| Salida final esperada | \( AK = 0.3125 \) |

**Tabla 1.** Parámetros identificados para un sistema de primer orden

---

## 5. Código

💡Ejemplo 4: Código en MATLAB para graficar la respuesta escalón
```matlab
K = 0.3125;
tau = 0.125;
t = 0:0.01:1;
y = K * (1 - exp(-t/tau));
plot(t, y);
xlabel('Tiempo (s)');
ylabel('Salida y(t)');
title('Respuesta escalón - Sistema de Primer Orden');


Ejercicio 1
Dado el sistema con función de transferencia:

𝐺
(
𝑠
)
=
10
3
𝑠
+
5
G(s)= 
3s+5
10
​
 
Determine 
𝐾
K y 
𝜏
τ

Encuentre la respuesta al escalón unitario

✅ Solución:

𝐾
=
10
5
=
2
,
𝜏
=
3
5
=
0.6
K= 
5
10
​
 =2,τ= 
5
3
​
 =0.6
𝑦
(
𝑡
)
=
1
⋅
2
(
1
−
𝑒
−
𝑡
/
0.6
)
y(t)=1⋅2(1−e 
−t/0.6
 )
Ejercicio 2
Una planta química tiene una ganancia estática de 4 y una constante de tiempo de 2 s. Obtenga la función de transferencia y la respuesta al escalón unitario.

✅ Solución:

𝐺
(
𝑠
)
=
4
2
𝑠
+
1
⇒
𝑦
(
𝑡
)
=
4
(
1
−
𝑒
−
𝑡
/
2
)
G(s)= 
2s+1
4
​
 ⇒y(t)=4(1−e 
−t/2
 )
10. Conclusiones
Los sistemas de primer orden permiten modelar fenómenos simples pero muy representativos de la realidad. El análisis de su función de transferencia y respuesta a entradas estándar (escalón, rampa) nos da herramientas clave para predecir el comportamiento de un sistema. Los parámetros 
𝜏
τ y 
𝐾
K son esenciales para el diseño de controladores.


# Clase: Sistemas Hidráulicos

En esta clase se abordará el modelamiento de sistemas hidráulicos, que son esenciales en ingeniería de procesos y control. Estos sistemas permiten representar tanques, válvulas y tuberías, y son una analogía directa de sistemas eléctricos o térmicos. Su estudio se centra en cómo varía el nivel del fluido o el caudal frente a una entrada, y se modelan usando ecuaciones diferenciales basadas en balances de masa o energía.

---

## 1. Modelos de Tanques Hidráulicos

### 1.1 Tanque simple

🔑 > *Tanque simple*: Sistema con una entrada de flujo constante y una salida proporcional al nivel del líquido. Su dinámica se describe por una ecuación diferencial de primer orden.

**Ecuación diferencial del sistema**:
A1 * (dh1/dt) = qi - h1/R1


**Función de transferencia** (forma canónica):
H1(s)/Qi(s) = R1 / (R1A1s + 1)

💡Ejemplo 1:

Un tanque con A1 = 2 m² y R1 = 5 s/m². Determine la función de transferencia.

**Solución**:

H1(s)/Qi(s) = 5 / (10s + 1)

### 1.2 Salida como variable de interés

🔑 > *Caudal de salida*: Se puede modelar como variable de salida, usando la relación q1 = h1 / R1.

Entonces:

R1A1(dq1/dt) = qi - q1


---

## 2. Dos Tanques Interconectados

🔑 > *Tanques interconectados*: Sistema de dos tanques donde el flujo entre ellos depende de la diferencia de niveles.

**Ecuaciones del sistema**:


q1 = (h1 - h2)/R1
q2 = h2 / R2

A1*(dh1/dt) = qi - q1
A2*(dh2/dt) = q1 - q2



💡Ejemplo 2:

Para A1 = A2 = 1 m², R1 = R2 = 2 s/m², encuentre la ecuación que relaciona h2 con qi.

**Solución** (esbozo):
1. Derivar q1 y q2 en función de h1 y h2.
2. Sustituir y eliminar variables intermedias para llegar a:

A1R1R2A2 * d²q2/dt² + (A1R1 + A1R2 + R2A2) * dq2/dt + q2 = qi

---

## 3. Representación Gráfica

![Tanque simple](imagenes/tanque_simple.png)  
**Figura 1.** Representación de un tanque con entrada y salida

---

## 4. Tabla de parámetros

|
