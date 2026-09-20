# CAPITULO II: TEORIA DE PROBABILIDADES

En la comunicación diaria estamos acostumbrados a hacer y a oír afirmaciones que llevan implícito el concepto de probabilidad como, por ejemplo: Los pronósticos meteorológicos nos indican las probabilidades de lluvias, de frio, etc. Los médicos nos dicen qué probabilidad hay de que nuestras enfermedades se curen con cierto tratamiento; los pedagogos especulan sobre las probabilidades de éxito en la Universidad de algunos estudiantes; los encuestadores políticos nos dicen que tan probable es que gane en unas elecciones nuestro candidato favorito, etc., etc.

El conocimiento de probabilidad permite que los individuos tomen decisiones bien documentadas acerca de su vida.

---

## II.1 TECNICAS DE CONTEO

Para el cálculo de probabilidades es necesario calcular el número de veces que ocurre un determinado evento. En muchas situaciones de importancia práctica es virtualmente imposible contar físicamente el número de ocurrencias de un evento. En estas situaciones es necesario y útil disponer de un método corto, rápido y eficaz para contar. Por tal motivo introducimos algunos conceptos como permutación y combinación.

### 1. EL PRINCIPIO DE LA MULTIPLICACION

Una técnica fundamental de conteo que se conoce es el de principio de la multiplicación; se puede establecer de la siguiente manera:

Si hay que hacer k operaciones y si la primera se puede hacer de n1 maneras, y si, no importando la forma en que se hizo la primera, la segunda operación se puede hacer de n2 maneras y si, no importando las formas en que se hicieron las dos primeras operaciones, la tercera operación se puede hacer de n3 maneras y así sucesivamente para las k operaciones, entonces la secuencia de k operaciones se puede hacer de (n1)(n2)…(nk) maneras, producto de los números individuales.

**EJEMPLO 2.1** Un empleado de una oficina que va todos los días a su centro de trabajo en su movilidad propia puede llegar desde su casa hasta la autopista por tres rutas diferentes (A, B, C). Luego puede tomar tres caminos diferentes para ir de la autopista al centro de la ciudad (I, II, III) y del centro de la ciudad hasta la cochera donde guarda su automóvil, se puede ir por dos rutas (1, 2). ¿Por cuántas rutas diferentes puede ir el empleado a su centro de trabajo?

### 2. PERMUTACIONES Y COMBINACIONES

#### 2.1 PERMUTACIONES

**DEFINICIÓN 1** Una permutación es uno de los diferentes arreglos en ordenaciones que se pueden hacer con todos o parte de los elementos de un conjunto

Se utiliza el concepto de permutación por ejemplo para determinar; el número de formas en que se les pueden asignar a los alumnos los asientos en una clase; el número de formas en que se pueden sentar en un escenario un grupo de conferencistas; el número de maneras en que se pueden colocar un grupo de libros en un instante, etc., etc.

El número de permutaciones de n objetos diferentes tomados los n a la vez es

$$P_n = n!$$

El número de permutaciones de n objetos tomados de r en r es

$$P_r^n = \frac{n!}{(n-r)!}$$

**Nota 1.-** Una característica de las permutaciones es que el orden en que se disponen los dos objetos es importante

#### 2.2 COMBINACION

**DEFINICIÓN 2** Una combinación es un arreglo de cierto número de objetos tomados de un conjunto de n objetos de tal forma que el orden en se disponen no importa.

El número de combinaciones de n objetos tomados de r en r está dado por

$$C_r^n = \frac{n!}{r!\,(n-r)!}$$

**EJEMPLO 2** Si tenemos las letras A, B, C, D, tenemos 6 subconjuntos de dos letras que es una combinación:

$$C_r^n = \frac{n!}{r!\,(n-r)!} = \frac{4!}{2!\,2!} = 6$$

$$\{A,B\}, \{A,C\}, \{A,D\}, \{B,C\}, \{B,D\}, \{C,D\}$$

