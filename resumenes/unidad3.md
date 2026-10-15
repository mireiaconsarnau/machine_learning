---
title: "Unidad 3"
parent: "Resúmenes visuales"
nav_order: 3
---

# Resumen visual · Unidad 3. Aprendizaje supervisado

[Ir a la unidad completa](../unidad3/unidad3.md){: .btn .btn-outline }

## Lección 1. ¿Qué es el aprendizaje supervisado? {#leccion-1}

<div class="ficha-lead">
Es enseñar a un modelo a <strong>predecir a partir de ejemplos conocidos</strong>: cada ejemplo trae sus variables de entrada y el resultado esperado. El modelo descubre las reglas en los datos y luego las aplica a <strong>datos nuevos</strong>.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>Reglas aprendidas, no programadas.</strong> En la programación tradicional se escriben las reglas paso a paso; aquí el modelo las aprende de los datos. Para mejorarlo basta con añadir datos y reentrenar.</div>
  <div class="idea"><strong>Clasificación o regresión.</strong> Si la salida es una clase («spam» / «no spam») es clasificación; si es un número continuo (precio de una casa), regresión. La edad exacta es regresión; la edad por intervalos, clasificación.</div>
  <div class="idea"><strong>Dividir para comprobar.</strong> Entrenamiento para aprender, validación para ajustar hiperparámetros y prueba para la evaluación final. Una división habitual: 70 % entrenamiento y 30 % validación y prueba.</div>
  <div class="idea"><strong>Validación cruzada.</strong> Se divide varias veces en pliegues (<em>folds</em>) y se promedia el rendimiento. Da una medida más robusta y es muy útil con pocos datos.</div>
  <div class="idea"><strong>Parámetros ≠ hiperparámetros.</strong> Los parámetros los aprende el modelo al entrenar; los hiperparámetros se fijan antes (a mano o con <em>grid search</em> / <em>random search</em>).</div>
  <div class="idea"><strong>Ni memorizar ni quedarse corto.</strong> El sobreajuste aprende hasta el ruido; el subajuste no capta los patrones. El equilibrio entre <em>bias</em> y <em>variance</em> es la clave.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">Las fases del aprendizaje supervisado</div>
  <div class="flujo cuatro">
    <div class="paso"><span class="num">1</span><strong>Recopilar</strong>Datos suficientes, relevantes y actualizados</div>
    <div class="paso"><span class="num">2</span><strong>Explorar y preparar</strong>Limpiar, escalar, codificar (Unidad 2)</div>
    <div class="paso"><span class="num">3</span><strong>Dividir</strong>Entrenamiento, validación y prueba</div>
    <div class="paso"><span class="num">4</span><strong>Entrenar y predecir</strong>El modelo ajusta sus parámetros</div>
    <div class="paso"><span class="num">5</span><strong>Validar</strong>¿Funciona con datos que no ha visto? ¿Sobreajusta?</div>
    <div class="paso"><span class="num">6</span><strong>Optimizar</strong>Hiperparámetros, otros algoritmos, combinar técnicas</div>
    <div class="paso"><span class="num">7</span><strong>Pruebas finales</strong>Sin sobreajuste, también con valores extremos</div>
    <div class="paso"><span class="num">8</span><strong>Conclusiones</strong>Interpretar y comunicar los resultados</div>
  </div>
  <p class="nota">Validar y optimizar no es lineal: se repite varias veces hasta dar con la mejor combinación.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Dividir los datos y validación cruzada</div>
  <svg class="svg-ancho" viewBox="0 0 340 184" role="img" aria-label="Barra con 70 % de entrenamiento y 30 % de validación y prueba; debajo, cinco iteraciones de validación cruzada en las que cada vez valida un pliegue distinto">
    <text x="170" y="12" text-anchor="middle">División simple</text>
    <rect x="20" y="20" width="210" height="20" fill="currentColor" fill-opacity="0.2" stroke="currentColor" stroke-width="1.5"/>
    <rect x="230" y="20" width="90" height="20" fill="#c62828" fill-opacity="0.15" stroke="#c62828" stroke-width="1.5"/>
    <text x="20" y="54">Entrenamiento (70 %)</text>
    <text x="320" y="54" text-anchor="end" style="fill:#c62828">Validación y prueba (30 %)</text>
    <text x="170" y="80" text-anchor="middle">Validación cruzada de 5 pliegues</text>
    <text x="72" y="98" text-anchor="end">Vuelta 1</text>
    <rect x="80" y="89" width="48" height="11" fill="#c62828" fill-opacity="0.35" stroke="#c62828"/>
    <rect x="130" y="89" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="180" y="89" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="230" y="89" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="280" y="89" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <text x="72" y="113" text-anchor="end">Vuelta 2</text>
    <rect x="80" y="104" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="130" y="104" width="48" height="11" fill="#c62828" fill-opacity="0.35" stroke="#c62828"/>
    <rect x="180" y="104" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="230" y="104" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="280" y="104" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <text x="72" y="128" text-anchor="end">Vuelta 3</text>
    <rect x="80" y="119" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="130" y="119" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="180" y="119" width="48" height="11" fill="#c62828" fill-opacity="0.35" stroke="#c62828"/>
    <rect x="230" y="119" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="280" y="119" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <text x="72" y="143" text-anchor="end">Vuelta 4</text>
    <rect x="80" y="134" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="130" y="134" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="180" y="134" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="230" y="134" width="48" height="11" fill="#c62828" fill-opacity="0.35" stroke="#c62828"/>
    <rect x="280" y="134" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <text x="72" y="158" text-anchor="end">Vuelta 5</text>
    <rect x="80" y="149" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="130" y="149" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="180" y="149" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="230" y="149" width="48" height="11" fill="currentColor" fill-opacity="0.2" stroke="currentColor"/>
    <rect x="280" y="149" width="48" height="11" fill="#c62828" fill-opacity="0.35" stroke="#c62828"/>
    <text x="170" y="178" text-anchor="middle">Cada vuelta valida un pliegue distinto (en rojo)</text>
  </svg>
  <p class="nota">Al final se calcula la media de la métrica en las cinco vueltas: es el rendimiento esperado del modelo.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Modelo, algoritmo, parámetros e hiperparámetros (ejemplo: un árbol de decisión)</div>
  <div class="comparativa">
    <div class="col"><h4>Algoritmo</h4><ul><li>La «receta»: los pasos para construir el modelo.</li><li>Cómo dividir los datos y qué criterio usar para crear las ramas.</li></ul></div>
    <div class="col"><h4>Modelo</h4><ul><li>El resultado final entrenado que hace predicciones.</li><li>El árbol ya entrenado con datos de pacientes.</li></ul></div>
    <div class="col"><h4>Parámetros</h4><ul><li>Los <strong>aprende</strong> el modelo al entrenar.</li><li>Las condiciones de división de cada nodo (en regresión lineal, los coeficientes).</li></ul></div>
    <div class="col"><h4>Hiperparámetros</h4><ul><li>Se <strong>fijan antes</strong> de entrenar y no cambian durante el entrenamiento.</li><li>Profundidad máxima, mínimo de muestras para dividir.</li></ul></div>
  </div>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Subajuste, equilibrio y sobreajuste</div>
  <svg class="svg-ancho" viewBox="0 0 420 146" role="img" aria-label="Tres gráficos con los mismos puntos: una recta plana que no capta la forma (subajuste), una curva suave que sigue la tendencia (equilibrio) y una línea en zigzag que pasa por todos los puntos (sobreajuste)">
    <g transform="translate(15,0)">
      <text x="55" y="12" text-anchor="middle">Subajuste</text>
      <line x1="0" y1="100" x2="110" y2="100" stroke="currentColor" stroke-opacity="0.4"/>
      <line x1="0" y1="20" x2="0" y2="100" stroke="currentColor" stroke-opacity="0.4"/>
      <g fill="currentColor"><circle cx="8" cy="88" r="3"/><circle cx="18" cy="74" r="3"/><circle cx="28" cy="54" r="3"/><circle cx="40" cy="50" r="3"/><circle cx="52" cy="38" r="3"/><circle cx="64" cy="52" r="3"/><circle cx="76" cy="50" r="3"/><circle cx="88" cy="72" r="3"/><circle cx="100" cy="84" r="3"/></g>
      <line x1="2" y1="64" x2="108" y2="64" stroke="#c62828" stroke-width="2.5"/>
      <text x="55" y="120" text-anchor="middle">No capta el patrón:</text>
      <text x="55" y="134" text-anchor="middle">falla en ambos conjuntos</text>
    </g>
    <g transform="translate(155,0)">
      <text x="55" y="12" text-anchor="middle">Equilibrio</text>
      <line x1="0" y1="100" x2="110" y2="100" stroke="currentColor" stroke-opacity="0.4"/>
      <line x1="0" y1="20" x2="0" y2="100" stroke="currentColor" stroke-opacity="0.4"/>
      <g fill="currentColor"><circle cx="8" cy="88" r="3"/><circle cx="18" cy="74" r="3"/><circle cx="28" cy="54" r="3"/><circle cx="40" cy="50" r="3"/><circle cx="52" cy="38" r="3"/><circle cx="64" cy="52" r="3"/><circle cx="76" cy="50" r="3"/><circle cx="88" cy="72" r="3"/><circle cx="100" cy="84" r="3"/></g>
      <path d="M2 94 Q 54 0 108 94" fill="none" stroke="currentColor" stroke-width="2.5"/>
      <text x="55" y="120" text-anchor="middle">Aprende la tendencia</text>
      <text x="55" y="134" text-anchor="middle">y generaliza</text>
    </g>
    <g transform="translate(295,0)">
      <text x="55" y="12" text-anchor="middle">Sobreajuste</text>
      <line x1="0" y1="100" x2="110" y2="100" stroke="currentColor" stroke-opacity="0.4"/>
      <line x1="0" y1="20" x2="0" y2="100" stroke="currentColor" stroke-opacity="0.4"/>
      <g fill="currentColor"><circle cx="8" cy="88" r="3"/><circle cx="18" cy="74" r="3"/><circle cx="28" cy="54" r="3"/><circle cx="40" cy="50" r="3"/><circle cx="52" cy="38" r="3"/><circle cx="64" cy="52" r="3"/><circle cx="76" cy="50" r="3"/><circle cx="88" cy="72" r="3"/><circle cx="100" cy="84" r="3"/></g>
      <polyline points="8,88 18,74 28,54 40,50 52,38 64,52 76,50 88,72 100,84" fill="none" stroke="#c62828" stroke-width="2.5"/>
      <text x="55" y="120" text-anchor="middle">Memoriza el ruido:</text>
      <text x="55" y="134" text-anchor="middle">falla con datos nuevos</text>
    </g>
  </svg>
  <p class="nota">Error bajo en entrenamiento pero alto en validación → <strong>sobreajuste</strong> (mucha <em>variance</em>). Error alto en los dos → <strong>subajuste</strong> (mucho <em>bias</em>).</p>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Aprendizaje supervisado</dt><dd>Aprender a predecir a partir de ejemplos con la respuesta conocida (datos etiquetados).</dd>
  <dt>Validación cruzada</dt><dd>Repetir el entrenamiento con distintas particiones (pliegues o <em>folds</em>) y promediar el rendimiento.</dd>
  <dt>Parámetro</dt><dd>Valor interno que el modelo ajusta solo durante el entrenamiento.</dd>
  <dt>Hiperparámetro</dt><dd>Valor que se fija antes de entrenar y controla cómo funciona el algoritmo.</dd>
  <dt>Sobreajuste</dt><dd>El modelo se adapta tanto al entrenamiento que aprende ruido y no generaliza.</dd>
  <dt>Subajuste</dt><dd>El modelo es demasiado simple y no capta los patrones principales.</dd>
  <dt>Bias / variance</dt><dd>Error por simplificar demasiado (bias) frente a sensibilidad excesiva a los datos concretos (variance).</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Evaluar el modelo con los mismos datos con los que ha aprendido.** Parecerá muy bueno aunque solo haya memorizado.
