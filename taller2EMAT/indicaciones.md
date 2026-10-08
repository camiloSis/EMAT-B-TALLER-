# Indicaciones para el agente: reorganización del informe de probabilidad (LaTeX)

> **Documento a modificar:** el `.tex` principal del informe "Estadística matemática, probabilidades y métodos empíricos" (UNSA / EPIS, Grupo N.º 1). Estructura actual: Resumen, Abstract, Índice, 1 Introducción, 2 Marco Teórico, 3 Aplicaciones de probabilidades, 4 Conclusiones, Bibliografía.
> **Objetivo:** corregir la jerarquía del índice, ordenar el Marco Teórico por bloques lógicos, unificar el experimento y la notación de la sección de Aplicaciones, y corregir una afirmación invertida.
> **Idioma del documento:** español. Mantener el estilo y el tono existentes.

---

## 0. Reglas generales (leer antes de editar)

1. **Hacer una copia de respaldo** del `.tex` antes de tocar nada (p. ej. `informe.bak.tex`).
2. **No cambiar ningún resultado numérico ni ninguna fórmula matemática**, salvo donde este documento lo indique de forma explícita (tareas T2 y T7). Resultados que deben quedar idénticos: `1/12`, `1/132`, `7/12`, `5/12`, `2/7`, `1/5`, `2/3`, `1/3`, `7/22`, `35/66`, `5/33`, `25/144`, `35/72`, `49/144`, `5/6`.
3. **No tocar** el preámbulo, `portada.tex`, `referencias.bib`, los encabezados/pies de página ni las imágenes.
4. **No agregar citas, referencias bibliográficas ni distribuciones nuevas.** La integración de más distribuciones (Geométrica, Gamma, etc.) se hará en una tarea aparte; la estructura de este documento ya deja el lugar para ellas (ver §3).
5. Todo lo marcado **(OPCIONAL)** o **(PENDIENTE DEL USUARIO)** **no se ejecuta** sin confirmación expresa.
6. Cuando se mueva un bloque de texto, **moverlo completo y sin reescribirlo**, salvo los cambios indicados.
7. Tras terminar, ejecutar la verificación de §7.

---

## 1. Diagnóstico (qué está mal y por qué)

