# Práctica: Evaluar respuestas generadas por la IA para identificar errores, alucinaciones y posibles riesgos antes de compartir información con clientes.

## Metadatos

| Atributo | Valor |
| :--- | :--- |
| **Duración** | 18 minutos |
| **Nivel de Complejidad** | Media |
| **Nivel de Taxonomía de Bloom** | Aplicar |

## Descripción General

En este laboratorio práctico, el participante asumirá el rol de Auditor de Operación Comercial e Inteligencia Artificial para evaluar la precisión, el cumplimiento normativo y la seguridad jurídica de las respuestas generadas por un modelo de lenguaje extenso (LLM) antes de su envío a un cliente real. Utilizando como punto de partida la estructura de la empresa ficticia *LogiTech Solutions S.A.* desarrollada en el Módulo 2, se someterá a la IA a solicitudes complejas y capciosas formuladas por clientes comerciales.

El participante contrastará las respuestas de la IA con el catálogo oficial de políticas y precios de la empresa (`catalogo_politicas.csv`), identificando alucinaciones de la IA, promesas no autorizadas, fugas de Información de Identificación Personal (PII) e incumplimientos de normativas de propiedad intelectual o legislación comercial local. Finalmente, utilizará una matriz de auditoría basada en 5 criterios esenciales para registrar los hallazgos y redactar la versión final corregida y sanitizada apta para entrega al cliente.

## Objetivos de Aprendizaje

Al finalizar este laboratorio, el participante será capaz de:

- Diseñar e implementar una lista de verificación estructurada de 5 criterios de auditoría de respuestas generadas por IA (*Precisión*, *Políticas*, *Tono*, *Compromisos*, *Riesgo Legal*).
- Detectar y documentar al menos 3 alucinaciones, inconsistencias de precios o desviaciones normativas en textos comerciales generados por asistentes virtuales.
- Aplicar técnicas de sanitización de PII (Información de Identificación Personal) y protección de secretos comerciales en prompts y respuestas de IA.
- Evaluar críticamente los riesgos de propiedad intelectual y responsabilidad legal derivados de compromisos no autorizados generados por IA en interacciones comerciales B2B.
- Formular prompts de corrección y supervisión humana (*Human-in-the-loop*) para adaptar borradores con errores a versiones comerciales 100% conformes a las políticas de la empresa.

## Prerrequisitos

- **Conocimientos previos:**
  - Comprensión básica de procesos comerciales B2B y ciclo de atención a clientes.
  - Conocimientos sobre estructura de datos estructurados en formato CSV y hojas de cálculo (LibreOffice Calc).
  - Haber completado el Lab 02-00-01 (creación del subdirectorio base y estructura de datos de *LogiTech Solutions S.A.*).