- **Ajustar hiperparámetros mirando el conjunto de prueba.** La prueba es el examen final; para ajustar está la validación.
- **Creer que un modelo más complejo siempre es mejor.** Un árbol muy profundo acierta todo en entrenamiento y falla con datos nuevos.
- **Confundir parámetros e hiperparámetros.** La profundidad máxima de un árbol no se aprende: la decides tú (o una búsqueda).
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>Quieres predecir cuántos minutos tardará un pedido en llegar. ¿Clasificación o regresión? ¿Y si solo quieres saber si llegará «a tiempo» o «tarde»?</summary>
    <div class="respuesta">Los minutos son un número continuo: <strong>regresión</strong>. «A tiempo» / «tarde» son dos clases: <strong>clasificación</strong> (binaria). La misma variable puede plantearse de las dos formas.</div></details>
  <details><summary>Tu modelo tiene un error muy bajo en entrenamiento y muy alto en validación. ¿Qué le pasa?</summary>
    <div class="respuesta">Está <strong>sobreajustado</strong>: ha memorizado los datos de entrenamiento (incluido el ruido) y no generaliza. Se puede controlar con regularización, validación cruzada o un modelo menos complejo.</div></details>
  <details><summary>¿La profundidad máxima de un árbol es un parámetro o un hiperparámetro?</summary>
    <div class="respuesta">Un <strong>hiperparámetro</strong>: se fija antes de entrenar y no cambia durante el entrenamiento. Las condiciones de división de cada nodo sí son parámetros.</div></details>
  <details><summary>Tienes pocos datos y no quieres depender de una única división. ¿Qué técnica usarías?</summary>
    <div class="respuesta"><strong>Validación cruzada</strong>: entrenas varias veces con pliegues distintos y promedias. Aprovechas mejor los datos y obtienes una medida más robusta.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/yeSjA9QJFLU">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad3/l1.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L10.ipynb">Colab: fases del aprendizaje supervisado</a>
