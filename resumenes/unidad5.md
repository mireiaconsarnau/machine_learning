---
title: "Unidad 5"
parent: "Resúmenes visuales"
nav_order: 5
---

# Resumen visual · Unidad 5. Redes neuronales y modelos avanzados

[Ir a la unidad completa](../unidad5/unidad5.md){: .btn .btn-outline }

## Lección 1. Redes neuronales artificiales {#leccion-1}

<div class="ficha-lead">
Una red neuronal combina muchas <strong>neuronas</strong> sencillas organizadas en <strong>capas</strong>. No sigue reglas escritas a mano: <strong>aprende ajustando pesos y sesgos</strong> a partir de los datos, repitiendo un ciclo de predecir, medir el error y corregir.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>Cada neurona hace algo simple:</strong> multiplica cada entrada por su peso, suma todo, añade el sesgo y aplica una función de activación. La potencia está en combinar miles de ellas.</div>
  <div class="idea"><strong>MLP = feedforward y fully connected.</strong> La información va en una sola dirección (entrada → ocultas → salida) y cada neurona se conecta con todas las de la capa siguiente.</div>
  <div class="idea"><strong>Parámetros ≠ hiperparámetros.</strong> Pesos y sesgos los aprende la red; épocas, batch, tasa de aprendizaje o número de capas se fijan antes de entrenar.</div>
  <div class="idea"><strong>La salida depende de la tarea.</strong> Sigmoide para clasificación binaria, softmax para multiclase y salida lineal para regresión, cada una con su función de pérdida.</div>
  <div class="idea"><strong>ReLU en las capas ocultas.</strong> Es rápida y mantiene vivo el gradiente. La sigmoide y la tanh se saturan con valores extremos (gradiente desaparecido).</div>
  <div class="idea"><strong>Vigila la validación.</strong> Si <code>loss</code> baja pero <code>val_loss</code> sube, hay sobreajuste: dropout, early stopping y regularización L2 ayudan a evitarlo.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">De la neurona artificial a la red MLP</div>
  <svg class="svg-ancho" viewBox="0 0 360 165" role="img" aria-label="Neurona artificial: entradas multiplicadas por pesos, suma con sesgo, función de activación y salida">
    <defs><marker id="u5-fl-1" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M0 0 L10 5 L0 10 Z" fill="currentColor"/></marker></defs>
    <g stroke="currentColor" stroke-width="1.5">
      <line x1="42" y1="30" x2="158" y2="68"/>
      <line x1="42" y1="75" x2="158" y2="75"/>
      <line x1="42" y1="120" x2="158" y2="82"/>
    </g>
    <circle cx="30" cy="30" r="12" fill="#fff" stroke="currentColor" stroke-width="2"/>
    <circle cx="30" cy="75" r="12" fill="#fff" stroke="currentColor" stroke-width="2"/>
    <circle cx="30" cy="120" r="12" fill="#fff" stroke="currentColor" stroke-width="2"/>
    <text x="30" y="34" text-anchor="middle">x1</text>
    <text x="30" y="79" text-anchor="middle">x2</text>
    <text x="30" y="124" text-anchor="middle">x3</text>
    <text x="95" y="38" text-anchor="middle">w1</text>
    <text x="100" y="70" text-anchor="middle">w2</text>
    <text x="95" y="119" text-anchor="middle">w3</text>
    <text x="180" y="12" text-anchor="middle" style="fill:#c62828">b (sesgo)</text>
    <line x1="180" y1="17" x2="180" y2="51" stroke="#c62828" stroke-width="1.5"/>
    <circle cx="180" cy="75" r="22" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/>
    <text x="180" y="80" text-anchor="middle" style="font-size:16px">Σ</text>
    <line x1="202" y1="75" x2="238" y2="75" stroke="currentColor" stroke-width="1.5" marker-end="url(#u5-fl-1)"/>
    <rect x="240" y="57" width="46" height="36" rx="6" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/>
    <text x="263" y="79" text-anchor="middle">f( )</text>
    <line x1="286" y1="75" x2="318" y2="75" stroke="currentColor" stroke-width="1.5" marker-end="url(#u5-fl-1)"/>
    <circle cx="332" cy="75" r="12" fill="#fff" stroke="currentColor" stroke-width="2"/>
    <text x="332" y="79" text-anchor="middle">y</text>
    <text x="30" y="145" text-anchor="middle">Entradas</text>
    <text x="180" y="112" text-anchor="middle">Suma ponderada</text>
    <text x="263" y="108" text-anchor="middle">Activación</text>
    <text x="332" y="100" text-anchor="middle">Salida</text>
    <text x="200" y="160" text-anchor="middle">y = f(w1·x1 + w2·x2 + w3·x3 + b)</text>
  </svg>
  <svg class="svg-ancho" viewBox="0 0 360 186" role="img" aria-label="Red MLP con capa de entrada, dos capas ocultas y capa de salida, todas conectadas con todas">
    <text x="40" y="14" text-anchor="middle">Entrada</text>
    <text x="140" y="14" text-anchor="middle">Oculta 1</text>
    <text x="230" y="14" text-anchor="middle">Oculta 2</text>
    <text x="320" y="14" text-anchor="middle">Salida</text>
    <g stroke="currentColor" stroke-width="1" stroke-opacity="0.35">
      <line x1="50" y1="55" x2="130" y2="35"/><line x1="50" y1="55" x2="130" y2="75"/><line x1="50" y1="55" x2="130" y2="115"/><line x1="50" y1="55" x2="130" y2="155"/><line x1="50" y1="95" x2="130" y2="35"/><line x1="50" y1="95" x2="130" y2="75"/><line x1="50" y1="95" x2="130" y2="115"/><line x1="50" y1="95" x2="130" y2="155"/><line x1="50" y1="135" x2="130" y2="35"/><line x1="50" y1="135" x2="130" y2="75"/><line x1="50" y1="135" x2="130" y2="115"/><line x1="50" y1="135" x2="130" y2="155"/>
      <line x1="150" y1="35" x2="220" y2="35"/><line x1="150" y1="35" x2="220" y2="75"/><line x1="150" y1="35" x2="220" y2="115"/><line x1="150" y1="35" x2="220" y2="155"/><line x1="150" y1="75" x2="220" y2="35"/><line x1="150" y1="75" x2="220" y2="75"/><line x1="150" y1="75" x2="220" y2="115"/><line x1="150" y1="75" x2="220" y2="155"/><line x1="150" y1="115" x2="220" y2="35"/><line x1="150" y1="115" x2="220" y2="75"/><line x1="150" y1="115" x2="220" y2="115"/><line x1="150" y1="115" x2="220" y2="155"/><line x1="150" y1="155" x2="220" y2="35"/><line x1="150" y1="155" x2="220" y2="75"/><line x1="150" y1="155" x2="220" y2="115"/><line x1="150" y1="155" x2="220" y2="155"/>
      <line x1="240" y1="35" x2="310" y2="75"/><line x1="240" y1="35" x2="310" y2="115"/><line x1="240" y1="75" x2="310" y2="75"/><line x1="240" y1="75" x2="310" y2="115"/><line x1="240" y1="115" x2="310" y2="75"/><line x1="240" y1="115" x2="310" y2="115"/><line x1="240" y1="155" x2="310" y2="75"/><line x1="240" y1="155" x2="310" y2="115"/>
    </g>
    <g stroke="currentColor" stroke-width="2" fill="#fff">
      <circle cx="40" cy="55" r="10"/><circle cx="40" cy="95" r="10"/><circle cx="40" cy="135" r="10"/>
    </g>
    <g stroke="currentColor" stroke-width="2" fill="currentColor" fill-opacity="0.25">
      <circle cx="140" cy="35" r="10"/><circle cx="140" cy="75" r="10"/><circle cx="140" cy="115" r="10"/><circle cx="140" cy="155" r="10"/>
      <circle cx="230" cy="35" r="10"/><circle cx="230" cy="75" r="10"/><circle cx="230" cy="115" r="10"/><circle cx="230" cy="155" r="10"/>
    </g>
    <g stroke="#c62828" stroke-width="2" fill="#c62828" fill-opacity="0.2">
      <circle cx="320" cy="75" r="10"/><circle cx="320" cy="115" r="10"/>
    </g>
    <text x="180" y="182" text-anchor="middle">Todas conectadas con todas · la información solo va hacia delante</text>
  </svg>
  <p class="nota">La capa de entrada solo transmite los datos; las ocultas los transforman; la de salida da la clase o el valor. Más capas y neuronas = más capacidad, pero también más coste y más riesgo de sobreajuste.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">El ciclo de entrenamiento (se repite muchas veces)</div>
  <div class="flujo cuatro">
    <div class="paso"><span class="num">1</span><strong>Propagación hacia delante</strong>Los datos recorren la red y sale una predicción con los pesos actuales.</div>
    <div class="paso"><span class="num">2</span><strong>Función de pérdida</strong>Compara la predicción con la respuesta correcta y da un número: el error.</div>
    <div class="paso"><span class="num">3</span><strong>Retropropagación</strong>Envía el error hacia atrás y calcula el gradiente de cada peso (regla de la cadena).</div>
    <div class="paso"><span class="num">4</span><strong>Descenso del gradiente</strong>El optimizador (Adam, SGD…) mueve cada peso un paso hacia menos error.</div>
  </div>
  <p class="nota">Como una bola que baja hacia el fondo del valle: la <strong>tasa de aprendizaje</strong> es el tamaño del paso. Si es muy grande se salta el mínimo; si es muy pequeña, el proceso es lentísimo.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Funciones de activación: forma y dónde usarlas</div>
  <div class="mini-graficos">
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><line x1="5" y1="40" x2="115" y2="40" stroke="currentColor" stroke-opacity="0.3"/><line x1="60" y1="5" x2="60" y2="55" stroke="currentColor" stroke-opacity="0.3"/><path d="M5 40 L60 40 L112 8" fill="none" stroke="currentColor" stroke-width="2.5"/></svg>
      <strong>ReLU</strong>Deja pasar los positivos y anula los negativos.
      <span class="accion">Capas ocultas: la más usada.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><line x1="5" y1="8" x2="115" y2="8" stroke="currentColor" stroke-opacity="0.3" stroke-dasharray="3 3"/><line x1="5" y1="52" x2="115" y2="52" stroke="currentColor" stroke-opacity="0.3"/><path d="M5 51 C 40 51, 45 30, 60 30 C 75 30, 80 9, 115 9" fill="none" stroke="currentColor" stroke-width="2.5"/></svg>
      <strong>Sigmoide</strong>Convierte cualquier valor en un número entre 0 y 1.
      <span class="accion">Salida binaria · <code>binary_crossentropy</code>.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><line x1="5" y1="30" x2="115" y2="30" stroke="currentColor" stroke-opacity="0.3"/><line x1="60" y1="5" x2="60" y2="55" stroke="currentColor" stroke-opacity="0.3"/><path d="M5 52 C 45 52, 50 30, 60 30 C 70 30, 75 8, 115 8" fill="none" stroke="currentColor" stroke-width="2.5"/></svg>
      <strong>tanh</strong>Como la sigmoide, pero de −1 a 1 y centrada en cero.
      <span class="accion">Ocultas en redes pequeñas o RNN.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true" fill="currentColor"><rect x="18" y="49" width="20" height="6" opacity="0.5"/><rect x="50" y="10" width="20" height="45"/><rect x="82" y="49" width="20" height="6" opacity="0.5"/><line x1="10" y1="55" x2="110" y2="55" stroke="currentColor" stroke-opacity="0.3"/></svg>
      <strong>Softmax</strong>Probabilidades por clase que suman 1.
      <span class="accion">Salida multiclase · <code>categorical_crossentropy</code>.</span>
    </div>
    <div class="mini">
      <svg viewBox="0 0 120 60" aria-hidden="true"><line x1="5" y1="30" x2="115" y2="30" stroke="currentColor" stroke-opacity="0.3"/><line x1="60" y1="5" x2="60" y2="55" stroke="currentColor" stroke-opacity="0.3"/><path d="M8 55 L112 5" fill="none" stroke="currentColor" stroke-width="2.5"/></svg>
      <strong>Lineal</strong>No transforma: la salida puede tomar cualquier valor.
      <span class="accion">Salida en regresión · MSE o MAE.</span>
    </div>
  </div>
  <p class="nota">Clasificación binaria: <strong>1 neurona</strong> de salida. Multiclase: <strong>una neurona por clase</strong>. Regresión: una neurona por cada valor que se quiera predecir.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Cómo leer las curvas de pérdida por época</div>
  <svg class="svg-ancho" viewBox="0 0 360 150" role="img" aria-label="Tres gráficos de pérdida frente a épocas: aprendizaje correcto, sobreajuste e infraajuste">
    <g stroke="currentColor" stroke-opacity="0.5" stroke-width="1">
      <path d="M15 20 L15 110 L115 110" fill="none"/>
      <path d="M130 20 L130 110 L230 110" fill="none"/>
      <path d="M245 20 L245 110 L345 110" fill="none"/>
    </g>
    <g fill="none" stroke-width="2.5">
      <path d="M15 28 C 40 80, 60 95, 115 100" stroke="currentColor"/>
      <path d="M15 32 C 40 82, 60 90, 115 92" stroke="#c62828" stroke-dasharray="5 3"/>
      <path d="M130 28 C 155 80, 175 98, 230 104" stroke="currentColor"/>
      <path d="M130 32 C 150 80, 165 82, 180 80 S 210 60, 230 48" stroke="#c62828" stroke-dasharray="5 3"/>
      <path d="M245 35 C 270 45, 300 48, 345 50" stroke="currentColor"/>
      <path d="M245 30 C 270 40, 300 43, 345 45" stroke="#c62828" stroke-dasharray="5 3"/>
    </g>
    <line x1="180" y1="22" x2="180" y2="110" stroke="#c62828" stroke-width="1" stroke-dasharray="2 3"/>
    <text x="180" y="16" text-anchor="middle" style="fill:#c62828">parar aquí</text>
    <text x="65" y="128" text-anchor="middle">Aprende bien</text>
    <text x="65" y="142" text-anchor="middle">las dos bajan juntas</text>
    <text x="180" y="128" text-anchor="middle">Sobreajuste</text>
    <text x="180" y="142" text-anchor="middle">val_loss vuelve a subir</text>
    <text x="295" y="128" text-anchor="middle">Infraajuste</text>
    <text x="295" y="142" text-anchor="middle">las dos se quedan altas</text>
  </svg>
  <p class="nota">Línea continua: <code>loss</code> (entrenamiento). Línea roja discontinua: <code>val_loss</code> (validación). Eje horizontal: épocas. Contra el sobreajuste: <strong>dropout</strong> (apagar neuronas al azar), <strong>early stopping</strong> (parar cuando <code>val_loss</code> deja de mejorar) y <strong>L2</strong> (penalizar pesos grandes).</p>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Peso</dt><dd>Número de cada conexión que indica cuánto influye una entrada en una neurona. Lo aprende la red.</dd>
  <dt>Sesgo (bias)</dt><dd>Valor que se suma dentro de la neurona para desplazar el resultado y que pueda activarse aunque las entradas sean débiles.</dd>
  <dt>Función de activación</dt><dd>Transformación no lineal que se aplica tras la suma; permite aprender relaciones complejas.</dd>
  <dt>Función de pérdida</dt><dd>Mide el error entre la predicción y la respuesta correcta y guía el aprendizaje (entropía cruzada, MSE, MAE).</dd>
  <dt>Retropropagación</dt><dd>Envío del error hacia atrás para calcular el gradiente de cada peso.</dd>
  <dt>Época y batch</dt><dd>Época: una pasada completa por los datos de entrenamiento. Batch: ejemplos que se procesan juntos antes de actualizar los pesos.</dd>
  <dt>Tasa de aprendizaje</dt><dd>Tamaño del paso con el que cambian los pesos en cada actualización (habitual: 0,001 o 0,0001).</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Usar sigmoide en las capas ocultas.** Se satura y frena el aprendizaje; en las ocultas, ReLU.
