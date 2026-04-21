# Desuperheater CFD Simulation — Co-Current vs. Counter-Current Flow

Transient DPM Evaporation Study using ANSYS Fluent 2026 R1

---

## Overview

This repository contains CFD simulation reports and results for a **desuperheater** modeled in two flow configurations:

- **Co-Current Flow** — spray injected in the same direction as steam (+Y)
- **Counter-Current Flow** — spray injected opposing the steam flow (–Y steam, +Y spray)

The study uses the **Discrete Phase Model (DPM)** with two-way coupling, Rosin-Rammler droplet size distribution, and cone injection to simulate water spray cooling of superheated steam at 10 bar operating pressure.

---

## Repository Contents

```
├── Co_Current_Flow_Report.docx       # Full simulation report — co-current configuration
├── Counter_Current_Flow_Report.docx  # Full simulation report — counter-current configuration
└── README.md
```

---

## Geometry

| Parameter | Value |
|---|---|
| Main Pipe OD | Ø219 mm |
| Main Pipe ID | Ø166.3 mm |
| Main Pipe Length | 1376 mm |
| Nozzle Pipe OD | Ø88.9 mm |
| Nozzle Exit Diameter | 8 mm |
| Water Inlet Diameter | 28.4 mm |
| Torus Ring Centerline Radius | R97.15 mm |
| Torus Ring Tube Radius | R16.7 mm |

Geometry modeled in **ANSYS SpaceClaim**. Mesh generated in **ANSYS Meshing** with local refinement near the nozzle junction to resolve the spray-steam interaction zone.

---
<img width="1528" height="1077" alt="Screenshot 2026-04-21 094530" src="https://github.com/user-attachments/assets/2f44e0cd-ae77-4968-9680-7532752a89c5" />
<img width="1671" height="820" alt="Screenshot 2026-04-21 094448" src="https://github.com/user-attachments/assets/4fee2eaf-1595-4bcc-8e17-52937faee83e" />
<img width="1670" height="823" alt="Screenshot 2026-04-21 094433" src="https://github.com/user-attachments/assets/1caadf69-0cf9-405d-8e1b-0c489a6a2067" />
<img width="1671" height="819" alt="Screenshot 2026-04-21 094421" src="https://github.com/user-attachments/assets/0e1ede4d-deb3-4c19-b923-cd8acec6c09a" />
<img width="1469" height="751" alt="Screenshot 2026-04-21 094759" src="https://github.com/user-attachments/assets/e96b176b-9081-4d70-bb41-cd03d6e089f1" />
<img width="1469" height="755" alt="Screenshot 2026-04-21 094737" src="https://github.com/user-attachments/assets/a96c7092-0dda-4b18-9a71-d83d06f2b80f" />


---

## Physics & Numerical Setup

| Setting | Value |
|---|---|
| Software | ANSYS Fluent 2026 R1 (Student Edition) |
| Solver | Pressure-Based, Coupled, Transient |
| Turbulence Model | SST k-ω |
| Species Model | Species Transport — N₂ + H₂O, Diffusion Energy Source ON |
| DPM | Two-way coupling, Rosin-Rammler distribution |
| Operating Pressure | 1,000,000 Pa (10 bar) |
| Steam Inlet Temperature | 523 K (250°C) |
| Steam Inlet Velocity | 30 m/s |
| Time Step | 0.0002 s × 2,500 steps = 0.5 s total |

### DPM Injection (Cone Type)

| Parameter | Value |
|---|---|
| Injection Type | Cone — Solid Cone |
| Number of Streams | 120 |
| Injection Velocity | 40 m/s |
| Cone Half Angle | 15° |
| Outer Radius | 4 mm |
| Total Flow Rate | 0.1045 kg/s |
| Mean Diameter | 0.025 mm |
| Spread Parameter | 3.5 |

---

## Flow Configurations

### Co-Current Flow
- Steam enters from the **bottom** (+Y direction)
- Spray injected **co-currently** in +Y direction from nozzle at Y = 233 mm
- Steam outlet at the **top**

### Counter-Current Flow
- Steam enters from the **top** (–Y direction)
- Spray injected **counter-currently** in +Y direction (opposing steam)
- Steam outlet at the **bottom**
- All other settings (geometry, mesh, materials, DPM, solver) remain identical to co-current

---

## Results Summary

### Co-Current Flow