</div>

## Lección 2. Modelos de clasificación {#leccion-2}

<div class="ficha-lead">
Clasificar es <strong>asignar a cada observación una clase</strong>. El porcentaje de aciertos no basta: hay que elegir la <strong>métrica según el coste de cada error</strong>, comprobar que el modelo no está sobreajustado y escoger el <strong>algoritmo que encaja con los datos</strong>.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>Binaria o multiclase.</strong> Dos clases («spam» / «no spam») o más («gato», «perro», «conejo»). En multiclase cada clase se analiza como «positiva» frente a todas las demás y se promedia (macro o micro).</div>
  <div class="idea"><strong>La matriz de confusión</strong> cruza predicciones y clases reales: aciertos (TP, TN) y errores (FP, FN). De ella salen casi todas las métricas.</div>
  <div class="idea"><strong>La métrica depende del contexto.</strong> Si un tipo de error es muy grave, se vigila la métrica que lo mide. Con clases desequilibradas, la exactitud engaña: mejor el F1-score.</div>
  <div class="idea"><strong>Detectar el sobreajuste</strong> exige más que una métrica alta: validación cruzada, comparar entrenamiento y test, curvas de aprendizaje y datos externos o nuevos.</div>
  <div class="idea"><strong>Cada algoritmo tiene su lógica:</strong> probabilidades (Naive Bayes), distancias (KNN), fronteras (regresión logística, SVM), reglas (árboles) o combinación de modelos (Random Forest, AdaBoost).</div>
  <div class="idea"><strong>Escalar o no.</strong> KNN, SVM y regresión logística necesitan datos escalados. Naive Bayes y los árboles (también Random Forest) no lo requieren.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">Matriz de confusión y métricas (ejemplo del material)</div>
  <svg class="svg-ancho" viewBox="0 0 340 196" role="img" aria-label="Matriz de confusión con la clase positiva Sano: 95 verdaderos positivos, 20 falsos positivos, 5 falsos negativos y 30 verdaderos negativos">
    <text x="215" y="12" text-anchor="middle">Valor real</text>
    <text x="170" y="32" text-anchor="middle">Sano</text>
    <text x="260" y="32" text-anchor="middle">VIH</text>
    <text x="115" y="66" text-anchor="end">Predice Sano</text>
    <text x="115" y="122" text-anchor="end">Predice VIH</text>
    <rect x="125" y="40" width="90" height="56" fill="currentColor" fill-opacity="0.2" stroke="currentColor" stroke-width="1.5"/>
    <rect x="215" y="40" width="90" height="56" fill="#c62828" fill-opacity="0.12" stroke="#c62828" stroke-width="1.5"/>
    <rect x="125" y="96" width="90" height="56" fill="#c62828" fill-opacity="0.12" stroke="#c62828" stroke-width="1.5"/>
    <rect x="215" y="96" width="90" height="56" fill="currentColor" fill-opacity="0.2" stroke="currentColor" stroke-width="1.5"/>
    <text x="170" y="66" text-anchor="middle" style="font-size:14px;font-weight:700">TP = 95</text>
    <text x="170" y="84" text-anchor="middle">sano → sano</text>
    <text x="260" y="66" text-anchor="middle" style="font-size:14px;font-weight:700;fill:#c62828">FP = 20</text>
    <text x="260" y="84" text-anchor="middle" style="fill:#c62828">VIH → «sano»</text>
    <text x="170" y="122" text-anchor="middle" style="font-size:14px;font-weight:700;fill:#c62828">FN = 5</text>
    <text x="170" y="140" text-anchor="middle" style="fill:#c62828">sano → «VIH»</text>
    <text x="260" y="122" text-anchor="middle" style="font-size:14px;font-weight:700">TN = 30</text>
    <text x="260" y="140" text-anchor="middle">VIH → VIH</text>
    <text x="170" y="172" text-anchor="middle">Clase positiva: «Sano». 150 casos: 100 sanos y 50 con VIH.</text>
    <text x="170" y="188" text-anchor="middle">Diagonal = aciertos · fuera de la diagonal = errores</text>
  </svg>
  <table class="chuleta">
    <thead><tr><th>Métrica</th><th>Qué mide</th><th>Cálculo y valor del ejemplo</th></tr></thead>
    <tbody>
      <tr><td><strong>Exactitud</strong> (accuracy)</td><td>Aciertos sobre el total</td><td><code>(TP+TN)/total</code> = 125/150 ≈ 0,83</td></tr>
      <tr><td><strong>Precisión</strong> (precision, PPV)</td><td>De los que predice positivos, cuántos lo son</td><td><code>TP/(TP+FP)</code> = 95/115 ≈ 0,83</td></tr>
      <tr><td><strong>Sensibilidad</strong> (recall)</td><td>De los positivos reales, cuántos detecta</td><td><code>TP/(TP+FN)</code> = 95/100 = 0,95</td></tr>
      <tr><td><strong>Especificidad</strong></td><td>De los negativos reales, cuántos detecta</td><td><code>TN/(TN+FP)</code> = 30/50 = 0,6</td></tr>
      <tr><td><strong>F1-score</strong></td><td>Media armónica de precisión y sensibilidad</td><td>≈ 0,89</td></tr>
      <tr><td><strong>Kappa</strong></td><td>Concordancia descontando el azar</td><td>≈ 0,55</td></tr>
      <tr><td><strong>NPV</strong></td><td>De los que predice negativos, cuántos lo son</td><td><code>TN/(TN+FN)</code> = 30/35 ≈ 0,86</td></tr>
    </tbody>
  </table>
  <p class="nota">Exactitud alta, pero <strong>20 personas con VIH</strong> reciben un «sano»: en un diagnóstico médico este modelo no sería admisible.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Curva ROC y AUC</div>
  <svg class="svg-ancho" viewBox="0 0 340 224" role="img" aria-label="Curva ROC: un buen modelo sube rápido hacia la esquina superior izquierda; la diagonal representa el azar con AUC 0,5">
    <line x1="60" y1="180" x2="300" y2="180" stroke="currentColor" stroke-opacity="0.5"/>
    <line x1="60" y1="180" x2="60" y2="20" stroke="currentColor" stroke-opacity="0.5"/>
    <path d="M60 180 L 60 20 L 300 20" fill="none" stroke="currentColor" stroke-opacity="0.25" stroke-dasharray="2 3"/>
    <line x1="60" y1="180" x2="300" y2="20" stroke="currentColor" stroke-opacity="0.6" stroke-dasharray="5 4"/>
    <path d="M60 180 C 62 70, 110 32, 156 28 S 260 20, 300 20" fill="currentColor" fill-opacity="0.08" stroke="currentColor" stroke-width="2.5"/>
    <circle cx="156" cy="28" r="4.5" fill="#c62828"/>
    <text x="164" y="46" style="fill:#c62828">Ejemplo VIH: (0,4 ; 0,95)</text>
    <text x="90" y="100">Buen modelo:</text>
    <text x="90" y="114">AUC ≈ 1</text>
    <text x="222" y="118">Azar: AUC = 0,5</text>
    <text x="60" y="194" text-anchor="middle">0</text>
    <text x="300" y="194" text-anchor="middle">1</text>
    <text x="52" y="24" text-anchor="end">1</text>
    <text x="180" y="214" text-anchor="middle">Tasa de falsos positivos (1 − especificidad)</text>
    <text x="0" y="0" text-anchor="middle" transform="translate(30,100) rotate(-90)">Sensibilidad</text>
  </svg>
  <p class="nota">Cada punto de la curva es un umbral de decisión distinto. Cuanto más se acerca a la esquina superior izquierda, mejor separa las clases.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Cómo decide cada algoritmo</div>
  <div class="mini-graficos">
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><path d="M5 55 C 25 55, 30 8, 45 8 S 65 55, 85 55" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/><path d="M35 55 C 55 55, 60 24, 75 24 S 95 55, 115 55" fill="none" stroke="currentColor" stroke-width="2" stroke-dasharray="4 3"/><line x1="55" y1="6" x2="55" y2="55" stroke="#c62828" stroke-dasharray="3 2"/><circle cx="55" cy="55" r="3.5" fill="#c62828"/></svg>
      <strong>Naive Bayes</strong>Calcula la probabilidad de cada clase y elige la más alta.
      <span class="accion">Texto, spam, variables discretas.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><g fill="currentColor"><circle cx="15" cy="15" r="3.5"/><circle cx="25" cy="27" r="3.5"/><circle cx="18" cy="42" r="3.5"/><circle cx="45" cy="22" r="3.5"/><circle cx="40" cy="36" r="3.5"/></g><g fill="none" stroke="currentColor" stroke-width="1.5"><rect x="67" y="37" width="7" height="7"/><rect x="82" y="12" width="7" height="7"/><rect x="92" y="30" width="7" height="7"/><rect x="100" y="45" width="7" height="7"/><rect x="104" y="15" width="7" height="7"/></g><circle cx="55" cy="32" r="19" fill="none" stroke="#c62828" stroke-dasharray="3 2"/><circle cx="55" cy="32" r="3.5" fill="#c62828"/></svg>
      <strong>KNN</strong>Mira los <em>k</em> vecinos más cercanos y vota la clase mayoritaria.
      <span class="accion">Escalar siempre. Pocas dimensiones.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><line x1="2" y1="30" x2="118" y2="30" stroke="#c62828" stroke-dasharray="3 2"/><path d="M5 52 C 50 52, 70 8, 115 8" fill="none" stroke="currentColor" stroke-width="2.5"/><g fill="currentColor" fill-opacity="0.5"><circle cx="10" cy="56" r="3"/><circle cx="22" cy="56" r="3"/><circle cx="34" cy="56" r="3"/><circle cx="48" cy="56" r="3"/><circle cx="72" cy="4" r="3"/><circle cx="86" cy="4" r="3"/><circle cx="100" cy="4" r="3"/><circle cx="112" cy="4" r="3"/></g></svg>
      <strong>Regresión logística</strong>La sigmoide da una probabilidad de 0 a 1; se compara con un umbral (0,5).
      <span class="accion">Frontera lineal, fácil de interpretar.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><line x1="30" y1="58" x2="90" y2="2" stroke="currentColor" stroke-width="2.5"/><line x1="18" y1="58" x2="78" y2="2" stroke="currentColor" stroke-dasharray="3 2"/><line x1="42" y1="58" x2="102" y2="2" stroke="currentColor" stroke-dasharray="3 2"/><g fill="currentColor"><circle cx="15" cy="20" r="3"/><circle cx="28" cy="10" r="3"/><circle cx="25" cy="34" r="3"/><circle cx="10" cy="44" r="3"/><circle cx="48" cy="30" r="3"/></g><g fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="85" cy="50" r="3"/><circle cx="100" cy="40" r="3"/><circle cx="105" cy="54" r="3"/><circle cx="76" cy="56" r="3"/><circle cx="61" cy="40" r="3"/></g><circle cx="48" cy="30" r="6" fill="none" stroke="#c62828" stroke-width="1.5"/><circle cx="61" cy="40" r="6" fill="none" stroke="#c62828" stroke-width="1.5"/></svg>
      <strong>SVM</strong>Busca la frontera con el <em>margen máximo</em>; solo cuentan los vectores soporte.
      <span class="accion">Kernels para fronteras curvas. Escalar.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><g fill="none" stroke="currentColor" stroke-width="1.5"><line x1="60" y1="14" x2="30" y2="30"/><line x1="60" y1="14" x2="90" y2="30"/><line x1="90" y1="38" x2="72" y2="48"/><line x1="90" y1="38" x2="108" y2="48"/></g><rect x="45" y="3" width="30" height="12" rx="2" fill="currentColor"/><rect x="15" y="28" width="30" height="12" rx="2" fill="currentColor" fill-opacity="0.3" stroke="currentColor"/><rect x="75" y="28" width="30" height="12" rx="2" fill="currentColor"/><rect x="58" y="46" width="28" height="12" rx="2" fill="currentColor" fill-opacity="0.3" stroke="currentColor"/><rect x="94" y="46" width="24" height="12" rx="2" fill="#c62828" fill-opacity="0.3" stroke="#c62828"/></svg>
      <strong>Árbol de decisión</strong>Divide con reglas sencillas hasta llegar a hojas lo más puras posible (Gini o entropía).
      <span class="accion">Interpretable. Limitar la profundidad.</span>
    </div>
  </div>
  <div class="comparativa">
    <div class="col">
      <span class="etiqueta">Ensamble en paralelo</span>
      <h4>Random Forest</h4>
      <ul>
        <li>Muchos árboles, cada uno con una muestra aleatoria de datos (con reemplazo) y de variables.</li>
        <li>Cada árbol vota y gana la clase mayoritaria.</li>
        <li>Reduce el sobreajuste, aguanta ruido y outliers y mide la importancia de las variables.</li>
      </ul>
    </div>
    <div class="col">
      <span class="etiqueta">Ensamble en secuencia</span>
      <h4>AdaBoost</h4>
      <ul>
        <li>Modelos débiles (árboles de un solo nivel, <em>stumps</em>) entrenados uno tras otro.</li>
        <li>Cada nuevo modelo da más peso a los datos mal clasificados por el anterior.</li>
        <li>Votación ponderada: los modelos más fiables pesan más. Muy sensible a ruido y outliers.</li>
      </ul>
    </div>
  </div>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Chuleta comparativa de algoritmos</div>
  <table class="chuleta">
    <thead><tr><th>Algoritmo</th><th>Funciona bien con…</th><th>Cuidado con…</th><th>Hiperparámetros clave</th></tr></thead>
    <tbody>
      <tr><td><strong>Naive Bayes</strong></td><td>Texto, muchas variables discretas, pocos datos</td><td>Variables muy correlacionadas (supone independencia)</td><td>Tipo: gaussiano, multinomial, Bernoulli</td></tr>
      <tr><td><strong>KNN</strong></td><td>Clases bien separadas, pocas dimensiones, datos normalizados</td><td>Muchas dimensiones, ruido, datos grandes (lento)</td><td><code>k</code>, distancia</td></tr>
      <tr><td><strong>Regresión logística</strong></td><td>Separación aproximadamente lineal; necesitas interpretar</td><td>Relaciones no lineales, multicolinealidad</td><td><code>C</code>, L1 / L2</td></tr>
      <tr><td><strong>SVM</strong></td><td>Muchas características y pocos datos, márgenes claros</td><td>Solapamiento, ruido, datos grandes</td><td><code>C</code>, kernel, <code>gamma</code></td></tr>
      <tr><td><strong>Árbol de decisión</strong></td><td>Reglas simples, datos mixtos, explicar decisiones</td><td>Crecer sin límite (sobreajuste), fronteras curvas</td><td><code>max_depth</code>, <code>min_samples_leaf</code></td></tr>
      <tr><td><strong>Random Forest</strong></td><td>Muchas variables, ruido, relaciones no lineales</td><td>Poco interpretable, más coste de cálculo</td><td><code>n_estimators</code>, <code>max_features</code></td></tr>
      <tr><td><strong>AdaBoost</strong></td><td>Datos limpios con fronteras complejas</td><td>Ruido y outliers, no se paraleliza</td><td><code>n_estimators</code>, <code>learning_rate</code></td></tr>
    </tbody>
  </table>
  <p class="nota">Escalar es imprescindible en KNN, SVM y regresión logística (MinMaxScaler o StandardScaler). Cada problema es distinto: siempre hay que ajustar, validar y comparar.</p>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Matriz de confusión</dt><dd>Tabla que cruza las clases reales con las predichas: TP, TN, FP y FN.</dd>
  <dt>Precisión</dt><dd>Porcentaje de predicciones positivas que realmente son positivas.</dd>
  <dt>Sensibilidad (recall)</dt><dd>Porcentaje de positivos reales que el modelo detecta.</dd>
  <dt>F1-score</dt><dd>Media armónica de precisión y sensibilidad; útil con clases desequilibradas.</dd>
  <dt>Curva ROC / AUC</dt><dd>Gráfico de sensibilidad frente a falsos positivos para distintos umbrales; el AUC va de 0,5 (azar) a 1 (perfecto).</dd>
  <dt>Kernel</dt><dd>Función que permite a SVM separar clases como si los datos estuvieran en un espacio de más dimensiones.</dd>
  <dt>Ensamble</dt><dd>Modelo que combina muchos modelos (Random Forest, AdaBoost) para ganar precisión y estabilidad.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Fiarse solo de la exactitud.** Con muy pocos casos positivos, predecir siempre la clase mayoritaria da una exactitud alta sin aprender nada.
