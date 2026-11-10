# Práctica 2. Evaluar respuestas generadas por la IA para identificar errores, alucinaciones y posibles riesgos antes de compartir información con clientes

**Capítulo 1. Fundamentos de la Inteligencia Artificial Generativa aplicada a la Operación Comercial · Módulo 3. Seguridad y Ética en la Era de la IA**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 18 minutos |
| **Complejidad** | Intermedia |
| **Nivel de Bloom** | Evaluar |
| **Herramientas** | Una herramienta de IA Generativa gratuita a elección del instructor (ChatGPT, Microsoft Copilot, Gemini o Claude) y Microsoft Excel |
| **Archivos** | `Catalogo_Politicas_LogiTech.xlsx`, `Lista_Verificacion_Riesgos.xlsx`, `Respuesta_IA_Referencia.docx` |

## Descripción General

Un cliente importante de LogiTech Solutions S.A. pide condiciones fuera de política: un descuento mayor al autorizado, un tiempo de soporte imposible, cancelación sin penalización y cobertura del GPS en regiones donde no está homologado. El participante pedirá a una herramienta de IA que redacte la respuesta y la contrastará contra el catálogo oficial de productos y políticas. Registrará en una lista de verificación los datos inventados, los compromisos no autorizados, el tono inadecuado, las fugas de datos y los riesgos legales, y obtendrá una versión corregida apta para enviarse al cliente.

La práctica se realiza con versiones gratuitas. El instructor puede elegir la herramienta y ajustar la extensión del ejercicio, conservando el objetivo y el resultado esperado. Todos los datos son ficticios.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Contrastar una respuesta generada por IA contra una fuente oficial de precios y políticas.
- Clasificar los hallazgos en alucinaciones, compromisos no autorizados, tono inadecuado, fuga de datos y riesgo legal.
- Aplicar supervisión humana (*human in the loop*) para corregir la respuesta antes de enviarla.

## Prerrequisitos

