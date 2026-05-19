# AWS Certified AI Practitioner — AIF-C01
## 65 Preguntas de Practica con Respuestas y Explicaciones

> **Rodrigo Aguilar** | Cloud Architect & AWS Authorized Instructor  
> Basado en simulacro de examen AIF-C01

---

## INDICE DE PREGUNTAS

| # | Tema Principal |
|---|---------------|
| 1–5 | Conceptos fundamentales de IA/ML |
| 6–10 | Modelos Fundacionales y parametros |
| 11–20 | Servicios AWS de IA |
| 21–30 | Amazon Bedrock y Agentes |
| 31–40 | Personalizacion y Fine-Tuning |
| 41–50 | Prompt Engineering |
| 51–58 | Evaluacion, Metricas y Monitoreo |
| 59–65 | Gobernanza, Seguridad y Responsabilidad |

---

## PREGUNTAS

---

### Pregunta 1
**Un especialista en IA tiene una base de datos de fotos de animales. El especialista quiere identificar y clasificar automaticamente a los animales de las fotos sin esfuerzo humano. ¿Que estrategia cumple estos requisitos?**

- A. Deteccion de objetos
- B. Deteccion de anomalias
- C. Reconocimiento de entidades nombradas
- D. Restauracion de imagenes

**✅ Respuesta correcta: A — Deteccion de objetos**

**Explicacion:** La deteccion de objetos (object detection) identifica y clasifica objetos dentro de una imagen, devolviendo la clase del objeto y su ubicacion. Es exactamente lo que se necesita para identificar y clasificar animales en fotos automaticamente.

- **B incorrecta:** La deteccion de anomalias busca patrones inusuales, no clasifica objetos.
- **C incorrecta:** NER (Named Entity Recognition) opera sobre texto, no imagenes.
- **D incorrecta:** La restauracion de imagenes mejora la calidad visual, no clasifica contenido.

---

### Pregunta 2
**Una empresa desea usar un modelo de lenguaje de gran tamano (LLM) en Amazon Bedrock para el analisis de sentimiento. La empresa quiere que el LLM produzca respuestas consistentes. ¿Que ajuste debe hacer la empresa a un parametro de inferencia para cumplir con estos requisitos?**

- A. Disminuir el valor de la temperatura
- B. Aumentar el valor de la temperatura
- C. Reducir la longitud de los tokens de salida
- D. Aumentar la longitud maxima de generacion

**✅ Respuesta correcta: A — Disminuir el valor de la temperatura**

**Explicacion:** El analisis de sentimiento requiere respuestas **deterministicas y consistentes** (positivo/negativo/neutro). La temperatura controla la aleatoriedad: valores bajos (cercanos a 0) producen respuestas predecibles. Temperatura alta genera variabilidad, lo opuesto a lo requerido.

- **B incorrecta:** Temperatura alta aumenta la creatividad/variabilidad, indeseable para clasificacion.
- **C y D incorrectas:** La longitud de tokens no afecta la consistencia del resultado.

---

### Pregunta 3
**Una empresa esta creando un agente para su aplicacion mediante Agentes para Amazon Bedrock. El agente tiene un buen rendimiento, pero la empresa quiere mejorar la exactitud del agente mediante algunos ejemplos especificos. ¿Que solucion cumple estos requisitos?**

- A. Modificar las peticiones avanzadas para que el agente incluya los ejemplos
- B. Crear una barrera de proteccion para el agente que incluya los ejemplos
- C. Utilizar Amazon SageMaker Ground Truth para etiquetar los ejemplos
- D. Ejecutar un script en AWS Lambda que agregue los ejemplos al conjunto de datos de entrenamiento

**✅ Respuesta correcta: A — Modificar las peticiones avanzadas para que el agente incluya los ejemplos**

**Explicacion:** Los **advanced prompts** en Bedrock Agents permiten incluir ejemplos especificos (few-shot prompting) directamente en las instrucciones del agente para mejorar la precision sin reentrenar el modelo.

- **B incorrecta:** Las guardrails controlan seguridad y contenido, no mejoran exactitud con ejemplos.
- **C incorrecta:** SageMaker Ground Truth es para etiquetar datos de entrenamiento, no ajustar un agente existente.
- **D incorrecta:** Agregar ejemplos al training data requeriria reentrenar el modelo — costoso y desproporcionado.

---

### Pregunta 4
**Una empresa quiere desarrollar una aplicacion de IA para ayudar a sus empleados a comprobar las reclamaciones de los clientes, identificar los detalles de reclamaciones especificas y acceder a los documentos de una reclamacion. ¿Que solucion cumple estos requisitos?**

- A. Usar Agentes para Amazon Bedrock con Amazon Fraud Detector para crear la aplicacion
- B. Usar Agentes para Amazon Bedrock con las bases de conocimiento de Amazon Bedrock para crear la aplicacion
- C. Usar Amazon Personalize con las bases de conocimiento de Amazon Bedrock para crear la aplicacion
- D. Usar la IA de Amazon SageMaker para crear la aplicacion mediante el entrenamiento de un nuevo modelo de ML

**✅ Respuesta correcta: B — Usar Agentes para Amazon Bedrock con las bases de conocimiento de Amazon Bedrock**

**Explicacion:** El escenario requiere logica de orquestacion (agente) + acceso a documentos de reclamaciones (knowledge base con RAG). Bedrock Agents orquesta la tarea y las Knowledge Bases proveen acceso a los documentos corporativos.

- **A incorrecta:** Fraud Detector detecta fraude financiero, no gestiona documentos de reclamaciones.
- **C incorrecta:** Amazon Personalize es para recomendaciones personalizadas, no gestion de reclamaciones.
- **D incorrecta:** Entrenar un modelo nuevo desde cero es desproporcionado y no resuelve el acceso a documentos.

---

### Pregunta 5
**Una empresa necesita usar la IA de Amazon SageMaker para la inferencia y el entrenamiento de modelos. La empresa debe cumplir con los requisitos normativos para ejecutar los trabajos de SageMaker en un entorno aislado sin acceso a Internet. ¿Que solucion cumplira con estos requisitos?**

- A. Ejecutar el entrenamiento y la inferencia de SageMaker mediante SageMaker Experiments
- B. Ejecutar el entrenamiento y la inferencia de SageMaker mediante el aislamiento de red
- C. Cifrar los datos en reposo mediante el cifrado para las capacidades geoespaciales de SageMaker
- D. Asociar los roles apropiados de AWS IAM con los trabajos de SageMaker

**✅ Respuesta correcta: B — Ejecutar el entrenamiento y la inferencia de SageMaker mediante el aislamiento de red**

**Explicacion:** El **network isolation** en SageMaker bloquea todo el trafico de red saliente durante los jobs, garantizando que los datos y modelos no salgan del entorno controlado. Es la solucion especifica para entornos aislados por cumplimiento normativo.

- **A incorrecta:** SageMaker Experiments es para tracking de experimentos, no aislamiento de red.
- **C incorrecta:** El cifrado protege confidencialidad, no aislamiento de conectividad.
- **D incorrecta:** IAM controla permisos de acceso a servicios AWS, no el aislamiento de red del job.

---

### Pregunta 6
**Un especialista en IA utiliza un modelo de lenguaje de gran tamano (LLM) para crear contenido de campanas de marketing. El contenido generado parece verosimil y objetivo, pero es inexacto. ¿Cual problema tiene el LLM?**

- A. Fuga de datos
- B. Alucinacion
- C. Ajuste excesivo
- D. Ajuste deficiente

**✅ Respuesta correcta: B — Alucinacion**

**Explicacion:** La **alucinacion** (hallucination) ocurre cuando el modelo genera contenido que parece verdadero y bien fundamentado, pero es factualmente incorrecto. Es el problema clasico de los LLMs en produccion.

- **A incorrecta:** La fuga de datos implica exposicion de informacion privada del entrenamiento.
- **C incorrecta:** Overfitting ocurre cuando el modelo memoriza datos de entrenamiento y no generaliza.
- **D incorrecta:** Underfitting es cuando el modelo no aprendio lo suficiente y produce respuestas pobres en general.

---

### Pregunta 7
**Un especialista en IA desea usar un modelo fundacional (FM) para disenar una aplicacion de busqueda. La aplicacion de busqueda debe gestionar las consultas que contienen texto e imagenes y la consulta de incrustaciones de un modelo de IA generativa como vectores en la base de datos. ¿Que tipo de FM debe usar el especialista en IA para impulsar la aplicacion de busqueda?**

- A. Modelo de incrustacion multimodal
- B. Modelo de incrustacion de texto
- C. Modelo de generacion multimodal
- D. Modelo de generacion de imagenes

**✅ Respuesta correcta: A — Modelo de incrustacion multimodal**

**Explicacion:** La aplicacion debe procesar consultas con **texto e imagenes** y convertirlas en vectores para busqueda semantica. Un modelo de embedding multimodal convierte ambas modalidades (texto e imagenes) en vectores en un espacio semantico comun.

- **B incorrecta:** Un modelo de embedding de solo texto no puede procesar imagenes.
- **C incorrecta:** Un modelo de generacion multimodal crea contenido nuevo, no esta optimizado para busqueda por similitud.
- **D incorrecta:** Un modelo de generacion de imagenes produce imagenes, no vectores para busqueda.

---

### Pregunta 8
**¿Que termino describe a las representaciones numericas de objetos y conceptos del mundo real usadas por los modelos de IA y de procesamiento de lenguaje natural (NLP) para comprender informacion textual?**

- A. Incrustaciones
- B. Tokens
- C. Modelos
- D. Binarios

**✅ Respuesta correcta: A — Incrustaciones (Embeddings)**

