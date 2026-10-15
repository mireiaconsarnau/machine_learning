---
title: "Unidad 4"
parent: "Resúmenes visuales"
nav_order: 4
---

# Resumen visual · Unidad 4. Aprendizaje no supervisado

[Ir a la unidad completa](../unidad4/unidad4.md){: .btn .btn-outline }

## Lección 1. ¿Qué es el aprendizaje no supervisado? {#leccion-1}

<div class="ficha-lead">
Trabajamos con datos <strong>sin etiquetas</strong>: nadie nos dice a qué grupo pertenece cada elemento. El algoritmo descubre por sí mismo <strong>patrones, grupos y estructuras ocultas</strong> a partir de la proximidad, la forma o la densidad de los datos.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>No hay respuesta correcta para comparar.</strong> Sin etiquetas no se puede medir directamente el error: el sistema organiza la información según las relaciones que detecta.</div>
  <div class="idea"><strong>Tres tareas principales:</strong> agrupación (clustering), detección de anomalías y reducción de dimensiones. Las tres exploran la estructura interna de los datos.</div>
  <div class="idea"><strong>Un buen clúster</strong> tiene <em>alta cohesión</em> (sus elementos se parecen entre sí) y <em>alta separación</em> (se diferencia de los demás grupos).</div>
  <div class="idea"><strong>Similitud = distancia.</strong> Cuanto más cerca están dos puntos, más parecidos se consideran. La métrica elegida (euclidiana, Manhattan…) cambia los grupos que salen.</div>
  <div class="idea"><strong>PCA simplifica.</strong> Convierte muchas variables en pocos componentes independientes que conservan la mayor parte de la varianza (por ejemplo, el 95 %). Exige escalar antes.</div>
  <div class="idea"><strong>Se evalúa con métricas internas</strong> (silueta, Davies-Bouldin, Calinski-Harabasz) cuando no hay etiquetas, y con métricas externas (ARI, V-measure) cuando sí las hay.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">Proceso general del aprendizaje no supervisado</div>
  <div class="flujo cinco">
    <div class="paso"><span class="num">A</span><strong>Preparar</strong>Limpiar errores, duplicados, nulos y atípicos; escalar</div>
    <div class="paso"><span class="num">B</span><strong>Escoger técnica</strong>Agrupar, reducir dimensiones, detectar anomalías…</div>
    <div class="paso"><span class="num">C</span><strong>Ejecutar</strong>El modelo analiza los datos sin supervisión</div>
    <div class="paso"><span class="num">D</span><strong>Analizar</strong>Cohesión y separación de los grupos, o información conservada</div>
    <div class="paso"><span class="num">E</span><strong>Interpretar</strong>Segmentaciones útiles y decisiones prácticas</div>
  </div>
  <p class="nota">Es buena práctica comparar varias técnicas y quedarse con la que ofrece mejores resultados con tus datos.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">¿Qué es un clúster y cómo se mide la similitud?</div>
  <svg class="svg-ancho" viewBox="0 0 340 150" role="img" aria-label="Dos grupos de puntos compactos y separados entre sí, y un punto aislado que es una anomalía">
    <circle cx="90" cy="67" r="34" fill="currentColor" fill-opacity="0.08" stroke="currentColor" stroke-dasharray="4 3"/>
    <circle cx="250" cy="66" r="34" fill="currentColor" fill-opacity="0.08" stroke="currentColor" stroke-dasharray="4 3"/>
    <g fill="currentColor">
      <circle cx="70" cy="60" r="4"/><circle cx="85" cy="50" r="4"/><circle cx="100" cy="62" r="4"/><circle cx="78" cy="80" r="4"/><circle cx="95" cy="85" r="4"/><circle cx="110" cy="75" r="4"/><circle cx="88" cy="68" r="4"/>
      <circle cx="230" cy="55" r="4"/><circle cx="248" cy="48" r="4"/><circle cx="262" cy="62" r="4"/><circle cx="240" cy="78" r="4"/><circle cx="258" cy="84" r="4"/><circle cx="270" cy="72" r="4"/><circle cx="250" cy="66" r="4"/>
    </g>
    <line x1="126" y1="67" x2="214" y2="66" stroke="#c62828" stroke-width="2" stroke-dasharray="5 3"/>
    <text x="170" y="58" text-anchor="middle" style="fill:#c62828">Separación</text>
    <text x="90" y="118" text-anchor="middle">Cohesión alta</text>
    <text x="250" y="118" text-anchor="middle">Cohesión alta</text>
    <circle cx="170" cy="128" r="4.5" fill="#c62828"/>
    <text x="180" y="132" style="fill:#c62828">Anomalía (no encaja)</text>
  </svg>
  <div class="mini-graficos">
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><line x1="20" y1="50" x2="100" y2="12" stroke="currentColor" stroke-width="2"/><circle cx="20" cy="50" r="4" fill="currentColor"/><circle cx="100" cy="12" r="4" fill="currentColor"/></svg>
      <strong>Euclidiana</strong>Distancia en línea recta.
      <span class="accion">La más habitual, con variables normalizadas.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><path d="M20 50 H 47 V 37 H 74 V 24 H 100 V 12" fill="none" stroke="currentColor" stroke-width="2"/><circle cx="20" cy="50" r="4" fill="currentColor"/><circle cx="100" cy="12" r="4" fill="currentColor"/></svg>
      <strong>Manhattan</strong>Suma de diferencias en cada eje.
      <span class="accion">Trayectos solo horizontales y verticales.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><path d="M20 50 H 100 V 12" fill="none" stroke="currentColor" stroke-width="2" stroke-dasharray="4 3"/><line x1="20" y1="50" x2="100" y2="12" stroke="currentColor" stroke-width="2"/><circle cx="20" cy="50" r="4" fill="currentColor"/><circle cx="100" cy="12" r="4" fill="currentColor"/></svg>
      <strong>Minkowski</strong>Generaliza las dos anteriores.
      <span class="accion">Un parámetro ajusta el cálculo.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><g stroke="currentColor" stroke-width="1.5"><rect x="12" y="10" width="16" height="16" fill="currentColor"/><rect x="32" y="10" width="16" height="16" fill="none"/><rect x="52" y="10" width="16" height="16" fill="currentColor"/><rect x="72" y="10" width="16" height="16" fill="currentColor"/><rect x="92" y="10" width="16" height="16" fill="none"/><rect x="12" y="34" width="16" height="16" fill="currentColor"/><rect x="32" y="34" width="16" height="16" fill="currentColor"/><rect x="52" y="34" width="16" height="16" fill="currentColor"/><rect x="72" y="34" width="16" height="16" fill="none"/><rect x="92" y="34" width="16" height="16" fill="none"/></g><line x1="32" y1="56" x2="48" y2="56" stroke="#c62828" stroke-width="3"/><line x1="72" y1="56" x2="88" y2="56" stroke="#c62828" stroke-width="3"/></svg>
      <strong>Hamming</strong>Cuenta las posiciones que difieren.
      <span class="accion">Datos categóricos o binarios.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><ellipse cx="60" cy="30" rx="44" ry="14" transform="rotate(-20 60 30)" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/><circle cx="60" cy="30" r="3" fill="currentColor"/><circle cx="100" cy="46" r="4" fill="#c62828"/></svg>
      <strong>Mahalanobis</strong>Punto frente a un grupo, con media y covarianza.
      <span class="accion">Variables correlacionadas o redundantes.</span>
    </div>
  </div>
  <p class="nota">No hay una métrica que funcione siempre: depende del tipo de datos, de su escala y de las correlaciones entre variables.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Familias de algoritmos de agrupación</div>
  <div class="arbol cuatro">
    <div class="rama">
      <div class="rama-cab">Partición<small>Hay que fijar el nº de grupos</small></div>
      <div class="hoja"><strong>Rígida</strong>Cada punto, en un solo grupo. Ej.: K-means.</div>
      <div class="hoja"><strong>Suave</strong>Probabilidad de pertenencia a cada grupo. Ej.: mezclas gaussianas (GMM).</div>
    </div>
    <div class="rama">
      <div class="rama-cab">Jerárquicos<small>Grupos anidados en un árbol</small></div>
      <div class="hoja"><strong>Aglomerativo</strong>De abajo arriba: se van fusionando grupos.</div>
      <div class="hoja"><strong>Divisivo</strong>De arriba abajo: se va dividiendo un único grupo.</div>
    </div>
    <div class="rama">
      <div class="rama-cab">Densidad<small>Zonas con muchos puntos</small></div>
      <div class="hoja"><strong>DBSCAN</strong>No necesita el nº de grupos, admite formas irregulares y marca el ruido.</div>
    </div>
    <div class="rama">
      <div class="rama-cab">Otros<small>Enfoques específicos</small></div>
      <div class="hoja"><strong>Espectral</strong>Álgebra sobre matrices de similitud.</div>
      <div class="hoja"><strong>Por celdas (grid)</strong>Divide el espacio en regiones.</div>
      <div class="hoja"><strong>Difuso (fuzzy)</strong>Grados de pertenencia a varios grupos.</div>
    </div>
  </div>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">¿Cómo sé si el agrupamiento es bueno?</div>
  <div class="comparativa">
    <div class="col">
      <span class="etiqueta">Lo habitual: sin etiquetas</span>
      <h4>Métricas internas</h4>
      <ul>
        <li><strong>Silueta</strong> (−1 a 1): ↑ mejor. Compara cohesión y separación.</li>
        <li><strong>Davies-Bouldin</strong>: ↓ mejor.</li>
        <li><strong>Calinski-Harabasz</strong>: ↑ mejor, sin límite superior.</li>
        <li><strong>Dunn</strong>: ↑ mejor.</li>
        <li><strong>Inercia</strong>: ↓ mejor; solo sirve para comparar configuraciones.</li>
      </ul>
    </div>
    <div class="col teoria">
      <span class="etiqueta">Si hay clases reales</span>
      <h4>Métricas externas</h4>
      <ul>
        <li><strong>ARI</strong> (−1 a 1): 1 = coincidencia perfecta con las clases.</li>
        <li><strong>Homogeneidad</strong>: cada clúster, de una sola clase.</li>
        <li><strong>Completitud</strong>: cada clase, en un solo clúster.</li>
        <li><strong>V-measure</strong>: media armónica de las dos anteriores.</li>
      </ul>
    </div>
  </div>
  <p class="nota">En los notebooks se usa esta guía para la silueta: por encima de 0,5, clústeres bien definidos; entre 0,3 y 0,5, aceptable. Completa siempre las métricas con una inspección visual.</p>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Aprendizaje no supervisado</dt><dd>Técnicas que descubren patrones en datos sin etiquetas ni respuestas conocidas.</dd>
  <dt>Clúster</dt><dd>Grupo de elementos parecidos entre sí y diferentes de los de otros grupos.</dd>
  <dt>Cohesión / separación</dt><dd>Lo cerca que están los puntos de un mismo grupo / lo lejos que están los grupos entre sí.</dd>
  <dt>Anomalía</dt><dd>Elemento que se aleja mucho del patrón general y no encaja en ningún grupo.</dd>
  <dt>Métrica de distancia</dt><dd>Fórmula que cuantifica lo parecidos que son dos elementos (euclidiana, Manhattan, Hamming…).</dd>
  <dt>Componente principal</dt><dd>Nueva variable de PCA, independiente de las demás, que recoge la máxima varianza posible.</dd>
  <dt>Métrica interna</dt><dd>Evalúa los grupos con sus propias características, sin necesidad de etiquetas.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Buscar la «exactitud» del modelo.** Sin etiquetas no hay aciertos ni errores: se evalúa la calidad de los grupos.
