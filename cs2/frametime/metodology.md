# CS2 Frametime Analysis (Linux vs Windows)

## Hypothesis / Research Question
When utilizing a modern mid-range AMD hardware configuration (Ryzen 7 5700X / RX 7600), which operating system and frame cap configuration yields the optimal balance of high average frame rates and minimal micro-stutters?

---

## Methodology & Settings

### Benchmark Scenario
* **Map:** Dust2 with bots in infinite warm-up.
* **Duration:** 120-second frametime log.
* **Frame Caps Tested (`fps_max`):** 0 (Uncapped), 480, 400.

### Advanced Video Settings
* **Resolution:** 1280x960 Stretched Fullscreen (Exclusive on Windows and Windowed on Linux)

| CS2 In-Game Setting Option | Value |
| :--- | :--- |
| **Boost Player Contrast** | Enabled |
| **Anti-Aliasing Mode** | CMAA2 |
| **Global Shadow Quality** | Low |
| **Model / Texture Detail** | Medium |
| **Texture Filtering Mode** | Anisotropic 4x |
| **Shader Detail** | Low |
| **Particle Detail** | Low |
| **Ambient Occlusion** | Disabled |
| **High Dynamic Range (HDR)** | Quality |
| **FidelityFX Super Resolution (FSR)** | Disabled |

---

## Test Environments

### Hardware Specifications
* **CPU:** AMD Ryzen 7 5700X (3.4GHz / 4.6GHz Turbo, 8C/16T, AM4)
* **GPU:** ASUS Dual Radeon RX 7600 V2 8GB GDDR6
* **RAM:** XPG Gammix D10 16GB (2x8GB) DDR4 3200MHz CL16 (XMP Enabled)
* **Storage:** Kingston KC3000 512GB NVMe PCIe 4.0 M.2 SSD
* **Motherboard:** ASUS TUF Gaming B550M-Plus (AMD B550)
* **Cooler:** DeepCool AK400 Air Cooler
* **PSU:** Cooler Master MWE Gold 650W V3 (80 Plus Gold)
* **Case:** Corsair 480T Airflow Mid-Tower ATX

### Linux Environment
* **OS:** Arch Linux
* **Kernel:** 7.0.12-zen1-1-zen (64-bit)
* **Desktop Environment:** KDE Plasma 6.6.5 (Frameworks 6.26.0 / Qt 6.11.1)
* **Display Server:** Wayland (KDE Native Stretched, No Gamescope)
* **Graphics Driver:** Mesa 26.1.2-arch1.1 (RADV)
* **API / Optimization:** Vulkan | Smart Access Memory (SAM) Enabled
* **Capture Tool:** MangoHud
* **Launch Option:** MANGOHUD_CONFIG="output_folder=~/Documents,output_file=cs2,log_duration=120" gamemoderun mangohud %command%

### Windows Environment
* **OS:** Windows 11 Home 25H2 (Build 26200.8655)
* **Graphics Driver:** AMD Adrenalin 26.6.1
* **API / Optimization:** DX11 | HAGS Enabled | Performance Power Plan | SAM Enabled | Game Mode Enabled
* **Capture Tool:** OCAT
* **Launch Option:** -allow_third_party_software

---

## Benchmarking Results

### Linux Performance Data
![](linux.png)

### Windows Performance Data
![](windows.png)

---