**Explicacion:** Las **incrustaciones (embeddings)** son representaciones vectoriales numericas de conceptos, palabras o documentos que capturan relaciones semanticas. Son el mecanismo fundamental que permite a los modelos de IA comprender el significado del texto.

- **B incorrecta:** Los tokens son unidades de texto fragmentado (palabras/subpalabras), no representaciones numericas de conceptos.
- **C incorrecta:** Los modelos son los sistemas de IA en si mismos.
- **D incorrecta:** Los binarios no tienen relacion con representaciones semanticas en IA.

---

### Pregunta 9
**Una empresa financiera usa IA para ayudar con algunas de las tareas de la empresa. ¿Que opcion es uno de los usos de los modelos de IA generativa?**

- A. Resumir los reclamos de los clientes
- B. Clasificar los clientes segun su uso del producto
- C. Segmentar a los clientes segun el tipo de inversiones
- D. Prever los ingresos para ciertos productos

**✅ Respuesta correcta: A — Resumir los reclamos de los clientes**

**Explicacion:** Resumir texto es una tarea de **generacion de lenguaje** — el modelo genera un resumen nuevo a partir de contenido existente. Esto es caracteristico de la IA generativa.

- **B y C incorrectas:** Clasificacion y segmentacion de clientes son tareas de ML tradicional (clasificacion/clustering), no generacion.
- **D incorrecta:** Prever ingresos es una tarea de regresion predictiva, ML tradicional.

---

### Pregunta 10
**Una empresa usa modelos de dominios especificos. La empresa quiere evitar crear modelos nuevos. En su lugar, quiere adoptar modelos previamente entrenados y adaptarlos a sus dominios especificos para realizar tareas relacionadas. ¿Que estrategia de ML cumple estos requisitos?**

- A. Aumentar el numero de fechas de inicio
- B. Usar el aprendizaje por transferencia
- C. Disminuir el numero de fechas de inicio
- D. Usar el aprendizaje no supervisado

**✅ Respuesta correcta: B — Usar el aprendizaje por transferencia**

**Explicacion:** El **transfer learning** permite reutilizar modelos preentrenados como punto de partida y adaptarlos a dominios especificos sin entrenar desde cero. Es exactamente lo que describe el enunciado.

- **A y C incorrectas:** Modificar fechas de inicio son parametros de entrenamiento sin relacion con reutilizacion de modelos.
- **D incorrecta:** El aprendizaje no supervisado es un paradigma de entrenamiento para datos sin etiquetas, no resuelve la reutilizacion de modelos.

---

### Pregunta 11
**Una empresa esta entrenando a sus empleados sobre como estructurar mejor las peticiones para modelos fundacionales. Seleccione la tecnica de ingenieria de peticiones correcta para cada plantilla:**

- **Plantilla 1:** "Clasifique la tematica del siguiente texto como deportiva, politica o de entretenimiento: [texto de entrada]"
- **Plantilla 2:** "[Imagen 1], [Imagen 2] y [Imagen 3] son ejemplos de [clase objetivo]. Clasifique la siguiente imagen como..."
- **Plantilla 3:** "[Pregunta.] [Instrucciones a seguir.] Piense paso a paso y cuenteme su razonamiento"

Opciones: Razonamiento en cadena de pensamiento / Aprendizaje few-shot / Aprendizaje zero-shot

**✅ Respuestas correctas:**

| Plantilla | Tecnica |
|-----------|---------|
| Plantilla 1 | **Zero-shot** — Solo instruccion, sin ejemplos |
| Plantilla 2 | **Few-shot** — Provee ejemplos antes de la tarea |
| Plantilla 3 | **Chain-of-thought** — "Paso a paso" es el marcador definitorio |

**Explicacion:**
- **Zero-shot:** Solo se da la instruccion sin ejemplos. El modelo usa su conocimiento preentrenado.
- **Few-shot:** Se proporcionan ejemplos (shots) para que el modelo aprenda el patron.
- **Chain-of-thought:** La frase "piense paso a paso" instruye al modelo a mostrar su razonamiento antes de responder.

---

### Pregunta 12
**Una empresa desea evaluar los costos asociados con el uso de un modelo de lenguaje de gran tamano (LLM) para generar inferencias. La empresa quiere usar Amazon Bedrock para elegir adecuadamente para su aplicacion generativa. ¿Que factor impulsara los costos de inferencia?**

- A. Cantidad de tokens consumidos
- B. Valor de temperatura
- C. Cantidad de datos usados para entrenar el LLM
- D. Tiempo total de entrenamiento

**✅ Respuesta correcta: A — Cantidad de tokens consumidos**

**Explicacion:** En Amazon Bedrock, el pricing de inferencia se basa directamente en **tokens de entrada + tokens de salida**. A mas tokens procesados, mayor es el costo.

- **B incorrecta:** La temperatura es un parametro de sampling que no afecta el precio.
- **C y D incorrectas:** Los costos de datos de entrenamiento y tiempo de entrenamiento corresponden al proceso de fine-tuning, no a la inferencia en produccion.

---

### Pregunta 13
**Una empresa busca respuestas mas personalizadas para las peticiones de sus modelos de IA generativa. Seleccione la metodologia de personalizacion correcta para cada caso practico:**

- **Caso 1:** A los modelos se les debe ensenar una nueva tarea especifica del dominio
- **Caso 2:** Hay disponible una cantidad limitada de datos etiquetados y se necesitan mas datos
- **Caso 3:** Estan disponibles los datos sin etiquetar

Opciones: Entrenamiento previo continuo / Aumento de datos / Ajuste del modelo

**✅ Respuestas correctas:**

| Caso | Metodologia |
|------|-------------|
| Caso 1 | **Ajuste del modelo (Fine-tuning)** |
| Caso 2 | **Aumento de datos (Data Augmentation)** |
| Caso 3 | **Entrenamiento previo continuo (Continued Pre-training)** |

**Explicacion:**
- **Fine-tuning:** Adapta el modelo a una tarea especifica con datos etiquetados del dominio.
- **Data Augmentation:** Genera variaciones sinteticas cuando los datos etiquetados son escasos.
- **Continued Pre-training:** Usa grandes volumenes de datos no etiquetados para expandir el conocimiento del modelo.

---

### Pregunta 14
**Una empresa quiere ajustar un modelo fundacional (FM) para responder preguntas de un dominio especifico. La empresa quiere usar un ajuste basado en instrucciones. ¿Como debe preparar la empresa los datos de entrenamiento?**

- A. Reunir documentos internos de la empresa y materiales especificos del sector. Combinar los documentos y materiales en un solo archivo.
- B. Recopilar resenas externas de la empresa de varias fuentes en linea. Etiquetar manualmente cada opinion como positiva o negativa.
- C. Crear pares de preguntas y respuestas que aborden especificamente temas relacionados con el dominio de la empresa.
- D. Redactar peticiones few-shot para que el modelo responda exclusivamente con informacion del dominio.

**✅ Respuesta correcta: C — Crear pares de preguntas y respuestas que aborden especificamente temas relacionados con el dominio**

**Explicacion:** El **instruction tuning** requiere pares prompt → respuesta esperada. El modelo aprende a seguir instrucciones en el contexto del dominio especifico a partir de estos pares estructurados.

- **A incorrecta:** Juntar documentos es util para continued pre-training, no instruction tuning.
- **B incorrecta:** Etiquetar resenas como positivo/negativo es preparacion para un clasificador de sentimiento.
- **D incorrecta:** Redactar few-shot prompts es prompt engineering, no preparacion de datos de entrenamiento.

---

### Pregunta 15
**Una empresa esta creando un chatbot. El chatbot usa Amazon Lex y Amazon OpenSearch Service. El chatbot usa los datos privados de la empresa para responder preguntas. La empresa almacena los datos en una representacion vectorial antes de almacenarlos en una base de datos. ¿Que tipo de modelo fundacional (FM) cumple con estos requisitos?**

- A. Modelo de finalizacion de textos
- B. Modelo de seguimiento de instrucciones
- C. Modelo de incrustaciones de texto
- D. Modelo de generacion de imagenes

**✅ Respuesta correcta: C — Modelo de incrustaciones de texto**

**Explicacion:** El escenario describe una arquitectura RAG con OpenSearch como vector store. Los datos se convierten en **representaciones vectoriales (embeddings)** antes de almacenarse. Eso es exactamente lo que hace un modelo de embedding de texto.

- **A y B incorrectas:** Los modelos de finalizacion y seguimiento de instrucciones son generativos, no producen vectores para indexacion.
- **D incorrecta:** Un modelo de generacion de imagenes no tiene relacion con este caso de uso.

---

### Pregunta 16
**¿Que metrica mide la eficiencia en tiempo de ejecucion de los modelos de IA en funcionamiento?**

- A. Puntuacion de satisfaccion del cliente (CSAT)
- B. Tiempo de entrenamiento para cada fecha de inicio
- C. Tiempo medio de respuesta
- D. Numero de instancias de entrenamiento

**✅ Respuesta correcta: C — Tiempo medio de respuesta**

**Explicacion:** El **tiempo medio de respuesta** (latencia promedio) mide directamente que tan rapido responde el modelo en produccion, es decir, su eficiencia en tiempo de ejecucion.

- **A incorrecta:** CSAT mide satisfaccion del usuario, no eficiencia tecnica.
- **B incorrecta:** El tiempo de entrenamiento es una metrica del proceso de entrenamiento, no de inferencia en produccion.
- **D incorrecta:** El numero de instancias de entrenamiento es un parametro de infraestructura.

---

### Pregunta 17
**Un banco ajusto un modelo de lenguaje de gran tamano (LLM) para acelerar el proceso de aprobacion de prestamos. Durante una auditoria externa del modelo, la empresa descubrio que el modelo aprueba prestamos a un ritmo mas rapido para un grupo demografico especifico que para otros. ¿Como deberia el banco solucionar este problema de la manera MAS rentable?**

