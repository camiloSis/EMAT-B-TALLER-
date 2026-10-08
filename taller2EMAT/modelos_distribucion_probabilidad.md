# Modelos de distribución de probabilidad — Material verificado para Marco Teórico

> **Fuente base:** *Modelos de distribución de probabilidad*, versión 2.0. Dra. Antonia Quispe Mamani. Arequipa, Perú, agosto de 2025 (PDF `M_DP_pptx.pdf`, 62 diapositivas).
> **Verificación realizada:** (1) recálculo numérico de todos los ejemplos con Python/SciPy; (2) contraste de fórmulas y parametrizaciones con fuentes externas (ver §8).
> **Idioma:** español. **Decimales:** punto (`0.0781`), como en el PDF.

---

## 0. Instrucciones para el agente que integra esto en LaTeX

1. **Usar siempre las fórmulas de este archivo, no las del PDF original.** El PDF tiene errores (listados en §7). Donde hay corrección, aparece marcada con **⚠ Corrección**.
2. Etiquetas usadas en este archivo:
   - **[PDF]** = contenido presente en la presentación de la docente (ya verificado).
   - **[COMPL]** = complemento verificado que **no** está en el PDF (propiedades, relaciones, parametrizaciones). Incluirlo es opcional pero recomendable para un marco teórico completo.
   - **⚠ Corrección** = el PDF dice algo distinto o erróneo; se indica lo correcto.
3. Convenciones de notación (mantener uniformes en todo el documento):
   - $X$: variable aleatoria; $x$: valor observado.
   - $p$: probabilidad de éxito; $q = 1-p$: probabilidad de fracaso.
   - $E(X)$: esperanza (media, $\mu$); $\operatorname{Var}(X)$: varianza ($\sigma^2$).
   - $\Phi(z)$: función de distribución de la normal estándar; $F(x)=P(X\le x)$: función de distribución acumulada (FDA).
   - $\binom{n}{x}=\dfrac{n!}{x!\,(n-x)!}$.
4. Todas las fórmulas están en LaTeX estándar (`$...$` en línea, `$$...$$` en bloque), listas para copiar.
5. Los **ejemplos resueltos** están pensados para una subsección "Ejemplo" tras cada distribución. Los **ejercicios que el PDF deja sin resolver** figuran con su respuesta calculada dentro de cada distribución (tablas de ejercicios de $\chi^2$, $t$, $F$, lognormal) y, para la normal, en §6 (úsense solo si el marco teórico lleva ejemplos; si no, omitir).

---

## 1. Conceptos generales [COMPL]

**Variable aleatoria discreta.** Toma valores en un conjunto finito o numerable. Se describe con su **función de probabilidad (fdp o pmf)** $p(x)=P(X=x)$:

$$p(x)\ge 0,\qquad \sum_x p(x)=1,\qquad F(x)=P(X\le x)=\sum_{t\le x}p(t)$$

$$E(X)=\sum_x x\,p(x),\qquad \operatorname{Var}(X)=E(X^2)-[E(X)]^2$$

**Variable aleatoria continua.** Toma valores en un intervalo. Se describe con su **función de densidad** $f(x)$:

$$f(x)\ge 0,\qquad \int_{-\infty}^{\infty}f(x)\,dx=1,\qquad P(a\le X\le b)=\int_a^b f(x)\,dx$$

$$E(X)=\int_{-\infty}^{\infty}x f(x)\,dx,\qquad \operatorname{Var}(X)=E(X^2)-[E(X)]^2$$

En el caso continuo $P(X=x)=0$; **la probabilidad es el área bajo la curva** (idea de la diapositiva 27 [PDF]: "PROBABILIDAD → ÁREA").

**Clasificación de los modelos del PDF (diap. 2 y 24):**

| Discretos | Continuos |
|---|---|
| Bernoulli, Binomial, Poisson, Hipergeométrica, Geométrica, Binomial negativa, Uniforme discreta, Multinomial | Normal, Exponencial, Uniforme continua, Gamma, Chi-cuadrada, $t$ de Student, $F$ de Fisher–Snedecor, Beta, Weibull, Lognormal |

> ⚠ **Corrección:** la diapositiva 24 incluye "Distribución Binomial Negativa" en la lista de modelos **continuos**. Es una distribución **discreta** (aparece correctamente en la lista discreta y en la diap. 17).

---

# PARTE I — MODELOS DE DISTRIBUCIÓN DISCRETA

## 2.1 Distribución de Bernoulli [PDF diap. 7–8]

**Experimento:** un solo ensayo con dos resultados mutuamente excluyentes: éxito (1) o fracaso (0).

$$P(X=1)=p,\qquad P(X=0)=1-p=q$$

Forma compacta [COMPL]: $P(X=x)=p^{x}(1-p)^{1-x},\; x\in\{0,1\}$.

$$E(X)=p,\qquad \operatorname{Var}(X)=p(1-p)=pq$$

> ⚠ **Corrección:** el PDF (diap. 7) escribe $\operatorname{Var}(X)=1-p$. Lo correcto es $\operatorname{Var}(X)=p(1-p)$. Verificación: $E(X^2)=p$ ⇒ $\operatorname{Var}=p-p^2$.

**Función de distribución [PDF]:**

$$F(x)=\begin{cases}0, & x<0\\[2pt] 1-p, & 0\le x<1\\[2pt] 1, & x\ge 1\end{cases}$$

**Ejemplos [PDF]:**

1. Dado, éxito = sacar 6: $P(X=1)=\tfrac16$; probabilidad de fracaso $P(X=0)=\tfrac56$.
2. Máquina con 3 % de piezas defectuosas; éxito = pieza no defectuosa: $P(\text{no defectuosa})=1-0.03=0.97$ *(el PDF plantea la pregunta sin resolverla)*.

---

## 2.2 Distribución Binomial [PDF diap. 3–6]

**Experimento:** $n$ ensayos de Bernoulli independientes, con la misma probabilidad de éxito $p$. $X$ = número de éxitos.

$$b(x;n,p)=P(X=x)=\binom{n}{x}p^{x}(1-p)^{n-x},\qquad x=0,1,\dots,n$$

$$E(X)=np,\qquad \operatorname{Var}(X)=npq,\qquad q=1-p$$

**Propiedades [COMPL]:** $X=\sum_{i=1}^{n}X_i$ con $X_i\sim\text{Bernoulli}(p)$ independientes; Bernoulli es el caso $n=1$; la gráfica es simétrica si $p=0.5$ (diap. 3: $p=0.5$, $n=40,80,160$, se acerca a una forma de campana al crecer $n$).

**Casos donde se presenta [PDF diap. 4]:** lanzamiento de una moneda regular (cara/sello); siembra de una semilla (germina/no germina); circuito eléctrico (funciona/no funciona); selección de un equipo (gana/pierde); pacientes que sobreviven a una intervención; selección de un producto (bueno/malo); inoculación de un paciente (se recupera/no se recupera); ordenadores de una subred infectados por un virus; mensajes a 100 destinatarios.

**Ejemplos resueltos (verificados):**

