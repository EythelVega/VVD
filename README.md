# VVD

# Proyecto: Gestión de Contactos (Simulada)

Este proyecto es un **frontend completamente funcional** que permite agregar, editar y eliminar contactos directamente desde la interfaz, simulando una base de datos en memoria. Es ideal para practicar **BDD, pruebas automatizadas y validaciones de datos**, ya que todos los elementos de la UI son accesibles y predecibles.

---

## Paleta de colores usada

| Elemento | Color |
|----------|-------|
| Fondo de la página | #f4f7f6 |
| Tarjetas (`card`) | #ffffff |
| Botón principal (Agregar) | #6c5ce7 |
| Botón editar | #fd79a8 |
| Botón eliminar | #e74c3c |
| Tabla encabezado | #0984e3 |
| Texto principal | #2d3436 |

---

## Funcionalidades

- Agregar contactos con **nombre, correo y teléfono**.
- **Editar y eliminar** contactos desde la tabla.
- **Validaciones básicas** de campos obligatorios.
- **Datos almacenados en memoria**, simulando base de datos.
- **Interfaz moderna** con Bootstrap y colores personalizados.
- Código preparado para pruebas **BDD o automatización UI**.

---

## Estructura del proyecto


- **index.html**: Contiene toda la lógica de la aplicación, estilos y estructura.
- **README.md**: Documentación detallada.

---

## Explicación detallada del código JavaScript

### 1. Variables globales



let contactos = []; // Array que almacena todos los contactos en memoria
let nextId = 1;     // Contador incremental para asignar ID único a cada contacto
function mostrarContactos() {
    const tbody = document.querySelector('#tablaContactos tbody');
    tbody.innerHTML = '';
    contactos.forEach(c => {
        tbody.innerHTML += 
        <tr>
            <td>${c.id}</td>
            <td>${c.nombre}</td>
            <td>${c.correo}</td>
            <td>${c.telefono}</td>
            <td>
                <button class="btn btn-sm btn-warning" onclick="editarContacto(${c.id})">Editar</button>
                <button class="btn btn-sm btn-danger" onclick="eliminarContacto(${c.id})">Eliminar</button>
            </td>
        </tr>`;
    });
}
document.getElementById('contactoForm').addEventListener('submit', (e) => {
    e.preventDefault();
    const nombre = document.getElementById('nombre').value.trim();
    const correo = document.getElementById('correo').value.trim();
    const telefono = document.getElementById('telefono').value.trim();

  if(!nombre || !correo || !telefono) return alert('Todos los campos son obligatorios');

  contactos.push({ id: nextId++, nombre, correo, telefono });
    document.getElementById('contactoForm').reset();
    mostrarContactos();
});
function eliminarContacto(id) {
    contactos = contactos.filter(c => c.id !== id);
    mostrarContactos();
}

function editarContacto(id) {
    const c = contactos.find(c => c.id === id);
    const nombre = prompt("Editar nombre:", c.nombre);
    const correo = prompt("Editar correo:", c.correo);
    const telefono = prompt("Editar teléfono:", c.telefono);
    if(nombre && correo && telefono){
        c.nombre = nombre;
        c.correo = correo;
        c.telefono = telefono;
        mostrarContactos();
    }
}


mostrarContactos();