- A. Incluir datos de entrenamiento mas diversos. Volver a ajustar el modelo con los nuevos datos.
- B. Usar la generacion aumentada por recuperacion (RAG) con el modelo ajustado.
- C. Usar las comprobaciones de AWS Trusted Advisor para eliminar los sesgos.
- D. Preentrear un nuevo LLM con datos de entrenamiento mas diversos.

**✅ Respuesta correcta: A — Incluir datos de entrenamiento mas diversos. Volver a ajustar el modelo con los nuevos datos.**

**Explicacion:** El sesgo demografico proviene de datos de entrenamiento no representativos. La solucion mas rentable es re-hacer el fine-tuning con datos mas diversos y balanceados, reutilizando el modelo existente.

- **B incorrecta:** RAG recupera informacion pero no corrige sesgos aprendidos durante el entrenamiento.
- **C incorrecta:** Trusted Advisor es para optimizacion de costos e infraestructura, no sesgo en modelos ML.
- **D incorrecta:** Preentrear un LLM nuevo desde cero es la opcion mas costosa y desproporcionada.

---

### Pregunta 18
**Una empresa quiere mantener su modelo fundacional (FM) relevante mediante el uso de los datos mas recientes. La empresa quiere implementar una estrategia de actualizaciones periodicas del FM. ¿Que solucion cumple estos requisitos?**

- A. Aprendizaje por lotes
- B. Entrenamiento previo continuo
- C. Entrenamiento estatico
- D. Entrenamiento latente

**✅ Respuesta correcta: B — Entrenamiento previo continuo**

**Explicacion:** El **continued pre-training** consiste en seguir entrenando el modelo base periodicamente con nuevos datos para mantenerlo actualizado, sin cambiar su arquitectura ni requerir datos etiquetados.

- **A incorrecta:** El aprendizaje por lotes es una tecnica de optimizacion del proceso de entrenamiento, no una estrategia de actualizacion continua.
- **C incorrecta:** Entrenamiento estatico implica no actualizar el modelo — lo opuesto a lo requerido.
- **D incorrecta:** "Entrenamiento latente" no es un termino estandar en el examen AIF-C01.

---

### Pregunta 19
**Una empresa de medios quiere analizar el comportamiento y la demografia de los espectadores para recomendar contenido personalizado. La empresa quiere mantener el rendimiento. La empresa tambien desea observar si la calidad del modelo cambia con el tiempo. ¿Que servicio o caracteristica de AWS cumple estos requisitos?**

- A. Amazon Rekognition
- B. Amazon SageMaker Clarify
- C. Amazon Comprehend
- D. Amazon SageMaker Model Monitor

**✅ Respuesta correcta: D — Amazon SageMaker Model Monitor**

**Explicacion:** El requisito clave es **observar si la calidad del modelo cambia con el tiempo** (data drift, model drift) en produccion. SageMaker Model Monitor es el servicio especifico para monitoreo continuo de calidad del modelo.

- **A incorrecta:** Rekognition analiza imagenes y video.
- **B incorrecta:** SageMaker Clarify detecta sesgos y explica predicciones, no monitorea calidad en el tiempo de forma continua.
- **C incorrecta:** Comprehend es NLP para analisis de texto.

---

### Pregunta 20
**¿A que se refiere la inferencia en el contexto de la IA?**

- A. El proceso de creacion de nuevos algoritmos de IA
- B. El uso de un modelo entrenado para hacer predicciones o decisiones sobre datos no vistos
- C. El proceso de combinar varios modelos de IA en un solo modelo
- D. El metodo de recopilacion de datos de entrenamiento para sistemas de IA

**✅ Respuesta correcta: B — El uso de un modelo entrenado para hacer predicciones o decisiones sobre datos no vistos**

**Explicacion:** La **inferencia** es la fase de produccion donde un modelo ya entrenado se aplica a datos nuevos para generar predicciones, clasificaciones o respuestas. Es la fase opuesta al entrenamiento.

- **A incorrecta:** Crear nuevos algoritmos es investigacion/desarrollo.
- **C incorrecta:** Combinar modelos es ensemble learning.
- **D incorrecta:** Recopilar datos de entrenamiento es preparacion de datos.

---

### Pregunta 21
**Una empresa necesita supervisar el rendimiento de sus sistemas de ML mediante el uso de un servicio de AWS altamente escalable. ¿Que servicio de AWS cumple con estos requisitos?**

- A. Amazon CloudWatch
- B. AWS CloudTrail
- C. AWS Trusted Advisor
- D. AWS Config

**✅ Respuesta correcta: A — Amazon CloudWatch**

**Explicacion:** **Amazon CloudWatch** es el servicio nativo de monitoreo de AWS: recopila metricas, logs y eventos de cualquier servicio incluyendo SageMaker, y escala automaticamente. Es el servicio correcto para supervisar rendimiento de sistemas ML.

- **B incorrecta:** CloudTrail registra llamadas a la API para auditoria, no monitoreo de rendimiento.
- **C incorrecta:** Trusted Advisor da recomendaciones de buenas practicas y costos.
- **D incorrecta:** AWS Config rastrea cambios en la configuracion de recursos.

---

### Pregunta 22
**Una empresa crea un modelo de clasificacion de imagenes para predecir las enfermedades de las plantas a partir de fotografias de hojas de plantas. La empresa desea enviar algunas imagenes nuevas y quiere evaluar correctamente el modelo. ¿Que metrica de evaluacion debe usar la empresa para medir el rendimiento del modelo?**

- A. Puntuacion de coeficiente de correlacion R2
- B. Exactitud
- C. Error cuadratico medio (RMSE)
- D. Tasa de aprendizaje

**✅ Respuesta correcta: B — Exactitud (Accuracy)**

**Explicacion:** El modelo es de **clasificacion** (enfermedades de plantas = categorias discretas). La metrica estandar para clasificacion es la **exactitud**: proporcion de predicciones correctas sobre el total.

- **A y C incorrectas:** R2 y RMSE son metricas de **regresion** (valores numericos continuos), no clasificacion.
- **D incorrecta:** La tasa de aprendizaje es un hiperparametro del entrenamiento, no una metrica de evaluacion.

---

### Pregunta 23
**Una empresa esta implementando agentes inteligentes para ofrecer experiencias de busqueda conversacional a sus clientes. La empresa necesita un servicio de base de datos que almacene los datos de incrustaciones de un modelo de IA generativa como vectores en la base de datos. ¿Que servicio de AWS cumplira estos requisitos?**

- A. Amazon Athena
- B. Amazon Aurora PostgreSQL
- C. Amazon Redshift
- D. Amazon EMR

**✅ Respuesta correcta: B — Amazon Aurora PostgreSQL**

**Explicacion:** Amazon Aurora PostgreSQL soporta la extension **pgvector**, que permite almacenar y consultar embeddings (vectores) directamente en la base de datos relacional. Es la solucion nativa de AWS para vector store en arquitecturas RAG.

- **A incorrecta:** Athena es para consultas SQL sobre S3, no una base de datos con soporte de vectores.
- **C incorrecta:** Redshift es un data warehouse analitico sin soporte nativo de vectores.
- **D incorrecta:** EMR es para procesamiento de big data (Spark/Hadoop), no una base de datos para embeddings.

---

### Pregunta 24
**Una empresa esta desarrollando un modelo de ML para la aprobacion de prestamos. La empresa debe implementar una solucion para detectar sesgos en el modelo y las predicciones del modelo. ¿Que servicio cumplira con estos requisitos?**

- A. Amazon SageMaker Clarify
- B. Amazon SageMaker Data Wrangler
- C. Tarjetas modelo de Amazon SageMaker
- D. Tarjetas de servicio de IA de AWS

**✅ Respuesta correcta: A — Amazon SageMaker Clarify**

**Explicacion:** **SageMaker Clarify** es el servicio especifico para detectar sesgos en datos y modelos, y generar explicaciones de predicciones (feature importance). Es la herramienta correcta para aplicaciones de credito donde el sesgo es un riesgo regulatorio.

- **B incorrecta:** Data Wrangler es para preparacion y transformacion de datos.
- **C incorrecta:** Las Model Cards son documentacion del modelo, no deteccion de sesgos.
- **D incorrecta:** Las tarjetas de servicio de IA de AWS son documentacion de servicios, no herramientas de analisis.

---

### Pregunta 25
**Una empresa hace previsiones cada trimestre para decidir como optimizar las operaciones y asi poder satisfacer la demanda esperada. La empresa usa modelos de ML para tomar estas decisiones. Un especialista en IA esta redactando un informe sobre los modelos de ML para garantizar la transparencia y explicabilidad a las partes interesadas de la empresa. ¿Que debe incluir el especialista en IA en el informe para cumplir con los requisitos de transparencia y explicabilidad?**

- A. Codigo para el entrenamiento de modelos
- B. Graficos de dependencia parcial (PDP)
- C. Datos de muestra para el entrenamiento
- D. Tablas de convergencia de modelos

**✅ Respuesta correcta: B — Graficos de dependencia parcial (PDP)**

**Explicacion:** Los **PDP (Partial Dependence Plots)** muestran visualmente como cada feature influye en las predicciones del modelo. Son la herramienta estandar de explicabilidad en ML, comprensibles para audiencias no tecnicas (stakeholders).

- **A incorrecta:** El codigo de entrenamiento es tecnico e interno, no aporta explicabilidad a stakeholders.
- **C incorrecta:** Los datos de muestra son insumos del modelo, no explican sus decisiones.
- **D incorrecta:** Las tablas de convergencia muestran el proceso de optimizacion durante el entrenamiento, no como el modelo toma decisiones.

