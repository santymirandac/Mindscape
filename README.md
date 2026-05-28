🤖 MINDSCAPE — Laboratorio Digital de Aprendizaje
> Aplicación educativa gamificada sobre Hardware y Redes de Computadores para estudiantes de básica secundaria.
---
📋 Información General
Campo	Detalle
Nombre de la app	Mindscape
Subtítulo	Laboratorio Digital de Aprendizaje
Autor	Santiago Miranda
Programa Académico	Licenciatura en Tecnología
Asignatura	Hardware y Redes
Institución	Universidad del Magdalena
Año	2026
Archivo principal	`Mindscape\_v2.html`
Tecnología	HTML5 · CSS3 · JavaScript Vanilla (sin dependencias externas)
---
🎯 Propósito
Mindscape es una herramienta didáctica interactiva diseñada para que estudiantes de básica secundaria (5to a 11vo grado) aprendan los conceptos fundamentales de hardware de computadores y redes de forma lúdica, a través de misiones, retos de selección múltiple, retroalimentación inmediata y un sistema de progreso gamificado.
---
🗺️ Estructura de la Aplicación
La aplicación está organizada en pantallas navegables sin recarga de página:
```
Perfil → Home → Lección → Juego → Fin de Mundo / Game Over
                  ↓
              Ranking
                  ↓
              Créditos
```
Pantallas
Pantalla	ID	Descripción
Perfil	`screen-profile`	Registro inicial: avatar, nombre y grado. Persiste en localStorage.
Home	`screen-home`	Portada principal con los 4 mundos, sección "Cómo se usa" y accesos a Ranking y Créditos.
Lección	`screen-lesson`	Introducción teórica del mundo seleccionado: conceptos clave antes de jugar.
Juego	`screen-game`	Pantalla de preguntas con temporizador, vidas, puntaje y barra de progreso.
Fin de Mundo	`screen-worldend`	Resultados al completar un mundo: puntaje, respuestas correctas, tiempo promedio y estrellas.
Game Over	`screen-gameover`	Pantalla de derrota al perder las 3 vidas. Permite reintentar.
Ranking	`screen-ranking`	Tabla de los mejores puntajes registrados en el dispositivo (localStorage).
Créditos	`screen-credits`	Información del autor, institución, tecnologías y descripción de la app.
---
🌍 Mundos y Contenido
La app contiene 4 mundos temáticos, cada uno con 5 niveles de dificultad progresiva.
Mundo 01 — 🖥️ Hardware Interno
Componentes dentro del gabinete del computador y sus funciones.
Conceptos: CPU · RAM · Disco Duro / SSD · Fuente de poder · Tarjeta madre · Tarjeta de video
Nivel	Tipo de reto
1	Identificar el componente por descripción técnica (CPU)
2	Diagnosticar problema por síntomas (RAM insuficiente)
3	Relacionar descripción con componente (Tarjeta madre)
4	Comparar tecnologías HDD vs SSD
5	Análisis de falla por códigos de pitido del BIOS
---
Mundo 02 — 🖱️ Periféricos
Dispositivos externos de entrada, salida y almacenamiento.
Conceptos: Periférico de Entrada · Periférico de Salida · Almacenamiento Externo · Periférico Mixto
Nivel	Tipo de reto
1	Clasificar periférico según función
2	Diagnosticar problema de impresora
3	Identificar periférico mixto (pantalla táctil)
4	Seleccionar periférico correcto para una tarea
5	Resolver caso de monitor sin señal
---
Mundo 03 — 🌐 Redes de Computadores
Conceptos de conectividad, topologías y protocolos.
Conceptos: LAN · MAN · WAN · Router · Switch · Protocolo TCP/IP · Topología en estrella
Nivel	Tipo de reto
1	Clasificar tipo de red por alcance
2	Identificar función del router vs switch
3	Analizar topología de red
4	Distinguir LAN, MAN y WAN
5	Diagnosticar falla de conectividad parcial
---
Mundo 04 — 🔧 Mantenimiento y Soporte
Diagnóstico, mantenimiento preventivo y correctivo de computadores.
Conceptos: Mantenimiento Preventivo · Mantenimiento Correctivo · Temperatura · Limpieza Interna · Diagnóstico · Drivers
Nivel	Tipo de reto
1	Clasificar tipo de mantenimiento
2	Diagnosticar apagado por sobrecalentamiento
3	Identificar herramientas necesarias
4	Analizar error de pantalla azul (BSOD)
5	Planear mantenimiento integral
---
🎮 Mecánicas de Juego
Mecánica	Detalle
Vidas	3 vidas por mundo (corazones 💜). Se pierde una por respuesta incorrecta o tiempo agotado.
Temporizador	30 segundos por pregunta. La barra cambia a naranja (≤60%) y rojo (≤30%).
Puntaje	`máx(10, 100 - tiempo\_usado × 2)` — responder rápido da más puntos.
Pista	Cada pregunta tiene una pista ocultable (clic para revelar).
Retroalimentación	Modal con explicación y frase de memoria tras cada respuesta.
Estrellas	⭐ (< 60% correctas) · ⭐⭐ (60–89%) · ⭐⭐⭐ (≥ 90%)
---
👤 Sistema de Perfil y Progreso
El jugador elige un avatar (20 opciones), escribe su nombre y selecciona su grado escolar (5to–11vo).
El perfil se guarda en `localStorage` y se restaura automáticamente al recargar la página.
El progreso por mundo (puntaje, aciertos, tiempo) también se persiste en `localStorage`.
Claves de localStorage
Clave	Contenido
`mindscape\_profile\_v1`	Objeto `{ name, grade, avatar }`
`mindscape\_progress\_v1`	Objeto indexado por mundo `{ 0: {score, correctCount, levels, completedAt}, ... }`
`mindscape\_ranking\_v1`	Array de hasta 20 entradas ordenadas por puntaje total
---
🏆 Ranking
Se actualiza automáticamente al completar cada mundo.
Muestra: posición (🥇🥈🥉), avatar, nombre, grado, puntaje total acumulado, mundos completados y estrellas.
Los datos persisten en `localStorage` del navegador (por dispositivo).
Incluye botón para borrar el ranking completo.
---
🤖 ChatBot (JotForm)
La aplicación integra un asistente virtual embebido mediante JotForm Agent:
```html
<script src='https://cdn.jotfor.ms/agent/embedjs/019e611043bf72149389d5ba8f994f6f90b7/embed.js?autoOpenChatIn=1'></script>
```
Aparece como botón flotante en la esquina inferior derecha.
Sirve como asistente del estudiante: puede dar instrucciones, explicar conceptos, resolver dudas y guiar el uso de la app.
Se abre automáticamente al iniciar la sesión.
---
🎵 Música y Sonido
Elemento	Descripción
Música de fondo	Generada en tiempo real con Web Audio API. Estilo ambiental cyberpunk/tech. Escala pentatónica menor en Do (C4–G5).
Efectos de sonido	Correct (acorde mayor), Wrong (sawtooth descendente), Click, Alerta de tiempo, Fanfare de inicio.
Control música	Botón 🎵/🎶 — activa/desactiva la música de fondo.
Control sonido	Botón 🔊/🔇 — activa/desactiva todos los sonidos (incluida la música).
Sin archivos externos	100% sintetizado con Web Audio API. Sin copyright.
---
🎨 Diseño y Tecnologías
Tecnología	Uso
HTML5	Estructura de pantallas y componentes
CSS3	Variables CSS, animaciones, grid, diseño responsivo
JavaScript Vanilla	Lógica del juego, audio, canvas, localStorage
Web Audio API	Música generativa y efectos de sonido
Canvas API	Fondo animado con nodos y conexiones · Confetti
localStorage	Persistencia de perfil, progreso y ranking
Google Fonts	Orbitron (títulos) · Exo 2 (texto general)
JotForm	ChatBot asistente embebido
---
📱 Compatibilidad
Funciona directamente en el navegador, sin instalación ni servidor.
Compatible con Chrome, Firefox, Edge y Safari modernos.
Diseño responsivo: adaptado para pantallas de escritorio y móvil.
Para abrir: doble clic en `Mindscape\_v2.html` o arrastrar al navegador.
---
🚀 Cómo usar la aplicación
Abrir `Mindscape\_v2.html` en un navegador web moderno.
En la pantalla de perfil, elegir un avatar, escribir el nombre y seleccionar el grado.
Hacer clic en "⚡ Ingresar al Laboratorio".
En el Home, leer la sección "¿Cómo se usa?" y seleccionar un mundo.
Leer la lección del mundo antes de jugar (conceptos clave).
Presionar "⚡ Iniciar Misión" y responder las preguntas dentro del tiempo.
Al completar un mundo, el puntaje se guarda automáticamente en el Ranking.
Consultar el ranking con el botón 🏆 desde el Home o desde la pantalla de fin de mundo.
---
📁 Archivos del Proyecto
```
Mindscape/
├── Mindscape\_v2.html   ← Aplicación completa (archivo único autocontenido)
└── README.md           ← Este documento
```
> Toda la aplicación está contenida en un \*\*único archivo HTML\*\* autocontenido: CSS, JavaScript, datos del juego, audio y estilos están integrados sin dependencias externas descargables.
---
Mindscape — Laboratorio Digital de Aprendizaje · Santiago Miranda · Universidad del Magdalena · 2026