1. Dado lanzado 7 veces; éxito = salir 5 ($p=\tfrac16$). $P(X=3)$:
$$P(X=3)=\binom{7}{3}\left(\tfrac16\right)^{3}\left(\tfrac56\right)^{4}=0.0781$$
2. Exactamente 2 caras en 12 lanzamientos de moneda equilibrada ($p=\tfrac12$) *(sin resolver en el PDF)*:
$$P(X=2)=\binom{12}{2}\left(\tfrac12\right)^{12}=\frac{66}{4096}=\frac{33}{2048}\approx 0.0161$$
3. Moneda lanzada 6 veces; éxito = cara ($n=6$, $p=\tfrac12$):
   - a) $P(X=3)=b(3;6,\tfrac12)=\tfrac{20}{64}=\tfrac{5}{16}=0.3125$
   - b) $P(X\ge4)=b(4;6,\tfrac12)+b(5;6,\tfrac12)+b(6;6,\tfrac12)=\tfrac{15}{64}+\tfrac{6}{64}+\tfrac{1}{64}=\tfrac{22}{64}=\tfrac{11}{32}=0.34375$
   - c) $P(X\le2)=F(2)=\tfrac{1+6+15}{64}=\tfrac{11}{32}=0.34375$
   - d) $P(X\le4)=F(4)=\tfrac{1+6+15+20+15}{64}=\tfrac{57}{64}=0.890625$

> ⚠ **Corrección (diap. 6, inciso b):** el PDF escribe $b(4,6;\tfrac12)=\tfrac{11}{64}$. El valor correcto es $\tfrac{15}{64}$ ($\binom64=15$). El resultado final $\tfrac{11}{32}$ del PDF sí es correcto (suma $\tfrac{22}{64}$). Los incisos c) y d) están solo planteados en el PDF ($F(2)$, $F(4)$); los valores de arriba están calculados.

---

## 2.3 Distribución de Poisson [PDF diap. 9–11]

**Modelo:** número de eventos que ocurren en un intervalo de tiempo o región del espacio, con tasa media constante.

$$P(X=x)=\frac{\lambda^{x}e^{-\lambda}}{x!},\qquad x=0,1,2,\dots$$

$$E(X)=\lambda,\qquad \operatorname{Var}(X)=\lambda$$

$\lambda$ = número promedio de eventos esperados por unidad de tiempo o de espacio [PDF]. Si la tasa es $\nu$ por unidad y el intervalo mide $t$, entonces $\lambda=\nu t$ [COMPL]. En la diap. 10 se grafican $\lambda=1,4,10$ (la distribución se desplaza a la derecha y se vuelve más simétrica al crecer $\lambda$).

**Casos donde se presenta [PDF diap. 10]:** pacientes que llegan a un consultorio en un lapso dado; llamadas a un servicio de urgencias durante 1 hora; células anormales en una superficie histológica o glóbulos blancos en un milímetro cúbico de sangre; glóbulos blancos en una gota de sangre (suceso = observar un glóbulo blanco; "intervalo" continuo = una gota).

**Aproximación de la binomial por Poisson [COMPL]:** si $n$ es grande y $p$ pequeño, $b(x;n,p)\approx P(x;\lambda=np)$ (regla usual: $n\ge 50$ y $np\le 5$, o $n$ grande con $p\le 0.05$).

**Ejemplo resuelto [PDF diap. 11]:** probabilidad de insolación en un desfile $=0.005$; asisten $3000$ personas. $P(X=18)$ con $\lambda=3000(0.005)=15$:

$$P(18;15)=\frac{15^{18}e^{-15}}{18!}=0.0706$$

Verificación: la binomial exacta $b(18;3000,0.005)=0.0707$, coherente con la aproximación.

---

## 2.4 Distribución Hipergeométrica [PDF diap. 12–13]

**Modelo:** muestreo **sin reemplazamiento** de una población finita con dos tipos de elementos; frecuente en control de calidad.

$$P(X=x)=\frac{\binom{k}{x}\binom{N-k}{n-x}}{\binom{N}{n}}$$

donde:

- $N$: cantidad de elementos de la población
- $n$: número de elementos de la muestra
- $k$: cantidad de elementos de la población que cumplen la característica
- $x$: éxitos obtenidos en la muestra

Soporte exacto [COMPL]: $\max(0,\,n-(N-k))\le x\le \min(n,k)$. *(El PDF indica "$x=0,1,\dots,n$", válido solo cuando $n\le k$ y $n\le N-k$.)*

$$E(X)=\frac{nk}{N},\qquad \operatorname{Var}(X)=n\,p\,q\left(\frac{N-n}{N-1}\right),\quad p=\frac{k}{N},\; q=1-p$$

El factor $\frac{N-n}{N-1}$ es la **corrección por población finita** [COMPL]. Si $N$ es grande respecto a $n$ (regla usual $n/N<0.05$), la hipergeométrica se aproxima por la binomial con $p=k/N$.

**Ejemplo resuelto [PDF diap. 13]:** fiesta con 20 personas (14 casadas, 6 solteras); se eligen 3 al azar. $P(\text{las 3 solteras})$ con $N=20,\,k=6,\,n=3,\,x=3$:

$$P(X=3)=\frac{\binom{6}{3}\binom{14}{0}}{\binom{20}{3}}=\frac{20}{1140}=\frac1{57}\approx 0.0175$$

---

## 2.5 Distribución Geométrica [PDF diap. 14–16]

**Modelo:** secuencia de ensayos de Bernoulli independientes; distribución del **tiempo de espera hasta el primer éxito**. $X$ = número del ensayo en que ocurre el primer éxito.

$$P(X=x)=(1-p)^{x-1}p,\qquad x=1,2,3,\dots$$

$$E(X)=\frac1p,\qquad \operatorname{Var}(X)=\frac{1-p}{p^{2}}\qquad\text{[COMPL]}$$

$$F(x)=P(X\le x)=1-(1-p)^{x}\quad\text{[COMPL]}$$

> ⚠ **Aclaración de parametrización:** el PDF dice "$X$ es el número de intentos *o fallas antes* del primer éxito", lo cual mezcla dos convenciones:
> - **(a)** $X$ = número de **ensayos** hasta el primer éxito: $P(X=x)=q^{x-1}p$, $x=1,2,\dots$, $E(X)=1/p$. *(Es la que usa el PDF en la fórmula y el ejemplo; usar esta.)*
> - **(b)** $Y=X-1$ = número de **fallas** antes del primer éxito: $P(Y=y)=q^{y}p$, $y=0,1,\dots$, $E(Y)=q/p$.

**Propiedad [COMPL]:** carece de memoria, $P(X>m+n\mid X>m)=P(X>n)$.

**Gráficos [PDF diap. 16]:** función de masa y función de distribución acumulada para $p=0.1$ (la masa decrece geométricamente; la acumulada crece hacia 1).

**Ejemplo resuelto [PDF diap. 15]:** dado lanzado hasta que aparece un 6 ($p=\tfrac16$). $P(\text{necesitar exactamente 3 lanzamientos})$:

$$P(X=3)=\left(\tfrac56\right)^{3-1}\left(\tfrac16\right)=\frac{25}{216}=0.1157$$

---

## 2.6 Distribución Binomial Negativa [PDF diap. 17–19]

**Modelo:** se repiten ensayos independientes de Bernoulli (resultados $A$ con $P(A)=p$ y no $A$ con $P(\text{no }A)=q$) **hasta conseguir $r$ éxitos**. Si $r=1$ se obtiene la distribución geométrica. $X$ = número de **ensayos** necesarios para conseguir los $r$ éxitos.

$$P(X=x)=\binom{x-1}{r-1}p^{r}(1-p)^{x-r},\qquad x=r,\,r+1,\,r+2,\dots;\quad r>0$$

