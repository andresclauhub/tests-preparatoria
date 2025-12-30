# 📝 Configuración del Test con Registro de Respuestas

Este test guarda las respuestas de los estudiantes en un archivo JSON para que puedas revisarlas después.

## 🚀 Pasos para Configurar

### Paso 1: Crear cuenta en JSONBin.io (Gratis)

1. Ve a **https://jsonbin.io**
2. Haz clic en **"Sign Up"** (Registrarse)
3. Crea una cuenta con tu email

### Paso 2: Crear el Bin (almacenamiento JSON)

1. Una vez que inicies sesión, haz clic en **"Create a Bin"**
2. En el contenido del bin, escribe exactamente esto:

```json
{"respuestas": []}
```

3. Haz clic en **"Create"**
4. **Copia el BIN ID** que aparece en la URL (es algo como: `677296c6acd3cb34a8b4eb5f`)

### Paso 3: Crear tu API Key

1. Haz clic en tu nombre de usuario (arriba a la derecha)
2. Ve a **"API Keys"**
3. Haz clic en **"Create Access Key"**
4. Marca **Read** y **Update** (lectura y actualización)
5. Haz clic en **"Save"**
6. **Copia el API Key** (es algo como: `$2a$10$xxxxxxxxxxxxx`)

### Paso 4: Configurar el archivo HTML

1. Abre el archivo `test_unidad1_con_registro.html`
2. Busca estas líneas al principio del JavaScript:

```javascript
const JSONBIN_BIN_ID = 'TU_BIN_ID_AQUI';
const JSONBIN_API_KEY = 'TU_API_KEY_AQUI';
```

3. Reemplaza con tus valores:

```javascript
const JSONBIN_BIN_ID = '677296c6acd3cb34a8b4eb5f'; // Tu BIN ID
const JSONBIN_API_KEY = '$2a$10$xxxxxx'; // Tu API Key
```

4. Guarda el archivo

### Paso 5: Subir a GitHub Pages

```bash
cd /Users/andresaguilar/Escuela/primer_semestre/github_tests
cp ../Archivos/3_Tests_Online/test_unidad1_con_registro.html index.html
git add .
git commit -m "Test con registro de respuestas"
git push
```

---

## 📊 Cómo Ver las Respuestas de tus Estudiantes

### Opción 1: Ver en JSONBin.io

1. Ve a https://jsonbin.io
2. Inicia sesión
3. Haz clic en tu Bin
4. Verás todas las respuestas en formato JSON

### Opción 2: Descargar el JSON

1. Ve a tu Bin en JSONBin.io
2. Haz clic en **"Download"** o copia el JSON
3. Guárdalo como `respuestas.json`

### Opción 3: Usar la API

Puedes obtener las respuestas con este comando en terminal:

```bash
curl -X GET https://api.jsonbin.io/v3/b/TU_BIN_ID/latest \
  -H "X-Access-Key: TU_API_KEY" \
  | python3 -m json.tool > respuestas.json
```

---

## 📋 Formato de las Respuestas

Cada respuesta se guarda con esta estructura:

```json
{
  "nombre": "Juan Pérez García",
  "materia": "ciencias_sociales",
  "materiaTitle": "Ciencias Sociales I",
  "calificacion": 80,
  "correctas": 8,
  "totalPreguntas": 10,
  "fecha": "30/12/2025",
  "hora": "17:30:45",
  "timestamp": "2025-12-30T23:30:45.123Z",
  "respuestas": [
    {
      "pregunta": "¿Qué estudian las ciencias sociales?",
      "respuestaEstudiante": "Al ser humano en sociedad",
      "respuestaCorrecta": "Al ser humano en sociedad",
      "correcta": true
    },
    // ... más preguntas
  ]
}
```

---

## 🔒 Características de Seguridad

- ✅ **Solo una vez**: Cada estudiante solo puede contestar una vez por materia
- ✅ **Registro completo**: Se guarda nombre, fecha, hora, calificación y cada respuesta
- ✅ **Verificación por nombre**: Si un estudiante intenta contestar de nuevo, el sistema se lo impide
- ✅ **Respaldo local**: Si hay problemas de conexión, las respuestas se guardan localmente

---

## ⚠️ Notas Importantes

1. **El límite gratuito de JSONBin.io** es de 10,000 solicitudes por mes, suficiente para una clase
2. **No compartas tu API Key** con los estudiantes
3. **Haz respaldos** del JSON periódicamente
4. Los estudiantes son identificados por nombre (deben escribirlo igual cada vez)

---

## 🛠️ Solución de Problemas

### "Error al guardar respuestas"
- Verifica que tu BIN ID y API Key sean correctos
- Verifica tu conexión a internet
- Las respuestas se guardan localmente como respaldo

### "Un estudiante dice que ya contestó pero no aparece"
- Puede que haya escrito su nombre diferente
- Revisa el JSON para ver cómo registró su nombre

### Regenerar el test sin perder respuestas
- Las respuestas están en JSONBin.io, no en el HTML
- Puedes actualizar el HTML sin perder datos

---

*Última actualización: Diciembre 2025*

