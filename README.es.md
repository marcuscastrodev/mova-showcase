<div align="center">

[🇺🇸 English](./README.md) · [🇧🇷 Português](./README.pt-BR.md) · **🇪🇸 Español**

# mova.

### Tus proyectos en movimiento.

**Una plataforma full-stack para clientes, proyectos, tareas, calendario, colaboradores y finanzas.**

Caso de ingeniería de producto de **Marcus Castro** · MOVA, by EMI

[Conocer el producto](#el-producto) · [Decisiones técnicas](#decisiones-de-ingeniería) · [Demo privada](https://mova.agenciaemi.com)

**Next.js 16 · React 19 · TypeScript · Supabase · PostgreSQL · Tailwind CSS 4**

</div>

> **Caso de portafolio, no aplicación de código abierto.** El código de producción es privado. Este repositorio documenta el producto y sus decisiones de ingeniería sin exponer código propietario, credenciales ni datos de clientes. El acceso a la demostración está restringido.

## El problema

Los profesionales independientes y pequeños equipos creativos suelen gestionar clientes, proyectos, plazos, colaboradores y finanzas en distintas herramientas. Esto dificulta conectar tareas, entregables y pagos.

**MOVA centraliza estos flujos en un espacio de trabajo**, orientado a la gestión diaria de empresas de servicios.

## El producto

| Área | Experiencia |
| --- | --- |
| **Panel principal** | Proyectos, clientes, tareas pendientes y atrasadas, agenda y notas |
| **Clientes** | Registros, estados, búsqueda y proyectos relacionados |
| **Proyectos** | Plazos, filtros, clientes, estados y vistas de lista/tablero |
| **Tareas** | Kanban, prioridades, responsables y progreso |
| **Calendario** | Vistas de mes, semana y lista, eventos y zonas horarias |
| **Colaboradores** | Profesionales externos vinculados a proyectos |
| **Finanzas** | Cobros, pagos, liquidaciones parciales, reversiones e historial |

## Galería de interfaces

### 01 — Acceso y registro

Una pantalla de bienvenida con la propuesta de valor y las opciones de autenticación.

![Acceso a MOVA](screenshots/01-sign-in.webp)

### 02 — Panel del espacio de trabajo

Indicadores, tareas priorizadas, agenda y acciones rápidas.

![Panel principal de MOVA](screenshots/02-dashboard.webp)

### 03 — Gestión de proyectos

Búsqueda y filtros por cliente, estado y orden para el trabajo diario.

![Proyectos en MOVA](screenshots/03-projects.webp)

### 04 — Calendario

Vista mensual de eventos y plazos, con alternativas semanal y de lista.

![Calendario de MOVA](screenshots/04-calendar.webp)

## Decisiones de diseño

- Jerarquía: indicadores y acciones antes de las listas detalladas.
- Navegación consistente: menú lateral permanente.
- Acciones rápidas: creación de tareas, proyectos, clientes y eventos.
- Estados claros: avisos visuales de retrasos y etiquetas que complementan el color.
- Contexto visible: espacio de trabajo activo y rol del usuario.

## Características técnicas

- **Arquitectura multiinquilino:** espacios, membresías y autorización por ámbito.
- **Seguridad de datos:** Supabase Auth, PostgreSQL Row Level Security (RLS), funciones y validación en servidor.
- **Finanzas:** liquidaciones parciales, historial, reversiones y prevención de duplicados.
- **Fechas:** separación de plazos, eventos con hora y eventos de día completo, respetando la zona horaria del espacio.
- **Despliegue:** Docker multietapa, Next.js standalone y Render.
- **Pruebas:** TypeScript, pruebas unitarias, Playwright y pgTAP.

## Tecnologías

| Capa | Stack |
| --- | --- |
| Frontend | Next.js 16, React 19, TypeScript, Tailwind CSS 4 |
| Backend | App Router, Server Components, Server Actions, Supabase |
| Base de datos | PostgreSQL 17, migraciones SQL, RLS, RPCs y triggers |
| Autenticación | Supabase Auth y acceso HTTP Basic para la demo |
| Calidad | Playwright, pruebas unitarias, pgTAP |
| Entrega | GitHub, Docker, Render |

## Arquitectura

```text
Navegador → Render HTTPS + acceso HTTP Basic
          → Next.js (App Router y Server Actions)
          → Sesión Supabase Auth
          → PostgreSQL / RLS / funciones
          → Datos aislados por espacio de trabajo
```

La autorización se aplica también en la base de datos, independientemente de los controles visibles.

## Decisiones de ingeniería

**01 — Aislamiento entre clientes:** membresías y roles con RLS y comprobaciones del servidor.

**02 — Historial financiero:** las liquidaciones parciales y reversiones conservan los movimientos en lugar de sobrescribir únicamente un saldo.

**03 — Fechas y zonas horarias:** plazos, reuniones y eventos de día completo requieren semánticas diferentes.

**04 — Demo privada:** entorno separado con datos ficticios y acceso restringido.

## Demostración

**[mova.agenciaemi.com](https://mova.agenciaemi.com)** · Acceso privado bajo solicitud.

Es un prototipo activo, no un SaaS lanzado al público.

## Documentación

- [Arquitectura](docs/architecture.md)
- [Funciones](docs/features.md)
- [Notas técnicas](docs/engineering.md)
- [Hoja de ruta](docs/roadmap.md)
- [Galería](screenshots/README.md)

## Mi papel

Requisitos de producto, UX/UI, desarrollo full-stack, modelado de datos, autorización, pruebas, despliegue y documentación.

## Estado y próximos pasos

La demo cubre panel principal, clientes, proyectos, tareas, calendario, colaboradores y finanzas. Próximos pasos: onboarding, colaboración, informes y preparación para producción.

---

**[Marcus Castro](https://github.com/marcuscastrodev)** · Desarrollo web e ingeniería de producto