$$E(X)=\frac{r}{p},\qquad \operatorname{Var}(X)=\frac{r\,q}{p^{2}}=\frac{r}{p}\left(\frac1p-1\right)$$

> ⚠ **Corrección (diap. 18):** el PDF da $\mu=\dfrac{rq}{p}$ junto con $\sigma^2=\dfrac{r}{p}\left(\dfrac1p-1\right)$ para la variable "número de pruebas" $X$. Eso es inconsistente: $\mu=rq/p$ corresponde al número de **fallas** $Y=X-r$, no a $X$. Para $X$ (número de ensayos, la definición usada en el PDF):
> - $E(X)=r/p$ y $\operatorname{Var}(X)=rq/p^2$.
> - Para $Y=X-r$ (número de fallas antes del $r$-ésimo éxito): $E(Y)=rq/p$ y $\operatorname{Var}(Y)=rq/p^2$ (la varianza es la misma).
>
> Además, el PDF usa indistintamente "$k$ éxitos" y "$r$ éxitos"; unificar con **$r$**.

**Parametrización alternativa [COMPL]:** muchos programas (R, SciPy) definen la binomial negativa como el número de **fallas** $Y=0,1,2,\dots$: $P(Y=y)=\binom{y+r-1}{y}p^{r}q^{y}$. Conviene declarar cuál se usa.

**Gráfica [PDF diap. 18]:** $p=0.5$ y $p=0.3$ con $r=5$ y $r=10$ (el centro se desplaza a la derecha al disminuir $p$ o aumentar $r$).

**Ejemplo resuelto [PDF diap. 19]:** 10 % de una población grande padece una enfermedad; se necesitan $r=10$ afectados. $X$ = número de personas seleccionadas hasta tener los 10 afectados. $R_X=\{10,11,\dots\}$, $p=0.10$.

$$P(X=x)=\binom{x-1}{9}(0.10)^{10}(0.90)^{x-10}$$

$$P(X=15)=\binom{14}{9}(0.10)^{10}(0.90)^{5}=2002\times10^{-10}\times0.59049\approx 1.18\times10^{-7}$$

> ⚠ **Corrección (diap. 19):** el PDF sustituye $(0.10)^{10}$ por $0.0001$ (que es $10^{-4}$) y concluye $0.2002\times0.59$. En realidad $(0.10)^{10}=10^{-10}$. El valor correcto es $\approx 1.18\times10^{-7}$ (muy pequeño: con $p=0.1$ se esperan $E(X)=r/p=100$ selecciones, así que terminar en 15 es extremadamente raro).

---

## 2.7 Distribución Uniforme discreta [PDF diap. 20–21]

**Modelo:** $n$ valores $x_1,\dots,x_n$ equiprobables.

$$f_X(x)=P(X=x)=\begin{cases}\dfrac1n, & x=x_1,x_2,\dots,x_n\\[4pt] 0, & \text{en otro caso}\end{cases}$$

Para $X\in\{1,2,\dots,n\}$ [COMPL]: $E(X)=\dfrac{n+1}{2}$, $\operatorname{Var}(X)=\dfrac{n^{2}-1}{12}$.

*(El PDF numera esta sección como "6", igual que la binomial negativa; corresponde a la 7.ª en la lista discreta.)*

**Gráfico [PDF diap. 20]:** distribución de las caras de un dado (6 barras de altura $\tfrac16\approx0.1667$).

**Ejemplos [PDF diap. 21; resueltos aquí]:**

1. Dado regular, $P(X=x)=\tfrac16$ para $x\in\{1,\dots,6\}$. $P(X\le4)=\tfrac46=\tfrac23\approx0.667$.
2. Bolilla al azar de $\{1,\dots,20\}$: $P(X\ge7)=\tfrac{14}{20}=\tfrac{7}{10}=0.7$.
3. Bombillas de 40, 60, 75 y 100 watts, equiprobables: $P(X=x)=\tfrac14$ para $x\in\{40,60,75,100\}$ y $0$ en otro caso.

---

## 2.8 Distribución Multinomial [PDF diap. 22–23]

**Modelo:** generalización de la binomial cuando cada ensayo tiene $k>2$ resultados posibles. Denotación [PDF]: $f(x_1,x_2,\dots,x_k;\,n,p_1,p_2,\dots,p_k)$.

$$f(x_1,\dots,x_k;\,n,p_1,\dots,p_k)=\frac{n!}{x_1!\,x_2!\cdots x_k!}\;p_1^{x_1}p_2^{x_2}\cdots p_k^{x_k}$$

con $\displaystyle n=\sum_{i=1}^{k}x_i$ y $\displaystyle\sum_{i=1}^{k}p_i=1$; cada categoría $i$ tiene probabilidad de ocurrencia $p_i$.

> ⚠ **Corrección (diap. 22):** el denominador del PDF termina en "$x_3!$"; debe terminar en **$x_k!$**.

**Momentos por categoría [COMPL]:** $E(X_i)=np_i$, $\operatorname{Var}(X_i)=np_i(1-p_i)$, $\operatorname{Cov}(X_i,X_j)=-np_ip_j$ ($i\ne j$). Para $k=2$ se obtiene la binomial.

**Ejemplo resuelto [PDF diap. 23]:** donación de órganos: 15 % en contra ($p_1=0.15$), 40 % indiferentes ($p_2=0.40$), 45 % a favor ($p_3=0.45$). Muestra de $n=20$. $P(5\text{ en contra},\,10\text{ indiferentes},\,5\text{ a favor})$:

$$P(x_1=5,\,x_2=10,\,x_3=5)=\frac{20!}{5!\,10!\,5!}\,(0.15)^{5}(0.40)^{10}(0.45)^{5}=46\,558\,512\times(0.15)^5(0.40)^{10}(0.45)^5\approx 0.0068$$

> ⚠ **Corrección (diap. 23):** el PDF escribe $x_2=5$ en el planteamiento (debe ser $x_2=10$, pues $5+10+5=20$) y da como resultado $0.41$. El valor correcto es $\approx 0.0068$ (≈ 0.68 %). Además el PDF escribe $(0.40^{10})$ y $(0.15^5)$ como si fueran exponentes de toda la base; entender $(0.40)^{10}$, $(0.15)^5$, $(0.45)^5$.

---

# PARTE II — MODELOS DE DISTRIBUCIÓN CONTINUA

## 3.1 Distribución Normal [PDF diap. 25–33]

### 3.1.1 Definición

$$f(x)=\frac{1}{\sigma\sqrt{2\pi}}\exp\!\left[-\frac{(x-\mu)^{2}}{2\sigma^{2}}\right],\qquad -\infty<x<\infty$$

con parámetros $\mu\in\mathbb R$ y $\sigma>0$; $E(X)=\mu$, $\operatorname{Var}(X)=\sigma^{2}$. Se escribe $X\sim N(\mu,\sigma^{2})$.

> Nota de notación: la diap. 25 escribe el exponente como "$-1/2\,(x-\mu)^2/\sigma^2$"; la forma correcta y sin ambigüedad es la de arriba.

**Gráfica [PDF diap. 25]:** "campana de Gauss", simétrica respecto a $\mu$, con puntos de inflexión en $\mu\pm\sigma$.
**Propiedades [COMPL]:** media = mediana = moda $=\mu$; regla empírica: $P(|X-\mu|\le\sigma)\approx0.683$, $P(|X-\mu|\le2\sigma)\approx0.954$, $P(|X-\mu|\le3\sigma)\approx0.997$.

