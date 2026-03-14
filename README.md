# 🧪 Laboratorio: Documentación de Pruebas de API REST

 Esta actividad debe documentarse íntegramente en este archivo `README.md`. Por cada punto, el estudiante debe ejecutar la petición indicada y completar los espacios en blanco con la **Respuesta del Servidor** y el **Código de Estado** real obtenido en su entorno local.

---

## 🚀 Guía de Pruebas y Documentación

### 1. Crear un nuevo estudiante

* **Método:** `POST`
* **URL:** `http://localhost:8080/api/students`
* **Cuerpo de la Petición (JSON):**

```json
{
  "firstName": "Ana",
  "lastName": "García",
  "email": "ana.garcia@estudiante.com",
  "birthDate": "2001-03-12",
  "phone": "3004445566"
}

```

* **Respuesta del Servidor (Completar):**

```json

{
  "firstName": "Ana",
  "lastName": "García",
  "email": "ana.garcia@estudiante.com",
  "birthDate": "2001-03-12",
  "phone": "3004445566"
}

```

* **Código de Estado (Status Code):** `__201 OK __`

---

### 2. Obtener la lista completa

* **Método:** `GET`
* **URL:** `http://localhost:8080/api/students`
* **Respuesta del Servidor (Completar):**

```json

[
    {
        "firstName": "Ana",
        "lastName": "García",
        "email": "ana.garcia@estudiante.com",
        "birthDate": "2001-03-12",
        "id": 1,
        "phone": "3004445566"
    }
]
```

* **Código de Estado (Status Code):** `__200 OK__`

---

### 3. Buscar estudiante por ID (Existente)

* **Método:** `GET`
* **URL:** `http://localhost:8080/api/students/1`
* **Respuesta del Servidor (Completar):**

```json

{
    "firstName": "Ana",
    "lastName": "García",
    "email": "ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "id": 1,
    "phone": "3004445566"
}
```

* **Código de Estado (Status Code):** `__200 OK__`

---

### 4. Buscar estudiante por Email

* **Método:** `GET`
* **URL:** `http://localhost:8080/api/students/email/ana.garcia@estudiante.com`
* **Respuesta del Servidor (Completar):**

```json
{
  "id": 1,
  "firstName": "Ana María",
  "lastName": "García",
  "email": "ana.garcia@estudiante.com",
  "birthDate": "2001-03-12",
  "phone": "3119998877"
}

```

* **Código de Estado (Status Code):** `__200 OK__`

---

### 5. Actualizar datos del estudiante

* **Método:** `PUT`
* **URL:** `http://localhost:8080/api/students/1`
* **Cuerpo de la Petición (JSON):**

```json
{
  "firstName": "Ana María",
  "lastName": "García",
  "email": "ana.garcia@estudiante.com",
  "birthDate": "2001-03-12",
  "phone": "3119998877"
}

```

* **Respuesta del Servidor (Completar):**

```json
{
    "firstName": "Ana María",
    "lastName": "García",
    "email": "ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "id": 1,
    "phone": "3119998877"
}

```

* **Código de Estado (Status Code):** `_200 OK___`

---

### 6. Escenario de Error: Buscar ID inexistente

* **Método:** `GET`
* **URL:** `http://localhost:8080/api/students/999`
* **Respuesta del Servidor (Completar):**

```json
{}

```

* **Código de Estado (Status Code):** `__404 Not Found__`

---

### 7. Eliminar el registro

* **Método:** `DELETE`
* **URL:** `http://localhost:8080/api/students/1`
* **Respuesta del Servidor (Completar):**

```json
{}

```

* **Código de Estado (Status Code):** `__204 No Content__`

---

## 📝 Cuestionario de Análisis

**Instrucciones:** Responda las siguientes preguntas basándose en su experiencia durante el laboratorio y el código del proyecto.

1. **¿Cuál es la diferencia entre los códigos de estado 200 y 201? ¿En qué endpoints se obtuvieron cada uno?**
* *Respuesta:*El código 200 OK es una respuesta genérica que indica que la solicitud fue exitosa. El código 201 Created es más específico e indica que, además de ser exitosa, la solicitud resultó en la creación de un nuevo recurso.



2. **En el escenario de error (punto 6), ¿qué información devuelve la API y por qué es importante para un desarrollador frontend recibir un código 404 en lugar de un código 500?**
* *Respuesta:* La API devuelve un objeto JSON con detalles del error (timestamp, status 404 y un mensaje como "Student not found").



3. **¿Qué sucede en la base de datos PostgreSQL cuando se ejecuta con éxito la petición DELETE? (Explique brevemente en términos de persistencia).**
* *Respuesta:*Ocurre una eliminación física del registro. En términos de persistencia, esto significa que el dato deja de estar almacenado de forma permanente en el disco duro. Una vez borrado, cualquier intento de consulta posterior no encontrará el recurso porque ya no existe en el almacenamiento persistente.


4. **Si intentara crear un estudiante con el mismo email que ya existe en la base de datos, ¿qué cree que sucedería y qué código de error sería el más adecuado para devolver?**
* *Respuesta:*El servidor lanzaría una excepción de violación de unicidad (si el campo email está configurado como UNIQUE). La operación de guardado fallaría para evitar datos duplicados.


5. **¿Por qué utilizamos el método PUT para actualizar y no el método POST? ¿Cuál es la convención técnica detrás de esta decisión?**
* *Respuesta:*Se utiliza PUT porque es un método idempotente. Esto significa que si envías la misma petición de actualización varias veces, el resultado final siempre será el mismo.



