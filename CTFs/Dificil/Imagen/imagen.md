# Imagen Misteriosa

## 🕵️ Descripción: Un analista de seguridad encuentra una imagen sospechosa en el equipo de un usuario comprometido. Se sospecha que el atacante ha ocultado información dentro de ella. Tu misión es analizar la imagen y extraer la información oculta.

📂 Material proporcionado: Un archivo .png o .jpg (imagen con datos ocultos).

**🔍 Pistas:**

1. Usa strings para ver si hay texto oculto en la imagen.
2. Prueba con exiftool para ver metadatos sospechosos.
3. Si hay información binaria extraña, usa steghide o zsteg para analizarla.
4. Si la imagen contiene texto visual, aplica OCR (tesseract).