- **Usar siempre la misma métrica.** Hay que pensar qué error es más grave en cada problema y elegir la métrica que lo vigila.
- **Aplicar KNN, SVM o regresión logística sin escalar.** La variable con el rango más amplio domina el resultado.
- **Dejar crecer un árbol sin límites.** Memoriza los datos; limita `max_depth` o pasa a Random Forest.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>Solo el 2 % de las transacciones son fraude y tu modelo tiene un 98 % de exactitud. ¿Es un buen modelo?</summary>
    <div class="respuesta">No se sabe: diciendo siempre «no fraude» ya se acierta el 98 %. Con clases desequilibradas hay que mirar la <strong>matriz de confusión</strong>, la sensibilidad y el <strong>F1-score</strong>.</div></details>
  <details><summary>En una enfermedad muy contagiosa no quieres que se te escape ningún caso, aunque haya falsas alarmas. ¿Qué métrica priorizas?</summary>
    <div class="respuesta">La <strong>sensibilidad (recall)</strong>: mide qué porcentaje de enfermos reales detecta el modelo. En regresión logística, además, se puede bajar el umbral por debajo de 0,5.</div></details>
  <details><summary>En KNN eliges k = 1. ¿Qué riesgo corres?</summary>
    <div class="respuesta">Que el modelo sea muy <strong>sensible al ruido</strong>: basta un dato mal etiquetado para cambiar la predicción (sobreajuste). Un k demasiado grande, en cambio, suaviza en exceso. Se elige probando con validación cruzada, mejor con valores impares.</div></details>
  <details><summary>Tu modelo acierta 42 de 45 positivos en validación, pero solo 30 de 45 en un test externo. ¿Qué indica?</summary>
    <div class="respuesta">Que está <strong>sobreajustado</strong>: funciona con los datos que conoce pero no generaliza a casos nuevos. Hay que revisarlo antes de usarlo.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/NeHhxBUhndI">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad3/l2.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L21.ipynb">Colab: inicio del ejemplo</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad3/csv/wildfires.csv">Datos: incendios (CSV)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L22.ipynb">Colab: Naive Bayes</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L23.ipynb">Colab: KNN</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L24.ipynb">Colab: regresión logística</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L25.ipynb">Colab: SVM</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L26.ipynb">Colab: árboles y Random Forest</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L27.ipynb">Colab: AdaBoost</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L28.ipynb">Colab: final del ejemplo</a>
