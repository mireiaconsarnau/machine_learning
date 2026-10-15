---
title: "Unidad 2"
parent: "Resúmenes visuales"
nav_order: 2
---

# Resumen visual · Unidad 2. Preprocesamiento de datos

[Ir a la unidad completa](../unidad2/unidad2.md){: .btn .btn-outline }

## Lección 1. Importancia del preprocesamiento {#leccion-1}

<div class="ficha-lead">
Un modelo solo es tan bueno como los datos con los que aprende. <strong>Preprocesar</strong> es revisar, limpiar y transformar los datos en bruto para que el modelo aprenda <strong>patrones reales</strong> y no errores ni sesgos.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>Calidad:</strong> datos completos, bien organizados y que representen la realidad. Con datos erróneos, el modelo podría predecir que una casa pequeña vale más que una grande.</div>
  <div class="idea"><strong>Consistencia:</strong> la misma información, siempre en el mismo formato y sin contradicciones. «1,000» y «1000 euros», o «Nueva York» y «New York», confunden al modelo.</div>
  <div class="idea"><strong>Sesgos:</strong> los duplicados cuentan la misma información varias veces, y si hay muchos más datos de un grupo, el modelo tenderá a favorecerlo.</div>
  <div class="idea"><strong>Solo con los datos de entrenamiento.</strong> Las transformaciones que «aprenden» de los datos se ajustan con el entrenamiento y después se aplican a la prueba, para que el modelo no vea información que no debería.</div>
  <div class="idea"><strong>No es una receta fija.</strong> Según el problema, los pasos cambian de orden, se combinan o se omiten. Y tras entrenar, se puede volver atrás a probar otras opciones.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">Trabajar los datos de forma estructurada</div>
  <div class="flujo cinco">
    <div class="paso"><span class="num">1</span><strong>Explorar</strong>Distribuciones, atípicos, correlaciones</div>
    <div class="paso"><span class="num">2</span><strong>Limpiar</strong>Nulos, duplicados, errores, formatos</div>
    <div class="paso"><span class="num">3</span><strong>Transformar</strong>Normalizar, escalar, codificar</div>
    <div class="paso"><span class="num">4</span><strong>Seleccionar</strong>Quedarse con las variables útiles (filtrado, PCA)</div>
    <div class="paso"><span class="num">5</span><strong>Dividir</strong>Entrenamiento y prueba</div>
  </div>
  <p class="nota">Es un proceso dinámico: tras entrenar el modelo se pueden probar otras limpiezas o transformaciones.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Las herramientas de la unidad</div>
  <div class="comparativa">
    <div class="col"><h4>NumPy</h4><ul><li>Arrays y operaciones matemáticas rápidas con muchos datos numéricos.</li></ul></div>
    <div class="col"><h4>Pandas</h4><ul><li>Datos en tabla: detectar nulos y duplicados, transformar columnas.</li></ul></div>
    <div class="col"><h4>Matplotlib</h4><ul><li>Gráficos para ver distribuciones, relaciones y valores atípicos.</li></ul></div>
    <div class="col"><h4>Scikit-learn</h4><ul><li>Codificar, escalar, seleccionar características y crear pipelines.</li></ul></div>
  </div>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Preprocesamiento</dt><dd>Conjunto de pasos para convertir datos en bruto en una base sólida y coherente para el modelo.</dd>
  <dt>Calidad de datos</dt><dd>Que los datos estén completos, organizados y representen lo que queremos analizar.</dd>
  <dt>Consistencia</dt><dd>Que la información esté alineada: mismos formatos, sin contradicciones.</dd>
  <dt>Sesgo</dt><dd>Desviación que altera los resultados o su interpretación, por ejemplo favorecer a un grupo.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Ir directamente al modelo sin mirar los datos.** El modelo aprenderá también sus errores.
