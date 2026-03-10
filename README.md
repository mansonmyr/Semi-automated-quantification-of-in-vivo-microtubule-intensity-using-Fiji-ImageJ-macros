# Semi-automated-quantification-of-in-vivo-microtubule-intensity-using-Fiji-ImageJ-macros
This repository contains ImageJ macros for semi-automated quantification of microtubule fluorescence intensity from immunofluorescence microscopy images.  The workflow detects centrosomal microtubule foci and mitotic spindle poles using automated pixel maxima detection and ROI-based intensity measurements. 
# Workflow Overview
1. Image Preprocessing
The macro applies the following preprocessing steps:
	1.	Sum projection of z-stack
	2.	Adaptive median filtering (external plugin required: https://imagej.net/plugins/adaptive-median-filter)
	3.	Gaussian blur
	4.	Mean filtering
These steps enhance signal-to-noise ratio for reliable centrosome detection.

2. Object Detection
Centrosomal foci are detected using the ImageJ Find Maxima algorithm. This function identifies local intensity maxima that exceed a defined tolerance threshold relative to surrounding pixels. Detected maxima coordinates are stored for subsequent ROI placement.

3. ROI Generation
For each detected maxima:
	1.	Circular ROI is generated
	2.	User manually adjusts ROI to select adjacent background region
	3.	Background-subtracted intensity is calculated

4. Output
The macro outputs:
	•	centrosomal microtubule intensity
	•	background intensity
	•	corrected intensity values
Results can be exported as CSV tables or copy-paste into your spreadsheet.

# Analysis Pipeline
1. Measures centrosomal microtubule intensity.

Z-stack -> Sum projection -> Median filter -> Gaussian blur -> Mean filter -> FindMaxima() -> Save XY coordinates -> Circular ROI placement -> Background subtraction -> Centrosome intensity output

2. Quantifies spindle pole characteristics.
Measured parameters:
	•	γ-tubulin spindle pole intensity
	•	spindle length (distance between two poles)
	•	spindle microtubule intensity

Image preprocessing -> Spindle pole detection (FindMaxima)
   					-> Two pole coordinate identification -> Distance calculation
   					-> Rectangular ROI placement along spindle -> Intensity measurement

# Example 1
<img width="189" height="126" alt="image" src="https://github.com/user-attachments/assets/faa5036b-f855-4a5b-ae6d-ae49de8799a4" />
<img width="290" height="138" alt="image" src="https://github.com/user-attachments/assets/b6a3fa73-fd59-4fa7-adb6-2e749fa66a2c" />
<img width="362" height="291" alt="image" src="https://github.com/user-attachments/assets/f1ce5f2b-04ef-461c-90e9-1fe91d3e10a9" />

Note: Sum projection and not Max projection. SUM adds all voxel intensities along Z → therefore reflects total integrated intensity. complete accumulated signal. Max projection picks only the brightest pixel along Z. throws away  the rest of the intensity. Max projection does NOT scale with total fluorophore amount.

<img width="424" height="146" alt="image" src="https://github.com/user-attachments/assets/3dabcf78-58a9-4411-b220-0fea627b305b" />

Note: Note: Before clicking ‘OK’, you drag the circle to anywhere of the centrosome.

<img width="360" height="287" alt="image" src="https://github.com/user-attachments/assets/e0dd2ad1-b9bc-4fca-b769-0df952d31037" />

# Example 2
Quantification of spindle pole in FIJI
![ScreenRecording2025-11-22at3 11 23PM-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/c09b96d3-fce1-41ce-96d2-cb694a70f0ee)

# About set Scale ()
The images taken for this repository utilize the Zeiss Inverted Epifluorescence Microscope at 2048 x 2048 to capture fixed sarcoma cells stained with alpha-tubulin and gamma-tubulin. Thus, the scale has to be set accordingly to the model and meta-data of the microscope before runnign the script. All the image capture are *z-stack*.

# Literature Reference
The circular ROI size was reference to Ali, A., Vineethakumari, C., Lacasa, C., & Lüders, J. (2023). Microtubule nucleation and γTuRC centrosome localization in interphase cells require ch-TOG. Nature communications, 14(1), 289. https://doi.org/10.1038/s41467-023-35955-w

The spindle ROI idea was reference to Walczak, C. E., Zong, H., Jain, S., & Stout, J. R. (2016). Spatial regulation of astral microtubule dynamics by Kif18B in PtK cells. Molecular biology of the cell, 27(20), 3021–3030. https://doi.org/10.1091/mbc.E16-04-0254
<img width="172" height="128" alt="image" src="https://github.com/user-attachments/assets/51da44ed-6df4-42b9-8775-3a64fe6e123f" />

# Citation
cff-version: 1.2.0
message: "If you use this software, please cite it as below."
authors:
- family-names: "Ooi"
  given-names: "Kai Hong"
  orcid: "https://orcid.org/0000-0003-3803-7864"
title: "Semi-automated-quantification-of-in-vivo-microtubule-intensity-using-Fiji-ImageJ-macros"
version: 1.0.0
date-released: 2026-03-10
url: "https://github.com/mansonmyr/Semi-automated-quantification-of-in-vivo-microtubule-intensity-using-Fiji-ImageJ-macros"