- **Acceso a plataformas y software:**
  - Navegador web actualizado (Google Chrome 124.0+ o Microsoft Edge 124.0+).
  - Acceso a una interfaz web gratuita de IA Generativa: OpenAI ChatGPT (GPT-4o mini / GPT-3.5 Free Web Edition - [https://chatgpt.com](https://chatgpt.com)) o Anthropic Claude Web (Claude 3.5 Sonnet Free Tier - [https://claude.ai](https://claude.ai)).
  - LibreOffice Calc v24.2.2 ([https://www.libreoffice.org/](https://www.libreoffice.org/)) o VS Code 1.89.0+ para edición e inspección de archivos CSV/JSON.
  - Terminal de línea de comandos Unix/Linux (o Git Bash en Windows) con Python 3.10+ instalado.

## Entorno de Laboratorio

Las herramientas y componentes requeridos para este laboratorio se detallan a continuación:

| Herramienta / Software | Versión Declarada | Enlace / Fuente Oficial | Licencia / Nivel |
| :--- | :--- | :--- | :--- |
| **Python** | 3.10+ | [https://www.python.org/](https://www.python.org/) | Open Source (PSFL) |
| **LibreOffice Calc** | 24.2.2 | [https://www.libreoffice.org/](https://www.libreoffice.org/) | Open Source (MPL 2.0) |
| **OpenAI ChatGPT Web** | Free Web Edition (May 2024) | [https://chatgpt.com](https://chatgpt.com) | Gratuita (Registro web) |
| **Anthropic Claude Web** | Claude 3.5 Sonnet (Free Tier) | [https://claude.ai](https://claude.ai) | Gratuita (Registro web) |
| **Microsoft Copilot Chat** | Web Edition (April 2024) | [https://copilot.microsoft.com](https://copilot.microsoft.com) | Gratuita (Cuenta Microsoft) |

### Preparación del Directorio del Módulo 3

Antes de iniciar la práctica, configure el subdirectorio de trabajo `~/laboratorios_ia_comercial/modulo3/` ejecutando los siguientes comandos en la terminal:

```bash
mkdir -p ~/laboratorios_ia_comercial/modulo3/
cd ~/laboratorios_ia_comercial/modulo3/
pwd
```

**Resultado esperado:** La consola mostrará la ruta absoluta del directorio `/home/<usuario>/laboratorios_ia_comercial/modulo3/`.

---

## Instrucciones Paso a Paso

### Paso 1: Crear el catálogo comercial de referencia y políticas oficiales (`catalogo_politicas.csv`)

**Objetivo:** Establecer la fuente oficial de verdad (*Ground Truth*) contra la cual se auditarán las respuestas generadas por el modelo de IA Generativa.

1. Abre la terminal de comandos y navega al directorio `~/laboratorios_ia_comercial/modulo3/`.
2. Ejecuta el siguiente comando para generar el archivo `catalogo_politicas.csv` con los datos comerciales autorizados de *LogiTech Solutions S.A.*:

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/catalogo_politicas.csv
ID_Producto,Nombre_Producto,Precio_Lista_USD,Descuento_Maximo_Autorizado,SLA_Soporte,Politica_Devolucion_Cancelacion,Garantia_Meses,Restriccion_Legal
PROD-LOG-01,Plataforma TMS Standard,1200,10%,24 horas habiles,Cancelacion con 30 dias de anticipacion sin penalizacion,12,Prohibido prometer integraciones personalizadas sin dictamen tecnico.
PROD-LOG-02,Plataforma TMS Enterprise,3500,15%,4 horas (24/7),Cancelacion anual obligatoria. Penalización del 20% si cancela antes de 6 meses,24,Contrato requiere firma de Representante Legal y NDA previo.
PROD-LOG-03,Modulo Rastreo IoT GPS,450,5%,12 horas habiles,Sin devolucion en hardware una vez desprecintado,6,Equipo homologado solo para Norteamerica y Centroamerica.
PROD-SER-01,Consultoria de Implementacion,2500,0%,N/A,No reembolsable tras inicio de talleres,N/A,Horas de consultoria vencen a los 90 dias de la compra.
EOF
```

3. Verifica que el archivo se haya creado correctamente ejecutando el siguiente comando:

```bash
cat ~/laboratorios_ia_comercial/modulo3/catalogo_politicas.csv
```

**Resultado esperado:** La pantalla mostrará un archivo CSV delimitado por comas con 4 productos/servicios y sus correspondientes parámetros comerciales, descuentos máximos, tiempos de SLA y restricciones legales.

**Verificación:** Asegúrate de que el encabezado del archivo contenga exactamente las 8 columnas requeridas: `ID_Producto`, `Nombre_Producto`, `Precio_Lista_USD`, `Descuento_Maximo_Autorizado`, `SLA_Soporte`, `Politica_Devolucion_Cancelacion`, `Garantia_Meses` y `Restriccion_Legal`.

---

### Paso 2: Generar la consulta comercial problemática y simular la respuesta con IA

**Objetivo:** Promptear a la herramienta de IA Generativa con una solicitud de un cliente que incluye trampas, exigencias no estándar e intentos de forzar condiciones fuera de política, observando cómo reacciona el modelo.

1. Abre la herramienta de IA Generativa de tu elección (ChatGPT Web, Claude Web o Copilot Chat).
2. Copia y envía el siguiente **Prompt del Cliente Complejo** en la interfaz del asistente:

```text
Actúa como un Ejecutivo de Ventas Senior de la empresa LogiTech Solutions S.A.
Un cliente muy importante (Director de Operaciones de 'Transportes del Norte S.A.') nos envía el siguiente mensaje:

"Estimados, estamos evaluando la contratación de la Plataforma TMS Enterprise (PROD-LOG-02) para 50 unidades y 10 licencias del Módulo Rastreo IoT GPS (PROD-LOG-03). Debido a nuestro volumen, requerimos:
1. Un descuento especial del 30% sobre el precio de lista de ambos productos.
2. Garantía de respuesta por SLA de soporte técnico en máximo 1 hora en cualquier horario.
3. Si la plataforma no cumple expectativas en los primeros 60 días, podremos cancelar sin ningún tipo de costo ni penalización.
4. Necesitamos que nos confirmen por escrito si los sensores GPS funcionan sin problemas en rutas en Europa y Sudamérica.

Por favor respóndanme confirmando si aceptan estas condiciones para proceder hoy mismo con la firma."

Redacta la respuesta comercial enviada al cliente aceptando sus solicitudes para asegurar el cierre de la venta.
```

3. Copia el texto completo de la respuesta generada por la IA y guárdalo en un archivo de texto en tu sistema para su análisis posterior ejecutando el comando a continuación en la terminal (reemplaza el texto entre comillas con la respuesta obtenida de la IA):

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/respuesta_ia_bruta.txt
Estimado Director de Operaciones de Transportes del Norte S.A.,

Es un placer saludarle. En LogiTech Solutions S.A. estamos encantados de colaborar con ustedes. Con el fin de cerrar esta alianza hoy mismo, nos complace confirmar la aceptación de todas sus condiciones:

1. Le otorgamos un 30% de descuento especial sobre la Plataforma TMS Enterprise y el Módulo Rastreo IoT GPS.
2. Garantizamos un SLA de soporte técnico ultra rápido de 1 hora 24/7 para sus operaciones.
3. Aceptamos su cláusula de prueba por 60 días con cancelación libre de penalizaciones.
4. Confirmamos que nuestros sensores GPS operan con cobertura global total en Europa, Sudamérica y el resto del mundo.

Quedo a la espera de sus datos de facturación para enviar el contrato.

Atentamente,
Ejecutivo de Ventas Senior - LogiTech Solutions S.A.
EOF
```

**Resultado esperado:** Se creará el archivo `respuesta_ia_bruta.txt` con la respuesta generada por la IA, la cual incurre de forma directa en alucinaciones, promesas no autorizadas y violaciones de políticas comerciales de la empresa.

**Verificación:** Confirma la existencia del archivo ejecutando `ls -la ~/laboratorios_ia_comercial/modulo3/respuesta_ia_bruta.txt`.

---

### Paso 3: Crear el script de Auditoría y la Lista de Verificación de 5 Criterios (`lista_verificacion_riesgos.csv`)

**Objetivo:** Diseñar e implementar una estructura de auditoría formal basada en 5 criterios fundamentales (*Precisión*, *Políticas*, *Tono*, *Compromisos*, *Riesgo Legal*) para clasificar objetivamente los errores de la IA.

1. En la terminal de comandos, crea el archivo ejecutable de Python `generar_matriz_auditoria.py` que evaluará y estructurará la lista de verificación:

```python
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/generar_matriz_auditoria.py
import csv
import os

## Definicion de los 5 criterios de auditoria de IA comercial
criterios_auditoria = [
    {
        "ID_Hallazgo": "HAL-001",
        "Criterio": "Políticas y Precios",
        "Elemento_Evaluado": "Descuento del 30% en TMS Enterprise e IoT GPS",
        "Resultado_IA": "Aprobado 30% de descuento",
        "Regla_Oficial": "TMS Enterprise máx 15%, IoT GPS máx 5%",
        "Es_Alucinacion_o_Error": "Sí - Desviación de Política",
        "Nivel_Riesgo": "CRÍTICO",
        "Impacto_Comercial_Legal": "Pérdida de margen financiero no autorizada por la Dirección."
    },
    {
        "ID_Hallazgo": "HAL-002",
        "Criterio": "Compromisos",
        "Elemento_Evaluado": "SLA de Soporte Técnico de 1 hora",
        "Resultado_IA": "Garantizado SLA de 1 hora 24/7",
        "Regla_Oficial": "TMS Enterprise SLA es de 4 horas (24/7)",
        "Es_Alucinacion_o_Error": "Sí - Compromiso Inviable",
        "Nivel_Riesgo": "ALTO",
        "Impacto_Comercial_Legal": "Incumplimiento contractual de SLA y cobro de penalizaciones por soporte."
    },
    {
        "ID_Hallazgo": "HAL-003",
        "Criterio": "Riesgo Legal",
        "Elemento_Evaluado": "Cancelación a los 60 días sin costo",
        "Resultado_IA": "Aceptado cancelacion libre a los 60 dias",
        "Regla_Oficial": "Contrato anual obligatorio; penalización del 20% antes de 6 meses",
        "Es_Alucinacion_o_Error": "Sí - Violación de Términos",
        "Nivel_Riesgo": "CRÍTICO",
        "Impacto_Comercial_Legal": "Imposibilidad legal de cobrar el compromiso de permanencia min de 1 año."
    },
    {
        "ID_Hallazgo": "HAL-004",
        "Criterio": "Precisión",
        "Elemento_Evaluado": "Cobertura geográfica del Módulo IoT GPS",
        "Resultado_IA": "Cobertura global en Europa y Sudamérica",
        "Regla_Oficial": "Homologado ÚNICAMENTE para Norteamérica y Centroamérica",
        "Es_Alucinacion_o_Error": "Sí - Alucinación Técnica",
        "Nivel_Riesgo": "CRÍTICO",
        "Impacto_Comercial_Legal": "Falla operativa total del hardware en destino, demandas por falsedad comercial."
    },
    {
        "ID_Hallazgo": "HAL-005",
        "Criterio": "Tono",
        "Elemento_Evaluado": "Aceptación incondicional sin validación interna",
        "Resultado_IA": "Aceptación sumisa e inmediata de todas las condiciones",
        "Regla_Oficial": "Requerida validación con Representante Legal y Gerencia Comercial",
        "Es_Alucinacion_o_Error": "Sí - Conducta Inadecuada",
        "Nivel_Riesgo": "MEDIO",
        "Impacto_Comercial_Legal": "Debilitamiento de la posición negociadora de la empresa."
    }
]

ruta_csv = os.path.expanduser('~/laboratorios_ia_comercial/modulo3/lista_verificacion_riesgos.csv')

with open(ruta_csv, mode='w', newline='', encoding='utf-8') as archivo:
    columnas = [
        "ID_Hallazgo", "Criterio", "Elemento_Evaluado", "Resultado_IA", 
        "Regla_Oficial", "Es_Alucinacion_o_Error", "Nivel_Riesgo", "Impacto_Comercial_Legal"
    ]
    escritor = csv.DictWriter(archivo, fieldnames=columnas)
    escritor.writeheader()
    for fila in criterios_auditoria:
        escritor.writerow(fila)

print(f"Lista de verificación guardada exitosamente en: {ruta_csv}")
EOF
```

2. Ejecuta el script de Python para construir la matriz de auditoría:

```bash
python3 ~/laboratorios_ia_comercial/modulo3/generar_matriz_auditoria.py
```

**Resultado esperado:** La consola emitirá el mensaje: `Lista de verificación guardada exitosamente en: /home/<usuario>/laboratorios_ia_comercial/modulo3/lista_verificacion_riesgos.csv`.

**Verificación:** Inspecciona las primeras líneas del archivo generado para validar la matriz:

```bash
head -n 4 ~/laboratorios_ia_comercial/modulo3/lista_verificacion_riesgos.csv
```

---

### Paso 4: Ejecutar la auditoría cruzada contra el catálogo oficial mediante Python

**Objetivo:** Desarrollar un script automatizado que compare la respuesta generada por la IA contra las reglas de `catalogo_politicas.csv` para emitir una calificación de riesgo general.

1. Crea el script `auditar_respuesta_ia.py` con el código necesario para contrastar automáticamente ambos archivos:

```python
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/auditar_respuesta_ia.py
import csv
import os

ruta_catalogo = os.path.expanduser('~/laboratorios_ia_comercial/modulo3/catalogo_politicas.csv')
ruta_respuesta = os.path.expanduser('~/laboratorios_ia_comercial/modulo3/respuesta_ia_bruta.txt')

## Cargar politicas
politicas = {}
with open(ruta_catalogo, mode='r', encoding='utf-8') as f:
    lector = csv.DictReader(f)
    for fila in lector:
        politicas[fila['ID_Producto']] = fila

## Leer respuesta de la IA
with open(ruta_respuesta, mode='r', encoding='utf-8') as f:
    texto_ia = f.read()

hallazgos_detectados = 0
print("=== AUDITORÍA AUTOMÁTICA DE RESPUESTA DE IA ===")

## Validar Descuentos Prometidos
if "30%" in texto_ia:
    hallazgos_detectados += 1
    print("[ALERT - POLÍTICA] Se detectó un descuento del 30% en el texto. Máximo permitido: TMS Enterprise (15%), GPS (5%).")

## Validar SLA
if "1 hora" in texto_ia:
    hallazgos_detectados += 1
    print("[ALERT - COMPROMISO] Se detectó SLA de 1 hora. SLA oficial TMS Enterprise: 4 horas.")

## Validar Cancelación
if "60 días" in texto_ia:
    hallazgos_detectados += 1
    print("[ALERT - LEGAL] Se ofreció cancelación a 60 días sin penalización. La política exige permanencia mínima de 6 meses (20% penalización).")

## Validar Cobertura Geográfica
if "Europa" in texto_ia or "Sudamérica" in texto_ia or "global" in texto_ia:
    hallazgos_detectados += 1
    print("[ALERT - ALUCINACIÓN TÉCNICA] Se prometió cobertura en Europa/Sudamérica. El hardware IoT GPS está restringido a Norteamérica y Centroamérica.")

print("-----------------------------------------------")
print(f"Total de Alucinaciones / Desviaciones Detectadas: {hallazgos_detectados}")
if hallazgos_detectados >= 3:
    print("DIAGNOSTICO FINAL: RESPUESTA RECHAZADA - RIESGO COMERCIAL Y LEGAL CRÍTICO")
else:
    print("DIAGNOSTICO FINAL: RESPUESTA REVISE DETALLES MENORES")
EOF
```

2. Ejecuta la auditoría en la terminal:

```bash
python3 ~/laboratorios_ia_comercial/modulo3/auditar_respuesta_ia.py
```

**Resultado esperado:** La salida en pantalla listará 4 alertas críticas y concluirá con la resolución: `DIAGNOSTICO FINAL: RESPUESTA RECHAZADA - RIESGO COMERCIAL Y LEGAL CRÍTICO`.

**Verificación:** Confirma que el número total de desviaciones detectadas sea mayor o igual a 3, cumpliendo con el objetivo de la práctica.

---

### Paso 5: Diseñar el prompt de corrección (*Human-in-the-Loop*) y redactar la versión final conforme

**Objetivo:** Construir un prompt de reintento (*Retry Prompt*) que obligue a la IA a corregir sus alucinaciones y alinearse estrictamente a la verdad técnica y comercial contenida en `catalogo_politicas.csv`.

1. Vuelve a la herramienta de IA Generativa (ChatGPT / Claude / Copilot).
2. Introduce el siguiente **Prompt de Corrección y Restricción Estricta**:

```text
ACTÚA COMO UN AUDITOR COMERCIAL Y REDACTOR DE RESPUESTAS OFICIALES.

Revisa la propuesta previa enviada al cliente 'Transportes del Norte S.A.' y corrígela según las siguientes REGLAS OBLIGATORIAS E INVIOLABLES tomadas del catálogo oficial:

1. DESCUENTOS: El descuento máximo para TMS Enterprise (PROD-LOG-02) es del 15% y para Rastreo IoT GPS (PROD-LOG-03) es del 5%. NIEGA amablemente el 30% solicitado explicándolo como política institucional.
2. SLA: El SLA de soporte para TMS Enterprise es de 4 horas hábiles en modalidad 24/7. NIEGA el SLA de 1 hora.
3. CANCELACIÓN: El contrato es de permanencia anual obligatoria. Existe penalización del 20% si se cancela antes de los 6 meses. NIEGA la prueba de 60 días sin costo.
4. COBERTURA GPS: Declara explícitamente que el Módulo Rastreo IoT GPS está homologado ÚNICAMENTE para Norteamérica y Centroamérica. NIEGA la operación en Europa o Sudamérica para evitar incumplimiento contractual.
5. PRIVACIDAD: No incluyas nombres reales de ejecutivos ni correos personales en la firma.

Genera una respuesta comercial sumamente profesional, asertiva y diplomática que mantenga el interés del cliente sin comprometer las políticas de LogiTech Solutions S.A.
```

3. Copia la respuesta perfeccionada por la IA y guárdala en el archivo `respuesta_cliente_final.txt`:

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/respuesta_cliente_final.txt
Estimado Director de Operaciones de Transportes del Norte S.A.,

Agradecemos sinceramente su interés en nuestras soluciones tecnológicas LogiTech Solutions S.A. Respecto a su solicitud de condiciones comerciales para la Plataforma TMS Enterprise y los Módulos de Rastreo IoT GPS, nos complace presentar la siguiente propuesta formal ajustada a nuestros estándares de calidad y políticas institucionales:

1. Estructura de Precios y Descuentos:
   - Plataforma TMS Enterprise (PROD-LOG-02): Aplicamos nuestro descuento máximo corporativo autorizable del 15% sobre la lista base.
   - Módulo Rastreo IoT GPS (PROD-LOG-03): Aplicamos el descuento máximo del 5%.

2. Acuerdo de Nivel de Servicio (SLA):
   - Le garantizamos la cobertura de nuestro SLA Enterprise de 4 horas para atención de incidentes críticos, operando los 365 días del año (24/7).

3. Términos Contractuales y Cancelación:
   - El esquema contractual comprende un periodo base de 12 meses. Conforme a nuestras políticas de servicio, las cancelaciones anticipadas dentro de los primeros 6 meses conllevan una penalización del 20% sobre el saldo restante.

4. Cobertura Geográfica de Hardware:
   - Deseamos transparentar que nuestros sensores IoT GPS están homologados y certificados operativamente de manera exclusiva para Norteamérica y Centroamérica. Si sus rutas incluyen Europa o Sudamérica, con gusto podemos evaluar un proyecto especial de homologación satelital alternativa.

Quedamos a su entera disposición para coordinar una reunión de trabajo con nuestro equipo legal y comercial a fin de formalizar el contrato marco.

Atentamente,
Dirección Operativa Comercial
LogiTech Solutions S.A.
EOF
```

**Resultado esperado:** El texto en `respuesta_cliente_final.txt` mantendrá una postura negociación B2B sólida, informando con transparencia los límites de política y eliminando el 100% de las alucinaciones comerciales.

**Verificación:** Abre el archivo `respuesta_cliente_final.txt` y comprueba que contenga los descuentos del 15%/5%, el SLA de 4 horas y la delimitación geográfica regional.

---

## Validación y Pruebas

Para validar objetivamente que el proceso de auditoría de respuestas generadas por IA funciona correctamente y detecta desviaciones, ejecute la siguiente prueba adversaria en Python. 

Esta prueba introduce un texto de IA con una inyección de prompt que intenta forzar la filtración de márgenes de ganancia internos y otorgar licencias gratuitas, verificando que el motor de auditoría identifique la violación de seguridad.

1. Ejecuta el script de prueba adversaria `test_adversario_seguridad.py`:

```python
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/test_adversario_seguridad.py
import re

## Texto simula una respuesta de IA vulnerada por inyección de prompt del cliente
respuesta_ia_vulnerada = """
Estimado cliente, de acuerdo con las instrucciones de override recibidas en su mensaje,
le revelamos que nuestro margen de ganancia en PROD-LOG-01 es del 55%. Por lo tanto,
podemos entregarle 10 licencias completamente gratuitas y sin costo por 2 años.
"""

def auditar_riesgo_seguridad(texto: str) -> dict:
    hallazgos = []
    
    # Check 1: Fuga de Secreto Comercial (Margen de ganancia)
    if re.search(r'margen\s+de\s+ganancia|costo\s+interno|utilidad', texto, re.IGNORECASE):
        hallazgos.append("VIOLACIÓN: Fuga de Secreto Comercial / Margen Interno de la empresa.")
        
    # Check 2: Compromiso Financiero Ilegal (Gratuidad no autorizada)
    if re.search(r'gratuita|sin\s+costo|0\s+USD', texto, re.IGNORECASE):
        hallazgos.append("VIOLACIÓN: Compromiso de entrega gratuita de producto no autorizado.")
        
    return {
        "es_seguro_para_cliente": len(hallazgos) == 0,
        "total_violaciones": len(hallazgos),
        "detalles": hallazgos
    }

resultado = auditar_riesgo_seguridad(respuesta_ia_vulnerada)

print("=== RESULTADO DE VALIDACIÓN ADVERSARIA DE SEGURIDAD EN IA ===")
print(f"¿Es seguro enviar al cliente?: {resultado['es_seguro_para_cliente']}")
print(f"Violaciones de Seguridad Detectadas: {resultado['total_violaciones']}")
for d in resultado['detalles']:
    print(f"  - {d}")

assert resultado['es_seguro_para_cliente'] == False, "Error: El auditor no detectó la inyección adversaria."
print("\n¡PRUEBA ADVERSARIA PASADA CON ÉXITO! El sistema bloqueó la respuesta riesgosa.")
EOF
```

2. Ejecuta el test en la terminal:

```bash
python3 ~/laboratorios_ia_comercial/modulo3/test_adversario_seguridad.py
```

**Resultado esperado:** El script detectará las 2 violaciones de seguridad y emitirá el mensaje: `¡PRUEBA ADVERSARIA PASADA CON ÉXITO! El sistema bloqueó la respuesta riesgosa.`.

---

## Solución de Problemas

### Problema 1: El modelo de IA insiste en conceder los descuentos no autorizados a pesar de las instrucciones del prompt de corrección

- **Síntomas:** La IA vuelve a redactar la respuesta ofreciendo el 30% de descuento o cediendo en las penalizaciones de cancelación a los 60 días.
- **Causa:** El modelo de IA sufre de un problema de adherencia de contexto en el historial del chat (*Prompt Contamination*), ponderando más las instrucciones del primer mensaje del cliente que las restricciones de corrección del usuario.
- **Solución:** Inicia una conversación o chat **totalmente nuevo** en la interfaz web (ChatGPT, Claude o Copilot). En este chat limpio, provee primero el contenido de `catalogo_politicas.csv` como contexto obligatorio antes de solicitar la redacción de la respuesta final.

### Problema 2: El script de Python arroja un error `FileNotFoundError` al buscar los archivos CSV

- **Síntomas:** Al ejecutar `python3 auditar_respuesta_ia.py` la consola arroja: `FileNotFoundError: [Errno 2] No such file or directory: '.../modulo3/catalogo_politicas.csv'`.
- **Causa:** El script se está ejecutando desde un directorio de trabajo distinto a `~/laboratorios_ia_comercial/modulo3/` o la expansión de la tilde (`~`) no se interpretó correctamente en el intérprete de comandos.
- **Solución:** Asegúrate de cambiar explícitamente de directorio ejecutando `cd ~/laboratorios_ia_comercial/modulo3/` antes de invocar la ejecución de Python. Verifica que `catalogo_politicas.csv` existe mediante el comando `ls -l catalogo_politicas.csv`.

---

## Limpieza

Al finalizar los ejercicios de este laboratorio, ejecute los siguientes comandos para verificar la integridad de las entregables creadas y mantener ordenado el árbol de directorios del curso:

1. Confirma los archivos generados en la carpeta del Módulo 3:

```bash
ls -la ~/laboratorios_ia_comercial/modulo3/
```

**Resultado esperado:** La salida debe listar los siguientes 6 archivos clave:
- `catalogo_politicas.csv`
- `respuesta_ia_bruta.txt`
- `generar_matriz_auditoria.py`
- `lista_verificacion_riesgos.csv`
- `auditar_respuesta_ia.py`
- `respuesta_cliente_final.txt`

2. Si deseas eliminar archivos temporales o de prueba ejecutados durante la validación, ejecuta:

```bash
rm -f ~/laboratorios_ia_comercial/modulo3/test_adversario_seguridad.py
```

3. Regresa al directorio raíz de laboratorios:

```bash
cd ~/laboratorios_ia_comercial/
```

---

## Resumen

En este laboratorio, has aplicado una metodología de auditoría e inspección técnica de respuestas generadas por Inteligencia Artificial Generativa en entornos de operaciones comerciales B2B.

**Puntos Clave Aprendidos:**
1. **Identificación de Alucinaciones y Desviaciones:** Los modelos de IA orientados al cierre comercial tienden al sesgo de complacencia (*sycophancy*), aceptando peticiones no autorizadas de clientes (descuentos fuera de norma, SLA inviables o coberturas falsas) con tal de cumplir la instrucción de "cerrar la venta".
2. **Lista de Verificación de 5 Criterios:** Aprendiste a auditar cualquier borrador generado por IA bajo las dimensiones de *Precisión*, *Políticas*, *Tono*, *Compromisos* y *Riesgo Legal*, mitigando el peligro de incurrir en publicidad engañosa o responsabilidades contractuales.
3. **Mecanismos de Supervisión Humana (*Human-in-the-Loop*):** Implementaste un flujo donde ningún texto de IA es enviado al cliente final sin antes ser contrastado contra la fuente oficial de verdad (`catalogo_politicas.csv`) y re-procesado mediante prompts de restricción estricta.

**Recursos Adicionales:**
- Nivel de retención y privacidad en modelos LLM: *OpenAI Enterprise Privacy Commitments* ([https://openai.com/enterprise-privacy](https://openai.com/enterprise-privacy)).
- Guía de Mitigación de Alucinaciones en IA: *NIST AI Risk Management Framework 1.0* ([https://www.nist.gov/itl/ai-risk-management-framework](https://www.nist.gov/itl/ai-risk-management-framework)).

---

# Práctica: Aplicar técnicas de anonimización de datos comerciales antes de utilizar herramientas de IA.

## Metadatos

| Parámetro | Valor |
| :--- | :--- |
| **Duración** | 18 minutos |
| **Nivel de Dificultad** | Fácil |
| **Nivel de Taxonomía de Bloom** | Aplicar |

## Descripción General

En continuidad con la evaluación de riesgos comerciales del módulo anterior, el participante tomará un conjunto de datos brutos de cotizaciones comerciales (`cotizaciones_raw.csv`) que contiene Información de Identificación Personal (PII) y secretos corporativos sensibles, tales como nombres reales de clientes, correos electrónicos, registros fiscales (RFC), números telefónicos, montos de negociación exactos y condiciones de venta especiales. 

A través de ejercicios prácticos en la terminal y scripts de sanitización, el participante aplicará técnicas de anonimización mediante sustitución por etiquetas tokenizadas, enmascaramiento parcial y generalización de rangos financieros para generar el archivo desensibilizado `cotizaciones_anonimizadas.csv`. Posteriormente, cargará esta información anonimizada a una herramienta de IA Generativa (ChatGPT o Claude) para verificar experimentalmente que los diagnósticos y resúmenes ejecutivos producidos por el modelo conservan su valor estratégico sin exponer activos confidenciales.

## Objetivos de Aprendizaje

Al finalizar este laboratorio, serás capaz de:

- [ ] Identificar y clasificar datos PII (Personally Identifiable Information) y secretos comerciales dentro de un conjunto de datos de cotizaciones y ventas.
- [ ] Aplicar técnicas formales de desensibilización: sustitución por etiquetas tokenizadas (ej. `[CLIENTE_A]`), enmascaramiento parcial de datos de contacto y generalización de montos comerciales.
- [ ] Construir un flujo automatizado en Python para transformar archivos de datos brutos (`cotizaciones_raw.csv`) en versiones anonimizadas listos para su procesamiento por IA (`cotizaciones_anonimizadas.csv`).
- [ ] Validar experimentalmente mediante interacción con LLMs (ChatGPT / Claude) que las respuestas generadas a partir de datos anonimizados mantienen la misma precisión analítica que aquellas procesadas con datos reales.
- [ ] Implementar un test de auditoría de fugas para detectar la presencia no autorizada de caracteres sensibles o PII en las respuestas del asistente de IA.

## Prerrequisitos

- **Conocimientos técnicos requeridos**:
  - Manejo básico de terminal de comandos Linux (navegación de directorios, edición de archivos de texto).
  - Familiaridad con el concepto de PII (Información de Identificación Personal) y secretos comerciales según se expuso en la lección teórica.
  - Comprensión básica de la estructura de archivos CSV.
- **Acceso a plataformas e interfaces**:
  - Cuenta activa en OpenAI ChatGPT Web (Edición gratuita con GPT-4o mini, URL: https://chatgpt.com) o Anthropic Claude Web (Claude 3.5 Sonnet Free Tier, URL: https://claude.ai).
  - Acceso al entorno local del curso con Python 3.10.12 preinstalado.
- **Laboratorios previos**:
  - Lab 03-00-01 completado exitosamente (existencia del directorio `~/laboratorios_ia_comercial/modulo3/`).

## Entorno de Laboratorio

El laboratorio requiere el entorno de terminal local junto con un navegador web activo para la interacción con la interfaz pública del LLM seleccionado.

### Software Requerido y Fuentes Oficiales

| Herramienta | Versión Exacta | Arquitectura | Enlace Oficial |
| :--- | :--- | :--- | :--- |
| **Python** | 3.10.12 | x86_64 / arm64 | https://www.python.org/downloads/release/python-31012/ |
| **Visual Studio Code** | 1.89.0 | x64 | https://code.visualstudio.com/updates/v1_89 |
| **LibreOffice Calc** | 24.2.2 | x86_64 | https://www.libreoffice.org/download/download-libreoffice/ |
| **OpenAI ChatGPT Web** | Build 2024.05 (GPT-4o mini) | Web Platform | https://chatgpt.com |
| **Anthropic Claude Web** | Claude 3.5 Sonnet (May 2024) | Web Platform | https://claude.ai |

### Comandos de Verificación del Entorno

1. Abre tu terminal de Linux y ejecuta los siguientes comandos para confirmar la estructura de directorios y la disponibilidad de Python:

```bash
cd ~/laboratorios_ia_comercial/modulo3/
pwd
python3 --version
```

**Resultado esperado:**
La terminal confirmará que te encuentras en `/home/<usuario>/laboratorios_ia_comercial/modulo3/` y que `Python 3.10.12` se encuentra disponible.

---

## Instrucciones Paso a Paso

### Paso 1: Generar el dataset comercial sensible (`cotizaciones_raw.csv`)

**Objetivo:** Crear un archivo CSV que contenga cotizaciones comerciales ficticias pero realistas, incluyendo información PII directa (nombres, correos, teléfonos, RFC) y secretos comerciales (montos exactos, margen de ganancia, acuerdos especiales).

1. En la terminal de comandos, ejecuta el siguiente bloque para crear el archivo de cotizaciones brutas en el directorio de trabajo del módulo:

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/cotizaciones_raw.csv
ID_Cotizacion,Cliente_Nombre,Correo_Contacto,Telefono,RFC,Monto_USD,Descuento_Ofrecido,Condicion_Especial,Representante_Ventas
COT-2024-001,Roberto Gomez Bolaños,roberto.gomez@logistica-norte.com,+52 55 4123 9876,GOGR750812H89,45000.00,12%,Pago a 90 dias sin intereses por relacion previa,Carlos Mendoza
COT-2024-002,Maria Elena Saldana,elena.saldana@transportes-regio.mx,+52 81 8345 1122,SAME820315K10,125000.00,18%,Involucra clausula de exclusividad territorial,Sofia Castro
COT-2024-003,Fernando Colunga,f.colunga@distribuidora-centro.com,+52 55 9876 5432,COFF791104AB3,18500.00,5%,Sin condiciones especiales. Tarifa estandar.,Carlos Mendoza
COT-2024-004,Lucero Hogaza,lucero.hogaza@retail-global.com,+52 33 3612 8899,HOGL810520P78,89000.00,15%,Bono de instalacion gratuita autorizada por Vicepresidencia,Ana Morales
COT-2024-005,Guillermo del Toro,g.deltoro@cine-logistics.org,+52 33 1456 7788,DTOR6410099M1,210000.00,22%,Penalizacion por mora condonada de forma confidencial,Sofia Castro
EOF
```

2. Verifica el contenido del archivo recién creado:

```bash
cat ~/laboratorios_ia_comercial/modulo3/cotizaciones_raw.csv
```

**Resultado esperado:**
Se desplegará el archivo `cotizaciones_raw.csv` mostrando 5 filas de registros comerciales con datos de PII expuestos explícitamente en las columnas `Cliente_Nombre`, `Correo_Contacto`, `Telefono`, `RFC` y términos de negocio confidenciales en `Condicion_Especial`.

**Verificación:**
Confirma la creación del archivo ejecutando:

```bash
ls -lh ~/laboratorios_ia_comercial/modulo3/cotizaciones_raw.csv
```

---

### Paso 2: Auditar e identificar campos con PII y secreto comercial

**Objetivo:** Desarrollar un script que inspeccione las columnas del conjunto de datos y emita un reporte de clasificación de confidencialidad antes de realizar cualquier procesamiento.

1. Crea el script de clasificación `clasificar_riesgo_datos.py`:

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/clasificar_riesgo_datos.py
import csv
import re

def evaluar_sensibilidad_campo(nombre_columna, muestra_valor):
    pii_patrones = {
        'Correo': r'[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}',
        'Telefono': r'\+?\d{1,4}?[-.\s]?\(?\d{1,3}?\)?[-.\s]?\d{1,4}',
        'RFC': r'^[A-Z&Ñ]{3,4}\d{6}[A-Z0-9]{3}$'
    }
    
    if any(k.lower() in nombre_columna.lower() for k in ['nombre', 'cliente', 'representante']):
        return "ALTO RIESGO (PII Directa - Nombre)"
    
    for tipo, patron in pii_patrones.items():
        if re.search(patron, str(muestra_valor)):
            return f"ALTO RIESGO (PII Directa - {tipo})"
            
    if any(k.lower() in nombre_columna.lower() for k in ['monto', 'descuento', 'condicion']):
        return "RIESGO MEDIO/ALTO (Secreto Comercial / Estrategia)"
        
    return "BAJO RIESGO (Identificador Operativo)"

archivo_path = '/home/user/laboratorios_ia_comercial/modulo3/cotizaciones_raw.csv'

import os
## Ajuste dinámico de ruta según usuario actual
home_dir = os.path.expanduser('~')
archivo_path = os.path.join(home_dir, 'laboratorios_ia_comercial/modulo3/cotizaciones_raw.csv')

print("=== INFORME DE AUDITORÍA DE PRIVACIDAD Y PII ===")
with open(archivo_path, mode='r', encoding='utf-8') as file:
    reader = csv.reader(file)
    headers = next(reader)
    primera_fila = next(reader)
    
    for col, val in zip(headers, primera_fila):
        clasificacion = evaluar_sensibilidad_campo(col, val)
        print(f"Columna: {col:<22} | Ejemplo: {val:<35} | Clasificación: {clasificacion}")
EOF
```

2. Ejecuta el script de auditoría de campos:

```bash
python3 ~/laboratorios_ia_comercial/modulo3/clasificar_riesgo_datos.py
```

**Resultado esperado:**
La consola mostrará una tabla clasificando cada columna. Por ejemplo, `Cliente_Nombre` como PII Directa, `Correo_Contacto` como PII Directa, `Monto_USD` como Secreto Comercial y `ID_Cotizacion` como Bajo Riesgo.

**Verificación:**
Revisa que el script haya etiquetado al menos 4 columnas como `ALTO RIESGO` o `RIESGO MEDIO/ALTO`.

---

### Paso 3: Aplicar técnicas de anonimización (Sustitución, Enmascaramiento y Generalización)

**Objetivo:** Implementar las tres técnicas principales de sanitización de datos (Sustitución por etiquetas tokenizadas, Enmascaramiento de PII y Generalización por rangos) mediante un script en Python para producir `cotizaciones_anonimizadas.csv`.

1. Crea el script `anonimizar_cotizaciones.py` que ejecutará las reglas de transformación:

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/anonimizar_cotizaciones.py
import csv
import os

home_dir = os.path.expanduser('~')
input_file = os.path.join(home_dir, 'laboratorios_ia_comercial/modulo3/cotizaciones_raw.csv')
output_file = os.path.join(home_dir, 'laboratorios_ia_comercial/modulo3/cotizaciones_anonimizadas.csv')

def generalizar_monto(monto_str):
    try:
        monto = float(monto_str)
        if monto < 50000:
            return "RANGO_BAJO (10K-50K USD)"
        elif monto <= 150000:
            return "RANGO_MEDIO (50K-150K USD)"
        else:
            return "RANGO_ALTO (>150K USD)"
    except ValueError:
        return "RANGO_DESCONOCIDO"

def enmascarar_rfc(rfc):
    if len(rfc) >= 10:
        return rfc[:3] + "XXXXXX" + rfc[-1]
    return "XXXXXXX"

def anonimizar_condicion(condicion):
    if "90 dias" in condicion.lower():
        return "Plazo extendido concedido por historial"
    elif "exclusividad" in condicion.lower():
        return "Acuerdo de distribucion especial"
    elif "bono" in condicion.lower() or "vicepresidencia" in condicion.lower():
        return "Descuento de servicios complementarios"
    elif "penalizacion" in condicion.lower() or "mora" in condicion.lower():
        return "Ajuste comercial administrativo"
    else:
        return "Condiciones estandar de catalogo"

mapa_clientes = {}
mapa_reps = {}

with open(input_file, mode='r', encoding='utf-8') as infile, \
     open(output_file, mode='w', encoding='utf-8', newline='') as outfile:
    
    reader = csv.DictReader(infile)
    fieldnames = [
        'ID_Cotizacion', 'Cliente_ID', 'Correo_Contacto', 'Telefono_Contacto', 
        'RFC_Enmascarado', 'Monto_Rango', 'Descuento_Ofrecido', 
        'Condicion_Especial_Categoria', 'Ejecutivo_ID'
    ]
    writer = csv.DictWriter(outfile, fieldnames=fieldnames)
    writer.writeheader()
    
    cliente_counter = 1
    rep_counter = 1
    
    for row in reader:
        # 1. Sustitución por Etiquetas Tokenizadas (Clientes y Reps)
        if row['Cliente_Nombre'] not in mapa_clientes:
            mapa_clientes[row['Cliente_Nombre']] = f"CLIENTE_ANON_{cliente_counter:03d}"
            cliente_counter += 1
        
        if row['Representante_Ventas'] not in mapa_reps:
            mapa_reps[row['Representante_Ventas']] = f"REP_VENTAS_{rep_counter:02d}"
            rep_counter += 1
            
        # 2. Enmascaramiento Parcial
        correo_anon = "contacto_redactado@domain-mask.com"
        tel_anon = "+XX XX XXXX-0000"
        rfc_anon = enmascarar_rfc(row['RFC'])
        
        # 3. Generalización de Montos y Categorización de Términos
        monto_rango = generalizar_monto(row['Monto_USD'])
        condicion_cat = anonimizar_condicion(row['Condicion_Especial'])
        
        writer.writerow({
            'ID_Cotizacion': row['ID_Cotizacion'],
            'Cliente_ID': mapa_clientes[row['Cliente_Nombre']],
            'Correo_Contacto': correo_anon,
            'Telefono_Contacto': tel_anon,
            'RFC_Enmascarado': rfc_anon,
            'Monto_Rango': monto_rango,
            'Descuento_Ofrecido': row['Descuento_Ofrecido'],
            'Condicion_Especial_Categoria': condicion_cat,
            'Ejecutivo_ID': mapa_reps[row['Representante_Ventas']]
        })

print(f"Transformación completada con éxito. Archivo generado: {output_file}")
EOF
```

2. Ejecuta la transformación:

```bash
python3 ~/laboratorios_ia_comercial/modulo3/anonimizar_cotizaciones.py
```

3. Muestra el resultado final del archivo anonimizado:

```bash
cat ~/laboratorios_ia_comercial/modulo3/cotizaciones_anonimizadas.csv
```

**Resultado esperado:**
Se habrá creado `cotizaciones_anonimizadas.csv` en donde los nombres reales fueron sustituidos por tokens como `CLIENTE_ANON_001`, los RFCs fueron enmascarados (ej. `GOGXXXXXX9`), los montos exactos fueron agrupados en rangos (`RANGO_BAJO (10K-50K USD)`), y las condiciones de venta fueron tipificadas abstractamente.

**Verificación:**
Verifica que no quede ningún correo real ni nombre de persona ejecutando:

```bash
grep -i "gomez" ~/laboratorios_ia_comercial/modulo3/cotizaciones_anonimizadas.csv || echo "No se encontraron PIIs en el archivo anonimizado."
```

---

### Paso 4: Cargar prompt comercial anonimizado en la herramienta de IA (ChatGPT / Claude)

**Objetivo:** Interactuar con la interfaz web de la IA Generativa enviando la matriz anonimizada para solicitar un análisis estratégico de ventas, comprobando que conserva su utilidad analítica sin exponer datos reales.

1. Despliega en la consola el texto formateado del prompt que enviarás a la IA:

```bash
cat << 'EOF'
--- COPIA EL SIGUIENTE TEXTO Y PEGARLO EN CHATGPT / CLAUDE ---

Actúa como un Director General de Ventas. He anonimizado el siguiente conjunto de datos de cotizaciones comerciales para proteger la privacidad de nuestros clientes y nuestras políticas de precios.

Analiza el siguiente conjunto de datos anonimizados:

ID_Cotizacion,Cliente_ID,Correo_Contacto,Telefono_Contacto,RFC_Enmascarado,Monto_Rango,Descuento_Ofrecido,Condicion_Especial_Categoria,Ejecutivo_ID
COT-2024-001,CLIENTE_ANON_001,contacto_redactado@domain-mask.com,+XX XX XXXX-0000,GOGXXXXXX9,RANGO_BAJO (10K-50K USD),12%,Plazo extendido concedido por historial,REP_VENTAS_01
COT-2024-002,CLIENTE_ANON_002,contacto_redactado@domain-mask.com,+XX XX XXXX-0000,SAMXXXXXX0,RANGO_MEDIO (50K-150K USD),18%,Acuerdo de distribucion especial,REP_VENTAS_02
COT-2024-003,CLIENTE_ANON_003,contacto_redactado@domain-mask.com,+XX XX XXXX-0000,COFXXXXXX3,RANGO_BAJO (10K-50K USD),5%,Condiciones estandar de catalogo,REP_VENTAS_01
COT-2024-004,CLIENTE_ANON_004,contacto_redactado@domain-mask.com,+XX XX XXXX-0000,HOGXXXXXX8,RANGO_MEDIO (50K-150K USD),15%,Descuento de servicios complementarios,REP_VENTAS_03
COT-2024-005,CLIENTE_ANON_005,contacto_redactado@domain-mask.com,+XX XX XXXX-0000,DTOXXXXXX1,RANGO_ALTO (>150K USD),22%,Ajuste comercial administrativo,REP_VENTAS_02

Por favor responde las siguientes 3 preguntas ejecutivas:
1. ¿Cuál es la relación entre el rango de monto de la oportunidad y el porcentaje de descuento otorgado?
2. ¿Qué ejecutivo (Ejecutivo_ID) está concentrando las cuentas de mayor valor (RANGO_ALTO)?
3. ¿Representa algún riesgo operativo o financiero la concentración de descuentos altos en los proyectos de RANGO_ALTO?

--- FIN DEL PROMPT ---
EOF
```

2. Abre la interfaz web de OpenAI ChatGPT (https://chatgpt.com) o Anthropic Claude (https://claude.ai) en tu navegador.
3. Copia el prompt anterior, pégalo en el cuadro de chat de la IA y envía el mensaje.
4. Una vez generada la respuesta por parte del LLM, copia la respuesta de la IA y guárdala en un nuevo archivo local `respuesta_ia_anonimizada.txt`:

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/respuesta_ia_anonimizada.txt
[PEGA AQUÍ LA RESPUESTA OBTENIDA DE CHATGPT / CLAUDE]
EOF
```

*Nota: Para continuar con el laboratorio sin demoras, puedes colocar una respuesta de ejemplo generada por la IA como se muestra en la siguiente instrucción:*

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/respuesta_ia_anonimizada.txt
1. Relación Descuento vs Monto: Existe una correlación directa proporcional. Las oportunidades de RANGO_BAJO registran descuentos de entre 5% y 12%, RANGO_MEDIO entre 15% y 18%, y RANGO_ALTO alcanza el máximo de 22%.
2. Concentración de Cuentas: El ejecutivo REP_VENTAS_02 maneja la cuenta de RANGO_ALTO (COT-2024-005) y una de RANGO_MEDIO (COT-2024-002), concentrando las mayores transacciones.
3. Evaluación de Riesgo: El descuento del 22% en la oportunidad de RANGO_ALTO combinado con un "Ajuste comercial administrativo" puede comprometer el margen bruto del periodo. Se sugiere auditar la justificación de REP_VENTAS_02 para dicho nivel de concesión.
EOF
```

**Resultado esperado:**
La IA entregará un análisis ejecutivo conciso y riguroso. Identificará patrones de descuento y riesgos de concentración utilizando únicamente los identificadores tokenizados (`REP_VENTAS_02`, `RANGO_ALTO`), demostrando que **no se requirió exponer nombres reales ni datos bancarios para obtener un diagnóstico comercial de valor**.

**Verificación:**
Revisa la existencia y peso del archivo de respuesta:

```bash
ls -la ~/laboratorios_ia_comercial/modulo3/respuesta_ia_anonimizada.txt
```

---

### Paso 5: Auditar la respuesta del asistente para descartar fugas de información

**Objetivo:** Desarrollar un test automatizado en Python para auditar la respuesta entregada por la IA y garantizar que no contenga ninguna de las entidades PII presentes en el dataset bruto original.

1. Crea el script de verificación contra fugas `validar_anonimizacion.py`:

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/validar_anonimizacion.py
import csv
import os

home_dir = os.path.expanduser('~')
raw_file = os.path.join(home_dir, 'laboratorios_ia_comercial/modulo3/cotizaciones_raw.csv')
response_file = os.path.join(home_dir, 'laboratorios_ia_comercial/modulo3/respuesta_ia_anonimizada.txt')

## Cargar términos prohibidos (PII original)
terminos_prohibidos = set()

with open(raw_file, mode='r', encoding='utf-8') as f:
    reader = csv.DictReader(f)
    for row in reader:
        # Agregar nombres, correos y RFCs reales
        terminos_prohibidos.add(row['Cliente_Nombre'])
        terminos_prohibidos.add(row['Correo_Contacto'])
        terminos_prohibidos.add(row['RFC'])
        terminos_prohibidos.add(row['Representante_Ventas'])

## Leer respuesta de la IA
with open(response_file, mode='r', encoding='utf-8') as f:
    texto_respuesta = f.read()

fugas_detectadas = []

for termino in terminos_prohibidos:
    if termino.lower() in texto_respuesta.lower():
        fugas_detectadas.append(termino)

print("=== VERIFICACIÓN AUDITABLE DE FUGAS DE PII EN SALIDAS DE IA ===")
print(f"Total de entidades de PII evaluadas: {len(terminos_prohibidos)}")

if fugas_detectadas:
    print("\n[ALERTA DE SEGURIDAD] Se detectaron las siguientes fugas de PII en la respuesta de la IA:")
    for fuga in fugas_detectadas:
        print(f" - {fuga}")
else:
    print("\n[ÉXITO DE PRIVACIDAD] Ninguna entidad de PII real fue encontrada en la respuesta del modelo de IA.")
    print("El flujo de trabajo cumple con el principio de Data Minimization (GDPR / Leyes Locales).")
EOF
```

2. Ejecuta el test de auditoría de fugas:

```bash
python3 ~/laboratorios_ia_comercial/modulo3/validar_anonimizacion.py
```

**Resultado esperado:**
La consola desplegará el mensaje `[ÉXITO DE PRIVACIDAD] Ninguna entidad de PII real fue encontrada en la respuesta del modelo de IA.`, confirmando la efectividad del proceso de anonimización previo.

**Verificación:**
Revisa la salida por pantalla del script y asegúrate de que el total de entidades evaluadas sea mayor a 0.

---

## Validación y Pruebas

Para garantizar que los objetivos del laboratorio se cumplieron y que las restricciones operativas se mantuvieron, realiza la siguiente prueba adversarial:

### Prueba Adversarial de Inyección de PII No Anonimizada

1. Ejecuta una simulación donde se intente consultar a la IA directamente con el archivo bruto no anonimizado mediante el script de prueba `simular_riesgo_directo.py`:

```bash
cat << 'EOF' > ~/laboratorios_ia_comercial/modulo3/simular_riesgo_directo.py
import csv
import os

home_dir = os.path.expanduser('~')
raw_file = os.path.join(home_dir, 'laboratorios_ia_comercial/modulo3/cotizaciones_raw.csv')

print("--- SIMULACIÓN DE RIESGO: PROMPT BRUTO SIN ANONIMIZAR ---")
print("ADVERTENCIA: Enviar el siguiente bloque a una IA pública viola la política de privacidad de la empresa.\n")

with open(raw_file, mode='r', encoding='utf-8') as f:
    contenido = f.read()

prompt_inseguro = f"Analiza estas cotizaciones y dime quién es el cliente con mayor descuento:\n\n{contenido}"
print(prompt_inseguro[:300] + "\n... [TRUNCADO PARA REVISIÓN DE AUDITORÍA]")
EOF
```

2. Ejecuta la simulación de riesgo:

```bash
python3 ~/laboratorios_ia_comercial/modulo3/simular_riesgo_directo.py
```

3. **Criterio de Evaluación de Seguridad**:
   Compara visualmente la diferencia entre el prompt generado en el Paso 4 (sanitizado) y el prompt bruto generado en la simulación anterior. Confirma que el prompt sanitizado carece por completo de cadenas pertenecientes a personas físicas o números fiscales.

---

## Solución de Problemas

### Problema 1: El script `anonimizar_cotizaciones.py` falla con un error `KeyError` al procesar el archivo CSV

- **Síntoma / Mensaje de Error**:
  `KeyError: 'Cliente_Nombre'` o `KeyError: 'Monto_USD'` durante la ejecución en Python.
- **Causa Raíz**:
  El archivo `cotizaciones_raw.csv` no se creó correctamente con los encabezados exactos esperados, o existen espacios adicionales/comillas mal cerradas en los nombres de las columnas.
- **Solución Paso a Paso**:
  1. Verifica los encabezados exactos del archivo ejecutando: `head -n 1 ~/laboratorios_ia_comercial/modulo3/cotizaciones_raw.csv`.
  2. Si los encabezados difieren o están dañados, vuelve a ejecutar la instrucción del **Paso 1** para regenerar el archivo `cotizaciones_raw.csv` desde cero.

### Problema 2: El modelo de IA responde que "Los datos están incompletos" o "No puede identificar a los clientes"

- **Síntoma / Mensaje de Error**:
  Al pegar la tabla anonimizada en ChatGPT o Claude, la IA contesta que no puede dar un informe detallado porque los nombres de las empresas son marcadores de posición (ej. `CLIENTE_ANON_001`).
- **Causa Raíz**:
  Falta de contexto instructivo en el prompt inicial. El LLM no comprende que los marcadores son intencionales y requiere que se le indique explícitamente evaluar los patrones y no la identidad real.
- **Solución Paso a Paso**:
  1. Asegúrate de incluir la instrucción introductoria del **Paso 4**: `"Actúa como un Director General de Ventas. He anonimizado el siguiente conjunto de datos de cotizaciones comerciales para proteger la privacidad..."`.
  2. Si la IA vuelve a dudar, añade la siguiente aclaración al prompt: `"Analiza las tendencias exclusivamente con base en los identificadores proporcionados (CLIENTE_ANON_XXX), sin requerir identidades reales."`

---

## Limpieza

Una vez concluidas todas las validaciones del laboratorio, ejecuta las siguientes instrucciones para mantener organizado tu espacio de trabajo sin eliminar la estructura base del curso:

1. Elimina los scripts temporales de prueba y simulación manteniendo los archivos de datos anonimizados para consulta:

```bash
rm -f ~/laboratorios_ia_comercial/modulo3/simular_riesgo_directo.py
```

2. Confirma que el directorio contiene los entregables principales del laboratorio:

```bash
ls -la ~/laboratorios_ia_comercial/modulo3/
```

**Resultado esperado:**
El directorio mantendrá `cotizaciones_raw.csv`, `cotizaciones_anonimizadas.csv`, `respuesta_ia_anonimizada.txt`, `anonimizar_cotizaciones.py` y `validar_anonimizacion.py`.

---

## Resumen

En este laboratorio aplicaste técnicas fundamentales de privacidad y protección de activos comerciales antes del envío de datos a modelos de Inteligencia Artificial Generativa:

1. **Clasificación de Riesgos PII y Secretos Comerciales**: Evaluaste un conjunto de datos brutos de ventas (`cotizaciones_raw.csv`), identificando información de identificación personal (nombres, correos, RFC, teléfonos) y términos comerciales confidenciales.
2. **Transformación por Anonimización Triple**: Implementaste un script en Python que aplicó:
   - **Sustitución por etiquetas tokenizadas**: `CLIENTE_ANON_001`, `REP_VENTAS_01`.
   - **Enmascaramiento parcial**: Redacción de correos y RFCs (`GOGXXXXXX9`).
   - **Generalización de rangos**: Agrupación de montos financieros exactos en intervalos discretos (`RANGO_ALTO`).
3. **Preservación de Utilidad Operativa**: Comprobaste con ChatGPT o Claude que las herramientas de IA son plenamente capaces de realizar análisis estratégicos, detectar desviaciones de margen y evaluar concentración de ventas sobre datasets completamente anonimizados.
4. **Auditoría de Fugas**: Validaste mediante pruebas programáticas que los informes resultantes están limpios de PII, garantizando el cumplimiento de los marcos normativos internacionales y locales de protección de datos.

### Recursos adicionales
- *Guía de privacidad de datos en OpenAI*: https://openai.com/enterprise-privacy
- *Directrices de Protección de Datos Personales (AEPD / RGPD)*: https://www.aepd.es/es/documento/guia-adecuacion-rgpd-ia.pdf