- **Poner softmax o sigmoide en la salida de una regresión sin límites.** La salida debe ser lineal para poder dar cualquier valor.
- **No escalar ni codificar las entradas.** Una MLP necesita datos limpios, con escalas parecidas y categorías en One-Hot.
- **Seguir entrenando cuando `val_loss` ya sube.** La red está memorizando; usa early stopping o regularización.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>¿Qué diferencia hay entre los pesos y la tasa de aprendizaje?</summary>
    <div class="respuesta">Los <strong>pesos son parámetros</strong>: la red los ajusta sola durante el entrenamiento. La <strong>tasa de aprendizaje es un hiperparámetro</strong>: la decides tú antes de entrenar y controla cuánto cambian los pesos en cada paso.</div></details>
  <details><summary>Tienes que clasificar productos en 4 categorías. ¿Cómo será la capa de salida y qué pérdida usarás?</summary>
    <div class="respuesta"><strong>4 neuronas con softmax</strong> (una probabilidad por categoría, que suman 1) y <strong>entropía cruzada categórica</strong>: <code>categorical_crossentropy</code> con etiquetas one-hot o <code>sparse_categorical_crossentropy</code> con etiquetas enteras.</div></details>
  <details><summary>Con 1000 ejemplos, <code>batch_size=100</code> y 20 épocas, ¿cuántas veces se actualizan los pesos?</summary>
    <div class="respuesta">Cada época tiene 1000 / 100 = <strong>10 pasos</strong>, así que en 20 épocas hay <strong>200 actualizaciones</strong>. Con <code>batch_size=10</code> serían 100 pasos por época y 2000 en total.</div></details>
  <details><summary>Tras unas épocas, <code>accuracy</code> sigue subiendo pero <code>val_accuracy</code> baja. ¿Qué pasa y qué harías?</summary>
    <div class="respuesta">Es <strong>sobreajuste</strong>: la red memoriza el entrenamiento y deja de generalizar. Se puede aplicar <strong>early stopping</strong>, <strong>dropout</strong>, <strong>regularización L2</strong> o simplificar la arquitectura.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/LvNclpD5WnU">▶ Vídeo de recapitulación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad5/l1.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad5/cuadernos/U5L11.ipynb">Colab: MLP clasificación</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad3/csv/product_success_prediction_extended.csv">Datos clasificación (CSV)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad5/cuadernos/U5L12.ipynb">Colab: MLP regresión</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad5/csv/drug_effect_time.csv">Datos regresión (CSV)</a>