- **Agrupar o aplicar PCA sin escalar.** Las variables con cifras grandes dominan las distancias y la varianza.
- **Usar la distancia euclidiana con cualquier tipo de dato.** Para datos categóricos o binarios encaja mejor Hamming.
- **Incluir la columna con el número de clúster al calcular las métricas o el PCA.** Hay que excluirla (`df.drop(columns=['kmeans_labels'])`): si no, los resultados salen falseados.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>¿Cuál es la diferencia esencial entre el aprendizaje supervisado y el no supervisado?</summary>
    <div class="respuesta">En el supervisado el modelo aprende de ejemplos con <strong>respuesta conocida (etiquetas)</strong> y se puede medir su error. En el no supervisado <strong>no hay etiquetas</strong>: el algoritmo descubre por sí mismo grupos o estructuras.</div></details>
  <details><summary>Un banco quiere localizar operaciones muy distintas del resto sin tenerlas marcadas previamente. ¿Qué tarea es?</summary>
    <div class="respuesta"><strong>Detección de anomalías</strong>: identificar elementos que se alejan significativamente del patrón general y no encajan en los grupos formados.</div></details>
  <details><summary>Tus datos tienen la edad (18–90) y los ingresos anuales (10 000–200 000). ¿Qué pasa si agrupas sin escalar?</summary>
    <div class="respuesta">Las distancias dependerían casi solo de los <strong>ingresos</strong>, por tener cifras mucho mayores. Hay que <strong>escalar</strong> para que ambas variables contribuyan de forma equilibrada.</div></details>
  <details><summary>Obtienes silueta = 0,53 y Davies-Bouldin = 0,68. ¿Es un buen agrupamiento?</summary>
    <div class="respuesta">Sí, razonablemente bueno: la silueta indica que los puntos están más cerca de su clúster que de los demás, y un <strong>Davies-Bouldin bajo</strong> señala grupos compactos y bien separados.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/_FS5azNi1_Y">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad4/l1.pdf">Material teórico (PDF)</a>
