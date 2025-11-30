# RTX 3070 16GB VRAM Upgrade Guide

This guide provides a detailed step-by-step process for upgrading the NVIDIA RTX 3070 graphics card to **16GB of VRAM**. The process involves replacing the existing VRAM modules with **2GB modules** and adjusting hardware straps.

Do **NOT** attempt this mod if you have never soldered before, or are not prepared to lose your GPU! It is recommended to practice SMD Soldering on a burner GPU before working on your actual card. Any old GPU is will be fine as they all have similar VRAM chips and resistors you can practice on. Proceed at your own Risk!

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

- Soldering station
- Hot air gun/Station (adjustable Temperature highly recommened)
- Flux (no-clean)
- Isopropyl alcohol (99%)
- Precision tweezers
- Microscope (highly recommened)
- Thermal paste (Arctic MX-4 or similar)
- Thermal pads (Verify thickness based on the card's design. You maybe could also just reuse the old ones.)

### **Software Tools:**

- **MATS Test Suite** (for VRAM diagnostics)
- **NVFlash** (BIOS backup and flashing)
- Benchmark tools: **FurMark**, **OCCT**, **3DMark**
- Overclocking tools: **MSI Afterburner** or **Firestorm** or Evga Precision X1. Use whichever tools your board supports.

### **Parts:**

- **VRAM Modules**:
  - Samsung **K4ZAF325BM-HC14** (14 Gbps) or **K4ZAF325BM-HC16** (16 Gbps).
  - You might also want to have some spares in case you damage one.
- Heat-resistant tape (Kapton tape or similar)
- Thick metal shield for protecting GPU die during heating (thin sheet from an empty soda can is ideal, but take care not to cut yourself!)

---

## **2. Preparation**

1. Backup the **GPU BIOS** using **NVFlash**.
2. Watch tutorial videos for visual references:
   - [Tutorial 1](https://www.youtube.com/watch?v=EM1UL4GHviU\&t=1s)
   - [Tutorial 2](https://www.youtube.com/watch?v=wh5EeJKUYjk)
3. Ensure a static-free workspace. An antistatic mat is ideal, but if you don't have one make a habit of regularly touching a grounded metal surface such as your computer case (with it plugged in!).
---

## **3. Disassembly**

1. Remove the heatsink and backplate.
2. Note thermal pad placement and thickness. Take **photos** of VRAM module orientation. (Not completely necessary as you can also find out by looking at the triangles on the chip and the pads on the board)
3. Use Kapton or similar heat-resistant tape to cover sensitive components and GPU die.
4. Protect the GPU core with a **thick metal plate** or at least some Aluminium foil to shield it during heating.
5. Protect the capacitors using some additional alumuminum foil.

---

## **4. Removing VRAM Modules**
1. Preheat the Board to around 120 Degrees.
1. Apply **flux** around the VRAM modules.
2. Heat each module using a **heat gun (very risky due to the missing temperature settings)** or **hot air station until solder melts.**
3. Carefully lift off the modules with tweezers.
4. Clean the pads with **isopropyl alcohol**.

---

## **5. Installing New Modules**

1. Align new VRAM modules (**K4ZAF325BM-HC14** or **HC16**) properly based on orientation photos or PCB markings.
2. Place flux on the pads and position the modules.
3. Use the **heat gun** to reflow solder until the modules are securely attached.
4. Verify alignment and connection under magnification.

---

## **6. Soldering Straps** (Soon to be updated)

1. Identify the straps to modify. Refer to the specific tutorial. This is different for every manufacturer, but there are usually four possible configurations. It may take a bit of trial and error to find the correct combination.
2. Move the **resistors** to new positions to match the 16GB configuration.

---

## **7. Cleaning and Reassembly**

1. Clean the entire board with **isopropyl alcohol** to remove flux residue.
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
3. PC Probably crashes after stopping the benchmarks. This is a common problem that is often resolved by changing the power settings for the card to high performance mode (see below).

---

## **9. Troubleshooting**

### **Issue 1: Black Screen After Benchmark**

- **Solution 1:**

  - Open **NVIDIA Control Panel**.
  - Go to **3D Settings** > **Global Settings** > **Power Management Mode**.
  - Set to **Prefer Maximum Performance**.
  
  Some Windows components have a default profile added by Nvidia that overwrites the power settings, and should be changed to avoid random black screens [(Reference)](https://www.youtube.com/watch?v=EwXDcKiLSdg)

  - Go to **3D Settings** > **Program Settings** 
  - Look through every program on the list and scroll down, set the **Power Management Mode** to **Prefer Maximum Performance** or **Use global setting (Prefer Maximum Performance)** if not already. Some programs might have the value set to NVIDIA RECOMMENDED or Adaptive, which could cause random black screens. Examples includes:
    - Windows Explorer
    - Mircosoft Shell Experience Host
    - Windows Lock Screen
    - etc.

  **(Optional)** Disable power saving modes (dynamic P-state) completely [(Reference)](https://www.youtube.com/watch?v=EwXDcKiLSdg)
  
  This will causes higher idle power draw (25% TDP, ~60W verus ~45W with Prefer Maximum Performance) but no longer requires changing individual Application Profiles

  - Open regedit
  - Go to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Class\{4d36e968-e325-11ce-bfc1-08002be10318}\0000`
  - Add a `DWORD32` called `DisableDynamicPstate` and set it to a value of `1`
  - Reboot PC.
  
- **Solution 2:**

  - Open **Firestorm** , **Evga Precision X1**, **MSI Afterburner** or any other software that works with your GPU.
  - Underclock GPU core and VRAM clocks slightly.

### **Issue 3: Stability Issues** (Unknown if this is really needed. Doesn't seem too be necessary to do?)

- Adjust memory timings if using the **HC16 modules**.
- Use stock timings initially, then test higher speeds incrementally.
- Normally this shouldn't be required, but you may find that certain timings may improve stability, and by finding the upper limit of your card you will get more out of your GPU.

---

## **10. Final Notes**

- Ensure proper testing before heavy usage.
- Don't be stupid. If you don't understand a single word from here. Please do NOT touch your GPU. This is an extremely risky modification.
- For Legal reasons, I cannot be held liable for anything in this Guide. Follow at your own risk!

If you run into any issues or have any questions, just email me or open an Issue. \:D