</div>

## Lección 2. Otras arquitecturas de redes neuronales {#leccion-2}

<div class="ficha-lead">
La MLP trata los datos como una lista plana. Cuando el dato tiene <strong>estructura espacial</strong> (imágenes), <strong>orden temporal</strong> (secuencias) o lo que queremos es <strong>comprimir o generar</strong>, usamos arquitecturas adaptadas: <strong>CNN, RNN/LSTM, autoencoders y GAN</strong>.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>Cada dato, su red.</strong> Adaptar la arquitectura al tipo de dato es meter conocimiento previo en el modelo: aprende antes y mejor.</div>
  <div class="idea"><strong>CNN:</strong> filtros que recorren la imagen y detectan bordes, formas y texturas. Necesitan menos parámetros que una MLP y aprenden solas qué patrones importan.</div>
  <div class="idea"><strong>RNN:</strong> guardan un estado interno (memoria) que pasa de un paso de la secuencia al siguiente. Con secuencias largas sufren el gradiente desaparecido o explosivo.</div>
  <div class="idea"><strong>LSTM:</strong> añaden compuertas de entrada, olvido y salida que deciden qué recordar y qué descartar. Por eso, en la práctica, se suelen preferir a las RNN simples.</div>
  <div class="idea"><strong>Autoencoder:</strong> aprende a copiar su propia entrada pasando por un «cuello de botella». Sirve para comprimir, quitar ruido y detectar anomalías.</div>
  <div class="idea"><strong>GAN:</strong> dos redes compiten. El generador crea datos falsos a partir de ruido y el discriminador intenta descubrirlos, hasta que los falsos parecen reales.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">Qué red elegir según el tipo de dato</div>
  <table class="chuleta">
    <thead><tr><th>Red</th><th>Datos</th><th>Estructura</th><th>Usos habituales</th></tr></thead>
    <tbody>
      <tr><td><strong>MLP</strong></td><td>Tabulares</td><td>Capas densas</td><td>Clasificación y regresión con datos simples</td></tr>
      <tr><td><strong>CNN</strong></td><td>Imágenes, señales</td><td>Convolución + pooling</td><td>Visión artificial, reconocimiento de patrones visuales</td></tr>
      <tr><td><strong>RNN</strong></td><td>Secuencias</td><td>Capas recurrentes</td><td>Texto, series temporales, voz</td></tr>
      <tr><td><strong>LSTM</strong></td><td>Secuencias largas</td><td>Recurrentes con memoria (compuertas)</td><td>Predicción de tendencias, generación de texto</td></tr>
      <tr><td><strong>Autoencoder</strong></td><td>Imágenes, vectores</td><td>Encoder y decoder simétricos</td><td>Compresión, limpieza, anomalías</td></tr>
      <tr><td><strong>VAE</strong></td><td>Imágenes, vectores</td><td>Encoder, decoder y espacio latente</td><td>Generar datos nuevos parecidos</td></tr>
      <tr><td><strong>GAN</strong></td><td>Imágenes, texto, voz</td><td>Generador y discriminador</td><td>Crear contenido nuevo, mejorar la calidad</td></tr>
    </tbody>
  </table>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Estructura típica de una CNN</div>
  <div class="flujo cinco">
    <div class="paso"><span class="num">1</span><strong>Imagen</strong>Cuadrícula de píxeles (p. ej. 28 × 28)</div>
    <div class="paso"><span class="num">2</span><strong>Convolución</strong>Filtros que detectan patrones locales (<code>Conv2D</code>)</div>
    <div class="paso"><span class="num">3</span><strong>Activación</strong>ReLU para añadir no linealidad</div>
    <div class="paso"><span class="num">4</span><strong>Pooling</strong>Reduce el tamaño y conserva lo esencial (<code>MaxPooling2D</code>)</div>
    <div class="paso"><span class="num">5</span><strong>Densas</strong><code>Flatten</code> + <code>Dense</code>: decisión final (softmax)</div>
  </div>
  <p class="nota">Los pasos 2 a 4 se repiten varias veces: cuanto más profunda la red, más complejos son los patrones que detecta.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Autoencoder: comprimir y reconstruir</div>
  <svg class="svg-ancho" viewBox="0 0 360 145" role="img" aria-label="Autoencoder en forma de embudo: el encoder comprime 784 valores a 32 y el decoder los reconstruye a 784">
    <polygon points="20,20 140,50 140,90 20,120" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/>
    <rect x="150" y="50" width="60" height="40" rx="4" fill="#c62828" fill-opacity="0.12" stroke="#c62828" stroke-width="2"/>
    <polygon points="220,50 340,20 340,120 220,90" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/>
    <text x="75" y="74" text-anchor="middle">Encoder</text>
    <text x="180" y="74" text-anchor="middle" style="fill:#c62828">Latente</text>
    <text x="285" y="74" text-anchor="middle">Decoder</text>
    <text x="20" y="13" text-anchor="middle">784</text>
    <text x="180" y="43" text-anchor="middle" style="fill:#c62828">32</text>
    <text x="340" y="13" text-anchor="middle">784</text>
    <text x="75" y="138" text-anchor="middle">Entrada (p. ej. con ruido)</text>
    <text x="285" y="138" text-anchor="middle">Salida reconstruida</text>
  </svg>
  <p class="nota">Se entrena para que la salida se parezca lo más posible a la entrada (pérdida: normalmente MSE). Si reconstruye mal un dato, ese dato es «raro»: así se detectan <strong>anomalías</strong>. Variantes: <strong>convolucional</strong> (limpiar o comprimir imágenes) y <strong>VAE</strong> (generar datos nuevos).</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">GAN: dos redes que compiten</div>
  <svg class="svg-ancho" viewBox="0 0 360 145" role="img" aria-label="GAN: el generador transforma ruido en datos falsos; el discriminador recibe falsos y reales y decide si son reales">
    <defs><marker id="u5-fl-2" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M0 0 L10 5 L0 10 Z" fill="currentColor"/></marker></defs>
    <rect x="10" y="20" width="60" height="30" rx="5" fill="#fff" stroke="currentColor" stroke-width="2"/>
    <text x="40" y="39" text-anchor="middle">Ruido</text>
    <line x1="70" y1="35" x2="93" y2="35" stroke="currentColor" stroke-width="1.5" marker-end="url(#u5-fl-2)"/>
    <rect x="95" y="20" width="90" height="30" rx="5" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/>
    <text x="140" y="39" text-anchor="middle">Generador</text>
    <polyline points="185,35 245,35 245,58" fill="none" stroke="currentColor" stroke-width="1.5" marker-end="url(#u5-fl-2)"/>
    <text x="215" y="29" text-anchor="middle" style="fill:#c62828">falso</text>
    <rect x="10" y="105" width="90" height="30" rx="5" fill="#fff" stroke="currentColor" stroke-width="2"/>
    <text x="55" y="124" text-anchor="middle">Datos reales</text>
    <polyline points="100,120 245,120 245,96" fill="none" stroke="currentColor" stroke-width="1.5" marker-end="url(#u5-fl-2)"/>
    <text x="170" y="114" text-anchor="middle">real</text>
    <rect x="200" y="60" width="90" height="34" rx="5" fill="currentColor" fill-opacity="0.15" stroke="currentColor" stroke-width="2"/>
    <text x="245" y="81" text-anchor="middle">Discriminador</text>
    <line x1="290" y1="77" x2="310" y2="77" stroke="currentColor" stroke-width="1.5" marker-end="url(#u5-fl-2)"/>
    <text x="333" y="74" text-anchor="middle">1 real</text>
    <text x="333" y="88" text-anchor="middle">0 falso</text>
  </svg>
  <p class="nota">El generador intenta <strong>engañar</strong> al discriminador; el discriminador intenta <strong>no equivocarse</strong>. Se entrenan a la vez hasta el equilibrio: los datos generados ya no se distinguen de los reales.</p>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Filtro (kernel)</dt><dd>Pequeña ventana que se desliza sobre la imagen para detectar un patrón local, como una línea o una esquina.</dd>
  <dt>Pooling</dt><dd>Capa que reduce la resolución agrupando regiones vecinas; el max pooling conserva el valor más alto.</dd>
  <dt>Estado interno</dt><dd>Memoria de una red recurrente que se actualiza en cada paso de la secuencia.</dd>
  <dt>Compuertas</dt><dd>Mecanismos de la LSTM (entrada, olvido, salida) que controlan qué información se guarda o se olvida.</dd>
  <dt>Representación latente</dt><dd>Versión comprimida del dato que produce el encoder de un autoencoder.</dd>
  <dt>Generador / discriminador</dt><dd>Las dos redes de una GAN: una crea datos falsos y la otra decide si son reales o falsos.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Usar una MLP para imágenes o secuencias.** Funciona, pero desaprovecha la estructura del dato y necesita muchísimos parámetros.