</div>

## Lección 2. K-means y agrupamiento jerárquico {#leccion-2}

<div class="ficha-lead">
<strong>K-means</strong> reparte los datos en <strong>K grupos</strong> fijados de antemano, alrededor de sus centroides. El <strong>agrupamiento jerárquico</strong> construye un árbol de grupos (dendrograma) y permite decidir cuántos clústeres formar <strong>después</strong>, cortándolo a la altura deseada.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>K-means es rápido y fácil de interpretar:</strong> cada punto queda asociado al centroide más cercano. Va bien con grupos esféricos de tamaño y densidad parecidos.</div>
  <div class="idea"><strong>Elegir K es clave.</strong> Una K baja mezcla grupos distintos; una K alta parte grupos reales. Se combinan el método del codo, la silueta y el conocimiento del problema.</div>
  <div class="idea"><strong>La inicialización importa.</strong> K-means puede quedarse en una mala solución. K-means++ reparte bien los centroides iniciales y <code>n_init</code> repite el proceso y se queda con la menor inercia.</div>
  <div class="idea"><strong>Jerárquico aglomerativo (AGNES):</strong> cada punto empieza solo y se fusionan los grupos más cercanos hasta tener uno. No hace falta fijar K al principio.</div>
  <div class="idea"><strong>El método de enlace decide qué se fusiona.</strong> Ward da grupos regulares y parecidos; el enlace simple puede crear cadenas alargadas.</div>
  <div class="idea"><strong>Límites del jerárquico:</strong> es costoso con muchos datos, no admite datos nuevos sin repetirlo todo y sus fusiones no se deshacen.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">K-means en cinco fases</div>
  <div class="flujo cinco">
    <div class="paso"><span class="num">1</span><strong>Elegir K</strong>Codo, silueta, conocimiento del dominio</div>
    <div class="paso"><span class="num">2</span><strong>Iniciar centroides</strong>Al azar o, mejor, con K-means++</div>
    <div class="paso"><span class="num">3</span><strong>Asignar</strong>Cada punto, al centroide más cercano</div>
    <div class="paso"><span class="num">4</span><strong>Actualizar</strong>Cada centroide pasa a la media de sus puntos</div>
    <div class="paso"><span class="num">5</span><strong>Repetir</strong>3 y 4 hasta que nada cambie (convergencia)</div>
  </div>
  <p class="nota">K-means busca minimizar la <strong>inercia</strong>: la suma de las distancias al cuadrado de cada punto a su centroide.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">¿Cuántos clústeres? Método del codo y método de la silueta</div>
  <svg class="svg-ancho" viewBox="0 0 340 160" role="img" aria-label="Gráfico del codo: la inercia baja deprisa hasta K igual a 3 y luego casi nada. Gráfico de silueta: el valor máximo está en K igual a 3">
    <text x="22" y="12">Inercia ↓</text>
    <line x1="22" y1="18" x2="22" y2="124" stroke="currentColor"/>
    <line x1="22" y1="124" x2="165" y2="124" stroke="currentColor"/>
    <polyline points="35,22 55,72 75,97 95,105 115,109 135,112 155,114" fill="none" stroke="currentColor" stroke-width="2"/>
    <g fill="currentColor"><circle cx="35" cy="22" r="3"/><circle cx="55" cy="72" r="3"/><circle cx="95" cy="105" r="3"/><circle cx="115" cy="109" r="3"/><circle cx="135" cy="112" r="3"/><circle cx="155" cy="114" r="3"/></g>
    <circle cx="75" cy="97" r="6" fill="none" stroke="#c62828" stroke-width="2"/>
    <circle cx="75" cy="97" r="3" fill="#c62828"/>
    <text x="80" y="88" style="fill:#c62828">Codo</text>
    <text x="35" y="136" text-anchor="middle">1</text><text x="55" y="136" text-anchor="middle">2</text><text x="75" y="136" text-anchor="middle">3</text><text x="95" y="136" text-anchor="middle">4</text><text x="115" y="136" text-anchor="middle">5</text><text x="135" y="136" text-anchor="middle">6</text><text x="155" y="136" text-anchor="middle">7</text>
    <text x="95" y="152" text-anchor="middle">K</text>
    <text x="188" y="12">Silueta media ↑</text>
    <line x1="188" y1="18" x2="188" y2="124" stroke="currentColor"/>
    <line x1="188" y1="124" x2="325" y2="124" stroke="currentColor"/>
    <polyline points="200,55 222,30 244,48 266,62 288,70 310,78" fill="none" stroke="currentColor" stroke-width="2"/>
    <g fill="currentColor"><circle cx="200" cy="55" r="3"/><circle cx="244" cy="48" r="3"/><circle cx="266" cy="62" r="3"/><circle cx="288" cy="70" r="3"/><circle cx="310" cy="78" r="3"/></g>
    <circle cx="222" cy="30" r="6" fill="none" stroke="#c62828" stroke-width="2"/>
    <circle cx="222" cy="30" r="3" fill="#c62828"/>
    <text x="230" y="28" style="fill:#c62828">Máximo</text>
    <text x="200" y="136" text-anchor="middle">2</text><text x="222" y="136" text-anchor="middle">3</text><text x="244" y="136" text-anchor="middle">4</text><text x="266" y="136" text-anchor="middle">5</text><text x="288" y="136" text-anchor="middle">6</text><text x="310" y="136" text-anchor="middle">7</text>
    <text x="255" y="152" text-anchor="middle">K</text>
  </svg>
  <p class="nota">Codo: a partir de ese punto, añadir clústeres apenas reduce la inercia. Silueta: elige la K con el valor medio más alto. Si no coinciden (en el notebook, el codo apunta a 4 y la silueta a 7), decide según prefieras simplicidad o detalle.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">El dendrograma y dónde cortarlo</div>
  <svg class="svg-ancho" viewBox="0 0 340 175" role="img" aria-label="Dendrograma de ocho elementos; una línea de corte horizontal cruza dos ramas verticales y da dos clústeres">
    <text x="6" y="14">Distancia</text>
    <line x1="22" y1="22" x2="22" y2="142" stroke="currentColor" stroke-opacity="0.5"/>
    <g fill="none" stroke="currentColor" stroke-width="2">
      <path d="M40 142 V125 H70 V142"/>
      <path d="M100 142 V120 H130 V142"/>
      <path d="M55 125 V95 H115 V120"/>
      <path d="M190 142 V128 H220 V142"/>
      <path d="M260 142 V118 H300 V142"/>
      <path d="M205 128 V100 H280 V118"/>
      <path d="M85 95 V30 H242 V100"/>
    </g>
    <line x1="22" y1="65" x2="330" y2="65" stroke="#c62828" stroke-width="2" stroke-dasharray="6 4"/>
    <text x="163" y="58" text-anchor="middle" style="fill:#c62828">Corte → 2 clústeres</text>
    <circle cx="85" cy="65" r="4" fill="#c62828"/>
    <circle cx="242" cy="65" r="4" fill="#c62828"/>
    <text x="40" y="156" text-anchor="middle">a</text><text x="70" y="156" text-anchor="middle">b</text><text x="100" y="156" text-anchor="middle">c</text><text x="130" y="156" text-anchor="middle">d</text><text x="190" y="156" text-anchor="middle">e</text><text x="220" y="156" text-anchor="middle">f</text><text x="260" y="156" text-anchor="middle">g</text><text x="300" y="156" text-anchor="middle">h</text>
    <text x="170" y="172" text-anchor="middle">Elementos individuales (hojas)</text>
  </svg>
  <p class="nota">Cuanto más alta es una unión, más distintos eran los grupos al fusionarse. Busca el <strong>tramo vertical más largo</strong> que no cruce ninguna línea horizontal y corta ahí: el número de ramas cortadas es el número de clústeres. Cortar más abajo da más grupos y más parecidos por dentro.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Métodos de enlace e hiperparámetros</div>
  <div class="comparativa">
    <div class="col"><h4>Ward</h4><ul><li>Minimiza el aumento de variación interna al fusionar.</li><li>Grupos de tamaño y forma parecidos. Solo con distancia euclidiana.</li></ul></div>
    <div class="col"><h4>Completo</h4><ul><li>Distancia entre los dos puntos <strong>más lejanos</strong>.</li><li>Grupos compactos; evita uniones por un único punto.</li></ul></div>
    <div class="col"><h4>Medio</h4><ul><li>Distancia <strong>media</strong> entre todos los puntos.</li><li>Intermedio y equilibrado; alternativa a Ward con otras distancias.</li></ul></div>
    <div class="col"><h4>Simple</h4><ul><li>Distancia entre los dos puntos <strong>más cercanos</strong>.</li><li>Puede formar cadenas alargadas.</li></ul></div>
  </div>
  <table class="chuleta">
    <thead><tr><th>Hiperparámetro</th><th>Para qué sirve</th></tr></thead>
    <tbody>
      <tr><td><code>KMeans(n_clusters=4)</code></td><td>Número de clústeres K</td></tr>
      <tr><td><code>init='k-means++'</code></td><td>Cómo se eligen los centroides iniciales (o <code>'random'</code>)</td></tr>
      <tr><td><code>n_init</code>, <code>max_iter</code>, <code>tol</code></td><td>Nº de ejecuciones, máximo de iteraciones y umbral de parada</td></tr>
      <tr><td><code>AgglomerativeClustering(linkage='ward')</code></td><td>Método de enlace: <code>'ward'</code>, <code>'complete'</code>, <code>'average'</code>, <code>'single'</code></td></tr>
      <tr><td><code>distance_threshold</code></td><td>Distancia a partir de la cual se deja de fusionar (alternativa a <code>n_clusters</code>)</td></tr>
      <tr><td><code>connectivity</code></td><td>Matriz que restringe qué puntos pueden fusionarse</td></tr>
    </tbody>
  </table>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Centroide</dt><dd>Punto central de un clúster: la media de los puntos que lo forman.</dd>
  <dt>Inercia</dt><dd>Suma de las distancias al cuadrado de cada punto a su centroide. Cuanto menor, más compactos los grupos.</dd>
  <dt>Convergencia</dt><dd>Momento en que las asignaciones y los centroides ya no cambian significativamente.</dd>
  <dt>K-means++</dt><dd>Inicialización que elige centroides iniciales alejados entre sí para mejorar el resultado.</dd>
  <dt>Dendrograma</dt><dd>Árbol que muestra cómo y a qué distancia se fueron uniendo los grupos.</dd>
  <dt>Método de enlace</dt><dd>Forma de medir la distancia entre dos clústeres para decidir cuáles fusionar.</dd>
  <dt>Matriz de conectividad</dt><dd>Restricción que indica qué puntos son vecinos y, por tanto, pueden fusionarse.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Fijar K «a ojo» sin probar.** Compara varias K con el codo y la silueta, y valora si los grupos tienen sentido.