- **Ajustar transformaciones con todos los datos antes de dividirlos.** El modelo «ve» información de la prueba y los resultados parecen mejores de lo que son.
- **Aplicar todos los pasos siempre y en el mismo orden.** Cada paso es una herramienta que se usa si el caso lo necesita.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>En una columna un porcentaje aparece como «10 %» y en otra como «0.1». ¿Qué problema de los datos es este?</summary>
    <div class="respuesta">Un problema de <strong>consistencia</strong>: es la misma información en formatos distintos, y el modelo puede confundirse al compararla. Hay que unificar el formato.</div></details>
  <details><summary>¿Por qué el escalado se ajusta solo con los datos de entrenamiento?</summary>
    <div class="respuesta">Para que el modelo <strong>no acceda a información del conjunto de prueba</strong> durante el entrenamiento. Si no, la evaluación sería engañosamente optimista.</div></details>
  <details><summary>Tus datos tienen el triple de registros de un grupo de clientes que de otro. ¿Qué riesgo hay?</summary>
    <div class="respuesta">Que el modelo <strong>favorezca al grupo mayoritario</strong> (sesgo). Detectarlo y equilibrarlo durante el preprocesamiento ayuda a que el modelo sea justo.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/gG059WZI8Ow">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad2/l1.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad2/cuadernos/U2L11.ipynb">Colab: NumPy</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad2/cuadernos/U2L12.ipynb">Colab: Pandas</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad2/cuadernos/U2L13.ipynb">Colab: Matplotlib</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad2/cuadernos/U2L14.ipynb">Colab: Scikit-learn</a>
</div>

## Lección 2. Limpieza de datos {#leccion-2}

<div class="ficha-lead">
Limpiar es <strong>detectar y tratar valores nulos, duplicados y errores</strong>. Es imprescindible porque la calidad final del modelo depende directamente de la calidad de los datos que recibe.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>Identificar antes de tratar.</strong> Primero se localiza el problema; después se decide qué hacer según el tipo de dato, el volumen y la importancia de la variable.</div>
  <div class="idea"><strong>Cada tratamiento tiene un coste.</strong> Eliminar filas pierde información; rellenar con la media puede distorsionar. No hay una opción universal.</div>
  <div class="idea"><strong>Los duplicados no siempre son idénticos.</strong> Puede haber registros casi iguales que requieren un análisis más profundo, sobre todo al combinar fuentes.</div>
  <div class="idea"><strong>Los errores se descubren explorando:</strong> revisando distribuciones, comprobando reglas de negocio y buscando valores que no tienen sentido.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">Los tres problemas de la limpieza</div>
  <div class="arbol">
    <div class="rama">
      <div class="rama-cab">Valores nulos<small>Celdas vacías, NaN, valores especiales</small></div>
      <div class="hoja"><strong>Por qué importan</strong>Muchos algoritmos no los procesan y dan errores o resultados erráticos.</div>
      <div class="hoja"><strong>Detectar</strong><code>isna()</code></div>
      <div class="hoja"><strong>Tratar</strong>Eliminar filas o columnas con muchos nulos · rellenar con media, mediana u otro valor representativo (<code>fillna()</code>) · imputación avanzada con modelos.</div>
    </div>
    <div class="rama">
      <div class="rama-cab">Duplicados<small>Registros repetidos</small></div>
      <div class="hoja"><strong>Por qué importan</strong>Dan un peso excesivo a ciertos casos: el modelo cree que son más frecuentes de lo que son.</div>
      <div class="hoja"><strong>Detectar</strong><code>duplicated()</code>, revisando todas o algunas columnas clave.</div>
      <div class="hoja"><strong>Tratar</strong>Eliminar o consolidar para dejar una sola representación (<code>drop_duplicates()</code>).</div>
    </div>
    <div class="rama">
      <div class="rama-cab">Errores<small>Formatos, rangos, contradicciones</small></div>
      <div class="hoja"><strong>Ejemplos</strong>Fechas mal escritas, edad negativa, precios imposibles, columnas que se contradicen.</div>
      <div class="hoja"><strong>Detectar</strong>Exploración, estadísticas resumen, gráficos, <code>unique()</code>.</div>
      <div class="hoja"><strong>Tratar</strong>Unificar formatos · reemplazar valores fuera de rango · validar con otras fuentes · eliminar si no se pueden corregir.</div>
    </div>
  </div>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Chuleta de Pandas para limpiar</div>
  <table class="chuleta">
    <thead><tr><th>Código</th><th>Para qué sirve</th></tr></thead>
    <tbody>
      <tr><td><code>df.isna().sum()</code></td><td>Cuenta los nulos de cada columna</td></tr>
      <tr><td><code>df['col'].fillna(valor)</code></td><td>Rellena los nulos de una columna</td></tr>
      <tr><td><code>df.duplicated().sum()</code></td><td>Cuenta las filas duplicadas</td></tr>
      <tr><td><code>df.drop_duplicates()</code></td><td>Elimina las filas duplicadas</td></tr>
      <tr><td><code>df['col'].unique()</code></td><td>Muestra los valores distintos (útil para ver errores de escritura)</td></tr>
    </tbody>
  </table>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Valor nulo</dt><dd>Dato ausente o no registrado (celda vacía, <code>NaN</code>).</dd>
  <dt>Imputación</dt><dd>Rellenar valores nulos con un valor estimado: media, mediana o uno calculado con un modelo.</dd>
  <dt>Duplicado</dt><dd>Registro repetido, idéntico o casi idéntico a otro.</dd>
  <dt>Valor fuera de rango</dt><dd>Valor imposible para esa variable, como una edad negativa.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Borrar todas las filas con algún nulo sin mirar cuántas son.** Puedes perder buena parte del dataset.