| N.º | Problema | Dónde | Tarea |
|---|---|---|---|
| 1 | **Jerarquía incorrecta:** "Modelos de distribución de probabilidad" es un `\subsubsection` dentro de "Variable aleatoria" (queda numerado 2.11.5). Una familia de modelos no es una parte de la definición de variable aleatoria; debe estar al mismo nivel. | Marco Teórico | T1 |
| 2 | **Las distribuciones no aparecen en el índice:** Bernoulli, binomial, Poisson, hipergeométrica, normal y exponencial son solo `\textbf{...}` dentro de un párrafo. Además, no hay separación entre discretas y continuas. | Marco Teórico | T1 |
| 3 | **Marco Teórico plano:** 11 `\subsection` seguidos (conteo, experimento, excluyentes, probabilidad, axiomas, teoremas, condicional, multiplicación, total, Bayes, variable aleatoria) sin agrupar por tema. | Marco Teórico | T1 |
| 4 | **Orden poco lógico:** "Técnicas de conteo" aparece antes de definir experimento, espacio muestral y evento. | Marco Teórico | T1 |
| 5 | **Afirmación invertida (error de contenido):** el último párrafo del Marco Teórico dice que "la primera [con reposición] se modela con una distribución hipergeométrica, mientras que la segunda [sin reposición] corresponde a una binomial". Es al revés (con reposición → binomial; sin reposición → hipergeométrica), y contradice la Introducción, las Conclusiones y la sección 3.5. Además es contenido de la aplicación, no de la teoría. | Final del Marco Teórico | T2 |
| 6 | **Dos "estuches" distintos:** la sección 3.1 define $S$ con 12 colores (azul, amarillo, rojo, verde, negro, blanco, anaranjado, morado, rosado, marrón, celeste, gris), pero las secciones 3.4 y 3.5 usan otro $\Omega$ de 12 colores (rojo, amarillo, azul, verde oscuro, verde claro, anaranjado, fucsia, marrón, rosa, celeste, negro, morado). Son listas incompatibles para "el mismo estuche". | Sección 3 | T3 |
| 7 | **El evento $A$ (colores primarios) de 3.1 nunca se vuelve a usar;** en 3.4 el mismo conjunto reaparece con otro nombre ($E$). La clasificación claros/oscuros se define dos veces (en 3.4 como $E_1,E_2$ y en 3.5 en prosa). | Sección 3 | T3 |
| 8 | **Colisión de símbolos:** $S$ (3.1–3.3) vs. $\Omega$ (3.4–3.5); $E$ significa "rojo en el 2.º intento" en 3.3 y "color primario" en 3.4; $C$ es "evento compuesto" en 3.3, "claro" en 3.5.2 y combinaciones ($C_r^n$) en el Marco Teórico. | Sección 3 | T4 |
| 9 | **Presentación inconsistente en 3.5:** la tabla sin reposición va en orden $x=0,1,2$ y la de con reposición en $x=2,1,0$; hay `itemize` de un solo ítem seguidos; las tablas usan `[h]` aunque `float` está cargado (pueden despegarse de su texto); falta un subapartado de comparación. | Sección 3.5 | T5 |
| 10 | **Términos usados en la sección 3 que el Marco Teórico no define:** "evento simple", "evento compuesto", "eventos independientes", "partición", y $\binom{n}{r}$ (el Marco solo introduce $C_r^n$). | Marco / Sección 3 | T7 |
| 11 | **Limpieza:** comentario obsoleto `% 4.3 APLICACIÓN DE PROBABILIDAD`, typo `% APLICACIOES BAYES`, comentario de la Introducción que dice "las dos variables del informe", títulos de subsecciones con nombres inconsistentes, uso de `$$...$$`. | Todo el archivo | T6 |

---

## 2. Principios de la nueva organización

- Orden lógico del Marco Teórico: **conjuntos/eventos → conteo → probabilidad → probabilidad condicional → variable aleatoria → modelos de distribución**.
- Profundidad máxima del índice: 3 niveles (`\section` > `\subsection` > `\subsubsection`), que el índice ya muestra por defecto en la clase `article`. No se usa `\paragraph` para nada que deba salir en el índice.
- La sección 3 (Aplicaciones) sigue el **mismo orden** que el Marco Teórico y define el experimento **una sola vez**.

---

## 3. Estructura objetivo (índice final esperado)

```
Resumen / Abstract            (sin numerar, como ahora)
Índice

1  Introducción

2  Marco Teórico
   2.1  Espacio muestral y eventos
        2.1.1  Experimento aleatorio, espacio muestral y evento
        2.1.2  Eventos mutuamente excluyentes
   2.2  Técnicas de conteo
        2.2.1  Permutaciones
        2.2.2  Combinaciones
        2.2.3  Permutaciones con repetición
   2.3  Probabilidad
        2.3.1  Probabilidad de un evento
        2.3.2  Axiomas de probabilidad
        2.3.3  Teoremas importantes sobre probabilidades
   2.4  Probabilidad condicional y teorema de Bayes
        2.4.1  Probabilidad condicional
        2.4.2  Regla de la multiplicación
        2.4.3  Probabilidad total
        2.4.4  Teorema de Bayes
   2.5  Variable aleatoria
        2.5.1  Tipos de variable aleatoria
        2.5.2  Función de distribución acumulada
        2.5.3  Esperanza matemática
        2.5.4  Varianza y desviación estándar
   2.6  Modelos de distribución discreta
        2.6.1  Distribución de Bernoulli
        2.6.2  Distribución binomial
        2.6.3  Distribución de Poisson
        2.6.4  Distribución hipergeométrica
        (aquí se insertarán después: Geométrica, Binomial negativa, Uniforme discreta, Multinomial)
   2.7  Modelos de distribución continua
        2.7.1  Distribución normal
        2.7.2  Distribución exponencial
        (aquí se insertarán después: Uniforme, Gamma, Chi-cuadrada, t de Student, F, Beta, Weibull, Lognormal)

3  Aplicaciones de probabilidad
   3.1  Contexto general del experimento
   3.2  Evento simple
   3.3  Evento compuesto
   3.4  Aplicación del teorema de Bayes
   3.5  Aplicación de variable aleatoria
        3.5.1  Caso sin reposición (distribución hipergeométrica)
        3.5.2  Caso con reposición (distribución binomial)
        3.5.3  Comparación entre ambos casos

4  Conclusiones
Bibliografía (heading=bibintoc, como ahora)
```

