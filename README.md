# sincronia-canchas-LT
Primeros pasos de desarrollo de web para una sincronia completa en el flujo de trabajo existente actualmente en los muros de contencion del tranque Las Tortolas perteneciente a AngloAmerican, donde se involucra Besalco, Linkapsis, LlayLlay.


flowchart TD
    AA[AngloAmerican (Mandante)] -->|Solicita cancha| BES[Besalco (Maquinarias)]
    BES -->|Trabaja cancha (compacta, estira, corta, rellena)| LIN[Linkapsis (Topografía)]
    LIN -->|Valida espesores| LINCheck{¿Espesores OK?}
    LINCheck -- Sí --> LLA[LlayLlay (Laboratorio)]
    LINCheck -- No --> BES
    LLA -->|Muestra densidad| LLAValida{¿Densidad OK?}
    LLAValida -- Sí --> AA
    LLAValida -- No --> BES
    AA -->|Firma y cierra cancha| END[Cancha cerrada]