- **Confundir un autoencoder convolucional con una CNN.** Comparten capas, pero la CNN clasifica (acaba en una etiqueta) y el autoencoder reconstruye su propia entrada.
- **Usar una RNN simple con secuencias largas.** Olvida lo lejano por el gradiente desaparecido; una LSTM lo resuelve mejor.
- **Usar un VAE para limpiar imágenes.** Para limpiar o comprimir, mejor un autoencoder convolucional; el VAE está pensado para generar.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>Quieres predecir el precio de mañana a partir de los precios de los días anteriores. ¿Qué red elegirías?</summary>
    <div class="respuesta">Una <strong>LSTM</strong>: el orden de los datos importa y hay que recordar el pasado. La salida sería <strong>una neurona lineal</strong> con pérdida MSE, porque es una regresión.</div></details>
  <details><summary>¿Por qué una CNN necesita menos parámetros que una MLP para clasificar imágenes?</summary>
    <div class="respuesta">Porque sus <strong>filtros se aplican localmente</strong> y se reutilizan en toda la imagen, en lugar de conectar cada píxel con todas las neuronas de la siguiente capa.</div></details>
  <details><summary>Has entrenado un autoencoder con transacciones normales. Una nueva transacción se reconstruye con un error muy alto. ¿Qué indica?</summary>
    <div class="respuesta">Que probablemente es una <strong>anomalía</strong>: el modelo solo sabe reconstruir bien los datos parecidos a los que vio, así que un error de reconstrucción alto señala un caso atípico.</div></details>
  <details><summary>En una GAN, ¿cuándo se dice que se ha alcanzado el equilibrio?</summary>
    <div class="respuesta">Cuando el generador produce datos tan realistas que el <strong>discriminador ya no puede diferenciarlos</strong> con claridad de los reales.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/RVDHBUZWnnE">▶ Vídeo de recapitulación: autoencoders</a>
  <a class="btn btn-primary" href="https://youtu.be/hJd_i8V5uW8">▶ Vídeo de recapitulación: RNN y LSTM</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad5/l2.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad5/cuadernos/U5L21.ipynb">Colab: autoencoder convolucional</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad5/csv/notMNIST_small.tar.gz">Datos autoencoder (TAR.GZ)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad5/cuadernos/U5L22.ipynb">Colab: LSTM series temporales</a>
