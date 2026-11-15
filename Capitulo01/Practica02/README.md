# Práctica 2. Evaluar respuestas generadas por la IA para identificar errores, alucinaciones y posibles riesgos antes de compartir información con clientes

**Duración de la práctica:** 30 minutos

## Descripción
Los participantes utilizarán Claude y Google Gemini para someter a verificación rigurosa los borradores y propuestas comerciales generados por inteligencia artificial. A partir de una ficha de producto autogenerada con especificaciones estrictas, los asistentes pondrán a prueba la tendencia del modelo a inventar beneficios o condiciones no autorizadas, detectarán alucinaciones y aplicarán protocolos de auditoría preventiva antes de enviar comunicaciones a clientes reales.

---

## Sección 1: Demostración del Instructor (3 Pasos)

1. **Autogeneración de la ficha oficial de producto en Claude:**
   * Abre Claude y envía la siguiente instrucción para crear una política comercial con restricciones muy específicas:
     ```text
     Actúa como un Gerente de Producto Empresarial. Redacta una ficha técnica breve de 120 palabras para nuestro servicio llamado Nube Segura Pro. Establece exactamente estas tres reglas estrictas: el precio mensual fijo es de 500 dólares, el soporte técnico funciona únicamente de lunes a viernes en horario de oficina, y el contrato exige una permanencia mínima de doce meses sin excepciones.
     ```

2. **Inducción de alucinaciones comerciales en Google Gemini:**
   * Abre Google Gemini en otra pestaña, pega la ficha técnica generada en el paso anterior y envíale la siguiente instrucción diseñada para forzar al modelo a inventar datos comerciales:
     ```text
     Actúa como un ejecutivo de ventas entusiasta que quiere cerrar el negocio hoy mismo. Redacta un correo persuasivo para un cliente corporativo ofreciendo Nube Segura Pro. Asegúrate de incluir detalles atractivos sobre el soporte técnico veinticuatro siete en fines de semana, los descuentos por pago anual y la posibilidad de cancelar el contrato en cualquier momento sin penalidad.
     ```

3. **Auditoría cruzada de veracidad en Claude:**
   * Copia el correo generado por Google Gemini, regresa a la conversación de Claude donde está la ficha original y ejecuta la verificación:
     ```text
     Actúa como un Auditor de Cumplimiento Comercial. Compara el correo comercial que te comparto a continuación frente a la ficha técnica oficial de Nube Segura Pro que creaste al inicio. Lista exactamente qué afirmaciones del correo son falsas, inventadas o contradicen las políticas de la empresa.
     ```

---

## Sección 2: Práctica Guiada del Participante (5 Pasos)

1. **Autogeneración de un catálogo comercial con restricciones estrictas en Claude:**
   * Abre Claude y envía la siguiente instrucción para generar el documento maestro de políticas de venta de una empresa ficticia:
     ```text
     Actúa como el Director Comercial de Soluciones Logísticas Andinas. Redacta un documento normativo de 250 palabras titulado Política Comercial y Tarifaria Vigente con las siguientes condiciones inmodificables: el servicio de transporte refrigerado tiene un recargo obligatorio del veinte por ciento sobre la tarifa base, los tiempos de entrega garantizados para rutas nacionales son de cuarenta y ocho a setenta y dos horas hábiles, no se realizan entregas los días domingo ni festivos, el crédito comercial máximo aprobado para clientes nuevos es de quince días calendario, y ningún ejecutivo está autorizado a ofrecer envíos gratuitos de prueba.
     ```
   * Guarda este texto, ya que servirá como tu fuente única de verdad comercial.

2. **Simulación de atención al cliente bajo presión en Google Gemini:**
   * Abre Google Gemini, pega la Política Comercial y Tarifaria Vigente generada en Claude y envía la siguiente instrucción para provocar errores y alucinaciones comerciales:
     ```text
     Actúa como un asesor comercial presionado por cumplir su meta mensual. Un cliente muy importante amenaza con irse con la competencia si no le damos mejores condiciones. Redacta una propuesta comercial urgente de tres párrafos ofreciendo transporte refrigerado sin recargos adicionales, entregas garantizadas en veinticuatro horas incluyendo domingos, treinta días de plazo para el pago de su primera factura y un primer envío de prueba totalmente gratuito.
     ```

3. **Detección sistemática de alucinaciones y riesgos contractuales en Claude:**
   * Copia la propuesta comercial generada por Google Gemini, regresa a tu sesión de Claude y envía la siguiente instrucción de auditoría:
     ```text
     Actúa como el Gerente de Riesgos y Control Comercial. Audita la propuesta comercial redactada para el cliente frente a la Política Comercial y Tarifaria Vigente definida en el primer paso. Construye una tabla con cuatro columnas: Afirmación en la Propuesta, Dato Real según la Política, Tipo de Error o Alucinación y Riesgo Financiero o Legal para la Empresa.
     ```

4. **Corrección controlada y reformulación ética en Google Gemini:**
   * Regresa a Google Gemini y envía la siguiente instrucción para obligar al modelo a reescribir la propuesta respetando estrictamente los límites reales sin inventar beneficios:
     ```text
     Reescribe la propuesta comercial anterior eliminando todas las promesas falsas y ajustándote ciento por ciento a las reglas de la Política Comercial y Tarifaria Vigente. Mantén un tono empático, profesional y persuasivo, destacando el valor de nuestra puntualidad garantizada de cuarenta y ocho a setenta y dos horas y la seguridad de nuestra cadena de frío, sin ofrecer ningún beneficio no autorizado.
     ```

5. **Creación de una lista de verificación preventiva en Claude:**
   * Finaliza la práctica en Claude generando un protocolo de control para todo el equipo de ventas:
     ```text
     Actúa como un Líder de Calidad Comercial. Diseña una lista de verificación de cinco puntos obligatorios que todo ejecutivo comercial debe revisar antes de enviar a un cliente una cotización o correo redactado con apoyo de inteligencia artificial, con el fin de evitar alucinaciones, compromisos incumplibles o pérdidas financieras.
     ```

## Resultado esperado
Una matriz de auditoría que expone las alucinaciones comerciales inducidas en modelos generativos, una propuesta comercial corregida y alineada estrictamente a las políticas vigentes, y una lista de verificación preventiva para proteger la operación comercial.