| Parameter | Value |
|---|---|
| Outlet Temperature (steady state) | ~508 K (235°C) |
| Temperature Reduction | ~15 K |
| Outlet Velocity (average) | ~29.2 m/s |
| Evaporation Rate (steady state) | ~0.0088 kg/s |
| Evaporation Efficiency | ~8.4% of injected water |
| Pressure Drop | 1,200–2,600 Pa (stable oscillation) |
| Min Temperature in Spray Zone | 434 K |
---
<img width="1289" height="586" alt="residuals" src="https://github.com/user-attachments/assets/4cf7935e-3cb4-454d-b2a6-7c9d43ca2552" />
<img width="1289" height="586" alt="pressure_drop" src="https://github.com/user-attachments/assets/84835024-e3d7-47ae-903f-4ddadbd6f263" />
<img width="1289" height="586" alt="pathlines_velocity_magnitude" src="https://github.com/user-attachments/assets/0509a0df-e492-4da1-a199-094c715fd54f" />
<img width="1289" height="586" alt="pathlines_temp" src="https://github.com/user-attachments/assets/5e16802b-381a-4153-ba3a-01be4b170ccc" />
<img width="1289" height="586" alt="particle_track_velocity_magnitude" src="https://github.com/user-attachments/assets/fbdfc902-2915-4405-a4b5-e1d8cad73253" />
<img width="1289" height="586" alt="particle_track_temp" src="https://github.com/user-attachments/assets/19e7477f-a4f8-4d4d-81e6-c52c8f88fbf1" />
<img width="1289" height="586" alt="particle_track_diameter" src="https://github.com/user-attachments/assets/b0115576-3c26-4a8e-9cc1-7b0146e07ffe" />
<img width="1289" height="586" alt="outlet_velocity" src="https://github.com/user-attachments/assets/791ce8fe-601a-4287-a63a-dd59049368d1" />
<img width="1289" height="586" alt="outlet_temp" src="https://github.com/user-attachments/assets/bf81fc71-c56d-476c-b2a7-26b16ee9b4c6" />
<img width="1289" height="586" alt="outlet_h20" src="https://github.com/user-attachments/assets/eb85c524-692a-41a5-a1e9-24a763104f03" />
<img width="1289" height="586" alt="mesh" src="https://github.com/user-attachments/assets/8e959aa9-2aef-44f5-938a-24a285fcb7e0" />
<img width="1289" height="586" alt="evap_rate" src="https://github.com/user-attachments/assets/994a58b4-7085-44b8-aed8-ac476ea218be" />
<img width="1289" height="586" alt="contour_velocity_magnitude_t" src="https://github.com/user-attachments/assets/ff0c421f-6db7-4061-aabc-bb076c0463e8" />
<img width="1289" height="586" alt="contour_velocity_magnitude_l" src="https://github.com/user-attachments/assets/4cd355b9-e3c2-4a53-97b6-aa2dea3bf55e" />
<img width="1289" height="586" alt="contour_turbulent_K_E_h20_t" src="https://github.com/user-attachments/assets/c596eeba-28aa-454c-b7e4-f96d156d5518" />
<img width="1289" height="586" alt="contour_turbulent_K_E_h20_l" src="https://github.com/user-attachments/assets/fdc47ddc-0403-4c18-bda1-659c777b9dc2" />
<img width="1289" height="586" alt="contour_temp_t" src="https://github.com/user-attachments/assets/50960f96-f274-4f7b-8255-a31dfb96a173" />
<img width="1289" height="586" alt="contour_temp_l" src="https://github.com/user-attachments/assets/25230169-fc05-4e75-bcc1-51157702563d" />
<img width="1289" height="586" alt="contour_pressure_t" src="https://github.com/user-attachments/assets/041eec3d-a0d1-4bfc-a9cd-e2e021b2096b" />
<img width="1289" height="586" alt="contour_pressure_l" src="https://github.com/user-attachments/assets/320b9a9d-e241-4c13-b581-6b533fab1bb2" />
<img width="1289" height="586" alt="contour_mass_fraction_h20_t" src="https://github.com/user-attachments/assets/ee355eef-676e-49db-9a51-66096a035411" />
<img width="1289" height="586" alt="contour_mass_fraction_h20_l" src="https://github.com/user-attachments/assets/5da48e8b-0dff-409b-8a6c-bcbe44744c6b" />


https://github.com/user-attachments/assets/4a798bdd-b449-451c-9713-1282a0cb07ab



https://github.com/user-attachments/assets/182eb4df-58a0-420d-8a26-cc8f9e394f15



https://github.com/user-attachments/assets/d893cb7e-55ac-4d4d-bca6-62e03b40ba27



https://github.com/user-attachments/assets/fcc1cc83-4ae3-4cfc-a166-7ca710fb3991



https://github.com/user-attachments/assets/68edae53-323b-47ee-9ce1-bbd9d6172aed



https://github.com/user-attachments/assets/8316a592-5c7c-4bf6-a993-89e8e30b6974



https://github.com/user-attachments/assets/d946324b-0d3a-4c2c-855d-d10dabe991ab



https://github.com/user-attachments/assets/569cb0b2-f7dc-4143-9df8-ffeb81fb810d