</div>

## Lección 3. Transfer learning y metaheurísticas {#leccion-3}

<div class="ficha-lead">
No siempre hay que empezar de cero: con <strong>transfer learning</strong> reutilizamos una red ya entrenada y la adaptamos a una tarea nueva con menos datos y menos tiempo. Y cuando hay que buscar la mejor combinación entre muchísimas posibles, los <strong>algoritmos genéticos</strong> exploran soluciones imitando la evolución.
</div>

### Ideas clave

<div class="ideas">
  <div class="idea"><strong>Reutilizar conocimiento.</strong> Se parte de un modelo entrenado con muchos datos (VGG, ResNet o MobileNet con ImageNet) y se cambia su parte final por capas adaptadas al nuevo problema.</div>
  <div class="idea"><strong>Fase 1, congelación:</strong> los pesos del modelo base no se tocan y solo se entrenan las capas nuevas. Menos tiempo y menos riesgo de sobreajuste.</div>
  <div class="idea"><strong>Fase 2, fine-tuning:</strong> se descongelan algunas capas profundas y se afinan con una tasa de aprendizaje muy baja, para no caer en la «catástrofe del olvido».</div>
  <div class="idea"><strong>Las primeras capas son genéricas.</strong> En una CNN detectan bordes y texturas útiles para casi cualquier imagen; las últimas son más específicas de la tarea original.</div>
  <div class="idea"><strong>Algoritmos genéticos:</strong> una población de soluciones mejora generación tras generación con selección, cruce y mutación. No necesitan derivadas.</div>
  <div class="idea"><strong>No son ML, pero ayudan al ML:</strong> no aprenden de datos, pero sirven para ajustar hiperparámetros o seleccionar variables. No sustituyen al preprocesado.</div>