- **Leer la inercia como un valor absoluto.** Siempre baja al aumentar K; solo sirve para comparar configuraciones.
- **Usar K-means con grupos de formas irregulares o tamaños muy distintos.** Forzará particiones poco realistas.
- **Usar Ward con distancias no euclidianas.** En ese caso, mejor el enlace medio.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>En el gráfico del codo, la inercia cae mucho de K = 1 a K = 3 y después apenas baja. ¿Qué K eliges?</summary>
    <div class="respuesta"><strong>K = 3</strong>: es el punto de inflexión. A partir de ahí, añadir clústeres apenas mejora la compacidad y solo complica el modelo.</div></details>
  <details><summary>Ejecutas K-means dos veces y obtienes grupos distintos. ¿Por qué? ¿Cómo lo mitigas?</summary>
    <div class="respuesta">Porque es <strong>sensible a la inicialización</strong> de los centroides. Se mitiga con <strong>K-means++</strong> y con un <code>n_init</code> alto, que repite el algoritmo y se queda con la ejecución de menor inercia.</div></details>
  <details><summary>Si cortas el dendrograma a una altura mayor, ¿obtienes más o menos clústeres?</summary>
    <div class="respuesta"><strong>Menos clústeres</strong>, pero con menor similitud entre los elementos de cada grupo. Cortar más abajo da más grupos y más homogéneos.</div></details>
  <details><summary>Quieres clústeres de tamaño y forma parecidos con distancia euclidiana. ¿Qué método de enlace eliges?</summary>
    <div class="respuesta"><strong>Ward</strong>, porque minimiza el aumento de variación interna en cada fusión y produce grupos regulares.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/5BDQW-Vc5-4">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad4/l2.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad4/cuadernos/U4L21.ipynb">Colab: K-means</a>
  <a class="btn" href="https://youtu.be/eyZ3Htah7HA">Vídeo: ejemplo K-means</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad4/cuadernos/U4L22.ipynb">Colab: AGNES</a>
  <a class="btn" href="https://youtu.be/ampVBnzFQLQ">Vídeo: ejemplo AGNES</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad4/csv/customers.csv">Datos de clientes (CSV)</a>
