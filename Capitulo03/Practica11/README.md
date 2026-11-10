# Práctica 11. Analizar una base de datos comercial con Advanced Data Analysis para identificar tendencias de venta, oportunidades de negocio y elaborar un reporte ejecutivo dentro de Canvas

**Capítulo 3. Herramientas de Inteligencia Artificial para la Operación Comercial · Módulo 6. Aplicación de plataformas de IA en la operación comercial (Canvas, Advanced Data Analysis y GPT Store)**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 16 minutos |
| **Complejidad** | Intermedia |
| **Nivel de Bloom** | Analizar |
| **Herramientas** | ChatGPT (versión gratuita, con análisis de datos y Canvas) y Microsoft Word |
| **Archivos** | `Datos_Ventas_Q4_2025.csv` |

## Descripción General

El participante cargará en ChatGPT una base de 215 transacciones del cuarto trimestre de 2025 y usará el análisis de datos (Advanced Data Analysis) para detectar y corregir problemas de calidad, obtener estadísticas y gráficas por región, producto y cliente, e identificar tendencias, riesgos y oportunidades. Con los hallazgos, redactará y refinará un reporte ejecutivo dentro de Canvas.

La práctica se realiza con ChatGPT en su versión gratuita, ya que forma parte de los objetivos del módulo. El instructor puede reducir el número de consultas según los límites disponibles. Todos los datos son ficticios.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Auditar y limpiar una base de datos comercial con instrucciones en lenguaje natural.
- Obtener métricas y gráficas por región, producto y cliente.
- Verificar los resultados contra valores de referencia.
- Redactar y refinar un reporte ejecutivo en Canvas.

## Prerrequisitos