---

## 4. Tareas

### T1. Reestructurar la jerarquía del Marco Teórico

Conservar `\section{Marco Teórico}` y su párrafo introductor. Reordenar y reencabezar **sin modificar el texto interno** de cada bloque, según esta tabla (se busca por el encabezado actual):

| Encabezado actual | Nuevo encabezado y posición |
|---|---|
| `\subsection{Técnicas de conteo}` (con sus 3 `\subsubsection`) | Se **mueve** para quedar después de 2.1 y antes de 2.3. Sigue siendo `\subsection` (2.2). Sus tres `\subsubsection` y el párrafo del principio de multiplicación no cambian. |
| `\subsection{Experimento aleatorio, espacio muestral y evento}` | `\subsubsection{Experimento aleatorio, espacio muestral y evento}` dentro de un **nuevo** `\subsection{Espacio muestral y eventos}` (2.1, va primero). |
| `\subsection{Eventos excluyentes}` | `\subsubsection{Eventos mutuamente excluyentes}` (2.1.2). |
| *(nuevo)* | `\subsection{Probabilidad}` (2.3). |
| `\subsection{Probabilidad de un evento}` | `\subsubsection{Probabilidad de un evento}` (2.3.1). |
| `\subsection{Axiomas de probabilidad}` | `\subsubsection{Axiomas de probabilidad}` (2.3.2). |
| `\subsection{Teoremas importantes sobre probabilidades}` | `\subsubsection{...}` (2.3.3). |
| *(nuevo)* | `\subsection{Probabilidad condicional y teorema de Bayes}` (2.4). |
| `\subsection{Probabilidad condicional}` | `\subsubsection{...}` (2.4.1). |
| `\subsection{Regla de la multiplicación}` | `\subsubsection{...}` (2.4.2). |
| `\subsection{Probabilidad total}` | `\subsubsection{...}` (2.4.3). |
| `\subsection{Teorema de Bayes}` | `\subsubsection{...}` (2.4.4). |
| `\subsection{Variable aleatoria}` | **Sin cambios** (2.5). Conserva su texto de definición y sus 4 `\subsubsection` (Tipos, Función de distribución acumulada, Esperanza matemática, Varianza y desviación estándar). |
| `\subsubsection{Modelos de distribución de probabilidad}` | **Se elimina como encabezado.** Su párrafo introductor ("Las distribuciones de probabilidad describen cómo se asignan las probabilidades…") pasa a ser el primer párrafo de la nueva `\subsection{Modelos de distribución discreta}` (2.6). |
| `\textbf{Distribución de Bernoulli.}` | `\subsubsection{Distribución de Bernoulli}` (2.6.1); el texto que seguía en el mismo párrafo pasa a ser el primer párrafo de la subsección. |
| `\textbf{Distribución binomial.}` | `\subsubsection{Distribución binomial}` (2.6.2), igual que arriba. |
| `\textbf{Distribución de Poisson.}` | `\subsubsection{Distribución de Poisson}` (2.6.3). |
| `\textbf{Distribución hipergeométrica.}` | `\subsubsection{Distribución hipergeométrica}` (2.6.4). |
| *(nuevo)* | `\subsection{Modelos de distribución continua}` (2.7). |
| `\textbf{Distribución normal.}` | `\subsubsection{Distribución normal}` (2.7.1). |
| `\textbf{Distribución exponencial.}` | `\subsubsection{Distribución exponencial}` (2.7.2). |
| Último párrafo ("En el caso del taller, la comparación entre extracciones…") | **Sale del Marco Teórico** (ver T2). |