</div>

## Lección 3. Agrupación por densidad (DBSCAN) {#leccion-3}

<div class="ficha-lead">
<strong>DBSCAN</strong> forma clústeres donde los puntos se concentran y marca como <strong>ruido</strong> los que quedan aislados. No hay que decirle cuántos grupos buscar y detecta <strong>formas irregulares</strong>, pero depende mucho de dos hiperparámetros: <code>eps</code> y <code>min_samples</code>.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>Densidad, no distancia global.</strong> Un clúster es cualquier región con suficiente concentración de puntos, tenga la forma que tenga.</div>
  <div class="idea"><strong>Tres tipos de puntos:</strong> núcleo (con suficientes vecinos), frontera (cerca de un núcleo, pero sin vecinos suficientes) y ruido (fuera de cualquier grupo).</div>
  <div class="idea"><strong>Robusto frente a los atípicos:</strong> los puntos aislados se tratan como ruido desde el principio. No necesita inicializar centroides.</div>
  <div class="idea"><strong>Muy sensible a <code>eps</code> y <code>min_samples</code></strong> y a la escala de los datos: hay que escalar y ajustarlos con cuidado, por ejemplo con el gráfico de k-distancias.</div>
  <div class="idea"><strong>Le cuestan las densidades variables.</strong> Como <code>eps</code> es igual para todo el espacio, puede fallar si unos grupos son muy densos y otros dispersos. Alternativas: HDBSCAN, OPTICS, MeanShift, GMM…</div>
  <div class="idea"><strong>La silueta le hace poca justicia.</strong> Esa métrica supone grupos más bien regulares, así que puede salir baja aunque DBSCAN haya separado bien formas complejas.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">Tipos de puntos en DBSCAN</div>
  <svg class="svg-ancho" viewBox="0 0 340 150" role="img" aria-label="Grupo denso de puntos con un punto núcleo y su radio eps, un punto frontera en el borde y dos puntos de ruido aislados">
    <circle cx="110" cy="75" r="30" fill="currentColor" fill-opacity="0.08" stroke="currentColor" stroke-dasharray="4 3"/>
    <line x1="110" y1="75" x2="140" y2="75" stroke="currentColor"/>
    <text x="125" y="71" text-anchor="middle">eps</text>
    <g fill="currentColor">
      <circle cx="96" cy="64" r="4"/><circle cx="115" cy="58" r="4"/><circle cx="100" cy="88" r="4"/><circle cx="92" cy="77" r="4"/><circle cx="120" cy="92" r="4"/><circle cx="76" cy="62" r="4"/><circle cx="80" cy="90" r="4"/><circle cx="102" cy="45" r="4"/><circle cx="70" cy="76" r="4"/>
    </g>
    <circle cx="110" cy="75" r="6" fill="currentColor"/>
    <circle cx="136" cy="96" r="4.5" fill="none" stroke="currentColor" stroke-width="2"/>
    <circle cx="40" cy="30" r="4.5" fill="#c62828"/>
    <circle cx="165" cy="130" r="4.5" fill="#c62828"/>
    <circle cx="205" cy="36" r="6" fill="currentColor"/>
    <text x="218" y="40">Punto núcleo</text>
    <circle cx="205" cy="62" r="4.5" fill="none" stroke="currentColor" stroke-width="2"/>
    <text x="218" y="66">Punto frontera</text>
    <circle cx="205" cy="88" r="4.5" fill="#c62828"/>
    <text x="218" y="92" style="fill:#c62828">Ruido (etiqueta −1)</text>
    <circle cx="205" cy="114" r="8" fill="none" stroke="currentColor" stroke-dasharray="3 2"/>
    <text x="218" y="118">Radio de vecindad eps</text>
  </svg>
  <p class="nota">Un punto es <strong>núcleo</strong> si tiene al menos <code>min_samples</code> vecinos dentro de <code>eps</code>. Los puntos <strong>frontera</strong> forman parte del clúster, pero no sirven para seguir expandiéndolo.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Cómo trabaja DBSCAN</div>
  <div class="flujo cinco">
    <div class="paso"><span class="num">1</span><strong>Fijar parámetros</strong><code>eps</code> y <code>min_samples</code></div>
    <div class="paso"><span class="num">2</span><strong>Tomar un punto</strong>Si tiene vecinos suficientes, es núcleo y empieza un clúster; si no, se marca como ruido</div>
    <div class="paso"><span class="num">3</span><strong>Expandir</strong>Se añaden sus vecinos; si alguno es núcleo, se sigue creciendo</div>
    <div class="paso"><span class="num">4</span><strong>Nuevo clúster</strong>Se elige otro punto sin visitar y se repite</div>
    <div class="paso"><span class="num">5</span><strong>Terminar</strong>Cada punto queda en un clúster o como ruido</div>
  </div>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Elegir eps con el gráfico de k-distancias</div>
  <svg class="svg-ancho" viewBox="0 0 340 150" role="img" aria-label="Curva de k-distancias ordenadas que sube lentamente y luego bruscamente; eps se toma en el punto de inflexión">
    <text x="44" y="12">Distancia al k-ésimo vecino</text>
    <line x1="40" y1="16" x2="40" y2="120" stroke="currentColor"/>
    <line x1="40" y1="120" x2="320" y2="120" stroke="currentColor"/>
    <path d="M45 114 C 150 110, 230 102, 262 86 S 300 32, 315 18" fill="none" stroke="currentColor" stroke-width="2"/>
    <line x1="40" y1="84" x2="264" y2="84" stroke="#c62828" stroke-width="1.5" stroke-dasharray="5 3"/>
    <circle cx="265" cy="84" r="5" fill="#c62828"/>
    <text x="36" y="88" text-anchor="end" style="fill:#c62828">eps</text>
    <text x="255" y="76" text-anchor="end" style="fill:#c62828">Punto de inflexión</text>
    <text x="180" y="136" text-anchor="middle">Puntos ordenados de menor a mayor distancia</text>
  </svg>
  <p class="nota">1) Calcula para cada punto la distancia a su k-ésimo vecino. 2) Ordénalas y dibújalas. 3) Toma <code>eps</code> donde la curva empieza a subir bruscamente. 4) Usa <code>min_samples</code> = k. Con un <code>min_samples</code> muy bajo entran puntos poco representativos; muy alto, se pierden clústeres válidos.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">K-means, jerárquico y DBSCAN, cara a cara</div>
  <div class="comparativa">
    <div class="col"><h4>K-means</h4><ul><li><strong>Lógica:</strong> centroide más cercano.</li><li><strong>Nº de grupos:</strong> hay que fijarlo (K).</li><li><strong>Ruido:</strong> bastante sensible.</li><li><strong>Coste:</strong> muy rápido.</li><li><strong>Ideal:</strong> grupos esféricos y parecidos.</li></ul></div>
    <div class="col"><h4>Jerárquico</h4><ul><li><strong>Lógica:</strong> árbol de similitudes.</li><li><strong>Nº de grupos:</strong> se decide al cortar el dendrograma.</li><li><strong>Ruido:</strong> depende del enlace.</li><li><strong>Coste:</strong> alto con muchos puntos.</li><li><strong>Ideal:</strong> ver grupos y subgrupos.</li></ul></div>
    <div class="col"><h4>DBSCAN</h4><ul><li><strong>Lógica:</strong> zonas densas.</li><li><strong>Nº de grupos:</strong> lo descubre solo.</li><li><strong>Ruido:</strong> lo detecta y aparta.</li><li><strong>Coste:</strong> casi lineal; eficiente.</li><li><strong>Ideal:</strong> formas irregulares y datos espaciales.</li></ul></div>
  </div>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Densidad</dt><dd>Concentración de puntos en una zona del espacio.</dd>
  <dt>eps (épsilon)</dt><dd>Radio máximo para que dos puntos se consideren vecinos.</dd>
  <dt>min_samples</dt><dd>Número mínimo de puntos dentro de <code>eps</code> para considerar densa una zona.</dd>
  <dt>Punto núcleo</dt><dd>Punto con al menos <code>min_samples</code> vecinos dentro de su radio.</dd>
  <dt>Punto frontera</dt><dd>No tiene vecinos suficientes, pero está en el radio de un núcleo: entra en el clúster.</dd>
  <dt>Ruido</dt><dd>Punto aislado que no pertenece a ningún clúster.</dd>
  <dt>Gráfico de k-distancias</dt><dd>Curva de las distancias al k-ésimo vecino ordenadas; su codo sugiere el valor de <code>eps</code>.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Aplicar DBSCAN sin escalar.** `eps` es una distancia: si las variables tienen escalas distintas, el radio no significa lo mismo en cada una.