- **Rellenar siempre con la media.** Con valores extremos, la mediana suele representar mejor los datos.
- **Buscar solo duplicados exactos.** Los casi duplicados también sesgan el modelo.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>En la columna «edad» aparece un −3. ¿Qué tipo de problema es y qué puedes hacer?</summary>
    <div class="respuesta">Es un <strong>valor fuera de rango</strong>. Se puede corregir si se conoce el valor real (validando con otra fuente), reemplazarlo como si fuera un nulo o eliminar el registro si no se puede corregir.</div></details>
  <details><summary>¿Por qué los duplicados perjudican al modelo?</summary>
    <div class="respuesta">Porque el modelo da <strong>más peso</strong> a esos casos e interpreta que sus patrones son más frecuentes de lo que son en realidad.</div></details>
  <details><summary>Una variable poco importante tiene el 70 % de valores nulos. ¿Qué harías?</summary>
    <div class="respuesta">Probablemente <strong>eliminar la columna</strong>: rellenar tantos huecos inventaría la mayor parte de la información, y la variable apenas aporta.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/cywZLikJCcY">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad2/l2.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad2/cuadernos/U2L21.ipynb">Colab: limpieza de datos</a>
</div>

## Lección 3. Visualización exploratoria {#leccion-3}

<div class="ficha-lead">
Antes de entrenar hay que <strong>mirar los datos</strong>. Los gráficos revelan cómo se distribuyen las variables, si hay <strong>valores atípicos</strong>, cómo se <strong>relacionan</strong> entre sí y si hay huecos o <strong>clases desequilibradas</strong>.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>La forma de la distribución importa.</strong> Muchos algoritmos asumen ciertos comportamientos estadísticos; la distribución indica cómo preparar los datos.</div>
  <div class="idea"><strong>Los outliers se ven mejor en un boxplot.</strong> Pueden ser errores (corregir o eliminar) o casos reales valiosos (conservar).</div>
  <div class="idea"><strong>Correlación no es causalidad.</strong> Indica si dos variables se mueven juntas, no si una provoca a la otra.</div>
  <div class="idea"><strong>Pearson o Spearman.</strong> Pearson para relaciones lineales con datos normales; Spearman para relaciones no lineales, datos asimétricos o con atípicos.</div>
  <div class="idea"><strong>Correlación alta ≠ eliminar.</strong> Dos variables muy correlacionadas pueden ser redundantes (multicolinealidad), pero la decisión se toma probando y comparando métricas.</div>
  <div class="idea"><strong>Clases desequilibradas.</strong> Si una clase domina, el modelo puede aprender solo de ella. A veces conviene equilibrar; otras, ajustar solo la métrica.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">Tipos de distribución y qué hacer con cada una</div>
  <div class="mini-graficos">
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><path d="M5 55 C 35 55, 45 8, 60 8 S 85 55, 115 55" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/></svg>
      <strong>Normal</strong>Campana simétrica alrededor de la media.
      <span class="accion">La «ideal» para muchos modelos.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><path d="M5 55 C 14 55, 20 8, 32 8 C 48 8, 58 46, 115 53 L 115 55 Z" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/></svg>
      <strong>Sesgada</strong>Cola larga hacia un lado (ingresos, precios).
      <span class="accion">Logaritmo, raíz cuadrada o Box-Cox.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><path d="M5 55 C 18 55, 22 12, 35 12 C 48 12, 50 38, 60 38 C 70 38, 72 18, 85 18 C 98 18, 102 55, 115 55" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/></svg>
      <strong>Multimodal</strong>Varios picos: subgrupos mezclados.
      <span class="accion">Segmentar o usar clústeres / ensamblajes.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><path d="M5 55 L 10 20 L 110 20 L 115 55" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/></svg>
      <strong>Uniforme</strong>Todos los valores igual de probables.
      <span class="accion">Ingeniería de características.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true" fill="currentColor"><rect x="8" y="40" width="12" height="15" opacity="0.5"/><rect x="26" y="22" width="12" height="33" opacity="0.5"/><rect x="44" y="10" width="12" height="45" opacity="0.5"/><rect x="62" y="16" width="12" height="39" opacity="0.5"/><rect x="80" y="34" width="12" height="21" opacity="0.5"/><rect x="98" y="46" width="12" height="9" opacity="0.5"/></svg>
      <strong>Discreta</strong>Valores concretos y separados (nº de llamadas).
      <span class="accion">Valorar agrupar o transformar.</span>
    </div>
  </div>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Cómo se lee un boxplot</div>
  <svg class="svg-ancho" viewBox="0 0 340 130" role="img" aria-label="Boxplot con caja de Q1 a Q3, mediana, bigotes y valores atípicos">
    <text x="150" y="14" text-anchor="middle">Caja: el 50 % central de los datos (IQR)</text>
    <line x1="50" y1="48" x2="250" y2="48" stroke="currentColor" stroke-width="2"/>
    <line x1="50" y1="35" x2="50" y2="61" stroke="currentColor" stroke-width="2"/>
    <line x1="250" y1="35" x2="250" y2="61" stroke="currentColor" stroke-width="2"/>
    <rect x="100" y="28" width="100" height="40" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/>
    <line x1="150" y1="28" x2="150" y2="68" stroke="currentColor" stroke-width="3"/>
    <circle cx="18" cy="48" r="4" fill="#c62828"/>
    <circle cx="285" cy="48" r="4" fill="#c62828"/>
    <circle cx="312" cy="48" r="4" fill="#c62828"/>
    <text x="100" y="84" text-anchor="middle">Q1</text>
    <text x="150" y="84" text-anchor="middle">Mediana</text>
    <text x="200" y="84" text-anchor="middle">Q3</text>
    <text x="50" y="84" text-anchor="middle">Bigote</text>
    <text x="250" y="84" text-anchor="middle">Bigote</text>
    <text x="298" y="72" text-anchor="middle" style="fill:#c62828">Outliers</text>
    <text x="150" y="112" text-anchor="middle">Los bigotes llegan hasta 1,5 × IQR desde la caja;</text>
    <text x="150" y="126" text-anchor="middle">lo que queda fuera se considera atípico</text>
  </svg>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">El coeficiente de correlación va de −1 a 1</div>
  <div class="escala">
    <div class="barra"></div>
    <div class="marcas"><span>−1</span><span>0</span><span>+1</span></div>
    <div class="ejemplos">
      <div><strong>Negativa</strong>Una sube y la otra baja. Ej.: tiempo de espera y satisfacción del cliente.</div>
      <div><strong>Nula</strong>Sin relación aparente. Ej.: número de zapatos y horas de sueño.</div>
      <div><strong>Positiva</strong>Suben juntas. Ej.: horas de deporte y resistencia física.</div>
    </div>
  </div>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Desequilibrio de clases: opciones</div>
  <div class="arbol">
    <div class="rama">
      <div class="rama-cab">En la variable objetivo<small>Una clase domina a las demás</small></div>
      <div class="hoja"><strong>Sobremuestreo</strong>Copias o ejemplos sintéticos de la minoritaria (SMOTE, ADASYN).</div>
      <div class="hoja"><strong>Submuestreo</strong>Quitar registros de la mayoritaria (se pierde información).</div>
      <div class="hoja"><strong>Ajustar el modelo</strong>Pesos para la clase minoritaria y métricas justas: f1-score, balanced accuracy.</div>
    </div>
    <div class="rama">
      <div class="rama-cab">En las características<small>Categorías muy poco frecuentes</small></div>
      <div class="hoja"><strong>Agrupar</strong>Unir las categorías raras en un valor «Otros».</div>
      <div class="hoja"><strong>Codificar con cuidado</strong>Técnicas de codificación que suavicen su peso.</div>
      <div class="hoja"><strong>A veces, no tocar</strong>Si la clase rara es la importante (fraude, errores graves), puede convenir mantenerla.</div>
    </div>
  </div>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Distribución</dt><dd>Cómo se organizan los valores de una variable.</dd>
  <dt>Histograma</dt><dd>Gráfico de barras que cuenta cuántos datos caen en cada rango.</dd>
  <dt>Outlier</dt><dd>Valor atípico, muy alejado del resto de los datos.</dd>
  <dt>IQR</dt><dd>Rango intercuartílico: distancia entre Q1 y Q3, donde está el 50 % central de los datos.</dd>
  <dt>Correlación</dt><dd>Medida de cuánto se parecen u oponen dos variables en su comportamiento.</dd>
  <dt>Multicolinealidad</dt><dd>Variables muy correlacionadas entre sí que pueden volver inestable un modelo de regresión.</dd>
  <dt>Desequilibrio</dt><dd>Cuando unas clases o categorías tienen muchos más registros que otras.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Eliminar todos los outliers sin pensar.** Pueden ser casos reales y valiosos; primero comprueba si son errores.
