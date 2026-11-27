# Práctica 12. Analizar contratos, propuestas comerciales, procedimientos y correos relacionados con un proceso comercial utilizando Claude para identificar inconsistencias, riesgos, compromisos pendientes y generar un informe consolidado para apoyar el control de la operación

**Duración de la práctica:** 30 minutos

## Descripción
Los participantes utilizarán la funcionalidad de **Proyectos en Claude (Claude Projects)** para gestionar un expediente comercial completo. Claude se encargará de crear, centralizar y auditar de forma autónoma textos multicanal (extractos de contratos, propuestas de valor, procedimientos operativos y cadenas de correos electrónicos). Mediante instrucciones especializadas, los participantes identificarán riesgos legales ocultos, contradicciones contractuales, compromisos pendientes y redactarán un informe consolidado de control.

---

## Cómo acceder y configurar Proyectos en Claude (Claude Projects)

1. **Acceso a la plataforma:**
   * Ingresa a tu cuenta de Claude en la web oficial (claude.ai).
2. **Creación del Proyecto:**
   * En el menú lateral izquierdo, haz clic en la opción **Proyectos** (Projects) y selecciona **Crear nuevo proyecto** (Create project).
   * Asigna un nombre claro al espacio de trabajo, por ejemplo: `Auditoría Comercial B2B`.
3. **Configuración de instrucciones del sistema (System Prompts del Proyecto):**
   * Configura las directrices del proyecto para que Claude actúe permanentemente como un auditor corporativo especializado en revisión contractual y gestión de riesgos.

---

## Sección 1: Demostración del Instructor - Tres Pasos

1. **Autogeneración del expediente comercial integrado en Claude Projects:**
   * Abre tu proyecto en Claude y envía la siguiente instrucción para que el modelo cree de forma autónoma los documentos base:

     ```text
     Actúa como un Administrador de Operaciones Legales Comerciales.
     Genera de manera completamente autónoma un expediente comercial simulado que incluya cuatro textos cortos:
     1. Un fragmento de propuesta comercial con plazos flexibles.
     2. Una cláusula de contrato restrictiva con penalidades severas.
     3. Un procedimiento interno de control de plazos.
     4. Una cadena de correos electrónicos con promesas hechas al cliente.
     Mantén estos textos como contexto activo para las siguientes consultas del proyecto.
     ```

2. **Auditoría de contradicciones y riesgos en el proyecto:**
   * Solicita al modelo revisar las fuentes autogeneradas mediante el siguiente comando:

     ```text
     Actúa como un Auditor de Riesgos Legales y Comerciales.
     Revisa el expediente comercial autogenerado en este proyecto y detecta si existen contradicciones directas
     entre las promesas hechas por correo electrónico y los términos restrictivos del contrato,
     evaluando el riesgo financiero asociado para la compañía.
     ```

3. **Generación del informe consolidado de control comercial:**
   * Finaliza la demostración estructurando el reporte gerencial con la siguiente instrucción:

     ```text
     Actúa como un Director de Operaciones Comerciales.
     Redacta un informe ejecutivo de control de dos párrafos dirigido al comité legal y de ventas,
     resumiendo las principales inconsistencias detectadas en el expediente autogenerado
     y proponiendo una adenda contractual urgente para blindar la operación.
     ```

---

## Sección 2: Práctica Guiada del Participante - Cinco Pasos

1. **Autogeneración del expediente comercial multicanal en el espacio de trabajo:**
   * Crea un nuevo proyecto en Claude titulado **Auditoría de Contratos B2B** y envía la siguiente instrucción para que la plataforma genere los textos simulados de forma autónoma:

     ```text
     Actúa como un Ingeniero de Documentación Comercial.
     Genera de manera completamente autónoma un expediente comercial compuesto por cuatro documentos de texto integrados:
     1. Una propuesta de valor para implementación de software con soporte por un año.
     2. Un borrador de contrato con penalidades estrictas y soporte limitado a seis meses.
     3. Un procedimiento interno que exige autorizaciones previas para cambios de plazos.
     4. Un correo de negociación donde el equipo comercial otorga concesiones especiales al cliente.
     Confirma la generación del expediente y resume en tres líneas el conflicto principal detectado.
     ```

2. **Auditoría cruzada de inconsistencias y contradicciones normativas:**
   * Envía la siguiente instrucción para que Claude contraste de forma masiva los documentos autogenerados:

     ```text
     Actúa como un Auditor Jurídico Comercial.
     Realiza una auditoría cruzada de los cuatro documentos autogenerados en el proyecto y genera una tabla con tres columnas:
     Documento o Fuente, Inconsistencia Detectada (Contradicción) y Nivel de Riesgo (Alto, Medio, Bajo).
     Enfócate en las diferencias críticas entre la propuesta inicial y el borrador de contrato.
     ```

3. **Mapeo de compromisos pendientes y obligaciones cruzadas:**
   * Solicita al modelo inventariar las tareas que quedaron sueltas utilizando el siguiente comando:

     ```text
     Actúa como un Administrador de Proyectos Comerciales.
     A partir de los correos y procedimientos generados en el expediente,
     extrae una lista de control con cuatro compromisos operativos pendientes que la empresa debe resolver inmediatamente
     para evitar un incumplimiento con el cliente corporativo.
     ```

4. **Diseño de recomendaciones de mitigación y redacción de adendas correctivas:**
   * Pide la redacción de propuestas de ajuste normativo utilizando la siguiente instrucción:

     ```text
     Actúa como un Especialista en Negociación y Redacción Contractual.
     Utilizando el contexto documental autogenerado en el proyecto, redacta el texto formal de una adenda correctiva para modificar el contrato,
     alineando los plazos y condiciones de soporte técnico con la propuesta inicial
     y ajustando las penalidades a un rango razonable de mercado para destrabar la negociación.
     ```

5. **Consolidación del informe ejecutivo de control comercial para la gerencia:**
   * Finaliza la práctica compilando todo el análisis en un informe directivo mediante el siguiente comando:

     ```text
     Actúa como un Director de Operaciones y Control Comercial.
     Redacta un informe ejecutivo consolidado titulado Auditoría de Riesgos y Cierre de Contrato,
     estructurado con:
     1. Resumen ejecutivo de la situación del expediente basado en los documentos autogenerados.
     2. Matriz de riesgos legales y operativos priorizados.
     3. Plan de acción inmediato con responsables sugeridos para el equipo de preventas y legal antes de fin de semana.
     ```

## Resultado esperado
Un análisis integral de un expediente comercial multicanal autogenerado y centralizado en **Claude Projects**, capaz de auditar fuentes documentales creadas por la inteligencia artificial, identificar contradicciones entre contratos, propuestas, procedimientos y correos, respaldado por una matriz de riesgos, una propuesta de adenda correctiva y un informe ejecutivo de control para la gerencia.