</div>

## Lección 3. Modelos de regresión {#leccion-3}

<div class="ficha-lead">
La regresión <strong>predice un valor numérico continuo</strong>: un precio, una duración, un consumo. Se evalúa midiendo <strong>cuánto se equivoca</strong> (MAE, MSE, RMSE) y <strong>cuánto explica</strong> (R²), y revisando los errores con gráficos.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>MAE trata todos los errores igual.</strong> Es la media de los errores absolutos: robusta frente a valores extremos.</div>
  <div class="idea"><strong>MSE y RMSE castigan los errores grandes.</strong> Un error cuatro veces mayor pesa dieciséis veces más. El RMSE vuelve a las unidades de la variable (euros, minutos), así que se lee mejor.</div>
  <div class="idea"><strong>R² nunca va solo.</strong> Indica qué parte de la variabilidad explica el modelo (0,85 = 85 %), pero no lo cerca que están las predicciones. Un R² algo menor con un RMSE mucho menor puede ser mejor modelo.</div>
  <div class="idea"><strong>Exactitud ≠ precisión.</strong> Exacto: acierta cerca del valor real. Preciso: sus predicciones son coherentes entre sí, aunque estén lejos del valor correcto.</div>
  <div class="idea"><strong>Mira los errores uno a uno.</strong> Comparar predicción y valor real, el gráfico de predicciones frente a reales y el de residuos revela fallos que la métrica global esconde.</div>
  <div class="idea"><strong>Mismos algoritmos, otra salida.</strong> La regresión lineal es propia de regresión; SVM (SVR), árboles, Random Forest y AdaBoost se adaptan para predecir números.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">MAE, MSE y RMSE</div>
  <div class="comparativa">
    <div class="col"><h4>MAE</h4><ul><li>Media de los errores en valor absoluto.</li><li>Todos los errores pesan igual.</li><li><strong>Úsalo</strong> si no quieres que unos pocos extremos dominen (consumos, temperaturas, tiempos de entrega).</li></ul></div>
    <div class="col"><h4>MSE</h4><ul><li>Media de los errores al cuadrado.</li><li>Los errores grandes pesan muchísimo; muy sensible a atípicos.</li><li><strong>Úsalo</strong> si un error grande es especialmente costoso (viviendas, costes médicos).</li></ul></div>
    <div class="col"><h4>RMSE</h4><ul><li>Raíz cuadrada del MSE.</li><li>Penaliza los errores grandes, pero en las <strong>mismas unidades</strong> que los datos.</li><li><strong>Úsalo</strong> para interpretar fácilmente el margen medio de error.</li></ul></div>
  </div>
  <table class="tabla-mini">
    <thead><tr><th>Coche usado</th><th>Error</th><th>Error absoluto</th><th>Error al cuadrado</th></tr></thead>
    <tbody>
      <tr><td>Vale 10.000 €, predice 9.000 €</td><td>1.000 €</td><td>1.000</td><td>1.000.000</td></tr>
      <tr><td>Vale 15.000 €, predice 10.000 €</td><td>5.000 €</td><td>5.000</td><td class="si">25.000.000</td></tr>
      <tr><td><strong>Media</strong></td><td></td><td class="si">MAE = 3.000</td><td class="si">MSE = 13.000.000</td></tr>
    </tbody>
  </table>
  <p class="nota"><strong>R²</strong> completa la foto: 1 = predicción perfecta, 0 = no mejora a predecir siempre la media, negativo = peor que la media. Con muchas variables, mejor el R² ajustado.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Exactitud y precisión: la diana</div>
  <svg class="svg-ancho" viewBox="0 0 400 132" role="img" aria-label="Cuatro dianas: puntos dispersos alrededor del centro, puntos dispersos lejos del centro, puntos agrupados en el centro y puntos agrupados lejos del centro">
    <g fill="none" stroke="currentColor" stroke-opacity="0.5"><circle cx="50" cy="52" r="40"/><circle cx="50" cy="52" r="26"/><circle cx="50" cy="52" r="12"/><circle cx="150" cy="52" r="40"/><circle cx="150" cy="52" r="26"/><circle cx="150" cy="52" r="12"/><circle cx="250" cy="52" r="40"/><circle cx="250" cy="52" r="26"/><circle cx="250" cy="52" r="12"/><circle cx="350" cy="52" r="40"/><circle cx="350" cy="52" r="26"/><circle cx="350" cy="52" r="12"/></g>
    <g fill="currentColor"><circle cx="50" cy="52" r="2"/><circle cx="150" cy="52" r="2"/><circle cx="250" cy="52" r="2"/><circle cx="350" cy="52" r="2"/></g>
    <g fill="#c62828"><circle cx="28" cy="37" r="3.5"/><circle cx="70" cy="70" r="3.5"/><circle cx="75" cy="40" r="3.5"/><circle cx="32" cy="72" r="3.5"/><circle cx="52" cy="24" r="3.5"/></g>
    <g fill="#c62828"><circle cx="165" cy="22" r="3.5"/><circle cx="182" cy="44" r="3.5"/><circle cx="145" cy="30" r="3.5"/><circle cx="178" cy="72" r="3.5"/><circle cx="122" cy="24" r="3.5"/></g>
    <g fill="#c62828"><circle cx="250" cy="52" r="3.5"/><circle cx="254" cy="49" r="3.5"/><circle cx="246" cy="55" r="3.5"/><circle cx="253" cy="56" r="3.5"/><circle cx="247" cy="48" r="3.5"/></g>
    <g fill="#c62828"><circle cx="372" cy="30" r="3.5"/><circle cx="376" cy="27" r="3.5"/><circle cx="368" cy="33" r="3.5"/><circle cx="375" cy="34" r="3.5"/><circle cx="369" cy="26" r="3.5"/></g>
    <text x="50" y="110" text-anchor="middle">Alta exactitud</text>
    <text x="50" y="124" text-anchor="middle">baja precisión</text>
    <text x="150" y="110" text-anchor="middle">Baja exactitud</text>
    <text x="150" y="124" text-anchor="middle">baja precisión</text>
    <text x="250" y="110" text-anchor="middle">Alta exactitud</text>
    <text x="250" y="124" text-anchor="middle">alta precisión</text>
    <text x="350" y="110" text-anchor="middle">Baja exactitud</text>
    <text x="350" y="124" text-anchor="middle">alta precisión</text>
  </svg>
  <p class="nota">El último caso suele indicar un <strong>error sistemático</strong>: el modelo se equivoca siempre de forma parecida. Ej.: predecir siempre 155.000 € para pisos de 120.000, 190.000 y 155.000 €.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Regresión lineal y residuos</div>
  <svg class="svg-ancho" viewBox="0 0 360 150" role="img" aria-label="A la izquierda, puntos con una recta ajustada y los residuos como segmentos verticales rojos. A la derecha, dos gráficos de residuos: uno con puntos aleatorios alrededor de cero y otro con forma de curva">
    <text x="95" y="12" text-anchor="middle">Recta y residuos</text>
    <line x1="20" y1="135" x2="170" y2="135" stroke="currentColor" stroke-opacity="0.4"/>
    <line x1="20" y1="20" x2="20" y2="135" stroke="currentColor" stroke-opacity="0.4"/>
    <g stroke="#c62828" stroke-width="1.5"><line x1="35" y1="100" x2="35" y2="114"/><line x1="55" y1="112" x2="55" y2="102"/><line x1="75" y1="80" x2="75" y2="90"/><line x1="95" y1="90" x2="95" y2="77"/><line x1="115" y1="58" x2="115" y2="66"/><line x1="135" y1="62" x2="135" y2="53"/><line x1="155" y1="30" x2="155" y2="41"/></g>
    <line x1="25" y1="120" x2="165" y2="35" stroke="currentColor" stroke-width="2.5"/>
    <g fill="currentColor"><circle cx="35" cy="100" r="3"/><circle cx="55" cy="112" r="3"/><circle cx="75" cy="80" r="3"/><circle cx="95" cy="90" r="3"/><circle cx="115" cy="58" r="3"/><circle cx="135" cy="62" r="3"/><circle cx="155" cy="30" r="3"/></g>
    <text x="270" y="12" text-anchor="middle">Gráfico de residuos</text>
    <text x="270" y="28" text-anchor="middle">Aleatorios alrededor de 0: bien</text>
    <line x1="200" y1="50" x2="340" y2="50" stroke="currentColor" stroke-opacity="0.5" stroke-dasharray="4 3"/>
    <g fill="currentColor"><circle cx="210" cy="45" r="2.5"/><circle cx="225" cy="57" r="2.5"/><circle cx="240" cy="43" r="2.5"/><circle cx="255" cy="54" r="2.5"/><circle cx="270" cy="47" r="2.5"/><circle cx="285" cy="60" r="2.5"/><circle cx="300" cy="41" r="2.5"/><circle cx="315" cy="52" r="2.5"/><circle cx="330" cy="47" r="2.5"/></g>
    <text x="270" y="90" text-anchor="middle" style="fill:#c62828">Con forma o grupos: revisar</text>
    <line x1="200" y1="120" x2="340" y2="120" stroke="currentColor" stroke-opacity="0.5" stroke-dasharray="4 3"/>
    <g fill="#c62828"><circle cx="210" cy="104" r="2.5"/><circle cx="225" cy="113" r="2.5"/><circle cx="240" cy="120" r="2.5"/><circle cx="255" cy="126" r="2.5"/><circle cx="270" cy="129" r="2.5"/><circle cx="285" cy="126" r="2.5"/><circle cx="300" cy="120" r="2.5"/><circle cx="315" cy="112" r="2.5"/><circle cx="330" cy="103" r="2.5"/></g>
  </svg>
  <p class="nota">La recta se ajusta por <strong>mínimos cuadrados</strong>: minimiza la suma de los residuos al cuadrado. Exige linealidad, residuos normales, varianza constante (homoscedasticidad), sin autocorrelación y, en la múltiple, evitar la multicolinealidad.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Los algoritmos de regresión</div>
  <table class="chuleta">
    <thead><tr><th>Algoritmo</th><th>Cómo predice</th><th>A tener en cuenta</th><th>Hiperparámetros clave</th></tr></thead>
    <tbody>
      <tr><td><strong>Regresión lineal</strong></td><td>Recta o hiperplano por mínimos cuadrados</td><td>Interpretable; no capta relaciones no lineales; sensible a outliers</td><td><code>fit_intercept</code></td></tr>
      <tr><td><strong>SVR</strong></td><td>Línea o curva con un margen de tolerancia ε: los errores pequeños no cuentan</td><td>Escalar siempre; robusta al ruido; poco interpretable y lenta con muchos datos</td><td><code>epsilon</code>, <code>C</code>, kernel, <code>gamma</code></td></tr>
      <tr><td><strong>Árbol de decisión</strong></td><td>Cada hoja devuelve la media de sus datos: predicción escalonada</td><td>Divide reduciendo la varianza; sobreajusta sin límites; no necesita escalar</td><td><code>max_depth</code> (3-7), <code>min_samples_leaf</code> (5-20)</td></tr>
      <tr><td><strong>Random Forest</strong></td><td>Media de muchos árboles distintos</td><td>Reduce la varianza; aguanta ruido; menos interpretable</td><td><code>n_estimators</code>, <code>max_features='sqrt'</code></td></tr>
      <tr><td><strong>AdaBoost</strong></td><td>Media ponderada de árboles simples en secuencia, cada uno centrado en los errores grandes</td><td>Muy sensible a outliers; no se paraleliza</td><td><code>n_estimators</code> (50-200), <code>learning_rate</code> (0.01-1), <code>loss</code></td></tr>
    </tbody>
  </table>
  <p class="nota">Las cifras entre paréntesis son orientativas, según el material, para conjuntos pequeños o medianos.</p>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>MAE</dt><dd>Error absoluto medio: cuánto se equivoca el modelo de media, sin importar el signo.</dd>
  <dt>MSE</dt><dd>Error cuadrático medio: media de los errores al cuadrado; castiga los errores grandes.</dd>
  <dt>RMSE</dt><dd>Raíz del MSE; mide el error en las mismas unidades que la variable.</dd>
  <dt>R²</dt><dd>Coeficiente de determinación: proporción de la variabilidad que explica el modelo.</dd>
  <dt>Residuo</dt><dd>Diferencia entre el valor real y el valor predicho.</dd>
  <dt>Homoscedasticidad</dt><dd>Que la dispersión de los residuos sea constante para todas las predicciones.</dd>
  <dt>Margen ε (epsilon)</dt><dd>En SVR, «colchón» de tolerancia: los errores dentro de él no se penalizan.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Valorar el modelo solo con R².** Puede ser alto y aun así haber errores importantes; acompáñalo siempre de MAE o RMSE.