</div>

### Esquema

<div class="diagrama">
  <div class="diagrama-titulo">Transfer learning en dos fases</div>
  <svg class="svg-ancho" viewBox="0 0 360 140" role="img" aria-label="Fase 1: todas las capas del modelo base congeladas y solo se entrenan las capas nuevas. Fase 2: se descongelan las últimas capas del modelo base">
    <text x="10" y="14">Fase 1 · congelación</text>
    <g stroke="#9aa5b1" stroke-width="1.5" fill="#9aa5b1" fill-opacity="0.35">
      <rect x="10" y="20" width="36" height="28" rx="4"/><rect x="52" y="20" width="36" height="28" rx="4"/><rect x="94" y="20" width="36" height="28" rx="4"/><rect x="136" y="20" width="36" height="28" rx="4"/><rect x="178" y="20" width="36" height="28" rx="4"/>
    </g>
    <g stroke="#c62828" stroke-width="2" fill="#c62828" fill-opacity="0.2">
      <rect x="250" y="20" width="40" height="28" rx="4"/><rect x="296" y="20" width="40" height="28" rx="4"/>
    </g>
    <text x="232" y="38" text-anchor="middle">+</text>
    <text x="10" y="74">Fase 2 · fine-tuning (tasa de aprendizaje muy baja)</text>
    <g stroke="#9aa5b1" stroke-width="1.5" fill="#9aa5b1" fill-opacity="0.35">
      <rect x="10" y="80" width="36" height="28" rx="4"/><rect x="52" y="80" width="36" height="28" rx="4"/><rect x="94" y="80" width="36" height="28" rx="4"/>
    </g>
    <g stroke="#c62828" stroke-width="2" fill="#c62828" fill-opacity="0.2">
      <rect x="136" y="80" width="36" height="28" rx="4"/><rect x="178" y="80" width="36" height="28" rx="4"/>
      <rect x="250" y="80" width="40" height="28" rx="4"/><rect x="296" y="80" width="40" height="28" rx="4"/>
    </g>
    <text x="232" y="98" text-anchor="middle">+</text>
    <text x="112" y="128" text-anchor="middle">Modelo base preentrenado</text>
    <text x="293" y="128" text-anchor="middle">Capas nuevas</text>
  </svg>
  <p class="nota">Gris: capas congeladas (sus pesos no cambian). Rojo: capas que se entrenan. Las capas iniciales, que detectan patrones genéricos, se suelen dejar congeladas.</p>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">¿Cuántas capas congelar?</div>
  <div class="arbol cuatro">
    <div class="rama">
      <div class="rama-cab">Todas<small>Solo se entrena la capa final nueva</small></div>
      <div class="hoja"><strong>Cuándo</strong>Pocos datos y muy parecidos a los originales.</div>
      <div class="hoja"><strong>Ejemplo</strong>De perros y gatos a otros animales domésticos.</div>
    </div>
    <div class="rama">
      <div class="rama-cab">Todas menos la última<small>Se ajusta un poco el final</small></div>
      <div class="hoja"><strong>Cuándo</strong>Tarea parecida, pero no idéntica.</div>
      <div class="hoja"><strong>Ejemplo</strong>De 10 tipos de flores a 5 especies de árboles.</div>
    </div>
    <div class="rama">
      <div class="rama-cab">Solo las iniciales<small>Se reentrenan las últimas</small></div>
      <div class="hoja"><strong>Cuándo</strong>Más datos o diferencias importantes.</div>
      <div class="hoja"><strong>Ejemplo</strong>De fotos de ImageNet a radiografías.</div>
    </div>
    <div class="rama">
      <div class="rama-cab">Ninguna<small>Se entrena todo el modelo</small></div>
      <div class="hoja"><strong>Cuándo</strong>Muchos datos y bastante diferentes.</div>
      <div class="hoja"><strong>Ojo</strong>Partiendo de los pesos preentrenados y con tasa de aprendizaje muy baja.</div>
    </div>
  </div>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Las piezas de un algoritmo genético (ejemplo: descubrir una contraseña)</div>
  <div class="nido">
    <div class="nido-nombre">Población</div>
    <div class="nido-desc">Conjunto de soluciones candidatas que compiten en cada generación: muchas cadenas generadas al azar.</div>
    <div class="nido">
      <div class="nido-nombre">Cromosoma (individuo)</div>
      <div class="nido-desc">Una solución posible: una cadena del mismo tamaño que la contraseña. Su <strong>fitness</strong> mide cuánto se parece a la real.</div>
      <div class="nido">
        <div class="nido-nombre">Gen</div>
        <div class="nido-desc" style="margin-bottom:0">La unidad mínima: cada carácter (letra, número o símbolo) de la cadena.</div>
      </div>
    </div>
  </div>