### 3.1.2 Normal estandarizada [PDF diap. 26]

$$Z=\frac{X-\mu}{\sigma}\sim N(0,1),\qquad f(z)=\frac{1}{\sqrt{2\pi}}\,e^{-z^{2}/2},\qquad \mu=0,\;\sigma^{2}=1$$

### 3.1.3 Cálculo de probabilidades como áreas [PDF diap. 27–29]

$$P(Z\le k)=\Phi(k)=\int_{-\infty}^{k}\frac{1}{\sqrt{2\pi}}e^{-z^{2}/2}\,dz$$

**Atención con la tabla de la diap. 29:** es una tabla de **áreas de 0 a $z$**, es decir $P(0\le Z\le z)=\Phi(z)-0.5$ (encabezado "Áreas bajo la curva normal tipificada de 0 a $Z$"; filas = $z$ hasta décimas, columnas = centésimas). Reglas de uso [COMPL]: $P(Z\ge z)=0.5-A(z)$, $P(Z\le -z)=P(Z\ge z)$, $P(a\le Z\le b)=\Phi(b)-\Phi(a)$.

### 3.1.4 Ejemplo de aplicación [PDF diap. 30]

C.I. $\sim N(100,\,10^{2})$. Proporción con C.I. mayor que 125:

$$P(X\ge125)=P\!\left(Z\ge\frac{125-100}{10}\right)=P(Z\ge2.5)=0.0062$$

Es decir, el 0.62 % de la población tiene C.I. mayor a 125 (valor exacto $0.00621$).

### 3.1.5 Aproximación de la binomial a la normal [PDF diap. 31–33]

Una binomial es suma de $n$ Bernoulli independientes, $X=\sum X_i$, con $E(X)=np$ y $\operatorname{Var}(X)=npq$. Por el **teorema del límite central**:

$$Z=\frac{X-np}{\sqrt{npq}}\;\approx\;N(0,1)\quad\text{para }n\text{ grande}$$

**Condición de buena aproximación.** El PDF indica "$p$ cercano a 0.5 y $n>10$". [COMPL] La regla estándar en textos es $np\ge5$ **y** $nq\ge5$ (algunos exigen $>10$); si $p$ es pequeño y $np$ es moderado, es preferible la aproximación de Poisson.

**Corrección por continuidad [PDF diap. 32]** (sumar o restar 0.5):

$$P(a\le X\le b)\approx P(a-0.5\le Y\le b+0.5),\qquad P(X=k)\approx P(k-0.5\le Y\le k+0.5)$$

con $Y\sim N(np,\,npq)$. Casos de una cola [COMPL]: $P(X\le k)\approx P(Y\le k+0.5)$; $P(X\ge k)\approx P(Y\ge k-0.5)$.

**Ejemplo [PDF diap. 33], con correcciones.** 300 fusibles, 2 % defectuosos; $P(\text{exactamente 1 defectuoso})$. $X\sim\text{Bin}(n=300,\,p=0.02)$; $np=6$, $npq=5.88$, $\sigma=\sqrt{npq}\approx2.425$.

$$P(X=1)\approx P(0.5\le Y\le1.5)=P\!\left(\frac{0.5-6}{2.425}\le Z\le\frac{1.5-6}{2.425}\right)=P(-2.27\le Z\le-1.86)\approx0.0201$$

> ⚠ **Correcciones (diap. 33):**
> - $\sigma=\sqrt{npq}=\sqrt{5.88}\approx2.43$ (el PDF escribe $\sqrt{np}=\sqrt{5.88}$, mezclando $np=6$ con $npq=5.88$).
> - Los límites estandarizados son $-2.27$ y $-1.86$ (**ambos negativos**; el PDF escribe "$5.5-6$" y "$1.86$" positivo y su resultado $0.0198$ no es consistente con ello).
> - Para contexto: el valor **exacto** es $b(1;300,0.02)=0.0143$ y la aproximación de Poisson ($\lambda=6$) da $0.0149$. Con $np=6$ y $p=0.02$ (casi el límite de la regla $np\ge5$) la aproximación normal es **mediocre** y la de Poisson es mejor. Se recomienda presentar este ejemplo como ilustración del procedimiento, no de una aproximación precisa.

---

## 3.2 Distribución Exponencial [PDF diap. 34–36]

$$f(x)=\lambda e^{-\lambda x},\qquad x\ge0,\;\lambda>0$$

$$F(x)=1-e^{-\lambda x},\qquad P(X>x)=e^{-\lambda x},\qquad E(X)=\mu=\frac1\lambda\;\text{(vida media)},\qquad \operatorname{Var}(X)=\frac1{\lambda^{2}}$$

Comprobación de normalización [PDF]: $\displaystyle\int_0^{\infty}\lambda e^{-\lambda x}dx=\left[-e^{-\lambda x}\right]_0^{\infty}=1$; y $\displaystyle\mu=\int_0^{\infty}x\lambda e^{-\lambda x}dx=\frac1\lambda$. La gráfica compara $\lambda=2.0,\,1.0,\,0.5,\,0.2$.

**Uso [PDF diap. 35]:** papel fundamental en el **análisis de fiabilidad**: describe tiempos de fallo de un dispositivo durante su vida útil, donde la **tasa de fallo es aproximadamente constante**, $r(t)=\lambda$. Con tasa constante, para un dispositivo que no ha fallado, la probabilidad de fallar en el siguiente intervalo es independiente del tiempo transcurrido. También modela el **tiempo entre dos sucesos aleatorios** de tasa de ocurrencia $\lambda$ (relación con Poisson).
**Propiedad [COMPL]:** falta de memoria, $P(X>s+t\mid X>s)=P(X>t)$.

**Ejemplo [PDF diap. 36], resuelto.** Tiempo de atención de un cajero ~ exponencial con media 40 segundos. En minutos: media $=\tfrac23$ min, $\lambda=\tfrac{1}{40}\,\text{s}^{-1}=1.5\,\text{min}^{-1}$.

- a) $P(1<X<2\text{ min})=F(2)-F(1)=e^{-1.5}-e^{-3}\approx0.2231-0.0498=0.1733$
- b) $P(X>2\text{ min})=1-F(2)=e^{-3}\approx0.0498$

> Nota: el enunciado del PDF no indica la unidad de "entre 1 y 2"; el resultado $e^{-3}$ del inciso b) del PDF solo es consistente si el tiempo está en **minutos** con $\lambda=1.5$. El PDF deja el inciso a) planteado como $F(2)-F(1)$.

---

## 3.3 Distribución Uniforme continua [PDF diap. 37–38]

$$f(x)=\begin{cases}\dfrac{1}{b-a}, & a\le x\le b\\[4pt] 0, & \text{en otro caso}\end{cases}$$

Notación $X\sim U(a,b)$. [COMPL]: $F(x)=\dfrac{x-a}{b-a}$ para $a\le x\le b$; $E(X)=\dfrac{a+b}{2}$; $\operatorname{Var}(X)=\dfrac{(b-a)^{2}}{12}$.

**Ejemplo [PDF diap. 38]:** volumen de ventas de un almacén $\sim U(38,120)$ (miles de dólares). $P(\text{ventas}>100\text{ mil dólares})$:

$$f(x)=\frac{1}{120-38}=\frac1{82},\qquad P(X>100)=\int_{100}^{120}\frac{1}{82}\,dx=\frac{20}{82}=0.2439$$

