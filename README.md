# Clase: Sistemas de Primer Orden

Los sistemas de primer orden son fundamentales en el estudio de la dinámica de sistemas, ya que representan el comportamiento de muchos procesos físicos reales como tanques hidráulicos, circuitos eléctricos RC o sistemas térmicos simples. En esta clase aprenderemos a identificar su ecuación característica, hallar su función de transferencia, y analizar su comportamiento temporal frente a diferentes tipos de entrada.

---

## 1. Estructura y forma general

### 1.1 Ecuación diferencial general

🔑 > *Ecuación de primer orden*: Ecuación que relaciona la derivada de una variable dependiente con ella misma y una entrada forzada. Su forma general es:
$$
a \frac{dy(t)}{dt} + b y(t) = c u(t)
$$

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