---

### Pregunta 26
**Una empresa quiere identificar el lenguaje danino en la seccion de comentarios de las publicaciones en sus redes sociales mediante el uso de un modelo de ML. La empresa necesita entrenar el modelo. ¿Que estrategia debe usar la empresa para identificar el lenguaje danino?**

- A. Usar la moderacion de Amazon Rekognition
- B. Usar la deteccion de toxicidad de Amazon Comprehend
- C. Usar los algoritmos integrados de la IA de Amazon SageMaker para entrenar el modelo
- D. Usar Amazon Polly para supervisar los comentarios

**✅ Respuesta correcta: B — Usar la deteccion de toxicidad de Amazon Comprehend**

**Explicacion:** Amazon Comprehend tiene una funcion especifica de **deteccion de contenido toxico** en texto, disenada exactamente para identificar lenguaje danino, abusivo o inapropiado en comentarios y redes sociales.

- **A incorrecta:** Rekognition es para analisis de imagenes y video, no texto.
- **C incorrecta:** Usar algoritmos de SageMaker requeriria entrenar un modelo propio desde cero, innecesario cuando Comprehend ya lo resuelve.
- **D incorrecta:** Amazon Polly es text-to-speech, completamente fuera de contexto.

---

### Pregunta 27
**¿Que estrategia evalua la exactitud de un modelo fundacional (FM) que se usa en las tareas de clasificacion de imagenes?**

- A. Calcular el costo total de los recursos que usa el modelo
- B. Medir la exactitud del modelo en comparacion con un conjunto de datos de referencia predefinido
- C. Contar el numero de capas de la red neuronal
- D. Evaluar la exactitud de color de las imagenes que procesa el modelo

**✅ Respuesta correcta: B — Medir la exactitud del modelo en comparacion con un conjunto de datos de referencia predefinido**

**Explicacion:** Evaluar la exactitud de un modelo de clasificacion se hace comparando sus predicciones contra un **dataset de referencia etiquetado (benchmark)**. Este es el metodo estandar de evaluacion de modelos supervisados.

- **A incorrecta:** El costo de recursos mide eficiencia economica, no precision del modelo.
- **C incorrecta:** Contar capas describe la arquitectura, no el rendimiento.
- **D incorrecta:** La exactitud de color no tiene relacion con clasificacion.

---

### Pregunta 28
**Una empresa esta utilizando un modelo de lenguaje de gran tamano (LLM) previamente entrenado para crear un chatbot que realice recomendaciones de productos. La empresa se da cuenta de que las solicitudes del LLM usan textos breves y estan escritas en un idioma especifico. La empresa quiere que las solicitudes cumplan con las expectativas de la empresa. ¿Que solucion alineara la calidad de respuesta del LLM con las expectativas de la empresa?**

- A. Ajustar la peticion
- B. Elegir un LLM de un tamano diferente
- C. Aumentar la temperatura
- D. Aumentar el valor K superior

**✅ Respuesta correcta: A — Ajustar la peticion**

**Explicacion:** Cuando el modelo no cumple las expectativas de formato, idioma o estilo, la solucion mas directa y eficiente es el **prompt engineering**: ajustar la peticion para guiar al modelo hacia el output esperado. Es la opcion de menor costo y mayor velocidad de implementacion.

- **B incorrecta:** Cambiar el tamano del LLM no garantiza mejor alineacion con un idioma o estilo especifico.
- **C incorrecta:** Aumentar la temperatura incrementa variabilidad — lo opuesto a lo que se necesita para consistencia.
- **D incorrecta:** Top-K es un parametro de sampling que no resuelve el problema de calidad en el idioma requerido.

---

### Pregunta 29
**Un especialista en IA esta desarrollando una peticion para un modelo de Amazon Titan. El modelo se aloja en Amazon Bedrock. El especialista en IA necesita una solucion para tomar datos de prueba y analizarlos para encontrar patrones y errores. Pide al modelo que "muestre su trabajo razonando paso a paso" al final de la peticion. ¿Que tecnica de ingenieria de peticiones usa el especialista en IA?**

- A. Peticiones de cadena de pensamiento
- B. Inyeccion de peticiones
- C. Peticiones zero-shot
- D. Plantillas de peticiones

**✅ Respuesta correcta: A — Peticiones de cadena de pensamiento (Chain-of-Thought)**

**Explicacion:** La frase **"muestre su trabajo razonando paso a paso"** es el marcador definitorio del chain-of-thought prompting. Esta tecnica instruye al modelo a explicitar su proceso de razonamiento antes de dar la respuesta final.

- **B incorrecta:** La inyeccion de peticiones es un ataque de seguridad, no una tecnica legitima.
- **C incorrecta:** Zero-shot solo da la instruccion sin guiar el razonamiento.
- **D incorrecta:** Las plantillas de peticiones son estructuras reutilizables, no una tecnica de razonamiento.

---

### Pregunta 30
**Una empresa debe registrar todas las solicitudes realizadas en su API de Amazon Bedrock. La empresa debe retener los registros de forma segura durante tiempo indefinido a bajo costo. ¿Que combinacion de servicio y clase de almacenamiento de AWS cumple estos requisitos? (Seleccione DOS)**

- A. AWS CloudTrail
- B. Amazon CloudWatch
- C. AWS Audit Manager
- D. Amazon S3 Intelligent-Tiering
- E. Amazon S3 Standard

**✅ Respuesta correcta: A y E — AWS CloudTrail + Amazon S3 Standard**

**Explicacion:**
- **CloudTrail** registra todas las llamadas a la API de AWS, incluyendo Amazon Bedrock — es el servicio de auditoria de API calls.
- **S3 Standard** es el destino natural para almacenar logs de auditoria de forma segura y duradera con retencion configurable.

- **B incorrecta:** CloudWatch monitorea metricas y logs operacionales, no es el registro primario de API calls.
- **C incorrecta:** Audit Manager gestiona marcos de cumplimiento, no captura logs de API directamente.
- **D incorrecta:** S3 Intelligent-Tiering optimiza costos para datos con acceso variable — innecesario para logs de auditoria que se almacenan y raramente se consultan.

---

### Pregunta 31
**Una empresa financiera usa AWS para alojar a sus modelos de IA generativa. La empresa debe generar informes para demostrar el cumplimiento de las normas internacionales de manejo de datos confidenciales de los clientes. ¿Que servicio de AWS cumple con estos requisitos?**

- A. Amazon Macie
- B. AWS Artifact
- C. AWS Secrets Manager
- D. AWS Config

**✅ Respuesta correcta: B — AWS Artifact**

**Explicacion:** **AWS Artifact** es el portal que provee acceso a informes de cumplimiento normativo y certificaciones de AWS (SOC, ISO, PCI DSS, HIPAA, etc.) para presentar a auditores y reguladores externos.

- **A incorrecta:** Macie detecta datos sensibles en S3, no genera informes de cumplimiento.
- **C incorrecta:** Secrets Manager gestiona credenciales y secretos.
- **D incorrecta:** AWS Config rastrea cambios de configuracion, no genera informes de cumplimiento normativo.

---

### Pregunta 32
**Una empresa quiere colaborar con varios institutos de investigacion para desarrollar un modelo de IA. La empresa necesita documentacion estandarizada sobre el seguimiento del desarrollo del modelo para analizar las predicciones del modelo. ¿Que solucion cumple estos requisitos?**

- A. Realizar un seguimiento de los cambios del modelo mediante Git
- B. Realizar un seguimiento de los cambios del modelo mediante Amazon Fraud Detector
- C. Realizar un seguimiento de los cambios del modelo mediante tarjetas modelo de Amazon SageMaker
- D. Realizar un seguimiento de los cambios del modelo mediante Amazon Comprehend

**✅ Respuesta correcta: C — Tarjetas modelo de Amazon SageMaker**

**Explicacion:** Las **SageMaker Model Cards** son documentacion estandarizada que registra el proposito del modelo, metricas de desempeno, sesgos conocidos, limitaciones y historial de versiones. Son ideales para colaboracion con institutos de investigacion y transparencia.

- **A incorrecta:** Git rastrea cambios de codigo, no documentacion estandarizada de modelos ML.
- **B incorrecta:** Fraud Detector es para deteccion de fraude, sin relacion con tracking de modelos.
- **D incorrecta:** Comprehend es NLP para analisis de texto, no para documentar modelos.

---

### Pregunta 33
**Una institucion financiera esta creando una solucion de IA para tomar decisiones de aprobacion de prestamos mediante el uso de un modelo fundacional (FM). Por motivos de transparencia, la empresa necesita que las decisiones de la solucion de IA sean explicables. ¿Que factor se relaciona con la explicabilidad de las decisiones de la solucion de IA?**

- A. Complejidad del modelo
- B. Tiempo de entrenamiento
- C. Numero de hiperparametros
- D. Tiempo de implementacion

**✅ Respuesta correcta: A — Complejidad del modelo**

**Explicacion:** Existe un trade-off directo entre **complejidad del modelo** y su **explicabilidad**. Modelos mas complejos (LLMs, deep neural networks) son inherentemente menos interpretables. A mayor complejidad, mas dificil explicar por que el modelo tomo una decision especifica.

- **B y D incorrectas:** El tiempo de entrenamiento e implementacion son metricas operacionales sin relacion con explicabilidad.
- **C incorrecta:** El numero de hiperparametros afecta el proceso de optimizacion, no la capacidad de explicar decisiones individuales.

---

### Pregunta 34
**Una empresa de fabricacion tiene una aplicacion que ingiere los reclamos de los consumidores de fuentes disponibles publicamente. La empresa quiere escalar esta logica en todos los mercados y lineas de productos. ¿Que ventaja ofrecen los modelos de IA generativa para este escenario?**