> ⚠ **Correcciones (diap. 38):** el PDF escribe "$f(x)=1/(120-80)=1/82$"; debe ser $1/(120-38)=1/82$. Además el enunciado dice "superiores a 1000,000 dólares", pero el cálculo usa $100$ (miles), es decir **100 000 dólares**.

---

## 3.4 Función Gamma y Distribución Gamma [PDF diap. 39–42]

### 3.4.1 Función Gamma

$$\Gamma(x)=\int_{0}^{\infty}t^{x-1}e^{-t}\,dt,\qquad x>0$$

$$\Gamma(1)=1,\qquad \Gamma\!\left(\tfrac12\right)=\sqrt\pi$$

**Propiedades [PDF]:** $\Gamma(n+1)=n\,\Gamma(n)$ para $n>0$; si $n$ es entero positivo, $\Gamma(n+1)=n!$ y $\Gamma(n)=(n-1)!$. (La diap. 40 grafica el integrando $y=e^{-t}t^{5-1}$, cuya área es $\Gamma(5)=24$.)

### 3.4.2 Distribución Gamma

$$f(x)=\frac{1}{\Gamma(\alpha)\,\beta^{\alpha}}\;x^{\alpha-1}e^{-x/\beta},\qquad x>0;\;\alpha>0,\;\beta>0$$

$$E(X)=\mu=\alpha\beta,\qquad \operatorname{Var}(X)=\sigma^{2}=\alpha\beta^{2}$$

$\alpha$: parámetro de forma; $\beta$: parámetro de escala [COMPL]. Casos particulares [COMPL]: $\alpha=1,\;\beta=1/\lambda$ ⇒ exponencial; $\alpha=m/2,\;\beta=2$ ⇒ chi-cuadrada con $m$ grados de libertad.

**Ejemplo [PDF diap. 42]:** tiempo semanal de mantenimiento $X\sim\text{Gamma}(\alpha=3,\beta=2)$ (horas).

- a) $P(X>8)=e^{-4}\left(1+4+8\right)=13e^{-4}=0.2381$ *(coincide con el PDF)*.
- b) Costo $C=3X+2X^{2}$:
$$E(C)=3E(X)+2E(X^{2}),\quad E(X)=\alpha\beta=6,\quad E(X^{2})=\operatorname{Var}(X)+[E(X)]^{2}=12+36=48$$
$$E(C)=3(6)+2(48)=114\text{ dólares}$$

> ⚠ **Corrección (diap. 42):** el PDF da como respuesta del inciso b) **276 dólares**. Con $\alpha=3,\,\beta=2$ el valor esperado correcto es **114 dólares** (verificado analítica y numéricamente). El inciso a) del PDF ($0.2381$) es correcto.

---

## 3.5 Distribución Chi-cuadrada ($\chi^2$) [PDF diap. 43–46]

$$f(x)=\frac{1}{2^{m/2}\,\Gamma\!\left(\frac m2\right)}\;x^{\frac m2-1}e^{-x/2},\qquad x>0$$

$m$ = grados de libertad. $E(X)=m$ (el PDF afirma "la media es igual al número de grados de libertad"); [COMPL] $\operatorname{Var}(X)=2m$. Es un caso particular de la Gamma con $\alpha=m/2,\;\beta=2$, y equivale a la suma de los cuadrados de $m$ variables $N(0,1)$ independientes.

**Tablas [PDF diap. 44–45]:** dan $P(\chi^{2}\ge x)=p$ (cola **derecha**), con filas = grados de libertad y columnas = $p$ (p. ej. $p=0.995,0.99,\dots,0.60$ en la diap. 44; $p=0.5,0.25,\dots,0.001$ en la diap. 45).

**Ejercicios [PDF diap. 46] con respuestas** (cola derecha, usar la tabla; valores exactos entre paréntesis):

| Inciso | Planteamiento | Resultado |
|---|---|---|
| a | $P(X\ge35.172)$, gl = 23 | $0.05$ ($0.0500$) |
| b | $P(X\le15.44)$, gl = 21 | $0.20$ ($0.1998$) |
| c | $P(X<7.807)$, gl = 12 | $0.20$ ($0.2000$) |
| d | $P(X>16.31)$, gl = 17 | $\approx0.50$ ($0.5020$) |
| e | $P(9.591\le X<15.45)$, gl = 20 | $0.975-0.75=0.225$ ($0.2249$) |
| f | $P(X\ge K)=0.80$, gl = 21 | $K=15.44$ ($15.4446$) |

---

## 3.6 Distribución $t$ de Student [PDF diap. 47–50]

$$f(x)=\frac{\Gamma\!\left(\frac{m+1}{2}\right)}{\sqrt{m\pi}\;\Gamma\!\left(\frac m2\right)}\left(1+\frac{x^{2}}{m}\right)^{-\frac{m+1}{2}},\qquad x\in\mathbb R$$

$m$ = grados de libertad. [COMPL] $E(X)=0$ ($m>1$), $\operatorname{Var}(X)=\dfrac{m}{m-2}$ ($m>2$). Si $Z\sim N(0,1)$ y $V\sim\chi^2_m$ independientes, $T=\dfrac{Z}{\sqrt{V/m}}\sim t_m$.

**Observación [PDF diap. 47 y 49]:** la curva $t$ es simétrica y en forma de campana como la normal, pero con **colas más pesadas**; al aumentar los grados de libertad se aproxima a la normal estándar ($\nu=\infty$ ⇒ curva $z$; las curvas mostradas son $\nu=1,\,10,\,\infty$).
*(El título de la diap. 47 dice "STUENT"; el nombre correcto es **Student**.)*

**Tabla [PDF diap. 48]:** $P(T\ge t)=p$ (cola derecha), filas = grados de libertad.

**Ejercicios [PDF diap. 50] con respuestas** (el PDF pide además mostrar la gráfica en cada caso):

| N.º | Planteamiento | Resultado |
|---|---|---|
| 1 | $X\sim t_4$, $P(X\ge1.190)$ | $0.15$ |
| 2 | $X\sim t_{18}$, $P(X<2.101)$ | $0.975$ |
| 3 | $X\sim t_{20}$, $P(X\le2.528)$ | $0.99$ |
| 4 | $X\sim t_{15}$, $P(X<-0.691)$ | $0.25$ (simetría) |
| 5 | $X\sim t_{10}$, $c$ tal que $P(X\ge c)=0.15$ | $c=1.093$ |
| 6 | $X\sim t_4$, $P(0\le X\le1.08)$ | $\approx0.3295$ |
| 7 | $P(T\ge T_0)=0.025$, gl = 27 | $T_0=2.052$ |
| 8 | $X\sim t_{20}$, $P(-0.127\le X\le2.086)$ | $1-0.025-0.45=0.525$ ($0.5249$) |

---

## 3.7 Distribución $F$ de Fisher–Snedecor [PDF diap. 51–54]

$$f(x)=\frac{\Gamma\!\left(\frac{m+n}{2}\right)}{\Gamma\!\left(\frac m2\right)\Gamma\!\left(\frac n2\right)}\left(\frac mn\right)^{m/2}\frac{x^{\frac m2-1}}{\left(1+\frac mn\,x\right)^{(m+n)/2}},\qquad x\ge0$$

$m$ = grados de libertad del numerador, $n$ = del denominador. [COMPL]: $F=\dfrac{V_1/m}{V_2/n}$ con $V_1\sim\chi^2_m$, $V_2\sim\chi^2_n$ independientes; $E(X)=\dfrac{n}{n-2}$ ($n>2$); $\operatorname{Var}(X)=\dfrac{2n^{2}(m+n-2)}{m(n-2)^{2}(n-4)}$ ($n>4$); $F_{1-\alpha;\,m,n}=\dfrac{1}{F_{\alpha;\,n,m}}$.

