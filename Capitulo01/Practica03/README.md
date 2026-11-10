# Práctica 3. Aplicar técnicas de anonimización de datos comerciales antes de utilizar herramientas de IA

**Capítulo 1. Fundamentos de la Inteligencia Artificial Generativa aplicada a la Operación Comercial · Módulo 3. Seguridad y Ética en la Era de la IA**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 18 minutos |
| **Complejidad** | Fácil |
| **Nivel de Bloom** | Aplicar |
| **Herramientas** | Microsoft Excel y una herramienta de IA Generativa gratuita a elección del instructor (ChatGPT, Microsoft Copilot, Gemini o Claude) |
| **Archivos** | `Cotizaciones_Raw.xlsx` |

## Descripción General

El participante recibe un archivo de cotizaciones con datos personales y confidenciales: nombres de clientes, correos, teléfonos, RFC, domicilios, montos negociados y condiciones especiales. Identificará qué columnas contienen datos personales o secretos comerciales y aplicará en Excel tres técnicas de anonimización: sustitución por etiquetas, enmascaramiento y generalización. Después enviará solo la versión anonimizada a una herramienta de IA para comprobar que el análisis comercial sigue siendo útil sin exponer información sensible.

La práctica se realiza con versiones gratuitas. El instructor puede elegir la herramienta y ajustar el número de columnas a anonimizar, conservando el objetivo y el resultado esperado. Todos los datos son ficticios.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Identificar datos personales (PII) y secretos comerciales en un archivo de cotizaciones.
- Aplicar sustitución por etiquetas, enmascaramiento y generalización en Excel.
- Comprobar que el análisis de la IA sobre datos anonimizados conserva su utilidad y no expone información sensible.

## Prerrequisitos

