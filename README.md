# Product Recognition of Books — Traditional Computer Vision

> Academic project for the Image Processing and Computer Vision course
> A.Y. 2025/26 — University of Bologna

## Overview

This repository implements a **traditional computer vision system** for
automatic book recognition on library and bookstore shelves.
Given a reference image for each book, the system locates and identifies
all instances of that book within real shelf scene images — using only
classical computer vision techniques, without any deep learning.

Potential real-world applications include:
- Automated inventory management (detecting misplaced or out-of-stock books)
- Accessibility tools for visually impaired users to locate books by title/author
- Faster book retrieval systems based on spine or cover recognition

## Task

For each reference book provided, the system must:
1. **Detect** all instances of that book in a given shelf scene image
2. **Localize** each instance by computing an oriented bounding box
3. **Report** for each detected instance:
   - Number of instances found
   - Position (four corners of the bounding box)
   - Dimension (bounding box area in pixels)
4. **Overlay** the bounding boxes on the scene image

All steps are solved using **traditional computer vision techniques only**.

## Dataset

Two sets of images are provided:

| Split   | # Images | Description                              |
|---------|----------|------------------------------------------|
| Models  | 22       | One reference image per book             |
| Scenes  | 29       | Shelf images to test the pipeline on     |

Reference images vary widely in size and aspect ratio (typically tall and
narrow, reflecting book spines), while scene images are uniform at 640×640
pixels.

## Pipeline

The detection pipeline consists of the following stages:

1. **Exploratory Data Analysis** — size and aspect ratio analysis of
   reference and scene images
2. **Preprocessing** — image normalization and resizing
3. **Keypoint Extraction & Matching** — using SIFT/ORB descriptors
4. **Homography Estimation** — robust geometric transformation via RANSAC
5. **Bounding Box Computation** — oriented bounding box projection onto
   the scene image
6. **Visualization** — overlay of results on scene images