**EJERCICIO 1**

1. obtener las permutaciones de conjunto {A, B, C, D}
2. obtener las combinaciones del conjunto {A, B, C, D}
3. haga la diferencia de combinación y permutación obtenidos

### 3. PERMUTACIONES CON REPETICIÓN

Hasta ahora hemos considerado objetos todos diferentes para su ordenamiento. Es posible algunas veces que se desee calcular el número de permutaciones de n objetos de los cuales n1 son del tipo 1, n2 del tipo 2 y nk son del tipo k, entonces la fórmula para calcular el número de ordenamientos distintos denotado por $P^{n}_{n_1,n_2,\ldots,n_k}$ es

$$P^{n}_{n_1,n_2,\ldots,n_k} = \frac{n!}{n_1!\,n_2!\,\ldots\,n_k!}$$

**EJEMPLO 3.** En un salón de la Cuna UNSA, hay 8 figuras, 3 cuadrados, 3 triángulos, y 2 círculos. ¿De cuántas maneras pueden ordenar los niños las figuras si quieren hacer con ellas una fila sobre la mesa?

**Solución:** Habrá

$$P^{n}_{n_1,n_2,\ldots,n_k} = \frac{8!}{3!\,3!\,2!} = 560 \text{ maneras}$$

---

## II.2 EXPERIMENTO

En estadística se denomina experimento aleatorio a un proceso de observación o medición cuyos resultados no se pueden determinar con anterioridad.

**EJEMPLO 4** Son ejemplos de experimentos

- a) El proceso de verificación si un interruptor está en posición de encendido o apagado.
- b) Encontrar las imperfecciones que hay en un rollo de tela
- c) Determinar la masa de un electrón
- d) El número de automóviles que pasan por el Puente Grau, en un intervalo de tiempo, por decir de 10.00 horas hasta las 15.00 horas
- e) El número de alumnos desaprobados en una prueba escrita, durante un semestre.
- f) Aplicar un estímulo a un organismo.
- g) Evaluar a un estudiante.
- h) Juegos de azar.
- j) fabricar artículos, hasta producir 7 defectuosos y contar el número total de artículos fabricados

### ESPACIO MUESTRAL

El conjunto de todos los posibles resultados de un experimento aleatorio se llama espacio muestral. Lo denotaremos por Ω o también por S

### EVENTO

Evento es un subconjunto del espacio muestral Ω.

**EJERCICIO 2** Sea el experimento clásico del lanzamiento de un par de dados, uno blanco y otro rojo, y observar sus resultados.

- a) ¿Cuál es el evento de que la suma sea impar?
- b) ¿Cuál es el evento de que la suma sea mayor o igual que 9?
- c) ¿Cuál es el evento de que la suma sea igual que 6?
- d) muestre gráficamente, alguno de los eventos anteriores

---

## II.3 EVENTOS EXCLUYENTES

Decimos que dos o mas eventos son mutuamente excluyentes, si en caso de ocurrir uno los otros no pueden ocurrir. Los eventos pasar y reprobar respecto de un examen determinado son mutuamente excluyentes puesto que ningún estudiante puede, al mismo tiempo pasar y reprobar un examen

---

## II.4 PROBABILIDAD DE UN EVENTO

Consideramos la definición clásica de probabilidad. Esta definición se basa en el supuesto de que todos los resultados posibles de un experimento aleatorio, tienen la misma probabilidad. Fue dada por Laplace en su obra "teoría analítica de las probabilidades" publicada en 1812.

**DEFINICIÓN 3** La probabilidad de un evento A ⊂ Ω se define por:

$$P(A) = \frac{n(A)}{n(\Omega)}, \quad P(A) \neq 0$$

Donde n(A), indica el número de casos favorables al evento A, n(Ω) es el número de casos posibles.

**Nota 5.-** la probabilidad del evento A, también se denota por P[A]

