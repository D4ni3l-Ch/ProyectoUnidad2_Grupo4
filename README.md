# ProyectoUnidad2_Grupo4
# 🏢 Sistema Web de Gestión Inmobiliaria

![Estado](https://img.shields.io/badge/Estado-En%20Desarrollo%20(Actividad%201)-blue)
![Versión](https://img.shields.io/badge/Versión-1.0-green)
![Modelo](https://img.shields.io/badge/Ciclo%20de%20Vida-Incremental%20Evolutivo-orange)
![Normativa](https://img.shields.io/badge/Estándares-ISO%2FIEC%2FIEEE%2012207%20%7C%2029148%20%7C%2015289-lightgrey)

Aplicación web diseñada para centralizar y automatizar la administración operativa, contractual y contable de una empresa de administración de bienes raíces con un portafolio inicial de **10 propiedades** (casas, departamentos y locales comerciales) bajo modalidades de **renta tradicional** y **renta temporal**.

Asignatura: Modelos de Procesos de Desarrollo de Software

Institución: Universidad de las Fuerzas Armadas - ESPE

Grupo de Desarrollo (Grupo 4)

* Fernando Chicaiza
* Christopher Benavides
* Alejandro Rivadeneira
* Mikael Hidalgo
* Adrián Toapanta 

---

## 📋 Tabla de Contenidos
1. [Descripción y Justificación](#-descripción-y-justificación)
2. [Alcance y Módulos del Sistema](#-alcance-y-módulos-del-sistema)
3. [Roles de Usuario](#-roles-de-usuario)
4. [Arquitectura y Stack Tecnológico](#-arquitectura-y-stack-tecnológico)
5. [Planificación por Incrementos](#-planificación-por-incrementos)
6. [Estructura del Repositorio](#-estructura-del-repositorio)

---

## 🎯 Descripción y Justificación

Actualmente, la gestión inmobiliaria se realiza de forma manual mediante documentos físicos, recibos sueltos y comunicaciones dispersas, lo que dificulta el seguimiento de contratos y genera errores en el cálculo de ingresos, egresos y comisiones.

Este sistema sustituye dicho flujo por una plataforma centralizada, trazable y segura, desarrollada bajo el modelo **Incremental Evolutivo** y alineada con las normas **ISO/IEC/IEEE 12207:2026**, **29148:2018** y **15289:2019**.

---

## 🧩 Alcance y Módulos del Sistema

El sistema opera como un **entorno cerrado de uso interno** (sin portal público ni integraciones API directas con Airbnb o Booking) y se divide en **6 módulos principales**:

1. **Portafolio de Propiedades y Rentas:** Gestión de fichas técnicas de inmuebles, características físicas, estados y cambio controlado entre *Renta Tradicional* y *Renta Temporal*.
2. **Gestión Documental de Contratos (PDF):** Respaldo seguro de contratos notariados en formato `.pdf` (almacenados fuera de la BD), control de vigencia, historial de renovaciones sin sobrescritura y alertas tempranas de vencimiento.
3. **Inventario Valorizado:** Control detallado de bienes y enseres en propiedades amobladas, cálculo automático del valor patrimonial activo y registro de daños o pérdidas.
4. **Control de Ingresos y Egresos:** Registro de cánones, reservas, garantías y gastos operativos con exigencia obligatoria de comprobante digital adjunto.
5. **Liquidación de Comisiones:** Cálculo y asiento contable de comisiones de administradores externos (**20%, 25% o 30%**) a partir de los informes mensuales de renta temporal.
6. **Reportes Financieros y Cierre de Mes:** Cálculo exacto de utilidad neta (`Ingresos Brutos - Comisión - Egresos Operativos`), gráficos comparativos, exportación en **PDF / Excel (CSV)** y bloqueo contable mediante *Cierre de Mes*.

---

## 👥 Roles de Usuario

* **Propietario / Gestor General:** Supervisión de sus inmuebles, consulta de reportes financieros consolidados y auditoría de utilidades.
* **Administrador Operativo:** Gestión integral del portafolio, registro de contratos PDF, control de inventario y carga de informes externos.
* **Contador / Asistente Financiero:** Registro y validación de ingresos, egresos, comprobantes, liquidación de comisiones y reportes contables.

> *Nota: Los inquilinos y administradores externos de estancias cortas no tienen acceso directo a la plataforma.*

---

## 🛠️ Arquitectura y Stack Tecnológico

* **Base de Datos:** PostgreSQL 17 (uso estricto de tipos `NUMERIC/DECIMAL` para precisión financiera).
* **Almacenamiento de Archivos:** Volúmenes persistentes en servidor (los PDFs no se almacenan como binarios en la BD, solo sus rutas y metadatos).
* **Contenerización y Despliegue:** Docker & Docker Compose sobre VPS Ubuntu Server 22.04 x64 (DigitalOcean).
* **Diseño UI/UX:** Figma.
* **Control de Versiones:** Git & GitHub.

---

## 📅 Planificación por Incrementos

| Hito / Fase | Fecha Prevista | Entregables Principales |
| :--- | :--- | :--- |
| **Actividad N.º 1 (Inicio y Requisitos)** | 18/11/2026 | Acta de Inicio (`ACT-INM-001`), SRS v1.0, Estructura Git y `README.md`. |
| **Incremento 1 (I1 - Entrega Parcial)** | 18/12/2026 | Autenticación por roles, gestión de propiedades, contratos PDF, inventario valorizado y registro base de ingresos/egresos. |
| **Incremento 2 (I2 - Entrega Final)** | 01–04/02/2027 | Liquidación de comisiones, reportes financieros (PDF/Excel), gráficos, cierre de mes y despliegue final en VPS. |

---

## 📁 Estructura del Repositorio

```text
ProyectoUnidad2_Grupo4/
├── docs/                      # Documentación normativa del proyecto
│   ├── acta-inicio/           # Acta de Inicio y Autorización (ISO/IEC/IEEE 12207)
│   ├── srs/                   # Especificación de Requisitos de Software (ISO/IEC/IEEE 29148)
│   └── entrevistas/           # Evidencias y registro de elicitación con el cliente
├── design/                    # Prototipos de interfaz y diagramas (Figma / UML)
├── src/                       # Código fuente (a implementar en Incrementos I1 e I2)
├── docker/                    # Configuración de contenedores y volúmenes (próximas fases)
└── README.md                  # Documentación principal del repositorio
