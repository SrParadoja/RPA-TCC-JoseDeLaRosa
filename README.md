# RPA-TCC-JoseDeLaRosa
Automatización para la consulta de procesos en la Rama Judicial de Colombia.
# Solución RPA - Consulta Rama Judicial 
## Información del Candidato
* **Nombre:** Jose Alejandro De la Rosa David
* **Rol:** Tecnólogo en Análisis y Desarrollo de Software con Tarjeta COPNIA / Estudiante de Ingeniería de Sistemas de 5to Semestre

## Descripción del Proyecto
Automatización desatendida desarrollada en Power Automate Desktop que realiza la consulta de procesos judiciales a partir de un disparador de correo electrónico.

## Flujo de Trabajo
1. **Disparador:** Recupera correos no leídos desde `pruebatccrpa@gmail.com`(el cual es el correo de pruebas que se creo para tener el ambiente ideal de testeos) vía IMAP
2. **Procesamiento de Datos:** - Extrae el nombre del cuerpo del correo.
   - Limpia el texto eliminando firmas automáticas (ej. "Enviado desde Outlook") mediante división de texto por saltos de línea.
   - Aplica "Trim" para eliminar espacios en blanco accidentales.
3. **Navegación Web:** - Ingresa a la Rama Judicial, selecciona "Todos los procesos" y tipo de persona "Natural".
   - Utiliza selectores dinámicos (Ordinal: 5) para identificar siempre el sexto registro, garantizando robustez ante diferentes resultados de búsqueda.
4. **Descarga y Envío:** - Descarga el archivo .doc con nombre descriptivo.
   - Envía el resultado vía SMTP a `jhrey@tcc.com.co` con los detalles del proceso.

## Decisiones Técnicas Destacadas
- **Manejo de Errores:** Se implementó un bloque "On Block Error" para gestionar fallos en la carga de la página web.
- **Selectores Dinámicos:** Se evitó el uso de IDs estáticos o textos "quemados" para asegurar que el bot funcione con cualquier nombre consultado.
