# DIY-LMD-Drive // Beltless Linear Magnetic Motor System

[![Part of Relux-9X](https://shields.io)](https://github.com/TMcTrain-TechLab/Relux-9X) ; 
[![YouTube](https://shields.io)](https://www.youtube.com/@TMcTrainTechLab) ; 
[![SimpleFOC](https://shields.io)](https://simplefoc.com) ; 
[![Firmware](https://shields.io)](https://klipper3d.org) ; 
[![License: GPL v3](https://shields.io)](https://gnu.org)

> **Zero belts. Zero backlash. Instantaneous electromagnetic thrust.**

**DIY-LMD-Drive** is an open-source, flat-track Linear Magnetic Drive engineered as the primary X/Y motion system for the [Relux-9X](https://github.com/TMcTrain-TechLab/Relux-9X) autonomous 3D printing cell. Designed to mount directly onto standard `2040` aluminum extrusions and lightweight carbon-fiber gantries, it replaces mechanical belts and lead screws with custom-wound 3-phase copper coils gliding over a Halbach permanent magnet array.

---

## ⚙️ Hardware & Control Architecture

* **Halbach Permanent Magnet Track:** Constructed from `15 × 4 × 4 mm` Neodymium `45M` block magnets (`Q-15-04-04-MN`, rated up to 100 °C for heated chambers). Arranged in a 90° rotating Halbach pattern with an **8 mm pole-to-pole pitch** (120 magnets per 480 mm rail) to focus magnetic flux toward the coils while canceling stray fields toward the frame.
* **Custom 3-Phase Coil Stator (Moving Forcer):** Hand-wound enameled copper coils mounted to an asymmetrical carriage bracket, maintaining a tightly controlled air-gap parallel to the magnet track.
* **FOC Motor Driver:** Powered by the **STMicroelectronics `B-G431B-ESC1`** running **SimpleFOC** for closed-loop Field-Oriented Control, low-side phase current sensing, and active stall/docking force limiting.
* **Klipper Step/Dir Bridge:** Uses a standard 32-bit 3D printer MCU (`STM32`) to translate Klipper's real-time `STEP` and `DIR` pulses directly into SimpleFOC position targets.
* **Linear Guidance & EMI-Shielded Feedback:** Guided by `MGN12H` (Y-axis) and dual `MGN12C` (X-axis) linear rails. Position feedback uses a compact magnetic linear encoder nested in a separate extrusion slot to isolate the readhead from LMD flux saturation.

---

## 🚀 Development Roadmap

- [x] **Hardware Selection:** `B-G431B-ESC1` driver acquisition & Halbach magnet sizing (`480 mm` track).
- [ ] **Stage 1 (Bench Testbed):** Halbach array assembly on a `2040` profile, magnetic flux verification, and first open/closed-loop motion test (*"And it moves!"*).
- [ ] **Stage 2 (Closed-Loop Tuning):** Staggered magnetic encoder tape integration, PID tuning, and high-acceleration velocity profiling.
- [ ] **Stage 3 (Carbon X-Gantry):** Lightweight dual-rail `MGN12C` carbon-fiber beam integration for the [Relux-9X](https://github.com/TMcTrain-TechLab/Relux-9X) with [Relux-TC](https://github.com/TMcTrain-TechLab/Relux-TC) toolchanger.

---

## 📂 Repository Structure

*(Files, coil winding calculators, and firmware configs will be uploaded as each stage is verified)*

```text
├── CAD/                 # Halbach magnet track holders, assembly jigs, winding bobbins & carriage brackets
├── Firmware/            # SimpleFOC Arduino/PlatformIO sketches for B-G431B-ESC1
├── Klipper/             # Step/Dir bridge pinouts, printer.cfg sections & acceleration test macros
└── BOM/                 # Magnets, enameled copper wire gauges, magnetic encoder & PSU specifications
```

---

## ⚠️ Safety Notice

* **Strong Magnetic Fields:** Assembling a Halbach array requires forcing neodymium magnets against strong repelling forces. Always wear protective gloves, eye protection, and use mechanical assembly jigs to prevent magnets from snapping together and shattering.
* **High Currents & Thermal Limits:** Monitor coil temperatures during initial PID tuning to avoid exceeding the thermal rating of the wire enamel or the `100 °C` Curie limit of the `45M` magnets.

---

## 📜 License & Contact

This project is open-source and licensed under the **GNU General Public License v3.0 (GPL-3.0)** — see the [LICENSE](LICENSE) file for details.

* **YouTube:** [TMcTrain TechLab](https://www.youtube.com/@TMcTrainTechLab)
* **Discord:** `@TMcTrain`
* **Business & Sponsorship Inquiries:** `tmctrain.techlab@gmail.com`