- **Leer una correlación como causa.** Que dos variables suban juntas no significa que una provoque la otra.
- **Usar Pearson con datos muy asimétricos o con atípicos.** Spearman es más fiable en esos casos.
- **Fiarse de la exactitud con clases desequilibradas.** Si el 95 % es de una clase, acertar siempre esa da un 95 % sin aprender nada.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>La variable «ingresos» tiene una cola muy larga hacia la derecha. ¿Qué tipo de distribución es y qué podrías hacer?</summary>
    <div class="respuesta">Es una distribución <strong>sesgada a la derecha</strong>. Se puede aplicar una transformación <strong>logarítmica, raíz cuadrada o Box-Cox</strong> para hacerla más simétrica.</div></details>
  <details><summary>En un boxplot aparecen varios puntos fuera de los bigotes. ¿Los eliminas?</summary>
    <div class="respuesta">No directamente. Primero hay que <strong>comprobar si son errores</strong> (entonces se corrigen o eliminan) o <strong>casos reales</strong> que aportan información. También se pueden usar técnicas robustas como la mediana o transformar los datos.</div></details>
  <details><summary>La productividad sube rápido con la motivación y luego se estabiliza. ¿Pearson o Spearman?</summary>
    <div class="respuesta"><strong>Spearman</strong>, porque la relación no es una línea recta pero sí sigue una tendencia (cuando una sube, la otra también). Pearson la subestimaría.</div></details>
  <details><summary>Quieres detectar fraudes, que son el 1 % de los casos. ¿Debes equilibrar siempre las clases?</summary>
    <div class="respuesta">No siempre. Como la clase minoritaria es justo la que interesa, a veces es mejor <strong>mantener el desequilibrio y usar métricas adecuadas</strong> (f1-score, balanced accuracy). Hay que probar qué funciona mejor.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/DY68-iWHpus">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad2/l3.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad2/cuadernos/U2L22.ipynb">Colab: visualización exploratoria</a>