Detalles:

- El primer párrafo del nuevo 2.6 debe terminar con una frase de enlace: *"A continuación se presentan los modelos discretos; los modelos continuos se presentan en la Sección \ref{sec:continuas}."* Para ello agregar `\label{sec:continuas}` justo después de `\subsection{Modelos de distribución continua}`.
- Si algún bloque movido empieza con un `\clearpage` o `\newpage` suelto, no arrastrarlo.
- Mantener los `\clearpage` existentes entre secciones (antes de `\section{Marco Teórico}` y antes de `\section{Aplicaciones…}`).

### T2. Mover y **corregir** el párrafo invertido

1. Eliminar del final del Marco Teórico este párrafo exacto:
   > "En el caso del taller, la comparación entre extracciones con y sin reposición es particularmente relevante: la primera se modela con una distribución hipergeométrica, mientras que la segunda corresponde a una distribución binomial. Esta diferencia explica por qué, aunque el valor esperado pueda coincidir, las probabilidades de cada resultado son distintas en ambos escenarios."
2. Crear al final de la sección 3.5 el nuevo subapartado `\subsubsection{Comparación entre ambos casos}` (3.5.3) con este texto **corregido**:

```latex
\subsubsection{Comparación entre ambos casos}

La comparación entre las extracciones sin reposición y con reposición es particularmente relevante: la extracción sin reposición se modela con una distribución hipergeométrica, mientras que la extracción con reposición corresponde a una distribución binomial. Esta diferencia explica por qué, aunque el valor esperado coincide ($E(X)=5/6$ en ambos casos), las probabilidades de cada resultado son distintas en los dos escenarios.

\begin{table}[H]
    \centering
    \begin{tabular}{|c|c|c|}
        \hline
        $x_i$ & Sin reposición (hipergeométrica) & Con reposición (binomial) \\
        \hline
        0 & $\dfrac{7}{22}\approx 0.3182$  & $\dfrac{49}{144}\approx 0.3403$ \\[10pt]
        1 & $\dfrac{35}{66}\approx 0.5303$ & $\dfrac{35}{72}\approx 0.4861$ \\[10pt]
        2 & $\dfrac{5}{33}\approx 0.1515$  & $\dfrac{25}{144}\approx 0.1736$ \\
        \hline
        $E(X)$ & $\dfrac{5}{6}$ & $\dfrac{5}{6}$ \\
        \hline
    \end{tabular}
    \caption{Comparación de la distribución de probabilidad de $X$ según el tipo de extracción}
\end{table}
```

(Todos los valores de la tabla provienen de las tablas ya existentes en 3.5.1 y 3.5.2; no se calcula nada nuevo.)

### T3. Definir el experimento **una sola vez** (sección 3.1)

Decisión por defecto (confirmar con el usuario según **P1** de §6): usar como estuche canónico la lista de las secciones 3.4/3.5, porque de ella dependen todos los cálculos de Bayes y de variable aleatoria.

