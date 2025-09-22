# VVD

# Proyecto: Gestión de Contactos (Simulada)

Este proyecto es un **frontend completamente funcional** que permite agregar, editar y eliminar contactos directamente desde la interfaz, simulando una base de datos en memoria.

---

## Paleta de colores usada

| Elemento | Color |
|----------|-------|
| Fondo de la página | #f4f7f6 |
| Tarjetas (`card`) | #ffffff |
| Botón principal | #6c5ce7 |
| Botón editar | #fd79a8 |
| Tabla encabezado | #0984e3 |
| Texto principal | #2d3436 |

---

## Funcionalidades

- Agregar contactos con nombre, correo y teléfono.
- Editar y eliminar contactos desde la tabla.
- Validaciones básicas de campos obligatorios.
- Datos almacenados en memoria simulando base de datos.
- Interfaz moderna con Bootstrap y colores personalizados.

---

## Explicación del código JavaScript

**Variables principales:**

```javascript
let contactos = []; // Array que guarda los contactos
let nextId = 1;     // Contador de ID único


