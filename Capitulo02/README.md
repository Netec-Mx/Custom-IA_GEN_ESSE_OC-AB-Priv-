# Práctica: Analizar un proceso comercial completo e identificar actividades susceptibles de automatizarse mediante Inteligencia Artificial, así como puntos críticos donde la IA puede fortalecer el control y seguimiento de la operación.

## Metadatos

| Campo | Valor |
| :--- | :--- |
| **Duración** | 42 minutos |
| **Complejidad** | Intermedia |
| **Nivel Bloom** | Aplicar |
| **Directorio de trabajo** | `~/laboratorios_ia_comercial/modulo2/` |
| **Archivo de salida principal** | `~/laboratorios_ia_comercial/modulo2/matriz_procesos.xlsx` |

## Descripción General

En este laboratorio práctico, el estudiante asume el rol de un Analista de Operaciones Comerciales para cartografiar, desglosar y auditar un ciclo comercial B2B completo de 5 fases (Prospección, Atención/Calificación, Propuesta, Cierre y Seguimiento/Retención). Utilizando un asistente de Inteligencia Artificial Generativa (OpenAI ChatGPT o Anthropic Claude), el estudiante evaluará un escenario comercial ficticio ("LogiTech Solutions S.A."), identificando micro-actividades manuales y repetitivas de bajo valor agregado, determinando los puntos críticos donde ocurren fugas de oportunidades o desviaciones de control, y estructurando los indicadores clave de rendimiento (KPIs) asociados a la velocidad del pipeline. Finalmente, el estudiante construirá y validará una matriz de priorización operativa en una hoja de cálculo (`matriz_procesos.xlsx`), clasificando cada iniciativa según su Impacto en el Negocio frente a su Facilidad de Implementación.

## Objetivos de Aprendizaje

Al finalizar este laboratorio, serás capaz de:

- **Desglosar** las 5 fases del ciclo comercial B2B (Prospección, Atención, Propuesta, Cierre y Seguimiento) utilizando modelos de lenguaje estructurados para documentar micro-actividades operativas.
- **Identificar** puntos críticos de control, fugas de pipeline y tareas repetitivas susceptibles de automatización mediante IA Generativa.
- **Formular** Indicadores Clave de Rendimiento (KPIs) específicos para medir la velocidad de pipeline y el control operativo en cada fase comercial.
- **Construir** una Matriz de Priorización Operativa en formato CSV/Excel categorizando las iniciativas por Impacto comercial vs. Facilidad técnica de implementación.
- **Auditar** la precisión de las recomendaciones generadas por la IA ante escenarios adversos o datos incompletos.

## Prerrequisitos

- Comprensión básica del ciclo de ventas B2B y sus etapas fundamentales.
- Manejo básico de la terminal de comandos de Linux/macOS o PowerShell en Windows.
- Familiaridad básica con el uso de hojas de cálculo (LibreOffice Calc o Microsoft Excel).
- Acceso activo a una interfaz web gratuita o de pago de Inteligencia Artificial Generativa (OpenAI ChatGPT o Anthropic Claude).

## Entorno de Laboratorio

### Herramientas y Versiones Específicas

