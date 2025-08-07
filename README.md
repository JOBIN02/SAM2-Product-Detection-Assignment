Project: Zero-Shot Product Detection using SAM2

1. Introduction

This document details the solution to the recruitment assignment, which involves using the Segment Anything 2 (SAM2) model for zero-shot object detection. The goal was to use the first image and mask of a product from the CMU-10 3D dataset to detect that same product in subsequent images and evaluate the model's performance using the Intersection over Union (IoU) metric.


2. Methodology

The project was developed in a Google Colab environment to leverage GPU acceleration. The process involved several key steps:

Environment Setup: The first step was to configure the environment by installing all required libraries, including segment-anything-2 and pycocotools. The SAM2 "tiny" model checkpoint and the CMU-10 3D dataset were also downloaded.

Bounding Box Extraction: As required, a function (process_img_png_mask) was created to extract the initial bounding box coordinates from the provided PNG mask files. This involved using NumPy to find the boundaries of the object in the mask.

Object Tracking: The provided track_item_boxes function was used to perform the tracking. The script was designed to:

Programmatically pair each .jpg image with its corresponding _gt.png mask file.

Use the first image-mask pair of each product to initialize the SAM2 model.

Run the model on the remaining images of that product to get the predicted masks.


Performance Evaluation: The accuracy of the model was calculated for each product individually. For each prediction, the output mask was converted into a bounding box. This predicted box was then compared against the ground-truth box (derived from the test image's own mask) to calculate the IoU score. The scores for each product were then averaged.

"*Code and Final Output Attached in the Sam2_fixed.ipynb and Sam2_Download.ipynb file*"
NOTE:Sam2_fixed.ipynb is for previewing the output and Sam2_Download.ipynb is to check and download the code, kindly download this file. 

3.Conclusion

This project successfully implemented a pipeline for zero-shot object detection using SAM2. The main challenges involved handling the dataset's file structure and ensuring the environment was correctly configured. The final script successfully tracks objects and evaluates the model's performance as required.