</div>

## Lección 4. Transformación de datos {#leccion-4}

<div class="ficha-lead">
Los modelos necesitan <strong>números en escalas comparables</strong>. Transformamos los datos para que ninguna variable pese más solo por tener cifras grandes, para corregir distribuciones sesgadas y para convertir las <strong>categorías en números</strong>.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>Magnitud ≠ importancia.</strong> Sin escalar, un salario de 0 a 5000 € pesa mucho más que una altura de 150 a 200 cm, aunque no sea más relevante.</div>
  <div class="idea"><strong>Normalizar vs. estandarizar.</strong> Normalizar lleva los valores a un rango fijo (0–1). Estandarizar los deja con media 0 y dispersión común. «Escalar» engloba ambas.</div>
  <div class="idea"><strong>Codificar es obligatorio</strong> para usar variables categóricas (colores, niveles, tipos de producto) en la mayoría de algoritmos.</div>
  <div class="idea"><strong>Un pipeline encadena los pasos</strong> y los aplica siempre igual y en el mismo orden: proceso reproducible y sin errores manuales.</div>
  <div class="idea"><strong>No siempre hace falta.</strong> Si las distribuciones ya están equilibradas, transformar puede no aportar nada. Comprueba su efecto en la práctica.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">Formas de escalar</div>
  <div class="comparativa">
    <div class="col"><h4>Min-Max</h4><ul><li><strong>Qué hace:</strong> lleva los valores a un rango fijo, normalmente 0–1.</li><li><strong>Cuándo:</strong> variables con distribuciones parecidas que solo difieren en escala.</li></ul></div>
    <div class="col"><h4>Estandarización (Z-score)</h4><ul><li><strong>Qué hace:</strong> media 0 y dispersión uniforme; indica cuánto se aleja cada valor de la media.</li><li><strong>Cuándo:</strong> distribuciones distintas o algoritmos que necesitan medias y varianzas equilibradas.</li></ul></div>
    <div class="col"><h4>Escalado robusto</h4><ul><li><strong>Qué hace:</strong> usa la mediana y el rango central.</li><li><strong>Cuándo:</strong> hay valores extremos que distorsionan los datos.</li></ul></div>
  </div>
  <p class="nota">Para distribuciones muy sesgadas o con valores extremos: <strong>transformación logarítmica</strong> o de <strong>potencia</strong> (raíz cuadrada, Box-Cox).</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Codificar variables categóricas</div>
  <div class="comparativa">
    <div class="col">
      <h4>LabelEncoder</h4>
      <ul><li>Un número por categoría: rojo → 0, azul → 1, verde → 2.</li><li><strong>Cuándo:</strong> el modelo no depende de magnitudes, como los árboles de decisión.</li></ul>
    </div>
    <div class="col">
      <h4>OneHotEncoder</h4>
      <ul><li>Una columna por categoría con 1 o 0. Para «azul»:</li></ul>
      <table class="tabla-mini"><thead><tr><th>rojo</th><th>azul</th><th>verde</th></tr></thead><tbody><tr><td>0</td><td class="si">1</td><td>0</td></tr></tbody></table>
      <ul><li><strong>Cuándo:</strong> categorías sin orden y pocas categorías.</li></ul>
    </div>
    <div class="col">
      <h4>Codificación ordinal</h4>
      <ul><li>Respeta el orden: básico &lt; medio &lt; avanzado.</li><li><strong>Cuándo:</strong> la categoría tiene un orden natural (OrdinalEncoder).</li></ul>
    </div>
  </div>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Secuencia habitual (y lo que automatiza un pipeline)</div>
  <div class="flujo cinco">
    <div class="paso"><span class="num">1</span><strong>Limpiar</strong>Nulos, errores y campos sin valor (IDs)</div>
    <div class="paso"><span class="num">2</span><strong>Outliers</strong>Decidir si ajustarlos o conservarlos</div>
    <div class="paso"><span class="num">3</span><strong>Codificar</strong>Categorías a números</div>
    <div class="paso"><span class="num">4</span><strong>Corregir sesgo</strong>Logaritmo o Box-Cox</div>
    <div class="paso"><span class="num">5</span><strong>Escalar</strong>Normalizar o estandarizar</div>
  </div>
  <p class="nota">El orden exacto depende de los datos y del modelo, y no todos los pasos son siempre necesarios.</p>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Normalizar</dt><dd>Ajustar los valores a un rango fijo, como de 0 a 1.</dd>
  <dt>Estandarizar</dt><dd>Transformar los valores para que tengan media 0 y una dispersión común.</dd>
  <dt>Escalar</dt><dd>Término general para ajustar las proporciones de los datos (incluye las dos anteriores).</dd>
  <dt>Codificar</dt><dd>Convertir valores de texto o categorías en números.</dd>
  <dt>Box-Cox</dt><dd>Transformación de potencia que hace más simétrica una distribución sesgada.</dd>
  <dt>Pipeline</dt><dd>Cadena de pasos de transformación (y modelo) que se aplica siempre igual.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **No escalar antes de usar redes neuronales, clustering o regresión.** El modelo confunde magnitud con importancia.