- A. Previsibilidad de las salidas
- B. Adaptabilidad
- C. Menor sensibilidad a los cambios en las entradas
- D. Explicabilidad

**✅ Respuesta correcta: B — Adaptabilidad**

**Explicacion:** El escenario requiere escalar la misma logica a multiples mercados y lineas de productos con variaciones en lenguaje, formato y contexto. La **adaptabilidad** de los modelos generativos les permite manejar estas variaciones sin reglas explicitas para cada caso.

- **A, C y D incorrectas:** Previsibilidad limitada, alta sensibilidad a entradas y baja explicabilidad son en realidad **desventajas** de la IA generativa, no ventajas.

---

### Pregunta 35
**Una empresa esta desarrollando un sistema de IA para ayudar al equipo de administracion de riesgos a decidir las designaciones de prestamos para diferentes grupos demograficos. ¿Que debe hacer el banco para desarrollar un modelo de ML imparcial?**

- A. Reducir el tamano del conjunto de datos de entrenamiento
- B. Asegurar que las predicciones del modelo de ML sean consistentes con los resultados historicos
- C. Crear un modelo de ML diferente para cada grupo demografico
- D. Medir el desequilibrio de clases en el conjunto de datos de entrenamiento. Adaptar el proceso de entrenamiento en consecuencia.

**✅ Respuesta correcta: D — Medir el desequilibrio de clases en el conjunto de datos de entrenamiento. Adaptar el proceso de entrenamiento en consecuencia.**

**Explicacion:** El sesgo mas comun en modelos de credito es el **desequilibrio de clases** — algunos grupos demograficos tienen menos representacion en los datos historicos. La solucion es medirlo y corregirlo (oversampling, undersampling, class weights).

- **A incorrecta:** Reducir el dataset empeora la representatividad.
- **B incorrecta:** Usar resultados historicos como referencia perpetua los sesgos historicos.
- **C incorrecta:** Modelos separados por grupo demografico es discriminacion por diseno.

---

### Pregunta 36
**Una empresa de investigacion implemento un chatbot mediante un modelo fundacional (FM) de Amazon Bedrock. El chatbot busca respuestas a las preguntas de una gran base de datos de textos de investigacion. Tras varios intentos de ingenieria de peticiones, la empresa descubre que el FM funciona mal debido a la complejidad de los terminos cientificos de los articulos de investigacion. ¿Que puede hacer la empresa para mejorar el rendimiento del chatbot?**

- A. Usar peticiones few-shot para definir como el FM puede responder a las preguntas
- B. Usar el ajuste de adaptacion de dominio para adaptar el FM a los terminos cientificos complejos
- C. Cambiar los parametros de inferencia del FM
- D. Limpiar los datos del trabajo de investigacion para eliminar terminos cientificos complejos

**✅ Respuesta correcta: B — Usar el ajuste de adaptacion de dominio para adaptar el FM a los terminos cientificos complejos**

**Explicacion:** El problema es que el FM no maneja la **terminologia cientifica especializada**. La solucion es el **domain adaptation fine-tuning**: ajustar el modelo con datos del dominio cientifico para que aprenda ese vocabulario y contexto especializado.

- **A incorrecta:** Few-shot ayuda marginalmente pero es insuficiente para terminologia cientifica extensa y compleja.
- **C incorrecta:** Cambiar parametros de inferencia no ensena al modelo nuevos terminos.
- **D incorrecta:** Eliminar los terminos cientificos destruye el contenido que el chatbot necesita manejar.

---

### Pregunta 37
**Una empresa quiere crear una nueva solucion mediante AWS Glue. La empresa tiene una experiencia minima en programacion con AWS Glue. ¿Que servicio de AWS puede ayudar a la empresa a usar AWS Glue?**

- A. Amazon Q Developer
- B. AWS Config
- C. Amazon Personalize
- D. Amazon Comprehend

**✅ Respuesta correcta: A — Amazon Q Developer**

**Explicacion:** **Amazon Q Developer** es el asistente de IA de AWS para desarrolladores. Puede generar codigo para AWS Glue, explicar como usarlo y asistir a usuarios con poca experiencia directamente en el IDE o consola de AWS.

- **B incorrecta:** AWS Config rastrea configuraciones de recursos, no asiste con programacion.
- **C incorrecta:** Amazon Personalize es para recomendaciones personalizadas.
- **D incorrecta:** Amazon Comprehend es NLP para analisis de texto.

---

### Pregunta 38
**Una tienda de comestibles quiere crear un chatbot para ayudar a los clientes a encontrar productos en la tienda. El chatbot debe consultar el inventario en tiempo real y proporcionar la ubicacion del producto en la tienda. ¿Que tecnica de ingenieria de peticiones debe usar la tienda para crear el chatbot?**

- A. Peticiones zero-shot
- B. Peticiones few-shot
- C. Peticiones de menor a mayor
- D. Peticiones de razonamiento y actuacion (ReAct)

**✅ Respuesta correcta: D — Peticiones de razonamiento y actuacion (ReAct)**

**Explicacion:** El chatbot debe **consultar el inventario en tiempo real** (herramienta externa). ReAct combina razonamiento con llamadas a herramientas externas (APIs, bases de datos), permitiendo que el modelo actue sobre informacion en tiempo real.

- **A y B incorrectas:** Zero-shot y few-shot generan respuestas solo con el conocimiento del modelo, sin acceso a sistemas externos.
- **C incorrecta:** Least-to-most prompting descompone problemas en partes pero no interactua con sistemas externos.

---

### Pregunta 39
**¿Que son los tokens en el contexto de los modelos de IA generativa?**

- A. Los tokens son las unidades basicas de entrada y salida con las que opera un modelo de IA generativa, que representan palabras, subpalabras u otras unidades linguisticas.
- B. Los tokens son las representaciones matematicas de las palabras o los conceptos que se usan en los modelos de IA generativa.
- C. Los tokens son las ponderaciones preentrenadas de un modelo de IA generativa que se ajustan para realizar tareas especificas.
- D. Los tokens son las peticiones o instrucciones especificas que se dan a un modelo de IA generativa para generar resultados.

**✅ Respuesta correcta: A — Los tokens son las unidades basicas de entrada y salida con las que opera un modelo de IA generativa**

**Explicacion:** Los **tokens** son la unidad minima de procesamiento de texto en un LLM. Pueden ser palabras completas, partes de palabras (subpalabras) o caracteres individuales, dependiendo del tokenizador utilizado.

- **B incorrecta:** Describe los embeddings, no los tokens.
- **C incorrecta:** Describe los pesos (weights) del modelo.
- **D incorrecta:** Describe los prompts o peticiones.

---

### Pregunta 40
**Una editorial creo una solucion basada en RAG para ofrecer a sus usuarios la posibilidad de interactuar con el contenido publicado. Todos los dias se publica contenido nuevo. La empresa quiere ofrecer una experiencia casi en tiempo real a los usuarios. ¿Que pasos en la canalizacion de RAG deberia implementar la empresa mediante el procesamiento por lotes sin conexion? (Seleccione DOS)**

- A. Generacion de incrustaciones de contenido
- B. Generacion de incrustaciones para consultas de usuarios
- C. Creacion del indice de busqueda
- D. Recuperacion de contenido relevante
- E. Generacion de respuestas para el usuario

**✅ Respuesta correcta: A y C — Generacion de incrustaciones de contenido + Creacion del indice de busqueda**

**Explicacion:** El pipeline RAG tiene dos fases:
- **Fase offline (batch):** Generar embeddings del contenido (A) y crear el indice de busqueda vectorial (C). Estos se ejecutan sin conexion del usuario, procesando el contenido nuevo diariamente.
- **Fase online (tiempo real):** Los pasos B, D y E ocurren cuando el usuario hace una consulta.

---

### Pregunta 41
**Una empresa necesita entrenar un modelo de ML para clasificar imagenes de diferentes tipos de animales. La empresa tiene un gran conjunto de datos de imagenes etiquetadas y sin etiquetar a traves del dataset. ¿Que tipo de aprendizaje debe utilizar la empresa para entrenar el modelo?**

- A. Aprendizaje supervisado
- B. Aprendizaje no supervisado
- C. Aprendizaje por refuerzo
- D. Aprendizaje activo

**✅ Respuesta correcta: A — Aprendizaje supervisado**

**Explicacion:** El requisito es clasificar imagenes de animales con un dataset de imagenes **etiquetadas**. Datos etiquetados + clasificacion = aprendizaje supervisado. Es la combinacion mas directa en ML.

- **B incorrecta:** El aprendizaje no supervisado trabaja con datos sin etiquetar para descubrir patrones, no para clasificar.
- **C incorrecta:** El aprendizaje por refuerzo usa recompensas/penalizaciones, no datos etiquetados.
- **D incorrecta:** El aprendizaje activo selecciona que datos etiquetar; no entrena directamente con datos ya etiquetados.

---

### Pregunta 42
**Una empresa esta desarrollando un modelo de ML para analizar los datos archivados. La empresa debe realizar inferencias sobre grandes conjuntos de datos de varios GB de tamano. La empresa necesita acceder inmediatamente a las predicciones del modelo. ¿Que opcion de inferencia de la IA de Amazon SageMaker cumplira estos requisitos?**

- A. Inferencia por lotes
- B. Inferencia en tiempo real
- C. Inferencia sin servidor
- D. Inferencia asincronica

**✅ Respuesta correcta: A — Inferencia por lotes (Batch Transform)**

**Explicacion:** El escenario tiene datos **archivados** de gran tamano (varios GB) que se procesan de una vez. **Batch Transform** de SageMaker procesa grandes volumenes de datos sin endpoint activo permanente y almacena los resultados. Es el modo correcto cuando los datos son estaticos y el volumen es grande.

