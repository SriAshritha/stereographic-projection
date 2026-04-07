#  Stereographic Projection of Warli Art onto a 3D Sphere

##  Overview
This project demonstrates how traditional Warli art (2D binary geometry) can be transformed into a 3D spherical mesh using stereographic projection, computational geometry, and MATLAB.

The pipeline converts a flat image into a watertight 3D printable solid mesh, preserving the topology of the original artwork.

---

##  Key Features

- Image → Binary Mask (Otsu Thresholding)
- Foreground Pixel Extraction → 2D Point Cloud
- Delaunay Triangulation (robust mesh generation)
- Triangle Filtering (remove noise & artifacts)
- Stereographic Projection (plane → sphere mapping)
- Solid Mesh Generation (thickness + boundary stitching)
- Export to ".OBJ" (compatible with Rhino / Blender / slicers)

---
