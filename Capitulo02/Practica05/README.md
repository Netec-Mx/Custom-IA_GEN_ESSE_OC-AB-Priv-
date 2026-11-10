# Práctica 5. Diseñar prompts para responder a clientes, redactar correos comerciales, preparar reuniones, elaborar propuestas y generar seguimientos comerciales

**Capítulo 2. Ingeniería de Prompts para Procesos Comerciales · Módulo 4. Fundamentos de la ingeniería de prompts**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 20 minutos |
| **Complejidad** | Intermedia |
| **Nivel de Bloom** | Crear |
| **Herramientas** | Una herramienta de IA Generativa gratuita a elección del instructor (ChatGPT, Microsoft Copilot, Gemini o Claude) y Microsoft Word |
| **Archivos** | `Plantilla_Biblioteca_Prompts.docx` |

## Descripción General

El participante construirá cinco plantillas de prompts para las tareas comerciales más frecuentes: respuesta a clientes, correo de prospección, preparación de reunión, propuesta y seguimiento. Aplicará la estructura de rol, contexto, tarea, formato de salida y restricciones, e incorporará las técnicas Few-Shot (ejemplos) y Chain of Thought (razonamiento paso a paso) donde aporten valor. Refinará cada prompt a partir del resultado obtenido y guardará las versiones finales en una biblioteca reutilizable para el equipo comercial.

La práctica se realiza con versiones gratuitas. El instructor puede elegir la herramienta y reducir el número de plantillas si hay límites de uso, conservando el objetivo y el resultado esperado. Todos los datos son ficticios o anonimizados.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Diseñar prompts con rol, contexto, tarea, formato de salida y restricciones para tareas comerciales.
- Aplicar Few-Shot para fijar estilo y formato, y Chain of Thought para tareas que requieren análisis.
- Refinar un prompt a partir de los problemas observados en la respuesta.
- Integrar una biblioteca de plantillas reutilizables con variables.

## Prerrequisitos

