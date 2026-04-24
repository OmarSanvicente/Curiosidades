# Curiosidades (Modelos, Simulación y Visualización)

Repositorio personal donde exploro modelos matemáticos, simulaciones y visualizaciones interactivas con Python.

Aquí documento experimentos que combinan:

* Sistemas dinámicos
* Análisis numérico
* Visualización interactiva
* Visualización

---

# Proyectos

+ [Atractor de Lorenz](#atractor-de-lorenz)

+ [Péndulo simple](#péndulo-simple)
---
### Atractor de Lorenz

Simulación del sistema dinámico caótico conocido como Sistema de Lorenz, resuelto numéricamente con `scipy` y visualizado con `plotly`.

**Características de la exploración de Lorenz:**

* Resolución de ecuaciones diferenciales con `odeint`
* Visualización 3D interactiva
* Exploración de comportamiento caótico

**Visualización interactiva de Lorenz:**

[Explorar el atractor de Lorenz (interactivo)](https://omarsanvicente.github.io/Curiosidades/Interactive/lorenz_attractor.html)


---
# Péndulo simple

## Simulación de un Péndulo Simple

Este proyecto modela y simula el comportamiento dinámico de un **péndulo simple** mediante la solución numérica de una ecuación diferencial ordinaria (EDO). Se utiliza integración numérica para analizar la evolución temporal del sistema.

---

### Planteamiento del problema

Un péndulo simple consiste en una masa puntual suspendida de un hilo inextensible y sin masa, bajo la acción de la gravedad.

El sistema se describe mediante la siguiente ecuación diferencial no lineal:

$$
\frac{d^2 \theta}{dt^2} + \frac{g}{l} \sin(\theta) = 0
$$

Donde:

- $\theta(t)$: ángulo del péndulo respecto a la vertical  
- $g$: aceleración de la gravedad  
- $l$: longitud del péndulo  
---

### Reformulación del sistema

Para resolver esta ecuación con métodos numéricos, se transforma en un sistema de primer orden:

$$
\begin{cases}
\frac{d\theta}{dt} = \omega \\
\frac{d\omega}{dt} = -\frac{g}{l} \sin(\theta)
\end{cases}
$$

Donde:
$\omega$: velocidad angular  

---

### Parámetros del modelo

| Parámetro | Valor | Descripción |
|----------|------|------------|
| $g$ | 9.81 m/s² | Gravedad |
| $l$ | 1.0 m | Longitud del péndulo |
| $\theta_0$ | $\frac{\pi}{4}$ | Ángulo inicial |
| $\omega_0$ | 0.0 | Velocidad angular inicial |

---

### Método de solución

Se utiliza la función `odeint` de la librería **SciPy**, que implementa métodos de integración para sistemas de ecuaciones diferenciales ordinarias.

El sistema se evalúa en un intervalo de tiempo de:

$$
t \in [0, 10]
$$

con 100 puntos de discretización.

---

### Resultados

El script genera una gráfica que muestra:

- Evolución del ángulo $\theta(t)$
- Evolución de la velocidad angular $\omega(t)$

Esto permite observar el comportamiento oscilatorio del péndulo y su dinámica no lineal.

---

##  Objetivo del repositorio

Este repositorio no está enfocado en productos finales, sino en:

* Explorar conceptos matemáticos aplicados
* Desarrollar intuición sobre modelos dinámicos
* Construir visualizaciones que faciliten la interpretación

---
## Tecnologías utilizadas

* Python
* NumPy
* SciPy
* Plotly

