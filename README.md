# Proyecto Canchas AngloAmerican

## Resumen
Este proyecto busca digitalizar y transparentar el flujo de trabajo de validación de canchas entre empresas colaboradoras de AngloAmerican, usando tecnologías web modernas (**Astro** como frontend y **Supabase** como backend).

## Diagrama general del proceso entre empresas

```mermaid
flowchart TD
    AA[AngloAmerican (Mandante)] -->|Solicita cancha| BES[Besalco (Maquinarias)]
    BES -->|Trabaja cancha| LIN[Linkapsis (Topografía)]
    LIN -->|Valida espesores| LINCheck{¿Espesores OK?}
    LINCheck -- Sí --> LLA[LlayLlay (Laboratorio)]
    LINCheck -- No --> BES
    LLA -->|Muestra densidad| LLAValida{¿Densidad OK?}
    LLAValida -- Sí --> AA
    LLAValida -- No --> BES
    AA -->|Firma y cierra cancha| END[Cancha cerrada]
```

## Diagrama técnico del flujo de desarrollo web

```mermaid
flowchart TD
    User[Usuario de empresa] -->|Login (Supabase Auth)| WebPanel[Web App (Astro)]
    WebPanel -->|Consulta estado de canchas (Supabase DB)| Supabase[(Supabase)]
    WebPanel -->|Visualiza mapa (Leaflet/MapLibre)| MapComponent[Componente de Mapa]
    WebPanel -->|Realiza acción en proceso (validar, rechazar, firmar)| Supabase
    Supabase -->|Actualiza estado| WebPanel
    WebPanel -->|Notificación/Actualización en tiempo real| User
```

## Tecnologías consideradas

- **Astro**: Framework moderno para frontend, permite crear una web rápida y visual.
- **Supabase**: Backend como servicio, provee autenticación, base de datos (PostgreSQL), y APIs automáticas.
- **Leaflet.js / MapLibre**: Para visualización interactiva de mapas y ubicación de canchas.
- **Control de acceso**: Cada empresa accede sólo a sus procesos y acciones.

## Objetivo

Centralizar el seguimiento y validación del proceso de trabajo de canchas, permitiendo a cada empresa interactuar y validar los hitos, con trazabilidad y visualización en tiempo real sobre el mapa.

---

Este README sirve como contexto inicial. Si el proyecto avanza, aquí se irá documentando el desarrollo, estructura y decisiones técnicas.
