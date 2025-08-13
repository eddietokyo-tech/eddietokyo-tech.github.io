---
layout: post
title: IRISS Intraocular Surgical Robot
description: Developed ML-integrated intraocular surgical system for OCT-guided cataract procedures, enabling real-time feedback and classification of ocular structures.
skills:
  - Machine Learning
  - PyTorch
  - OCT Imaging
  - LabVIEW
  - Surgical Robotics
main-image: /iriss-cover.png
---

## Overview

As an undergraduate researcher in UCLA's Advanced Robotic Micro Surgery (ARMS) Lab, I worked on the Intraocular Robotic Interventional and Surgical System (IRISS) — a teleoperated platform for anterior and posterior ocular surgeries. My focus was developing a machine learning pipeline for real-time surgical assistance using OCT imaging.

{% include image-gallery.html images="setup.png" height="400" %} 
*Figure 1: Experiment setup with the IRISS system holding the A-scan probe and zoomed in view of the A-scan probe pointed at the pig eye's sclera.*

# Deep Learning for Ophthalmic Tissue Identification and Proximity Sensing

**Research Publication** | *Translational Vision Science & Technology*

## Overview

This research presents the first demonstration of real-time intraocular tissue classification and proximity sensing using deep learning and optical coherence tomography (OCT). The system addresses critical challenges in minimally invasive ophthalmic surgery by providing surgeons with real-time feedback about tissue types and tool positioning.


## Problem Statement

Minimally invasive ophthalmic procedures require precise manipulation of delicate tissues within the eye. Current challenges include:

- **Limited field of view** - Conventional surgical microscopes are constrained by the pupil
- **Obscured visualization** - Tissues beyond the pupil are often invisible
- **High complication risk** - Procedures like posterior capsule polishing carry increased risk of retinal breaks and hemorrhage
- **Lack of real-time feedback** - No continuous tissue detection or distance estimation during surgery

## Technical Innovation

### Core Technology
- **Intraocular A-scan OCT probe** integrated into surgical tools
- **Dual deep learning models** for simultaneous tissue classification and distance measurement
- **Real-time processing** at 20Hz frequency
- **Robotic integration** with the IRISS (Intraocular Robotic Intervention Surgical System)

### System Architecture
- **Classification Model**: EfficientNet-B0 architecture for tissue type identification
- **Distance Detection**: U-Net model for micron-level proximity sensing
- **Hardware**: Spectral-domain OCT engine (1060 nm wavelength, 9.18μm axial resolution)
- **Integration**: ROS-based communication system for real-time feedback

{% include image-gallery.html images="classifications" height="400" %} 
*Figure 2: Dual deep learning architecture featuring EfficientNet-B0 for tissue classification (top) and U-Net for distance detection (bottom). The parallel processing design enables simultaneous real-time tissue identification and micron-level proximity sensing.*

## Methodology

### Data Collection
- **Dataset**: Over 10,000 labeled A-scan signals from 15 ex vivo pig eyes
- **Tissue Types**: Sclera, iris, lens, posterior capsule, and retina
- **Validation**: Simultaneous B-scan OCT and microscope imaging for ground truth
- **Data Split**: 10 eyes (training), 3 eyes (validation), 2 eyes (testing)

### Model Development
- **Classification**: EfficientNet-B0 adapted for single-channel grayscale OCT images
- **Distance Detection**: U-Net architecture with hybrid loss function (binary cross-entropy + Dice loss + SSIM)
- **Training**: Adam optimizer with adaptive scheduling and data augmentation
- **Real-time Pipeline**: Integrated with robotic system for continuous feedback

## Key Results

### Performance Metrics
- **Classification Accuracy**: 98.62% across all tissue types
- **Distance Detection**: RMS error of 5.06μm (sub-pixel accuracy)
- **Processing Speed**: 20Hz real-time operation
- **System Latency**: 51ms total processing time per frame


{% include image-gallery.html images="confusion-matrix.png" height="400" %} 

*Figure 3: Confusion matrix showing classification performance across five tissue types (sclera, iris, lens, posterior capsule, retina) with 98.62% overall accuracy. Each cell shows the number of predictions, with perfect diagonal performance indicating excellent tissue discrimination.*

{% include image-gallery.html images="unet.png" height="400" %} 
*Figure 4: U-Net predictions overlaid on B-scan OCT images across different tissue types. Predicted tissue boundaries (colored overlays) demonstrate accurate spatial localization matching the actual tissue interfaces visible in cross-sectional images.*