1. En **3.1**, reemplazar el contenido de la tabla `tabularx` por (mantener el formato `tabularx` actual con `\textbf{...} & ...`):
   - **Experimento:** Elegir un plumón al azar de un estuche de 12 plumones de colores.
   - **Espacio muestral ($\Omega$):** $\Omega=\{\text{rojo, amarillo, azul, verde oscuro, verde claro, anaranjado, fucsia, marrón, rosa, celeste, negro, morado}\}$, con $n(\Omega)=12$.
   - **Evento ($E$):** Escoger un color primario: $E=\{\text{rojo, azul, amarillo}\}$, con $n(E)=3$.
   - **Clasificación por tono:** los plumones se dividen en oscuros, $E_1=\{\text{verde oscuro, fucsia, marrón, azul, negro, rojo, morado}\}$ con $n(E_1)=7$, y claros, $E_2=\{\text{amarillo, rosa, celeste, anaranjado, verde claro}\}$ con $n(E_2)=5$. Los eventos $E_1$ y $E_2$ forman una partición de $\Omega$.
2. En **3.4 (Bayes):** eliminar la redefinición de $\Omega$, de $E_1$, de $E_2$ y de $E$ (los bloques `$$ \Omega = ... $$`, `$$ E_1 = ... $$`, `$$ E_2 = ... $$`, `$$ E = ... $$`). Sustituirlos por una sola oración:
   > "Se utiliza el estuche descrito en la Sección \ref{sec:contexto}, con el espacio muestral $\Omega$, la partición $\{E_1,E_2\}$ (plumones oscuros y claros) y el evento de interés $E$ (colores primarios)."
   Mantener intactos todos los cálculos: $P(E_1)=7/12$, $P(E_2)=5/12$, $P(E)=3/12$, $P(E\mid E_1)=2/7$, $P(E\mid E_2)=1/5$, y el desarrollo de $P(E_1\mid E)$ y $P(E_2\mid E)$. Agregar `\label{sec:contexto}` justo después de `\subsection{Contexto general del experimento}`.
3. En **3.5.1:** reemplazar la enumeración de colores entre paréntesis por una referencia: "…de los cuales $K=5$ son claros (evento $E_2$) y $12-K=7$ son oscuros (evento $E_1$)."
4. Al final de 3.4, **agregar una línea de interpretación** (las demás subsecciones de 3.2 y 3.3 la tienen y esta no), por ejemplo:
   > `\noindent\textbf{Interpretación:} si se sabe que el plumón extraído es de un color primario, la probabilidad de que sea oscuro es $2/3$ y la de que sea claro es $1/3$. Nótese que el denominador del teorema de Bayes coincide con $P(E)=3/12=1/4$ (probabilidad total).`

### T4. Unificar símbolos

| Cambio | Alcance |
|---|---|
| $S$ → $\Omega$ (y $S_1,S_2$ → $\Omega_1,\Omega_2$ en 3.3); eliminar "$n(S)$" a favor de "$n(\Omega)$". | Secciones 3.1, 3.2, 3.3 |
| En 3.3 renombrar los eventos: $D\to Y_1$ ("amarillo en el 1.er intento"), $E\to R_2$ ("rojo en el 2.º intento, dado que el primero fue amarillo"), $C\to Y_1\cap R_2$ (sin nombre propio). Ajustar todas las fórmulas: $P(Y_1\cap R_2)=P(Y_1)\,P(R_2\mid Y_1)$, etc. Resultado: $\tfrac1{12}\cdot\tfrac1{11}=\tfrac1{132}$. | Sección 3.3 |
| En 3.5, distinguir el espacio muestral de cada caso: usar $\Omega_{\text{sr}}$ (sin reposición, pares no ordenados) y $\Omega_{\text{cr}}$ (con reposición, $\{CC,CO,OC,OO\}$). | Secciones 3.5.1 y 3.5.2 |
| En el Marco Teórico, 2.2.2 Combinaciones: añadir la equivalencia con la notación del coeficiente binomial: $C_r^n=\binom{n}{r}=\dfrac{n!}{r!\,(n-r)!}$ (ver T7). | 2.2.2 |

### T5. Uniformizar la sección 3.5

