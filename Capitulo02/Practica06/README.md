# Práctica 6. Construir un flujo automatizado en n8n que reciba una solicitud comercial, utilice un modelo de IA para clasificarla según su prioridad, genere un resumen automático y proponga un borrador de respuesta para el ejecutivo responsable

**Duración de la práctica:** 30 minutos

## Descripción
Los participantes utilizarán n8n Cloud y su asistente de inteligencia artificial integrado en la pantalla principal para construir un flujo automatizado mediante instrucciones en lenguaje natural. El sistema recibirá una solicitud comercial, utilizará un modelo de inteligencia artificial para clasificarla según su prioridad, generará un resumen ejecutivo y redactará un borrador de respuesta para el ejecutivo responsable.

---

## Sección 0: Acceso a la Interfaz y Configuración con Inteligencia Artificial

1. **Paso a paso para ingresar a n8n Cloud:**
   * Ingresa a la plataforma n8n mediante tu navegador web con tus credenciales institucionales.
   * Al iniciar sesión, la interfaz te mostrará de forma predeterminada la pantalla del asistente de inteligencia artificial con la barra de texto central bajo la pregunta **What do you want to automate?**.
   * Utilizarás directamente este chat conversacional de inteligencia artificial tanto para la demostración como para la práctica, sin necesidad de arrastrar nodos manualmente.

2. **Explicación de conceptos clave para la automatización:**
   * **Plataforma de bajo código:** Espacio visual que permite integrar aplicaciones y modelos de inteligencia artificial mediante flujos lógicos conectados, reduciendo la necesidad de programación tradicional.
   * **Estructura JSON:** Formato estándar basado en texto estructurado mediante llaves y pares de clave y valor, utilizado para intercambiar datos organizados entre sistemas.
   * **Webhook:** Mecanismo de integración que permite a una aplicación enviar información en tiempo real hacia otra plataforma cada vez que se genera un evento comercial.

---

## Sección 1: Demostración del Instructor (3 Pasos)

1. **Creación del flujo automatizado mediante instrucción a la inteligencia artificial en n8n:**
   * El instructor se ubica en la barra de chat del asistente y le pide generar el flujo completo escribiendo lo siguiente:
     ```text
     Crea un flujo automatizado que reciba una solicitud comercial por webhook,
     la clasifique por prioridad mediante inteligencia artificial
     y genere un borrador de respuesta.
     ```

2. **Validación del esquema de datos y variables procesadas:**
   * El instructor verifica que la estructura generada automáticamente contenga los datos del cliente y el mensaje de entrada listos para ser procesados.

3. **Prueba de ejecución y verificación de la salida comercial:**
   * El instructor hace clic en el botón de prueba o ejecución dentro de la misma interfaz generada por la inteligencia artificial y observa cómo el sistema entrega la prioridad, el resumen y el borrador de respuesta ya listos.

---

## Sección 2: Práctica Guiada del Participante (5 Pasos)

1. **Acceso al panel principal y preparación del asistente de inteligencia artificial:**
   * Desde tu panel principal de n8n Cloud donde visualizas la barra de chat con la pregunta **What do you want to automate?**, mantén seleccionada la opción **Assistant** en el menú lateral izquierdo.

2. **Ingreso del prompt maestro para la generación automática del flujo:**
   * Escribe y envía la siguiente instrucción detallada en varias líneas dentro de la barra de chat de la inteligencia artificial de n8n:
     ```text
     Construye un flujo automatizado completo de atención comercial que realice lo siguiente:
     1. Inicie con un nodo de Webhook preparado para recibir peticiones POST con datos de clientes.
     2. Integre un nodo de procesamiento de inteligencia artificial que analice el mensaje recibido.
     3. Clasifique la prioridad comercial estrictamente en Alta, Media o Baja basándote en la urgencia.
     4. Genere un resumen de dos líneas con la necesidad exacta y proponga un borrador de respuesta formal.
     ```

3. **Configuración de los datos de prueba en formato JSON dentro del flujo generado:**
   * Una vez que la inteligencia artificial genere la estructura visual del flujo, abre el nodo de entrada y configura una solicitud de prueba utilizando la siguiente estructura JSON con datos complejos:
     ```json
     {
       "solicitud_id": "REQ-8821",
       "razon_social": "Industrias Metalmecánicas del Sur",
       "contacto_nombre": "Carlos Mendoza",
       "correo_contacto": "cmendoza@metalmecanicasur.com",
       "detalle_mensaje": "Requerimos con extrema urgencia la cotización y despacho prioritario de trescientas válvulas de alta presión para nuestra línea de producción principal, ya que una falla imprevista detuvo nuestra operación esta mañana."
     }
     ```

4. **Ajuste de la instrucción interna del nodo de inteligencia artificial:**
   * Dentro del nodo de inteligencia artificial creado automáticamente en tu lienzo, verifica y ajusta la directriz interna para garantizar una salida limpia y estructurada mediante el siguiente comando multilineal:
     ```text
     Actúa como un Analista de Operaciones Comerciales.
     Procesa el JSON recibido y devuelve obligatoriamente:
     - Nivel de Prioridad: (Alta, Media o Baja).
     - Resumen Ejecutivo: (Necesidad operativa del cliente).
     - Borrador de Respuesta: (Correo formal de tres párrafos redactado por el ejecutivo).
     ```

5. **Ejecución y verificación del flujo automatizado:**
   * Haz clic en el botón de prueba o ejecución manual en tu lienzo de n8n, verifica en el panel de resultados que la inteligencia artificial procese el JSON de prueba, determine la prioridad como Alta y entregue el borrador de respuesta comercial listo para el equipo de ventas.

## Resultado esperado
Un flujo automatizado completo construido mediante el asistente de inteligencia artificial de n8n Cloud[cite: 3], capaz de recibir solicitudes comerciales mediante estructuras JSON, clasificarlas según su urgencia y generar resúmenes con borradores de respuesta automáticos.
