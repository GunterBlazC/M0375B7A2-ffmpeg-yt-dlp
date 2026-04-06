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

Primero instalé **FFmpeg** en Ubuntu con el gestor de paquetes. Cuando terminó la instalación, comprobé que la herramienta ya estaba disponible y lista para usarse en la terminal.

<img width="517" height="27" alt="image" src="https://github.com/user-attachments/assets/c49ef8f7-7c70-4dd3-9820-1c0840d55de7" />

Después intenté consultar la información de un vídeo con `ffmpeg -i`, pero al principio tuve un pequeño fallo porque no estaba usando bien el nombre o la ruta del archivo. Esta prueba me sirvió para darme cuenta de que antes de trabajar con FFmpeg tenía que asegurarme bien de dónde estaba guardado el vídeo.

<img width="728" height="409" alt="image" src="https://github.com/user-attachments/assets/95c73861-82b2-424c-b829-aa5e9c820a4d" />

Luego instalé **yt-dlp** descargándolo desde GitHub y dándole permisos de ejecución para poder usarlo desde cualquier carpeta del sistema.

<img width="1150" height="60" alt="image" src="https://github.com/user-attachments/assets/274b059d-24aa-45fc-9faf-50ac6ccf15b1" />

Una vez instalado, consulté los formatos disponibles de un vídeo de YouTube. Así pude ver las distintas resoluciones, los formatos de audio y vídeo y los identificadores de cada opción antes de descargar nada.

<img width="1141" height="178" alt="image" src="https://github.com/user-attachments/assets/d504fdcd-484c-4598-b1e6-adda229708f7" />

Después descargué uno de los formatos disponibles del vídeo y comprobé que el archivo se había bajado correctamente. Este mismo vídeo fue el que utilicé luego para hacer toda la parte práctica con FFmpeg.

<img width="1155" height="604" alt="image" src="https://github.com/user-attachments/assets/22b7f4ab-c8df-44b8-a15c-08231c6de1eb" />

Con el vídeo ya guardado en el sistema, volví a usar `ffmpeg -i` para consultar su información técnica. Ahí ya pude ver la duración, el bitrate, la resolución y los códecs del archivo descargado.

<img width="1157" height="773" alt="image" src="https://github.com/user-attachments/assets/09e66429-194d-4fa1-a739-7c3233050897" />

A partir de ahí empecé con las conversiones. Primero pasé el vídeo original a formato **MKV con H.264** y luego repetí el mismo proceso usando **H.265**. Después comparé los tamaños para ver la diferencia entre los dos resultados.

<img width="892" height="256" alt="image" src="https://github.com/user-attachments/assets/d82cc684-d86e-420a-a0c9-89f9aa3657bd" />

Después hice una prueba cambiando solo el **audio** del archivo. Para eso mantuve el vídeo sin modificar y fui probando distintos códecs, empezando por **MP3**.

<img width="1156" height="513" alt="image" src="https://github.com/user-attachments/assets/f9361fb3-e4e8-4881-b242-ad8e8eb76a86" />

Luego comprobé el resultado generado con ese cambio de audio para ver que el archivo nuevo se había creado correctamente.

<img width="840" height="150" alt="image" src="https://github.com/user-attachments/assets/797a8366-e677-4764-bc2e-4d69efc19f4d" />

Después repetí la misma idea usando **AAC**, manteniendo igual la parte de vídeo y cambiando solamente la pista de audio.

<img width="1156" height="738" alt="image" src="https://github.com/user-attachments/assets/2d1f72ca-eabc-41f2-907f-4943f2b8f19f" />

Volví a revisar los archivos generados para comprobar que también se había creado correctamente esta versión.

<img width="851" height="161" alt="image" src="https://github.com/user-attachments/assets/916a1bc4-cf1d-4e65-9bff-b13b0693e538" />

La última prueba de esta parte fue cambiar el audio a **Vorbis**, otra vez sin tocar el vídeo. Así pude comparar varios códecs de audio usando el mismo archivo de partida.

<img width="1153" height="723" alt="image" src="https://github.com/user-attachments/assets/ff34e439-3d30-4c8f-b255-9504f7f84026" />

Después comparé de nuevo los resultados para ver cómo habían quedado los distintos archivos y qué diferencias había en el tamaño final según el audio usado.

<img width="850" height="179" alt="image" src="https://github.com/user-attachments/assets/11505e39-ac31-4e35-9e2c-b73f65999cb7" />

Más adelante hice una prueba modificando manualmente el **bitrate** del vídeo y del audio. En este caso el cambio fue muy visible, porque el archivo final pasó a ocupar bastante más que el original.

<img width="1159" height="703" alt="image" src="https://github.com/user-attachments/assets/ba10ba20-9de5-4003-b3bb-cd73b0a994be" />

Por último, extraje solo el **audio** del vídeo y también recorté un fragmento corto para generar un clip independiente. Con estas dos pruebas cerré la práctica usando funciones básicas pero muy útiles de FFmpeg.

<img width="843" height="192" alt="image" src="https://github.com/user-attachments/assets/f16c3d56-0851-4280-bd38-b3d8f82d306d" />

En el resultado final ya se pueden ver juntos todos los archivos que fui generando durante la práctica: las conversiones con H.264 y H.265, las versiones con distintos audios, el archivo con bitrate modificado, el audio extraído y el clip recortado.

<img width="1152" height="498" alt="image" src="https://github.com/user-attachments/assets/4d95fb4a-e029-4385-8156-6b7289bf8ece" />
