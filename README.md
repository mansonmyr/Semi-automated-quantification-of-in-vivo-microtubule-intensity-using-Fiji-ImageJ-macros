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

Z-stack
   ↓
Sum projection
   ↓
Median filter
   ↓
Gaussian blur
   ↓
Mean filter
   ↓
FindMaxima()
   ↓
Save XY coordinates
   ↓
Circular ROI placement
   ↓
Background subtraction
   ↓
Centrosome intensity output

2. Quantifies spindle pole characteristics.
Measured parameters:
	•	γ-tubulin spindle pole intensity
	•	spindle length (distance between two poles)
	•	spindle microtubule intensity

Image preprocessing
   ↓
Spindle pole detection (FindMaxima)
   ↓
Two pole coordinate identification
   ↓
Distance calculation
   ↓
Rectangular ROI placement along spindle
   ↓
Intensity measurement
