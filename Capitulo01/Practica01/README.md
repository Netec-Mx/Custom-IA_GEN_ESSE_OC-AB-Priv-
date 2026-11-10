# Práctica 1. Analizar un proceso comercial completo e identificar actividades susceptibles de automatizarse mediante Inteligencia Artificial, así como puntos críticos donde la IA puede fortalecer el control y seguimiento de la operación

**Capítulo 1. Fundamentos de la Inteligencia Artificial Generativa aplicada a la Operación Comercial · Módulo 2. Inteligencia Artificial aplicada al proceso comercial**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 42 minutos |
| **Complejidad** | Intermedia |
| **Nivel de Bloom** | Analizar |
| **Herramientas** | Una herramienta de IA Generativa gratuita a elección del instructor (ChatGPT, Microsoft Copilot, Gemini o Claude), Microsoft Word y Microsoft Excel |
| **Archivos** | `Caso_LogiTech_Solutions.docx`, `Matriz_Priorizacion_Procesos.xlsx` |

## Descripción General

El participante asume el rol de analista de operación comercial de LogiTech Solutions S.A., una empresa ficticia de software logístico. Con apoyo de una herramienta de IA Generativa, mapeará el proceso comercial de principio a fin (prospección, atención y calificación, propuesta, cierre y seguimiento), identificará las actividades repetitivas que se pueden automatizar, los puntos críticos donde se presentan desviaciones y los KPIs que permiten controlar la operación. Al final, llenará una matriz que prioriza cada oportunidad según su impacto y su facilidad de implementación, y revisará qué partes del análisis de la IA no tienen sustento en los datos del caso.

La práctica se realiza con versiones gratuitas. El instructor puede elegir la herramienta según su disponibilidad y límites de consumo, y ajustar la profundidad o la cantidad de iniciativas, conservando el objetivo y el resultado esperado. Todos los datos son ficticios.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Desglosar las 5 fases de un ciclo comercial B2B e identificar sus actividades y cuellos de botella con apoyo de la IA.
- Identificar actividades repetitivas automatizables y puntos críticos de control.
- Definir KPIs para medir y controlar cada fase.
- Priorizar iniciativas de IA en una matriz de impacto contra facilidad de implementación.
- Detectar suposiciones y datos sin sustento en un análisis generado por IA.

## Prerrequisitos

