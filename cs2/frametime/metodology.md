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
* **Resolution:** 1280x960 Stretched Fullscreen

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
* **RAM:** XPG Gammix D10 16GB (2x8GB) DDR4 3200MHz CL16
* **Storage:** Kingston KC3000 512GB NVMe PCIe 4.0 M.2 SSD
* **Motherboard:** ASUS TUF Gaming B550M-Plus (AMD B550)
* **Cooler:** DeepCool AK400 Air Cooler
* **PSU:** Cooler Master MWE Gold 650W V3 (80 Plus Gold)
* **Case:** Corsair 480T Airflow Mid-Tower ATX

### Linux Environment
* **OS:** Arch Linux
* **Kernel:** 7.0.11-arch1-1 (64-bit)
* **Desktop Environment:** KDE Plasma 6.6.5 (Frameworks 6.26.0 / Qt 6.11.1)
* **Display Server:** Wayland (KDE Native Stretched, No Gamescope)
* **Graphics Driver:** Mesa 26.1.2-arch1.1 (RADV)
* **API / Optimization:** Vulkan | Smart Access Memory (SAM) Enabled
* **Capture Tool:** MangoHud
* **Launch Option:** gamemoderun %command%

### Windows Environment
* **OS:** Windows 11 Home 25H2 (Build 26200.8655)
* **Graphics Driver:** AMD Adrenalin 26.6.1
* **API / Optimization:** DX11 | HAGS Enabled | Performance Power Plan | SAM Enabled | Game Mode Enabled
* **Capture Tool:** OCAT
* **Launch Option:** none

---

## Benchmarking Results

### Linux Performance Data
![](linux.png)

### Windows Performance Data
![](windows.png)

---

## Conclusion

After analyzing the 120-second frametime logs across both operating systems and frame rate caps, **Windows with `fps_max 480`** emerges as the most balanced configuration for this hardware setup (Ryzen 7 5700X / RX 7600). 

While Linux Uncapped (`0`) achieves the absolute highest raw performance with an average of 402.40 FPS, it comes at the cost of the highest frame variance, as evidenced by its elevated Standard Deviation (160.82). This high STDEV indicates less consistent frame delivery, which matches the visible micro-stutters reflected in its lower 0.1% lows. 

Conversely, capping the frame rate to 480 FPS on Windows strikes the perfect statistical balance. It sacrifices a negligible amount of average performance (~20 FPS) but stabilizes frame pacing significantly. This configuration yields a much tighter Standard Deviation (150.92) compared to the uncapped runs while simultaneously securing the highest 0.1% lows (126.25 FPS). This mathematical consistency guarantees excellent competitive responsiveness with minimal frame-to-frame pacing spikes during intense gameplay.

### Scenario Ranking (Best to Worst Balance)

1. **Windows - `fps_max 480`** (Score: 10/10)  
   * **Why:** The ideal sweet spot. It pairs exceptional 0.1% lows (126.25 FPS) with a controlled standard deviation (150.92), ensuring smooth frame delivery without severely throttling your hardware's potential (376.20 FPS average).
2. **Linux - `fps_max 0` (Uncapped)** (Score: 9/10)  
   * **Why:** Delivers the absolute highest raw performance (402.40 FPS average) and the best 1% lows (159.56 FPS). It takes second place because it suffers from the worst frame-to-frame instability, holding the highest STDEV (160.82) in the entire test.
3. **Windows - `fps_max 0` (Uncapped)** (Score: 8.5/10)  
   * **Why:** Extremely competitive raw performance (395.61 FPS average) paired with great 0.1% lows (126.17 FPS). Its STDEV (151.10) is solid, but it remains slightly less consistent than its capped 480 counterpart.
4. **Linux - `fps_max 480`** (Score: 7.5/10)  
   * **Why:** Respectable average performance (351.35 FPS) and a decent STDEV baseline (151.63), but it experiences a sharper drop-off in 1% and 0.1% lows compared to Windows at the same cap.
5. **Windows - `fps_max 400`** (Score: 6.5/10)  
   * **Why:** Offers the lowest standard deviation (136.21) across all tests, making it the most mathematically stable configuration. However, it ranks lower because it chokes overall performance too aggressively, dropping average frame rates down to 324.15 FPS.
6. **Linux - `fps_max 400`** (Score: 5/10)  
   * **Why:** The weakest baseline overall. While it offers a relatively low STDEV (140.75), it aggressively restricts average performance (318.81 FPS) without providing any stability or percentile advantages over the equivalent Windows setup.
