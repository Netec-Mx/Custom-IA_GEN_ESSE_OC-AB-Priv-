# Práctica 6. Construir un flujo automatizado en n8n que reciba una solicitud comercial, utilice un modelo de IA para clasificarla según su prioridad, genere un resumen automático y proponga un borrador de respuesta para el ejecutivo responsable

**Duración de la práctica:** 30 minutos

## Descripción
Los participantes utilizarán **n8n Cloud** y su asistente de inteligencia artificial en la pantalla principal para construir un flujo automatizado **escribiendo una sola instrucción en lenguaje natural**. No necesitarán hacer clic en ningún bloque, configurar estructuras JSON ni programar; el sistema generará y conectará todo automáticamente para recibir solicitudes comerciales, clasificarlas según su prioridad mediante IA, crear resúmenes ejecutivos y redactar borradores de respuesta para el ejecutivo responsable.

---

## Sección 0: Acceso a la Interfaz y Conceptos Básicos

1. **Paso a paso para ingresar a n8n Cloud:**
   * Ingresa a la plataforma n8n con tus credenciales institucionales.
   * Al iniciar sesión, verás de forma predeterminada la pantalla principal del asistente con la barra de texto central bajo la pregunta **What do you want to automate?**.
   * Todo el trabajo se realiza directamente en este chat, dejando que la inteligencia artificial dibuje y conecte los bloques por ti.

2. **Conceptos clave en lenguaje sencillo:**
   * **Automatización Conversacional:** Creación de flujos de trabajo dictando órdenes directas por escrito a la IA, sin manipular componentes visuales uno por uno ni escribir código.
   * **Chat de Prueba Integrado:** Ventana de conversación directa que permite enviar mensajes normales para verificar el funcionamiento del flujo al instante.

---

## Sección 1: Demostración del Instructor (3 Pasos)

1. **Creación automática del flujo mediante una orden directa:**
   * El instructor se ubica en la barra de chat del asistente (**What do you want to automate?**) y escribe un único comando maestro:

     ```text
     Crea un flujo automatizado completo que inicie con un chat de prueba para escribir una solicitud comercial,
     luego use inteligencia artificial para clasificar su prioridad (Alta, Media o Baja),
     genere un resumen ejecutivo corto y redacte un borrador de respuesta para el ejecutivo responsable.
     ```

2. **Verificación visual del flujo generado por la IA:**
   * El instructor muestra cómo la pantalla de n8n se llena automáticamente con los bloques conectados sin haber tenido que abrir ni configurar ningún nodo de forma manual.

3. **Prueba inmediata escribiendo un mensaje:**
   * El instructor abre el chat lateral, escribe una solicitud comercial normal *"Necesitamos cotizar urgentemente 100 licencias de software porque nuestra operación arranca la próxima semana"*, y muestra cómo la IA responde al instante con la prioridad, el resumen y el borrador de respuesta ya listos.

---

## Sección 2: Práctica Guiada del Participante (5 Pasos)

1. **Acceso al chat principal del asistente en n8n Cloud:**
   * Desde tu panel principal de n8n Cloud, mantén la vista en la barra de texto central con la pregunta **What do you want to automate?** (o haz clic en **Assistant** en el menú izquierdo).

2. **Envío del prompt maestro para que la IA haga todo el trabajo:**
   * Copia y envía la siguiente instrucción detallada dentro del chat de la inteligencia artificial:

     ```text
     Construye un flujo automatizado de atención comercial de punta a punta que haga lo siguiente:
     1. Inicie con un nodo de Chat (Chat Trigger) para recibir solicitudes comerciales en texto normal.
     2. Conecte un nodo de inteligencia artificial encargado de analizar el mensaje recibido.
     3. Clasifique la prioridad comercial estrictamente en Alta, Media o Baja basándose en la urgencia del cliente.
     4. Genere un resumen ejecutivo de dos líneas con la necesidad exacta y redacte un borrador de respuesta formal listo para el ejecutivo responsable.
     Genera todo el flujo automáticamente en mi pantalla.
     ```

3. **Verificación visual del flujo generado por la IA:**
   * Observa cómo el asistente de n8n despliega instantáneamente los bloques conectados en tu lienzo de trabajo sin requerir que hagas clic en ninguno de ellos para configurarlos.

4. **Apertura del chat de prueba para enviar una solicitud real:**
   * En la parte inferior o lateral de tu pantalla, haz clic en el botón de prueba o en **Open chat**.
   * Escribe y envía la siguiente solicitud comercial en lenguaje cotidiano (sin códigos ni formatos especiales):

     ```text
     Hola equipo, les escribo desde Industrias Metalmecánicas del Sur. Requerimos con extrema urgencia la cotización y despacho prioritario de trescientas válvulas de alta presión para nuestra línea de producción principal, ya que una falla imprevista detuvo nuestra operación esta mañana. Quedo atento, Carlos Mendoza.
     ```

5. **Verificación del resultado instantáneo:**
   * Revisa la ventana de conversación y observa cómo el sistema procesa tu mensaje de forma autónoma, entregando la prioridad comercial clasificada como **Alta**, el resumen ejecutivo de la necesidad del cliente y el borrador de respuesta listo para el ejecutivo de ventas.

## Resultado esperado
Un flujo automatizado completo construido mediante el asistente de inteligencia artificial de n8n Cloud, capaz de recibir solicitudes comerciales mediante estructuras JSON, clasificarlas según su urgencia y generar resúmenes con borradores de respuesta automáticos.
