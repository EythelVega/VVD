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


2. Función mostrarContactos()
function mostrarContactos() {
    const tbody = document.querySelector('#tablaContactos tbody');
    tbody.innerHTML = '';
    contactos.forEach(c => {
        tbody.innerHTML += `
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


Descripción:

Actualiza dinámicamente la tabla HTML con los contactos actuales.

Limpia el <tbody> antes de renderizar los contactos (tbody.innerHTML = '').

Crea filas para cada contacto con sus datos y botones de editar y eliminar.

3. Funcionalidad de agregar contacto
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


Descripción:

Escucha el evento submit del formulario y evita que la página se recargue (e.preventDefault()).

Obtiene los valores de los campos y elimina espacios al inicio y final (trim()).

Valida que todos los campos tengan contenido, mostrando alerta si falta alguno.

Agrega el contacto al array contactos con un ID único.

Reinicia el formulario y actualiza la tabla llamando mostrarContactos().

4. Función eliminarContacto(id)
function eliminarContacto(id) {
    contactos = contactos.filter(c => c.id !== id);
    mostrarContactos();
}


Descripción:

Recibe un id de contacto y elimina ese contacto del array contactos.

Filtra todos los contactos cuyo ID no coincida con el ID recibido.

Llama mostrarContactos() para actualizar la tabla inmediatamente.

5. Función editarContacto(id)
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


Descripción:

Encuentra el contacto por id usando find().

Solicita al usuario nuevos valores mediante prompt().

Si todos los campos tienen datos, actualiza el contacto.

Llama a mostrarContactos() para reflejar los cambios en la tabla.

6. Inicialización de la tabla
mostrarContactos();


Descripción:

Al cargar la página, muestra la tabla vacía, lista para agregar contactos.

Permite que la UI esté visible aunque no haya contactos agregados.

Buenas prácticas implementadas

Separación de responsabilidades: Cada función tiene una tarea clara: mostrar, agregar, editar o eliminar contactos.

Validación de datos: Se asegura que no se agreguen campos vacíos.

Interfaz limpia y moderna: Uso de Bootstrap y paleta de colores personalizada.

Preparado para pruebas BDD o automatización UI: Todos los elementos de la UI tienen ID o botones con eventos claros.

Código mantenible: Uso de variables descriptivas y comentarios claros.

Cómo usar el proyecto

Abrir index.html en un navegador web moderno.

Agregar un contacto llenando los campos y presionando Agregar.

Editar un contacto usando el botón Editar.

Eliminar un contacto usando el botón Eliminar.

Todos los cambios se reflejan de inmediato en la tabla, simulando un sistema de gestión de contactos.

Posibles mejoras futuras

Almacenar datos en localStorage para persistencia entre sesiones.

Validar formato de correo y teléfono en tiempo real.

Agregar conteo de palabras o vocales del nombre para prácticas de validación.

Integrar con BDD y Selenium para pruebas automatizadas de UI.

Añadir filtros y búsqueda de contactos en la tabla.


