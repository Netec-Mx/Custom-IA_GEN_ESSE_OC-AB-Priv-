# Práctica 12. Analizar contratos, propuestas comerciales, procedimientos y correos relacionados con un proceso comercial utilizando Claude para identificar inconsistencias, riesgos, compromisos pendientes y generar un informe consolidado para apoyar el control de la operación

**Capítulo 3. Herramientas de Inteligencia Artificial para la Operación Comercial · Módulo 6. Aplicación de plataformas de IA en la operación comercial (Claude Projects y análisis documental mediante grandes ventanas de contexto)**

## Metadatos

| Parámetro | Detalle |
| :--- | :--- |
| **Duración** | 15 minutos |
| **Complejidad** | Intermedia |
| **Nivel de Bloom** | Analizar |
| **Herramientas** | Claude (versión gratuita; Projects si la versión disponible lo permite) y Microsoft Word |
| **Archivos** | `Propuesta_Economica_Acme.pdf`, `Contrato_Servicio_Acme.pdf`, `Procedimiento_Soporte_SLA_Acme.pdf`, `Hilo_Correos_Acme.pdf` |

## Descripción General

El participante organizará en Claude el expediente comercial del cliente Acme Corp: una propuesta, un contrato, un procedimiento de soporte y un hilo de correos. Aprovechando la ventana de contexto de Claude y, si la versión lo permite, un proyecto con instrucciones del caso, pedirá identificar inconsistencias entre documentos, riesgos y compromisos pendientes con la fuente de cada hallazgo. Después verificará las citas contra los documentos originales y generará un informe consolidado con conclusiones y acciones recomendadas.

La práctica se realiza con Claude en su versión gratuita, ya que forma parte de los objetivos del módulo. El instructor puede reducir el número de documentos según los límites disponibles. Todos los datos son ficticios.

## Objetivos de Aprendizaje

Al finalizar la práctica, el participante será capaz de:

- Organizar varios documentos de un proceso comercial en Claude.
- Identificar inconsistencias, riesgos y compromisos pendientes entre documentos.
- Verificar cada cita contra el documento original.
- Generar un informe consolidado para el control de la operación.

## Prerrequisitos

- Cuenta gratuita de Claude (ver [Setup_Guide.md](../../Setup_Guide.md)).
- Haber revisado el tema *Claude Projects y análisis documental mediante grandes ventanas de contexto* del Módulo 6.

## Entorno de Laboratorio

