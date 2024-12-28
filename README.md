# RTX 3070 16GB VRAM Upgrade Guide

This guide provides a detailed step-by-step process for upgrading the NVIDIA RTX 3070 graphics card to **16GB of VRAM**. The process involves replacing the existing VRAM modules with **2GB modules** and adjusting hardware straps. Follow all safety precautions to avoid damaging the GPU.

---

## **Table of Contents**

1. [Tools and Materials](#tools-and-materials)
2. [Preparation](#preparation)
3. [Disassembly](#disassembly)
4. [Removing VRAM Modules](#removing-vram-modules)
5. [Installing New Modules](#installing-new-modules)
6. [Soldering Straps](#soldering-straps)
7. [Cleaning and Reassembly](#cleaning-and-reassembly)
8. [Testing and Verification](#testing-and-verification)
9. [Troubleshooting](#troubleshooting)

---

## **1. Tools and Materials**

### **Hardware Tools:**

- Soldering station (with hot air rework capability)
- Heat gun
- Flux (no-clean)
- Isopropyl alcohol (99%)
- Precision tweezers
- microscope (heavily recommened)
- Thermal paste (Arctic MX-4 or similar. Just use whatever you used for your CPU)
- Thermal pads (verify thickness based on the card's design. You maybe could also just reuse the old ones.)

### **Software Tools:**

- **MATS Test Suite** (for VRAM diagnostics)
- **NVFlash** (BIOS backup and flashing)
- Benchmark tools: **FurMark**, **OCCT**, **3DMark**
- Overclocking tools: **MSI Afterburner** or **Firestorm** or Evga Precision X1. Just use whatever your board supports.

### **Parts:**

- **VRAM Modules**:
  - Samsung **K4ZAF325BM-HC14** (14 Gbps) or **K4ZAF325BM-HC16** (16 Gbps).
  - You might also want to have a spare one ready in case you damage one.
- Heat-resistant tape (Just use whatever you can find. Main Point it that you cover everything irrelevant. Just makes it safer.)
- Thick metal shield (for protecting GPU die during heating) (same as before)

---

## **2. Preparation**

1. Backup the **GPU BIOS** using **NVFlash**.
2. Watch tutorial videos for visual references:
   - [Tutorial 1](https://www.youtube.com/watch?v=EM1UL4GHviU\&t=1s)
   - [Tutorial 2](https://www.youtube.com/watch?v=wh5EeJKUYjk)
3. Ensure a static-free workspace. Probably makes it safer.

---

## **3. Disassembly**

1. Remove the heatsink, and backplate.
2. Note thermal pad placement and thickness. Take **photos** of VRAM module orientation.
3. Use heat-resistant tape to cover sensitive components and GPU die.
4. Protect the GPU core with a **thick metal plate** to shield it during heating.

---

## **4. Removing VRAM Modules**

1. Apply **flux** around the VRAM modules.
2. Heat each module using a **heat gun (very risky due to the missing temperature settings)** or **hot air station until solder melts.**
3. Carefully lift off the modules with tweezers.
4. Clean the pads with **isopropyl alcohol**.

---

## **5. Installing New Modules**

1. Align new VRAM modules (**K4ZAF325BM-HC14** or **HC16**) properly based on orientation photos.
2. Place flux on the pads and position the modules.
3. Use the **heat gun** to reflow solder until the modules are securely attached.
4. Verify alignment and connection under magnification.

---

## **6. Soldering Straps**

1. Identify the straps to modify (refer to the specific tutorial. This is different for every manufactor. I don't know how to find the correct one. Just try around. There are just 4 options available).
2. Move the **resistors** to new positions to match the 16GB configuration.

---

## **7. Cleaning and Reassembly**

1. Clean the entire board with **isopropyl alcohol** to remove residue made from the flux.
2. Reapply thermal paste and pads.
3. Reassemble the heatsink, fans, and backplate.
4. Ensure screws are securely fastened but avoid overtightening.

---

## **8. Testing and Verification**

### **Step 1: Check VRAM Capacity**

- Boot into Windows and open **Task Manager** > **Performance Tab**.
- Verify that **16GB of VRAM** is detected.

### **Step 2: MATS Testing**

- Use **MATS test suite** to check memory integrity and stability.

### **Step 3: Stress Testing**

1. Run **FurMark** to test thermal performance.
2. Use **OCCT VRAM Test** to verify memory stability.
3. PC Probably crashes after stopping the benchmarks. This is the problem we gotta fix.

---

## **9. Troubleshooting**

### **Issue 1: Black Screen After Benchmark**

- **Solution 1:**

  - Open **NVIDIA Control Panel**.
  - Go to **3D Settings** > **Global Settings** > **Power Management Mode**.
  - Set to **Prefer Maximum Performance**.

- **Solution 2:**

  - Open **Firestorm** , **Evga Precision X1**  or MSI Afterburner.
  - Underclock GPU core and VRAM clocks slightly. (TODO: Update this)

### **Issue 3: Stability Issues (Written by ChatGPT. I do NOT know if this an actual issue. But could be tried out)**

- Adjust memory timings if using **HC16 modules**.
- Use stock timings initially, then test higher speeds incrementally.

---

## **10. Final Notes**

- Ensure proper testing before heavy usage.
- Don't be stupid. If you don't understand a single word from here. Please do NOT touch your GPU. This is an extremely risky mod.
- For Legal reasons: I cannot be held liable for anything done in this Guide. Everything is up to your own Risk!

If you got any issue or questions just write me or open a bug. Just don't expect me to know the issue. This is also my first time doing something like this \:D