- **Usar LabelEncoder en categorías sin orden con un modelo que interpreta números.** El modelo supondría que verde (2) es «mayor» que rojo (0).
- **Repetir los pasos a mano cada vez.** Es fácil equivocarse o cambiar el orden; un pipeline lo evita.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>Tienes la duración de llamadas (1–20 min) y la factura mensual (10–500 €). ¿Por qué escalar?</summary>
    <div class="respuesta">Porque sin escalar la <strong>factura dominaría</strong> solo por tener cifras más grandes. Al escalar, las dos variables aportan de forma equilibrada.</div></details>
  <details><summary>Tus datos tienen valores extremos que no quieres eliminar. ¿Qué escalado elegirías?</summary>
    <div class="respuesta">El <strong>escalado robusto</strong>, que usa la mediana y el rango central, y por eso los valores extremos influyen mucho menos.</div></details>
  <details><summary>La variable «ciudad» tiene cuatro valores sin ningún orden y usarás una regresión. ¿Qué codificación aplicarías?</summary>
    <div class="respuesta"><strong>OneHotEncoder</strong>: crea una columna por ciudad y evita que el modelo suponga un orden o distancias que no existen.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/y8ARD16JLLc">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad2/l4.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad2/cuadernos/U2L23.ipynb">Colab: transformación de datos</a>
