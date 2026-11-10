<p align="center">
  <img src="assets/LogoNetec.png" alt="NETEC" width="300" />
</p>

# Setup Guide General

## Inteligencia Artificial Generativa Essentials aplicada a la Operación Comercial

| Control documental | Información |
|---|---|
| Clave del curso | Custom IA_GEN_ESSE_OC AB (Priv) |
| Versión del documento | 1.0 |
| Estado | BORRADOR: revisión documental completa; pendiente de validación con cuentas de participante |
| Instructor responsable | Por asignar por Netec |
| Fecha de elaboración | 2026-11-09 |
| Fecha de última validación | 2026-11-09 (revisión del repositorio) |
| Repositorio de laboratorios | [github.com/Netec-Mx/Custom-IA_GEN_ESSE_OC-AB-Priv-](https://github.com/Netec-Mx/Custom-IA_GEN_ESSE_OC-AB-Priv-) |
| Rama y revisión analizada | `changes_course`, versión 1.0 |
| Alcance revisado | 3 capítulos, 6 módulos, 12 prácticas, 22 archivos de recursos, README principal y Setup Guide |
| Modalidad del entorno | Web (servicios SaaS gratuitos) con aplicaciones de ofimática locales o en la web |

[Inicio](README.md)

# Objetivo

Preparar, para cada participante, un equipo con navegador actualizado, Microsoft Word, Excel y PowerPoint (o equivalentes en la web), cuentas gratuitas activas en ChatGPT, Microsoft Copilot, Google (Gemini, NotebookLM y Google AI Studio) y Claude, y acceso a n8n con una credencial de un modelo de IA gratuito. También se descargan los archivos ficticios de las 12 prácticas en una carpeta local. El entorno se considera listo cuando las validaciones obligatorias de la sección [Validación del Entorno](#validacion-entorno) se aprueban con la cuenta de un participante. No se requiere programación ni línea de comandos.

# Requisitos de Hardware

| Recurso | Mínimo requerido | Recomendado | Observaciones |
|---|---|---|---|
| Procesador y arquitectura | 64 bits, 2 núcleos | 4 núcleos o más | Las herramientas de IA y n8n Cloud se ejecutan en la nube |
| Memoria RAM | 8 GB | 16 GB | Varias pestañas del navegador y Office abiertos a la vez |
| Espacio libre | 2 GB | 5 GB | Los archivos de las prácticas ocupan menos de 1 MB |
| Pantalla | 1366 × 768 | 1920 × 1080 o dos monitores | Facilita comparar plataformas (Práctica 8) y trabajar en el lienzo de n8n (prácticas 6 y 7) |
| Conectividad | 10 Mbps por participante | 25 Mbps por participante | Necesaria durante todo el curso |

# Sistemas Operativos Compatibles

| Sistema operativo | Edición y versión | Arquitectura | Condición de soporte o validación |
|---|---|---|---|
| Windows 11 | Home, Pro o Enterprise | x64 | Plataforma base del curso; compatible según fabricante; pendiente de validar |
| macOS | 14 o posterior | Apple silicon o Intel | Compatible según fabricante; no validado. Los atajos de teclado cambian (Cmd en lugar de Ctrl) |

Las instrucciones usan Windows 11 y los nombres de menú de Microsoft Excel y Word en español. La Práctica 3 indica también los nombres de función en inglés.

# Software Requerido

| Componente | Edición y versión requerida | Arquitectura | Obligatorio u opcional | Fuente oficial |
|---|---|---|---|---|
| Navegador Microsoft Edge o Google Chrome | Versión estable vigente | x64 | Obligatorio | [google.com/chrome](https://www.google.com/chrome/) o [microsoft.com/edge](https://www.microsoft.com/edge) |
| Microsoft Word, Excel y PowerPoint | Escritorio o web (Office en la web gratuito con cuenta Microsoft); no se requiere licencia de Microsoft 365 Copilot | x64 | Obligatorio (para abrir y editar los archivos) | [microsoft365.com](https://www.microsoft365.com/) |
| ChatGPT | Servicio administrado, plan gratuito | N/A | Obligatorio (prácticas 8 y 11; opcional en 1 a 5) | [chatgpt.com](https://chatgpt.com/) |
| Microsoft Copilot Chat | Servicio administrado, versión gratuita | N/A | Obligatorio (prácticas 8 y 9; opcional en 1 a 5) | [copilot.microsoft.com](https://copilot.microsoft.com/) o [m365.cloud.microsoft/chat](https://m365.cloud.microsoft/chat) |
| Claude | Servicio administrado, plan gratuito | N/A | Obligatorio (prácticas 8 y 12; opcional en 1 a 5) | [claude.ai](https://claude.ai/) |
| Google Gemini | Servicio administrado, plan gratuito | N/A | Obligatorio (Práctica 8; opcional en 1 a 5) | [gemini.google.com](https://gemini.google.com/) |
| Google NotebookLM | Servicio administrado, plan gratuito | N/A | Obligatorio (Práctica 10) | [notebooklm.google.com](https://notebooklm.google.com/) |
| n8n | n8n Cloud (periodo de prueba gratuito) o n8n Community autoalojado por el instructor o TI | N/A | Obligatorio (prácticas 6 y 7) | [n8n.io/pricing](https://n8n.io/pricing/) y [docs.n8n.io/hosting](https://docs.n8n.io/hosting/) |
| Google AI Studio (API de Gemini) | Nivel gratuito | N/A | Obligatorio (prácticas 6 y 7) | [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey) |

Los servicios de IA son administrados y cambian sus modelos, funciones y límites sin previo aviso. Las prácticas no fijan una versión de modelo: registrar la versión observada y las limitaciones en el [Registro de validación](#registro-validacion).

**Criterios de uso de herramientas acordados con el cliente**

| Criterio | Aplicación en este curso |
|---|---|
| Versiones gratuitas | Todas las prácticas se realizan con versiones gratuitas o periodos de prueba sin costo; no es obligatorio adquirir licencias Premium |
| Herramientas obligatorias | Solo en los módulos 5 y 6: n8n en las prácticas 6 y 7, y ChatGPT, Copilot, Claude, Gemini y NotebookLM en las prácticas 8 a 12 |
| Flexibilidad del instructor | En los módulos 1 a 4 (prácticas 1 a 5), el instructor elige la herramienta de IA según sus capacidades, disponibilidad y límites de consumo |
| Copilot con Word, Excel y PowerPoint | Práctica 9: Copilot Chat gratuito con carga de archivos; Copilot genera el contenido o los entregables descargables. No se usa Copilot integrado en las aplicaciones de Office |
| Limitaciones de las versiones gratuitas | En todas las prácticas, el instructor puede simplificar escenarios, usar datos más pequeños o ajustar la profundidad y la extensión, conservando los objetivos y resultados esperados |

# Herramientas y Dependencias

## Paquetes, frameworks y componentes adicionales

| Dependencia | Versión o restricción | Componente que la necesita | Método de instalación o habilitación |
|---|---|---|---|
| Carga de archivos en las herramientas de IA | Incluida en los planes gratuitos, con límites diarios | Prácticas 1 a 5 y 8 a 12 | Botón **+** o clip del cuadro de mensaje; requiere sesión iniciada |
| Análisis de datos de ChatGPT (Advanced Data Analysis) | Disponible en el plan gratuito con límites | Práctica 11 | Se activa al adjuntar un CSV ([documentación](https://help.openai.com/en/articles/8437071-data-analysis-with-chatgpt)) |
| Canvas de ChatGPT | Disponible en el plan gratuito | Práctica 11 | Herramientas del cuadro de mensaje |
| Proyectos de Claude | Según el plan y la versión disponible | Práctica 12 | Panel izquierdo de Claude ([documentación](https://support.claude.com/en/articles/9517075-what-are-projects)); si no está disponible, se adjuntan los archivos en el chat |
| Fuentes y Studio de NotebookLM | Límites del plan gratuito | Práctica 10 | Panel **Fuentes** y panel **Studio** |
| Nodos de n8n | Form Trigger, Basic LLM Chain, Google Gemini Chat Model, Structured Output Parser, Switch, Edit Fields, Extract from File, Aggregate, Convert to File, n8n Form | Prácticas 6 y 7 | Incluidos en n8n Cloud y Community ([documentación](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainllm/)) |
| Credencial **Google Gemini(PaLM) Api** en n8n | Clave gratuita de Google AI Studio | Prácticas 6 y 7 | **Credentials > Create credential** ([documentación](https://docs.n8n.io/integrations/builtin/credentials/googleai/)) |
| Nodo Gmail de n8n | Opcional | Práctica 6, opción B | **Sign in with Google** desde el nodo ([documentación](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.gmail/)) |
| Archivos de las prácticas | Versión 1.0 del repositorio | Prácticas 1 a 12 | Carpetas `CapituloNN/PracticaNN/recursos/` |

## Licencias, cuentas y permisos

| Recurso o servicio | Licencia o suscripción | Cuenta o rol requerido | Permiso mínimo | Responsable de habilitación |
|---|---|---|---|---|
| ChatGPT | Gratuita | Cuenta de OpenAI | Usuario | Cada participante |
| Microsoft Copilot | Gratuita | Cuenta Microsoft (personal, de trabajo o escuela) | Usuario | Cada participante o TI del cliente |
| Gemini, NotebookLM y Google AI Studio | Gratuita | Cuenta de Google | Usuario | Cada participante |
| Claude | Gratuita | Cuenta de Anthropic | Usuario | Cada participante |
| n8n Cloud | Periodo de prueba gratuito | Cuenta de n8n (una por participante) | Propietario de su espacio | Cada participante, el mismo día o pocos días antes de las prácticas 6 y 7 |
| n8n Community (alternativa) | Licencia Sustainable Use (sin costo) | Usuario creado por el administrador | Miembro | Instructor o TI del cliente |
| Microsoft 365 | Licencia del cliente o cuenta gratuita de Office en la web | Cuenta Microsoft | Usuario | TI del cliente |
| Acceso al repositorio | Repositorio privado de GitHub | Cuenta de GitHub con acceso de lectura, o paquete ZIP entregado por el instructor | Lectura | Netec |

Las cuentas y la clave de Google AI Studio son personales. No registrar contraseñas, claves ni códigos de verificación en este repositorio ni en los entregables. El periodo de prueba de n8n Cloud es por tiempo limitado: crear la cuenta cerca de la fecha del Módulo 5 para que no venza antes.

# Instalación y Configuración

## 1. Obtener los materiales

- Repositorio autorizado: [github.com/Netec-Mx/Custom-IA_GEN_ESSE_OC-AB-Priv-](https://github.com/Netec-Mx/Custom-IA_GEN_ESSE_OC-AB-Priv-) (botón **Code > Download ZIP**) o paquete ZIP entregado por el instructor.
- Revisión: rama `main`, una vez integrados los cambios de `changes_course`.
- Directorio de trabajo: `Documentos\Practicas_IA_Comercial\` con una subcarpeta por práctica (`Practica01` a `Practica12`).
- Archivos de entrada: carpetas `recursos` de cada práctica.

## 2. Instalar o habilitar los componentes

### Navegador y ofimática

1. Verificar que Edge o Chrome esté actualizado (**Configuración > Acerca de**).
2. Verificar el acceso a Word, Excel y PowerPoint (escritorio o [microsoft365.com](https://www.microsoft365.com/)).

**Resultado esperado:** El navegador indica que está actualizado y Excel abre un libro en blanco.

### Cuentas de IA

1. Crear o iniciar sesión en ChatGPT, Copilot, Gemini, NotebookLM y Claude.
2. Aceptar los términos de uso de cada servicio.
3. Enviar un mensaje de prueba en cada uno (por ejemplo, *"Responde solo OK"*).

**Resultado esperado:** Cada servicio responde con la sesión iniciada.

### n8n y modelo de IA gratuito

1. Crear una cuenta de prueba en [n8n.io](https://n8n.io/pricing/) o recibir del instructor la dirección y el usuario de la instancia Community.
2. Obtener una clave en [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey) (**Create API key**).
3. En n8n, crear la credencial **Google Gemini(PaLM) Api** con la clave.

**Resultado esperado:** n8n abre el lienzo de flujos y la credencial queda guardada.

### Carpetas de trabajo

1. Descomprimir el ZIP del repositorio.
2. Crear `Documentos\Practicas_IA_Comercial\` y, dentro, las carpetas `Practica01` a `Practica12`.
3. Copiar a cada carpeta el contenido de `CapituloNN\PracticaNN\recursos` correspondiente.

**Resultado esperado:** 12 carpetas con 22 archivos en total.

## 3. Preparar archivos de configuración

No se requieren archivos de configuración. Los archivos de entrada están en las carpetas `recursos` y no deben modificarse antes de la práctica.

# Variables de Entorno

No se requieren variables de entorno: el curso no usa programación ni línea de comandos.

# Configuración Base para los Laboratorios

## Parámetros comunes

| Parámetro | Valor o convención | Observaciones |
|---|---|---|
| Raíz de trabajo | `Documentos\Practicas_IA_Comercial\` | Una carpeta por práctica |
| Nombre de entregables | `Nombre_[INICIALES].ext` | Ejemplo: `Matriz_Priorizacion_Procesos_LMR.xlsx` |
| Datos | Ficticios o anonimizados | No cargar información real de clientes |
| Separador de fórmulas | `;` (o `,` según la configuración regional) | Prácticas 1, 3, 4 y 8 |
| Nombres de flujos en n8n | `P06 ...` y `P07 ...` con las iniciales del participante | Evita confusiones en instancias compartidas |

## Estructura de carpetas

```text
Documentos\Practicas_IA_Comercial\
├── Practica01\ ... Practica12\   Archivos de cada práctica y entregables
```

## Recursos compartidos

No hay recursos compartidos entre participantes, salvo la instancia de n8n Community si el instructor la usa. En ese caso, cada participante crea sus propios flujos y su propia credencial.

## Correcciones de coherencia

| Inconsistencia o dependencia omitida | Configuración unificada | Ajuste necesario en las copias de trabajo |
|---|---|---|
| El repositorio tenía 5 carpetas numeradas por módulo (`Capitulo02` a `Capitulo06`); el temario define 3 capítulos con 6 módulos | `Capitulo01` a `Capitulo03`, con una carpeta y un README por práctica | Ninguno |
| Varias prácticas estaban juntas en un mismo README | Un README por práctica (12 en total) | Ninguno |
| Las prácticas requerían terminal, bash, Python, cURL y scripts, contrario al perfil "sin experiencia en programación" | Pasos con Word, Excel, PowerPoint, herramientas web y n8n sin código | Ninguno |
| Las prácticas de n8n dependían de un servidor de IA simulado en Python y de una clave de pago de OpenAI | Modelo Gemini con clave gratuita de Google AI Studio y formulario de n8n como entrada | Ninguno |
| Los archivos de entrada se generaban con scripts | 22 archivos listos para descargar en `recursos` | Ninguno |
| El archivo de cotizaciones usaba nombres de personas públicas reales | Nombres, RFC, domicilios y dominios de correo ficticios (`.example`) | Ninguno |
| El análisis de referencia de la práctica de Copilot tenía totales incorrectos (90,800 en lugar de la suma real) y atribuía mal un producto | Datos de Q1 2025 y Q1 2026 con valores de referencia recalculados | Ninguno |
| El caso de objeción pedía "demostrar" que el competidor era más caro, pero con los datos dados era más barato | Costos del competidor completos (1,290 USD al mes) y cálculo verificable | Ninguno |
| Se citaban versiones de modelos y herramientas de 2024 (Claude 3.5 Sonnet, GPT-4o, n8n 1.38.0) | Se indica "versión gratuita vigente" | Registrar la versión observada en cada curso |
| Los enlaces apuntaban a otro repositorio (`261109-Custom-IA-GEN-ESSE-OC-AB-Priv`) | Enlaces relativos dentro del repositorio | Ninguno |
| El archivo se llamaba `SETUP_GUIDE.md` | `Setup_Guide.md`, según la plantilla | Ninguno |

# Servicios Externos Requeridos

| Servicio | URL, endpoint o región | Uso | Acceso requerido |
|---|---|---|---|
| ChatGPT | [chatgpt.com](https://chatgpt.com/) | Prácticas 1 a 5 (opcional), 8 y 11 | Cuenta gratuita |
| Microsoft Copilot | [copilot.microsoft.com](https://copilot.microsoft.com/) | Prácticas 1 a 5 (opcional), 8 y 9 | Cuenta Microsoft |
| Google Gemini | [gemini.google.com](https://gemini.google.com/) | Prácticas 1 a 5 (opcional) y 8 | Cuenta de Google |
| Google NotebookLM | [notebooklm.google.com](https://notebooklm.google.com/) | Práctica 10 | Cuenta de Google |
| Claude | [claude.ai](https://claude.ai/) | Prácticas 1 a 5 (opcional), 8 y 12 | Cuenta gratuita |
| n8n Cloud | Dominio asignado al crear la cuenta (`*.app.n8n.cloud`) | Prácticas 6 y 7 | Cuenta de prueba |
| API de Gemini | `generativelanguage.googleapis.com` | Prácticas 6 y 7 (llamada desde n8n) | Clave gratuita de Google AI Studio |
| GitHub | [github.com](https://github.com/) | Descarga de materiales | Lectura del repositorio |

## Configuración de red

| Origen | Destino | Protocolo y puerto | Sentido | Condición |
|---|---|---|---|---|
| Equipo del participante | chatgpt.com, copilot.microsoft.com, m365.cloud.microsoft, gemini.google.com, notebooklm.google.com, aistudio.google.com, claude.ai, n8n.io, app.n8n.cloud, github.com | HTTPS 443 | Saliente | Los dominios no deben estar bloqueados por el proxy o el firewall del cliente |
| Instancia de n8n (Cloud o Community) | generativelanguage.googleapis.com | HTTPS 443 | Saliente | Necesario para que el nodo de IA responda |

# Creación de Entornos / Máquinas Virtuales / Emuladores

No aplica para los participantes. Si el instructor o TI decide usar n8n Community en lugar de n8n Cloud, debe instalarlo con anticipación siguiendo la [documentación oficial de hosting](https://docs.n8n.io/hosting/) y entregar a cada participante su usuario y la dirección de acceso.

<a id="validacion-entorno"></a>

# Validación del Entorno

| ID | Componente o capacidad | Procedimiento | Resultado esperado | Evidencia mínima |
|---|---|---|---|---|
| V-01 | Navegador y materiales | Abrir el repositorio y descargar el ZIP | El ZIP contiene `Capitulo01` a `Capitulo03` | Captura |
| V-02 | Ofimática | Abrir `Matriz_Priorizacion_Procesos.xlsx` y elegir *Alto* y *Alta* en la fila 2 | La columna **Cuadrante_prioridad** muestra *Victoria rápida* | Captura |
| V-03 | ChatGPT | Adjuntar `Datos_Ventas_Q4_2025.csv` y pedir el número de filas | 215 filas | Captura |
| V-04 | Copilot | Adjuntar `Ventas_Trimestrales.xlsx` (o el CSV) y pedir el total de `Ventas_Q1_2026` | 102,900 | Captura |
| V-05 | NotebookLM | Crear un cuaderno y subir `Politica_Descuentos_CloudLogix.pdf` | La fuente aparece en el panel | Captura |
| V-06 | Claude | Adjuntar `Contrato_Servicio_Acme.pdf` y preguntar la fecha de Go-Live | 15 de enero de 2027 | Captura |
| V-07 | Gemini | Enviar *"Responde solo OK"* | Responde OK | Captura |
| V-08 | n8n y modelo de IA | Crear un flujo con **On new n8n Form event** + **Basic LLM Chain** con Gemini y el prompt *"Responde solo OK"*; ejecutar | El nodo de IA responde OK | Captura de la ejecución |

**Criterio de entorno listo:** V-01 a V-08 aprobadas con la cuenta de un participante. Si V-08 falla por un bloqueo de red, el instructor debe resolverlo antes del Módulo 5 o usar una instancia de n8n con salida a Internet.

# Comandos de Verificación

No aplica. El curso se valida en interfaces web con los procedimientos V-01 a V-08, sin instalar herramientas de línea de comandos.

# Troubleshooting

| Síntoma | Causa probable | Comprobación | Corrección | Validación posterior |
|---|---|---|---|---|
| Un servicio de IA no carga | Bloqueo de red del cliente | Abrir el sitio desde otra red | Solicitar a TI la autorización del dominio | V-03 a V-08 |
| Límite de mensajes o de archivos alcanzado | Restricciones de la versión gratuita | Mensaje del servicio | Esperar, usar otra herramienta (prácticas 1 a 5) o reducir el alcance | Repetir el paso |
| Un archivo no se adjunta | Formato o tamaño no admitido | Mensaje de error | Usar la versión CSV o pegar el contenido como texto | Repetir el paso |
| Las fórmulas de Excel marcan error | Separador regional o Excel en inglés | Mensaje de error de la fórmula | Cambiar `;` por `,` o usar los nombres de función en inglés | V-02 |
| El nodo de IA de n8n responde con error 429 o *quota* | Límite del nivel gratuito de la API de Gemini | Mensaje del nodo | Esperar un minuto o elegir otro modelo Flash de la lista | V-08 |
| La credencial de Gemini no se guarda | Clave mal copiada o API no disponible en la región de la cuenta | Probar la clave en Google AI Studio | Crear una clave nueva; usar otra cuenta de Google si la región no está habilitada | V-08 |
| El periodo de prueba de n8n Cloud venció | Cuenta creada con demasiada anticipación | Mensaje al iniciar sesión | Crear la cuenta con otro correo o usar la instancia Community del instructor | V-08 |
| NotebookLM no está disponible | Restricción de edad, región o administración de la cuenta | Mensaje de acceso | Usar una cuenta de Google que cumpla los requisitos | V-05 |

# Checklist Final

- [ ] Navegador actualizado y Word, Excel y PowerPoint disponibles.
- [ ] Cuentas gratuitas activas en ChatGPT, Copilot, Google (Gemini, NotebookLM y AI Studio) y Claude.
- [ ] Acceso a n8n (prueba de n8n Cloud vigente o instancia Community) y credencial de Gemini guardada.
- [ ] Dominios de las herramientas permitidos en la red del cliente.
- [ ] 22 archivos de las prácticas descargados en `Documentos\Practicas_IA_Comercial\`.
- [ ] Validaciones V-01 a V-08 aprobadas y registradas.

# Resumen

Para iniciar el curso, cada participante necesita un navegador actualizado, Word, Excel y PowerPoint, cuentas gratuitas en las cuatro plataformas de IA y en NotebookLM, acceso a n8n con una clave gratuita de Gemini y los archivos ficticios de las prácticas descargados. No se requiere programación ni instalación de lenguajes o herramientas de línea de comandos.

<a id="registro-validacion"></a>

## Registro de validación

| Fecha | Responsable | Plataforma o entorno probado | Resultado | Limitaciones o acciones pendientes |
|---|---|---|---|---|
| 2026-11-09 | Desarrollo de contenido Netec | Revisión del repositorio: estructura, enlaces, recursos, tiempos, nombres y alineación con el temario. Se recalcularon los valores de referencia de las prácticas 1, 3, 7, 8, 9 y 11 a partir de los archivos | APTO para publicación del repositorio | No se ejecutaron las prácticas con cuentas de participante ni los flujos de n8n. Pendiente: V-01 a V-08 |

## Referencias oficiales

| Documento o recurso | URL | Fecha de consulta |
|---|---|---|
| Análisis de datos con ChatGPT | https://help.openai.com/en/articles/8437071-data-analysis-with-chatgpt | 2026-11-09 |
| Proyectos de Claude | https://support.claude.com/en/articles/9517075-what-are-projects | 2026-11-09 |
| Planes de n8n | https://n8n.io/pricing/ | 2026-11-09 |
| n8n: hosting de la edición Community | https://docs.n8n.io/hosting/ | 2026-11-09 |
| n8n: nodo n8n Form Trigger | https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.formtrigger/ | 2026-11-09 |
| n8n: nodo Basic LLM Chain | https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainllm/ | 2026-11-09 |
| n8n: credencial de Google Gemini | https://docs.n8n.io/integrations/builtin/credentials/googleai/ | 2026-11-09 |
| Precios y nivel gratuito de la API de Gemini | https://ai.google.dev/gemini-api/docs/pricing | 2026-11-09 |
| Política de privacidad de OpenAI | https://openai.com/es-ES/policies/privacy-policy/ | 2026-11-09 |
| Declaración de privacidad de Microsoft | https://www.microsoft.com/es-es/privacy/privacystatement | 2026-11-09 |
| Política de privacidad de Google | https://policies.google.com/privacy | 2026-11-09 |
| Política de privacidad de Anthropic | https://www.anthropic.com/legal/privacy | 2026-11-09 |

[Inicio](README.md)