- **Probar `eps` al azar.** Uno demasiado pequeño deja casi todo como ruido; uno demasiado grande lo une todo en un solo clúster. Usa el gráfico de k-distancias.
- **Descartar DBSCAN solo por una silueta baja.** Esa métrica supone grupos regulares; mira también la representación gráfica.
- **Usarlo con densidades muy distintas entre grupos.** Prueba alternativas como HDBSCAN u OPTICS.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>Un punto tiene solo dos vecinos dentro de <code>eps</code> (con <code>min_samples</code> = 5), pero uno de ellos es un punto núcleo. ¿Qué tipo de punto es?</summary>
    <div class="respuesta">Un <strong>punto frontera</strong>: no tiene vecinos suficientes para ser núcleo, pero está en el área de influencia de un núcleo, así que pertenece a su clúster.</div></details>
  <details><summary>Tus datos forman dos medias lunas entrelazadas y hay puntos sueltos. ¿K-means o DBSCAN?</summary>
    <div class="respuesta"><strong>DBSCAN</strong>: detecta formas irregulares y aparta los puntos aislados como ruido. K-means forzaría grupos esféricos y metería los atípicos en algún clúster.</div></details>
  <details><summary>¿Cómo puedes estimar un buen valor de <code>eps</code>?</summary>
    <div class="respuesta">Con el <strong>gráfico de k-distancias</strong>: ordenas las distancias de cada punto a su k-ésimo vecino y tomas <code>eps</code> en el punto donde la curva empieza a subir bruscamente. Después, <code>min_samples</code> = k.</div></details>
  <details><summary>En una zona hay grupos muy densos y otros muy dispersos, y DBSCAN no los detecta bien. ¿Por qué?</summary>
    <div class="respuesta">Porque <code>eps</code> y <code>min_samples</code> se aplican <strong>igual en todo el espacio</strong>: un valor que va bien para una zona no sirve para otra. Conviene ajustar con cuidado o usar <strong>HDBSCAN u OPTICS</strong>.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/AyHOSU6ilyM">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad4/l3.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad4/cuadernos/U4L31.ipynb">Colab: comparativa de algoritmos</a>
  <a class="btn" href="https://youtu.be/KAMi1hDdE0E">Vídeo: comparativa</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad4/cuadernos/U4L32.ipynb">Colab: DBSCAN</a>
  <a class="btn" href="https://youtu.be/pUrAkneaeW8">Vídeo: ejemplo DBSCAN</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad4/csv/house_data.csv">Datos de viviendas (CSV)</a>