</div>

## Lección 5. Selección y reducción de características {#leccion-5}

<div class="ficha-lead">
No todas las variables ayudan: algunas solo añaden <strong>ruido</strong>. Seleccionar las relevantes y <strong>reducir dimensiones</strong> hace que el modelo sea más preciso, más rápido y más fácil de interpretar.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>Más variables no es mejor.</strong> Las irrelevantes confunden al modelo, alargan el entrenamiento y favorecen el sobreajuste.</div>
  <div class="idea"><strong>Filtrado:</strong> evalúa cada variable por separado frente al objetivo (Pearson, Spearman, chi-cuadrado) y descarta las que no aportan.</div>
  <div class="idea"><strong>PCA</strong> crea nuevas variables, los <em>componentes principales</em>, que combinan las originales y recogen la mayor variabilidad posible.</div>
  <div class="idea"><strong>Los componentes están ordenados.</strong> El primero explica más varianza que el segundo, y así sucesivamente: se elige cuántos usar de forma objetiva.</div>
  <div class="idea"><strong>Escala antes de PCA.</strong> Funciona mejor tras un filtrado inicial y con los datos normalizados o estandarizados.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">PCA en una imagen</div>
  <div class="fusion">
    <div class="origen"><span>Altura</span><span>Peso</span><span>Longitud de pierna</span></div>
    <div class="flecha-grande">→</div>
    <div class="destino">Componente 1<br><small>«tamaño corporal»</small></div>
  </div>
  <p class="nota">Tres variables muy relacionadas se resumen en un solo componente que conserva casi toda su información: de 3 dimensiones a 1.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Varianza explicada por cada componente (ejemplo)</div>
  <div class="barras">
    <div class="fila"><span>PC1</span><div class="pista"><div class="relleno" style="width:70%"></div></div><span>70 %</span></div>
    <div class="fila"><span>PC2</span><div class="pista"><div class="relleno" style="width:25%"></div></div><span>25 %</span></div>
    <div class="fila tenue"><span>PC3</span><div class="pista"><div class="relleno" style="width:4%"></div></div><span>4 %</span></div>
    <div class="fila tenue"><span>PC4</span><div class="pista"><div class="relleno" style="width:1%"></div></div><span>1 %</span></div>
  </div>
  <p class="nota">Si los dos primeros componentes explican el 95 % de la varianza, podemos quedarnos solo con ellos.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Otras técnicas y cuándo usarlas</div>
  <div class="comparativa">
    <div class="col"><h4>LDA</h4><ul><li>Busca las direcciones que mejor <strong>separan las clases</strong>.</li><li>Problemas de clasificación.</li></ul></div>
    <div class="col"><h4>Autoencoders</h4><ul><li>Redes neuronales que aprenden una <strong>versión comprimida</strong> de los datos.</li><li>Datos complejos, relaciones no lineales.</li></ul></div>
    <div class="col"><h4>t-SNE y UMAP</h4><ul><li>Sobre todo para <strong>visualizar</strong> datos con muchas dimensiones.</li><li>Detectar patrones a simple vista.</li></ul></div>
  </div>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Característica</dt><dd>Cada variable de entrada que usa el modelo.</dd>
  <dt>Dimensionalidad</dt><dd>Número de características de un conjunto de datos.</dd>
  <dt>Filtrado</dt><dd>Seleccionar variables según su relación individual con el objetivo.</dd>
  <dt>Componente principal</dt><dd>Nueva variable que combina linealmente las originales y recoge la máxima variabilidad.</dd>
  <dt>Varianza explicada</dt><dd>Parte de la variabilidad de los datos que recoge cada componente.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Aplicar PCA sin escalar.** Las variables con cifras grandes dominarían los componentes.
