RPA-TCC-JoseDeLaRosa
Automatización para la consulta de procesos en la Rama Judicial de Colombia.

Información del Candidato
Nombre: Jose Alejandro De la Rosa David
Rol: Tecnólogo en Análisis y Desarrollo de Software con Tarjeta COPNIA / Estudiante de Ingeniería de Sistemas de 5to Semestre
Herramienta: Power Automate Desktop (Versión usada 11.2603.154.0)
1. Elección de la Herramienta
Se seleccionó Power Automate Desktop por dos razones principales:

Familiaridad técnica: Su lógica de manejo de flujos y el sistema de grabación resulta familiar a herramientas como Selenium, con las cuales he trabajado anteriormente, facilitando la curva de aprendizaje y la implementación.
Integración y Robustez: Ofrece una capacidad nativa de integración con el ecosistema Windows y alta robustez en la automatización de UI Web. Permite un manejo eficiente de selectores dinámicos y una integración simplificada con protocolos de correo (IMAP/SMTP) sin requerir licenciamientos complejos para esta prueba técnica.
2. Resumen de la Solución
El bot realiza una consulta desatendida de procesos judiciales siguiendo una lógica de procesamiento de datos y navegación web automatizada.

Diagrama del Flujo (ASCII)
[INICIO]
   |
[LECTURA CORREO] ----> (Extrae cuerpo del mensaje)
   |
[LIMPIEZA DATOS] ----> (Separa nombre de firmas de Outlook/Android)
   |
[NAVEGACIÓN WEB] ----> (Portal Rama Judicial: Todos los Procesos)
   |
[BÚSQUEDA] ----------> (Ingresa Nombre y Tipo Persona: Natural)
   |
[EXTRACCIÓN] --------> (Identifica 6to registro vía Selector Ordinal)
   |
[DESCARGA] ----------> (Guarda archivo .doc en C:\RPA)
   |
[ENVÍO CORREO] ------> (Remite detalle a jhrey@tcc.com.co)
   |
[FIN]

---

3. Configuración y Ejecución
Requisitos Previos
Navegador: Preferiblemente Google Chrome.

Software: Power Automate Desktop instalado y extensión de navegador habilitada.

Credenciales: Cuenta Gmail con "Contraseña de aplicación" activada para acceso IMAP/SMTP (Se usó pruebatccrpa@gmail.com).

Sistema: Existencia de la carpeta C:\RPA para el almacenamiento temporal de archivos.

Pasos para Importar
Crear un nuevo flujo en Power Automate Desktop.

Copiar el contenido del archivo Flujo_RPA.txt de este repositorio.

Pegar directamente en el lienzo de diseño del nuevo flujo.

Variables de Configuración
%EmailOrigen%: Correo que monitorea el bot (pruebatccrpa@gmail.com).

%EmailDestino%: Destinatario del informe (jhrey@tcc.com.co).

4. Decisiones Técnicas Clave
Estrategia 6to Resultado: Se omitió el uso de IDs estáticos. Se configuró un selector dinámico usando el atributo Ordinal: 5 (índice base 0) para garantizar que el bot siempre capture el sexto registro independientemente de la radicación.

Extracción del Nombre: Se implementó una división de texto (Split) por "Nueva Línea" para tomar solo el primer renglón del cuerpo del correo, ignorando firmas automáticas de dispositivos móviles y optimizando la búsqueda.

Descarga del Archivo: Se configuró una espera de UI para asegurar que el botón "Descargar DOC" esté totalmente disponible y cargado antes de la interacción, evitando errores por latencia de la página.

5. Limitaciones y Trabajo Pendiente
Limitación Actual: El bot procesa solo el primer correo no leído por ejecución.

Mejora Futura: Implementar un bucle (Loop) para procesar múltiples correos en una sola ejecución y agregar un sistema de logs en base de datos para trazabilidad histórica.

Seguridad: Actualmente la contraseña de aplicación está cifrada en el flujo; en una fase productiva se recomienda el uso de Azure Key Vault para el manejo seguro de credenciales.

Contacto
Jose Alejandro De la Rosa David

📧 josealejandro98@hotmail.com

📞 300 701 1165