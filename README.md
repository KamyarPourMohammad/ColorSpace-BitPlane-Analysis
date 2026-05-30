# Image Processing First Assignment

 
**Date:** May 2026

---

## Introduction

In every part of the world, human beings are willing to extract data from one to many single images. They would certainly be grateful if someone creates and trains a **ROBOT** or a model responsible for this duty.

In this assignment, I implement code and answer questions related to **HSV color space analysis** and **bit-plane slicing**.

---

## Part 1: HSV Color Space Analysis

I converted the given image to HSV color space and split the channels into H, S, and V.

### Why are saturated (thick/colorful) parts brighter in the S channel?

| Saturation Level | S Channel Value | Appearance |
|------------------|----------------|-------------|
| High (colorful) | High pixel value | **BRIGHTER** |
| Low (pale) | Low pixel value | **DARKER** |
| Zero (black/white/gray) | 0 | **COMPLETELY BLACK** |

> **Key insight:** The Saturation channel directly represents color intensity. More saturation = higher numerical value = brighter visualization.

---

## Part 2: Bit-Plane Slicing

I converted the image to grayscale and decomposed it into 8 bit-planes (Bit 7 = MSB to Bit 0 = LSB).

### By removing which bits does the image remain recognizable to the human eye?

**Answer:** The image remains recognizable when removing **Bit-planes 0, 1, and 2** (the 3 Least Significant Bits).

### Why?

| Bit Group | Information Content |
|-----------|---------------------|
| Bits 7,6,5,4 (4 MSBs) | **94%** of visual information |
| Bits 3,2,1,0 (4 LSBs) | **6%** (fine details & noise) |

### Effect of Removing Different Bit-Planes

| Bits Removed | Recognizability |
|--------------|-----------------|
| Bits 0-2 (3 LSBs) | ✅ Fully recognizable |
| Bits 0-3 (4 LSBs) | ⚠️ Partially recognizable |
| Bits 0-4 (5 LSBs) | ❌ Hard to recognize |

---

## Conclusion

| # | Key Finding |
|---|-------------|
| 1 | The **Saturation channel** in HSV space effectively represents color intensity — more saturated colors appear **brighter** |
| 2 | **MSBs (bits 4-7)** carry essential visual information; **LSBs (bits 0-3)** contain fine details and noise |
| 3 | Removing up to **3 LSBs (bits 0-2)** maintains image recognizability while reducing storage by **37.5%** |

---