> Nota: aunque el enunciado dice "acceder inmediatamente a las predicciones", en el contexto de datos archivados esto significa que las predicciones esten disponibles al completar el job, no latencia de milisegundos por solicitud.

- **B incorrecta:** Inferencia en tiempo real es para predicciones individuales con baja latencia.
- **C incorrecta:** Inferencia sin servidor es para cargas esporadicas, no grandes volumenes archivados.
- **D incorrecta:** Inferencia asincronica es para payloads grandes individuales con latencia tolerada.

---

### Pregunta 43
**Un hospital esta desarrollando un sistema de IA para ofrecer recomendaciones de tratamiento personalizadas a los pacientes. El sistema de ML debe proporcionar la privacidad de los pacientes y la informacion de seguridad de los registros. Los medicos y los pacientes pueden acceder a la informacion. ¿Que principio de diseno centrado en el ser humano presenta este escenario?**

- A. Explicabilidad
- B. Privacidad y seguridad
- C. Equidad
- D. Gobernanza de datos

**✅ Respuesta correcta: B — Privacidad y seguridad**

**Explicacion:** El escenario enfatiza la proteccion de datos medicos de pacientes y el control de acceso (medicos y pacientes pueden acceder). Los datos medicos son altamente sensibles y estan sujetos a regulaciones estrictas (HIPAA). El principio dominante es **privacidad y seguridad**.

- **A incorrecta:** La explicabilidad es importante pero secundaria al control de acceso en este escenario.
- **C incorrecta:** La equidad aplica mas a sesgos en las recomendaciones.
- **D incorrecta:** La gobernanza de datos es un marco mas amplio; el principio especifico aqui es privacidad y seguridad.

---

### Pregunta 44
**Una empresa medica esta personalizando un modelo fundacional (FM) con el fin de generar diagnosticos. La empresa necesita que el modelo sea transparente y justificable para cumplir con los requisitos reglamentarios. ¿Que solucion cumplira con estos requisitos?**

- A. Configurar la seguridad y el cumplimiento mediante Amazon Inspector
- B. Generar metricas, informes y ejemplos sencillos con Amazon SageMaker Clarify
- C. Cifrar y proteger los datos de entrenamiento con Amazon Macie
- D. Reunir mas datos. Usar Amazon Rekognition para agregar etiquetas personalizadas a los datos.

**✅ Respuesta correcta: B — Generar metricas, informes y ejemplos sencillos con Amazon SageMaker Clarify**

**Explicacion:** El requisito es **transparencia y explicabilidad** para cumplimiento regulatorio en diagnosticos medicos. SageMaker Clarify genera exactamente eso: metricas de sesgo, explicaciones de predicciones e informes de explicabilidad.

- **A incorrecta:** Inspector evalua vulnerabilidades de infraestructura, no explicabilidad de modelos.
- **C incorrecta:** Macie detecta datos sensibles en S3, no genera explicabilidad del modelo.
- **D incorrecta:** Rekognition para etiquetado es preparacion de datos, no explicabilidad del modelo.

---

### Pregunta 45
**Una empresa de redes sociales quiere usar un modelo de lenguaje de gran tamano (LLM) para resumir mensajes. La empresa eligio algunos LLM que estan disponibles en Amazon Bedrock. La empresa quiere comparar la toxicidad de salida generada por estos modelos. ¿Que estrategia ofrece a la empresa la posibilidad de evaluar los LLM con la MENOR sobrecarga operativa?**

- A. Evaluacion colaborativa
- B. Evaluacion automatica del modelo
- C. Evaluacion del modelo con trabajadores humanos
- D. Aprendizaje por refuerzo a partir de la retroalimentacion humana (RLHF)

**✅ Respuesta correcta: B — Evaluacion automatica del modelo**

**Explicacion:** La evaluacion automatica usa metricas predefinidas y modelos juez sin intervencion humana. Es la opcion de **menor sobrecarga operativa** para comparar multiples LLMs en Bedrock.

- **A incorrecta:** Evaluacion colaborativa implica multiples equipos coordinados — mayor overhead.
- **C incorrecta:** Evaluacion con trabajadores humanos requiere revisores manuales, costosa y lenta.
- **D incorrecta:** RLHF es un proceso completo de reentrenamiento con feedback humano — el mas costoso operacionalmente.

---

### Pregunta 46
**Una empresa quiere crear una aplicacion interactiva para ninos que genere historias nuevas basadas en historias clasicas. La empresa quiere usar Amazon Bedrock y debe asegurarse de que los temas sean apropiados para ninos. ¿Que servicio o caracteristica de AWS cumple con este requisito?**

- A. Amazon Rekognition
- B. Zonas de juego de Amazon Bedrock
- C. Barreras de proteccion para Amazon Bedrock
- D. Agentes para Amazon Bedrock

**✅ Respuesta correcta: C — Barreras de proteccion para Amazon Bedrock (Guardrails)**

**Explicacion:** Las **Guardrails de Bedrock** permiten configurar filtros de contenido, temas denegados y restricciones de seguridad para garantizar que el output sea apropiado para el publico objetivo (en este caso, ninos).

- **A incorrecta:** Rekognition analiza imagenes, no controla el contenido de texto generado.
- **B incorrecta:** Los Playgrounds de Bedrock son entornos de prueba para desarrolladores, no controles de produccion.
- **D incorrecta:** Los Agentes de Bedrock orquestan tareas complejas pero no filtran contenido por apropiado para ninos.

---

### Pregunta 47
**Una empresa de servicios de alimentos desea desarrollar un modelo de ML para ayudar a reducir el desperdicio diario de alimentos y aumentar los ingresos sin overlap. La empresa necesita desarrollar un modelo de ML que pronostique la cantidad del modelo. ¿Que solucion cumple estos requisitos?**

- A. Usar la IA de Amazon SageMaker e iterar con los datos mas recientes
- B. Usar Amazon Personalize e iterar con datos historicos
- C. Usar Amazon CloudWatch para analizar los pedidos de los clientes
- D. Usar Amazon Rekognition para optimizar el modelo

**✅ Respuesta correcta: A — Usar la IA de Amazon SageMaker e iterar con los datos mas recientes**

**Explicacion:** El requisito es construir y refinar un modelo predictivo de demanda de alimentos (regresion/forecasting). SageMaker es la plataforma correcta para entrenar, evaluar y re-entrenar modelos ML con datos frescos de forma iterativa.

- **B incorrecta:** Amazon Personalize es para recomendaciones personalizadas, no prediccion de cantidades de demanda.
- **C incorrecta:** CloudWatch monitorea metricas operacionales, no construye modelos predictivos.
- **D incorrecta:** Rekognition es para analisis de imagenes, no forecasting de demanda.

---

### Pregunta 48
**Una empresa de servicios de alimentos desea recopilar un conjunto de datos para predecir las preferencias alimentarias de los clientes. La empresa quiere asegurarse de que todos los grupos demograficos se incluyan en los datos. ¿Que caracteristica del conjunto de datos presenta este escenario?**

- A. Exactitud
- B. Diversidad
- C. Sesgo de actualidad
- D. Fiabilidad

**✅ Respuesta correcta: B — Diversidad**

**Explicacion:** El requisito de que **todos los grupos demograficos esten incluidos** describe la **diversidad** del dataset. Un dataset diverso asegura representacion equitativa para evitar sesgos demograficos en el modelo.

- **A incorrecta:** La exactitud se refiere a la correctitud de los valores en los datos.
- **C incorrecta:** El sesgo de actualidad es cuando los datos mas recientes tienen mayor peso que los historicos.
- **D incorrecta:** La fiabilidad se refiere a la consistencia y confiabilidad de los datos en el tiempo.

---

### Pregunta 49
**Un proveedor educativo esta creando una aplicacion de preguntas y respuestas que usa un modelo de IA generativa para explicar conceptos complejos. El proveedor educativo quiere cambiar automaticamente el estilo de la respuesta del modelo en funcion de la persona que formula la pregunta. ¿Cual solucion cumplira estos requisitos con el MENOR esfuerzo de implementacion?**

- A. Ajustar el modelo mediante el uso de datos de entrenamiento adicionales que sean representativos de los diferentes rangos de edad
- B. Agregar una descripcion de rol al contexto de la peticion que indique al modelo el rango de edad al que debe dirigirse
- C. Usar el razonamiento en cadena de pensamiento para deducir cuales son el estilo y la complejidad correctos
- D. Resumir el texto de la respuesta segun la edad del usuario para que los usuarios mas jovenes reciban respuestas mas cortas

**✅ Respuesta correcta: B — Agregar una descripcion de rol al contexto de la peticion**

**Explicacion:** La solucion de **menor esfuerzo** es el prompt engineering con role description: incluir en el system prompt que el modelo adapte su lenguaje y complejidad segun el rango de edad indicado en cada peticion. No requiere codigo adicional ni reentrenamiento.

- **A incorrecta:** Fine-tuning con datos adicionales requiere entrenamiento — mayor esfuerzo.
- **C incorrecta:** Chain-of-thought anade complejidad de razonamiento innecesaria para este caso.
- **D incorrecta:** Resumir la respuesta es un paso adicional de post-procesamiento que agrega complejidad al pipeline.

---

### Pregunta 50
**Una empresa esta implementando agentes inteligentes para ofrecer experiencias de busqueda conversacional a sus clientes. La empresa necesita un servicio de base de datos que almacene los datos de incrustaciones de un modelo de IA generativa como vectores en la base de datos. ¿Que servicio de AWS cumplira estos requisitos?**