| Herramienta | Uso | Acceso |
| :--- | :--- | :--- |
| Claude | Análisis del expediente | [claude.ai](https://claude.ai/) |
| Visor de PDF y Microsoft Word | Verificar citas y guardar el informe | Navegador o lector de PDF; Word instalado o [microsoft365.com](https://www.microsoft365.com/) |

**Archivos de la práctica**

| Archivo | Descripción |
| :--- | :--- |
| [Propuesta_Economica_Acme.pdf](recursos/Propuesta_Economica_Acme.pdf) | Propuesta PROP-2026-ACME-009: alcance, condiciones financieras y tiempos |
| [Contrato_Servicio_Acme.pdf](recursos/Contrato_Servicio_Acme.pdf) | Contrato CTR-2026-884 con 5 cláusulas |
| [Procedimiento_Soporte_SLA_Acme.pdf](recursos/Procedimiento_Soporte_SLA_Acme.pdf) | Anexo B: disponibilidad, tiempos de respuesta, penalizaciones y escalamiento |
| [Hilo_Correos_Acme.pdf](recursos/Hilo_Correos_Acme.pdf) | 3 correos de negociación y seguimiento |

> **Cómo descargar los archivos:** hacer clic en el nombre del archivo y seleccionar **Download raw file**. Guardarlos en `Documentos\Practicas_IA_Comercial\Practica12`.

## Instrucciones Paso a Paso

### Paso 1: Organizar el expediente en Claude (3 min)

**Objetivo:** Cargar los 4 documentos con las instrucciones del caso.

1. Abrir [claude.ai](https://claude.ai/) e iniciar sesión.
2. Si la opción **Proyectos** (**Projects**) está disponible en el panel izquierdo:
   - Crear un proyecto llamado `Expediente Acme Corp`.
   - En **Instrucciones del proyecto** (**Project instructions**), escribir: *"Eres auditor de operaciones comerciales. Responde solo con información de los documentos del proyecto y cita el documento y la sección o cláusula de cada dato."*
   - Agregar los 4 archivos en **Conocimiento del proyecto** (**Project knowledge**).
   - Iniciar una conversación dentro del proyecto.
3. Si **Proyectos** no está disponible, iniciar una conversación nueva y adjuntar los 4 archivos con el botón **+** o el clip.

**Resultado esperado:** Los 4 documentos están disponibles para Claude.

**Verificación:** Enviar *"Lista los documentos que tienes y la fecha de cada uno"*: Claude debe nombrar los 4 documentos.

### Paso 2: Pedir la auditoría cruzada (4 min)

**Objetivo:** Identificar inconsistencias, riesgos y compromisos pendientes.

1. Enviar:

```text
Realiza una auditoría cruzada del expediente de Acme Corp y entrega:

1. MATRIZ DE INCONSISTENCIAS: tabla con | Aspecto | Propuesta o correos | Contrato | Fuente exacta | Riesgo (Alto/Medio/Bajo) |. Compara precio de la licencia, costo de implementación, fecha de Go-Live, horario de soporte, capacitación y descuento por pronto pago.
2. RIESGOS: explica el impacto operativo y financiero de las 3 inconsistencias más graves.
3. COMPROMISOS PENDIENTES Y PENALIZACIONES: qué se prometió y no está formalizado, y qué penalizaciones aplican, con cita textual.
4. ACCIONES: 3 acciones concretas para corregir los hallazgos antes de iniciar el servicio.

Regla: cada hallazgo debe indicar el documento y la sección, cláusula o correo de origen. Si algo no está en los documentos, indícalo.
```

**Resultado esperado:** Un análisis con las 4 secciones y fuentes en cada hallazgo.

**Verificación:** La matriz incluye al menos estas inconsistencias:

| Aspecto | Propuesta o correos | Contrato |
| :--- | :--- | :--- |
| Licencia anual | 12,000 USD (propuesta, sección 2) | 14,400 USD (cláusula segunda) |
| Implementación | 5,000 USD (propuesta y correo 1) | 6,500 USD (cláusula segunda) |
| Go-Live | 15 de diciembre de 2026 (propuesta y correo 2) | 15 de enero de 2027 (cláusula tercera) |
| Soporte | 24/7 (propuesta y correo 1) | Horario hábil (cláusula cuarta) |
| Capacitación | Presencial, 25 usuarios (propuesta y correo 2) | En línea, 15 usuarios (cláusula quinta) |

### Paso 3: Verificar las citas contra los documentos (4 min)

**Objetivo:** Confirmar que los hallazgos son reales antes de usarlos.

1. Elegir 4 hallazgos de la respuesta.
2. Abrir el PDF citado en cada uno y localizar la sección, cláusula o correo indicado.
3. En un documento de Word nuevo, crear una tabla con las columnas **Hallazgo**, **Fuente citada por Claude**, **¿La cita es correcta? (Sí/No)** y **Comentario**.
4. Buscar además 2 hallazgos que Claude **no** haya mencionado. Pistas:
   - El correo 2 (25 de octubre) dice adjuntar la versión firmada, pero el contrato tiene fecha de firma del 28 de octubre.
   - El procedimiento garantiza 99.9% de disponibilidad, pero la penalización solo aplica por debajo de 99.0%, y el cliente debe solicitarla en 10 días hábiles.

**Resultado esperado:** Una tabla con 4 citas verificadas y los hallazgos adicionales.

**Verificación:** Si una cita es incorrecta, marcarla con **No** y corregirla con la fuente real.

### Paso 4: Generar el informe consolidado (3 min)

**Objetivo:** Obtener un informe listo para la Gerencia.

1. Enviar a Claude:

```text
Genera un informe consolidado para la Gerencia Comercial con: resumen ejecutivo (5 líneas), matriz de inconsistencias, riesgos priorizados, compromisos pendientes, penalizaciones aplicables y plan de acción con responsable y fecha. Incluye también estos hallazgos que verifiqué: [PEGAR LOS HALLAZGOS ADICIONALES DEL PASO 3]. Máximo 2 páginas.
```

2. Copiar el informe al documento de Word, debajo de la tabla de verificación.

**Resultado esperado:** Un informe con las 6 secciones.

**Verificación:** El informe recomienda alinear el contrato con lo acordado (o renegociarlo por escrito) antes de iniciar el proyecto el 1 de noviembre de 2026.

### Paso 5: Guardar la evidencia (1 min)

**Objetivo:** Conservar el informe y la verificación.

1. Guardar el documento como `Informe_Expediente_Acme_[INICIALES].docx`.

**Resultado esperado:** Un documento con la verificación de citas y el informe consolidado.

**Verificación:** El documento contiene la tabla de verificación y las 6 secciones del informe.

## Validación y Pruebas

| Caso | Acción o prompt | Resultado esperado |
| :--- | :--- | :--- |
| Cita verificable | Abrir la cláusula tercera del contrato | Dice Go-Live el 15 de enero de 2027 |
| Compromiso pendiente | Revisar la sección de compromisos | Incluye el soporte 24/7 y la capacitación presencial prometidos por correo y no formalizados |
| Prueba adversarial | Preguntar: *"¿Qué dice la cláusula octava del contrato sobre la renovación automática?"* | Claude debe indicar que el contrato solo tiene 5 cláusulas y no menciona la renovación automática |

## Solución de Problemas

### Problema 1: Claude no permite cargar los 4 archivos o alcanzó el límite

- **Síntomas:** Mensaje de límite de archivos, de tamaño o de uso.
- **Causa:** Restricciones de la versión gratuita.
- **Solución:** Cargar primero la propuesta y el contrato, y en un segundo mensaje el procedimiento y los correos. Si se alcanza el límite de mensajes, continuar al día siguiente o con la autorización del instructor.

### Problema 2: Claude da una cita general sin la cláusula

- **Síntomas:** Hallazgos con *"según el contrato"* pero sin número de cláusula.
- **Causa:** El prompt no se aplicó de forma estricta.
- **Solución:** Enviar: *"Para cada hallazgo, agrega el documento y la cláusula, sección o número de correo exacto"*.

## Limpieza

1. Conservar `Informe_Expediente_Acme_[INICIALES].docx` en `Documentos\Practicas_IA_Comercial\Practica12`.
2. Si la política de la empresa lo indica, eliminar el proyecto o la conversación de Claude.

## Resumen

- Se organizó un expediente comercial de 4 documentos en Claude.
- Se identificaron inconsistencias de precio, fechas, soporte y capacitación, así como compromisos pendientes y penalizaciones.
- Se verificaron las citas contra los documentos y se generó un informe consolidado para el control de la operación.

---

[⬅ Anterior: Práctica 11](../Practica11/README.md) | [Inicio](../../README.md)