1. **Orden de las tablas:** en la tabla del caso con reposición, ordenar las filas como $x=0,1,2$ (hoy está en $2,1,0$): `0 & 49/144`, `1 & 35/72`, `2 & 25/144`. Hacer lo mismo con la lista previa de probabilidades: `P(OO)`, `P(CO)`, `P(OC)`, `P(CC)`.
2. **Flotantes:** cambiar `\begin{table}[h]` por `\begin{table}[H]` en todo el documento (el paquete `float` ya está cargado).
3. **Estructura homogénea de los dos casos.** En 3.5.1 y 3.5.2, sustituir los `itemize` de un solo ítem (esperanza matemática e interpretación) y reorganizar con los mismos rótulos en negrita al inicio de párrafo, en este orden:
   - `\textbf{Espacio muestral y variable aleatoria.}`
   - `\textbf{Distribución de probabilidad.}` (lista de probabilidades + tabla)
   - `\textbf{Modelo.}` (identificación de la hipergeométrica / binomial y su fórmula particularizada)
   - `\textbf{Esperanza matemática.}`
   - `\textbf{Interpretación.}`
   El contenido de cada rótulo es el que ya existe; solo se redistribuye y se quitan los `itemize` sueltos.
4. **Títulos de 3.5.1 y 3.5.2:** `Caso sin reposición (distribución hipergeométrica)` y `Caso con reposición (distribución binomial)`.

### T6. Limpieza

1. Borrar el comentario `% 4.3 APLICACIÓN DE PROBABILIDAD` y su línea descriptiva; sustituir por `% 3. APLICACIONES DE PROBABILIDAD`. Agregar el banner faltante `% 2. MARCO TEÓRICO` antes de `\section{Marco Teórico}`.
2. Corregir el comentario `%------ APLICACIOES BAYES -------` → `% ---------- 3.4 Aplicación del teorema de Bayes ----------`.
3. En el comentario de la Introducción, cambiar "Anuncia las dos variables del informe" por "Anuncia el objetivo y la variable aleatoria $X$ del informe".
4. Reemplazar **todos** los `$$ ... $$` por `\[ ... \]` (mismo contenido, sin cambios matemáticos).
5. Renombrar `\section{Aplicaciones de probabilidades}` → `\section{Aplicaciones de probabilidad}` y `\subsection{Aplicación de variable aleatoria}` se mantiene. Los demás títulos de 3.x se mantienen como en §3.
6. Agregar `\label{sec:marco}` y `\label{sec:aplicaciones}` a esas secciones; en la Introducción, sustituir "la sección de aplicaciones" por "la Sección~\ref{sec:aplicaciones}". (No agregar más referencias cruzadas.)

### T7. Definiciones mínimas faltantes en el Marco Teórico

Insertar solo estos textos, en los lugares indicados (todos los demás párrafos quedan como están):

1. **En 2.1.1**, al final del párrafo (distinguir evento simple/compuesto):
   > "Un evento es \textbf{simple} si contiene un solo resultado del espacio muestral, y \textbf{compuesto} si contiene más de uno o se forma combinando otros eventos, por ejemplo mediante la intersección de eventos sucesivos."
2. **En 2.2.2 (Combinaciones)**, tras la fórmula $C_r^n$: añadir "que también se denota $\dbinom{n}{r}$ (coeficiente binomial)" y la igualdad $C_r^n=\binom{n}{r}$ (ver T4).
3. **En 2.4.2 (Regla de la multiplicación)**, antes de la fórmula de eventos independientes:
   > "Dos eventos $A$ y $B$ son \textbf{independientes} si la ocurrencia de uno no modifica la probabilidad del otro, es decir, si $P(B\mid A)=P(B)$."
4. **En 2.4.3 (Probabilidad total)**, después de "partición del espacio muestral":
   > "(es decir, los $E_i$ son mutuamente excluyentes y su unión es $\Omega$)"

---

## 5. (OPCIONAL — no aplicar sin confirmación)

**O1. Complementar 3.5 con varianza y función de distribución acumulada.** El Marco Teórico las presenta (2.5.2 y 2.5.4) y la Introducción menciona la acumulada, pero la aplicación solo calcula $E(X)$. Valores ya verificados:

| | Sin reposición (hipergeométrica) | Con reposición (binomial) |
|---|---|---|
| $F(0)$ | $21/66=7/22$ | $49/144$ |
| $F(1)$ | $56/66=28/33$ | $119/144$ |
| $F(2)$ | $1$ | $1$ |
| $\operatorname{Var}(X)$ | $\dfrac{175}{396}\approx0.4419$ | $\dfrac{35}{72}\approx0.4861$ |

Fórmulas a usar: hipergeométrica $\operatorname{Var}(X)=n\frac{K}{N}\left(1-\frac KN\right)\frac{N-n}{N-1}=2\cdot\frac5{12}\cdot\frac7{12}\cdot\frac{10}{11}$; binomial $\operatorname{Var}(X)=np(1-p)=2\cdot\frac5{12}\cdot\frac7{12}$. Esto refuerza el mensaje de 3.5.3: misma media, distinta varianza.

**O2. Corregir los axiomas (2.3.2).** El segundo axioma, "$0\le P(A)\le1$", no es un axioma (la cota superior es una consecuencia). Forma estándar (Kolmogorov): (i) $P(A)\ge0$; (ii) $P(\Omega)=1$; (iii) si $A$ y $B$ son mutuamente excluyentes, $P(A\cup B)=P(A)+P(B)$. Opcionalmente indicar que $0\le P(A)\le1$ se deduce de ellos.

**O3. Agregar al índice las entradas "Resumen" y "Abstract"** con `\addcontentsline{toc}{section}{Resumen}` / `{Abstract}` (hoy están sin numerar y no aparecen).

---

## 6. (PENDIENTE DEL USUARIO — el agente solo debe reportarlos, no resolverlos)

- **P1. Lista real de colores del estuche.** Hay dos listas distintas en el documento (ver §1, punto 6). T3 asume la de las secciones 3.4/3.5. Si el usuario indica que la correcta es la de 3.1, hay que rehacer $E_1$, $E_2$ y $E$ y recalcular Bayes y la variable aleatoria.
- **P2. Bibliografía vacía.** El documento no contiene ningún `\cite{...}`; `\printbibliography` saldrá vacío (con advertencia de biber) y la entrada del índice quedará sin contenido. El usuario debe decidir entre citar fuentes en el Marco Teórico o usar `\nocite{*}`. El agente **no debe** inventar citas ni editar `referencias.bib`.
- **P3. Integración de distribuciones adicionales** (archivo `modelos_distribucion_probabilidad.md`): se hará después. Las nuevas distribuciones entrarán como `\subsubsection` dentro de 2.6 (discretas) o 2.7 (continuas), en el orden indicado en §3.

---

## 7. Verificación final (checklist)

1. Compilar con la secuencia indicada en el encabezado del archivo: `pdflatex` → `biber` → `pdflatex` → `pdflatex`. Sin errores (`!`) y sin `Undefined control sequence`.
2. Revisar el log: ningún `LaTeX Warning: Reference ... undefined` (las etiquetas `sec:continuas`, `sec:contexto`, `sec:aplicaciones` deben resolverse). Se tolera la advertencia de biber por bibliografía vacía (ver P2).
3. El índice generado coincide con el árbol de §3 (mismos títulos, misma numeración).
4. `grep` de control: no queda ningún `$$`; no queda ningún `\textbf{Distribución ...}` usado como encabezado; la frase "la primera se modela con una distribución hipergeométrica" ya no existe; no queda ningún `n(S)` ni `S_1`/`S_2`.
5. Los resultados numéricos listados en §0.2 siguen apareciendo, sin cambios.
6. Ninguna tabla queda separada de su texto (todas con `[H]`) y las dos tablas de 3.5 están en orden $x=0,1,2$.
7. Entregar un resumen breve de lo realizado, listando por separado lo opcional que no se aplicó (§5) y los pendientes del usuario (§6).
