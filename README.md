# Aplicación de Smoothies con Snowflake y Streamlit  
**Proyecto Hands-On – Snowflake Data Application Builders Workshop**

Este repositorio contiene un proyecto práctico desarrollado como parte del **Snowflake Hands-On Essentials: Data Application Builders Workshop**.

El objetivo del proyecto es demostrar cómo construir **aplicaciones de datos directamente sobre Snowflake**, utilizando **Streamlit**, **Snowpark** y tablas de Snowflake como backend, sin infraestructura externa.

---

## Descripción General

La solución está compuesta por **dos aplicaciones Streamlit** que se ejecutan dentro de Snowflake y trabajan sobre la misma base de datos.

---

## 1️ Aplicación de Pedido de Smoothies

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

## 📄 Archivos del Proyecto

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

![Aplicación de Pedido de Smoothies](<img width="734" height="341" alt="image" src="https://github.com/user-attachments/assets/a2458d75-fc9a-4e09-ab36-68fd5bea8ca6" />)

