# Síntesis y Control Sonoro en Max/MSP
**Asignatura:** Taller de Interfaces (2026) | Universidad Adolfo Ibáñez  
**Estudiante:** Martín Donoso  
**Profesor:** Jorge Forero  
**Portafolio Web:** [Ver Proyecto Desplegado](https://martindonoso2005-cell.github.io/sintetizador/)  

---

## 1. Descripción Técnica del Sistema
Instrumento multimodal de generación y procesamiento de señal de audio en tiempo real programado en el entorno visual **Max/MSP** (Cycling '74). El parche integra cuatro motores sonoros independientes gobernados desde una interfaz gráfica unificada en *Presentation Mode*:

1. **Piano Tonal:** Generador senoidal (`cycle~`) con conversión de notas MIDI a frecuencia (`mtof`) y envolventes de amplitud dinámica (`line~`).
2. **Síntesis FM (Frecuencia Modulada):** Modulación de fase/frecuencia entre oscilador portador y modulador con escalamiento continuo del índice de modulación.
3. **Síntesis AM (Amplitud Modulada):** Modulación de amplitud mediante multiplicación de señales portadora y moduladora en el dominio analógico digital (`*~`).
4. **Módulo Percusivo (Batería por Ruido):** Síntesis de transientes percusivas mediante generador de ruido blanco (`noise~`), filtros pasabanda interactivos (`filtergraph~` / `biquad~`) y envolventes rápidas de decaimiento.
5. **Reproductor de Muestras:** Módulo de audio grabado (`sfplay~`) con control de volumen por potenciómetro rotatorio (`live.dial`).

---

## 2. Mapa de Controles (Presentation Mode)

La interfaz gráfica en modo presentación distribuye los controles requeridos por la pauta:

| Tipo de Control | Objeto Max | Función en el Parche |
| :--- | :--- | :--- |
| **Bangs / Disparadores** | `button` / `live.button` | • 9 pulsadores visuales asignados a la escala del piano.<br>• 2 disparadores dedicados a golpes percusivos (bombo/caja por ruido filtrado). |
| **Sliders / Faders** | `slider` (con objetos `scale`) | • Control de frecuencia de transportadora y moduladora en FM.<br>• Control del índice de modulación FM.<br>• Ajuste de frecuencias fundamentales en AM. |
| **Toggles / Switches** | `toggle` | • Activación individual del flujo de salida (`dac~`) para cada motor.<br>• Encendido/paro del reproductor de muestras (`sfplay~`). |
| **Visualizadores UI** | `scope~` / `spectroscope~` | • Monitoreo de forma de onda senoidal en tiempo real.<br>• Análisis de respuesta espectral y curvas de ecualización (`filtergraph~`). |

---

## 3. Guía de Interacción y Uso
* **Piano Melódico:** Presionar las teclas del teclado físico **`A`**, **`S`**, **`D`**, **`F`**, **`G`**, **`H`**, **`J`**, **`K`**, **`L`** (detectadas por el objeto `key` en códigos ASCII `97` a `108`), correspondientes a las notas MIDI `60` a `72`.
* **Módulos FM / AM:** Deslizar los faders verticales para alterar la textura tímbrica (armónicos laterales) y encender el switch `toggle` para escuchar la salida.
* **Sección de Batería:** Activar los botones percusivos para disparar ráfagas de ruido con envolvente de 100 ms y manipular los filtros bicuadráticos para cambiar el timbre percusivo.

---

## 4. Registro y Demostración en Video
> Demostración en tiempo real de la respuesta acústica y manipulación de controles en Modo Presentación:

* **Enlace a Demostración:** [Ver video en YouTube / Portafolio Web](https://martindonoso2005-cell.github.io/sintetizador/)

---

## 5. Estructura del Repositorio
```text
├── index.html                     # Despliegue web con ficha técnica y video embebido
├── mi primer sintetizador.maxpat  # Código fuente del parche de Max/MSP (v9.1.5)
└── README.md                      # Documentación técnica y guía de interacción
