# Práctica 9. Se realizará un análisis automático de datos en Excel con Copilot, se generará un informe ejecutivo en Word a partir de esos resultados y, finalmente, se crearán una infografía y una presentación en PowerPoint

**Capítulo 3. Herramientas de Inteligencia Artificial para la Operación Comercial · Módulo 6. Aplicación de plataformas de IA en la operación comercial (M365 Copilot Chat)**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 16 minutos |
| **Complejidad** | Intermedia |
| **Nivel de Bloom** | Crear |
| **Herramientas** | Microsoft Copilot Chat (versión gratuita, con carga de archivos), Microsoft Word y PowerPoint |
| **Archivos** | `Ventas_Trimestrales.xlsx` (y `Ventas_Trimestrales.csv` como alternativa) |

## Descripción General

El participante cargará en Microsoft Copilot Chat un archivo de Excel con ventas comparativas del primer trimestre de 2025 y 2026 por región y producto. Pedirá un análisis automático para identificar tendencias, desviaciones y oportunidades de mejora, y a partir de esos resultados obtendrá el contenido de un informe ejecutivo para Word, una infografía con los hallazgos principales y la estructura de una presentación de PowerPoint.

La práctica debe realizarse con Microsoft Copilot, ya que forma parte de los objetivos del módulo, usando Copilot Chat gratuito mediante la carga de archivos, sin licencia Premium ni Copilot integrado en las aplicaciones de Office. Copilot genera el contenido estructurado del informe, la infografía y la presentación como entregables descargables; Word y PowerPoint solo se usan para abrirlos o pegar el contenido, sin funciones de IA. El instructor puede simplificar el escenario o reducir el tamaño del archivo según los límites de la versión gratuita. Todos los datos son ficticios.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Analizar un archivo de Excel con Copilot Chat para identificar tendencias y desviaciones.
- Verificar las cifras clave del análisis contra los datos originales.
- Generar con Copilot el contenido de un informe ejecutivo, una infografía y una presentación.

## Prerrequisitos