- **Fiarse de la métrica global sin mirar los casos.** Revisa predicciones una a una y los residuos: puede fallar mucho en ciertos rangos.
- **Usar regresión lineal cuando la relación no es lineal** o cuando los residuos muestran patrones.
- **Entrenar SVR sin escalar** o dejar crecer un árbol de regresión sin limitar su profundidad.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>Modelo A: R² = 0,89 y RMSE = 5.000 €. Modelo B: R² = 0,85 y RMSE = 3.000 €. ¿Cuál es probablemente más útil para predecir precios?</summary>
    <div class="respuesta">El <strong>B</strong>: comete errores menores de media aunque explique algo menos de la variabilidad. Con cantidades económicas, el tamaño del error suele importar más.</div></details>
  <details><summary>Tu modelo tiene un R² negativo. ¿Qué significa?</summary>
    <div class="respuesta">Que funciona <strong>peor que predecir siempre la media</strong> de los datos. Hay que revisar el modelo o el planteamiento.</div></details>
  <details><summary>En el gráfico de residuos, los puntos forman una curva clara. ¿Es buena señal?</summary>
    <div class="respuesta">No. En un modelo que generaliza bien, los residuos se reparten <strong>al azar alrededor de cero</strong>. Una forma curva indica que el modelo no capta la estructura de los datos (por ejemplo, una relación no lineal).</div></details>
  <details><summary>Un error grande es especialmente grave en tu problema. ¿MAE o RMSE?</summary>
    <div class="respuesta"><strong>RMSE</strong> (o MSE), porque eleva los errores al cuadrado y castiga con fuerza los grandes. El MAE es preferible si buscas una medida robusta frente a valores extremos.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/lTEX-qJ9fE0">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad3/l3.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L31.ipynb">Colab: inicio del ejemplo</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad3/csv/drug_effect_time.csv">Datos: efecto del medicamento (CSV)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L32.ipynb">Colab: regresión lineal</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L33.ipynb">Colab: SVR</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L34.ipynb">Colab: árboles y Random Forest</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L35.ipynb">Colab: AdaBoost</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L36.ipynb">Colab: final del ejemplo</a>
