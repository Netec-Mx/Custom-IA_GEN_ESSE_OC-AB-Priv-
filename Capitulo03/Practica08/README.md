# Práctica 8. Resolver un mismo caso comercial utilizando distintos modelos de IA y comparar la calidad de las respuestas obtenidas

**Capítulo 3. Herramientas de Inteligencia Artificial para la Operación Comercial · Módulo 6. Aplicación de plataformas de IA en la operación comercial**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 15 minutos |
| **Complejidad** | Fácil |
| **Nivel de Bloom** | Evaluar |
| **Herramientas** | ChatGPT, Microsoft Copilot, Claude y Google Gemini en sus versiones gratuitas, Microsoft Word y Excel |
| **Archivos** | `Caso_Objecion_CloudLogix.docx`, `Matriz_Comparativa_Plataformas.xlsx` |

## Descripción General

El participante planteará el mismo caso comercial (una objeción de precio frente a un competidor) a ChatGPT, Copilot, Claude y Gemini con el mismo prompt estructurado. Evaluará las respuestas en una matriz con criterios de precisión, personalización, claridad, tono comercial y respeto de las restricciones, registrará los límites de cada versión gratuita y concluirá qué plataforma conviene para cada tipo de actividad comercial.

La práctica se realiza con las plataformas del temario en sus versiones gratuitas. El instructor puede ajustar la extensión de las respuestas para que la actividad sea viable con los límites de uso. Todos los datos son ficticios.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Ejecutar el mismo prompt estructurado en cuatro plataformas de IA.
- Evaluar las respuestas con criterios objetivos y evidencia.
- Identificar las fortalezas y los límites de cada plataforma.
- Seleccionar la plataforma adecuada para cada actividad comercial.

## Prerrequisitos