- **Quedarse con todos los componentes.** Se pierde la ventaja: elige los que explican la mayor parte de la varianza.
- **Usar t-SNE o UMAP para preparar los datos del modelo.** Están pensados sobre todo para visualizar.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>¿Qué diferencia hay entre el filtrado y el PCA?</summary>
    <div class="respuesta">El <strong>filtrado</strong> conserva o descarta variables originales según su relación con el objetivo. El <strong>PCA</strong> crea variables nuevas (componentes) combinando las originales.</div></details>
  <details><summary>Los tres primeros componentes explican el 96 % de la varianza de 20 variables. ¿Qué ganas usando solo esos tres?</summary>
    <div class="respuesta">Pasas de 20 a 3 dimensiones conservando casi toda la información: <strong>modelo más simple, entrenamiento más rápido y menos riesgo de sobreajuste</strong>.</div></details>
  <details><summary>Tu problema es de clasificación y quieres reducir dimensiones separando bien las clases. ¿Qué técnica encaja mejor?</summary>
    <div class="respuesta"><strong>LDA</strong>, porque busca precisamente las direcciones que mejor separan las clases, no solo las de mayor varianza.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/O_cY8SkGdUI">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad2/l5.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad2/cuadernos/U2L24.ipynb">Colab: PCA</a>
</div>

## Ejemplo completo: el mapa del notebook {#ejemplo-completo}

<div class="ficha-lead">
El notebook de síntesis aplica <strong>todo el preprocesamiento de la unidad</strong> sobre un mismo dataset de clientes. Úsalo como guía para tus propios proyectos.
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Recorrido del ejemplo, por fases</div>
  <div class="arbol cuatro">
    <div class="rama">
      <div class="rama-cab">1 · Cargar y limpiar<small>Lecciones 1 y 2</small></div>
      <div class="hoja">Cargar el CSV</div>
      <div class="hoja">Selección inicial de características</div>
      <div class="hoja">Nulos, valores únicos y duplicados</div>
    </div>
    <div class="rama">
      <div class="rama-cab">2 · Explorar<small>Lección 3</small></div>
      <div class="hoja">Distribuciones</div>
      <div class="hoja">Correlación con la variable objetivo</div>
      <div class="hoja">Equilibrio de clases y outliers</div>
    </div>
    <div class="rama">
      <div class="rama-cab">3 · Preparar<small>Lecciones 4 y 5</small></div>
      <div class="hoja">División en entrenamiento y prueba</div>
      <div class="hoja">Separar columnas por tipo y codificar</div>
      <div class="hoja">Correlaciones, escalado y PCA</div>
    </div>
    <div class="rama">
      <div class="rama-cab">4 · Automatizar<small>Lección 4</small></div>
      <div class="hoja">Pipelines que encadenan todo el proceso de forma reproducible</div>
    </div>
  </div>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/tjLTylLNwxM">▶ Vídeo explicativo</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad2/cuadernos/U2L25.ipynb">Abrir el notebook (Colab)</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad2/csv/datasetU2L2.csv">Archivo de datos (CSV)</a>
</div>