</div>

## Síntesis de la unidad {#sintesis}

<div class="ficha-lead">
Todo el aprendizaje no supervisado en una página: <strong>las preguntas que debes hacerte, en orden</strong>, y qué algoritmo o métrica usar en cada caso.
</div>

### El camino de un agrupamiento

<div class="diagrama">
  <div class="ruta">
    <div class="etapa">
      <div class="nombre"><span class="num">1</span>Preparar</div>
      <div class="pregunta">¿Están limpios y en escalas comparables?</div>
      <div class="tecnicas">Quitar IDs, nulos y duplicados; codificar; escalar</div>
      <span class="leccion">Lección 1</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">2</span>Escoger</div>
      <div class="pregunta">¿Qué forma tienen los grupos y sé cuántos hay?</div>
      <div class="tecnicas">K-means, jerárquico aglomerativo (AGNES), DBSCAN</div>
      <span class="leccion">Lecciones 2 y 3</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">3</span>Ajustar</div>
      <div class="pregunta">¿Cuántos grupos o qué parámetros?</div>
      <div class="tecnicas">Codo y silueta (K), corte del dendrograma, k-distancias (<code>eps</code>)</div>
      <span class="leccion">Lecciones 2 y 3</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">4</span>Evaluar</div>
      <div class="pregunta">¿Son grupos compactos y separados?</div>
      <div class="tecnicas">Silueta ↑, Davies-Bouldin ↓, Calinski-Harabasz ↑, sin la columna de etiquetas</div>
      <span class="leccion">Lección 1</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">5</span>Visualizar</div>
      <div class="pregunta">¿Se ven bien separados?</div>
      <div class="tecnicas">PCA a 2 dimensiones y diagramas de dispersión</div>
      <span class="leccion">Lección 1</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">6</span>Interpretar</div>
      <div class="pregunta">¿Qué perfil tiene cada grupo y para qué sirve?</div>
      <div class="tecnicas">Describir cada clúster, fusionar los muy parecidos, decidir acciones</div>
      <span class="leccion">Lección 1</span>
    </div>
  </div>
  <p class="nota">En no supervisado no hay división en entrenamiento y prueba: el modelo se ajusta y se evalúa sobre todo el conjunto.</p>