**Notación del PDF:** $F_{(a;\,m,n)}$ es el valor con **área $a$ a su izquierda**. Verificación: $F_{(0.95;\,15,10)}=2.85$ (diap. 51; exacto $2.845$).

**Ejercicios [PDF diap. 54] con respuestas:**

| N.º | Planteamiento | Resultado |
|---|---|---|
| 1 | Valor crítico $F_{0.95;\,3,71}$ | $2.73$ (exacto $2.7336$; en tablas con 60 y 120 gl se interpola) |
| 2 | Área a la derecha de $F_{0.95;\,3,71}$ | $0.05$ (sombrear la cola derecha desde $2.73$) |
| 3 | "Si $P(F\le F_0)=2.87$, calcular $F_0$" | **Enunciado inválido**: una probabilidad no puede ser $2.87$; probable error tipográfico (¿$F_0=2.87$?, ¿$P=0.95$?) |
| 4 | Área a la derecha de $F_{0.90;\,8,21}$ | $0.10$ (valor crítico $1.982$) |
| 5 | Área a la izquierda de $F_{0.95;\,3,16}$ | $0.95$ (valor crítico $3.239$) |

---

## 3.8 Distribución Beta [PDF diap. 55–56]

$X\sim\text{Beta}(\alpha,\beta)$:

$$f(x)=\begin{cases}\dfrac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)}\,x^{\alpha-1}(1-x)^{\beta-1}, & 0<x<1\\[6pt] 0, & \text{en otro caso}\end{cases}\qquad \alpha>0,\;\beta>0$$

$$\mu=\frac{\alpha}{\alpha+\beta},\qquad \sigma^{2}=\frac{\alpha\beta}{(\alpha+\beta)^{2}(\alpha+\beta+1)}$$

> ⚠ **Corrección (diap. 55):** el PDF dice "cuando ambos son 1, la distribución es uniforme ($\alpha=0$, $\beta=1$)". Lo correcto es: si $\alpha=\beta=1$ la distribución es la **uniforme** $U(0,1)$. ($\alpha=0$ no es un valor válido, pues se exige $\alpha>0$.)

**Ejemplo [PDF diap. 56]:** proporción semanal vendida de un tanque de gasolina $X\sim\text{Beta}(\alpha=4,\beta=2)$.

- a) $E(X)=\dfrac{4}{4+2}=\dfrac23$: se vende en promedio $2/3$ del tanque por semana. *(El PDF escribe "$4(4+2)$" por error de tipeo.)*
- b) $P(X>0.9)$: para $\text{Beta}(4,2)$, $f(x)=20x^{3}(1-x)$ y $F(x)=5x^{4}-4x^{5}$, así que
$$P(X>0.9)=1-\left[5(0.9)^4-4(0.9)^5\right]=1-0.91854=0.0815\approx8.1\%$$
*(el PDF redondea a $0.082=8.2\%$).*

---

## 3.9 Distribución de Weibull [PDF diap. 57–58]

**Parametrización usada en el PDF** ($\lambda$: parámetro de escala en forma de tasa; $\alpha$: parámetro de forma):

$$f(x)=\begin{cases}\lambda\alpha\,(\lambda x)^{\alpha-1}e^{-(\lambda x)^{\alpha}}, & x>0\\ 0, & x\le0\end{cases}\qquad F(x)=\begin{cases}1-e^{-(\lambda x)^{\alpha}}, & x>0\\ 0, & x\le0\end{cases}$$

$$\mu=\frac1\lambda\,\Gamma\!\left(1+\frac1\alpha\right),\qquad \sigma^{2}=\frac1{\lambda^{2}}\left[\Gamma\!\left(1+\frac2\alpha\right)-\Gamma^{2}\!\left(1+\frac1\alpha\right)\right]$$

**Parametrización estándar [COMPL]** (la más usada en R, SciPy, MATLAB): forma $k=\alpha$ y escala $\eta=1/\lambda$:

$$f(x)=\frac{k}{\eta}\left(\frac x\eta\right)^{k-1}e^{-(x/\eta)^{k}},\quad F(x)=1-e^{-(x/\eta)^{k}},\quad \mu=\eta\,\Gamma\!\left(1+\tfrac1k\right),\quad \sigma^{2}=\eta^{2}\!\left[\Gamma\!\left(1+\tfrac2k\right)-\Gamma^{2}\!\left(1+\tfrac1k\right)\right]$$

Ambas son equivalentes; conviene indicar cuál se usa. Con $\alpha=1$ se obtiene la exponencial de tasa $\lambda$. Usada en fiabilidad (tasa de fallo decreciente si $\alpha<1$, constante si $\alpha=1$, creciente si $\alpha>1$).

**Ejemplo [PDF diap. 58]:** tiempo de vida $X$ (horas) de un artículo, $\lambda=0.01$, $\alpha=2$. Probabilidad de falla antes de 8 horas:

$$F(8)=1-e^{-(0.01\cdot8)^{2}}=1-e^{-0.0064}\approx0.0064\;(0.64\%)$$

> ⚠ **Corrección (diap. 58):** el PDF escribe $F(8)=1-e^{-(0.01)^{8^{2}}}=0.473$. La expresión correcta es $(\lambda x)^{\alpha}=(0.01\cdot 8)^{2}$, no $(0.01)^{8^2}$; el resultado correcto para $x=8$ es $\mathbf{0.0064}$. El valor $0.473$ del PDF corresponde a $x=80$ horas: $1-e^{-(0.8)^2}=1-e^{-0.64}=0.473$. Verificar con la docente si el enunciado pretendía 8 o 80 horas.

---

## 3.10 Distribución Lognormal [PDF diap. 59–62]

**Definición:** $X$ es lognormal si $Y=\ln X$ es normal ($X>0$). Si $\ln X\sim N(\mu,\sigma^{2})$:

$$f(x;\mu,\sigma)=\begin{cases}\dfrac{1}{\sigma\,x\sqrt{2\pi}}\exp\!\left[-\dfrac{(\ln x-\mu)^{2}}{2\sigma^{2}}\right], & x>0\\[8pt] 0, & x\le0\end{cases}\qquad -\infty<\mu<\infty,\;\sigma>0$$

> ⚠ **Corrección (diap. 59):** el PDF omite el **signo menos** del exponente (escribe $e^{(\ln x-\mu)^2/2\sigma^2}$, que no integra 1). Además el soporte es $x>0$ (el PDF escribe $x\ge0$). $\mu$ y $\sigma$ son la media y la desviación estándar de $\ln X$ (no de $X$): $\mu$ es el parámetro de escala (la mediana es $e^{\mu}$) y $\sigma$ el parámetro de forma.

$$E(X)=e^{\mu+\sigma^{2}/2},\qquad \operatorname{Var}(X)=e^{2\mu+\sigma^{2}}\left(e^{\sigma^{2}}-1\right)$$

[COMPL] $F(x)=\Phi\!\left(\dfrac{\ln x-\mu}{\sigma}\right)$; mediana $=e^{\mu}$; moda $=e^{\mu-\sigma^{2}}$. Distribución asimétrica a la derecha (diap. 60).

