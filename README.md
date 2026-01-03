# Aplicación de Smoothies con Snowflake y Streamlit  
**Proyecto Hands-On – Snowflake Data Application Builders Workshop**

Este repositorio contiene un proyecto práctico desarrollado como parte del **Snowflake Hands-On Essentials: Data Application Builders Workshop**.

El objetivo del proyecto es demostrar cómo construir **aplicaciones de datos directamente sobre Snowflake**, utilizando **Streamlit**, **Snowpark** y tablas de Snowflake como backend, sin infraestructura externa.

---

## Descripción General

La solución está compuesta por **dos aplicaciones Streamlit** que se ejecutan dentro de Snowflake y trabajan sobre la misma base de datos.

---

## 1 Aplicación de Pedido de Smoothies

Aplicación interactiva que permite a los usuarios:

- Ingresar el nombre del cliente para el pedido
- Seleccionar hasta **5 ingredientes** desde una tabla Snowflake
- Consultar información nutricional en tiempo real desde una **API externa**
- Registrar el pedido directamente en Snowflake

### Características técnicas
- Conexión a Snowflake mediante `st.connection("snowflake")`
- Uso de **Snowpark DataFrames** para acceder a las tablas
- Conversión a **Pandas** para facilitar la interacción con la UI
- Integración con API REST utilizando `requests`
- Inserción de pedidos en la tabla `smoothies.public.orders`

---

## 2 Aplicación de Pedidos Pendientes

Aplicación destinada a la **gestión y preparación de pedidos**:

- Visualiza los pedidos pendientes almacenados en Snowflake
- Permite editar el estado de los pedidos desde la interfaz
- Actualiza los registros mediante operaciones **`MERGE` de Snowpark**

### Características técnicas
- Uso de `get_active_session()` para obtener el contexto activo de Snowflake
- Editor interactivo de datos con `st.data_editor`
- Actualizaciones transaccionales sobre la tabla de pedidos
- Gestión del ciclo de vida del pedido (pendiente → completado)

---

## Arquitectura

- **Frontend**: Streamlit (ejecutado dentro de Snowflake)
- **Backend**: Snowflake + Snowpark (Python)
- **Servicios externos**: API de información nutricional
- **Persistencia de datos**:
  - `smoothies.public.fruit_options`
  - `smoothies.public.orders`

Toda la lógica, procesamiento y persistencia de datos ocurre **dentro de Snowflake**.

---

## Tecnologías Utilizadas

- Snowflake
- Snowpark (Python)
- Streamlit
- Pandas
- Requests
- SQL

---

## Archivos del Proyecto

- `streamlit_app.py` – Aplicación de pedido de smoothies
- `pending_orders_app.py` – Aplicación de gestión de pedidos pendientes
- `requirements.txt` – Dependencias del proyecto

---

## Objetivo del Proyecto

Proyecto desarrollado con fines **educativos y de aprendizaje**, enfocado en:

- Construcción de aplicaciones de datos directamente sobre Snowflake
- Integración entre Streamlit y Snowpark
- Persistencia de estado mediante tablas Snowflake
- Flujo end-to-end de una aplicación de datos (frontend + backend + base de datos)

---

## Nota

Este proyecto es **educativo** y no está pensado para uso productivo.

---

## Capturas de Pantalla

### Aplicación de Pedido de Smoothies

<img width="734" height="341" alt="image" src="https://github.com/user-attachments/assets/a2458d75-fc9a-4e09-ab36-68fd5bea8ca6" />

### Flujo de carga de pedidos

<img width="706" height="878" alt="image" src="https://github.com/user-attachments/assets/d758a66a-a736-4164-ab64-f42609daf34b" />

#### Confirmación 

<img width="654" height="129" alt="image" src="https://github.com/user-attachments/assets/c95d38ca-af32-4ddf-95c9-f2e46459a560" />


### Confirmación y persistencia en base de datos

<img width="933" height="422" alt="image" src="https://github.com/user-attachments/assets/281a90ff-b06f-40bf-b3d6-0a7292e0af6f" />

#### Confirmación

<img width="928" height="459" alt="image" src="https://github.com/user-attachments/assets/94937823-b3cd-4095-9331-f54ce63b8af9" />

### Recepción del pedido y confirmación en base de datos

<img width="1280" height="215" alt="image" src="https://github.com/user-attachments/assets/efe43c5c-0faa-45e8-a4a3-788a4da8b00b" />

---

## Código de la aplicación de pedidos pendientes

Como se indica más arriba el repositorio incluye una segunda aplicación Streamlit encargada de la gestión de pedidos:

- Lectura de pedidos pendientes desde Snowflake
- Edición del estado del pedido desde la UI
- Actualización de registros mediante `MERGE` con Snowpark

Archivo:
- `pending_orders_app.py`





