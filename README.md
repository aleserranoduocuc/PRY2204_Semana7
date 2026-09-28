# PRY2204 - Semana 7 - Holding Carpenter SPA

## 📋 Actividad Formativa: Poblamiento y Consultas SQL

**Alumno:** Alejandro Serrano  
**Asignatura:** PRY2204 - Modelamiento de Bases de Datos  
**Institución:** Duoc UC Online  
**Fecha:** 28/09/2026  
**Base de datos:** Oracle Autonomous Database (Oracle Cloud)  
**Usuario BD:** `PRY2204_S7`

---

## 🎯 Objetivo

Implementar el modelo relacional del sistema de gestión de personal del **Holding Carpenter SPA**, incluyendo:

- Creación de tablas con restricciones de integridad (DDL)
- Definición de reglas de negocio mediante `ALTER TABLE`
- Poblamiento de datos usando secuencias e identity
- Generación de informes estadísticos con `SELECT`

---

## 📂 Contenido del repositorio

| Archivo | Descripción |
|---------|-------------|
| `Encargo_Semanal.sql` | Script completo con DDL, DML y consultas |
| `README.md` | Este documento |

---

## 🏗️ Estructura del script

### 🔹 Caso 1: Creación de tablas (DDL)

Se crean **10 tablas** en orden secuencial (fuertes → débiles):

1. `region` — Identity (inicia en 7, +2)
2. `genero`
3. `estado_civil`
4. `titulo`
5. `idioma` — Identity (inicia en 25, +3)
6. `comuna` — FK a region
7. `compania` — FK a comuna
8. `personal` — FKs a compania, comuna, estado_civil, genero
9. `titulacion` — PK compuesta
10. `dominio` — PK compuesta

**Restricciones incluidas:**
- PK (Primary Key)
- FK (Foreign Key)
- UN (Unique)
- CK (Check)

---

### 🔹 Caso 2: Reglas de negocio (ALTER TABLE)

Se aplican 3 reglas de negocio:

| Regla | Constraint |
|-------|------------|
| El email es opcional pero no repetible | `personal_email_un` (UNIQUE) |
| El DV del RUN solo acepta 0-9 y K | `personal_dv_ck` (CHECK) |
| Sueldo mínimo: $450.000 | `personal_sueldo_ck` (CHECK) |

---

### 🔹 Caso 3: Poblamiento de datos

Se pueblan **4 tablas** en orden de dependencias:

| Tabla | Filas | Método |
|-------|-------|--------|
| `idioma` | 5 | Identity (25, 28, 31, 34, 37) |
| `region` | 3 | Identity (7, 9, 11) |
| `comuna` | 10 | Sequence `seq_comuna` (1101, +6) |
| `compania` | 7 | Sequence `seq_compania` (10, +5) |

---

### 🔹 Caso 4: Informes

**Informe 1:** Simulación de Renta Promedio  
- Ordenado por Renta Promedio DESC y Nombre Empresa ASC

**Informe 2:** Nueva simulación con +15%  
- Ordenado por Renta Actual ASC y Empresa DESC

---

## 🛠️ Tecnologías utilizadas

- **Oracle Autonomous Database** (Oracle Cloud)
- **Oracle SQL Developer Web**
- **SQL** (DDL, DML, SELECT)
- **GitHub** (control de versiones)

---

## 🚀 Cómo ejecutar

1. Conectarse a Oracle Cloud con el usuario `ADMIN`.
2. Abrir **Database Actions → SQL**.
3. Ejecutar el script `Encargo_Semanal.sql` completo con `F5`.

> ⚠️ El script incluye `ALTER SESSION SET CURRENT_SCHEMA = PRY2204_S7;` al inicio para asegurar que todos los objetos se creen en el esquema correcto.

---

## 📊 Resultados

El script genera exitosamente:

- ✅ 10 tablas creadas
- ✅ 3 constraints de negocio
- ✅ 25 filas insertadas
- ✅ 2 secuencias creadas
- ✅ 2 informes con formato y orden solicitado

---

## 📝 Notas

- El modelo relacional fue proporcionado en la actividad (Figura 1).
- Los datos de ejemplo son referenciales según lo solicitado en la actividad.
- Se utilizó `NVL` para manejar valores `NULL` en el cálculo de simulación de renta.

---

**Duoc UC Online — 2026**
