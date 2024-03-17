## 3D Rubik's Cube Segmentation & State Detection through Video Stream

### Background & Motivation
Existing apps require you to frame the cube in a grid and take a photo per side, with specific orientation requirements to detect the state. This project aims to detect the cube state through a video stream, with the user rotating the cube in front of a camera.

This project initially started as a CalHacks project where we built a SwiftUI app with C++ OpenCV (for Swift interoperability). The cube detection was done through pure classical CV ([see project here](https://github.com/pdtxie/calhacks10-cubecv)), with CV techniques including masking & thresholding, contour maps, connected components, Canny edge detection and RDP polygonal approximation. Results can be seen here:
[![thumbnail](https://img.youtube.com/vi/UFktIos-ehQ/0.jpg)](https://www.youtube.com/watch?v=UFktIos-ehQ)

### Pipeline

We use DINO + LangSAM (bbox output from DINO to LangSAM for segmentation) to produce a segmented cube, and pass this into a classical CV pipeline, where the final state is extracted.
![pipeline](https://github.com/CubeCV/cubecv/assets/65262710/fbf1ae38-08da-4b5b-9a58-8a8e00dac2ef)


### Results

We obtained reasonable results on most cube inputs, with the exception of some hand placements obscuring corners, causing line detection to fail.

### Future work

An immediate next goal is to train an end-to-end model, bypassing the classical CV steps.

##### Ending note

This was our [Machine Learning @ Berkeley](https://ml.berkeley.edu)'s NMEP Project in Fall 2023.