**Ejemplo [PDF diap. 61]:** profundidad máxima de pozo (picaduras) en tuberías de hierro fundido enterradas, en mm. $\mu=0.353$, $\sigma=0.754$. Media de la profundidad:

$$E(X)=e^{\mu+\sigma^{2}/2}=e^{\,0.353+\frac{(0.754)^{2}}{2}}=e^{0.63726}=1.8913\text{ mm}$$

> ⚠ **Correcciones (diap. 61):** (i) el enunciado dice $\mu=0.35$ pero el cálculo usa $\mu=0.353$ (con $0.35$ resultaría $1.8856$); usar $0.353$. (ii) El PDF escribe $E(X)=e^{\mu}+\sigma^{2}/2$; lo correcto es $e^{\mu+\sigma^{2}/2}$ (el $\sigma^2/2$ va **dentro** del exponente).

**Ejercicios [PDF diap. 62] con respuestas:**

1. Con $\mu=0.353$, $\sigma=0.754$: $P(1<X<2)=\Phi\!\left(\dfrac{\ln2-0.353}{0.754}\right)-\Phi\!\left(\dfrac{\ln1-0.353}{0.754}\right)=\Phi(0.451)-\Phi(-0.468)\approx0.674-0.320=0.354$.
2. Supervivencia (años) lognormal con $\mu=2.32$ y $\sigma=0.20$ (la "escala 2.32" y "forma 0.20" del PDF). $P(T>123)=1-\Phi\!\left(\dfrac{\ln123-2.32}{0.20}\right)=1-\Phi(12.46)\approx6\times10^{-36}\approx0$. Es prácticamente nula: la mediana es $e^{2.32}\approx10.2$ años y la media $\approx10.4$ años.

---

# PARTE III — SÍNTESIS

## 4. Relaciones entre distribuciones [COMPL]

- Bernoulli($p$) = Binomial($1,p$); Binomial($n,p$) = suma de $n$ Bernoulli independientes; Multinomial con $k=2$ = Binomial.
- Binomial → Poisson: $n\to\infty$, $p\to0$, $np=\lambda$ constante.
- Binomial → Normal (teorema del límite central; de Moivre–Laplace): $n$ grande, $np\ge5$ y $nq\ge5$.
- Hipergeométrica → Binomial cuando $N$ es grande respecto a $n$.
- Geométrica = Binomial negativa con $r=1$; la Binomial negativa es suma de $r$ geométricas independientes.
- Poisson (conteos) ↔ Exponencial (tiempos entre eventos).
- Exponencial = Gamma($\alpha=1,\beta=1/\lambda$); $\chi^2_m$ = Gamma($\alpha=m/2,\beta=2$); Weibull con $\alpha=1$ = Exponencial.
- Beta(1,1) = Uniforme(0,1).
- $\chi^2_m$ = suma de $m$ cuadrados de $N(0,1)$ independientes; $t_m=Z/\sqrt{\chi^2_m/m}$; $F_{m,n}=(\chi^2_m/m)/(\chi^2_n/n)$; $t_m\to N(0,1)$ cuando $m\to\infty$.
- $X$ lognormal ⇔ $\ln X$ normal.

## 5. Tabla resumen

| Distribución | Soporte | $P(X=x)$ o $f(x)$ | $E(X)$ | $\operatorname{Var}(X)$ |
|---|---|---|---|---|
| Bernoulli($p$) | $\{0,1\}$ | $p^{x}q^{1-x}$ | $p$ | $pq$ |
| Binomial($n,p$) | $0,\dots,n$ | $\binom nx p^{x}q^{n-x}$ | $np$ | $npq$ |
| Poisson($\lambda$) | $0,1,2,\dots$ | $\dfrac{e^{-\lambda}\lambda^{x}}{x!}$ | $\lambda$ | $\lambda$ |
| Hipergeométrica($N,k,n$) | $\max(0,n-N+k)\le x\le\min(n,k)$ | $\dfrac{\binom kx\binom{N-k}{n-x}}{\binom Nn}$ | $\dfrac{nk}N$ | $npq\dfrac{N-n}{N-1},\;p=\tfrac kN$ |
| Geométrica($p$) | $1,2,\dots$ | $q^{x-1}p$ | $\dfrac1p$ | $\dfrac{q}{p^{2}}$ |
| Binomial negativa($r,p$) (ensayos) | $r,r+1,\dots$ | $\binom{x-1}{r-1}p^{r}q^{x-r}$ | $\dfrac rp$ | $\dfrac{rq}{p^{2}}$ |
| Uniforme discreta ($1..n$) | $1,\dots,n$ | $\dfrac1n$ | $\dfrac{n+1}2$ | $\dfrac{n^{2}-1}{12}$ |
| Multinomial($n;p_1..p_k$) | $\sum x_i=n$ | $\dfrac{n!}{\prod x_i!}\prod p_i^{x_i}$ | $E(X_i)=np_i$ | $np_i(1-p_i)$ |
| Normal($\mu,\sigma^2$) | $\mathbb R$ | $\dfrac{1}{\sigma\sqrt{2\pi}}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$ | $\mu$ | $\sigma^{2}$ |
| Exponencial($\lambda$) | $x\ge0$ | $\lambda e^{-\lambda x}$ | $\dfrac1\lambda$ | $\dfrac1{\lambda^{2}}$ |
| Uniforme($a,b$) | $[a,b]$ | $\dfrac1{b-a}$ | $\dfrac{a+b}2$ | $\dfrac{(b-a)^{2}}{12}$ |
| Gamma($\alpha,\beta$) | $x>0$ | $\dfrac{x^{\alpha-1}e^{-x/\beta}}{\Gamma(\alpha)\beta^{\alpha}}$ | $\alpha\beta$ | $\alpha\beta^{2}$ |
| Chi-cuadrada($m$) | $x>0$ | $\dfrac{x^{m/2-1}e^{-x/2}}{2^{m/2}\Gamma(m/2)}$ | $m$ | $2m$ |
| $t$ de Student($m$) | $\mathbb R$ | $\dfrac{\Gamma(\frac{m+1}2)}{\sqrt{m\pi}\Gamma(\frac m2)}\left(1+\frac{x^2}m\right)^{-\frac{m+1}2}$ | $0\;(m>1)$ | $\dfrac m{m-2}\;(m>2)$ |
| $F(m,n)$ | $x\ge0$ | (ver §3.7) | $\dfrac n{n-2}\;(n>2)$ | $\dfrac{2n^{2}(m+n-2)}{m(n-2)^{2}(n-4)}\;(n>4)$ |
| Beta($\alpha,\beta$) | $0<x<1$ | $\dfrac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)}x^{\alpha-1}(1-x)^{\beta-1}$ | $\dfrac\alpha{\alpha+\beta}$ | $\dfrac{\alpha\beta}{(\alpha+\beta)^{2}(\alpha+\beta+1)}$ |
| Weibull($\lambda,\alpha$) (convención PDF) | $x>0$ | $\lambda\alpha(\lambda x)^{\alpha-1}e^{-(\lambda x)^{\alpha}}$ | $\dfrac1\lambda\Gamma(1+\tfrac1\alpha)$ | $\dfrac1{\lambda^{2}}\left[\Gamma(1+\tfrac2\alpha)-\Gamma^{2}(1+\tfrac1\alpha)\right]$ |
| Lognormal($\mu,\sigma^2$) | $x>0$ | $\dfrac1{\sigma x\sqrt{2\pi}}e^{-\frac{(\ln x-\mu)^2}{2\sigma^2}}$ | $e^{\mu+\sigma^2/2}$ | $e^{2\mu+\sigma^2}(e^{\sigma^2}-1)$ |