{% include image-gallery.html images="error.png" height="400" %} 
*Figure 5: Histogram of distance prediction errors showing that most predictions achieve perfect accuracy (0μm) or single-pixel precision (9.18μm), resulting in an RMS error of 5.06μm.*

{% include image-gallery.html images="figure2.png" height="400" %} 
*Figure 6: Scatter plot comparing predicted versus true tool-to-tissue distances. The tight clustering along the diagonal line demonstrates micron-level accuracy across all tissue types with minimal deviation from ground truth measurements.*

### Technical Achievements
- **First demonstration** of intraocular A-scan-based classification for real-time surgical applications
- **Micron-level precision** in distance measurement
- **Multi-tissue classification** with near-perfect accuracy
- **Real-time integration** suitable for surgical environments

## Clinical Impact

### Surgical Applications
- **Enhanced Safety**: Real-time tissue identification prevents inadvertent damage
- **Improved Precision**: Micron-level distance sensing for delicate procedures
- **Expanded Capabilities**: Enables procedures in hard-to-visualize regions
- **Workflow Integration**: Compatible with both manual and robotic surgical systems

### Advantages Over Existing Methods
- **Intraocular sensing** eliminates field of view limitations
- **Non-contact operation** reduces risk of iatrogenic tissue damage
- **Compact integration** fits into existing surgical tools
- **High-speed feedback** enables real-time surgical adjustments

## Technical Specifications

### Hardware Components
- **OCT Engine**: Thorlabs Telesto II (Model 1060LR)
- **Wavelength**: 1060 nm central wavelength
- **Resolution**: 9.18μm axial resolution, 9.4mm imaging depth
- **Robotic System**: IRISS with 4 DOF + 3 DOF positioning stage
- **Accuracy**: 10μm positioning accuracy, 1μm incremental resolution

### Software Architecture
- **Framework**: Python with PyTorch for deep learning models
- **Communication**: ROS (Robotic Operating System) for data streaming
- **Interface**: LabVIEW for robot control and visualization
- **Processing**: Parallel data acquisition and inference for reduced latency

## Research Validation

### Experimental Setup
- **Controlled Environment**: Ex vivo pig eye model with robotic positioning
- **Multi-modal Validation**: Simultaneous microscope and B-scan OCT confirmation
- **Systematic Data Collection**: Varied angles (60°-90°) and distances (4mm range)
- **Rigorous Testing**: Separate eyes for training, validation, and testing

### Performance Analysis
- **Confusion Matrix**: Detailed classification performance across tissue types
- **Error Distribution**: Distance prediction accuracy visualization
- **Real-time Metrics**: Complete processing pipeline timing analysis

## Future Applications

### Clinical Translation
- **Human Eye Validation**: Expansion to human donor eyes and pathological samples
- **In Vivo Testing**: Validation in live surgical environments
- **Surgeon Interface**: Development of intuitive feedback systems
- **Regulatory Pathway**: Preparation for clinical trials and FDA approval

### Technology Extensions
- **Additional Tissues**: Expansion to corneal edema, retinal detachment detection
- **Enhanced Models**: Integration of pathological tissue classification
- **Improved Hardware**: Faster processing with advanced GPU acceleration
- **Surgical Automation**: Foundation for autonomous surgical procedures

## Publications & Recognition

- **Journal**: Translational Vision Science & Technology


## Technical Contributions

This research makes several significant contributions to the field:

1. **Novel Sensing Approach**: First intraocular A-scan-based system for real-time surgical feedback
2. **Dual-Model Architecture**: Simultaneous tissue classification and distance measurement
3. **Clinical Validation**: Comprehensive testing with surgical-grade accuracy requirements
4. **System Integration**: Complete pipeline from data acquisition to real-time feedback
5. **Translational Impact**: Clear pathway from research to clinical implementation


## Key Contributions

- Designed key mechanical subsystems including a syringe end effector and a quick tool-change mechanism using SolidWorks.
- Built an image classification and regression pipeline in PyTorch using EfficientNet, ResNet, and U-Net architectures, achieving:
  - 98% classification accuracy of ocular structures.
  - 50μm prediction accuracy for depth estimation.
- Managed dataset collection, cleaning, preprocessing (MATLAB + Python), and model tuning from start to finish.
- Integrated ML inference with LabVIEW to enable live OCT-based decision support during surgical simulation.
- Collaborated closely with surgeons and engineers across disciplines.

## Outcome

- Achieved real-time classification performance suitable for surgical use.
- Pending co-authorship on a research publication.
- Contributed directly to advancing semi-automated cataract surgery in research settings.