https://github.com/user-attachments/assets/8b6b84fd-74be-4651-8cb2-a4ee81d2aaaa



https://github.com/user-attachments/assets/3489ccf7-44d6-4131-ac03-acb08977cbef



https://github.com/user-attachments/assets/d0b09bd2-0cb3-47e1-91a3-cec02a5ace80



https://github.com/user-attachments/assets/89aa28d6-99b7-4b80-8213-590768029cd6



https://github.com/user-attachments/assets/dc5940e2-b9de-4f37-8c72-6c32694d632f



https://github.com/user-attachments/assets/a3ffe279-ec21-4f9d-b7c9-250dd30762dc




---

### Counter-Current Flow

| Parameter | Value |
|---|---|
| Outlet Temperature (steady state) | ~508–510 K (235–237°C) |
| Temperature Reduction | ~13–15 K |
| Outlet Velocity (steady state) | ~30 m/s |
| Evaporation Rate (steady state) | ~0.0025 kg/s |
| Evaporation Efficiency | ~2.4% of injected water |
| Pressure Drop | ±80,000 Pa initial → settles ~0 Pa |
| Min Temperature in Spray Zone | 364 K |

---


https://github.com/user-attachments/assets/bf7066fe-0314-49ac-b9a2-300b4505b20f



https://github.com/user-attachments/assets/e7e2c6e7-7d42-405b-b4af-a98f476f5822



https://github.com/user-attachments/assets/c65f7eb5-38d7-4eb5-ba7c-2aa7eeaa47c5



https://github.com/user-attachments/assets/e35cc30f-4f4b-44d6-b7d8-2e931c53841d



https://github.com/user-attachments/assets/3bd9e210-7a7e-4388-a8da-de186307f404



https://github.com/user-attachments/assets/74eb0f30-e797-49cf-9c8c-025f70c64984



https://github.com/user-attachments/assets/9f9c7de1-f72b-4f1b-b1a3-86c4a49e30b7



https://github.com/user-attachments/assets/0e814bcc-d6e7-4bd7-ae3d-d4defd711822



https://github.com/user-attachments/assets/a0335446-b475-4a90-a3b9-287ba7b5676d



https://github.com/user-attachments/assets/742dbe2a-8fdc-4661-83e3-dc5b9b4031f0



https://github.com/user-attachments/assets/dec945f3-47a0-48ce-99c7-559bb8cb4ba2



https://github.com/user-attachments/assets/7044a09e-9ac1-465d-aa55-85cb8a763a22



https://github.com/user-attachments/assets/07ed898d-d3dd-427d-b6b5-43f366734a0c



https://github.com/user-attachments/assets/0c516ad2-da8b-4778-9f03-59c3e11e6a62

<img width="1289" height="586" alt="residuals" src="https://github.com/user-attachments/assets/70c4fd9e-3a24-4f40-9205-ca64f8681077" />
<img width="1289" height="586" alt="pressure_drop" src="https://github.com/user-attachments/assets/d0fc916a-f28a-417b-8aca-3e1cc1f302ae" />
<img width="1289" height="586" alt="pathlines_velocity_magnitude" src="https://github.com/user-attachments/assets/ed8b6920-ab0e-4f4a-b1a8-abc681ca2541" />
<img width="1289" height="586" alt="pathlines_temp" src="https://github.com/user-attachments/assets/83b338d1-cd1f-44eb-bd21-1e5c2cd907d8" />
<img width="1289" height="586" alt="particle_track_velocity_magnitude" src="https://github.com/user-attachments/assets/306e1525-f944-47bf-8fe7-f1bb3155675f" />
<img width="1289" height="586" alt="particle_track_temp" src="https://github.com/user-attachments/assets/00233bca-2ada-441f-8bec-865ecdcfe8f2" />
<img width="1289" height="586" alt="particle_track_diameter" src="https://github.com/user-attachments/assets/300c4782-c0e3-46eb-9b18-733b447fb987" />
<img width="1289" height="586" alt="evap_rate" src="https://github.com/user-attachments/assets/ec2555e7-adb8-47bb-9763-e28e4ad1fe9b" />
<img width="1289" height="586" alt="contour_velocity_magnitude_t" src="https://github.com/user-attachments/assets/cfd12ab2-2b6f-4d79-b61d-24f3b0be416e" />
<img width="1289" height="586" alt="contour_velocity_magnitude_l" src="https://github.com/user-attachments/assets/141dfb42-3bb8-4eb2-821a-cb102bb4e8d3" />
<img width="1289" height="586" alt="contour_turbulence_t" src="https://github.com/user-attachments/assets/9934c662-9aeb-43cd-a177-7a5bcc3f616b" />
<img width="1289" height="586" alt="contour_turbulence_l" src="https://github.com/user-attachments/assets/60e189da-dd3b-40fb-b0cc-1be8e319a9ef" />
<img width="1289" height="586" alt="contour_temp_t" src="https://github.com/user-attachments/assets/3d090634-ce5e-4efb-8389-88dd8e34a32e" />
<img width="1289" height="586" alt="contour_temp_l" src="https://github.com/user-attachments/assets/dec67a26-5fba-4fca-8adf-95d16963ff12" />
<img width="1289" height="586" alt="contour_pressure_t" src="https://github.com/user-attachments/assets/ff8d5342-ddce-4835-84c4-60f0db83acf5" />
<img width="1289" height="586" alt="contour_pressure_l" src="https://github.com/user-attachments/assets/84a0f25b-3c5e-4aea-bc57-1dbbe080f06c" />
<img width="1289" height="586" alt="contour_mass_fraction_h2o_t" src="https://github.com/user-attachments/assets/b156e109-4272-477a-bc85-c77da7623859" />
<img width="1289" height="586" alt="contour_mass_fraction_h2o_l" src="https://github.com/user-attachments/assets/9cef971c-5505-42f5-9660-bab637f2ab3f" />
<img width="1289" height="586" alt="outlet_velocity" src="https://github.com/user-attachments/assets/b2e8e5af-044e-481a-8dd9-9eb9943800f3" />
<img width="1289" height="586" alt="outlet_temp" src="https://github.com/user-attachments/assets/1a457635-76d7-40ff-a11f-6b47a37fcf1d" />
<img width="1289" height="586" alt="outlet_h2o" src="https://github.com/user-attachments/assets/7b339b7b-0500-4645-8ea5-122f3f703b2b" />
<img width="1289" height="586" alt="mesh" src="https://github.com/user-attachments/assets/52632c55-98d8-4e12-a322-eb8d67d6f67f" />

