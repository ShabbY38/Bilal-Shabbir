# Hair Dryer Design, Mold Simulation & CNC Prep (DFM/CAE/CAM)

This project covers the full engineering workflow for a domestic hair dryer shell—taking it from a 3D CAD model, testing how it molds in a simulation, and setting up the actual CNC toolpaths to machine the mold block. 

---

## 🛠️ Design Choices & Rules I Followed
I modeled the 3D housing in **PTC Creo Parametric**, making sure it strictly followed real-world injection molding rules:
* **Wall Thickness:** Kept the entire plastic shell at a steady $3\text{ mm}$ thickness. This ensures the part is strong enough but won't get ugly sink marks as it cools down.
* **Draft Angles:** Added at least a $1^\circ$ draft angle to all vertical faces. Without this, the part would get stuck or scratched up when trying to eject it from the mold core.
* **Airflow Shape:** Looked at a couple of different layout options and chose an aerodynamic curvature to handle high-pressure airflow zones smoothly.

---

## 🧪 Simulation & Tweaking the Mold
To catch manufacturing defects before actually cutting any metal, I ran the cavity design through **Creo Mold Analysis (CMA)** and **ANSYS**:
* **The Issue:** My first design only used a single gate to inject the plastic. The simulation showed really high injection pressures and bad air traps right inside the structural ribs, meaning the part wouldn't mold properly.
* **The Fix:** I went back and redesigned the runner system to use **three gates** instead. This completely fixed the flow front, lowered the shrinking issues, and pushed the remaining air traps out to the edges where the mold can safely vent.

---

## ⚙️ Machining & Manufacturing Setup (CAM)
Once the mold geometry was locked in, I set up the full manufacturing assembly to prepare it for the workshop:
* **Tooling Layout:** Modeled the two-part injection mold block, including the core and cavity inserts, core pins, and a parting line that follows the curvy split-line of the hair dryer.
* **CNC Pathing:** Generated the 3-axis CNC toolpaths inside Creo NC for the roughing and finishing cuts on the mold cavity block.
* **Feeds & Speeds:** Calculated and set the proper cutting parameters (running at $2000\text{ RPM}$) to export functional G-code (`.tap` files) ready for a CNC mill.

---

## 📂 What's Inside the Folders
* **`01_CAD_Models/`** - My Creo part (`.prt`) and assembly (`.asm`) files for the hair dryer, mold blocks, and raw workpieces.
* **`02_CAE_Simulation/`** - Mold flow analysis data (`.xedz`), log summaries, and material info.
* **`03_CAM_Manufacturing/`** - My milling setups, cutter location data (`.ncl`), and the final post-processed G-code (`.tap`).
* **`04_Drawings_Reports/`** - Ready-to-print 2D manufacturing drawings with proper title blocks and my final uni project report.