</div>

## Síntesis de la unidad {#sintesis}

<div class="ficha-lead">
Un proyecto supervisado en una página: <strong>qué preguntas hacerte, en orden</strong>, y qué métrica o algoritmo usar en cada caso.
</div>

### El camino de un proyecto supervisado

<div class="diagrama">
  <div class="ruta">
    <div class="etapa">
      <div class="nombre"><span class="num">1</span>Plantear</div>
      <div class="pregunta">¿Quiero predecir una categoría o un número?</div>
      <div class="tecnicas">Clasificación (binaria o multiclase) o regresión</div>
      <span class="leccion">Lección 1</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">2</span>Preparar y dividir</div>
      <div class="pregunta">¿Datos limpios y separados para evaluar sin trampas?</div>
      <div class="tecnicas">Preprocesamiento (Unidad 2); entrenamiento, validación y prueba</div>
      <span class="leccion">Lección 1</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">3</span>Elegir algoritmo</div>
      <div class="pregunta">¿Qué modelo encaja con mis datos?</div>
      <div class="tecnicas">Naive Bayes, KNN, regresión logística, SVM, árboles, Random Forest, AdaBoost, regresión lineal</div>
      <span class="leccion">Lecciones 2 y 3</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">4</span>Entrenar y medir</div>
      <div class="pregunta">¿Qué error me importa más?</div>
      <div class="tecnicas">Matriz de confusión, precisión, recall, F1, AUC · MAE, RMSE, R²</div>
      <span class="leccion">Lecciones 2 y 3</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">5</span>Vigilar el sobreajuste</div>
      <div class="pregunta">¿Generaliza o ha memorizado?</div>
      <div class="tecnicas">Validación cruzada, entrenamiento frente a test, curvas de aprendizaje, residuos</div>
      <span class="leccion">Lecciones 1-3</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">6</span>Optimizar</div>
      <div class="pregunta">¿Puedo mejorarlo sin sobreajustar?</div>
      <div class="tecnicas">Hiperparámetros con <em>grid search</em> o <em>random search</em>, regularización, otro algoritmo</div>
      <span class="leccion">Lección 1</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">7</span>Probar y concluir</div>
      <div class="pregunta">¿Funciona con datos nuevos y casos extremos?</div>
      <div class="tecnicas">Test final, datos externos, interpretar y comunicar los resultados</div>
      <span class="leccion">Lección 1</span>
    </div>
  </div>
  <p class="nota">Validar y optimizar se repite varias veces: es un ciclo, no una línea recta.</p>
