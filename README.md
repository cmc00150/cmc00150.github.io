<div align="center">

# 🔌 ESP32-WROOM-32 · Pinout interactivo

### y simulador del circuito interno de un GPIO


**Entiende qué hace cada pin del ESP32 y qué hay dentro de un GPIO, de forma visual y didáctica.**

</div>

---

## 📑 Índice

- [✨ Qué es](#-qué-es)
- [🗺️ Vista de pinout](#️-vista-de-pinout)
- [🔬 Vista de circuito interno](#-vista-de-circuito-interno)
- [⚡ Simulación eléctrica](#-simulación-eléctrica)
- [📐 Modelo y datos](#-modelo-y-datos)
- [🚀 Cómo usarlo](#-cómo-usarlo)
- [🛠️ Detalles técnicos](#️-detalles-técnicos)

---

## ✨ Qué es

Una página web **de un solo archivo HTML**, sin build ni dependencias, con dos vistas:

| | Vista | Para qué sirve |
|---|---|---|
| 🗺️ | **Pinout** | Ver la placa, filtrar pines por grupos y consultar las funciones de cada uno |
| 🔬 | **Circuito interno** | Ver y manipular el circuito real del GPIO elegido, con zoom y simulación |

> [!TIP]
> Pasa el cursor sobre un pin y pulsa <kbd>Ctrl</kbd> + <kbd>clic</kbd> para saltar de una vista a otra.

---

## 🗺️ Vista de pinout

- 📍 **Pinout central** de la placa DevKitC de 38 pines.
- 🏷️ **Badges de grupo**: selecciona uno o varios y los pines correspondientes se marcan (GPIO, ADC, DAC, touch, PWM, UART, I²C, SPI, RTC, strapping, solo entrada, flash, alimentación…).
- 💬 **Ficha al pasar el cursor** con la información concreta del pin y todas sus funciones.
- ⌨️ **Atajo**: <kbd>Ctrl</kbd> + <kbd>clic</kbd> (o <kbd>Cmd</kbd> + clic en Mac) abre el circuito interno. También sirve el botón «Ver circuito interno →» al fijar la ficha.
- 📖 Sección **«Cómo leer el pinout»** con la leyenda de colores y símbolos.
- 🌗 Tema **claro y oscuro** automático.

---

## 🔬 Vista de circuito interno

Se entra con una transición de zoom desde el pinout y se puede cambiar de pin sin volver atrás.

### 🎨 Lienzo

- 🖱️ Esquema SVG a pantalla completa con **arrastre, rueda, pellizco y teclas** <kbd>+</kbd> / <kbd>−</kbd>.
- 🔍 Zoom nítido: el SVG se redimensiona, no se escala como imagen.
- 📦 Cabecera plegable con la descripción del pin y el código equivalente (`pinMode`, `digitalWrite`, `digitalRead`…).
- 🧭 Leyenda plegable de colores y tipos de línea.
- 🧩 **Cada GPIO tiene su propio esquema**: solo entrada (34–39), strapping, RTC, flash… no son todos iguales.

### 🎛️ Configuración del pin

| Opción | Detalle |
|---|---|
| ⬅️ **Entrada** | Activable de forma independiente |
| ➡️ **Salida** | Push-pull o colector abierto |
| 🔁 **Entrada + salida** | Ambas a la vez (`GPIO_MODE_INPUT_OUTPUT`) |
| ⛔ **Desactivado** | `GPIO_MODE_DISABLE` |
| ⬆️⬇️ **Pull-up / pull-down** | Independientes de la dirección, dibujados como transistores P-MOS y N-MOS que se encienden y apagan |

### 🧰 Funciones especiales

Cada una abre una **ventana flotante y minimizable** con sus parámetros y su gráfica:

- 〰️ **PWM**: forma de onda con frecuencia y ciclo de trabajo
- 📈 **ADC** y 📉 **DAC**
- 👆 **Touch**
- 💤 **RTC**
- 🔄 **UART**
- 🥾 **BOOT / strapping**

> [!NOTE]
> Los valores numéricos se escriben a mano con prefijos SI: `4k7`, `330`, `1µ`…

---

## ⚡ Simulación eléctrica

- 🧮 **Solver nodal** (bisección) que calcula la tensión del pin y la corriente de cada rama.
- 📊 **Barra de tensión vertical** con lectura digital (0 / 1 / indeterminado) y marcador.
- 🔌 Panel **«Tensión y corriente»** para conectar al pin:

  | Componente | |
  |---|---|
  | Nada (pin flotante) | ⚪ |
  | Fuente de tensión | 🔋 |
  | Fuente de corriente | ➡️ |
  | LED a GND | 💡 |
  | LED desde 3,3 V | 💡 |

  …con resistencia en serie y presets.
- 🌊 **Flujo animado** de corriente y señales lógicas.
- 📋 Tabla de **corrientes por rama**.
- 💬 Mensajes que explican el estado, por ejemplo por qué un pull-up lee 0 con una fuente de 0 V y 330 Ω.

### 🚨 Detección de daños

| Estado | Significado |
|---|---|
| 🟢 Normal | Dentro de los límites |
| 🟡 Al límite | Cerca del máximo admisible |
| 🔴 Se daña | Sobretensión o corriente excesiva por diodos de protección o transistores |

> [!IMPORTANT]
> Los avisos de fallo se mantienen visibles aunque cierres el menú.

---

## 📐 Modelo y datos

| Elemento | Valor didáctico |
|---|---|
| P-MOS | ≈ 40 Ω |
| N-MOS | ≈ 30 Ω |
| Pull-up / pull-down | ≈ 45 kΩ |
| Diodos de protección | 0,6 V |
| Corriente por pin | 20 mA recomendados · ~40 mA máximo |

> [!WARNING]
> Son valores **orientativos**. No sustituyen al datasheet del ESP32 ni al manual de referencia de Espressif.

---

## 🚀 Cómo usarlo

No hay nada que instalar. Descargalo y abrelo con el mismo navegador o visita la página de GitHub Pages.

---

## 🛠️ Detalles técnicos

- 📄 Un único `.html` con HTML, CSS y JS embebidos, sin frameworks.
- 🔤 Solo se cargan las fuentes **Archivo** y **JetBrains Mono** (Google Fonts); funciona igual si no cargan.
- 🎨 Colores con tokens `oklch` y temas claro y oscuro.
- 📱 Responsive y manejable con teclado, con atributos ARIA.
- 
---

<div align="center">

📚 Material con fines educativos. Comprueba siempre los límites eléctricos en la documentación oficial de Espressif antes de conectar hardware.

</div>
