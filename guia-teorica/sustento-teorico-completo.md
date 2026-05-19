# Guia Teorica Completa — AWS Certified AI Practitioner AIF-C01

> **Rodrigo Aguilar** | Cloud Architect & AWS Authorized Instructor LATAM

---

## Indice

1. [Fundamentos de Inteligencia Artificial](#1-fundamentos-de-inteligencia-artificial)
2. [Modelos Fundacionales y LLMs](#2-modelos-fundacionales-fm-y-llms)
3. [Inteligencia Artificial Generativa](#3-inteligencia-artificial-generativa)
4. [Tecnicas de Personalizacion de Modelos](#4-tecnicas-de-personalizacion-de-modelos)
5. [Generacion Aumentada por Recuperacion (RAG)](#5-generacion-aumentada-por-recuperacion-rag)
6. [Agentes de IA y Amazon Bedrock Agents](#6-agentes-de-ia-y-amazon-bedrock-agents)
7. [Amazon Bedrock — Plataforma Central](#7-amazon-bedrock--plataforma-central)
8. [Amazon SageMaker — Plataforma ML](#8-amazon-sagemaker--plataforma-ml)
9. [Servicios de IA de AWS](#9-servicios-de-ia-de-aws)
10. [Metricas de Evaluacion de Modelos](#10-metricas-de-evaluacion-de-modelos)
11. [Gobernanza, Seguridad y Responsabilidad en IA](#11-gobernanza-seguridad-y-responsabilidad-en-ia)
12. [Tecnicas de Vision por Computadora y Deteccion](#12-tecnicas-de-vision-por-computadora-y-deteccion)
13. [Glosario de Terminos Clave](#13-glosario-de-terminos-clave)

---

## 1. Fundamentos de Inteligencia Artificial

### 1.1 Que es la Inteligencia Artificial

La Inteligencia Artificial (IA) es la rama de la informatica que busca crear sistemas capaces de realizar tareas que normalmente requieren inteligencia humana. Estos sistemas pueden razonar, aprender, planificar, percibir el entorno y resolver problemas.

La IA es el concepto mas amplio y actua como paraguas que contiene tanto el Machine Learning como el Deep Learning.

### 1.2 La Jerarquia: IA, ML y Deep Learning

Existe una relacion jerarquica fundamental entre estos tres conceptos:

```
┌─────────────────────────────────────────┐
│           IA (Inteligencia Artificial)   │
│   Simula capacidades humanas             │
│  ┌───────────────────────────────────┐  │
│  │    Machine Learning (ML)           │  │
│  │    Aprende de datos                │  │
│  │  ┌─────────────────────────────┐  │  │
│  │  │     Deep Learning           │  │  │
│  │  │   Redes neuronales          │  │  │
│  │  └─────────────────────────────┘  │  │
│  └───────────────────────────────────┘  │
└─────────────────────────────────────────┘
```

- **IA**: Simula capacidades humanas de resolucion de problemas. Concepto mas amplio.
- **ML**: Subconjunto de IA que aplica tecnicas de aprendizaje basadas en datos para hacer predicciones sin ser programado explicitamente.
- **Deep Learning**: Subconjunto del ML que se enfoca en el procesamiento de datos mediante redes neuronales artificiales de multiples capas.

> **Regla de oro:** IA ⊃ ML ⊃ Deep Learning. Todo Deep Learning es ML, pero no todo ML es Deep Learning.

### 1.3 Tipos de Aprendizaje Automatico

#### Aprendizaje Supervisado
Utiliza datos **etiquetados** (con respuesta conocida) para entrenar el modelo. El modelo aprende la relacion entre entradas y salidas.

- **Casos de uso:** clasificacion de imagenes, deteccion de fraude, prediccion de precios
- **Ejemplo del examen:** dataset de imagenes etiquetadas de animales para clasificacion → aprendizaje supervisado

#### Aprendizaje No Supervisado
Trabaja con datos **sin etiquetar**. El modelo descubre patrones y estructuras ocultas por si mismo.

- **Casos de uso:** segmentacion de clientes, deteccion de anomalias, clustering

#### Aprendizaje por Refuerzo
El modelo (agente) aprende mediante interaccion con un entorno, recibiendo recompensas o penalizaciones por sus acciones.

- **Casos de uso:** juegos, robotica, optimizacion de rutas

#### Aprendizaje Activo
Tecnica donde el modelo selecciona activamente los datos mas informativos para etiquetar, minimizando el esfuerzo de etiquetado. Util cuando los datos etiquetados son escasos y costosos de obtener.

---

## 2. Modelos Fundacionales (FM) y LLMs

### 2.1 Que son los Modelos Fundacionales

Los modelos fundacionales (Foundation Models o FM) son modelos de IA de gran escala, entrenados con enormes volumenes de datos no etiquetados mediante aprendizaje autosupervisado. Pueden ser adaptados para una amplia variedad de tareas sin entrenamiento desde cero.

- Se entrenan una sola vez con grandes volumenes de datos
- Pueden ajustarse (fine-tune) para tareas especificas
- Reducen dramaticamente el costo y tiempo de desarrollo de soluciones IA

### 2.2 Grandes Modelos de Lenguaje (LLMs)

Los Large Language Models (LLMs) son un tipo especifico de modelo fundacional especializado en procesamiento y generacion de texto. Estan basados en la arquitectura Transformer.

**Arquitecturas clave mencionadas en el examen:**

| Arquitectura | Uso Principal |
|---|---|
| GPT (Generative Pre-trained Transformers) | Interfaces conversacionales en lenguaje natural |
| WaveNet | Generacion de audio y voz |
| ResNet (Red Neuronal Residual) | Vision por computadora |
| SVM (Support Vector Machine) | Clasificacion tradicional de ML |

### 2.3 Tokens

Los **tokens** son las unidades basicas de entrada y salida con las que opera un modelo de IA generativa. Representan palabras, subpalabras u otras unidades linguisticas en las que se divide el texto para su procesamiento.

- Un token puede ser una palabra completa, parte de una palabra, o un caracter
- El **costo de inferencia en Amazon Bedrock** se calcula en funcion de los tokens consumidos (entrada + salida)
- Los tokens NO son embeddings, ni pesos del modelo, ni prompts

### 2.4 Embeddings (Incrustaciones)

Los embeddings son representaciones matematicas numericas (vectores) de objetos y conceptos del mundo real. Permiten capturar relaciones semanticas entre conceptos en un espacio vectorial.

- Texto similar tiene vectores similares (cercanos en el espacio vectorial)
- Son fundamentales para busqueda semantica y sistemas RAG
- Los modelos de embedding convierten texto (o imagenes) en vectores

**Tipos relevantes para el examen:**

| Tipo | Descripcion |
|---|---|
| Modelo de embedding de texto | Convierte texto en vectores para busqueda semantica |
| Modelo de embedding multimodal | Convierte texto E imagenes en un espacio vectorial comun |

### 2.5 Parametros de Inferencia Clave

#### Temperatura
Controla la aleatoriedad (creatividad) del output del modelo.

- **Temperatura baja (cercana a 0):** respuestas deterministicas y predecibles → ideal para clasificacion, analisis de sentimiento
- **Temperatura alta:** respuestas mas creativas y variadas → ideal para generacion creativa de contenido

#### Top-K
Limita la seleccion del siguiente token a los K tokens mas probables. Un valor K mayor aumenta la variedad; uno menor la reduce.

#### Max Tokens (Longitud de salida)
Define la longitud maxima de la respuesta generada. No afecta la calidad ni el estilo de la respuesta, solo su extension.

---

## 3. Inteligencia Artificial Generativa

### 3.1 Que es la IA Generativa

La IA generativa es una rama de la IA capaz de **crear contenido nuevo**: texto, imagenes, audio, video, codigo. Se diferencia de la IA tradicional en que genera output original en lugar de solo clasificar o predecir.

**Casos de uso tipicos de IA generativa (segun el examen):**
- Resumir documentos, articulos, reclamos de clientes ✅
- Generar contenido de marketing ✅
- Traduccion de idiomas ✅
- Responder preguntas sobre documentos ✅
- Generacion de codigo ✅

**Lo que NO es IA generativa:**
- Clasificar clientes segun uso del producto → ML tradicional (clasificacion) ❌
- Segmentar clientes → ML tradicional (clustering) ❌
- Prever ingresos → ML tradicional (regresion) ❌

### 3.2 Alucinaciones en LLMs

Las **alucinaciones** (hallucinations) ocurren cuando un LLM genera contenido que parece verosimil, objetivo y bien redactado, pero es **factualmente incorrecto o inventado**.

**Estrategias para mitigar alucinaciones:**
- RAG: anclar las respuestas en fuentes externas verificadas
- Reducir la temperatura para respuestas mas deterministicas
- Configurar guardrails en Amazon Bedrock
- Evaluar el modelo regularmente con datasets de referencia

### 3.3 Sesgos en Modelos de IA

El sesgo (bias) ocurre cuando el modelo produce resultados sistematicamente injustos o discriminatorios.

| Tipo de Sesgo | Descripcion | Solucion |
|---|---|---|
| Sesgo demografico | El modelo funciona mejor para algunos grupos | Incluir datos mas diversos y representativos |
| Desequilibrio de clases | Una clase tiene muchos mas ejemplos que otra | Oversampling, undersampling, ajuste de pesos de clase |
| Sesgo historico | Perpetuar patrones discriminatorios del pasado | Nunca usar resultados historicos como unica referencia |

### 3.4 Fuga de Datos (Data Leakage)

La fuga de datos en IA ocurre cuando el modelo expone informacion privada que fue parte de su entrenamiento. Es diferente a las alucinaciones (datos falsos) — la fuga involucra datos reales que no deberian ser accesibles.

---

## 4. Tecnicas de Personalizacion de Modelos

### 4.1 Prompt Engineering (Ingenieria de Peticiones)

Tecnica de disenar y optimizar las instrucciones (prompts) que se dan al modelo para obtener mejores resultados, **sin modificar los pesos del modelo**. Es la forma mas economica y rapida de personalizar el comportamiento de un FM.

#### Zero-Shot Prompting
Se proporciona solo la instruccion **sin ejemplos**. El modelo resuelve la tarea basandose unicamente en su conocimiento preentrenado.

```
"Clasifique la tematica del siguiente texto como deportiva, politica 
o de entretenimiento: [texto de entrada]"
```

#### Few-Shot Prompting
Se proporcionan algunos **ejemplos** antes de la tarea real. El modelo aprende el patron de los ejemplos y lo aplica al nuevo caso.

```
"[Imagen 1], [Imagen 2] y [Imagen 3] son ejemplos de [clase objetivo]. 
Clasifique la siguiente imagen como..."
```

#### Chain-of-Thought (Cadena de Pensamiento)
Se instruye al modelo para que **muestre su razonamiento paso a paso** antes de dar la respuesta final.

```
"[Pregunta.] [Instrucciones a seguir.] 
Piense paso a paso y cuenteme su razonamiento"
```

#### ReAct (Reasoning + Acting)
Combina razonamiento con **acciones**. El modelo puede llamar herramientas externas (APIs, bases de datos) durante su proceso de razonamiento. Fundamental para agentes que necesitan informacion en tiempo real.

#### Role Description (Descripcion de Rol)
Se le asigna un **rol especifico** al modelo en el contexto del system prompt para adaptar el estilo, tono y nivel de la respuesta.

#### Inyeccion de Prompts
Es un **ATAQUE de seguridad**, no una tecnica legitima. Ocurre cuando un usuario malicioso inserta instrucciones en el prompt para manipular el comportamiento del modelo y saltarse sus restricciones.

### 4.2 Transfer Learning (Aprendizaje por Transferencia)

Tecnica que permite **reutilizar un modelo preentrenado** como punto de partida para una nueva tarea, en lugar de entrenar desde cero. Reduce drasticamente el tiempo, costo y datos necesarios.

> Es la estrategia cuando la empresa quiere "adoptar modelos previamente entrenados y adaptarlos a sus dominios especificos".

### 4.3 Fine-Tuning (Ajuste del Modelo)

Proceso de continuar el entrenamiento de un modelo preentrenado con datos especificos del dominio para especializarlo en tareas concretas. **Modifica los pesos del modelo.**

| Tipo | Descripcion | Datos requeridos |
|---|---|---|
| Instruction Tuning | Entrena con pares pregunta-respuesta | Etiquetados (prompt → respuesta) |
| Domain Adaptation | Adapta al vocabulario de un dominio especifico | Del dominio especifico |
| RLHF | Ajuste con retroalimentacion humana | Evaluaciones humanas |

### 4.4 Continued Pre-Training (Entrenamiento Previo Continuo)

Continuar entrenando el modelo base con nuevos datos (generalmente **no etiquetados**) para mantenerlo actualizado o expandir su conocimiento de dominio.

Util cuando:
- Se tienen datos sin etiquetar disponibles
- Se quiere mantener el modelo relevante con datos mas recientes
- Se necesita que el modelo adquiera nuevo conocimiento de dominio

### 4.5 Data Augmentation (Aumento de Datos)

Tecnica para **aumentar artificialmente** el tamano del dataset generando variaciones sinteticas de los datos existentes. Se usa cuando hay una cantidad limitada de datos etiquetados.

---

## 5. Generacion Aumentada por Recuperacion (RAG)

### 5.1 Que es RAG

RAG (Retrieval Augmented Generation) combina la recuperacion de informacion relevante desde una base de conocimiento externa con la capacidad generativa de un LLM. Permite que el modelo genere respuestas basadas en informacion actualizada y especifica, **sin necesidad de reentrenar**.

**Principal ventaja:** cuando el contenido cambia frecuentemente (politicas empresariales, documentacion), solo se actualiza la base de conocimiento, no el modelo.

### 5.2 Pipeline de RAG

```
FASE OFFLINE (Procesamiento por Lotes)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Documentos → [Modelo Embedding] → Vectores → [Vector Store]
                Paso 1                          Paso 2

FASE ONLINE (Tiempo Real — cuando el usuario consulta)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Consulta → [Embedding] → Busqueda similitud → Contexto → [LLM] → Respuesta
            Paso 3           Paso 4             Paso 5
```

**Pasos OFFLINE (batch sin conexion):** A y C — Generacion de embeddings + Creacion del indice  
**Pasos ONLINE (tiempo real):** B, D, E — Embedding de consulta, Recuperacion, Generacion

### 5.3 Vector Stores para RAG en AWS

- **Amazon Aurora PostgreSQL** con extension `pgvector` — solucion nativa de AWS para almacenar y consultar embeddings en base de datos relacional
- **Amazon OpenSearch Service** — tambien soporta busqueda vectorial para RAG

---

## 6. Agentes de IA y Amazon Bedrock Agents

### 6.1 Que son los Agentes de IA

Los agentes de IA son sistemas que pueden razonar, planificar y **ejecutar acciones de forma autonoma** para completar tareas complejas. A diferencia de un LLM estatico, un agente puede interactuar con herramientas externas, APIs y bases de datos.

### 6.2 Amazon Bedrock Agents

Servicio gestionado de AWS que permite crear agentes inteligentes que orquestan flujos de trabajo complejos.

- Integra LLMs con Knowledge Bases (RAG) y Action Groups (herramientas)
- Permite llamadas a APIs externas y sistemas empresariales
- **Ideal para:** procesamiento de reclamos, asistentes especializados, automatizacion de tareas empresariales

### 6.3 Advanced Prompts en Bedrock Agents

Los advanced prompts permiten personalizar las instrucciones del agente incluyendo **ejemplos especificos (few-shot)** para mejorar la precision de las respuestas, sin necesidad de reentrenar el modelo.

---

## 7. Amazon Bedrock — Plataforma Central

### 7.1 Que es Amazon Bedrock

Amazon Bedrock es el servicio de AWS que pone a disposicion **modelos fundacionales (FM) de multiples proveedores** (Anthropic Claude, Meta Llama, Mistral, Amazon Titan, etc.) para que los usuarios construyan y escalen aplicaciones de IA generativa sin gestionar infraestructura.

### 7.2 Modalidades de Rendimiento

| Modalidad | Descripcion | Cuando usar |
|---|---|---|
| On-Demand | Pago por tokens consumidos | Uso bajo o impredecible, pilotos |
| Provisioned Throughput | Capacidad reservada con pago fijo | Produccion con carga predecible y alta |

### 7.3 Guardrails de Bedrock

Las guardrails (barreras de proteccion) son configuraciones que controlan el comportamiento del modelo en produccion:

- Filtrar contenido inapropiado o toxico
- Bloquear temas especificos fuera del alcance de la aplicacion
- Redactar informacion sensible (PII)
- Evitar alucinaciones mediante filtros de respuestas fundamentadas

> **Caso de uso tipico del examen:** aplicacion para ninos donde se necesita garantizar contenido apropiado.

### 7.4 Knowledge Bases de Bedrock

Permiten conectar fuentes de datos empresariales (documentos en S3, etc.) a los FMs mediante **RAG gestionado**. La empresa solo actualiza los documentos y Bedrock se encarga de la indexacion y recuperacion automaticamente.

**Ideal cuando:** el contenido cambia frecuentemente y no se quiere reentrenar el modelo.

### 7.5 Evaluacion de Modelos en Bedrock

| Tipo | Descripcion | Sobrecarga |
|---|---|---|
| Evaluacion automatica | Metricas predefinidas y modelos juez sin humanos | Menor |
| Evaluacion con trabajadores humanos | Revisores humanos evaluan las respuestas | Mayor |

### 7.6 Playgrounds de Bedrock

Entornos de prueba dentro de la consola de Bedrock para experimentar con modelos de forma interactiva. Son herramientas de **desarrollo/exploracion**, no controles de produccion.

---

## 8. Amazon SageMaker — Plataforma ML

### 8.1 Que es SageMaker

Amazon SageMaker es la plataforma completa de AWS para construir, entrenar, ajustar y desplegar modelos de Machine Learning. A diferencia de Bedrock (que usa FMs preexistentes), SageMaker permite **construir modelos propios**.

### 8.2 Componentes Clave

#### SageMaker Clarify
Detecta **sesgos** en datos y modelos, y genera **explicaciones** de las predicciones (feature importance).

- Detectar sesgo demografico en modelos de credito, contratacion, etc.
- Generar metricas, informes y ejemplos para transparencia y explicabilidad
- Cumplir requisitos regulatorios de explicabilidad

#### SageMaker Model Monitor
Monitorea el **rendimiento y calidad** de los modelos en produccion a lo largo del tiempo.

- Detecta **data drift**: cambios en la distribucion de los datos de entrada
- Detecta **model drift**: degradacion del rendimiento del modelo con el tiempo
- Permite configurar alertas cuando el modelo se degrada

#### SageMaker Model Cards
**Documentacion estandarizada** del modelo que incluye proposito, metricas, sesgos conocidos, limitaciones y historial de versiones.

- Ideal para colaboracion con institutos de investigacion
- Transparencia hacia partes interesadas
- Seguimiento de cambios del modelo

> **Clarify vs Model Cards:** Clarify detecta sesgos y explica predicciones (herramienta tecnica). Model Cards documenta el modelo para transparencia y gobernanza (artefacto de documentacion).

#### SageMaker Data Wrangler
Herramienta para **preparacion, limpieza y transformacion** de datos antes del entrenamiento. No detecta sesgos ni explica predicciones.

#### SageMaker JumpStart
Repositorio de modelos preentrenados y soluciones ML que pueden desplegarse rapidamente. Requiere gestion de endpoints.

#### Network Isolation en SageMaker
Configuracion que **bloquea todo el trafico de red saliente** durante los jobs de entrenamiento e inferencia. Fundamental para cumplimiento normativo en entornos sin acceso a internet.

### 8.3 Modalidades de Inferencia en SageMaker

| Modalidad | Descripcion | Cuando usar |
|---|---|---|
| Inferencia en Tiempo Real | Endpoint activo, baja latencia | Predicciones individuales en produccion |
| Batch Transform | Procesa grandes volumenes sin endpoint permanente | Datos archivados de gran tamano |
| Inferencia Asincrona | Para payloads grandes con latencia tolerada | Solicitudes individuales grandes |
| Inferencia sin Servidor | Sin gestion de instancias | Cargas de trabajo esporadicas |

---

## 9. Servicios de IA de AWS

### 9.1 Servicios de Vision por Computadora

#### Amazon Rekognition
Servicio de **analisis de imagenes y videos**.

- Deteccion de objetos: identifica y clasifica objetos en imagenes
- **Moderacion de contenido:** detecta contenido inapropiado
- Reconocimiento facial, deteccion de texto en imagenes

> NO es adecuado para: analisis de texto, NLP, o etiquetado de datos para ML general.

#### Amazon Textract
**Extrae texto, tablas y formularios** de documentos escaneados (PDFs, imagenes). Va mas alla del OCR simple al entender la estructura del documento.

### 9.2 Servicios de Procesamiento de Lenguaje Natural

#### Amazon Comprehend
Servicio NLP que analiza texto para extraer:

- Entidades: personas, lugares, organizaciones, fechas
- Sentimiento: positivo, negativo, neutro, mixto
- **Deteccion de toxicidad:** identifica lenguaje danino o abusivo en comentarios

#### Amazon Comprehend Medical
Version especializada de Comprehend para textos medicos. Extrae:

- Diagnosticos y condiciones
- Medicamentos y dosis
- Procedimientos medicos
- Relaciones entre entidades clinicas

> Es el servicio correcto para procesar registros electronicos de salud (EHR).

#### Amazon Translate
Servicio de **traduccion automatica** de textos entre idiomas.

#### Amazon Transcribe
Convierte **audio a texto** (Speech-to-Text).

#### Amazon Polly
Convierte **texto en voz sintetizada** (Text-to-Speech).

#### Amazon Kendra
Servicio de **busqueda empresarial inteligente** que permite buscar en documentos corporativos usando lenguaje natural. Diferente a RAG porque es busqueda, no generacion.

### 9.3 Servicios de IA Especializados

#### Amazon Personalize
Servicio de **recomendaciones personalizadas** en tiempo real. Analiza el comportamiento del usuario para recomendar productos, contenido o acciones.

> NO es adecuado para: clasificacion, NLP, o analisis de imagenes.

#### Amazon Fraud Detector
**Detecta actividad fraudulenta** en transacciones online. Especifico para fraud detection, no para gestion de reclamos ni analisis de texto general.

#### Amazon Lex
Servicio para construir **chatbots conversacionales** con interfaces de voz y texto.

#### Amazon Q

| Servicio | Descripcion |
|---|---|
| Amazon Q Developer | Asistente de IA para desarrolladores. Genera codigo, explica servicios AWS. |
| Amazon Q Business | Asistente empresarial para empleados conectado a fuentes de datos corporativas. |

---

## 10. Metricas de Evaluacion de Modelos

### 10.1 Metricas para Clasificacion

#### Exactitud (Accuracy)
Proporcion de predicciones correctas sobre el total. Metrica principal para clasificacion cuando las clases estan **balanceadas**.

> Ejemplo: clasificacion de imagenes de animales, deteccion de enfermedades en plantas.

#### Puntuacion F1
Combina precision y recall en una sola metrica. Ideal para clasificacion con clases **desbalanceadas**, extraccion de informacion y NER.

### 10.2 Metricas para Regresion

#### RMSE (Root Mean Square Error)
Mide que tan lejos estan las predicciones de los valores reales. Se usa cuando el output es un **numero continuo** (prediccion de precios, temperaturas, etc.).

> NO se usa para clasificacion.

#### Coeficiente R2
Mide que tan bien el modelo explica la varianza en los datos. Tambien para regresion, no clasificacion.

### 10.3 Metricas para NLP y IA Generativa

#### BLEU (Bilingual Evaluation Understudy)
Metrica estandar para evaluar la calidad de **traducciones automaticas**. Compara n-gramas del texto traducido contra referencias humanas.

> Es la metrica correcta cuando se evalua traduccion de documentos entre idiomas.

#### ROUGE (Recall-Oriented Understudy for Gisting Evaluation)
Metrica para evaluar la calidad de **resumenes automaticos** de texto.

> NO es para traduccion.

### 10.4 Metricas de Rendimiento Operacional

#### Tiempo Medio de Respuesta (Latencia)
Mide la eficiencia en **tiempo de ejecucion** de los modelos en produccion.

#### CSAT (Customer Satisfaction Score)
Mide la **satisfaccion del usuario**, no la eficiencia tecnica del modelo.

### 10.5 Errores de Modelo

| Error | Descripcion |
|---|---|
| Overfitting (Ajuste Excesivo) | El modelo memoriza los datos de entrenamiento y no generaliza bien |
| Underfitting (Ajuste Deficiente) | El modelo no aprendio suficientemente, produce respuestas pobres en general |

---

## 11. Gobernanza, Seguridad y Responsabilidad en IA

### 11.1 Principios de IA Responsable

| Principio | Descripcion |
|---|---|
| Privacidad y Seguridad | Proteccion de datos personales y control de acceso |
| Equidad (Fairness) | Trato equitativo a todos los grupos demograficos |
| Explicabilidad | Capacidad de entender por que el modelo tomo una decision |
| Transparencia | Documentar y comunicar capacidades, limitaciones y sesgos |
| Gobernanza de Datos | Marco para gestionar como se recopilan, almacenan y usan los datos |

### 11.2 Complejidad vs Explicabilidad

Existe un **trade-off fundamental**: a mayor complejidad del modelo (LLMs, deep neural networks), menor es su explicabilidad. En sectores regulados (finanzas, salud) la explicabilidad es un requisito legal.

### 11.3 Residencia de Datos (Data Residency)

Estrategia de gobernanza que garantiza que los datos permanezcan dentro de una **jurisdiccion geografica especifica**. Critica para:

- Datos medicos bajo regulaciones locales
- Datos financieros sujetos a leyes de proteccion de datos
- Organizaciones en multiples paises con regulaciones distintas

### 11.4 Diversidad de Datos

La diversidad garantiza que todos los grupos demograficos esten **representados equitativamente**, reduciendo el sesgo del modelo.

> No debe confundirse con: exactitud (correctitud), sesgo de actualidad (mayor peso a datos recientes), o fiabilidad (consistencia).

### 11.5 Servicios AWS para Gobernanza y Cumplimiento

| Servicio | Proposito |
|---|---|
| AWS CloudTrail | Registra todas las llamadas a la API de AWS (auditoria) |
| AWS Artifact | Informes de cumplimiento normativo y certificaciones (SOC, ISO, PCI DSS) |
| AWS Audit Manager | Gestiona marcos de cumplimiento y recopila evidencia automaticamente |
| Amazon Macie | Detecta y protege datos sensibles (PII) en Amazon S3 |
| Amazon Inspector | Evalua vulnerabilidades de seguridad en infraestructura |
| AWS Config | Rastrea y registra cambios en la configuracion de recursos |
| Amazon CloudWatch | Monitoreo escalable de metricas, logs y eventos |

### 11.6 Seguridad con IAM

El **principio de minimo privilegio** (least privilege) con AWS IAM es la practica de seguridad fundamental para el uso seguro de LLMs en Amazon Bedrock. Garantiza que solo los roles autorizados puedan acceder a los modelos y recursos.

---

## 12. Tecnicas de Vision por Computadora y Deteccion

### 12.1 Deteccion de Objetos
Identifica y localiza objetos especificos dentro de una imagen, devolviendo tanto la clase del objeto como su posicion (bounding box).

> Ejemplo: identificar y clasificar animales en fotos de una base de datos.

### 12.2 Deteccion de Anomalias
Identifica patrones inusuales o fuera de lo normal en los datos. Se usa en mantenimiento predictivo, deteccion de fraude y control de calidad.

> No clasifica objetos en imagenes.

### 12.3 NER — Named Entity Recognition
**Reconocimiento de Entidades Nombradas:** identifica y clasifica entidades en texto (personas, organizaciones, lugares, fechas).

> Es NLP, no vision por computadora.

---

## 13. Glosario de Terminos Clave

| Termino | Definicion |
|---|---|
| **Inferencia** | Usar un modelo ya entrenado para hacer predicciones sobre datos nuevos (fase de produccion) |
| **Entrenamiento** | Proceso donde el modelo aprende patrones a partir de datos historicos |
| **Token** | Unidad basica de procesamiento de texto en LLMs (palabra, subpalabra o caracter) |
| **Embedding** | Representacion vectorial numerica de texto o imagenes para capturar significado semantico |
| **Temperatura** | Parametro que controla la aleatoriedad del output (0=deterministico, alto=creativo) |
| **Hallucination** | Cuando el modelo genera contenido que parece verdadero pero es factualmente incorrecto |
| **RAG** | Retrieval Augmented Generation: combina recuperacion de informacion con generacion de LLM |
| **Fine-tuning** | Ajustar un modelo preentrenado con datos especificos para especializarlo en una tarea |
| **Overfitting** | El modelo memoriza los datos de entrenamiento y no generaliza bien |
| **Underfitting** | El modelo no aprendio suficiente de los datos de entrenamiento |
| **BLEU** | Metrica para evaluar calidad de traducciones automaticas |
| **ROUGE** | Metrica para evaluar calidad de resumenes automaticos de texto |
| **RMSE** | Error cuadratico medio: metrica para modelos de regresion (valores continuos) |
| **Data Residency** | Garantia de que los datos no salgan de una jurisdiccion geografica especifica |
| **Guardrails** | Controles de seguridad y contenido que limitan el comportamiento del modelo en produccion |
| **Least Privilege** | Principio de seguridad: dar solo los permisos minimos necesarios |
| **Batch Inference** | Inferencia por lotes sobre grandes volumenes de datos archivados |
| **ReAct** | Tecnica de prompting que combina razonamiento con llamadas a herramientas externas |
| **Chain-of-Thought** | Tecnica que instruye al modelo a razonar paso a paso antes de dar una respuesta |
| **Transfer Learning** | Reutilizar un modelo preentrenado como base para nuevas tareas |
| **Data Augmentation** | Generar variaciones sinteticas de datos para ampliar el dataset |
| **Continued Pre-training** | Seguir entrenando el modelo base con nuevos datos no etiquetados para mantenerlo actualizado |
| **Instruction Tuning** | Fine-tuning con pares prompt-respuesta para ensena al modelo a seguir instrucciones |
| **RLHF** | Reinforcement Learning from Human Feedback: ajuste con retroalimentacion humana |
| **pgvector** | Extension de PostgreSQL para almacenar y consultar vectores de embeddings |
| **Data Drift** | Cambio en la distribucion de los datos de entrada en produccion |
| **Model Drift** | Degradacion del rendimiento del modelo en produccion con el tiempo |

---

*Documento elaborado para preparacion del examen AWS Certified AI Practitioner AIF-C01*  
*Rodrigo Aguilar — Cloud Architect & AWS Authorized Instructor LATAM*  
*Ultima actualizacion: Mayo 2026*