</div>

<div class="diagrama">
  <div class="diagrama-titulo">Fases de un algoritmo genético (se repiten en cada generación)</div>
  <div class="flujo">
    <div class="paso"><span class="num">1</span><strong>Inicialización</strong>Población inicial aleatoria y diversa.</div>
    <div class="paso"><span class="num">2</span><strong>Evaluación</strong>Se calcula el fitness de cada individuo.</div>
    <div class="paso"><span class="num">3</span><strong>Selección</strong>Los mejores tienen más opciones: ruleta, torneo, ranking (+ elitismo).</div>
    <div class="paso"><span class="num">4</span><strong>Cruce</strong>Se mezclan los genes de dos progenitores.</div>
    <div class="paso"><span class="num">5</span><strong>Mutación</strong>Cambios aleatorios, con baja probabilidad, para ganar diversidad.</div>
    <div class="paso"><span class="num">6</span><strong>Reemplazo</strong>La nueva generación sustituye a la anterior (a veces se guarda el mejor).</div>
  </div>
  <p class="nota">Se para al llegar al máximo de generaciones o al encontrar una solución suficientemente buena.</p>
</div>

### Vocabulario imprescindible

<dl class="glosario">
  <dt>Transfer learning</dt><dd>Reutilizar un modelo entrenado en una tarea para resolver otra nueva.</dd>
  <dt>Congelar capas</dt><dd>Impedir que sus pesos se actualicen durante el nuevo entrenamiento.</dd>
  <dt>Fine-tuning</dt><dd>Ajuste fino: descongelar algunas capas del modelo base y reentrenarlas con una tasa de aprendizaje baja.</dd>
  <dt>Catástrofe del olvido</dt><dd>Cuando el modelo sobrescribe lo aprendido inicialmente y pierde la ventaja del preentrenamiento.</dd>
  <dt>Metaheurística</dt><dd>Técnica de búsqueda que explora espacios de soluciones enormes sin probarlas todas.</dd>
  <dt>Fitness</dt><dd>Función de aptitud que puntúa lo buena que es una solución; a más fitness, más opciones de reproducirse.</dd>
  <dt>Óptimo local</dt><dd>Solución parcial que parece la mejor en su zona, pero no lo es globalmente; la mutación y el cruce ayudan a escapar de ella.</dd>
</dl>

### Errores típicos

<div class="ojo" markdown="1">
- **Hacer fine-tuning con una tasa de aprendizaje normal.** Se destruye el conocimiento previo; hay que usar una tasa muy baja.
- **Descongelar todo el modelo con pocos datos.** Aumenta mucho el riesgo de sobreajuste; empieza entrenando solo las capas nuevas.
- **Pensar que el algoritmo genético prepara los datos.** El escalado y la codificación se hacen antes, igual que con cualquier modelo.
- **Decir que los algoritmos genéticos son aprendizaje automático.** No aprenden de datos ni construyen modelos predictivos; optimizan decisiones.
</div>

### Comprueba si lo has entendido

<div class="autoeval">
  <details><summary>Tienes pocas fotos de razas de perro y una CNN preentrenada con ImageNet. ¿Qué estrategia aplicarías primero?</summary>
    <div class="respuesta"><strong>Congelar todo el modelo base</strong> y entrenar solo las capas nuevas añadidas al final. Si el resultado no basta, hacer <strong>fine-tuning</strong> descongelando algunas capas profundas con tasa de aprendizaje baja.</div></details>
  <details><summary>¿Por qué se suelen mantener congeladas las primeras capas de una CNN?</summary>
    <div class="respuesta">Porque aprenden <strong>patrones muy genéricos</strong> (líneas, bordes, texturas) que sirven para casi cualquier tarea con imágenes.</div></details>
  <details><summary>¿Para qué sirve la mutación en un algoritmo genético?</summary>
    <div class="respuesta">Introduce <strong>diversidad</strong> y evita que el algoritmo se estanque en soluciones mediocres, permitiéndole <strong>escapar de óptimos locales</strong>.</div></details>
  <details><summary>¿Qué ventaja tiene un algoritmo genético frente a grid search para buscar hiperparámetros?</summary>
    <div class="respuesta">No prueba todas las combinaciones fijas: <strong>adapta la búsqueda</strong> generación tras generación según la calidad de las soluciones anteriores, y no necesita derivadas ni conocer la fórmula del problema.</div></details>
