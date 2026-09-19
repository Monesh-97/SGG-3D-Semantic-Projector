# SGG 3D Semantic Projector

An interactive browser-based visualization platform for exploring **Scene Graph Generation (SGG)** representations in a high-dimensional semantic embedding space.

The system is inspired by the visualization workflow of **TensorFlow Embedding Projector** and is designed to transform scene graph entities into an interactive 3D semantic space using dimensionality-reduction techniques such as **PCA, t-SNE, and UMAP**.

---

## Overview

Scene Graph Generation represents an image as a structured graph consisting of:

- Objects / entities
- Semantic relationships
- Subject–predicate–object triples

This project provides an interactive environment for visualizing these semantic structures in a 3D embedding space.

Instead of representing relationships as independent nodes, relationships are visualized as **directed edges between semantic entities**.

### Conceptual Pipeline

```text
Image
  │
  ▼
Scene Graph Generation
  │
  ├── Objects / Entities
  │
  └── Relationships
          │
          ▼
   Semantic Embeddings
          │
          ▼
 PCA / t-SNE / UMAP
          │
          ▼
   3D Semantic Space
          │
          ▼
 Interactive Exploration