</div>

### Si ves… haz…

<div class="diagrama">
  <table class="decisiones">
    <tbody>
      <tr><td>La salida es una categoría o un número continuo</td><td>Clasificación en el primer caso, regresión en el segundo</td></tr>
      <tr><td>Clases desequilibradas</td><td>No te fíes de la exactitud: matriz de confusión y F1-score</td></tr>
      <tr><td>No puede escaparse ningún caso positivo</td><td>Prioriza la sensibilidad (recall); en regresión logística, baja el umbral</td></tr>
      <tr><td>Error muy bajo en entrenamiento y alto en validación</td><td>Sobreajuste: limita la profundidad, regulariza, reduce <code>gamma</code> o <code>C</code>, prueba Random Forest</td></tr>
      <tr><td>Errores altos en entrenamiento y validación</td><td>Subajuste: prueba un modelo más flexible o ajusta sus hiperparámetros</td></tr>
      <tr><td>Texto o muchas variables discretas</td><td>Naive Bayes como punto de partida</td></tr>
      <tr><td>Hay que explicar cada decisión</td><td>Árbol de decisión, regresión logística o regresión lineal</td></tr>
      <tr><td>Vas a usar KNN, SVM, SVR o regresión logística</td><td>Escala antes las variables numéricas</td></tr>
      <tr><td>En regresión, un error grande es muy costoso</td><td>Evalúa con RMSE o MSE; si quieres robustez frente a extremos, MAE</td></tr>
      <tr><td>Los residuos forman curvas o grupos</td><td>El modelo no capta la estructura: revisa variables o cambia de algoritmo</td></tr>
    </tbody>
  </table>
</div>

### Tres reglas de oro

<div class="reglas">
  <div class="regla"><strong>Evalúa con datos nuevos</strong>Un modelo solo es bueno si acierta con datos que no ha visto al entrenar.</div>
  <div class="regla"><strong>La métrica la elige el problema</strong>Piensa qué error sale más caro y vigila la métrica que lo mide.</div>
  <div class="regla"><strong>No hay algoritmo universal</strong>Prueba varios, ajusta, valida y compara antes de decidir.</div>
</div>

### Ponlo en práctica

Dos ejemplos completos para repetir todo el proceso con datos nuevos: uno de clasificación (éxito de un producto en el mercado) y otro de regresión (estadísticas de salud de pacientes).

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/GMsA2fVC_VA">▶ Vídeo: ejemplo de clasificación</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L29.ipynb">Notebook de clasificación (Colab)</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad3/csv/product_success_prediction_extended.csv">Datos de clasificación (CSV)</a>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/5sBVe-pOh3A">▶ Vídeo: ejemplo de regresión</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad3/cuadernos/U3L37.ipynb">Notebook de regresión (Colab)</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad3/csv/treatments.csv">Datos de regresión (CSV)</a>
</div>