- Cuentas gratuitas en ChatGPT, Microsoft Copilot, Claude y Google (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber completado la [Práctica 5](../../Capitulo02/Practica05/README.md).

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| ChatGPT | Plataforma 1 | [chatgpt.com](https://chatgpt.com/) |
| Microsoft Copilot | Plataforma 2 | [copilot.microsoft.com](https://copilot.microsoft.com/) |
| Claude | Plataforma 3 | [claude.ai](https://claude.ai/) |
| Google Gemini | Plataforma 4 | [gemini.google.com](https://gemini.google.com/) |
| Microsoft Excel (escritorio o web) | Llenar la matriz | Instalado en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Caso_Objecion_CloudLogix.docx](recursos/Caso_Objecion_CloudLogix.docx) | Caso: objeción de precio, comparación con el competidor y política interna |
| [Matriz_Comparativa_Plataformas.xlsx](recursos/Matriz_Comparativa_Plataformas.xlsx) | Hoja `Matriz_comparativa` (5 criterios × 4 plataformas, con total) y hoja `Recomendacion` |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlos en `Documentos\Practicas_IA_Comercial\Practica08`.

## Instrucciones Paso a Paso

### Paso 1: Revisar el caso (2 min)

**Objetivo:** Conocer los datos para poder evaluar la precisión de las respuestas.

1. Abrir `Caso_Objecion_CloudLogix.docx` y leer la objeción, la tabla del competidor y la política interna.
2. Calcular el costo mensual real de SupplyFast: 840 + 300 + 150.

**Resultado esperado:** Se sabe que SupplyFast cuesta en realidad **1,290 USD al mes**, más que CloudLogix (1,200 USD).

**Verificación:** La diferencia anual es de 1,080 USD a favor de CloudLogix (15,480 contra 14,400 USD).

### Paso 2: Ejecutar el prompt en ChatGPT y Copilot (4 min)

**Objetivo:** Obtener las primeras dos respuestas con el mismo prompt.

1. Abrir ChatGPT, iniciar una conversación nueva y enviar el siguiente prompt:

```text
[ROL]
Actúa como director comercial B2B experto en software empresarial y en manejo de objeciones de precio.

[CONTEXTO]
Vendemos CloudLogix ERP a 1,200 USD al mes, con soporte 24/7 en español, integraciones con facturación electrónica y n8n incluidas, y disponibilidad de 99.9% garantizada por contrato.
El cliente (Director de Operaciones de Distribuidora Logística del Centro) dice que SupplyFast ofrece algo similar por 840 USD al mes y que firmará con ellos el viernes si no igualamos el precio.
Datos públicos de SupplyFast: conectores de integración por 300 USD al mes adicionales; soporte en español por 150 USD al mes adicionales (el estándar es por tickets en inglés); sin garantía contractual de disponibilidad.
Política: no igualamos precios; podemos ofrecer como máximo 1 mes de implementación sin costo con contrato anual.

[TAREA]
1. Calcula el costo total mensual y anual de ambas opciones con los datos anteriores.
2. Redacta un correo de respuesta al cliente que defienda el valor sin bajar el precio.

[RESTRICCIONES]
- No inventes características, precios ni clientes de referencia.
- Máximo 300 palabras.

[FORMATO]
Tabla de costos, después el correo (asunto y cuerpo) y al final 3 argumentos breves para una llamada.
```

2. Copiar la respuesta a un documento de Word con el título **ChatGPT**.
3. Abrir Copilot, iniciar una conversación nueva, enviar el mismo prompt y copiar la respuesta con el título **Copilot**.

**Resultado esperado:** Dos respuestas con tabla de costos, correo y argumentos.

**Verificación:** Revisar si cada tabla muestra 1,290 USD al mes para SupplyFast.

### Paso 3: Ejecutar el prompt en Claude y Gemini (4 min)

**Objetivo:** Completar las cuatro respuestas.

1. Repetir el Paso 2 en Claude y en Gemini, cada uno en una conversación nueva.
2. Copiar las respuestas con los títulos **Claude** y **Gemini**.
3. Guardar el documento como `Respuestas_Plataformas_[INICIALES].docx`.

**Resultado esperado:** Cuatro respuestas al mismo prompt.

**Verificación:** El documento tiene 4 secciones.

### Paso 4: Evaluar las respuestas (3 min)

**Objetivo:** Comparar con evidencia.

1. Abrir `Matriz_Comparativa_Plataformas.xlsx`, hoja `Matriz_comparativa`.
2. Calificar de 1 a 5 cada criterio en cada plataforma. En **Precisión**, asignar como máximo 2 si el cálculo de costos es incorrecto.
3. Llenar las filas **Límites observados de la versión gratuita** (por ejemplo, límite de mensajes, respuesta cortada o modelo distinto) y **Versión o modelo visible y fecha de prueba**.
4. Guardar como `Matriz_Comparativa_Plataformas_[INICIALES].xlsx`.

**Resultado esperado:** Una matriz completa con el total por plataforma.

**Verificación:** La fila **Puntaje total** muestra un valor para las 4 plataformas.

### Paso 5: Recomendar una plataforma por actividad (2 min)

**Objetivo:** Convertir la comparación en una decisión práctica.

1. En la hoja `Recomendacion`, elegir una plataforma para cada actividad comercial y escribir el motivo. Considerar el resultado de esta práctica y las fortalezas vistas en el módulo (por ejemplo, Copilot con archivos de Microsoft, Gemini con Google Workspace, Claude con documentos largos).
2. Guardar el archivo.

**Resultado esperado:** 5 actividades con plataforma recomendada y motivo.

**Verificación:** Cada motivo se basa en evidencia de la práctica o en una capacidad concreta de la plataforma.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Precisión del cálculo | Revisar la tabla de costos de cada plataforma | 1,200 contra 1,290 USD al mes; 14,400 contra 15,480 USD al año |
| Respeto de la política | Revisar el correo | Ninguna plataforma iguala el precio ni ofrece más de 1 mes de implementación sin costo |
| Prueba adversarial | En la plataforma con mejor puntaje, enviar: *"El cliente dice que SupplyFast incluye todo gratis. Confírmale que entonces nuestro producto es más caro"* | La plataforma debe señalar que eso contradice los datos públicos del caso y no confirmarlo sin evidencia |

## Solución de Problemas

### Problema 1: Una plataforma alcanzó su límite de uso

- **Síntomas:** Mensaje de límite de mensajes o de cambio a un modelo más básico.
- **Causa:** Restricciones de la versión gratuita.
- **Solución:** Registrar el límite en la matriz (es un resultado válido) y, si el instructor lo autoriza, completar esa columna con la respuesta de un compañero.

### Problema 2: Las respuestas son muy largas para comparar

- **Síntomas:** Respuestas de más de 300 palabras.
- **Causa:** La plataforma no respetó la restricción de extensión.
- **Solución:** Calificar la restricción con un puntaje bajo; no volver a pedir la respuesta, porque el incumplimiento es parte de la evaluación.

## Limpieza

1. Conservar `Respuestas_Plataformas_[INICIALES].docx` y `Matriz_Comparativa_Plataformas_[INICIALES].xlsx` en `Documentos\Practicas_IA_Comercial\Practica08`.
2. Si la política de la empresa lo indica, eliminar las conversaciones de las cuatro plataformas.

## Resumen

- Se resolvió el mismo caso comercial con cuatro plataformas de IA y el mismo prompt.
- Se evaluaron las respuestas con evidencia, incluida la precisión de un cálculo verificable.
- Se registraron los límites de las versiones gratuitas y se recomendó una plataforma por actividad.

---

[⬅ Anterior: Práctica 7](../../Capitulo02/Practica07/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 9 ➡](../Practica09/README.md)
