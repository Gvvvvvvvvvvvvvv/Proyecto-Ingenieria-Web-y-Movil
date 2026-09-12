## Desarrollo de una aplicación web y móvil para la gestión y seguimiento de reclamos ciudadanos dirigidos a una municipalidad
# Desarrollo de una aplicación web y móvil para la gestión y seguimiento de reclamos ciudadanos dirigidos a una municipalidad

## Presentado por :
Felipe Bechan
Giovani Faúndez
Vicente Rodríguez
Tomás Olivares
## Presentado por:
* Felipe Bechan
* Giovani Faúndez
* Vicente Rodríguez
* Tomás Olivares

## Índice
1. [Justificación del problema](#1-justificación-del-problema)
2. [Usuarios y Roles](#2-usuarios-y-roles)
   * [Roles del Sistema](#roles-del-sistema)
   * [Definición de conceptos](#definición-de-conceptos)
   * [Proto-personas](#proto-personas)
3. [Requerimientos](#3-requerimientos)
   * [Requerimientos Funcionales por Rol](#requerimientos-funcionales-por-rol)
   * [Funcionalidades Transversales](#funcionalidades-transversales)
   * [Requerimientos No Funcionales](#requerimientos-no-funcionales)
4. [Arquitectura de la Información / UX](#4-arquitectura-de-la-información--ux)
   * [1. Rutas principales y secundarias](#1-rutas-principales-y-secundarias)
   * [2. Relaciones jerárquicas entre vistas](#2-relaciones-jerárquicas-entre-vistas)
   * [3. Diferenciación de acceso según roles](#3-diferenciación-de-acceso-según-roles)
   * [4. Flujos de Tareas (Task Flows)](#4-flujos-de-tareas-task-flows)
   * [5. Puntos críticos de interacción](#5-puntos-críticos-de-interacción)
   * [6. Justificación Técnica](#6-justificación-técnica)
5. [Bocetos UX/UI](#5-bocetos-uxui)
6. [Frontend con Ionic-React](#6-frontend-con-ionic-react)

# Proyecto de Ingeniería Web y Móvil: Plataforma de Gestión y Seguimiento de Reclamos Ciudadanos (Municipalidad)
---

## 1. Justificación del problema
En las administraciones locales y municipalidades, los ciudadanos frecuentemente experimentan tiempos de respuesta prolongados, falta de transparencia y poca efectividad al ingresar solicitudes, reclamos o denuncias. Esta situación corresponde al desafío **"Baja Capacidad de Respuesta ante Reclamos Ciudadanos"** identificado en el diagnóstico comunal. Actualmente, los municipios manejan estos requerimientos de forma desarticulada, a menudo mediante planillas Excel o herramientas manuales dispersas, lo que genera frustración en la comunidad y dificulta el seguimiento por parte de los funcionarios.

Basado en el marco normativo nacional (Ley Orgánica Constitucional de Municipalidades y el Manual de Ordenanzas Tipo de Participación Ciudadana), las municipalidades tienen el deber ético y jurídico de mantener canales abiertos, oportunos y transparentes de atención. El problema abordado en este proyecto radica en la necesidad de centralizar, automatizar y transparentar el ciclo de vida de los reclamos y solicitudes ciudadanas, mejorando los tiempos de respuesta y optimizando la comunicación bidireccional entre la comunidad y la municipalidad.
En el ámbito de la gestión pública local, la atención oportuna a las inquietudes vecinales es fundamental para fortalecer la confianza ciudadana y la gobernanza democrática. No obstante, el diagnóstico de desafíos públicos comunales revela una **"Baja Capacidad de Respuesta ante Reclamos Ciudadanos"** (Desafío 35), caracterizada por tiempos de respuesta prolongados, falta de trazabilidad y desarticulación entre las direcciones municipales.

De acuerdo con el marco normativo chileno establecido en la **Ley Nº 18.695 (Orgánica Constitucional de Municipalidades, Art. 98)** y el **Manual de Ordenanzas Tipo de Participación Ciudadana (Título VII, Párrafo 3° "De la OIRS", Artículos 40 al 48)**, cada municipalidad debe mantener en funcionamiento una Oficina de Informaciones, Reclamos y Sugerencias (OIRS) con la obligación de evacuar respuestas formales en un plazo máximo de 20 días corridos, garantizando accesibilidad, transparencia y protección de datos personales (Art. 47).

Actualmente, muchas administraciones gestionan estos trámites de manera fragmentada o manual (planillas de cálculo, expedientes físicos en papel), provocando demoras, duplicidad de esfuerzos y frustración en la comunidad. Asimismo, existe una brecha digital en sectores vulnerables o personas mayores que limita el acceso efectivo a estos canales.

Por consiguiente, este proyecto aborda la necesidad de diseñar e implementar una **plataforma web y móvil adaptativa para la gestión y seguimiento de reclamos ciudadanos**, que centralice el ciclo de vida de cada solicitud mediante un número de folio único, automatice la derivación a las unidades técnicas pertinentes, alerte sobre los plazos de vencimiento y ofrezca una experiencia accesible e inclusiva tanto para vecinos como para funcionarios municipales.

---

## 2. Usuarios objetivo y Roles
La plataforma considera tres grupos principales de usuarios con roles diferenciados:
- **Ciudadano / Vecino:** Usuario que habita, trabaja o estudia en la comuna. Requiere registrar solicitudes o reclamos, adjuntar evidencias, consultar el estado en tiempo real y recibir notificaciones sobre los avances.
- **Funcionario Municipal / Gestor:** Personal encargado de gestionar, derivar, responder, actualizar y resolver los reclamos asignados a su departamento mediante un panel administrativo.
- **Administrador:** Usuario con privilegios avanzados para la gestión general del sistema, control de cuentas, asignación de roles y supervisión de estadísticas globales.
## 2. Usuarios y Roles

La plataforma considera principalmente dos grupos de usuarios de interacción directa: **Ciudadanos** y **Funcionarios Municipales**, además de un rol de **Administrador** del sistema.

### Roles del Sistema
* **Ciudadano:** Usuario que reside, trabaja o transita en la comuna. Puede ingresar solicitudes, reclamos o sugerencias, adjuntar evidencias y realizar seguimiento del estado de sus trámites.
* **Funcionario / Gestor OIRS:** Personal municipal encargado de recepcionar, clasificar, derivar requerimientos a las direcciones técnicas (Obras, Aseo, Tránsito, etc.), redactar respuestas oficiales y emitir resoluciones dentro del plazo legal.
* **Administrador:** Encargado de la configuración general de la plataforma, gestión de cuentas de usuarios, asignación de roles y supervisión de métricas de cumplimiento municipal.

### Definición de conceptos
* **Rol:** Define qué puede y qué no puede hacer un usuario dentro del sistema (permisos, accesos y funciones).
* **Proto-persona:** Perfil hipotético basado en el contexto real que describe quién es el usuario, sus características sociodemográficas, necesidades, objetivos, limitaciones y contexto de uso.

### Proto-personas
* **Proto-persona 1: Camila (Vecina Autónoma)**
  * **Rol:** Ciudadano
  * **Características generales:** Utiliza principalmente su teléfono móvil y computador. Necesita reportar problemas de baches o luminarias rápidamente y poder hacerles seguimiento desde cualquier lugar sin trámites presenciales.
  * **Necesidades principales:** Acceso rápido, visualización clara del estado de sus requerimientos e interfaz intuitiva.

* **Proto-persona 2: Don Mario (Adulto Mayor)**
  * **Rol:** Ciudadano
  * **Características generales:** Presenta menor familiaridad con plataformas digitales complejas. Requiere asistencia visual, textos claros y la opción de ser apoyado por la OIRS municipal.
  * **Necesidades principales:** Navegación simple, instrucciones directas y canales accesibles.
#### Proto-persona 1: Ciudadana activa con interacción móvil autónoma
* **Nombre ficticio:** Camila
* **Tipo de usuario o rol:** Ciudadano
* **Características generales:** Joven profesional y vecina de 28 años. Utiliza permanentemente su teléfono inteligente para trámites cotidianos. Dispone de poco tiempo y prefiere resolver incidentes urbanos de manera digital e inmediata.
* **Necesidades principales:**
  * Ingresar reclamos (ej. luminarias apagadas, baches) en menos de 2 minutos.
  * Adjuntar fotos y georreferenciación directa desde el móvil.
  * Recibir notificaciones en tiempo real sin tener que acudir presencialmente al municipio.
* **Objetivos de uso:** Mantener su barrio en buenas condiciones y exigir respuestas formales y oportunas del municipio.
* **Dificultades o puntos de frustración:**
  * Formularios extensos que solicitan datos innecesarios.
  * No saber si su solicitud fue recibida o en qué unidad se encuentra estancada.
  * Interfaces no optimizadas para pantallas táctiles.
* **Funcionalidades que utilizaría:** Formulario rápido de reclamo, captura de cámara/geolocalización, consulta por folio y notificaciones de estado.
* **Dispositivo y contexto probable de acceso:** Teléfono móvil (iOS/Android) durante sus trayectos cotidianos o desde su hogar.

* **Proto-persona 3: Carlos (Funcionario OIRS / Operativo)**
  * **Rol:** Funcionario
  * **Características generales:** Trabaja desde un computador en oficina municipal. Necesita clasificar, derivar los reclamos a las unidades correspondientes (ej. Aseo, Tránsito, Obras) y registrar respuestas dentro de los plazos legales (20 días corridos).
  * **Necesidades principales:** Eficiencia en la gestión de expedientes, filtros por departamento y trazabilidad de plazos.
#### Proto-persona 2: Vecino adulto mayor con necesidad de accesibilidad y claridad
* **Nombre ficticio:** Don Mario
* **Tipo de usuario o rol:** Ciudadano
* **Características generales:** Jubilado de 68 años, con conocimiento digital básico. Suele frustrarse con interfaces sobrecargadas o letra pequeña. En ocasiones realiza consultas de manera presencial o telefónica en la OIRS.
* **Necesidades principales:**
  * Interfaz con textos grandes, lenguaje directo y alta legibilidad.
  * Instrucciones claras paso a paso.
  * Opción de consultar el estado de su trámite ingresando únicamente su folio o RUT.
* **Objetivos de uso:** Reportar problemas vecinales de aseo o ruidos molestos y asegurarse de que el municipio cumpla con los plazos de respuesta.
* **Dificultades o puntos de frustración:**
  * Navegación confusa con demasiados menús anidados.
  * Términos técnicos o jurídicos difíciles de comprender.
  * Pérdida de la información ingresada por fallas de conexión.
* **Funcionalidades que utilizaría:** Consulta simplificada por folio, vista clara de estado del requerimiento y canal de ayuda visual.
* **Dispositivo y contexto probable de acceso:** Computador de escritorio en casa o teléfono móvil con apoyo de un familiar.

#### Proto-persona 3: Funcionario municipal encargado de gestión OIRS
* **Nombre ficticio:** Carlos
* **Tipo de usuario o rol:** Funcionario
* **Características generales:** Funcionario administrativo de 42 años con experiencia en atención ciudadana. Recibe decenas de solicitudes diarias de distintos canales (web, presencial y telefónico) y debe distribuirlas a las direcciones municipales correspondientes.
* **Necesidades principales:**
  * Bandeja centralizada de solicitudes con filtros por estado, fecha y dirección técnica.
  * Monitoreo visual de los plazos legales de 20 días corridos para evitar infracciones administrativas.
  * Plantillas estandarizadas para redactar oficios y respuestas formales.
* **Objetivos de uso:** Derivar ágilmente las presentaciones a las unidades responsables y asegurar el cumplimiento de las respuestas dentro del marco legal.
* **Dificultades o puntos de frustración:**
  * Duplicidad de reclamos sobre un mismo evento.
  * Pérdida de trazabilidad al transferir solicitudes entre departamentos.
  * Sistemas lentos que dificultan la carga de informes técnicos.
* **Funcionalidades que utilizaría:** Panel de gestión de expedientes, derivación interna, control de plazos (semáforo de alerta), carga de informes técnicos y emisión de oficios de respuesta.
* **Dispositivo y contexto probable de acceso:** Computador de escritorio en la oficina municipal durante la jornada laboral.

---

## 3. Requerimientos del Sistema
## 3. Requerimientos

### Requerimientos Funcionales por Rol (RF)
| ID | Requerimiento Funcional | Rol |
### Requerimientos Funcionales por Rol
| ID | Requerimiento funcional | Rol |
| :--- | :--- | :--- |
| **RF-01** | El sistema deberá permitir al ciudadano registrar una nueva solicitud, reclamo o sugerencia indicando categoría, descripción y ubicación geográfica (georreferenciación). | Ciudadano |
| **RF-02** | El sistema deberá generar un código o folio único de seguimiento para cada reclamo ingresado, permitiendo su consulta pública o autenticada. | Ciudadano |
| **RF-03** | El sistema deberá permitir al ciudadano consultar el historial y estado actual de sus reclamos (Enviado, Derivado, En Proceso, Resuelto, Cerrado). | Ciudadano |
| **RF-04** | El sistema deberá permitir a los funcionarios visualizar el panel administrativo con la lista de reclamos asignados a su unidad o dirección. | Funcionario |
| **RF-05** | El sistema deberá permitir al funcionario actualizar el estado de un reclamo, cambiar su asignación, adjuntar informes técnicos y redactar la respuesta oficial. | Funcionario |
| **RF-06** | El sistema deberá enviar notificaciones automáticas al ciudadano ante cada cambio relevante o actualización del estado de su reclamo. | Transversal |
| **RF-07** | El sistema deberá permitir al administrador gestionar usuarios, roles y parámetros generales de las unidades municipales. | Administrador |
| **RF-01** | El sistema deberá permitir al ciudadano ingresar una presentación o reclamo clasificándolo por tipo (consulta, sugerencia, reclamo o denuncia), temática, descripción detallada, ubicación geográfica y archivos de respaldo. | Ciudadano |
| **RF-02** | El sistema deberá generar y asignar automáticamente un número de folio único e irrepetible para cada requerimiento ingresado, permitiendo su trazabilidad. | Ciudadano |
| **RF-03** | El sistema deberá permitir al ciudadano consultar el estado y avance de sus solicitudes mediante su cuenta o a través del folio público. | Ciudadano |
| **RF-04** | El sistema deberá permitir al funcionario OIRS visualizar la bandeja general de requerimientos, filtrando por estado, categoría, fecha de ingreso y plazo restante de respuesta. | Funcionario |
| **RF-05** | El sistema deberá permitir al funcionario derivar el requerimiento a la unidad técnica correspondiente (Obras, Tránsito, Aseo, etc.) y registrar observaciones internas. | Funcionario |
| **RF-06** | El sistema deberá permitir al funcionario redactar y registrar la respuesta formal al ciudadano, adjuntar informes técnicos y cambiar el estado del requerimiento a "Respondido / Cerrado". | Funcionario |
| **RF-07** | El sistema deberá permitir al administrador gestionar cuentas de usuarios, configurar los departamentos municipales y consultar métricas globales de tiempos de respuesta. | Administrador |

### Funcionalidades Transversales (FT)
- **FT-01:** El sistema deberá permitir el registro de nuevos usuarios (ciudadanos y funcionarios).
- **FT-02:** El sistema deberá permitir a los usuarios iniciar sesión mediante credenciales seguras.
- **FT-03:** El sistema deberá permitir cerrar una sesión activa.
- **FT-04:** El sistema deberá restringir las funcionalidades y rutas disponibles de acuerdo con el rol del usuario autenticado.
### Funcionalidades Transversales
* **FT-01:** El sistema deberá permitir el registro de nuevos usuarios en la plataforma.
* **FT-02:** El sistema deberá permitir a los usuarios iniciar sesión mediante credenciales seguras.
* **FT-03:** El sistema deberá permitir cerrar una sesión activa de forma segura.
* **FT-04:** El sistema deberá restringir las vistas y funcionalidades de acuerdo con el rol autenticado.

### Requerimientos No Funcionales (RNF)
- **RNF-01 (Diseño adaptable / Responsive):** La interfaz deberá adaptarse a dispositivos móviles y de escritorio, manteniendo accesibles las funcionalidades principales.
- **RNF-02 (Navegación consistente):** La aplicación mantendrá patrones de navegación consistentes y predecibles entre vistas.
- **RNF-03 (Seguridad de datos):** Almacenamiento de contraseñas mediante hash seguro (bcrypt), autenticación basada en tokens y validación estricta de datos.
- **RNF-04 (Rendimiento):** Las consultas habituales y operaciones de carga de reclamos deberán responder de manera fluida y estable.
### Requerimientos No Funcionales

#### UX y Usabilidad
* **RNF-UX-01 — Diseño adaptable:** La interfaz deberá adaptarse de forma responsive a dispositivos móviles, tablets y computadores de escritorio sin pérdida de componentes ni funcionalidades.
* **RNF-UX-02 — Navegación consistente:** Los patrones de navegación, botones de acción y cabeceras deberán mantener coherencia visual en todas las vistas de la aplicación.
* **RNF-UX-03 — Reducción de carga cognitiva:** Los formularios se estructurarán en pasos progresivos claros, evitando saturación de campos en una sola pantalla.
* **RNF-UX-04 — Retroalimentación al usuario:** Cada acción relevante (envío, guardado, error) deberá mostrar confirmaciones visuales inmediatas (alertas, modales, toasts).

#### Accesibilidad
* **RNF-ACC-01 — Claridad del contenido:** Se utilizará un lenguaje ciudadano comprensible y directo, evitando tecnicismos legales excesivos en los mensajes orientados al vecino.
* **RNF-ACC-02 — Jerarquía visual:** Se mantendrá contraste visual adecuado, tamaños de tipografía legibles e iconos universales de apoyo.

#### Seguridad y Privacidad
* **RNF-SEG-01 — Protección de contraseñas:** Las contraseñas de usuarios se almacenarán mediante algoritmos seguros de cifrado hash (bcrypt) y nunca en texto plano.
* **RNF-SEG-02 — Autenticación y autorización por roles:** Se implementará control de acceso estricto para asegurar que los ciudadanos no accedan a bandejas internas de gestión municipal.
* **RNF-SEG-03 — Privacidad de datos personales:** Los datos sensibles de los vecinos (RUT, teléfono, domicilio) deberán resguardarse bajo reserva conforme a la Ley Nº 19.628 y el Art. 47 del Manual de Ordenanza Municipal.

#### Rendimiento y Compatibilidad
* **RNF-REN-01 — Tiempo de respuesta:** Las consultas de expedientes y cambio de vistas no deberán superar los 2 segundos de respuesta bajo condiciones normales de conexión.
* **RNF-COM-01 — Compatibilidad de navegadores:** La plataforma deberá funcionar correctamente en los principales navegadores modernos: Google Chrome, Mozilla Firefox, Microsoft Edge y Safari.

---

## 4. Arquitectura de Navegación y UX
## 4. Arquitectura de la Información / UX

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
### 1. Rutas principales y secundarias

### Matriz de Acceso por Rol
#### Rutas públicas
| Ruta | Vista | Descripción |
| :--- | :--- | :--- |
| `/login` | Inicio de sesión | Permite el ingreso de ciudadanos y funcionarios mediante sus credenciales. |
| `/registro` | Registro de usuario | Permite crear una nueva cuenta de ciudadano en la plataforma. |
| `/consulta-folio` | Consulta pública | Permite consultar el estado de un reclamo ingresando únicamente el folio y el RUT. |

#### Rutas protegidas del Ciudadano
| Ruta | Vista | Descripción |
| :--- | :--- | :--- |
| `/ciudadano/inicio` | Inicio Ciudadano | Panel de bienvenida con accesos directos y resumen de trámites activos. |
| `/ciudadano/reclamos/nuevo` | Nuevo Requerimiento | Formulario guiado para redactar y enviar una nueva solicitud o reclamo. |
| `/ciudadano/mis-reclamos` | Historial de Trámites | Listado de todas las solicitudes ingresadas por el usuario y su estado actual. |
| `/ciudadano/reclamos/:id` | Detalle del Requerimiento | Muestra la trazabilidad, unidad asignada, plazos y la respuesta oficial municipal. |
| `/ciudadano/perfil` | Perfil de Usuario | Gestión de datos personales de contacto y preferencias de notificación. |

#### Rutas protegidas del Funcionario
| Ruta | Vista | Descripción |
| :--- | :--- | :--- |
| `/funcionario/inicio` | Panel Funcionario | Resumen de solicitudes asignadas, alertas de vencimiento y accesos rápidos. |
| `/funcionario/bandeja` | Bandeja de Reclamos | Listado integral con filtros por estado, dirección técnica y fecha de ingreso. |
| `/funcionario/reclamos/:id/atender` | Gestión de Solicitud | Interfaz para derivar a otra dirección, adjuntar informes técnicos y redactar respuesta. |

#### Rutas protegidas del Administrador
| Ruta | Vista | Descripción |
| :--- | :--- | :--- |
| `/admin/inicio` | Panel Administrador | Indicadores globales de gestión comunal y tiempos promedio de respuesta. |
| `/admin/usuarios` | Gestión de Usuarios | Administración de cuentas de funcionarios, asignación de dependencias y roles. |
| `/admin/configuracion` | Parámetros del Sistema | Configuración de categorías de reclamos y catálogo de unidades técnicas. |

---

### 2. Relaciones jerárquicas entre vistas

```text
Aplicación OIRS
│
├── Rutas públicas
│   ├── Login
│   ├── Registro
│   └── Consulta pública por folio
│
└── Rutas protegidas
    │
    ├── Ciudadano
    │   ├── Inicio
    │   ├── Nuevo Requerimiento (Ingreso)
    │   ├── Historial de Reclamos
    │   │   └── Detalle y Seguimiento de Reclamo
    │   └── Perfil de Usuario
    │
    ├── Funcionario
    │   ├── Inicio / Resumen de Alertas
    │   └── Bandeja de Reclamos
    │       ├── Detalle y Derivación Interna
    │       └── Emisión de Respuesta Oficial
    │
    └── Administrador
        ├── Inicio / Métricas Globales
        ├── Gestión de Usuarios y Roles
        └── Parámetros del Sistema
```

---

### 3. Diferenciación de acceso según roles

#### Matriz de acceso por rol
| Funcionalidad | Ciudadano | Funcionario | Administrador |
| :--- | :---: | :---: | :---: |
| Registrar reclamo / solicitud | ✅ | - | - |
| Consultar estado de reclamos propios | ✅ | - | - |
| Gestionar y responder reclamos asignados | - | ✅ | - |
| Supervisar todas las unidades y reportes | - | - | ✅ |
| Administrar usuarios y permisos | - | - | ✅ |
| Ingresar nuevo reclamo / solicitud | ✓ | — | — |
| Consultar estado por código de folio | ✓ | ✓ | ✓ |
| Visualizar historial de requerimientos propios | ✓ | — | — |
| Visualizar bandeja general de requerimientos municipales | — | ✓ | ✓ |
| Derivar requerimientos a direcciones técnicas | — | ✓ | — |
| Cargar informes técnicos y redactar respuesta oficial | — | ✓ | — |
| Monitorear semáforo de plazos legales (20 días) | — | ✓ | ✓ |
| Crear y gestionar cuentas de funcionarios | — | — | ✓ |
| Configurar unidades municipales y categorías | — | — | ✓ |

#### Acceso del Ciudadano
Tendrá acceso a las funcionalidades vinculadas a la presentación y seguimiento de sus requerimientos.
* **Podrá:** Completar el formulario de ingreso, adjuntar fotos/ubicación, consultar el estado de sus trámites, descargar respuestas oficiales y actualizar sus datos de contacto.
* **No podrá:** Acceder a bandejas internas de funcionarios, visualizar solicitudes privadas de otros vecinos ni modificar registros municipales.

#### Acceso del Funcionario
Tendrá acceso a las herramientas operativas de gestión y resolución de solicitudes asignadas a su dependencia.
* **Podrá:** Revisar solicitudes, derivar expedientes a otras unidades, adjuntar informes técnicos y emitir respuestas oficiales que cierren el trámite.
* **No podrá:** Alterar configuraciones globales de la plataforma ni gestionar permisos de otros usuarios.

#### Acceso del Administrador
Será el responsable de la gestión y supervisión general de la plataforma.
* **Podrá:** Crear usuarios funcionarios, asignarles roles y unidades técnicas, supervisar auditorías de plazos y modificar parámetros generales del sistema.
* **No tendrá como función:** La resolución técnica cotidiana de los reclamos vecinales.

#### Control de acceso a rutas
```text
/login
/registro
/consulta-folio

/ciudadano/inicio
/ciudadano/reclamos/nuevo
/ciudadano/mis-reclamos
/ciudadano/reclamos/:id
/ciudadano/perfil

/funcionario/inicio
/funcionario/bandeja
/funcionario/reclamos/:id/atender

/admin/inicio
/admin/usuarios
/admin/configuracion
```

---

## 5. Flujos de Tareas (Task Flows)
### 4. Flujos de Tareas (Task Flows)

### Task Flow 1: Registro y seguimiento de reclamo
* **Rol:** Ciudadano
* **Secuencia:** 
  Inicio de sesión -> Menú principal -> Seleccionar "Nuevo Reclamo" -> Ingresar categoría, descripción y ubicación -> Adjuntar evidencia fotográfica -> Enviar solicitud -> Obtener folio único -> Visualizar seguimiento en la lista de reclamos.
#### Task Flow 1: Ingreso de requerimiento y consulta de estado (Rol: Ciudadano)
```text
Inicio de sesión o acceso como vecino
        ↓
Inicio del ciudadano
        ↓
Seleccionar "Nuevo Requerimiento"
        ↓
Ingresar tipo (reclamo, consulta, sugerencia) y temática
        ↓
Describir situación y adjuntar ubicación/evidencia
        ↓
Revisar resumen de la solicitud
        ↓
¿Datos completos y válidos?
        ↓                       ↓
       No                       Sí
        ↓                       ↓
Mostrar alertas          Registrar solicitud
de validación                   ↓
                         Generar código de folio único
                                ↓
                         Mostrar pantalla de confirmación con folio
                                ↓
                         Redirigir a "Mis Reclamos" con estado "Enviado"
```

### Task Flow 2: Gestión y resolución de reclamos
* **Rol:** Funcionario
* **Secuencia:** 
  Inicio de sesión -> Panel de gestión -> Filtrar reclamos pendientes por dirección/departamento -> Seleccionar reclamo -> Redactar respuesta u oficio técnico -> Cambiar estado a "Resuelto" -> Guardar cambios -> Envío automático de notificación al ciudadano.
#### Task Flow 2: Gestión, derivación y respuesta oficial de requerimiento (Rol: Funcionario)
```text
Inicio de sesión del funcionario
        ↓
Panel de control OIRS
        ↓
Acceder a "Bandeja de Reclamos"
        ↓
Filtrar por reclamos pendientes / próximos a vencer (plazo 20 días)
        ↓
Seleccionar requerimiento a gestionar
        ↓
Revisar antecedentes y evidencias del ciudadano
        ↓
¿Corresponde a su unidad técnica?
        ↓                               ↓
       No                               Sí
        ↓                               ↓
Derivar a unidad competente      Elaborar informe técnico / respuesta
        ↓                               ↓
Actualizar estado a "Derivado"   ¿Requiere prórroga legal (10 días)?
                                        ↓                 ↓
                                       Sí                 No
                                        ↓                 ↓
                               Registrar prórroga   Redactar respuesta
                               y notificar vecino          ↓
                                                    Cambiar a "Resuelto"
                                                           ↓
                                                    Notificar al ciudadano
```

---

## 6. Justificación Técnica y Tecnologías
### 5. Puntos críticos de interacción

### Librerías y Frameworks Principales
* **Frontend:** Ionic Framework (v7+) con React, TypeScript y TailwindCSS para garantizar una interfaz adaptable (responsive) tanto en dispositivos móviles como en escritorio.
* **Backend:** Node.js con Express y base de datos relacional (PostgreSQL) para asegurar la integridad de los expedientes electrónicos y el control estricto de los plazos legales estipulados por la normativa OIRS (20 días corridos).
1. **Autenticación y direccionamiento seguro por rol:** El sistema deberá verificar inmediatamente el rol del usuario autenticado y redirigirlo a su respectivo módulo, impidiendo el acceso forzado a URLs internas mediante navegación directa.
2. **Ingreso y validación de evidencias multimedia:** Al subir fotografías del incidente (ej. microbasurales, baches) desde dispositivos móviles, la interfaz no debe congelarse. Debe existir validación de formatos (JPG, PNG, PDF) y compresión previa para optimizar la carga en conexiones móviles.
3. **Generación y resguardo del código de folio único:** El folio debe mostrarse de manera destacada al finalizar el envío y enviarse de inmediato por correo electrónico o mensaje al vecino, evitando que el usuario pierda el comprobante ante un cierre accidental de la aplicación.
4. **Alerta visual y control estricto de plazos legales (20 días corridos):** La bandeja del funcionario debe contar con indicadores visuales (semáforo verde, amarillo y rojo) para advertir la cercanía del vencimiento legal estipulado en la ordenanza (Art. 42 y 45), evitando sanciones administrativas.
5. **Claridad en la visualización del estado del expediente:** El ciudadano debe comprender exactamente en qué etapa se encuentra su solicitud (Enviado -> En Revisión -> Derivado a Unidad Técnica -> En Ejecución -> Respondido) sin terminología burocrática ambigua.
6. **Consistencia en la transición Web/Móvil:** La disposición de los controles principales (formulario de ingreso y seguimiento) debe mantenerse intuitiva tanto si el vecino utiliza la app en un teléfono inteligente en la calle como si consulta desde un computador de escritorio.

### Tabla de Tecnologías
| Librería / Herramienta | Propósito |
---

### 6. Justificación Técnica

#### Usabilidad
Se implementa una estructura de navegación simple, predecible y jerarquizada. Para el ciudadano se minimiza el esfuerzo de registro mediante un formulario en etapas con asistencia visual. Para el funcionario se prioriza una interfaz tipo tablero con filtros rápidos para agilizar la gestión diaria.

#### Eficiencia de interacción
Las acciones más críticas (ingresar reclamo y consultar folio) son accesibles en menos de 2 clics desde la pantalla de inicio. Se elimina el reingreso de datos mediante el almacenamiento seguro del perfil del usuario.

#### Claridad estructural
La separación de vistas públicas y protegidas por rol asegura un desacoplamiento claro entre la experiencia del vecino y los procesos internos de la administración municipal.

---

## 5. Bocetos UX/UI

* [Figma - Prototipo interactivo UI/UX de la Plataforma OIRS](https://www.figma.com/) *(reemplazar por el enlace a su prototipo en Figma)*

---

## 6. Frontend con Ionic-React

### Librerías usadas con React (Ionic)
* **TailwindCSS:** Utilizado para utilidades de diseño rápido, estilos personalizados y soporte de componentes adaptativos.

### Librerías principales
| Librería | Propósito |
| :--- | :--- |
| `react` | Construcción de la interfaz mediante componentes modulares. |
| `react-router-dom` | Gestión y enrutamiento entre las diferentes vistas de la plataforma. |
| `@ionic/react` | Componentes nativos y adaptativos de Ionic para web y móvil. |
| `ionicons` | Biblioteca de iconos estandarizada. |
| `TailwindCSS` | Estilizado rápido y diseño adaptable. |
| `react` | Biblioteca principal para la construcción de interfaces mediante componentes. |
| `react-dom` | Renderizado de componentes React en el entorno web. |
| `@ionic/react` | Proporciona los componentes de interfaz nativos y web (`IonPage`, `IonContent`, `IonHeader`, `IonCard`, `IonButton`, `IonInput`, etc.). |
| `@ionic/react-router` | Integración de los componentes de navegación de Ionic con React Router. |
| `react-router-dom` | Definición y gestión de rutas dinámicas y protegidas de la aplicación. |
| `ionicons` | Paquete oficial de iconos SVG para Ionic. |

### Tecnologías
* **Ionic Framework (v7+)**
* **React**
* **TypeScript**
* **Capacitor** (para soporte de funcionalidades nativas en dispositivos móviles, tales como cámara y geolocalización, si aplica)
