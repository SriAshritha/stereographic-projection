🎨 Stereographic Projection of Warli Art onto a 3D Sphere

📌 Overview

This project demonstrates how traditional Warli art (2D binary geometry) can be transformed into a 3D spherical mesh using stereographic projection, computational geometry, and MATLAB.

The pipeline converts a flat image into a watertight 3D printable solid mesh, preserving the topology of the original artwork.

---

🚀 Key Features

- Image → Binary Mask (Otsu Thresholding)
- Foreground Pixel Extraction → 2D Point Cloud
- Delaunay Triangulation (robust mesh generation)
- Triangle Filtering (remove noise & artifacts)
- Stereographic Projection (plane → sphere mapping)
- Solid Mesh Generation (thickness + boundary stitching)
- Export to ".OBJ" (compatible with Rhino / Blender / slicers)

---

🧠 Mathematical Foundation

🔹 Coordinate Normalization

Pixel indices mapped to Cartesian plane:

x = (c - 1)/(N - 1) * 2 - 1
y = -((r - 1)/(N - 1) * 2 - 1)

---

🔹 Delaunay Triangulation

- Ensures no point lies inside circumcircle
- Maximizes minimum triangle angle
- Avoids degenerate triangles

---

🔹 Stereographic Projection

Let:

H = x² + y²

Mapping from plane → sphere:

X = 2R x / (H + 1)
Y = 2R y / (H + 1)
Z = R (H - 1) / (H + 1)

- Conformal (angle-preserving)
- Maps infinite plane → sphere surface

---

🔹 Thickness Generation

Radial normals:

n̂ = p / ||p||

Inner surface:

p_inner = p - t · n̂

---

🛠️ Implementation (MATLAB)

Main Pipeline

% Step 1: Image Processing
imgGray = rgb2gray(img);
mask = imbinarize(imgGray);
mask = bwareaopen(mask,50);
mask = imresize(mask,[500 500]);

% Step 2: Point Extraction
[rows, cols] = find(mask);

% Step 3: Triangulation
DT = delaunayTriangulation(pts2d);

% Step 4: Projection
SpherePts = [
R*2*X./(H+1),
R*2*Y./(H+1),
R*(H-1)./(H+1)
];

---


🎯 Applications

- 3D Printing (lamps, artifacts, decor)
- Cultural heritage digitization
- Computational geometry demonstrations
- Architectural surface design
- XR / AR visualization

---
 

📎 Output Example

- 2D Warli → 3D Sphere Projection
- Exported ".OBJ" ready for Rhino / Blender
