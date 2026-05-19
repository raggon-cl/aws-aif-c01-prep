# AWS Certified AI Practitioner — AIF-C01

![AWS](https://img.shields.io/badge/AWS-Certified-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![IA](https://img.shields.io/badge/AI-Practitioner-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)
![Idioma](https://img.shields.io/badge/Idioma-Español-blue?style=for-the-badge)
![Estado](https://img.shields.io/badge/Estado-Activo-brightgreen?style=for-the-badge)

> Material de preparación completo para el examen **AWS Certified AI Practitioner (AIF-C01)** en español.  
> Elaborado por **Rodrigo Aguilar** — Cloud Architect & AWS Authorized Instructor LATAM.

---

## 📋 Contenido del Repositorio

```
aws-aif-c01-prep/
├── README.md                          ← Este archivo
└── guia-teorica/
    └── sustento-teorico-completo.md  ← Marco teórico completo AIF-C01
```

---

## 📚 Guia Teorica

El archivo [`guia-teorica/sustento-teorico-completo.md`](./guia-teorica/sustento-teorico-completo.md) cubre **13 capitulos** con todo el sustento conceptual del examen:

| # | Capitulo | Temas Clave |
|---|----------|-------------|
| 1 | Fundamentos de IA | IA vs ML vs Deep Learning, tipos de aprendizaje |
| 2 | Modelos Fundacionales y LLMs | GPT, tokens, embeddings, parametros de inferencia |
| 3 | IA Generativa | Alucinaciones, sesgos, fuga de datos |
| 4 | Tecnicas de Personalizacion | Fine-tuning, transfer learning, data augmentation |
| 5 | RAG | Pipeline offline/online, vector stores |
| 6 | Agentes de IA | Bedrock Agents, advanced prompts |
| 7 | Amazon Bedrock | Guardrails, Knowledge Bases, evaluacion de modelos |
| 8 | Amazon SageMaker | Clarify, Model Monitor, Model Cards, inferencia |
| 9 | Servicios IA de AWS | Rekognition, Comprehend, Textract, Kendra, Q |
| 10 | Metricas de Evaluacion | BLEU, ROUGE, RMSE, Accuracy, F1 |
| 11 | Gobernanza y Seguridad | IAM, CloudTrail, Artifact, residencia de datos |
| 12 | Vision por Computadora | Object detection, NER, anomalias |
| 13 | Glosario | 20+ terminos clave del examen |

---

## 🗺️ Mapa de Servicios AWS — Referencia Rapida

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

---

## 🎯 Tecnicas de Prompting — Identificacion Rapida

| Senal en el enunciado | Tecnica |
|----------------------|---------|
| "Sin ejemplos, solo instruccion" | Zero-shot |
| "Con ejemplos antes de la tarea" | Few-shot |
| "Paso a paso / muestre su razonamiento" | Chain-of-thought |
| "Consultar sistema externo en tiempo real" | ReAct |
| "Adaptar estilo segun perfil de usuario" | Role description |
| "Saltarse restricciones del modelo" | Inyeccion de prompts (ataque) |

---

## 📊 Metricas de Evaluacion — Cuando usar cada una

| Tarea | Metrica |
|-------|---------|
| Clasificacion | Exactitud (Accuracy), F1 |
| Regresion | RMSE, R2 |
| Traduccion automatica | BLEU |
| Resumenes de texto | ROUGE |
| Velocidad en produccion | Tiempo medio de respuesta |
| Satisfaccion del usuario | CSAT |

---

## 🏗️ Dominios del Examen AIF-C01

Segun la guia oficial de AWS, el examen cubre:

| Dominio | Peso aproximado |
|---------|----------------|
| Conceptos de IA y ML | ~20% |
| Fundamentos de IA Generativa | ~24% |
| Aplicaciones de Modelos Fundacionales | ~28% |
| Directrices de IA Responsable | ~14% |
| Seguridad, Cumplimiento y Gobernanza | ~14% |

---

## 🚀 Como usar este repositorio

1. **Lectura teorica**: Comienza con `guia-teorica/sustento-teorico-completo.md`
2. **Repaso rapido**: Usa las tablas de referencia de este README como cheatsheet
3. **Puntos debiles**: Identifica los dominios donde tienes dudas y vuelve a la guia teorica

---

## 📄 Licencia

Material elaborado para uso educativo. Basado en la guia oficial del examen AWS Certified AI Practitioner (AIF-C01).

> **Nota:** Este repositorio es material de estudio independiente y no esta afiliado oficialmente a Amazon Web Services.

---

*Ultima actualizacion: Mayo 2026*