**EJEMPLO 5** Calcular la probabilidad de que al lanzar un dado dos veces consecutivos, la suma de los puntos obtenidos sea mayor o igual que nueve

**Solución:** Del ejemplo 5 parte b, podemos observar que el evento C tiene 5 elementos, entonces p(C)= 5/36, considerando que los dados son homogéneos claro está.

**EJERCICIO 3** En una compañía hay 4 varones y 6 damas, aspirantes a ser miembros de un comité. Si se deben escoger dos al azar escribiendo los nombres dentro de una urna. ¿cuál es la probabilidad de que ambos sean damas? ¿cuál es la probabilidad de que sea un varón y una dama?

Es importante conocer también la definición de probabilidad por frecuencia relativa que a continuación se proporciona.

**DEFINICIÓN 4** Si un experimento bien definido se repite n veces (n grande), entonces:

$$P(A) = \frac{n_A}{n}$$

donde $n_A$ es el número de veces que el evento A ocurre en los n ensayos, $\frac{n_A}{n}$ se acerca a la verdadera probabilidad de un evento cuando n aumenta indefinidamente, es decir

$$P(A) = \lim_{n \to \infty} \frac{n_A}{n}$$

Que es la definición de probabilidad por frecuencia relativa

**EJEMPLO 6** una muestra aleatoria de 7 fábricas que emplean un total de 7,000 trabajadores, mostró que ocurrieron 300 accidentes de trabajo durante el año pasado. Hallar la probabilidad de un accidente de trabajo en una fábrica determinada.

**Solución:** n=7,000, veces, A = {un accidente}, n(A)= 300, entonces

$$P(A) = \frac{300}{7000} = \frac{3}{70} = 0.0429$$

---

## II.5 AXIOMAS DE PROBABILIDAD

El tema de probabilidad se basa en tres reglas de sentido común, conocidas como axiomas:

1. P(Ω)=1, donde Ω es el espacio muestral
2. 0≤P(A)≤1, para cualquier A ⊂ Ω
3. Si A y B son mutuamente excluyentes, entonces P(A∪B) = P(A) + P(B)

**Nota 6.-** P(A) ∈ [0,1] para cualquier A ⊂ Ω

---

## II.6 ALGUNOS TEOREMAS IMPORTANTES SOBRE PROBABILIDADES

- **Teorema 1.** Si ∅ es el evento imposible, entonces P(∅) = 0.
- **Teorema 2.** Si A^c es el complemento de un evento A, entonces: P(A^c) = 1 − P(A).
- **Teorema 3.** Si A ⊂ B, entonces: P(A) ≤ P(B).
- **Teorema 4.** Si A y B son dos eventos, entonces: P(A−B) = P(A) − P(A∩B).
- **Teorema 5.** Si A y B son dos eventos cualesquiera, entonces: P(A∪B) = P(A) + P(B) − P(A∩B)

---

## II.5 PROBABILIDAD CONDICIONAL

$$P(B/A) = \frac{P(A \cap B)}{P(A)}, \quad P(A) \neq 0$$

**EJEMPLO 6** En el experimento del lanzamiento de un par de dados. Si el resultado del lanzamiento es una suma par. ¿Cuál es la probabilidad de que esta suma sea menor que 5?

**Solución:** Asumimos que los dados son homogéneos y sean los eventos A de que la suma sea par, B el evento de que la suma sea menor que 5, entonces

$$P(B/A) = \frac{P(A \cap B)}{P(A)} = \frac{2}{9}$$

### REGLA DE LA MULTIPLICACIÓN

Sean dos eventos A y B, entonces:

$$P(A \cap B) = P(A)\,P(B/A), \quad \text{si B depende de A}$$

$$P(A \cap B) = P(A)\,P(B), \quad \text{si A y B son dos eventos independientes.}$$

---

## II.6 PROBABILIDAD TOTAL

Sean $\{E_1, E_2, \ldots, E_n\}$ cualquier partición del espacio muestral Ω y sea $E$ cualquier evento, entonces:

$$P(E) = \sum_{i=1}^{n} P(E_i)\,P(E/E_i)$$

Siempre que $P(E_i) \neq 0$ ; $i = 1, 2, \ldots, n$

**EJEMPLO 7** El Departamento de Estadística de la UNSA (DAE) está formado por 20 docentes, donde se encuentran los siguientes datos:

- a) Estado Civil: 10 son casado, 6 mujeres son solteras y 4 hombres solteros.
- b) Sexo: 12 hombres y 8 mujeres
- c) Preferencia Política: 10 Apristas, 8 de UPP y 2 independientes.
- d) Grados: 10 Maestros, 5 Doctorados, 4 Licenciados y 1 bachilleres.

6 de los docentes casados, 3 de las mujeres solteras y 1 hombre soltero, son Apristas. Se selecciona al azar un docente del DAE ¿Cuál es la probabilidad de que sea Aprista?

**Solución:** En este ejemplo se observa una partición del DAE, de diferentes formas. Se sugiere que el estudiante, haga el diagrama respectivo de las particiones y hacer el comentario en cada caso.

Utilizando el teorema precedente; sean los eventos:

$$E_1 = \{\text{docentes casados}\} \qquad E_2 = \{\text{damas solteras}\} \qquad E_3 = \{\text{solteros}\}$$

$$E = \{\text{apristas}\}$$

Tenemos luego:

$$P(E) = P(E_1)\,P(E/E_1) + P(E_2)\,P(E/E_2) + P(E_3)\,P(E/E_3)$$

$$P(E) = \frac{10}{20} \cdot \frac{6}{10} + \frac{6}{20} \cdot \frac{3}{6} + \frac{4}{20} \cdot \frac{1}{4} = \frac{1}{2}$$

---

## II.7 TEOREMA DE BAYES

Sea el conjunto de eventos $\{E_1, E_2, \ldots, E_n\}$ una partición del espacio muestral Ω, donde $P(E_i) \neq 0$ ; $i = 1, 2, \ldots, n$. Entonces, para cualquier evento E para el que $P(E) \neq 0$ y para $1 \leq K \leq n$, tenemos:

$$P(E_k/E) = \frac{P(E_k)\,P(E/E_k)}{\sum_{i=1}^{n} P(E_i)\,P(E/E_i)}$$

**EJERCICIO 4** Considerando el ejemplo 2.7, Si el docente seleccionado es soltero, cual es la probabilidad de que sea Aprista.

**EJEMPLO 8** En la república del Perú el 55% de los votantes están registrados como Ollantistas y el 45% están registrados como Fujimoritas. Existen dos candidatos a la alcaldía de Lima. Un Ollantistas (O) y un Fujimorista (K). en la elección 80% de los Ollantistas y 10% de los fujimoristas votaron por O. el 20% de los Ollantistas y 90% de los fujimoristas votaron por K, si se selecciona al azar un votante y se encuentra que ha votado por K. ¿Cuál es la probabilidad de que sea Fujimorista?

**Solución:** Considerando el teorema de Bayes. Sean:

$$E_1 = \{\text{el votante es un ollantista}\}$$

$$E_2 = \{\text{el votante es fujimorista}\}$$

$$\bar{E} = \{\text{el votante dio su voto a } K\}$$

$$E = \{\text{el votante dio su voto a } O\}$$

$$P(E_2/E) = \frac{P(E_2)\,P(E/E_2)}{P(E_1)\,P(E/E_1) + P(E_2)\,P(E/E_2)}$$

$$P(E_2/E) = \frac{0.45 \times 0.90}{(0.55 \times 0.20) + (0.45) \times (0.90)} = 0.786$$

**EJERCICIO 5** Considerando el ejemplo (8) si se selecciona un votante al azar y se encuentra que ha votado por O, ¿cuál es la probabilidad de que sea Ollantista?