</div>

### Si ves… haz…

<div class="diagrama">
  <table class="decisiones">
    <tbody>
      <tr><td>Variables con escalas muy distintas</td><td>Escalar antes de agrupar o de aplicar PCA</td></tr>
      <tr><td>Grupos más o menos redondos y muchos datos</td><td>K-means con K-means++ y un <code>n_init</code> alto</td></tr>
      <tr><td>No sabes cuántos grupos hay</td><td>Codo + silueta, dendrograma o DBSCAN</td></tr>
      <tr><td>Codo y silueta no coinciden</td><td>Simplicidad: la K menor; más detalle: la que maximiza la silueta</td></tr>
      <tr><td>Quieres ver grupos y subgrupos</td><td>Jerárquico aglomerativo y cortar el dendrograma</td></tr>
      <tr><td>Formas irregulares o alargadas</td><td>DBSCAN</td></tr>
      <tr><td>Puntos aislados que no encajan</td><td>DBSCAN: quedan como ruido (−1)</td></tr>
      <tr><td>Grupos con densidades muy distintas</td><td>HDBSCAN, OPTICS u otra alternativa</td></tr>
      <tr><td>Muchas variables o necesitas ver los grupos</td><td>PCA a 2 componentes para visualizar</td></tr>
      <tr><td>Métricas sospechosamente buenas</td><td>Comprobar que has excluido la columna del nº de clúster</td></tr>
    </tbody>
  </table>
</div>

### Tres reglas de oro

<div class="reglas">
  <div class="regla"><strong>Escala antes de medir distancias</strong>Agrupar es comparar distancias: sin escalar, mandan las variables con cifras grandes.</div>
  <div class="regla"><strong>Ninguna métrica decide sola</strong>Combina codo, silueta, otras métricas, gráficos y conocimiento del problema.</div>
  <div class="regla"><strong>Evalúa sin la etiqueta</strong>Quita la columna del clúster antes de calcular métricas o hacer PCA.</div>
</div>

### Ponlo en práctica

El notebook del ejemplo completo aplica K-means, AGNES y DBSCAN a los hábitos de consumo de unos 10 000 usuarios de una plataforma de streaming. Recuerda la fe de erratas: excluye la columna `kmeans_labels` al calcular las métricas y el PCA.

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/w_rB4BpJ5k4">▶ Vídeo explicativo</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad4/cuadernos/U4L33.ipynb">Abrir el notebook (Colab)</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad4/csv/streaming_usage_dataset.csv">Archivo de datos (CSV)</a>
</div>