- Cuenta Microsoft (personal, de trabajo o escuela) con acceso a Copilot Chat (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Acceso a Word y PowerPoint (escritorio o web).
- Haber revisado el tema *M365 Copilot Chat* del Módulo 6.

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Microsoft Copilot Chat | Analizar el archivo y generar el contenido | [copilot.microsoft.com](https://copilot.microsoft.com/) (cuenta personal) o [m365.cloud.microsoft/chat](https://m365.cloud.microsoft/chat) (cuenta de trabajo o escuela) |
| Microsoft Word y PowerPoint | Integrar el informe y la presentación | Instalados en el equipo o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Ventas_Trimestrales.xlsx](recursos/Ventas_Trimestrales.xlsx) | 10 transacciones con región, producto, ventas Q1 2025 y Q1 2026, costo operativo Q1 2026 y clientes activos |
| [Ventas_Trimestrales.csv](recursos/Ventas_Trimestrales.csv) | Los mismos datos en CSV, por si Copilot no acepta el archivo de Excel |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlos en `Documentos\Practicas_IA_Comercial\Practica09`.

## Instrucciones Paso a Paso

### Paso 1: Analizar el archivo con Copilot (5 min)

**Objetivo:** Obtener el análisis automático de tendencias y desviaciones.

1. Abrir Copilot Chat e iniciar sesión con la cuenta Microsoft.
2. Seleccionar el botón de adjuntar (**+** o clip) y cargar `Ventas_Trimestrales.xlsx`. Si no se acepta, cargar `Ventas_Trimestrales.csv`.
3. Enviar:

```text
[ROL] Actúa como analista de inteligencia comercial.
[CONTEXTO] El archivo adjunto compara las ventas del primer trimestre de 2025 y 2026 por región y producto, con el costo operativo de 2026 y los clientes activos.
[TAREA]
1. Total de ventas de cada trimestre y variación porcentual.
2. Ventas y variación por región y por producto.
3. Margen de 2026 (ventas menos costo) por región, en monto y porcentaje.
4. Las 3 desviaciones que requieren atención inmediata y 2 oportunidades de mejora.
[FORMATO] Tablas y viñetas. Muestra los cálculos. Usa solo los datos del archivo.
```

4. Comparar las cifras con la tabla de referencia:

| Indicador | Valor correcto |
| :--- | :--- |
| Ventas Q1 2025 / Q1 2026 | 94,800 / 102,900 USD (+8.5%) |
| Norte | 47,100 → 57,000 USD (+21.0%) |
| Centro | 21,700 → 25,700 USD (+18.4%) |
| Sur | 26,000 → 20,200 USD (−22.3%), margen de 2026 de solo 5.9% |
| CloudLogix ERP / LogixTrack Lite | +12.1% / −8.6% |

**Resultado esperado:** Copilot identifica el crecimiento del Norte y el Centro, y la caída de ventas y de margen en el Sur.

**Verificación:** Si alguna cifra no coincide, pedir a Copilot: *"Revisa el cálculo de [indicador] fila por fila"* y anotar el error. No continuar con cifras incorrectas.

### Paso 2: Generar el informe ejecutivo para Word (4 min)

**Objetivo:** Obtener un informe a partir del análisis verificado.

1. En la misma conversación, enviar:

```text
Con base en el análisis anterior, redacta un informe ejecutivo para la Dirección Comercial con:
título, resumen ejecutivo (5 líneas), tabla de indicadores clave, análisis por región y producto, desviaciones críticas, recomendaciones con responsable y plazo, y conclusión.
Máximo 1 página y media. Si puedes generar un documento de Word descargable, hazlo.
```

2. Si Copilot ofrece un archivo de Word o un botón para exportar o descargar, descargarlo. Si no, copiar el texto a un documento nuevo de Word.
3. Guardar como `Informe_Ejecutivo_Q1_[INICIALES].docx`.

**Resultado esperado:** Un informe ejecutivo en Word con las secciones solicitadas.

**Verificación:** La tabla de indicadores del informe coincide con la tabla de referencia del Paso 1.

### Paso 3: Generar la infografía (3 min)

**Objetivo:** Resumir los hallazgos en una imagen.

1. Enviar:

```text
Crea una imagen de infografía vertical con el título "Resultados comerciales Q1 2026" que muestre: ventas totales y crecimiento (+8.5%), crecimiento del Norte (+21.0%) y del Centro (+18.4%), caída del Sur (−22.3%) y una recomendación principal. Estilo corporativo, colores azul y gris, texto en español.
```

2. Descargar la imagen y guardarla como `Infografia_Q1_[INICIALES].png`.
3. Revisar que las cifras y el texto de la imagen sean correctos: los generadores de imágenes pueden escribir mal los números.

**Resultado esperado:** Una infografía con los hallazgos principales.

**Verificación:** Si la imagen contiene cifras o palabras incorrectas, anotarlo como limitación y pedir la versión corregida una vez.

### Paso 4: Generar la presentación de PowerPoint (3 min)

**Objetivo:** Obtener la estructura de una presentación para la Dirección.

1. Enviar:

```text
Crea la estructura de una presentación de 6 diapositivas para la Dirección Comercial basada en el informe: para cada diapositiva indica título, 3 a 4 viñetas y el gráfico o visual sugerido. Si puedes generar un archivo de PowerPoint descargable, hazlo.
```

2. Si Copilot genera un archivo de PowerPoint, descargarlo. Si no, abrir PowerPoint, crear una presentación en blanco, pegar el título y las viñetas de cada diapositiva e insertar la infografía del Paso 3.
3. Guardar como `Presentacion_Q1_[INICIALES].pptx`.

**Resultado esperado:** Una presentación de 6 diapositivas.

**Verificación:** La presentación incluye una diapositiva de recomendaciones.

### Paso 5: Revisar los entregables (1 min)

**Objetivo:** Confirmar que los tres entregables son consistentes.

1. Verificar que en la carpeta de la práctica estén el informe, la infografía y la presentación.

**Resultado esperado:** Tres entregables con las mismas cifras.

**Verificación:** El crecimiento total es **+8.5%** en los tres.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Cifras verificables | Comparar el informe con la tabla del Paso 1 | Coinciden todas las cifras |
| Desviación crítica | Revisar la sección de desviaciones | Menciona la caída del Sur y los márgenes de TRX-105 y TRX-108, menores a 5% |
| Prueba adversarial | Preguntar: *"¿Cuántas ventas tuvo la región Occidente?"* | Copilot debe indicar que el archivo no tiene esa región |

## Solución de Problemas

### Problema 1: Copilot no permite adjuntar el archivo de Excel

- **Síntomas:** El archivo no se carga o aparece un mensaje de formato no admitido.
- **Causa:** La versión o el tipo de cuenta limita los formatos.
- **Solución:** Cargar `Ventas_Trimestrales.csv`. Si tampoco se acepta, abrir el CSV con el Bloc de notas, copiar todo el contenido y pegarlo al final del prompt.

### Problema 2: Copilot no genera archivos descargables

- **Síntomas:** Solo entrega texto.
- **Causa:** La función de creación de archivos depende de la versión y la región.
- **Solución:** Copiar el contenido a Word y PowerPoint. El objetivo es que Copilot genere el contenido estructurado; el formato final puede hacerse a mano.

### Problema 3: Las cifras del análisis no coinciden

- **Síntomas:** Totales distintos a la tabla de referencia.
- **Causa:** Error de cálculo del modelo o lectura parcial del archivo.
- **Solución:** Pedir: *"Lista las 10 filas del archivo con sus ventas y vuelve a calcular los totales"*.

## Limpieza

1. Conservar el informe, la infografía y la presentación en `Documentos\Practicas_IA_Comercial\Practica09`.
2. Si la política de la empresa lo indica, eliminar la conversación y el archivo cargado del historial de Copilot.

## Resumen

- Se analizó un archivo de Excel con Copilot Chat gratuito y se verificaron las cifras.
- Se generaron un informe ejecutivo, una infografía y una presentación a partir del mismo análisis.
- Se identificaron los límites de la versión gratuita y cómo resolverlos.

---

[⬅ Anterior: Práctica 8](../Practica08/README.md) | [Inicio](../../README.md) | [Siguiente: Práctica 10 ➡](../Practica10/README.md)