---

## Comparative Analysis

| Parameter | Co-Current | Counter-Current |
|---|---|---|
| Steam Flow Direction | Bottom → Top (+Y) | Top → Bottom (–Y) |
| Spray Direction | +Y (same as steam) | +Y (opposing steam) |
| Outlet Temperature | ~508 K | ~508–510 K |
| Temperature Reduction | ~15 K | ~13–15 K |
| Evaporation Rate | ~0.0088 kg/s | ~0.0025 kg/s |
| Evaporation Efficiency | ~8.4% | ~2.4% |
| Spray Penetration | Full pipe length | Bottom ~1/3 of pipe |
| Pressure Drop | 1,200–2,600 Pa (stable) | ±80 kPa initial → ~0 Pa |
| Outlet Velocity Stability | Stable (~29 m/s) | Large oscillations → ~30 m/s |
| Convergence Speed | Fast (~0.03 s) | Slow (~0.3 s) |

---

## Key Findings

1. **Similar outlet temperature, different mechanism** — Both configurations achieve ~508–510 K at the outlet, but through different physical processes. Co-current flow distributes cooling uniformly over the full pipe length, while counter-current flow creates intense but spatially limited local cooling near the nozzle (down to 364 K vs. 434 K).

2. **Co-current evaporation is 3.5× higher** — The co-current configuration achieves an evaporation rate of ~0.0088 kg/s vs. ~0.0025 kg/s in counter-current. Opposing steam flow in counter-current mode reduces droplet residence time and sweeps many droplets out before full evaporation.

3. **Counter-current flow is significantly more unstable** — Pressure oscillations of ±80,000 Pa and velocity oscillations of 0–100 m/s are observed during the first 0.1–0.3 s in counter-current flow, compared to the immediately stable co-current behavior. This reflects head-on momentum exchange between spray and steam.

4. **Spray penetration is limited in counter-current flow** — Droplets remain concentrated in the bottom ~1/3 of the pipe due to opposing steam momentum, unlike co-current flow where spray spreads across the full pipe length.

5. **Co-current is recommended for overall desuperheating** — Higher evaporation efficiency (8.4% vs. 2.4%), better spray distribution, more stable pressure and velocity fields, and faster convergence make co-current the preferred configuration for temperature reduction of steam under these operating conditions.

6. **Counter-current may suit niche applications** — Where intense localized cooling or contained spray zone is needed, counter-current could offer an advantage despite its lower efficiency.

---

## Software & Tools

- **CFD Solver:** ANSYS Fluent 2026 R1 (Student Edition)
- **Geometry:** ANSYS SpaceClaim
- **Meshing:** ANSYS Meshing
- **Models Used:** Discrete Phase Model (DPM), Species Transport, SST k-ω turbulence, Energy equation

---

## Author

**Haris**
B.Tech Mechanical Engineering — VIT-AP University
Specialization: CFD & FEA Simulation (ANSYS Fluent, ANSYS Mechanical)

---

*Simulation Date: 21 April 2026*