*(Misma pregunta que #23 — variante con misma respuesta)*

**✅ Respuesta correcta: B — Amazon Aurora PostgreSQL**

**Explicacion:** Aurora PostgreSQL con la extension **pgvector** es la solucion de AWS para almacenar y consultar vectores de embeddings en una base de datos relacional. Es el vector store nativo de AWS para arquitecturas RAG.

---

### Pregunta 51
**Una empresa esta creando una aplicacion interactiva para ninos que use IA generativa. Durante la fase piloto, el uso es bajo y el rendimiento de la aplicacion no es un problema. La empresa no puede predecir el uso de la aplicacion una vez que esta se implemento por completo y desea minimizar los costos de aplicacion. ¿Que solucion cumplira con estos requisitos?**

- A. Usar instancias de Amazon EC2 impulsadas por GPU
- B. Usar Amazon Bedrock con rendimiento aprovisionado
- C. Usar Amazon Bedrock con rendimiento bajo demanda
- D. Usar Amazon SageMaker JumpStart

**✅ Respuesta correcta: C — Usar Amazon Bedrock con rendimiento bajo demanda**

**Explicacion:** Durante una fase piloto con **uso bajo e impredecible**, el modelo on-demand de Bedrock cobra solo por tokens consumidos sin compromisos de capacidad. Es la opcion de **menor costo** para uso esporadico.

- **A incorrecta:** EC2 con GPU implica pagar instancias corriendo continuamente.
- **B incorrecta:** Rendimiento aprovisionado requiere comprometer capacidad con pago fijo — justificado solo para produccion de alto volumen predecible.
- **D incorrecta:** SageMaker JumpStart implica gestionar endpoints con costo base permanente.

---

### Pregunta 52
**Una empresa crea una solucion mediante el uso de la IA generativa. La solucion usa modelos de lenguaje de gran tamano (LLM) para traducir manuales de formacion del ingles a otros idiomas. La empresa quiere evaluar la exactitud de la solucion mediante el analisis del texto generado para los manuales. ¿Que estrategia de evaluacion del modelo cumple estos requisitos?**

- A. Estudio de evaluacion bilingue (BLEU)
- B. Error cuadratico medio (RMSE)
- C. Sujeto orientado a la revocacion para la evaluacion de resumenes (ROUGE)
- D. Puntuacion de F1

**✅ Respuesta correcta: A — Estudio de evaluacion bilingue (BLEU)**

**Explicacion:** **BLEU** (Bilingual Evaluation Understudy) es la metrica estandar para evaluar la calidad de **traducciones automaticas**. Compara n-gramas del texto traducido contra referencias humanas.

- **B incorrecta:** RMSE es para regresion (valores numericos continuos), no traduccion.
- **C incorrecta:** ROUGE es para evaluacion de **resumenes** de texto, no traducciones.
- **D incorrecta:** F1 es para clasificacion y extraccion de informacion, no traduccion.

---

### Pregunta 53
**Una empresa creo un chatbot que puede responder a preguntas en lenguaje natural con imagenes. La empresa quiere asegurarse de que el chatbot no devuelva imagenes inapropiadas o no deseadas. ¿Que solucion cumplira con estos requisitos?**

- A. Implementar las API de moderacion
- B. Volver a entrenar el modelo con un conjunto de datos publico general
- C. Realizar la validacion del modelo
- D. Automatizar la integracion de comentarios de los usuarios

**✅ Respuesta correcta: A — Implementar las API de moderacion**

**Explicacion:** Las **APIs de moderacion de contenido** (como las de Amazon Rekognition para imagenes) filtran contenido inapropiado en tiempo real antes de que llegue al usuario. Es la solucion directa para este caso de uso.

- **B incorrecta:** Reentrenar con datos generales no garantiza que el modelo evite imagenes inapropiadas.
- **C incorrecta:** La validacion del modelo es una evaluacion puntual, no un control en tiempo real.
- **D incorrecta:** Los comentarios de usuarios son retroalimentacion post-facto, no prevencion activa.

---

### Pregunta 54
**Una empresa tiene terabytes de datos en una base de datos que puede usar para el analisis empresarial. La empresa quiere crear una aplicacion basada en ML que pueda consultar datos de forma natural que los empleados que tienen una experiencia minima con la tecnologia puedan usar. ¿Que solucion cumple estos requisitos?**

- A. Transformadores generativos preentrenados (GPT)
- B. Red neuronal residual
- C. Maquina de vector de soporte
- D. WaveNet

**✅ Respuesta correcta: A — Transformadores generativos preentrenados (GPT)**

**Explicacion:** El requisito es una interfaz de **lenguaje natural** para consultar datos, accesible para usuarios con poca experiencia tecnica. Los modelos GPT (transformers preentrenados) son la arquitectura que habilita interfaces conversacionales en lenguaje natural.

- **B incorrecta:** ResNet (red neuronal residual) es para vision por computadora.
- **C incorrecta:** SVM es clasificacion tradicional de ML, no lenguaje natural conversacional.
- **D incorrecta:** WaveNet es para generacion de audio/voz, no consultas en lenguaje natural.

---

### Pregunta 55
**Una empresa desarrollo un modelo de aprendizaje profundo para la deteccion de objetos y lo implemento en la produccion. ¿Que proceso de IA ocurre cuando el modelo analiza una nueva imagen para identificar objetos?**

- A. Entrenamiento
- B. Inferencia
- C. Implementacion del modelo
- D. Correccion del sesgo

**✅ Respuesta correcta: B — Inferencia**

**Explicacion:** Cuando el modelo **ya entrenado y desplegado** analiza una nueva imagen para identificar objetos, ese proceso es **inferencia**: aplicar el modelo a datos nuevos para generar predicciones en produccion.

- **A incorrecta:** El entrenamiento es cuando el modelo aprende de datos historicos.
- **C incorrecta:** La implementacion es el acto de desplegar el modelo, no el proceso de analisis.
- **D incorrecta:** La correccion del sesgo es una etapa de mejora del modelo.

---

### Pregunta 56
**¿Como pueden las empresas usar modelos de lenguaje de gran tamano (LLM) de forma segura en Amazon Bedrock?**

- A. Configurar los roles y las politicas de AWS IAM mediante el acceso con privilegios minimos
- B. Habilitar AWS Audit Manager para que realice trabajos automaticos de evaluacion del modelo
- C. Habilitar los trabajos automaticos de evaluacion del modelo de Amazon Bedrock
- D. Utilizar los Registros de Amazon CloudWatch para hacer que los modelos sean explicables y suprimirlos

**✅ Respuesta correcta: A — Configurar los roles y las politicas de AWS IAM mediante el acceso con privilegios minimos**

**Explicacion:** El principio de **minimo privilegio** con IAM es la practica de seguridad fundamental: garantiza que solo los usuarios, roles y servicios autorizados puedan acceder a los modelos y recursos de Bedrock, limitando la superficie de ataque.

- **B incorrecta:** Audit Manager genera informes de cumplimiento, no controla el acceso seguro.
- **C incorrecta:** Los trabajos de evaluacion miden calidad del modelo, no seguridad de acceso.
- **D incorrecta:** CloudWatch Logs provee observabilidad pero no controla el acceso seguro al servicio.

---

### Pregunta 57
**Una empresa almacena millones de documentos PDF en un bucket de Amazon S3. La empresa necesita extraer el texto de los PDF, generar resumenes del texto e indexarlos para realizar busquedas rapidas. ¿Que combinacion de servicios de AWS cumplira estos requisitos? (Seleccione DOS)**

- A. Amazon Translate
- B. Amazon Bedrock
- C. Amazon Transcribe
- D. Amazon Polly
- E. Amazon Textract

**✅ Respuesta correcta: B y E — Amazon Bedrock + Amazon Textract**

**Explicacion:**
- **Amazon Textract** extrae texto de documentos PDF (incluyendo tablas y formularios) con precision superior al OCR tradicional.
- **Amazon Bedrock** usa un LLM para generar los resumenes y puede indexar el contenido para busqueda semantica rapida.

- **A incorrecta:** Translate traduce idiomas, no extrae texto de PDFs.
- **C incorrecta:** Transcribe convierte audio a texto, no extrae texto de PDFs.
- **D incorrecta:** Polly convierte texto a voz, completamente fuera de contexto.

---

### Pregunta 58
**Una empresa esta desarrollando una aplicacion de asistente editorial que usa IA generativa. Durante la fase piloto, el uso es bajo y el rendimiento de la aplicacion no es un problema. La empresa no puede predecir el uso de la aplicacion una vez implementada por completo y desea minimizar los costos. ¿Que solucion cumplira con estos requisitos?**

*(Variante de la pregunta #51)*

**✅ Respuesta correcta: C — Usar Amazon Bedrock con rendimiento bajo demanda**

**Explicacion:** Para uso bajo e impredecible con objetivo de minimizar costos, el modelo **on-demand** de Bedrock es el correcto: pago por tokens, sin compromisos, sin costo base permanente.

---

### Pregunta 59
**Una empresa quiere crear un chatbot para responder a las preguntas de los empleados sobre las politicas de la empresa. Las politicas de la empresa se actualizan con frecuencia. El chatbot debe reflejar los cambios casi en tiempo real. La empresa quiere elegir un modelo de lenguaje de gran tamano (LLM). ¿Que solucion cumple estos requisitos?**

- A. Ajustar un LLM al texto de la politica de la empresa mediante Amazon SageMaker
- B. Seleccionar un modelo fundacional (FM) de Amazon Bedrock para crear una aplicacion
- C. Crear un flujo de trabajo de generacion aumentada por recuperacion (RAG) mediante las bases de conocimiento de Amazon Bedrock
- D. Usar Amazon Q Business para crear una Q App personalizada

**✅ Respuesta correcta: C — Crear un flujo de trabajo RAG mediante las bases de conocimiento de Amazon Bedrock**

**Explicacion:** El factor clave es que las politicas **se actualizan frecuentemente**. Con RAG, cuando cambia una politica solo se actualiza el documento en la Knowledge Base — sin reentrenar el modelo. El LLM siempre recupera la version mas reciente.

- **A incorrecta:** Fine-tuning con SageMaker es inviable para contenido que cambia frecuentemente — habria que reentrenar cada vez.
- **B incorrecta:** Un FM generico sin Knowledge Base no tiene acceso a las politicas corporativas actualizadas.
- **D incorrecta:** Q Business es valido pero RAG con Bedrock Knowledge Bases es la respuesta mas precisa para este flujo especifico.

---

### Pregunta 60
**Una empresa de servicios financieros debe asegurarse de que su chatbot generativo impulsado por IA proporcione respuestas objetivas para la conformidad normativa. ¿Que solucion evita que el modelo fundacional (FM) subyacente tenga alucinaciones?**

- A. Usar AWS Config para consultar los metadatos de cumplimiento mediante lenguaje natural
- B. Configurar la barrera de proteccion de Amazon Bedrock para evaluar las entradas de los usuarios y las respuestas del modelo
- C. Usar Amazon Fraud Detector para detectar actividades en linea potencialmente fraudulentas
- D. Utilizar AWS Audit Manager para preparar informes de cumplimiento y auditoria de TI

**✅ Respuesta correcta: B — Configurar la barrera de proteccion de Amazon Bedrock (Guardrails)**

**Explicacion:** Las **Guardrails de Bedrock** pueden configurarse para filtrar respuestas no fundamentadas, bloquear temas fuera del alcance y garantizar que las respuestas sean objetivas — directamente orientadas a reducir alucinaciones en entornos financieros regulados.

- **A incorrecta:** AWS Config rastrea configuraciones de infraestructura, no controla el output del modelo.
- **C incorrecta:** Fraud Detector detecta fraude transaccional, no alucinaciones del LLM.
- **D incorrecta:** Audit Manager genera informes de cumplimiento, no controla la calidad del output del FM.

---

### Pregunta 61
**Un hospital esta desarrollando un sistema de IA para ofrecer recomendaciones de tratamiento. El sistema debe mantener la privacidad de los pacientes y todos los datos de los pacientes no deben salir del pais en el que se encuentran. ¿Que estrategia de gobernanza de datos garantizara el cumplimiento y protegera la privacidad de los pacientes?**

- A. Residencia de datos
- B. Calidad de datos
- C. Descubrimiento de datos
- D. Enriquecimiento de datos

**✅ Respuesta correcta: A — Residencia de datos**

**Explicacion:** La **residencia de datos** garantiza que los datos permanezcan dentro de una jurisdiccion geografica especifica (en este caso, el pais donde se encuentran los pacientes). Es el requisito clave para cumplir con regulaciones locales de privacidad en salud.

- **B incorrecta:** La calidad de datos trata la precision y completitud, no la ubicacion geografica.
- **C incorrecta:** El descubrimiento de datos identifica que datos existen, no donde deben residir.
- **D incorrecta:** El enriquecimiento de datos agrega informacion adicional a los datos existentes.

---

### Pregunta 62
**Una empresa medica esta personalizando un modelo fundacional (FM) con el fin de generar diagnosticos. La empresa necesita que el modelo sea transparente y justificable para cumplir con los requisitos reglamentarios. ¿Que solucion cumplira con estos requisitos?**

*(Variante de pregunta #44)*

**✅ Respuesta correcta: B — Generar metricas, informes y ejemplos con Amazon SageMaker Clarify**

**Explicacion:** SageMaker Clarify es el servicio especifico para transparencia y explicabilidad de modelos ML en AWS. Genera metricas de sesgo, explicaciones de predicciones (SHAP values, feature importance) e informes para reguladores.

---

### Pregunta 63
**Una empresa quiere colaborar con varios institutos de investigacion para desarrollar un modelo de IA. La empresa quiere realizar un seguimiento de los cambios del modelo. ¿Que solucion cumple estos requisitos?**

*(Variante de pregunta #32)*

**✅ Respuesta correcta: C — Tarjetas modelo de Amazon SageMaker**

**Explicacion:** Las SageMaker Model Cards documentan el modelo de forma estandarizada e incluyen historial de cambios, metricas y limitaciones. Son ideales para colaboracion inter-institucional y seguimiento de versiones del modelo.

---

### Pregunta 64
**Un grupo de investigacion quiere probar diferentes modelos de IA generativa para crear articulos de investigacion. El grupo de investigacion establece una flota y métricas de criterio con una estandarizada. El grupo de investigacion quiere usar un equipo de cientificos para evaluar los resultados. ¿Que solucion cumple estos requisitos?**

- A. Usar la evaluacion automatica en Amazon Personalize
- B. Usar la moderacion de contenido en Amazon Rekognition
- C. Usar la evaluacion del modelo en Amazon Bedrock
- D. Usar el analisis de sentimiento en Amazon Comprehend

**✅ Respuesta correcta: C — Usar la evaluacion del modelo en Amazon Bedrock**

**Explicacion:** Amazon Bedrock tiene una funcionalidad nativa de **Model Evaluation** que permite comparar diferentes FMs usando evaluadores humanos (equipo de cientificos) o automaticos, con metricas estandarizadas. Es exactamente lo que describe el escenario.

- **A incorrecta:** Personalize es para recomendaciones, no evaluacion de modelos generativos.
- **B incorrecta:** Rekognition Moderation es para imagenes, no evaluacion de FMs.
- **D incorrecta:** Comprehend analiza sentimiento en texto, no evalua multiples modelos comparativamente.

---

### Pregunta 65
**Una empresa medica esta personalizando un modelo fundacional (FM) con el fin de generar diagnosticos. La empresa necesita procesar los registros estructurados de los pacientes, extraer informacion relevante y generar resumenes clinicos. ¿Que solucion cumplira con estos requisitos?**

- A. Usar Amazon Comprehend Medical para extraer las relaciones y entidades medicas relevantes. Aplicar una logica basada en reglas para estructurar y dar formato a los resumenes.
- B. Usar Amazon Personalize para analizar los patrones de participacion de los pacientes. Integrar la salida con una herramienta de resumen de textos de uso general.
- C. Usar Amazon Textract para convertir documentos escaneados en texto digital. Disenar un sistema de extraccion de palabras clave para generar resumenes.
- D. Implementar Amazon Kendra para proporcionar un indice de busqueda de registros medicos. Usar un sistema basado en plantillas para dar formato a los resumenes.

**✅ Respuesta correcta: A — Amazon Comprehend Medical + logica basada en reglas**

**Explicacion:** **Comprehend Medical** es el servicio especializado para extraer entidades medicas (diagnosticos, medicamentos, procedimientos, relaciones clinicas) de textos medicos. Es el servicio correcto para procesar registros electronicos de salud (EHR) y generar resumenes clinicos estructurados.

- **B incorrecta:** Personalize es para recomendaciones de contenido, no analisis de registros medicos.
- **C incorrecta:** Textract extrae texto de documentos escaneados pero no entiende entidades medicas ni relaciones clinicas.
- **D incorrecta:** Kendra es busqueda empresarial, no extraccion de informacion clinica estructurada.

---

## RESUMEN DE CONCEPTOS CLAVE

### Servicios AWS — Cuando usar cada uno

| Necesidad | Servicio Correcto |
|-----------|------------------|
| Clasificar texto, detectar toxicidad | Amazon Comprehend |
| Procesar registros medicos | Amazon Comprehend Medical |
| Detectar sesgo y explicar predicciones | SageMaker Clarify |
| Monitorear calidad del modelo en produccion | SageMaker Model Monitor |
| Documentar modelos para transparencia | SageMaker Model Cards |
| Modelos fundacionales gestionados | Amazon Bedrock |
| Control de contenido en produccion | Bedrock Guardrails |
| RAG con documentos corporativos | Bedrock Knowledge Bases |
| Agentes con herramientas externas | Bedrock Agents |
| Vector store para embeddings | Aurora PostgreSQL (pgvector) |
| Extraer texto de PDFs/documentos | Amazon Textract |
| Analizar imagenes y detectar objetos | Amazon Rekognition |
| Asistencia de codigo AWS | Amazon Q Developer |
| Chatbot empresarial | Amazon Q Business |
| Auditoria de API calls | AWS CloudTrail |
| Informes de cumplimiento normativo | AWS Artifact |
| Monitoreo de rendimiento escalable | Amazon CloudWatch |
| Deteccion de datos sensibles en S3 | Amazon Macie |
| Recomendaciones personalizadas | Amazon Personalize |

### Tecnicas de Prompting — Identificacion rapida

| Senal en el enunciado | Tecnica |
|----------------------|---------|
| "Sin ejemplos, solo instruccion" | Zero-shot |
| "Con ejemplos antes de la tarea" | Few-shot |
| "Paso a paso / muestre su razonamiento" | Chain-of-thought |
| "Consultar sistema externo en tiempo real" | ReAct |
| "Adaptar estilo segun perfil de usuario" | Role description |
| "Saltarse restricciones del modelo" | Inyeccion (ataque) |

### Metricas — Cuando usar cada una

| Tarea | Metrica |
|-------|---------|
| Clasificacion | Exactitud (Accuracy), F1 |
| Regresion | RMSE, R2 |
| Traduccion | BLEU |
| Resumenes de texto | ROUGE |
| Velocidad en produccion | Tiempo medio de respuesta |
| Satisfaccion del usuario | CSAT |

---

*Documento generado para preparacion del examen AWS Certified AI Practitioner AIF-C01*  
*Rodrigo Aguilar — Cloud Architect & AWS Authorized Instructor LATAM*
