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

+ [Dinámica de Poblaciones](#dinámica-de-poblaciones)
    + [Modelo de crecimiento exponencial](#modelo-de-crecimiento-exponencial-o-malthusiano)

    + [Modelo de crecimiento logístico](#modelo-de-crecimiento-lógistico-o-ecuación-de-verhulst)
    
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



### Resultados

El script genera una gráfica que muestra:

- Evolución del ángulo $\theta(t)$
- Evolución de la velocidad angular $\omega(t)$

Esto permite observar el comportamiento oscilatorio del péndulo y su dinámica no lineal.

![Movimiento Oscilatorio](/Images/pendulum.png)
*Figura 1:Posición y velocidad angular de un péndulo armónico simple.*

---
# Dinámica de poblaciones
El objetivo solo es mostrar el funcionamiento de distintos modelos de población.
## Modelo de crecimiento exponencial o malthusiano
Este modelo se basa en la suposición de que el crecimiento debe ser siempre creciente y no se detiene con nada, esta suposición es cierta hasta cierto punto y para unas poblaciones es mas real que para otras, pongamos por ejemplo el crecimiento humano, este siempre se vera limitado por el entorno, muchas veces es díficil conseguir alimentos o donde vivir, por lo que el crecimiento se ve "frenado" o relantizado, cada población dependiendo de sus circunstancias tiene un nivel límite al que puede crecer de esta manera.
### Planteamiento del problema
El modelo:
Recordemos la deducción para este tipo de problemas.
Suponemos que la población crece de modo proporcional al tiempo


$$
\frac{dN(t)}{dt} = k\cdot N(t)
$$

Donde $k$ es la tasa de crecimiento de la población.

Esto corresponde a una ecuación de variables separables, resolviendo se tiene que:

$$
N(t) = N_0\cdot e^{kt}
$$

Finalmente podemos ver las visualizaciones de los dos modelos desplegados:
Crecimiento bacteriano exponencial:

![Crecimiento bacteriano](/Images/crecimiento_bacteriano_exponencial.png)
*Figura 2: Crecimiento bacteriano bajo modelo exponencial.*

Crecimiento bacteriano exponencial E.Coli

![Crecimiento bacteriano real](/Images/crecimiento_bacteriano_duplicacion.png)
*Figura 3: Crecimiento bacteriano bajo modelo exponencial de E. Coli, la población se duplica cada determinado periodo T.*


## Modelo de crecimiento lógistico o ecuación de Verhulst

El modelo de crecimiento exponencial:

$$
\frac{dN}{dt} = rN
$$

describe un crecimiento ilimitado, lo cual no es realista en sistemas donde existen restricciones de recursos.



## 2. Formulación del modelo logístico

Para incorporar limitaciones, se introduce un factor de saturación:

$$
\left(1 - \frac{N}{K}\right)
$$

donde:
- $ N(t) $: tamaño de la población
- $  r $: tasa de crecimiento intrínseca
- $ K $: capacidad de carga

La ecuación de Verhulst queda:

$$
\frac{dN}{dt} = rN\left(1 - \frac{N}{K}\right)
$$

---

## 🔧 3. Solución de la ecuación diferencial

### Paso 1: Separación de variables

$$
\frac{dN}{N(1 - N/K)} = r\,dt
$$



### Paso 2: Fracciones parciales

$$
\frac{1}{N(1 - N/K)} = \frac{1}{N} + \frac{1}{K - N}
$$



### Paso 3: Integración

$$
\int \left( \frac{1}{N} + \frac{1}{K - N} \right) dN = \int r\,dt
$$

$$
\ln|N| - \ln|K - N| = rt + C
$$



### Paso 4: Simplificación

$$
\ln\left(\frac{N}{K - N}\right) = rt + C
$$



### Paso 5: Solución explícita

$$
\frac{N}{K - N} = Ae^{rt}
$$

$$
N(t) = \frac{K}{1 + Ae^{-rt}}
$$

donde $ A $ depende de la condición inicial.

Si tomamos $N(0) = N_0 $

Haciendo un poco de álgebra tendremos que:

$$
N = \frac{N_0\cdot K\cdot e^{rt}}{K+N_0( e^{rt}-1)}
$$
---
## 4. Interpretación

La solución es una función sigmoide con tres fases:

1. Crecimiento exponencial inicial $ N \ll K $
2. Desaceleración por competencia  
3. Saturación $ N \to K $

Además:

$$
\lim_{t \to \infty} N(t) = K
$$

---

## 5. Interpretación estructural

La ecuación también puede escribirse como:

$$
\frac{dN}{dt} = rN - \frac{r}{K}N^2
$$

- $rN $: crecimiento
- $ -\frac{r}{K}N^2 $: competencia entre individuos

Se puede observar en las familias de soluciones del modelo logístico que una población siempre estara sujeta al nivel de carga sinergetica que pueda soportar el sistema, esto quiere decir que el crecimiento siempre estara regulado.

![Crecimiento Logistico](/Images/familias_logistico.png)
*Figura 4: Crecimiento y decrecimiento de poblaciones, cuando una poblacion inicia por encima del nivel de carga sinergetica, esta decrece hasta el nivel de carga sinergetica del sistema, cuando por el contrario la población inicia por debajo del nivel de carga sinergetica, esta puede crecer hasta el nivel de carga sinergetica $K$ del sistema.*

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