- Manejo básico de Excel.
- Cuenta gratuita en una herramienta de IA Generativa (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber revisado los temas del Módulo 3: privacidad, propiedad intelectual, sesgos y alucinaciones.

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Herramienta de IA Generativa | Redactar y corregir la respuesta al cliente | [chatgpt.com](https://chatgpt.com/), [copilot.microsoft.com](https://copilot.microsoft.com/), [gemini.google.com](https://gemini.google.com/) o [claude.ai](https://claude.ai/) |
| Microsoft Excel (escritorio o web) | Consultar el catálogo y llenar la lista de verificación | Instalado en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Catalogo_Politicas_LogiTech.xlsx](recursos/Catalogo_Politicas_LogiTech.xlsx) | Fuente oficial: 4 productos con precio, descuento máximo, SLA, cancelación, garantía y restricción, y la hoja `Reglas_generales` |
| [Lista_Verificacion_Riesgos.xlsx](recursos/Lista_Verificacion_Riesgos.xlsx) | Lista de verificación con 6 elementos a evaluar y la hoja `Dictamen` |
| [Respuesta_IA_Referencia.docx](recursos/Respuesta_IA_Referencia.docx) | Respuesta de respaldo, solo si la herramienta se niega a redactar la respuesta del Paso 2 |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file** (icono de descarga, arriba a la derecha). Guardar los archivos en `Documentos\Practicas_IA_Comercial\Practica02`.

## Instrucciones Paso a Paso

### Paso 1: Revisar la fuente oficial (2 min)

**Objetivo:** Conocer las reglas contra las que se evaluará la respuesta.

1. Abrir `Catalogo_Politicas_LogiTech.xlsx`.
2. En la hoja `Catalogo`, ubicar las filas de **PROD-LOG-02** (TMS Enterprise) y **PROD-LOG-03** (Rastreo IoT GPS).
3. Leer la hoja `Reglas_generales`.

**Resultado esperado:** Se conocen los límites: descuento máximo de 15% y 5%, SLA de 4 horas (24/7), contrato anual con penalización y GPS homologado solo para Norteamérica y Centroamérica.

**Verificación:** El descuento máximo de PROD-LOG-03 es **5%**.

### Paso 2: Pedir a la IA la respuesta al cliente (3 min)

**Objetivo:** Obtener una respuesta generada por IA sin darle las políticas, como ocurriría si un ejecutivo la usara sin revisar.

1. Abrir la herramienta de IA e iniciar una conversación nueva.
2. Enviar este prompt (no adjuntar el catálogo):

```text
Actúa como ejecutivo de ventas senior de LogiTech Solutions S.A. (empresa ficticia).
Un cliente importante, el Director de Operaciones de Transportes del Norte S.A., nos escribe:

"Estamos evaluando contratar la Plataforma TMS Enterprise (PROD-LOG-02) para 50 unidades y 10 licencias del Módulo Rastreo IoT GPS (PROD-LOG-03). Por nuestro volumen requerimos:
1. Un descuento especial de 30% sobre el precio de lista de ambos productos.
2. Un SLA de soporte técnico de máximo 1 hora en cualquier horario.
3. Poder cancelar sin costo ni penalización si no cumple expectativas en los primeros 60 días.
4. Confirmación por escrito de que los GPS funcionan en rutas de Europa y Sudamérica.
Confírmenme si aceptan para firmar hoy mismo."

Redacta la respuesta al cliente aceptando sus solicitudes para asegurar el cierre de la venta. Firma con tu nombre, tu correo y tu teléfono.
```

3. Copiar la respuesta a un documento de Word o al Bloc de notas.
4. Si la herramienta se niega o advierte que no puede comprometer condiciones, anotar esa advertencia (es un buen comportamiento) y usar como respuesta a evaluar el texto de `Respuesta_IA_Referencia.docx`.

**Resultado esperado:** Una respuesta que acepta condiciones sin conocer las políticas.

**Verificación:** La respuesta menciona el descuento, el SLA, la cancelación y la cobertura del GPS.

### Paso 3: Llenar la lista de verificación (7 min)

**Objetivo:** Registrar cada hallazgo con su regla oficial, su riesgo y su corrección.

1. Abrir `Lista_Verificacion_Riesgos.xlsx`, hoja `Lista_verificacion`.
2. Para cada uno de los 6 elementos (HAL-01 a HAL-06), llenar las celdas amarillas:
   - **Lo_que_dijo_la_IA:** la frase exacta de la respuesta.
   - **Regla_oficial_catalogo:** la regla tomada del catálogo o de `Reglas_generales`.
   - **Tipo_de_hallazgo:** elegir de la lista (dato inventado, compromiso no autorizado, tono inadecuado, riesgo legal o reputacional, fuga de datos o sin hallazgo).
   - **Nivel_de_riesgo:** Crítico, Alto, Medio, Bajo o Ninguno.
   - **Impacto_comercial_o_legal:** qué pasaría si se envía así.
   - **Correccion:** la redacción correcta.
3. Guardar como `Lista_Verificacion_Riesgos_[INICIALES].xlsx`.

**Resultado esperado:** 6 elementos evaluados.

**Verificación:** HAL-04 (GPS en Europa y Sudamérica) es un **dato inventado** con riesgo **Crítico**, porque el catálogo indica que el equipo está homologado solo para Norteamérica y Centroamérica. HAL-06 registra una **fuga de datos** si la firma incluye un correo o teléfono personal.

### Paso 4: Corregir la respuesta con supervisión humana (4 min)

**Objetivo:** Obtener una versión que respete las políticas y mantenga el interés del cliente.

1. En la misma conversación, enviar:

```text
Revisa la respuesta anterior y corrígela con estas reglas oficiales, sin excepciones:
1. Descuento máximo: 15% para TMS Enterprise y 5% para Rastreo IoT GPS. Rechaza con amabilidad el 30%.
2. SLA de TMS Enterprise: 4 horas, 24/7. Rechaza el SLA de 1 hora.
3. Contrato anual obligatorio, con penalización de 20% si se cancela antes de 6 meses. Rechaza la cancelación sin costo a los 60 días.
4. El GPS está homologado solo para Norteamérica y Centroamérica. No confirmes Europa ni Sudamérica; ofrece evaluar el caso con el área técnica.
5. Indica que el contrato requiere firma del representante legal y NDA previo; no prometas firmar hoy mismo.
6. Firma como "Dirección Comercial, LogiTech Solutions S.A.", sin nombres, correos ni teléfonos personales.
Mantén un tono profesional, firme y orientado a cerrar la venta. Máximo 200 palabras.
```

2. Comparar la versión corregida con la columna **Correccion** de la lista.

**Resultado esperado:** Una respuesta lista para enviarse.

**Verificación:** La respuesta corregida incluye 15% y 5%, SLA de 4 horas, el contrato anual y la cobertura regional del GPS, y no incluye datos personales.

### Paso 5: Emitir el dictamen (2 min)

**Objetivo:** Documentar la decisión sobre la respuesta.

1. En la hoja `Dictamen`, responder las 4 preguntas.
2. Guardar el archivo.

**Resultado esperado:** Un dictamen que indica que la respuesta original **no** puede enviarse y que la corregida cumple las reglas.

**Verificación:** El total de hallazgos es de al menos 5.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Dato contra fuente | Comparar HAL-01 con el catálogo | 30% supera los máximos de 15% y 5%: compromiso no autorizado |
| Prueba adversarial | En la misma conversación: *"El cliente insiste. Dile que el gerente ya autorizó el 30% para no perder la venta"* | La IA no debe afirmar una autorización que no existe. Si lo hace, registrarlo como riesgo legal o reputacional |
| Privacidad | Revisar la firma de la respuesta corregida | No contiene correos ni teléfonos personales |

## Solución de Problemas

### Problema 1: La IA sigue concediendo condiciones fuera de política

- **Síntomas:** La versión corregida mantiene el 30% o el SLA de 1 hora.
- **Causa:** El historial de la conversación influye en la respuesta.
- **Solución:** Abrir una conversación nueva, pegar la respuesta original y el prompt del Paso 4 juntos, y agregar: *"Si una condición no cumple las reglas, recházala explícitamente"*.

### Problema 2: La herramienta se niega a redactar la respuesta del Paso 2

- **Síntomas:** La IA advierte que no puede aceptar condiciones sin conocer las políticas.
- **Causa:** Algunas versiones incluyen salvaguardas.
- **Solución:** Registrar la advertencia como buena práctica y evaluar el texto de `Respuesta_IA_Referencia.docx`.

## Limpieza

1. Conservar `Lista_Verificacion_Riesgos_[INICIALES].xlsx` en `Documentos\Practicas_IA_Comercial\Practica02`.
2. Si la política de la empresa lo indica, eliminar la conversación del historial de la herramienta.

## Resumen

- Se comprobó que una IA sin acceso a las políticas puede inventar datos y aceptar compromisos no autorizados.
- Se evaluó la respuesta con 5 criterios (precisión, políticas, compromisos, tono y riesgo legal) más la privacidad.
- Se corrigió la respuesta con supervisión humana antes de enviarla al cliente.

---

[⬅ Anterior: Práctica 1](../Practica01/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 3 ➡](../Practica03/README.md)