- Cuenta gratuita de ChatGPT (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber revisado el tema *Canvas, Advanced Data Analysis y GPT Store* del Módulo 6.

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| ChatGPT | Análisis de datos, gráficas y Canvas | [chatgpt.com](https://chatgpt.com/) |
| Microsoft Word (escritorio o web) | Guardar el reporte final | Instalado en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Datos_Ventas_Q4_2025.csv](recursos/Datos_Ventas_Q4_2025.csv) | 215 transacciones de octubre a diciembre de 2025 con fecha, cliente, región, producto, cantidad, monto, estado y ejecutivo. Contiene problemas de calidad intencionales |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlo en `Documentos\Practicas_IA_Comercial\Practica11`.

**Precios unitarios de referencia:** CloudLogix ERP 1,200 USD; LogixTrack Lite 450 USD; Soporte Premium 300 USD; Implementación 2,500 USD.

## Instrucciones Paso a Paso

### Paso 1: Cargar la base y auditar su calidad (3 min)

**Objetivo:** Identificar los problemas antes de analizar.

1. Abrir ChatGPT e iniciar una conversación nueva.
2. Adjuntar `Datos_Ventas_Q4_2025.csv` con el botón **+** o el clip.
3. Enviar:

```text
Actúa como analista de datos comerciales. Analiza el archivo adjunto y, sin modificarlo todavía, identifica:
1. Filas duplicadas (mismo ID y mismos valores).
2. Valores vacíos en Monto_USD.
3. Fechas con formato distinto a AAAA-MM-DD.
4. Valores de Region escritos de forma inconsistente.
Muestra los ID afectados en cada caso.
```

**Resultado esperado:** ChatGPT ejecuta el análisis y reporta los 4 tipos de problema.

**Verificación:** Comparar con la referencia:

| Problema | ID afectados |
| :--- | :--- |
| Duplicados (4) | TX1009, TX1056, TX1102, TX1161 |
| Monto vacío (5) | TX1006, TX1041, TX1078, TX1121, TX1151 |
| Fecha en formato DD/MM/AAAA (6) | TX1013, TX1034, TX1065, TX1099, TX1132, TX1171 |
| Región en mayúsculas (3) | TX1021, TX1089, TX1141 |

### Paso 2: Limpiar los datos (3 min)

**Objetivo:** Corregir los problemas con reglas explícitas.

1. Enviar:

```text
Limpia la base con estas reglas:
1. Elimina los duplicados y conserva una sola fila.
2. Completa Monto_USD vacío como precio unitario × Cantidad (CloudLogix ERP 1200, LogixTrack Lite 450, Soporte Premium 300, Implementación 2500).
3. Convierte todas las fechas a AAAA-MM-DD.
4. Escribe las regiones como Norte, Sur, Centro y Occidente.
Confirma el número final de filas y permite descargar la base limpia en CSV.
```

2. Descargar la base limpia y guardarla como `Datos_Ventas_Q4_2025_limpio.csv`.

**Resultado esperado:** Una base de 211 filas sin duplicados, vacíos ni formatos inconsistentes.

**Verificación:** ChatGPT confirma **211 filas**.

### Paso 3: Obtener métricas y gráficas (4 min)

**Objetivo:** Identificar tendencias, riesgos y oportunidades.

1. Enviar:

```text
Con la base limpia y considerando solo las transacciones con Estado = Cerrada:
1. Monto total y monto por región, con una gráfica de barras.
2. Monto por producto, con una gráfica de barras.
3. Los 3 clientes con mayor monto.
4. Tasa de oportunidades perdidas por región (perdidas / total de transacciones de la región).
5. 3 tendencias, 2 riesgos y 2 oportunidades de negocio basados en los datos.
```

2. Comparar con la referencia:

| Indicador | Valor correcto |
| :--- | :--- |
| Monto total cerrado | 233,450 USD |
| Por región | Centro 75,400; Norte 64,950; Occidente 56,900; Sur 36,200 USD |
| Por producto | CloudLogix ERP 129,600; LogixTrack Lite 58,950; Soporte Premium 24,900; Implementación 20,000 USD |
| Cliente con mayor monto | Logística Regia, 33,000 USD |
| Tasa de pérdida más alta | Sur: 11 de 41 transacciones (26.8%) |

**Resultado esperado:** Tablas y gráficas que coinciden con la referencia.

**Verificación:** Si alguna cifra no coincide, pedir a ChatGPT que muestre el cálculo y revisar si aplicó el filtro **Estado = Cerrada**.

### Paso 4: Redactar el reporte en Canvas (3 min)

**Objetivo:** Convertir el análisis en un reporte ejecutivo editable.

1. Enviar:

```text
Abre Canvas y redacta un reporte ejecutivo titulado "Desempeño comercial Q4 2025" con: 1. Resumen ejecutivo, 2. Indicadores clave, 3. Análisis por región y producto, 4. Riesgos, 5. Recomendaciones. Usa las cifras exactas del análisis.
```

2. Si Canvas no se abre automáticamente, seleccionar **Canvas** en el menú de herramientas del cuadro de mensaje (**+** o **Herramientas**) y repetir la instrucción.

**Resultado esperado:** El reporte aparece en el panel de Canvas con las 5 secciones.

**Verificación:** El resumen ejecutivo menciona 233,450 USD y el bajo desempeño de la región Sur.

### Paso 5: Refinar el reporte (2 min)

**Objetivo:** Mejorar una sección concreta del documento.

1. En Canvas, seleccionar el texto de la sección **5. Recomendaciones** y, en el cuadro que aparece, escribir:

```text
Reescribe esta sección con 3 acciones concretas: una para recuperar la región Sur, una de venta cruzada de Soporte Premium para clientes de LogixTrack Lite, y una de control de calidad de datos en el CRM. Incluye responsable y plazo.
```

2. Revisar el cambio aplicado.

**Resultado esperado:** La sección 5 tiene 3 acciones con responsable y plazo.

**Verificación:** Solo cambió la sección seleccionada.

### Paso 6: Guardar el reporte y conocer la GPT Store (1 min)

**Objetivo:** Conservar el entregable e identificar asistentes especializados.

1. Copiar el contenido de Canvas a un documento de Word y guardarlo como `Reporte_Ejecutivo_Q4_[INICIALES].docx`.
2. Opcional: en el menú lateral de ChatGPT, abrir **GPT** (**Explorar GPT**) y buscar *"sales"* o *"ventas"* para ver ejemplos de asistentes especializados. Antes de usar uno con datos de la empresa, revisar quién lo creó y su política de datos.

**Resultado esperado:** El reporte queda guardado en Word.

**Verificación:** El documento conserva las 5 secciones.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Calidad de datos | Paso 1 | Se detectan los 18 registros con problemas (4 + 5 + 6 + 3) |
| Cifras verificables | Paso 3 | El monto total cerrado es de 233,450 USD |
| Prueba adversarial | Preguntar: *"¿Cuánto vendimos en enero de 2026?"* | ChatGPT debe indicar que la base solo cubre de octubre a diciembre de 2025 |

## Solución de Problemas

### Problema 1: Se alcanzó el límite de análisis de la versión gratuita

- **Síntomas:** Mensaje de límite de uso o de archivos.
- **Causa:** Restricciones del plan gratuito.
- **Solución:** Esperar el tiempo indicado o continuar en una conversación nueva cargando la base limpia del Paso 2. El instructor puede omitir las gráficas y conservar las tablas.

### Problema 2: ChatGPT no ejecuta el análisis y solo describe el archivo

- **Síntomas:** La respuesta no incluye tablas calculadas ni gráficas.
- **Causa:** El archivo no se cargó correctamente o la herramienta de análisis no se activó.
- **Solución:** Volver a adjuntar el archivo y comenzar el prompt con: *"Usa la herramienta de análisis de datos para calcular..."*.

## Limpieza

1. Conservar la base limpia y el reporte en `Documentos\Practicas_IA_Comercial\Practica11`.
2. Si la política de la empresa lo indica, eliminar la conversación del historial de ChatGPT.

## Resumen

- Se auditó y limpió una base de 215 transacciones con instrucciones en lenguaje natural.
- Se obtuvieron métricas y gráficas, y se verificaron contra valores de referencia.
- Se redactó y refinó un reporte ejecutivo en Canvas.

---

[⬅ Anterior: Práctica 10](../Practica10/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 12 ➡](../Practica12/README.md)
