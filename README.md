# ProyectoUnidad2_Grupo4
## Sistema Web de Gestión Inmobiliaria

**Estado:** En desarrollo (Actividad N.º 1) | **Versión:** 1.0  
**Modelo de desarrollo:** Incremental Evolutivo  
**Normativa aplicada:** ISO/IEC/IEEE 12207:2026 | ISO/IEC/IEEE 29148:2018 | ISO/IEC/IEEE 15289:2019

Aplicación web diseñada para centralizar y ordenar la administración operativa, contractual y contable de una empresa familiar de bienes raíces con un portafolio inicial de **10 propiedades** (casas, departamentos y locales comerciales) bajo modalidades de **renta tradicional** y **renta temporal**.

- **Asignatura:** Modelos de Procesos de Desarrollo de Software
- **Institución:** Universidad de las Fuerzas Armadas - ESPE
- **Equipo de Desarrollo (Grupo 4):**
  - Fernando Chicaiza
  - Christopher Benavides
  - Alejandro Rivadeneira
  - Mikael Hidalgo
  - Adrián Toapanta

---

## Tabla de Contenidos
1. [Descripción y Justificación](#descripción-y-justificación)
2. [Alcance y Módulos del Sistema](#alcance-y-módulos-del-sistema)
3. [Roles de Usuario](#roles-de-usuario)
4. [Arquitectura y Stack Tecnológico](#arquitectura-y-stack-tecnológico)
5. [Planificación por Incrementos](#planificación-por-incrementos)
6. [Estructura del Repositorio](#estructura-del-repositorio)

---

## Descripción y Justificación

Actualmente, la gestión inmobiliaria del negocio se realiza de forma manual mediante documentos físicos, recibos sueltos y comunicaciones dispersas, lo que dificulta el seguimiento oportuno de los contratos y hace propenso a errores el cálculo de ingresos, egresos y comisiones.

Este sistema sustituye dicho flujo por una plataforma interna centralizada, trazable y verificable, desarrollada bajo el modelo **Incremental Evolutivo** y alineada con los estándares **ISO/IEC/IEEE 12207:2026**, **29148:2018** y **15289:2019**.

---

## Alcance y Módulos del Sistema

El sistema opera como un **entorno cerrado de uso interno** (sin portal público ni integraciones API directas con plataformas como Airbnb o Booking) y se organiza en **6 módulos principales**:

1. **Portafolio de Propiedades y Rentas:** Gestión de fichas técnicas de inmuebles, características físicas y cambio controlado entre *Renta Tradicional* y *Renta Temporal* una vez concluido el contrato vigente.
2. **Gestión Documental de Contratos (PDF):** Respaldo seguro de contratos notarizados en formato `.pdf` (almacenados fuera de la base de datos), control de vigencia, historial de renovaciones sin sobrescritura y alertas tempranas de vencimiento.
3. **Inventario Valorizado:** Control detallado de bienes y enseres en propiedades amobladas, cálculo automático del valor patrimonial activo y registro de novedades, daños o pérdidas.
4. **Control de Ingresos y Egresos:** Registro de cánones, reservas temporales, garantías y gastos operativos con exigencia obligatoria de comprobante digital adjunto.
5. **Liquidación de Comisiones:** Registro y asiento contable de comisiones de administradores externos (**20 %, 25 % o 30 %** según contrato) a partir de los informes mensuales de renta temporal.
6. **Reportes Financieros y Cierre de Mes:** Cálculo exacto de utilidad neta (`Ingresos Brutos - Comisión - Egresos Operativos`), gráficos comparativos, exportación formal en **PDF / Excel (CSV)** y bloqueo contable mediante *Cierre de Mes*.

---

## Roles de Usuario

- **Propietario / Gestor General:** Gestión de sus propias propiedades, consulta de reportes financieros y auditoría de utilidades.
- **Administrador del Sistema:** Control operativo integral sobre todas las propiedades, contratos en PDF, inventario valorizado y registros del portafolio.
- **Asistente / Contador:** Registro y validación de facturas de ingresos y egresos, comprobantes, liquidación de comisiones y consulta de reportes contables.

> *Nota: Los inquilinos y los administradores externos de estancias cortas no tienen usuario ni acceso directo a la plataforma.*

---

## Arquitectura y Stack Tecnológico

- **Base de Datos:** PostgreSQL 17 (uso estricto de tipos `NUMERIC`/`DECIMAL` para precisión financiera).
- **Almacenamiento de Archivos:** Volúmenes persistentes en servidor (los archivos `.pdf` no se almacenan como binarios en la base de datos, únicamente sus rutas y metadatos).
- **Contenerización y Despliegue:** Docker y Docker Compose sobre servidor VPS Ubuntu Server (DigitalOcean).
- **Diseño UI/UX:** Figma.
- **Control de Versiones:** Git y GitHub.

---

## Planificación por Incrementos

| Hito / Fase | Fecha Prevista | Entregables Principales |
| :--- | :--- | :--- |
| **Actividad N.º 1 (Inicio y Requisitos)** | 18/11/2026 | Acta de Inicio (`ACT-INM-001`), SRS v1.0, Estructura Git y `README.md`. |
| **Incremento 1 (I1 - Entrega Parcial)** | 18/12/2026 | Autenticación por roles, gestión de propiedades, contratos PDF, inventario valorizado y registro base de ingresos/egresos. |
| **Incremento 2 (I2 - Entrega Final)** | 01–04/02/2027 | Liquidación de comisiones, reportes financieros (PDF/Excel), gráficos, cierre de mes y despliegue final en VPS. |

---

## Estructura del Repositorio

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
