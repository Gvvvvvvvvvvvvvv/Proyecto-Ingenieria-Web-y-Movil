# Proyecto de Ingeniería Web y Móvil: Plataforma de Gestión y Seguimiento de Reclamos Ciudadanos (Municipalidad)

## 1. Justificación del problema
En las administraciones locales y municipalidades, los ciudadanos frecuentemente experimentan tiempos de respuesta prolongados, falta de transparencia y poca efectividad al ingresar solicitudes, reclamos o denuncias. Esta situación corresponde al desafío **"Baja Capacidad de Respuesta ante Reclamos Ciudadanos"** identificado en el diagnóstico comunal. Actualmente, los municipios manejan estos requerimientos de forma desarticulada, a menudo mediante planillas Excel o herramientas manuales dispersas, lo que genera frustración en la comunidad y dificulta el seguimiento por parte de los funcionarios.

Basado en el marco normativo nacional (Ley Orgánica Constitucional de Municipalidades y el Manual de Ordenanzas Tipo de Participación Ciudadana), las municipalidades tienen el deber ético y jurídico de mantener canales abiertos, oportunos y transparentes de atención. El problema abordado en este proyecto radica en la necesidad de centralizar, automatizar y transparentar el ciclo de vida de los reclamos y solicitudes ciudadanas, mejorando los tiempos de respuesta y optimizando la comunicación bidireccional entre la comunidad y la municipalidad.

---

## 2. Usuarios objetivo y Roles
La plataforma considera tres grupos principales de usuarios con roles diferenciados:
- **Ciudadano / Vecino:** Usuario que habita, trabaja o estudia en la comuna. Requiere registrar solicitudes o reclamos, adjuntar evidencias, consultar el estado en tiempo real y recibir notificaciones sobre los avances.
- **Funcionario Municipal / Gestor:** Personal encargado de gestionar, derivar, responder, actualizar y resolver los reclamos asignados a su departamento mediante un panel administrativo.
- **Administrador:** Usuario con privilegios avanzados para la gestión general del sistema, control de cuentas, asignación de roles y supervisión de estadísticas globales.

### Proto-personas
* **Proto-persona 1: Camila (Vecina Autónoma)**
  * **Rol:** Ciudadano
  * **Características generales:** Utiliza principalmente su teléfono móvil y computador. Necesita reportar problemas de baches o luminarias rápidamente y poder hacerles seguimiento desde cualquier lugar sin trámites presenciales.
  * **Necesidades principales:** Acceso rápido, visualización clara del estado de sus requerimientos e interfaz intuitiva.

* **Proto-persona 2: Don Mario (Adulto Mayor)**
  * **Rol:** Ciudadano
  * **Características generales:** Presenta menor familiaridad con plataformas digitales complejas. Requiere asistencia visual, textos claros y la opción de ser apoyado por la OIRS municipal.
  * **Necesidades principales:** Navegación simple, instrucciones directas y canales accesibles.

* **Proto-persona 3: Carlos (Funcionario OIRS / Operativo)**
  * **Rol:** Funcionario
  * **Características generales:** Trabaja desde un computador en oficina municipal. Necesita clasificar, derivar los reclamos a las unidades correspondientes (ej. Aseo, Tránsito, Obras) y registrar respuestas dentro de los plazos legales (20 días corridos).
  * **Necesidades principales:** Eficiencia en la gestión de expedientes, filtros por departamento y trazabilidad de plazos.

---

## 3. Requerimientos del Sistema

### Requerimientos Funcionales por Rol (RF)
| ID | Requerimiento Funcional | Rol |
| :--- | :--- | :--- |
| **RF-01** | El sistema deberá permitir al ciudadano registrar una nueva solicitud, reclamo o sugerencia indicando categoría, descripción y ubicación geográfica (georreferenciación). | Ciudadano |
| **RF-02** | El sistema deberá generar un código o folio único de seguimiento para cada reclamo ingresado, permitiendo su consulta pública o autenticada. | Ciudadano |
| **RF-03** | El sistema deberá permitir al ciudadano consultar el historial y estado actual de sus reclamos (Enviado, Derivado, En Proceso, Resuelto, Cerrado). | Ciudadano |
| **RF-04** | El sistema deberá permitir a los funcionarios visualizar el panel administrativo con la lista de reclamos asignados a su unidad o dirección. | Funcionario |
| **RF-05** | El sistema deberá permitir al funcionario actualizar el estado de un reclamo, cambiar su asignación, adjuntar informes técnicos y redactar la respuesta oficial. | Funcionario |
| **RF-06** | El sistema deberá enviar notificaciones automáticas al ciudadano ante cada cambio relevante o actualización del estado de su reclamo. | Transversal |
| **RF-07** | El sistema deberá permitir al administrador gestionar usuarios, roles y parámetros generales de las unidades municipales. | Administrador |

