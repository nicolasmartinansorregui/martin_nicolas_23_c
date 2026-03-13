# Simulador de Brecha Digital en Entornos Educativos VR

Este proyecto es una simulación inmersiva desarrollada en **WebXR** (A-Frame) que analiza el impacto de la conectividad y los protocolos de red en la teleducación. Permite experimentar en primera persona cómo las limitaciones técnicas de la red afectan a la recepción de contenidos académicos en entornos de Realidad Virtual.

## Propósito del Proyecto
El objetivo es doble:
1. **Concienciación Social:** Visibilizar la brecha digital y cómo la falta de una conexión estable excluye al alumno del flujo de aprendizaje.
2. **Demostración Técnica:** Simular comportamientos reales de redes de telecomunicaciones (latencia, jitter, pérdida de paquetes y adaptación de bitrate).

## Visión de Futuro: Telepresencia y Equidad
La idea central de este proyecto es que, en un futuro cercano, el acceso a la educación no dependa de la ubicación física. La **Realidad Virtual y la Telepresencia** permitirán que cualquier alumno asista a una clase magistral desde su hogar, eliminando barreras geográficas y reduciendo la huella de carbono del transporte.

Sin embargo, para que esta democratización del conocimiento sea real, es imperativo **subsanar la brecha digital**. Un sistema de teleeducación inmersivo solo es justo si:
1. **Infraestructura Universal:** El despliegue de redes 5G/6G llega a zonas rurales y desfavorecidas para evitar la exclusión.
2. **Calidad de Servicio (QoS):** Se garantiza una calidad mínima de recursos (audio y vídeo) para que la experiencia pedagógica sea efectiva para todos los usuarios, independientemente de su nivel socioeconómico.
3. **Acceso a Hardware:** El desarrollo de estándares abiertos (como WebXR, utilizado en este proyecto) permite el uso de recursos existentes (smartphones) sin necesidad de hardware propietario costoso.

Como ingenieros de telecomunicaciones, nuestra responsabilidad no es solo aumentar la velocidad de transmisión, sino asegurar que la tecnología sea un puente y no un muro.

## Tecnologías Utilizadas
- **A-Frame (WebXR):** Framework para la renderización de la escena 3D y el video 360 en el navegador.
- **FFmpeg:** Procesado y transcodificación de vídeo para generar los distintos niveles de calidad (Adaptive Bitrate).
- **Web Audio API:** Manipulación de señales de audio en tiempo real mediante nodos de filtrado digital.
- **JavaScript (Vanilla):** Lógica de control de estados y sincronización de medios.

## Implementación Técnica
El simulador incorpora tres pilares de las telecomunicaciones actuales:

### 1. Adaptive Bitrate Streaming (ABS)
Se han generado tres perfiles de calidad para el vídeo 360:
* **Alta (1080p):** Simula una conexión de fibra óptica/5G estable.
* **Media (360p):** Simula congestión moderada.
* **Baja (144p):** Simula condiciones de red críticas.
El sistema conmuta dinámicamente entre estos perfiles manteniendo la sincronización temporal.

### 2. Simulación de Protocolo UDP
A diferencia del streaming bajo demanda (TCP), esta simulación emula una clase en directo sobre **UDP**. Si se activa la "Brecha Digital", las caídas de red provocan una desincronización temporal: el alumno pierde fragmentos de la explicación que no podrá recuperar, simulando la pérdida de paquetes en tiempo real.

### 3. Procesado de Audio (Voz Robótica)
Mediante un filtro de paso bajo (`BiquadFilterNode`), el audio se degrada dinámicamente según el estado de la red, emulando la reducción del ancho de banda disponible para el códec de voz.

## Cómo Ejecutarlo
El proyecto está optimizado para su visualización en dispositivos móviles con carcasas de Realidad Virtual (VR).

1.  **Acceso:** Entre en el siguiente enlace: https://nicolasmartinansorregui.github.io/martin_nicolas_23_c/
2.  **Modo VR:** Pulse el icono de las gafas en la esquina inferior derecha.
3.  **Interacción (Gaze):** No se requieren mandos. La interacción se basa en la **mirada (fusing cursor)**. Mantenga la vista sobre los botones del panel de control para activarlos.
4.  **Ubicación de controles:** Los mandos de red y volumen se encuentran situados a los "pies" del usuario para no obstruir el campo visual de la clase.

## Estructura del Repositorio
```text
├── index.html              # Código fuente principal (Lógica y Escena)
├── README.md               # Documentación técnica
└── resources/              # Activos del proyecto
    ├── video/              # Versiones de vídeo (4K, 360p, 144p)
    └── audio/              # Pista de audio maestra
```

## Bibliografía y Referencias

## Bibliografía y Referencias

[1] A-Frame Documentation, "Cursor Component & Gaze-based Interaction," [En línea]. Disponible en: https://aframe.io/docs/1.4.0/components/cursor.html.

[2] MDN Web Docs, "BiquadFilterNode: Digital biquad filter implementation," Mozilla Foundation. [En línea]. Disponible en: https://developer.mozilla.org/en-US/docs/Web/API/BiquadFilterNode.

[3] R. Pantos y W. May, "HTTP Live Streaming: Variable Bit Rate (VBR) Encoding," RFC 8216, Section 6.2.2. [En línea]. Disponible en: https://datatracker.ietf.org/doc/html/rfc8216#section-6.2.2.

[4] GitHub Docs, "Configuring a publishing source for your GitHub Pages site," GitHub. [En línea]. Disponible en: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site.

[5] FFmpeg Documentation, "Video Rescaling and Pixel Format conversion," [En línea]. Disponible en: https://ffmpeg.org/ffmpeg-scaler.html.

[6] Lex Fridman, "MIT Sloan: Intro to Machine Learning (in 360/VR)" YouTube, [Video en línea]. Disponible en: https://www.youtube.com/watch?v=s3MuSOl1Rog&t=366s.
