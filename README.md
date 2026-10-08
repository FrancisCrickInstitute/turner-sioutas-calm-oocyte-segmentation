# Project Code
This is the git repo for the segmentation and overlap exclusion code for "Stage-specific checkpoint signalling by ATM, ATR and DNA-PL safeguards oocyte development" by Sioutas, et. al. 

This code was first written by Vanessa Dao, and then further assisted by Todd Fallesen, of Crick Advaned Light Microscopy STP at The Francis Crick Institute, London, UK.

## Segmentation
3D segmentation is perfomed using the CellPose plugin for Trackmate, run in Fiji.  3D segmentations are obtained by substituting the Time and Z axes for each other in an image, so that Trackmate believes it is tracking through time, while it is actually tracking through Z-space. The object detector used in Trackmate is Cellpose. In the datasets this script was created for, the objects of interest were of two different sizes. Cellpose 3 requires an estimated diameter, so this code was created to segment the same image with multiple estimated sizes, and then eliminate any overlapping segmentations between the segmentation maps, leaving a segmentation map with both large and small segmented objects of interest. 

### Trackmate/CellPose installation
Trackmate can be installed as a plugin in Fiji. The Trackmate-cellpose plugin also needs to be installed, instructions to install Trackmate and Trackmate-Cellpose can be found here: [https://imagej.net/plugins/trackmate/detectors/trackmate-cellpose](https://imagej.net/plugins/trackmate/detectors/trackmate-cellpose). Trackmate will also have to be configured to point at the local cellpose conda environment.  Instructions to install Cellpose Conda Environments can be found here: [https://cellpose.readthedocs.io/en/latest/index.html](https://cellpose.readthedocs.io/en/latest/index.html).  Please note, Cellpose 3 was used in this project.

### Trackmate_Cellpose_GUI.py
This Fiji script will run over all 3D images in a folder, creating XML files for the segmentations.  The XML files can be reloaded by the user to do any fine tuning on the segmentation maps before saving out the segmenations. 


To run: Change lines 96 and 99 to point to the local conda installation of cellpose.  
Change line 64, PixelSizes, to a list of pixel sizes that are appropriate for the objects of interest your images. 


## Combine segmentations

To install the functions for this code, you can simply use pip, calling 'pip install napari-segmentation-overlap-filter'. The functions used are also provided in this repo as functions.py.
The conda environment used is provided as parseg_env_no_builds.yml