| Software / Herramienta | Versión Declarada / Build | Licencia / Tipo | Enlace Oficial |
| :--- | :--- | :--- | :--- |
| **OpenAI ChatGPT Web** | GPT-4o / GPT-3.5 (Build 2024.05) | Gratuita / Plus Tier | [https://chatgpt.com](https://chatgpt.com) |
| **Anthropic Claude Web** | Claude 3.5 Sonnet (Build 2024.05) | Gratuita / Pro Tier | [https://claude.ai](https://claude.ai) |
| **LibreOffice Calc** | v24.2.2.3 (Linux x86_64) | Open Source (LGPLv3) | [https://www.libreoffice.org](https://www.libreoffice.org) |
| **Visual Studio Code** | v1.89.0 | Gratuita (MIT License) | [https://code.visualstudio.com](https://code.visualstudio.com) |
| **Python** | v3.10.12 (con `pandas` v2.2.2 y `openpyxl` v3.1.2) | Open Source (PSFL) | [https://www.python.org](https://www.python.org) |

### Estructura de Directorios

El entorno local debe contar con el siguiente directorio de trabajo inicializado:

```
~/laboratorios_ia_comercial/
└── modulo2/
    ├── datos_empresa.json
    ├── matriz_procesos.csv
    └── matriz_procesos.xlsx
```

## Instrucciones Paso a Paso

### Paso 1: Configurar el directorio de trabajo y verificar dependencias

**Objetivo:** Crear el subdirectorios de trabajo `~/laboratorios_ia_comercial/modulo2/` y verificar la disponibilidad de las herramientas locales para el procesamiento de datos.

1. Abre la consola de terminal en tu equipo.
2. Ejecuta los siguientes comandos para crear la estructura de directorios y verificar Python 3 y sus bibliotecas:

```bash
mkdir -p ~/laboratorios_ia_comercial/modulo2/
cd ~/laboratorios_ia_comercial/modulo2/
python3 --version
python3 -c "import pandas, openpyxl; print('Pandas y Openpyxl instalados correctamente.')"
```

3. Confirma que el directorio actual de trabajo es exactamente `~/laboratorios_ia_comercial/modulo2/`.

```bash
pwd
```

**Resultado esperado:** La terminal muestra la versión de Python (`Python 3.10.x`) y la confirmación de las bibliotecas `pandas` y `openpyxl`. La ruta devuelta por `pwd` finaliza en `/modulo2`.

**Verificación:** Ejecuta `ls -ld ~/laboratorios_ia_comercial/modulo2/` y comprueba que el directorio existe con permisos de escritura.

---

### Paso 2: Crear el archivo de datos del caso de estudio "LogiTech Solutions S.A."

**Objetivo:** Generar el archivo JSON local con la descripción operativa ficticia de la empresa B2B que servirá de entrada contextual para las consultas de IA.

1. En la terminal, dentro de `~/laboratorios_ia_comercial/modulo2/`, ejecuta el siguiente comando para generar `datos_empresa.json`:

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo2/datos_empresa.json
{
  "empresa": "LogiTech Solutions S.A.",
  "sector": "Servicios de Software y Logística B2B",
  "volumen_mensual_leads": 350,
  "fases_actuales": {
    "1_prospección": "Búsqueda manual de empresas en LinkedIn y directorios. Envío de correos fríos genéricos sin personalizar.",
    "2_atención_calificación": "Recepción de formularios web. Llamadas telefónicas de 20 min para validar presupuesto (BANT). Registro manual en CRM con retrasos de 24 a 48 horas.",
    "3_propuesta": "Elaboración individual de propuestas financieras en Word/Excel por cada ejecutivo. Demora promedio de 4 días hábiles.",
    "4_cierre": "Revisión legal manual de contratos, negociación de cláusulas por correo electrónico sin versionado centralizado.",
    "5_seguimiento_retención": "Encuesta anual de satisfacción manual. Alta tasa de cancelación (Churn del 14%) por falta de acompañamiento postventa."
  },
  "problemas_identificados": [
    "Tiempo de respuesta inicial a leads inbound: 30 horas.",
    "Cuello de botella en la elaboración de cotizaciones personalizadas.",
    "Falta de visibilidad sobre los KPIs de velocidad del pipeline.",
    "Carga administrativa manual del 45% del tiempo de los ejecutivos comercial."
  ]
}
EOF
```

2. Verifica la creación correcta del archivo ejecutando:

```bash
cat ~/laboratorios_ia_comercial/modulo2/datos_empresa.json | grep "empresa"
```

**Resultado esperado:** La terminal imprime `"empresa": "LogiTech Solutions S.A."`.

**Verificación:** Confirma que el archivo ocupa aproximadamente 1 KB utilizando el comando `ls -lh datos_empresa.json`.

---

### Paso 3: Configurar la sesión de IA Generativa con un Mensaje de Sistema (System Prompt)

**Objetivo:** Establecer el rol especializado y las restricciones operativas en la herramienta de IA Generativa (ChatGPT o Claude) antes de iniciar la interacción.

1. Abre tu navegador web e ingresa a tu herramienta de IA Generativa elegida (ChatGPT en [https://chatgpt.com](https://chatgpt.com) o Claude en [https://claude.ai](https://claude.ai)).
2. Inicia un **Nuevo Chat**.
3. Copia y envía el siguiente **mensaje de sistema / prompt de contexto inicial** para fijar la especialidad del modelo:

```text
[ROL Y CONTEXTO OPERATIVO]
Actúa como un Experto en Arquitectura de Procesos Comerciales B2B y Optimización con Inteligencia Artificial. Tu objetivo es analizar flujos de trabajo de ventas, identificar puntos de fricción, mapear micro-actividades y diseñar estrategias de automatización sin inventar datos no proporcionados.

[REGLAS ESTRICTAS DE RESPUESTA]
1. Mantén un tono técnico, estructurado y orientado a operaciones comerciales.
2. Basarás tus diagnósticos en las 5 fases estándar del ciclo B2B: Prospección, Atención/Calificación, Propuesta, Cierre y Seguimiento/Retención.
3. Si un dato no está especificado en el escenario, decláralo como "No especificado" o solicita aclaración antes de asumir.
4. No generes respuestas genéricas; utiliza tablas, listas con bullets explícitos y estructuras claras.
```

4. Observa la confirmación del asistente.

**Resultado esperado:** La IA confirma el rol recibido, indicando que está lista para analizar la operación comercial bajo las reglas establecidas.

**Verificación:** Asegúrate de que el asistente no comience a responder antes de recibir la información del escenario.

---

### Paso 4: Ejecutar la extracción estructurada de las 5 fases comerciales

**Objetivo:** Introducir el escenario operativo de "LogiTech Solutions S.A." a la IA y obtener la matriz inicial de micro-actividades y cuellos de botella por fase.

1. Copia el contenido del archivo `datos_empresa.json` o utiliza el siguiente **Prompt Estructurado #1** adaptado:

```text
[TAREA: DIAGNÓSTICO DE FASES OPERATIVAS]
Analiza la siguiente información de la empresa "LogiTech Solutions S.A." y genera un desglose en formato de tabla markdown con las siguientes columnas:
- Fase Comercial
- Micro-actividades Actuales (Detalladas)
- Puntos de Fricción / Cuellos de Botella Identificados
- Tiempo / Carga Operativa Estimada

[INFORMACIÓN DE LA EMPRESA]
- Sector: Servicios de Software y Logística B2B
- Volumen: 350 leads/mes
- Prospección: Búsqueda manual en LinkedIn; correos fríos genéricos.
- Atención/Calificación: Llamadas BANT de 20 min; retraso de 24-48h en registro CRM.
- Propuesta: Redacción manual de propuestas Word/Excel (4 días hábiles).
- Cierre: Revisión legal manual por correos sin versionado centralizado.
- Seguimiento: Encuesta anual manual; Churn del 14% por falta de onboarding.
- Tiempo de respuesta inbound: 30 horas. Carga administrativa: 45%.
```

2. Envía el prompt en el chat de la IA.

**Resultado esperado:** El asistente genera una tabla de 5 filas (una por cada fase) detallando las micro-actividades, las fricciones asociadas y el nivel de carga operativa.

**Verificación:** Valida que las 5 fases especificadas en la lección (`Prospección`, `Atención/Calificación`, `Propuesta`, `Cierre` y `Seguimiento/Retención`) estén presentes sin omisión.

---

### Paso 5: Analizar e identificar actividades automatizables con IA Generativa

**Objetivo:** Solicitar a la IA la identificación técnica de cuáles tareas dentro de las 5 fases son repetitivas y automatizables mediante soluciones Low-Code o modelos de lenguaje.

1. Envía el siguiente **Prompt Estructurado #2** en la misma conversación:

```text
[TAREA: IDENTIFICACIÓN DE OPORTUNIDADES DE AUTOMATIZACIÓN E IA]
Para cada una de las 5 fases analizadas anteriormente, identifica las actividades repetitivas que se pueden automatizar o potenciar con IA. Responde en una tabla con las columnas:
1. Fase
2. Tarea Repetitiva Identificada
3. Solución de IA / Automatización Sugerida (indicar si requiere IA Generativa, Automatización Low-Code o Integración CRM)
4. Tipo de Intervención (Ej. Asistente Virtual, Generación de Texto, Enrutamiento de Leads, Análisis Documental)

Asegúrate de NO proponer herramientas de pago complejas que requieran desarrollo a medida de alto costo; prioriza soluciones aplicables con herramientas estándar como ChatGPT/Claude y flujos en n8n.
```

2. Analiza los resultados entregados por el asistente.

**Resultado esperado:** Una tabla detallada que especifica la tarea repetitiva por fase (ejemplo: redactar correos fríos, calificar leads inbound, redactar borradores de propuestas, auditar cláusulas contractuales, enviar mensajes de onboarding) junto con el tipo de herramienta sugerida.

**Verificación:** Comprueba que cada fase tenga al menos una oportunidad de automatización asignada concretamente.

---

### Paso 6: Formular los Indicadores Clave de Rendimiento (KPIs) de la Operación

**Objetivo:** Definir los indicadores cuantitativos para controlar el impacto de la automatización y monitorear la velocidad del pipeline comercial.

1. Envía el siguiente **Prompt Estructurado #3** en el chat:

```text
[TAREA: MATRIZ DE KPIs Y CONTROL OPERATIVO]
Con base en la Ecuación de Velocidad del Pipeline (Velocidad = [Leads * Deal Size * Win Rate] / Duración Ciclo), define los KPIs de control operativo para las 5 fases de LogiTech Solutions S.A.

Genera una tabla con las siguientes columnas:
- Fase Comercial
- KPI Operativo Principal
- Fórmula o Método de Medición
- Meta Objetivo Sugerida (Mejora esperada con IA)
- Punto Crítico de Control (Evento donde la IA debe alertar sobre una desviación)
```

2. Revisa la salida generada por la IA.

**Resultado esperado:** La IA presenta KPIs como "Tiempo de Primera Respuesta (TTR)", "Tasa de Conversión Lead-to-SQL", "Días de Elaboración de Propuesta", "Tiempo de Ciclo Contractual", y "Tasa de Cancelación Temprana (Early Churn Rate)", acompañados de puntos críticos de alerta.

**Verificación:** Asegúrate de que las metas propuestas sean realistas (por ejemplo, reducir el tiempo de respuesta de 30 horas a menos de 1 hora).

---

### Paso 7: Generar la Matriz de Priorización Operativa en formato CSV

**Objetivo:** Consolidar el análisis anterior en una estructura matricial de priorización (Impacto vs. Facilidad) exportable en formato CSV estándar.

1. Envía el siguiente **Prompt Estructurado #4** al asistente de IA:

```text
[TAREA: CONSOLIDACIÓN EN FORMATO CSV ESTRUCTURADO]
Consolida los análisis anteriores en un único bloque de código en formato CSV estructurado. Utiliza exactamente el carácter coma (,) como separador y asegúrate de encerrar entre comillas dobles (") las cadenas que contengan comas internas.

Las columnas obligatorias son:
ID,Fase,Iniciativa_IA,Impacto_Negocio,Facilidad_Implementacion,Cuadrante_Prioridad,KPI_Asociado

Criterios de clasificación para Cuadrante_Prioridad:
- Impacto Alto / Facilidad Alta = "Victoria Rápida (Quick Win)"
- Impacto Alto / Facilidad Baja = "Proyecto Estratégico"
- Impacto Bajo / Facilidad Alta = "Tarea Secundaria"
- Impacto Bajo / Facilidad Baja = "Descartar"

Genera al menos 1 iniciativa por cada una de las 5 fases. Devuelve ÚNICAMENTE el bloque de código CSV sin explicaciones adicionales.
```

2. Copia el bloque CSV entregado por la IA.

**Resultado esperado:** Un bloque de texto plano en formato CSV con cabeceras y 5 a 7 filas de datos.

**Verificación:** Comprueba que las columnas sigan exactamente los nombres especificados y no contengan saltos de línea anómalos.

---

### Paso 8: Guardar el archivo CSV en el directorio local

**Objetivo:** Almacenar la respuesta generada en la terminal local como `matriz_procesos.csv`.

1. En la terminal de tu equipo, abre el editor de texto de tu preferencia (ej. `nano`) o utiliza `cat` para crear el archivo.

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo2/matriz_procesos.csv
ID,Fase,Iniciativa_IA,Impacto_Negocio,Facilidad_Implementacion,Cuadrante_Prioridad,KPI_Asociado
1,Prospección,Generación de borradores de correos personalizados con ChatGPT,Alto,Alta,Victoria Rápida (Quick Win),Tasa de Respuesta Outreach
2,Atención/Calificación,Calificación automática de leads inbound mediante chatbot/prompts,Alto,Alta,Victoria Rápida (Quick Win),Tiempo de Primera Respuesta (TTR)
3,Propuesta,Automatización de plantillas de propuestas con IA Generativa,Alto,Baja,Proyecto Estratégico,Días de Elaboración de Propuesta
4,Cierre,Revisión y comparación asistida de contratos legales con Claude,Medio,Alta,Victoria Rápida (Quick Win),Tiempo de Ciclo Contractual
5,Seguimiento/Retención,Generación de secuencias de onboarding y alertas de churn con IA,Alto,Baja,Proyecto Estratégico,Net Revenue Retention (NRR)
EOF
```

2. Verifica que el archivo no esté vacío ejecutando:

```bash
cat ~/laboratorios_ia_comercial/modulo2/matriz_procesos.csv
```

**Resultado esperado:** La terminal despliega el contenido de 6 líneas (cabecera + 5 filas).

**Verificación:** Ejecuta `wc -l ~/laboratorios_ia_comercial/modulo2/matriz_procesos.csv` y confirma que la salida sea `6`.

---

### Paso 9: Convertir y formatear la Matriz a Excel (`matriz_procesos.xlsx`) mediante Python

**Objetivo:** Procesar el archivo CSV y generar el entregable final en formato Excel profesional con múltiples pestañas y formato estructurado.

1. Crea el script de conversión en Python ejecutando en la terminal:

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo2/convertir_matriz.py
import pandas as pd
import openpyxl
from openpyxl.styles import Font, PatternFill, Alignment, Border, Side

## 1. Cargar CSV
csv_path = 'matriz_procesos.csv'
xlsx_path = 'matriz_procesos.xlsx'

df = pd.read_csv(csv_path)

## 2. Crear archivo Excel con openpyxl
wb = openpyxl.Workbook()
ws = wb.active
ws.title = "Matriz de Priorización"

## Escribir cabeceras
headers = list(df.columns)
ws.append(headers)

## Estilos visuales
header_fill = PatternFill(start_color="1F4E78", end_color="1F4E78", fill_type="solid")
header_font = Font(name="Calibri", size=11, bold=True, color="FFFFFF")
data_font = Font(name="Calibri", size=10)
thin_border = Border(
    left=Side(style='thin', color='D9D9D9'),
    right=Side(style='thin', color='D9D9D9'),
    top=Side(style='thin', color='D9D9D9'),
    bottom=Side(style='thin', color='D9D9D9')
)

for col_num, header in enumerate(headers, 1):
    cell = ws.cell(row=1, column=col_num)
    cell.fill = header_fill
    cell.font = header_font
    cell.alignment = Alignment(horizontal="center", vertical="center")

## Escribir datos
for row_idx, row in df.iterrows():
    row_data = list(row)
    ws.append(row_data)
    current_row = row_idx + 2
    for col_idx in range(1, len(row_data) + 1):
        cell = ws.cell(row=current_row, column=col_idx)
        cell.font = data_font
        cell.border = thin_border
        if col_idx in [1, 4, 5, 6]:
            cell.alignment = Alignment(horizontal="center")

## Ajustar ancho de columnas automáticamentes
for col in ws.columns:
    max_len = max(len(str(cell.value or '')) for cell in col)
    col_letter = openpyxl.utils.get_column_letter(col[0].column)
    ws.column_dimensions[col_letter].width = max(max_len + 4, 12)

wb.save(xlsx_path)
print(f"Archivo Excel generado exitosamente en: {xlsx_path}")
EOF
```

2. Ejecuta el script de Python:

```bash
python3 ~/laboratorios_ia_comercial/modulo2/convertir_matriz.py
```

**Resultado esperado:** La terminal muestra `Archivo Excel generado exitosamente en: matriz_procesos.xlsx`.

**Verificación:** Verifica la presencia del archivo ejecuntando `ls -la ~/laboratorios_ia_comercial/modulo2/matriz_procesos.xlsx`.

---

### Paso 10: Auditar y evaluar las limitaciones del análisis generado por la IA (Prueba Adversarial)

**Objetivo:** Identificar alucinaciones, inconsistencias o datos no fundamentados en la respuesta de la IA mediante un prompt de auditoría de calidad.

1. Regresa al chat con la IA Generativa e ingresa el siguiente **Prompt de Auditoría (Prueba Adversarial)**:

```text
[TAREA: AUDITORÍA DE CALIDAD Y DETECCIÓN DE ALUCINACIONES]
Revisa estrictamente la Matriz de Priorización propuesta anteriormente en comparación con los datos originales proporcionados de "LogiTech Solutions S.A.".

Responde a las siguientes 3 preguntas de control:
1. ¿Incluiste algún indicador o meta que Asuma capacidades técnicas no mencionadas en los datos originales?
2. ¿Existen estimaciones financieras de ROI concretas que representen alucinaciones (datos inventados sin sustento)?
3. Justifica por qué la iniciativa "Automatización de plantillas de propuestas" se clasificó como "Proyecto Estratégico" en lugar de "Victoria Rápida".

Devuelve tu respuesta en un formato de informe breve con conclusiones claras.
```

2. Lee con atención la respuesta proporcionada por la IA.

**Resultado esperado:** El asistente admite limitaciones en las estimaciones numéricas exactas que no venían en el texto base (ej. porcentajes exactos de incremento en tasa de conversión) y justifica lógicamente la clasificación del cuadrante basándose en la complejidad de integración del CRM con el generador de documentos.

**Verificación:** Confirma que el asistente reconozca explícitamente qué partes del análisis provienen de inferencias genéricas de mercado y cuáles provienen directamente del contexto original.

---

## Validación y Pruebas

Para garantizar que los objetivos del laboratorio se hayan cumplido satisfactoriamente, ejecuta la siguiente suite de verificación local en Python.

1. Crea el script de verificación automatizada en `~/laboratorios_ia_comercial/modulo2/validar_lab.py`:

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo2/validar_lab.py
import os
import pandas as pd

print("=== INICIANDO VERIFICACIÓN DE LABORATORIO 02-00-01 ===")

## Test 1: Verificar existencia de archivos
archivos_requeridos = ['datos_empresa.json', 'matriz_procesos.csv', 'matriz_procesos.xlsx']
for archivo in archivos_requeridos:
    ruta = os.path.join(os.path.expanduser('~/laboratorios_ia_comercial/modulo2'), archivo)
    if os.path.exists(ruta):
        print(f"[PASS] Archivo encontrado: {archivo}")
    else:
        print(f"[FAIL] Archivo ausente: {archivo}")

## Test 2: Validar estructura del CSV
try:
    csv_path = os.path.expanduser('~/laboratorios_ia_comercial/modulo2/matriz_procesos.csv')
    df = pd.read_csv(csv_path)
    columnas_esperadas = ['ID', 'Fase', 'Iniciativa_IA', 'Impacto_Negocio', 'Facilidad_Implementacion', 'Cuadrante_Prioridad', 'KPI_Asociado']
    
    if list(df.columns) == columnas_esperadas:
        print("[PASS] Estructura de columnas en CSV es correcta.")
    else:
        print(f"[FAIL] Columnas incorrectas en CSV. Se esperaba: {columnas_esperadas}")
        
    if len(df) >= 5:
        print(f"[PASS] El CSV contiene {len(df)} iniciativas (mínimo 5 requeridas).")
    else:
        print(f"[FAIL] El CSV contiene solo {len(df)} filas.")
        
except Exception as e:
    print(f"[FAIL] Error al procesar CSV: {str(e)}")

print("=== VERIFICACIÓN FINALIZADA ===")
EOF
```

2. Ejecuta el script de prueba:

```bash
python3 ~/laboratorios_ia_comercial/modulo2/validar_lab.py
```

**Criterios de Aceptación Evaluables:**
- Los 3 archivos (`datos_empresa.json`, `matriz_procesos.csv`, `matriz_procesos.xlsx`) existen en la ruta indicada.
- La matriz incluye exactamente las 7 columnas especificadas sin errores de formato.
- Se identifican iniciativas claras para las 5 fases comerciales sin dejar campos vacíos.

---

## Solución de Problemas

### Problema 1: La IA responde con texto narrativo en lugar de entregar el bloque en formato CSV estructurado

- **Síntoma:** El asistente de IA responde con explicaciones largas, viñetas o fragmentos incompletos de texto y omite los encabezados del CSV.
- **Causa Raíz:** El modelo de lenguaje interpretó el prompt como una solicitud analítica abierta en lugar de un comando estricto de formateo de datos.
- **Solución:** Reenvía un prompt de corrección estricto obligando la salida en un bloque de código markdown:
  ```text
  [CORRECCIÓN DE FORMATO]
  No incluyas introducciones ni explicaciones. Responde ÚNICAMENTE con una ventana de código delimitada por ```csv conteniendo el texto CSV válido con las columnas: ID,Fase,Iniciativa_IA,Impacto_Negocio,Facilidad_Implementacion,Cuadrante_Prioridad,KPI_Asociado
  ```

---

### Problema 2: Error al ejecutar el script de Python `convertir_matriz.py` por falta del módulo `openpyxl` o `pandas`

- **Síntoma:** La terminal muestra `ModuleNotFoundError: No module named 'openpyxl'` o `ModuleNotFoundError: No module named 'pandas'`.
- **Causa Raíz:** Las bibliotecas de procesamiento de datos no están instaladas en el entorno global de Python del sistema.
- **Solución:** Instala los paquetes requeridos utilizando `pip3` dentro de la terminal:
  ```bash
  pip3 install pandas openpyxl
  ```
  Si trabajas en un sistema administrado donde `pip` está restringido, utiliza la instalación por paquetes del sistema operativo o activa un entorno virtual:
  ```bash
  python3 -m venv ~/laboratorios_ia_comercial/venv
  source ~/laboratorios_ia_comercial/venv/bin/activate
  pip install pandas openpyxl
  ```

---

## Limpieza

Una vez terminadas todas las comprobaciones y validaciones del laboratorio, puedes eliminar los scripts auxiliares de verificación si deseas mantener limpio el directorio, conservando los artefactos principales del trabajo realizado:

1. Elimina los scripts Python temporales de conversión y validación:

```bash
rm -f ~/laboratorios_ia_comercial/modulo2/convertir_matriz.py
rm -f ~/laboratorios_ia_comercial/modulo2/validar_lab.py
```

2. Verifica que los archivos definitivos permanezcan intactos:

```bash
ls -la ~/laboratorios_ia_comercial/modulo2/
```

**Resultado esperado de la limpieza:** Permanece únicamente la información original y los entregables (`datos_empresa.json`, `matriz_procesos.csv`, `matriz_procesos.xlsx`).

---

## Resumen

En este laboratorio has completado con éxito el análisis integral de una operación comercial B2B mediante herramientas de Inteligencia Artificial Generativa:

1. **Mapeo Operativo:** Desglosaste el flujo completo de ventas en sus 5 fases fundamentales (Prospección, Atención/Calificación, Propuesta, Cierre y Seguimiento/Retención).
2. **Identificación de Fricciones:** Localizaste las tareas repetitivas de bajo valor añadido y los cuellos de botella que desaceleran la velocidad del pipeline comercial.
3. **Definición de Métricas y Controles:** Formulaste los KPIs clave y los puntos de control para monitorear desviaciones operativas.
4. **Priorización y Exportación:** Construiste y validaste una Matriz de Priorización Operativa (`matriz_procesos.xlsx`) categorizando iniciativas por su nivel de Impacto en el Negocio vs. Facilidad técnica de implementación.
5. **Auditoría Antialucinación:** Evaluaste críticamente la calidad de las respuestas del modelo generativo identificando suposiciones sin sustento.