- Manejo básico de Word.
- Cuenta gratuita en una herramienta de IA Generativa (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber completado la [Práctica 4](../Practica04/README.md) y revisado el tema *Técnicas de Chain of Thought y Few-Shot*.

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Herramienta de IA Generativa | Probar y refinar los prompts | [chatgpt.com](https://chatgpt.com/), [copilot.microsoft.com](https://copilot.microsoft.com/), [gemini.google.com](https://gemini.google.com/) o [claude.ai](https://claude.ai/) |
| Microsoft Word (escritorio o web) | Documentar la biblioteca | Instalado en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Plantilla_Biblioteca_Prompts.docx](recursos/Plantilla_Biblioteca_Prompts.docx) | Datos del caso y una tabla por plantilla: objetivo, técnica, variables, prompt versión 1, problema observado, prompt final y resultado |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlo en `Documentos\Practicas_IA_Comercial\Practica05`.

**Convención de variables:** escribir entre corchetes los datos que cambian en cada uso, por ejemplo `[NOMBRE_CLIENTE]`, `[PRODUCTO]` o `[FECHA_REUNION]`. Así la plantilla sirve para cualquier cliente.

## Instrucciones Paso a Paso

### Paso 1: Revisar el caso (2 min)

**Objetivo:** Conocer los datos que usarán los prompts.

1. Abrir `Plantilla_Biblioteca_Prompts.docx` y leer la tabla **Datos del caso**.
2. Guardar el archivo como `Biblioteca_Prompts_[INICIALES].docx`.

**Resultado esperado:** Se identifican el cliente, la cotización, la situación, la política y la próxima reunión.

**Verificación:** El descuento máximo autorizado es de 18% y el pago máximo es a 30 días.

### Paso 2: Plantilla 1, respuesta a clientes con Few-Shot (4 min)

**Objetivo:** Fijar el estilo de respuesta con ejemplos.

1. En una conversación nueva, enviar:

```text
[ROL] Eres ejecutivo de atención comercial de una empresa de software logístico.
[TAREA] Responde la consulta del cliente siguiendo el estilo de los ejemplos: saludo breve, respuesta directa, siguiente paso concreto y máximo 80 palabras.

Ejemplo 1
Consulta: ¿El plan incluye capacitación?
Respuesta: Hola, [NOMBRE]. Sí, el plan Enterprise incluye 2 sesiones de capacitación en línea. ¿Le parece si agendamos la primera para la próxima semana? Quedo atento.

Ejemplo 2
Consulta: ¿Pueden darme 30% de descuento?
Respuesta: Hola, [NOMBRE]. Gracias por su interés. Nuestro descuento máximo autorizado es de [DESCUENTO_MAXIMO]. Puedo preparar una propuesta con pagos en dos partes para facilitar su flujo. ¿Le comparto el detalle hoy?

Consulta real: [CONSULTA_DEL_CLIENTE]
```

2. Reemplazar `[CONSULTA_DEL_CLIENTE]` por: *"¿Pueden hacer la demostración del módulo de rutas este jueves? Y otra vez, ¿hay algún descuento adicional?"* y `[DESCUENTO_MAXIMO]` por *18%*.
3. Si la respuesta no sigue el estilo de los ejemplos, anotar el problema y ajustar el prompt.
4. Registrar en la tabla de la Plantilla 1: objetivo, variables, prompt versión 1, problema observado y prompt final.

**Resultado esperado:** Una respuesta breve con el mismo estilo que los ejemplos.

**Verificación:** La respuesta tiene menos de 80 palabras, no ofrece más de 18% y propone un siguiente paso.

### Paso 3: Plantilla 2, correo de prospección con Chain of Thought (4 min)

**Objetivo:** Pedir a la IA que analice antes de redactar.

1. Enviar:

```text
[ROL] Eres especialista en prospección B2B.
[CONTEXTO] Vendemos [PRODUCTO] a empresas de [SECTOR]. El prospecto es [PUESTO] en una empresa con [PROBLEMA_PROBABLE].
[TAREA] Antes de redactar, razona paso a paso y muestra:
1) Los 2 dolores más probables del prospecto.
2) El beneficio de [PRODUCTO] que responde a cada dolor.
3) La llamada a la acción más adecuada.
Después redacta el correo usando ese análisis.
[FORMATO] Asunto de máximo 8 palabras y cuerpo de máximo 120 palabras.
[RESTRICCIONES] No inventes cifras ni clientes de referencia.
```

2. Reemplazar las variables: `[PRODUCTO]` = *plataforma de gestión de transporte*, `[SECTOR]` = *distribución de alimentos*, `[PUESTO]` = *Director de Logística*, `[PROBLEMA_PROBABLE]` = *entregas retrasadas y poca visibilidad de su flota*.
3. Registrar la Plantilla 2.

**Resultado esperado:** El análisis en 3 pasos y el correo construido a partir de él.

**Verificación:** El correo no incluye cifras ni nombres de clientes inventados.

### Paso 4: Plantilla 3, preparación de reunión (3 min)

**Objetivo:** Obtener una guía de reunión lista para usar.

1. Enviar:

```text
[ROL] Eres gerente comercial.
[CONTEXTO] Tengo una reunión de [DURACION] con [ASISTENTES] del cliente [CLIENTE] sobre [TEMA]. Situación: [SITUACION].
[TAREA] Prepara: objetivo de la reunión, agenda con minutos, 5 preguntas de descubrimiento, 3 objeciones probables con su respuesta y el siguiente paso que debo conseguir.
[FORMATO] Tablas y viñetas. Máximo 1 página.
```

2. Llenar las variables con los datos de la tabla **Datos del caso** (reunión de 45 minutos, el jueves a las 10:00 h).
3. Registrar la Plantilla 3.

**Resultado esperado:** Una guía de reunión con agenda que suma 45 minutos.

**Verificación:** La agenda suma exactamente 45 minutos. Si no, pedir la corrección y anotarlo como problema observado.

### Paso 5: Plantillas 4 y 5, propuesta y seguimiento (5 min)

**Objetivo:** Completar el ciclo comercial con una propuesta y un seguimiento.

1. Para la **Plantilla 4 (propuesta)**, enviar:

```text
[ROL] Eres consultor comercial.
[CONTEXTO] Cliente: [CLIENTE]. Necesidad: [NECESIDAD]. Solución: [PRODUCTO], [PRECIO] con [DESCUENTO] de descuento. Condiciones: [CONDICIONES].
[TAREA] Piensa paso a paso qué valor recibe el cliente y luego redacta la estructura de la propuesta: resumen ejecutivo, necesidad, solución, inversión, condiciones y siguientes pasos.
[RESTRICCIONES] Usa solo los precios y condiciones indicados. Si falta un dato, escribe [POR DEFINIR].
```

2. Para la **Plantilla 5 (seguimiento)**, enviar:

```text
[ROL] Eres ejecutivo comercial.
[TAREA] Redacta un correo de seguimiento después de [EVENTO] con el estilo del ejemplo: máximo 90 palabras, un resumen de lo acordado y una pregunta de cierre con fecha.

Ejemplo
Asunto: Siguientes pasos de la demostración
Hola, [NOMBRE]. Gracias por su tiempo hoy. Acordamos [ACUERDO_1] y [ACUERDO_2]. Para avanzar, ¿podemos confirmar la revisión de la propuesta el [FECHA]?

Datos reales: [DATOS_DEL_EVENTO]
```

3. Probar ambos con los datos del caso y registrar las plantillas 4 y 5.

**Resultado esperado:** Una estructura de propuesta sin datos inventados y un correo de seguimiento breve.

**Verificación:** La propuesta usa 125,000 USD y 18%, y marca `[POR DEFINIR]` donde falta información.

### Paso 6: Consolidar la biblioteca (2 min)

**Objetivo:** Dejar la biblioteca lista para el equipo.

1. Revisar que cada plantilla tenga su **Prompt versión final** con variables entre corchetes.
2. Marcar en cada tabla si el resultado se puede usar con cambios mínimos (Sí o No).
3. Guardar el documento.

**Resultado esperado:** Una biblioteca con 5 plantillas probadas y refinadas.

**Verificación:** Al menos 2 plantillas usan Few-Shot y al menos 2 usan Chain of Thought.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Reutilización | Usar la Plantilla 1 con otra consulta: *"¿Tienen soporte los fines de semana?"* | La respuesta mantiene el estilo y no inventa un horario: pide confirmar o indica que lo verificará |
| Variables | Revisar las 5 plantillas finales | Ningún dato del caso queda escrito dentro de la plantilla; todos están como variables |
| Prueba adversarial | En la Plantilla 4, dejar `[PRECIO]` vacío | La IA escribe `[POR DEFINIR]` en lugar de inventar un precio |

## Solución de Problemas

### Problema 1: La IA no sigue el formato de los ejemplos (Few-Shot)

- **Síntomas:** La respuesta es más larga o tiene otra estructura.
- **Causa:** Los ejemplos no son lo bastante parecidos al caso real o falta una regla explícita.
- **Solución:** Agregar un tercer ejemplo y la regla: *"Responde con la misma estructura y extensión que los ejemplos"*.

### Problema 2: La IA muestra el razonamiento pero no redacta el correo

- **Síntomas:** Solo aparece el análisis de Chain of Thought.
- **Causa:** La respuesta se cortó o la instrucción final no fue clara.
- **Solución:** Enviar: *"Ahora redacta el correo usando tu análisis"*.

## Limpieza

1. Conservar `Biblioteca_Prompts_[INICIALES].docx` en `Documentos\Practicas_IA_Comercial\Practica05`. Esta biblioteca se reutiliza en las prácticas del Capítulo 3.
2. Si la política de la empresa lo indica, eliminar las conversaciones.

## Resumen

- Se diseñaron 5 plantillas de prompts para las tareas comerciales más frecuentes.
- Se aplicaron Few-Shot para fijar estilo y Chain of Thought para tareas de análisis.
- Se refinaron los prompts a partir de los problemas observados y se integró una biblioteca reutilizable.

---

[⬅ Anterior: Práctica 4](../Practica04/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 6 ➡](../Practica06/README.md)
