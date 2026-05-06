# 📊 Curiosidades: Modelos, Simulación y Visualización

Repositorio personal donde exploro modelos matemáticos, simulaciones y visualizaciones interactivas con Python.

Este repositorio documenta experimentos que combinan:

- Sistemas dinámicos  
- Análisis numérico  
- Visualización científica  
- Simulación computacional  

---

## 📂 Índice

### 🔹 Sistemas dinámicos
[Atractor de Lorenz](#atractor-de-lorenz)

[Péndulo simple](#péndulo-simple)

### 🔹 Dinámica de poblaciones
[Crecimiento exponencial](#modelo-de-crecimiento-exponencial)

[Crecimiento logístico](#modelo-de-crecimiento-logístico)

[Crecimiento con umbral](#modelo-de-crecimiento-con-umbral)

[Crecimiento logístico con umbral](#modelo)

---

# Atractor de Lorenz

Simulación del sistema dinámico caótico de Lorenz, resuelto numéricamente con `scipy` y visualizado con `plotly`.

### Características
- Resolución de EDOs con `odeint`
- Visualización 3D interactiva
- Exploración de comportamiento caótico

### Visualización interactiva
[Explorar el atractor de Lorenz](https://omarsanvicente.github.io/Curiosidades/Interactive/lorenz_attractor.html)

---

# Péndulo simple

## Planteamiento

El sistema está gobernado por:

$$
\frac{d^2 \theta}{dt^2} + \frac{g}{l} \sin(\theta) = 0
$$

### Variables
- $\theta(t)$: ángulo  
- $g$: gravedad  
- $l$: longitud  

---

## Reformulación

$$
\begin{cases}
\frac{d\theta}{dt} = \omega \\
\frac{d\omega}{dt} = -\frac{g}{l} \sin(\theta)
\end{cases}
$$

---

## Parámetros

| Parámetro | Valor |
|----------|------|
| $g$ | 9.81 |
| $l$ | 1.0 |
| $\theta_0$ | $\pi/4$ |
| $\omega_0$ | 0 |

---

## Resultado

![Péndulo](/Images/pendulum.png)

---

# Dinámica de poblaciones

---

## Modelo de crecimiento exponencial

$$
\frac{dN}{dt} = kN
$$

Solución:

$$
N(t) = N_0 e^{kt}
$$

### Ejemplo

![Exponencial](/Images/crecimiento_bacteriano_exponencial.png)

---

## Modelo de crecimiento logístico

$$
\frac{dN}{dt} = rN\left(1 - \frac{N}{K}\right)
$$

### Interpretación
- Crecimiento inicial exponencial  
- Saturación en $K$  
- Competencia interna  

### Solución

$$
N(t) = \frac{K}{1 + Ae^{-rt}}
$$

---

### Visualización

![Logístico](/Images/familias_logistico.png)

---

### Plano fase

![Plano fase](/Images/diagrama_fase_flujo.png)

---

## Modelo de crecimiento con umbral

$$
\frac{dP}{dt} = -r P \left(1 - \frac{P}{T}\right)
$$

### Interpretación

- $P < T$ → extinción  
- $P > T$ → crecimiento sin límite  

---

### Equilibrios

- $P = 0$ → estable  
- $P = T$ → inestable  

---

### Solución

$$
P(t) = \frac{T P_0}{(T - P_0)e^{rt} + P_0}
$$

---

### Interpretación

Este modelo introduce un **umbral crítico**:

- Si la población cae por debajo de $T$, no se recupera  
- Representa un **tipping point**  

![Crecimiento con Umbral](/Images/Crecimiento_umbral.png)

- Si $P < T$ → la población decrece hacia 0
- Si $P > T$ → la población crece sin límite
- $P = T$ es un punto crítico inestable

![Diagrama Fase del crecimiento con Umbral](/Images/diagrama_fase_umbral.png)

## Modelo logístico con umbral

$$
\frac{dN}{dt} = rN\left(1 - \frac{N}{K}\right)\left(\frac{N}{A} - 1\right)
$$

Este modelo combina:
- saturación (capacidad de carga $K$)
- umbral crítico $A$

### Comportamiento

- $N < A$ → la población colapsa a 0  
- $N > A$ → la población crece hacia $K$  

![Familia de soluciones modelo de crecimiento logístico con umbral](/Images/familias_soluciones_logistico_umbral.png)


### Equilibrios

- $N = 0$ → estable  
- $N = A$ → inestable  
- $N = K$ → estable  

![Diagrama fase del modelo de crecimiento logístico con umbral](/Images/diagrama_fase_logistico_umbral.png)


El sistema presenta **bistabilidad**: dos estados posibles dependiendo de la condición inicial.

Se presenta un repulsor en $A$, si la población no alcanza a pasar este umbral la población estara destinada a la extinción.

Por otro lado se presenta un atractor, el límite de carga sinergetica $K$ el cual es el límite natural del ambiente para albergar esta población.

Es importante hacer notar que este modelo es un modelo más realista e incluso se ha usado para analizar poblaciones

"*...Aparentemente, un modelo de esta clase general rigió la población de palomas viajeras, que existía en Estados Unidos en grandes números hasta fines del siglo XIX. Estas palomas fueron intensamente cazadas para alimentación y por deporte y, como consecuencia, el número de ellas se redujo drásticamente hacia la década de 1880. Sin embargo, parece que esta paloma pudo multiplicarse bien sólo cuando existió en grandes concentraciones, lo cual corresponde a un umbral $T$ relativamente alto. Aunque a fines de la década de 1880 permanecían vivos un número razonablemente grande de estos pájaros por separado, no existían los suficientes en algún lugar como para permitir que se reprodujeran con éxito, por lo que la población disminuyó con rapidez hasta extinguirse. La última sobreviviente murió en 1914. La disminución precipitada de la población de la paloma viajera desde grandes cantidades hasta la extinción en poco más de tres décadas fue uno de los primeros factores que contribuyeron al interés por la conservación en Estados Unidos...*"

Boyce - Diprima. Ecuaciones diferenciales con problemas de valores en la frontera.



---

---

# 🎯 Objetivo del repositorio

Este repositorio está enfocado en:

- Explorar modelos matemáticos  
- Desarrollar intuición en sistemas dinámicos  
- Construir visualizaciones interpretables  

---

# 🛠️ Tecnologías

- Python  
- NumPy  
- SciPy  
- Matplotlib  
- Plotly  