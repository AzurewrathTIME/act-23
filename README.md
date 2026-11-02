# 🏫 Sistema Escolar - Formularios HTML y Métodos HTTP

Implementación de un formulario web para capturar datos de alumnos y análisis del envío de información al servidor usando los métodos `GET` y `POST`.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat&logo=c%2B%2B&logoColor=white)
![HTTP](https://img.shields.io/badge/HTTP-GET%20%7C%20POST-blue)
![Status](https://img.shields.io/badge/status-completado-success)

---

## 📌 Descripción

En esta actividad se agregó una nueva página (`registro.html`) con un formulario funcional para registrar alumnos. El objetivo principal es **comprender cómo viaja la información** desde el navegador hacia el servidor utilizando los métodos HTTP `GET` y `POST`, observando el tráfico mediante las herramientas de desarrollador (DevTools).

---

## ✨ Características del Formulario

- 📝 **Campos validados:** Nombre, Edad (con límites) y Matrícula.
- 🔒 **Validación nativa:** Uso de `required`, `type="number"`, `min` y `max`.
- 🕵️ **Campo oculto:** Incluye un `<input type="hidden">` para enviar datos de origen sin que el usuario los vea (Mini-reto).
- 🔗 **Rutas absolutas:** Enlaces y recursos apuntan a la raíz del servidor (ej. `/styless.css`).
- ⚙️ **Method configurable:** Preparado para probar tanto `GET` como `POST`.

---

## 🛠️ Tecnologías

| Tecnología | Uso |
|------------|-----|
| HTML5 | Estructura del formulario y validaciones nativas |
| CSS3 | Estilos básicos para centrar el formulario |
| C++ | Servidor web encargado de recibir la petición (Actividad 22) |
| DevTools (F12) | Inspección del tráfico de red (Network / Payload) |

---

## 📁 Estructura del proyecto

```text
Sistema-Escolar/
├── servidor.cpp       <-- Servidor web en C++
├── README.md
└── Public/
    ├── index.html
    ├── registro.html  <-- NUEVO: Formulario de la Actividad 23
    ├── styless.css
    ├── app.js
    └── img/
        ├── mi.png
        └── fondo.gif
```

---

## 🚀 Cómo probarlo

1. Asegúrate de tener tu servidor C++ compilado y corriendo:
   ```bash
   ./servidor
   ```
2. Abre el navegador y visita:
   ```text
   http://localhost:8080/registro.html
   ```
3. Llena los datos del formulario y presiona **Enviar**.
4. Como el servidor de C++ aún no procesa la ruta `/registrar`, verás la página **404** que programamos en la actividad anterior.

---

## 🧠 Conceptos aplicados

### GET vs POST

| Aspecto | GET | POST |
|---------|-----|------|
| **Ubicación de datos** | En la URL (Query String) | En el cuerpo (Body) |
| **Visibilidad** | Visible en la barra de direcciones | Oculto en la URL |
| **Uso típico** | Búsquedas, filtros | Envío de datos, login, modificar estado |
| **Límite de tamaño** | Limitado por la URL (~2000 chars) | Sin límite práctico |

### URL Encoding
Los formularios codifican los caracteres especiales automáticamente.
- Espacio → `+` o `%20`
- Tilde (`ó`) → `%C3%B3`
- Ejemplo: `Ana López` viaja como `Ana+L%C3%B3pez`.

### Herramientas del Desarrollador (DevTools)
- Pestaña **Network** (Red).
- Pestaña **Payload** (Carga útil) para ver qué datos se enviaron.
- Pestaña **Headers** (Cabeceras) para ver el `Content-Type` (ej. `application/x-www-form-urlencoded`).

---

## 🧪 Prueba de Observación (F12)

Para comprobar la diferencia visual entre ambos métodos:

1. Abre DevTools (`F12`) → Pestaña **Network**.
2. Envía el formulario.
3. Haz clic en la petición `registrar` de la lista.
4. **Si usaste POST:** Revisa la pestaña *Payload* o *Request*. Ahí verás los datos.
   ```text
   nombre=Ana+L%C3%B3pez&edad=20&matricula=A001&origen=web
   ```
5. **Si usaste GET:** Revisa la barra de direcciones de tu navegador. Los datos estarán expuestos ahí:
   ```text
   http://localhost:8080/registrar?nombre=Ana+L%C3%B3pez&edad=20&matricula=A001&origen=web
   ```

---

## 📄 Licencia

MIT License