---

## 6. Resumen de ejercicios resueltos de la distribución Normal (diap. 28 del PDF)

El PDF plantea estos ejercicios sin resolver (tabla de la diap. 29 = áreas de 0 a $z$):

| Inciso | Planteamiento | Resultado |
|---|---|---|
| 1a | $P(0<Z\le2)$ | $0.4772$ |
| 1b | $P(-1.5\le Z\le1)$ | $0.7745$ |
| 1c | $P(Z<2.05)$ | $0.9798$ |
| 1d | $P(Z\ge-3.07)$ | $0.9989$ |
| 1e | $P(Z\le1.5)$ | $0.9332$ |
| 1f | $P(45\le X<60)$, $\mu=44$, $\sigma^2=16$ ($\sigma=4$) | $P(0.25\le Z<4)=0.4013$ |
| 1g | $P(13\le X\le21)$, $\mu=15$, $\sigma^2=0.49$ ($\sigma=0.7$) | $P(-2.857\le Z\le8.571)=0.9979$ |
| 1h | $P(Z\le R)=0.45$ | $R=-0.1257\approx-0.13$ |
| 1i | $P(Z<z_0)=0.0475$ | $z_0=-1.67$ |
| 2 | Área a la derecha de $z=2.05$ y a la izquierda de $-1.44$ | $0.0202+0.0749=0.0951$ |

---

## 7. Registro de erratas del PDF (resumen para trazabilidad)

| N.º | Diap. | El PDF dice | Lo correcto | Impacto |
|---|---|---|---|---|
| 1 | 7 | $\operatorname{Var}(X)=1-p$ (Bernoulli) | $\operatorname{Var}(X)=p(1-p)$ | Fórmula |
| 2 | 6 | $b(4;6,\tfrac12)=\tfrac{11}{64}$ | $\tfrac{15}{64}$ (suma final $\tfrac{11}{32}$ sí es correcta) | Dato intermedio |
| 3 | 14 | $X$ = "intentos o fallas antes del primer éxito" | Definir una sola convención (ensayos hasta el 1.er éxito) | Definición |
| 4 | 18 | $\mu=rq/p$ para $X$ = número de ensayos | $E(X)=r/p$; $rq/p$ es la media del número de fallas | Fórmula |
| 5 | 19 | $(0.10)^{10}=0.0001$; resultado $0.2002\times0.59$ | $(0.10)^{10}=10^{-10}$; $P\approx1.18\times10^{-7}$ | Resultado |
| 6 | 22 | Denominador multinomial $\dots x_3!$ | $\dots x_k!$ | Fórmula |
| 7 | 23 | $x_2=5$; resultado $0.41$ | $x_2=10$; resultado $\approx0.0068$ | Resultado |
| 8 | 24 | Binomial negativa listada como continua | Es discreta | Clasificación |
| 9 | 33 | $\sigma=\sqrt{np}$; límites $5.5-6$ y $+1.86$; $0.0198$ | $\sigma=\sqrt{npq}\approx2.43$; límites $-2.27$ y $-1.86$; $\approx0.0201$ (exacto $0.0143$) | Resultado |
| 10 | 38 | $f(x)=1/(120-80)$; "1000,000 dólares" | $1/(120-38)=1/82$; 100 000 dólares | Enunciado/dato |
| 11 | 42 | $E(C)=276$ dólares | $E(C)=114$ dólares | Resultado |
| 12 | 54 | "Si $P(F\le F_0)=2.87$" | Enunciado inválido (probabilidad $>1$) | Enunciado |
| 13 | 55 | Beta uniforme con "$\alpha=0,\beta=1$" | $\alpha=\beta=1$ ⇒ $U(0,1)$ | Afirmación |
| 14 | 56 | $\mu=4(4+2)$; $P(X>0.9)=0.082$ | $\mu=4/(4+2)$; $P\approx0.0815$ | Tipeo/redondeo |
| 15 | 58 | $F(8)=1-e^{-(0.01)^{8^2}}=0.473$ | $F(8)=1-e^{-(0.08)^2}=0.0064$ ($0.473$ corresponde a $x=80$) | Resultado |
| 16 | 59 | Lognormal sin signo "−" en el exponente; $x\ge0$ | $\exp\!\big[-(\ln x-\mu)^2/(2\sigma^2)\big]$; $x>0$ | Fórmula |
| 17 | 61 | $\mu=0.35$; $E(X)=e^{\mu}+\sigma^{2}/2$ | $\mu=0.353$; $E(X)=e^{\mu+\sigma^{2}/2}$ | Fórmula/dato |
| 18 | 47 | Título "STUENT" | "Student" | Ortografía |

Errores menores de numeración: las secciones "6" aparecen repetidas (Binomial negativa, Uniforme discreta en discretas; $t$, $F$ y $\chi^2$ en continuas) y la lista continua de la diap. 24 sigue otro orden que el desarrollo.

---

## 8. Referencias y fuentes de verificación

**Fuente principal**

- Quispe Mamani, A. (2025). *Modelos de distribución de probabilidad* (versión 2.0) [Diapositivas]. Universidad Nacional de San Agustín de Arequipa, Arequipa, Perú.

**Verificación numérica**

- Todos los valores numéricos de este documento fueron recalculados con Python 3 (SciPy 1.17: `scipy.stats`, distribuciones binomial, Poisson, hipergeométrica, geométrica, binomial negativa, multinomial, normal, exponencial, gamma, $\chi^2$, $t$, $F$, beta, Weibull y lognormal).

**Fuentes externas contrastadas en línea** (fórmulas, parametrizaciones y reglas de aproximación)

- MathWorks. *nbinstat — Negative binomial mean and variance*. https://es.mathworks.com/help/stats/nbinstat.html (media $rq/p$, varianza $rq/p^2$ según parametrización).
- Hyndman, R. J., et al. *dist_negative_binomial* y *dist_weibull*, paquete R `distributional`. https://pkg.robjhyndman.com/distributional/reference/dist_weibull.html (parametrización forma/escala de la Weibull y de la binomial negativa).
- R Core Team. *The Log Normal Distribution* (`stats::Lognormal`). https://rdrr.io/r/stats/Lognormal.html (densidad, media y varianza lognormal).
- Wikipedia. *Log-normal distribution*. https://en.wikipedia.org/wiki/Log-normal_distribution
- Wikipedia. *Continuity correction*. https://en.wikipedia.org/wiki/Continuity_correction
- Penn State, STAT 414. *Normal Approximation to Binomial* (sec. 28.1). https://online.stat.psu.edu/stat414/book/export/html/792

**Textos de referencia sugeridos para citar en el Marco Teórico** (obras estándar sobre estos modelos; no fueron consultadas directamente en esta verificación, por lo que conviene revisar las páginas exactas antes de citarlas):

- Walpole, R. E., Myers, R. H., Myers, S. L., & Ye, K. *Probabilidad y estadística para ingeniería y ciencias*. Pearson.
- Montgomery, D. C., & Runger, G. C. *Applied Statistics and Probability for Engineers*. Wiley.
- Devore, J. L. *Probabilidad y estadística para ingeniería y ciencias*. Cengage.
- Ross, S. M. *A First Course in Probability*. Pearson.
- NIST/SEMATECH. *e-Handbook of Statistical Methods*. https://www.itl.nist.gov/div898/handbook/
