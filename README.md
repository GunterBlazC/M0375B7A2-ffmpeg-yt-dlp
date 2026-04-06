# M0375B7A2-ffmpeg-yt-dlp
## Parte teorica
### 1. Protocolos: RTMP, HLS, RTSP y SRT

RTMP es un protocolo usado sobre todo para enviar vídeo y audio en directo desde un programa de emisión hacia un servidor. Tiene baja latencia, pero hoy se usa menos para la reproducción final en navegador. 

HLS divide el vídeo en fragmentos pequeños y los envía por HTTP. Su mayor ventaja es la gran compatibilidad con móviles, navegadores y televisores, aunque suele tener más latencia que otros protocolos.

RTSP se usa mucho en cámaras IP y videovigilancia. Permite controlar la transmisión y suele tener baja latencia, pero no es tan cómodo para páginas web normales. 

SRT es un protocolo moderno pensado para enviar vídeo con baja latencia y buena seguridad incluso cuando la red no es estable. Es muy útil en entornos profesionales. 

Resumen rápido: HLS destaca por compatibilidad, RTSP por cámaras, RTMP por emisión en directo y SRT por seguridad y estabilidad en redes complicadas. 

### 2. FFMPEG

1. ¿Qué es FFmpeg? ¿Para qué se utiliza?
FFmpeg es una herramienta de línea de comandos para trabajar con archivos de audio y vídeo. Se utiliza para convertir formatos, cambiar códecs, recortar vídeos, extraer audio, aplicar filtros y hacer tareas de procesamiento multimedia en general.

2. ¿Cuál es su página oficial y dónde está la documentación?
Su página oficial es la de FFmpeg. En esa misma web se puede encontrar la documentación técnica, sobre todo en los manuales de ffmpeg, ffmpeg-all, ffmpeg-formats y ffmpeg-codecs.

3. ¿Cómo se instala en Windows, macOS y Linux? ¿Qué hay que tener en cuenta?
En Linux normalmente se instala con el gestor de paquetes de la distribución. En Windows y macOS se suele descargar una versión ya compilada o usar un gestor de paquetes. Hay que tener en cuenta que no todas las compilaciones incluyen los mismos códecs o librerías, así que algunas funciones pueden cambiar según la versión instalada.

4. ¿Cuáles son sus características fundamentales?
Sus capacidades más destacadas son: convertir formatos, soportar muchos códecs, copiar pistas sin recodificar, aplicar filtros de audio y vídeo, y trabajar tanto con archivos locales como con flujos de red o streaming.

5. ¿Se puede cambiar de contenedor sin recodificar?
Sí. Eso consiste en cambiar solo el contenedor, por ejemplo de .mp4 a .mkv, sin modificar ni el vídeo ni el audio. Esta operación se hace copiando los streams, por ejemplo con ffmpeg -i video.mp4 -c copy video.mkv. La ventaja es que el proceso es rápido y no pierde calidad.

6. ¿Qué características tienen MP4 y MKV? ¿Cuándo conviene usar cada uno?
MP4 destaca por su gran compatibilidad con móviles, navegadores y televisores. MKV es más flexible y suele ir mejor cuando el archivo tiene varias pistas de audio, subtítulos o configuraciones más completas. Yo usaría MP4 para compatibilidad general y MKV cuando necesito más flexibilidad.

7. En el comando ffmpeg -i metal-violin-f616.mp4 -vcodec libx264 metal-violin-f616.mkv, ¿solo cambia el contenedor?
No. En ese comando también se está recodificando el vídeo, porque -vcodec libx264 obliga a codificarlo en H.264. Si solo se quisiera cambiar el contenedor, habría que usar -c copy.

8. ¿Qué características tiene H.264? ¿Qué diferencias hay con H.265?
H.264 es un códec muy usado porque ofrece buena calidad y muchísima compatibilidad. H.265 comprime mejor, así que puede mantener una calidad parecida ocupando menos espacio, pero suele necesitar más potencia y no siempre es tan compatible como H.264. Por eso H.264 sigue siendo la opción más segura cuando quieres que funcione en casi todo.

9. Si no se indica nada sobre el audio, ¿qué hace FFmpeg?
Si en el comando solo se especifica el códec de vídeo, FFmpeg no está copiando el audio de forma explícita. Lo normal es que procese la pista de audio según el formato de salida y sus valores por defecto. Si quieres asegurarte de que el audio se mantenga igual, lo correcto es poner -c:a copy. Esta última parte es una inferencia práctica basada en cómo FFmpeg documenta la copia explícita de streams.

### 3. YT-DLP

10. ¿Qué es yt-dlp y en qué se diferencia de youtube-dl?
yt-dlp es una herramienta de línea de comandos para descargar audio y vídeo de muchas páginas web. Se diferencia de youtube-dl en que es un fork más actualizado, con más funciones, más correcciones y mantenimiento más activo.

11. ¿Cómo se instala yt-dlp y qué hay que tener en cuenta?
Se puede instalar usando binarios oficiales o gestores de paquetes, según el sistema operativo. Lo más importante es tener presente que FFmpeg es muy recomendable, porque ayuda a unir vídeo y audio, convertir archivos y aprovechar mejor muchas funciones de yt-dlp.

12. ¿Cuáles son sus características fundamentales?
Sus funciones principales son: descargar vídeo y audio, elegir formato y calidad, bajar subtítulos, guardar metadatos e integrarse con FFmpeg. También permite automatizar descargas y elegir pistas concretas.

13. Comparativa entre AV1, VP9 y H.264
AV1 ofrece muy buena compresión y puede mantener alta calidad con menos tamaño, aunque suele ser más exigente para codificar o reproducir. VP9 también comprime mejor que H.264 y ha sido muy usado en la web. H.264 sigue siendo el más compatible de los tres, por eso todavía es el más seguro cuando quieres que funcione en casi cualquier dispositivo. En resumen: AV1 para mejor compresión, VP9 como opción intermedia y H.264 para máxima compatibilidad.

### ALTERNATIVAS

Alternativas a FFmpeg
Una alternativa bastante conocida es HandBrake. Su ventaja es que tiene interfaz gráfica y resulta más fácil para usuarios que no quieren usar comandos, pero a cambio ofrece menos flexibilidad que FFmpeg. Otra opción es VLC, que también puede convertir algunos formatos y es muy fácil de usar, aunque no está tan orientado a tareas avanzadas de procesamiento.

Alternativas a yt-dlp
La alternativa más directa es youtube-dl, que fue el proyecto original. Su ventaja es que fue muy popular, pero yt-dlp suele estar más actualizado y mejor mantenido. También existen programas con interfaz gráfica basados en estas herramientas, que son más cómodos para empezar, aunque normalmente dan menos control que usar yt-dlp en terminal.

## Parte practica 

<img width="517" height="27" alt="image" src="https://github.com/user-attachments/assets/c49ef8f7-7c70-4dd3-9820-1c0840d55de7" />
<img width="728" height="409" alt="image" src="https://github.com/user-attachments/assets/95c73861-82b2-424c-b829-aa5e9c820a4d" />
<img width="1150" height="60" alt="image" src="https://github.com/user-attachments/assets/274b059d-24aa-45fc-9faf-50ac6ccf15b1" />
<img width="1141" height="178" alt="image" src="https://github.com/user-attachments/assets/d504fdcd-484c-4598-b1e6-adda229708f7" />
<img width="1155" height="604" alt="image" src="https://github.com/user-attachments/assets/22b7f4ab-c8df-44b8-a15c-08231c6de1eb" />


