</div>

<div class="recursos">
  <a class="btn btn-primary" href="https://youtu.be/wkovhrD2_OI">▶ Vídeo de recapitulación: transfer learning</a>
  <a class="btn btn-primary" href="https://youtu.be/qjxRbiU5vWI">▶ Vídeo de recapitulación: algoritmos genéticos</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad5/l3.pdf">Material teórico (PDF)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad5/cuadernos/U5L31.ipynb">Colab: transfer learning con CNN</a>
  <a class="btn" href="https://github.com/mireiaconsarnau/machine_learning/raw/main/unidad5/csv/datos_U5L31.zip">Datos transfer learning (ZIP)</a>
  <a class="btn" href="https://colab.research.google.com/github/mireiaconsarnau/machine_learning/blob/main/unidad5/cuadernos/U5L32.ipynb">Colab: algoritmo genético</a>
</div>

## Síntesis de la unidad {#sintesis}

<div class="ficha-lead">
Toda la unidad en una página: <strong>las decisiones que tomas al construir una red neuronal</strong>, en orden, y qué hacer según lo que veas durante el entrenamiento.
</div>

### El camino de una red neuronal

<div class="diagrama">
  <div class="ruta">
    <div class="etapa">
      <div class="nombre"><span class="num">1</span>Elegir la red</div>
      <div class="pregunta">¿Qué tipo de dato tengo?</div>
      <div class="tecnicas">Tabla → MLP · imágenes → CNN · secuencias → LSTM · comprimir → autoencoder · generar → GAN o VAE</div>
      <span class="leccion">Lección 2</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">2</span>Preparar</div>
      <div class="pregunta">¿Llegan los datos limpios y en la misma escala?</div>
      <div class="tecnicas"><code>StandardScaler</code> o <code>MinMaxScaler</code>, One-Hot, nulos y desequilibrio</div>
      <span class="leccion">Lección 1</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">3</span>Diseñar</div>
      <div class="pregunta">¿Cuántas capas y qué salida?</div>
      <div class="tecnicas">ReLU en ocultas; sigmoide, softmax o lineal en la salida con su pérdida; empezar con una red modesta</div>
      <span class="leccion">Lección 1</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">4</span>Entrenar</div>
      <div class="pregunta">¿Cómo aprende?</div>
      <div class="tecnicas">Épocas, batch, tasa de aprendizaje y optimizador (Adam por defecto)</div>
      <span class="leccion">Lección 1</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">5</span>Vigilar</div>
      <div class="pregunta">¿Generaliza o memoriza?</div>
      <div class="tecnicas">Curvas de <code>loss</code> y <code>val_loss</code>; dropout, early stopping, L2</div>
      <span class="leccion">Lección 1</span>
    </div>
    <div class="etapa">
      <div class="nombre"><span class="num">6</span>Reutilizar y optimizar</div>
      <div class="pregunta">¿Puedo partir de algo hecho o buscar mejor?</div>
      <div class="tecnicas">Transfer learning (congelación + fine-tuning), algoritmos genéticos para hiperparámetros o variables</div>
      <span class="leccion">Lección 3</span>
    </div>
  </div>
  <p class="nota">Es un orden orientativo: en la práctica se prueban configuraciones y se vuelve atrás según los resultados en validación.</p>
</div>

### Si ves… haz…

<div class="diagrama">
  <table class="decisiones">
    <tbody>
      <tr><td>Datos en filas y columnas</td><td>MLP con entradas escaladas y categorías en One-Hot</td></tr>
      <tr><td>Imágenes</td><td>CNN; si tienes pocas, transfer learning con una red preentrenada</td></tr>
      <tr><td>Series temporales o texto</td><td>LSTM (mejor que una RNN simple con secuencias largas)</td></tr>
      <tr><td>Datos con ruido o casos raros que detectar</td><td>Autoencoder: limpiar ruido o medir el error de reconstrucción</td></tr>
      <tr><td>Hay que crear datos nuevos</td><td>GAN o VAE</td></tr>
      <tr><td>Clasificación</td><td>Binaria: 1 neurona sigmoide + <code>binary_crossentropy</code>. Multiclase: softmax + <code>categorical_crossentropy</code></td></tr>
      <tr><td>Hay que predecir un número</td><td>Salida lineal + MSE (o MAE si hay valores atípicos)</td></tr>
      <tr><td><code>loss</code> baja pero <code>val_loss</code> sube</td><td>Sobreajuste: early stopping, dropout, L2 o red más simple</td></tr>
      <tr><td>Las dos pérdidas altas y sin mejorar</td><td>Infraajuste: más capacidad, más épocas o revisar los datos y la tasa de aprendizaje</td></tr>
      <tr><td>Demasiadas combinaciones de hiperparámetros o variables</td><td>Algoritmo genético en lugar de probarlas todas</td></tr>
    </tbody>
  </table>
</div>

### Tres reglas de oro

<div class="reglas">
  <div class="regla"><strong>Cada dato, su red</strong>Elige la arquitectura según la estructura del dato, no por costumbre.</div>
  <div class="regla"><strong>La validación manda</strong>Compara siempre entrenamiento y validación para detectar sobreajuste o infraajuste.</div>
  <div class="regla"><strong>Empieza simple</strong>Una red modesta (o un modelo ya entrenado) primero; añade complejidad solo si los resultados lo justifican.</div>
</div>