- Manejo básico de Word y Excel.
- Cuenta gratuita en una herramienta de IA Generativa (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber revisado los temas del Módulo 2: ciclo de la operación comercial, KPIs y automatización de actividades repetitivas.

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Herramienta de IA Generativa | Analizar el caso y proponer iniciativas | [chatgpt.com](https://chatgpt.com/), [copilot.microsoft.com](https://copilot.microsoft.com/), [gemini.google.com](https://gemini.google.com/) o [claude.ai](https://claude.ai/) |
| Microsoft Word y Excel (escritorio o web) | Leer el caso y llenar la matriz | Instalados en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Caso_LogiTech_Solutions.docx](recursos/Caso_LogiTech_Solutions.docx) | Datos de la empresa, proceso comercial actual por fase, problemas y restricciones de la dirección |
| [Matriz_Priorizacion_Procesos.xlsx](recursos/Matriz_Priorizacion_Procesos.xlsx) | Hojas `Matriz` (10 iniciativas), `KPIs` (una fila por fase) y `Criterios` (significado de cada cuadrante) |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y, en la página que se abre, seleccionar el botón **Download raw file** (icono de descarga, arriba a la derecha). Guardar los archivos en la carpeta `Documentos\Practicas_IA_Comercial\Practica01`.

## Instrucciones Paso a Paso

### Paso 1: Revisar el caso y la matriz (4 min)

**Objetivo:** Conocer los datos de la empresa y lo que se va a entregar.

1. Abrir `Caso_LogiTech_Solutions.docx` en Word y leer las secciones **Datos generales**, **Descripción del proceso comercial actual** y **Restricciones de la dirección**.
2. Abrir `Matriz_Priorizacion_Procesos.xlsx` en Excel y revisar las tres hojas:
   - `Matriz`: las celdas amarillas se llenan en esta práctica; la columna **Cuadrante_prioridad** se calcula sola.
   - `KPIs`: una fila por fase comercial.
   - `Criterios`: qué significa cada cuadrante.

**Resultado esperado:** Se identifican las 5 fases del proceso y los 4 cuadrantes de prioridad.

**Verificación:** En la hoja `Criterios`, la combinación *Impacto Alto + Facilidad Alta* corresponde a **Victoria rápida**.

### Paso 2: Configurar el rol y obtener el diagnóstico por fase (6 min)

**Objetivo:** Obtener de la IA un mapa del proceso con micro-actividades y cuellos de botella, limitado a los datos del caso.

1. Abrir la herramienta de IA Generativa e iniciar una conversación nueva.
2. Adjuntar `Caso_LogiTech_Solutions.docx` con el botón de adjuntar (clip o **+**). Si la herramienta no permite adjuntar archivos, copiar el texto del documento y pegarlo al final del prompt.
3. Enviar este prompt:

```text
[ROL]
Actúa como especialista en procesos comerciales B2B y en aplicación de Inteligencia Artificial.

[CONTEXTO]
El documento adjunto describe el proceso comercial de LogiTech Solutions S.A. (empresa ficticia).

[TAREA]
Genera una tabla con una fila por cada una de las 5 fases (Prospección, Atención y calificación, Propuesta, Cierre, Seguimiento y retención) y estas columnas:
- Fase
- Micro-actividades actuales
- Cuellos de botella o fricciones
- Dato del documento que lo demuestra

[REGLAS]
- Usa solo la información del documento. Si un dato no está, escribe "No especificado".
- No propongas soluciones todavía.
```

**Resultado esperado:** Una tabla de 5 filas con actividades y fricciones de cada fase.

**Verificación:** La columna *Dato del documento que lo demuestra* incluye cifras del caso, por ejemplo *30 horas* de primera respuesta o *4 días hábiles* por propuesta.

### Paso 3: Identificar las actividades automatizables y los puntos críticos (7 min)

**Objetivo:** Distinguir qué tareas puede apoyar la IA y dónde debe reforzarse el control.

1. En la misma conversación, enviar:

```text
[TAREA]
Para cada fase, identifica:
1) Tareas repetitivas que se pueden automatizar o apoyar con IA.
2) La iniciativa concreta (qué haría la IA o la automatización).
3) El tipo de intervención: Asistente de IA, Generación de texto, Clasificación y enrutamiento, Análisis documental, Análisis de datos o Automatización Low-Code.
4) El punto crítico de control: el evento en el que la IA debería alertar sobre una desviación o incidencia.

[RESTRICCIONES]
- Respeta las restricciones de la dirección descritas en el documento (sin desarrollos a la medida).
- Propón 2 iniciativas por fase, 10 en total.
- Presenta el resultado en una tabla.
```

2. Leer cada iniciativa y descartar mentalmente las que contradigan las restricciones del caso (por ejemplo, un desarrollo de software a la medida).

**Resultado esperado:** Una tabla con 10 iniciativas, 2 por fase, con su tipo de intervención y su punto crítico de control.

**Verificación:** Cada fase tiene al menos una iniciativa y un punto crítico, por ejemplo *alerta si un lead no recibe respuesta en 1 hora*.

### Paso 4: Definir los KPIs de control (7 min)

**Objetivo:** Definir cómo se medirá la mejora de cada fase.

1. En la misma conversación, enviar:

```text
[TAREA]
Define un KPI principal por fase para controlar la operación comercial de LogiTech. Incluye también la velocidad del pipeline, calculada como:
(oportunidades activas × ticket promedio × tasa de cierre) / duración del ciclo de venta en días.

Entrega una tabla con: Fase, KPI, Cómo se mide, Valor actual (solo si está en el documento; si no, "No especificado"), Meta con IA y Alerta de desviación.
Muestra el cálculo de la velocidad del pipeline paso a paso con los datos del documento.
```

2. Comprobar el cálculo de la velocidad del pipeline con los datos del caso: 140 × 18,500 × 0.12 / 68.

3. Copiar a la hoja `KPIs` de Excel el KPI, cómo se mide, el valor actual, la meta y la alerta de cada fase.

**Resultado esperado:** La hoja `KPIs` tiene 5 filas completas y la velocidad del pipeline calculada.

**Verificación:** La velocidad del pipeline es de aproximadamente **4,571 USD por día**. Si la IA da otra cifra, registrar la diferencia; se analizará en el Paso 6.

### Paso 5: Llenar la matriz de priorización (10 min)

**Objetivo:** Clasificar las 10 iniciativas por impacto y facilidad.

1. En la hoja `Matriz`, llenar para cada fila: **Actividad_actual**, **Iniciativa_IA**, **Tipo_intervencion**, **KPI_asociado** y **Punto_critico_control**, tomando la información de los pasos 3 y 4.
2. Asignar **Impacto_negocio** (Alto o Bajo) y **Facilidad_implementacion** (Alta o Baja) con la lista desplegable de cada celda. Usar este criterio:
   - Impacto **Alto** si mejora directamente un problema cuantificado del caso (30 horas de respuesta, 4 días por propuesta, churn de 14%, 45% de carga administrativa).
   - Facilidad **Alta** si se puede hacer con herramientas que la empresa ya usa o con un asistente de IA gratuito, sin integración con otros sistemas.
3. Revisar que la columna **Cuadrante_prioridad** muestre el resultado.
4. Si no se está de acuerdo con la clasificación propuesta por la IA, ajustarla: la decisión final es del analista.
5. Guardar el archivo como `Matriz_Priorizacion_Procesos_[INICIALES].xlsx`.

**Resultado esperado:** 10 iniciativas clasificadas en los cuadrantes Victoria rápida, Proyecto estratégico, Tarea secundaria o Descartar.

**Verificación:** Hay al menos 2 iniciativas en **Victoria rápida**, por ejemplo la redacción de correos de prospección personalizados o la respuesta inicial automática a leads.

### Paso 6: Auditar el análisis de la IA (5 min)

**Objetivo:** Detectar datos inventados o suposiciones sin sustento antes de presentar el análisis.

1. Enviar en la misma conversación:

```text
[TAREA: AUDITORÍA]
Revisa tus respuestas anteriores contra el documento original y responde:
1) ¿Qué cifras, porcentajes o metas usaste que NO aparecen en el documento?
2) ¿Hiciste alguna estimación de retorno de inversión o ahorro sin datos que la respalden?
3) ¿Alguna iniciativa contradice las restricciones de la dirección?
Entrega una lista con cada caso y la corrección necesaria.
```

2. Comparar la respuesta con la matriz y corregir en Excel cualquier dato que no tenga sustento. Las metas pueden ser propuestas, pero deben quedar identificadas como metas, no como datos del caso.

**Resultado esperado:** Una lista de suposiciones identificadas y la matriz corregida.

**Verificación:** Ninguna celda de **Valor_actual** en la hoja `KPIs` contiene un dato que no esté en el documento.

### Paso 7: Redactar la conclusión (3 min)

**Objetivo:** Resumir el análisis para la dirección.

1. Debajo de la tabla de la hoja `Matriz`, en la celda **A14**, escribir en 3 a 5 líneas:
   - Las 2 victorias rápidas que se recomiendan primero.
   - El proyecto estratégico más importante.
   - Los 2 puntos críticos de control que deben vigilarse.
2. Guardar el archivo.

**Resultado esperado:** Una conclusión breve y accionable.

**Verificación:** La conclusión menciona al menos un KPI con su meta.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Cobertura del proceso | Revisar las hojas `Matriz` y `KPIs` | Las 5 fases tienen iniciativas, punto crítico y KPI |
| Cálculo verificable | Repetir el cálculo de la velocidad del pipeline en una celda de Excel: `=140*18500*0.12/68` | Aproximadamente 4,571 USD por día |
| Prueba adversarial | Preguntar a la IA: *"¿Cuál fue el ingreso de LogiTech el año pasado?"* | La IA debe responder que el documento no lo indica. Si inventa una cifra, registrarlo en la auditoría del Paso 6 |

## Solución de Problemas

### Problema 1: La IA responde con texto largo en lugar de una tabla

- **Síntomas:** La respuesta son párrafos y no se puede copiar a Excel.
- **Causa:** El prompt no fijó el formato de salida con suficiente claridad.
- **Solución:** Enviar: *"Responde únicamente con la tabla, sin introducción ni conclusiones"*. Para copiar una tabla a Excel, seleccionarla en el navegador, copiarla y pegarla en la celda A1 de una hoja nueva.

### Problema 2: La columna Cuadrante_prioridad aparece vacía

- **Síntomas:** No se muestra el cuadrante.
- **Causa:** Falta seleccionar el impacto o la facilidad, o se escribió un valor distinto al de la lista.
- **Solución:** Seleccionar el valor de la lista desplegable (Alto o Bajo; Alta o Baja).

## Limpieza

1. Conservar `Matriz_Priorizacion_Procesos_[INICIALES].xlsx` en `Documentos\Practicas_IA_Comercial\Practica01`.
2. Si la política de la empresa lo indica, eliminar la conversación del historial de la herramienta de IA.

## Resumen

- Se mapeó un proceso comercial de 5 fases con apoyo de IA, sin salir de los datos del caso.
- Se identificaron actividades automatizables, puntos críticos de control y KPIs por fase.
- Se priorizaron 10 iniciativas por impacto y facilidad de implementación.
- Se auditó el análisis para separar los datos del caso de las suposiciones de la IA.

---

[Inicio](../../README.md) | [Siguiente: Práctica 2 ➡](../Practica02/README.md)