### Funcionalidades Transversales (FT)
- **FT-01:** El sistema deberá permitir el registro de nuevos usuarios (ciudadanos y funcionarios).
- **FT-02:** El sistema deberá permitir a los usuarios iniciar sesión mediante credenciales seguras.
- **FT-03:** El sistema deberá permitir cerrar una sesión activa.
- **FT-04:** El sistema deberá restringir las funcionalidades y rutas disponibles de acuerdo con el rol del usuario autenticado.

### Requerimientos No Funcionales (RNF)
- **RNF-01 (Diseño adaptable / Responsive):** La interfaz deberá adaptarse a dispositivos móviles y de escritorio, manteniendo accesibles las funcionalidades principales.
- **RNF-02 (Navegación consistente):** La aplicación mantendrá patrones de navegación consistentes y predecibles entre vistas.
- **RNF-03 (Seguridad de datos):** Almacenamiento de contraseñas mediante hash seguro (bcrypt), autenticación basada en tokens y validación estricta de datos.
- **RNF-04 (Rendimiento):** Las consultas habituales y operaciones de carga de reclamos deberán responder de manera fluida y estable.

---

## 4. Arquitectura de Navegación y UX

### Rutas Principales y Secundarias
* **Rutas Públicas:**
  * `/login` - Inicio de sesión
  * `/registro` - Registro de nueva cuenta
  * `/consulta-folio` - Consulta rápida de reclamos sin autenticación
* **Rutas Protegidas del Ciudadano:**
  * `/ciudadano/inicio` - Resumen y accesos principales
  * `/ciudadano/reclamos` - Listado de reclamos realizados
  * `/ciudadano/reclamos/nuevo` - Formulario de ingreso de reclamo
  * `/ciudadano/reclamos/:id` - Detalle y seguimiento de un reclamo específico
  * `/ciudadano/perfil` - Gestión de datos personales del vecino
* **Rutas Protegidas del Funcionario:**
  * `/funcionario/inicio` - Panel de control y métricas operativas
  * `/funcionario/gestion-reclamos` - Listado y filtrado de reclamos asignados
  * `/funcionario/reclamos/:id/atender` - Interfaz para actualizar estado y responder
* **Rutas Protegidas del Administrador:**
  * `/admin/inicio` - Panel general de administración
  * `/admin/usuarios` - Gestión de cuentas y asignación de roles municipales

### Matriz de Acceso por Rol
| Funcionalidad | Ciudadano | Funcionario | Administrador |
| :--- | :---: | :---: | :---: |
| Registrar reclamo / solicitud | ✅ | - | - |
| Consultar estado de reclamos propios | ✅ | - | - |
| Gestionar y responder reclamos asignados | - | ✅ | - |
| Supervisar todas las unidades y reportes | - | - | ✅ |
| Administrar usuarios y permisos | - | - | ✅ |

---

## 5. Flujos de Tareas (Task Flows)

### Task Flow 1: Registro y seguimiento de reclamo
* **Rol:** Ciudadano
* **Secuencia:** 
  Inicio de sesión -> Menú principal -> Seleccionar "Nuevo Reclamo" -> Ingresar categoría, descripción y ubicación -> Adjuntar evidencia fotográfica -> Enviar solicitud -> Obtener folio único -> Visualizar seguimiento en la lista de reclamos.

### Task Flow 2: Gestión y resolución de reclamos
* **Rol:** Funcionario
* **Secuencia:** 
  Inicio de sesión -> Panel de gestión -> Filtrar reclamos pendientes por dirección/departamento -> Seleccionar reclamo -> Redactar respuesta u oficio técnico -> Cambiar estado a "Resuelto" -> Guardar cambios -> Envío automático de notificación al ciudadano.

---

## 6. Justificación Técnica y Tecnologías

### Librerías y Frameworks Principales
* **Frontend:** Ionic Framework (v7+) con React, TypeScript y TailwindCSS para garantizar una interfaz adaptable (responsive) tanto en dispositivos móviles como en escritorio.
* **Backend:** Node.js con Express y base de datos relacional (PostgreSQL) para asegurar la integridad de los expedientes electrónicos y el control estricto de los plazos legales estipulados por la normativa OIRS (20 días corridos).

### Tabla de Tecnologías
| Librería / Herramienta | Propósito |
| :--- | :--- |
| `react` | Construcción de la interfaz mediante componentes modulares. |
| `react-router-dom` | Gestión y enrutamiento entre las diferentes vistas de la plataforma. |
| `@ionic/react` | Componentes nativos y adaptativos de Ionic para web y móvil. |
| `ionicons` | Biblioteca de iconos estandarizada. |
| `TailwindCSS` | Estilizado rápido y diseño adaptable. |
