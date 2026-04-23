# Guía de Uso - MarkItDown

**MarkItDown** es una herramienta potente para convertir diversos tipos de documentos a formato Markdown de manera rápida y eficiente.

Aquesta guía interactiva te proporciona todo lo que necesitas para instalar, configurar y utilizar MarkItDown en tus proyectos.

---

## 📋 Contenidos

- [Instalación y Requisitos](#instalación-y-requisitos)
- [Línea de Comandos (CLI)](#línea-de-comandos-cli)
- [API de Python](#api-de-python)
- [Uso Avanzado y Docker](#uso-avanzado-y-docker)
- [Generador de Código](#generador-de-código)

---

## ⚙️ Instalación y Requisitos

### Requisitos Previos
- **Python 3.10** o superior

### Instalación Completa (Recomendada)

Instala MarkItDown con todas sus dependencias opcionales para acceso a todos los formatos:

```bash
pip install 'markitdown[all]'
```

### Instalación Modular

Si prefieres un entorno más ligero, instala solo las dependencias que necesitas:

```bash
pip install 'markitdown[pdf,docx,pptx]'
```

**Formatos soportados:**
- PDF
- Word (.docx)
- PowerPoint (.pptx)
- Hojas de Cálculo (.xlsx)
- Imágenes (.jpg, .png, etc.)
- Archivos comprimidos (.zip)
- Audio (.mp3 y otros formatos)

---

## 💻 Línea de Comandos (CLI)

### Conversión Básica

Convierte un archivo y especifica el nombre del archivo de salida usando la bandera `-o`:

```bash
markitdown documento.pdf -o resultado.md
```

### Uso con Tuberías (Pipes)

Puedes pasar el contenido de un archivo a través de la entrada estándar (stdin):

```bash
cat documento.pdf | markitdown > resultado.md
```

**Ventajas del CLI:**
- Integrarse fácilmente en scripts
- Procesar múltiples documentos en lotes
- Combinar con otras herramientas de línea de comandos

---

## 🐍 API de Python

Utiliza MarkItDown directamente en tus aplicaciones Python para mayor control y flexibilidad.

### Conversión Básica en Python

```python
from markitdown import MarkItDown

md = MarkItDown()
result = md.convert("documento.pdf")
print(result.text_content)
```

### Con Cliente LLM (OpenAI)

Integra análisis de inteligencia artificial para mejor extracción de contenido visual:

```python
from markitdown import MarkItDown
from openai import OpenAI

client = OpenAI()
md = MarkItDown(
    llm_client=client,
    llm_model="gpt-4o"
)
result = md.convert("documento_con_imagenes.pdf")
print(result.text_content)
```

### Con Plugins Habilitados

Activa extensiones de terceros para funcionalidades adicionales como OCR avanzado:

```python
from markitdown import MarkItDown

md = MarkItDown(enable_plugins=True)
result = md.convert("documento.pdf")
print(result.text_content)
```

---

## 🚀 Uso Avanzado y Docker

### Azure Document Intelligence

Utiliza la API de Azure Document Intelligence para extraer texto con mayor precisión y manejo de estructura en documentos complejos:

```python
from markitdown import MarkItDown

md = MarkItDown(docintel_endpoint="<TU_ENDPOINT_AZURE>")
result = md.convert("documento_complejo.pdf")
print(result.text_content)
```

**Ventajas:**
- Mayor precisión en OCR
- Mejor reconocimiento de tablas y estructuras
- Soporte para documentos en múltiples idiomas

### Uso mediante Docker

Ejecuta MarkItDown en un contenedor aislado, evitando conflictos de dependencias y simplificando la distribución:

```bash
docker run --rm -i markitdown:latest < documento.pdf > resultado.md
```

**Beneficios de Docker:**
- Entorno consistente en cualquier máquina
- Sin conflictos con dependencias del sistema
- Fácil distribución en equipos
- Escalabilidad en aplicaciones cloud

---

## 🛠️ Generador de Código

#### Configuración Interactiva

Accede a la herramienta generadora para configurar tus opciones:

1. **Selecciona el formato** del archivo que deseas convertir
2. **Habilita opciones avanzadas:**
   - **LLM (OpenAI)**: Permite analizar y describir imágenes incrustadas
   - **Plugins**: Activa extensiones de terceros (como OCR avanzado)
3. **Copia el código** generado automáticamente

El generador te proporcionará código Python listo para usar inmediatamente.

---

## 📚 Ejemplos Comunes

### Convertir un PDF a Markdown

```bash
markitdown libro.pdf -o libro.md
```

### Procesar múltiples documentos

```bash
for file in *.pdf; do
  markitdown "$file" -o "${file%.pdf}.md"
done
```

### Integración en una aplicación web

```python
from markitdown import MarkItDown
from flask import Flask, request

app = Flask(__name__)
md = MarkItDown()

@app.route('/convert', methods=['POST'])
def convert_document():
    file = request.files['document']
    result = md.convert(file)
    return result.text_content
```

---

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Por favor, sigue las directrices del repositorio oficial de MarkItDown.

---

## 📄 Licencia

Consulta la licencia del proyecto MarkItDown para más detalles.

---

## 🔗 Enlaces útiles

- [Repositorio oficial de MarkItDown](https://github.com/microsoft/markitdown)
- [Documentación de Python](https://docs.python.org)
- [Azure Document Intelligence](https://learn.microsoft.com/es-es/azure/ai-services/document-intelligence/)
- [Docker Documentation](https://docs.docker.com)

---

**Última actualización:** Abril 2026