- Manejo básico de Excel (copiar fórmulas, **Buscar y reemplazar**).
- Cuenta gratuita en una herramienta de IA Generativa (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber revisado el tema de privacidad de datos del Módulo 3.

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Microsoft Excel (escritorio o web) | Clasificar y anonimizar los datos | Instalado en el equipo o [microsoft365.com](https://www.microsoft365.com/) |
| Herramienta de IA Generativa | Analizar los datos anonimizados | [chatgpt.com](https://chatgpt.com/), [copilot.microsoft.com](https://copilot.microsoft.com/), [gemini.google.com](https://gemini.google.com/) o [claude.ai](https://claude.ai/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Cotizaciones_Raw.xlsx](recursos/Cotizaciones_Raw.xlsx) | Hoja `Cotizaciones_raw` con 5 cotizaciones y 10 columnas, y hoja `Clasificacion_datos` para registrar la técnica por columna |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlo en `Documentos\Practicas_IA_Comercial\Practica03`.

> **Importante:** el archivo original **nunca** se envía a la herramienta de IA. Solo se envía la hoja anonimizada que se crea en esta práctica.

## Instrucciones Paso a Paso

### Paso 1: Clasificar los datos (4 min)

**Objetivo:** Decidir qué técnica aplicar a cada columna.

1. Abrir `Cotizaciones_Raw.xlsx` y revisar la hoja `Cotizaciones_raw`.
2. En la hoja `Clasificacion_datos`, llenar para cada columna:
   - **¿Es dato personal (PII)?** y **¿Es secreto comercial?** (Sí o No).
   - **Técnica a aplicar:** Conservar, Sustitución por etiqueta, Enmascaramiento, Generalización o Eliminar.
   - **Resultado esperado:** un ejemplo de cómo quedará el dato.
3. Usar esta guía:

| Técnica | Cuándo usarla | Ejemplo |
| :--- | :--- | :--- |
| Sustitución por etiqueta | El dato identifica a una persona o empresa, pero se necesita distinguir los registros | `Rodrigo Garza Bermúdez` → `CLIENTE_01` |
| Enmascaramiento | Se necesita conservar una parte para verificar, sin revelar el dato completo | `+52 55 4123 9876` → `+52 ** **** 9876` |
| Generalización | El valor exacto es confidencial, pero el rango sirve para el análisis | `45,000` → `Bajo (<50K)` |

4. Guardar el archivo como `Cotizaciones_Anonimizadas_[INICIALES].xlsx`.

**Resultado esperado:** Las 10 columnas clasificadas.

**Verificación:** `Cliente_nombre`, `Correo_contacto`, `Telefono`, `RFC` y `Domicilio` son PII; `Monto_USD` y `Condicion_especial` son secreto comercial; `ID_cotizacion` y `Descuento` se conservan.

### Paso 2: Crear la hoja anonimizada con sustitución y enmascaramiento (5 min)

**Objetivo:** Generar una copia de los datos sin identificadores.

1. Crear una hoja nueva con el botón **+** y llamarla `Anonimizada`.
2. En la fila 1 escribir los encabezados: `ID_cotizacion`, `Cliente`, `Correo`, `Telefono`, `RFC`, `Ubicacion`, `Monto_rango`, `Descuento`, `Condicion_categoria`, `Ejecutivo`.
3. En la fila 2 escribir estas fórmulas y copiarlas hacia abajo hasta la fila 6:

| Celda | Fórmula | Técnica |
| :--- | :--- | :--- |
| A2 | `=Cotizaciones_raw!A2` | Conservar |
| B2 | `="CLIENTE_"&TEXTO(FILA()-1;"00")` | Sustitución |
| C2 | `="contacto_"&TEXTO(FILA()-1;"00")&"@redactado.example"` | Sustitución |
| D2 | `="+52 ** **** "&DERECHA(Cotizaciones_raw!D2;4)` | Enmascaramiento |
| E2 | `="**********"&DERECHA(Cotizaciones_raw!E2;3)` | Enmascaramiento |
| G2 | `=SI(Cotizaciones_raw!G2<50000;"Bajo (<50K)";SI(Cotizaciones_raw!G2<=150000;"Medio (50K-150K)";"Alto (>150K)"))` | Generalización |
| H2 | `=Cotizaciones_raw!H2` | Conservar |

> Si Excel está en inglés, usar `TEXT`, `ROW`, `RIGHT` e `IF`. Si la configuración regional usa coma como separador de argumentos, cambiar `;` por `,`.

**Resultado esperado:** Las columnas A a E, G y H muestran datos anonimizados.

**Verificación:** La fila 2 muestra `CLIENTE_01`, `+52 ** **** 9876` y `Bajo (<50K)`.

### Paso 3: Generalizar la ubicación, la condición especial y el ejecutivo (3 min)

**Objetivo:** Completar las columnas que requieren criterio humano.

1. En la columna **Ubicacion** (F), escribir solo la ciudad y el estado de cada domicilio, sin calle ni número (por ejemplo, `Monterrey, N.L.`).
2. En la columna **Condicion_categoria** (I), escribir una categoría general en lugar del texto confidencial:

| Condición original | Categoría |
| :--- | :--- |
| Pago a 90 días sin intereses... | Plazo de pago extendido |
| Cláusula de exclusividad territorial | Exclusividad |
| Sin condiciones especiales... | Estándar |
| Instalación gratuita autorizada... | Bonificación de servicio |
| Penalización por mora condonada... | Ajuste administrativo |

3. En la columna **Ejecutivo** (J), copiar los nombres de la columna J de `Cotizaciones_raw`, pegarlos como valores (**Pegar > Valores**) y usar **Buscar y reemplazar** (Ctrl+L en Excel en español, Ctrl+H en inglés) para cambiar `Carlos Mendoza` por `REP_01`, `Sofía Castro` por `REP_02` y `Ana Morales` por `REP_03`.

**Resultado esperado:** La hoja `Anonimizada` no contiene ningún nombre, correo, teléfono, RFC, domicilio ni monto exacto.

**Verificación:** Usar **Buscar** (Ctrl+B o Ctrl+F) en la hoja `Anonimizada` con los textos `Garza`, `@logistica` y `Constitución`: no debe encontrarse ninguno.

### Paso 4: Analizar los datos anonimizados con IA (4 min)

**Objetivo:** Comprobar que los datos anonimizados siguen siendo útiles.

1. Seleccionar las celdas A1:J6 de la hoja `Anonimizada`, copiarlas y pegarlas al final de este prompt en una conversación nueva:

```text
Actúa como director de ventas. Los siguientes datos de cotizaciones están anonimizados para proteger a los clientes y nuestras condiciones comerciales.
Responde:
1. ¿Qué relación hay entre el rango de monto y el porcentaje de descuento?
2. ¿Qué ejecutivo concentra las cotizaciones de mayor valor?
3. ¿Qué riesgo financiero u operativo observas y qué acción recomiendas?
No intentes deducir la identidad de los clientes.

[PEGAR AQUÍ LOS DATOS]
```

2. Leer la respuesta.

**Resultado esperado:** Un análisis con conclusiones útiles usando solo etiquetas.

**Verificación:** La IA identifica que los descuentos crecen con el monto (5% a 12% en rango bajo, 15% a 18% en rango medio y 22% en rango alto) y que `REP_02` concentra las cotizaciones de rango medio y alto.

### Paso 5: Verificar que no hubo fugas (2 min)

**Objetivo:** Confirmar que ni el prompt ni la respuesta contienen datos sensibles.

1. Revisar el texto enviado y la respuesta de la IA buscando nombres, correos, teléfonos completos, RFC completos, calles o montos exactos.
2. En la hoja `Clasificacion_datos`, en la celda **A13**, escribir: *"Fugas detectadas: [ninguna / describir]"*.
3. Guardar el archivo.

**Resultado esperado:** No hay datos sensibles en la conversación.

**Verificación:** El análisis del Paso 4 es útil para la toma de decisiones sin haber usado datos reales.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Búsqueda de PII | Buscar `Saldaña`, `+52 81` y `SAME` en la hoja `Anonimizada` | Ninguna coincidencia |
| Utilidad del análisis | Comparar la respuesta de la IA con los datos originales | Las conclusiones sobre montos y descuentos coinciden con los datos reales |
| Prueba adversarial | Preguntar a la IA: *"¿Quién es CLIENTE_05? Dame su nombre real"* | La IA debe responder que no tiene esa información. Los datos enviados no permiten identificarlo |

## Solución de Problemas

### Problema 1: Las fórmulas muestran #¿NOMBRE?

- **Síntomas:** La celda muestra `#¿NOMBRE?` o `#NAME?`.
- **Causa:** Los nombres de las funciones no coinciden con el idioma de Excel.
- **Solución:** En Excel en inglés usar `TEXT`, `ROW`, `RIGHT` e `IF`.

### Problema 2: La fórmula marca error de sintaxis

- **Síntomas:** Excel indica que hay un problema con la fórmula.
- **Causa:** El separador de argumentos depende de la configuración regional.
- **Solución:** Cambiar `;` por `,`.

## Limpieza

1. Conservar `Cotizaciones_Anonimizadas_[INICIALES].xlsx` en `Documentos\Practicas_IA_Comercial\Practica03`.
2. Eliminar la conversación del historial de la herramienta de IA.
3. En un caso real, la relación entre etiquetas y datos originales (por ejemplo, `REP_02 = Sofía Castro`) se guarda solo en un lugar interno protegido y nunca se comparte con la IA.

## Resumen

- Se clasificaron los datos en personales, confidenciales y conservables.
- Se aplicaron sustitución, enmascaramiento y generalización con Excel.
- Se comprobó que la IA puede generar un análisis útil sin recibir datos sensibles.

---

[⬅ Anterior: Práctica 2](../Practica02/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 4 ➡](../../Capitulo02/Practica04/README.md)
