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

```
Key Features

🖼️ Image-Based Scene Graph Visualization

Select an example image and explore its corresponding scene graph representation.

🧠 3D Semantic Embedding Space

Scene graph entities are projected into an interactive 3D coordinate space.

The visualization provides:

X/Y/Z axes
Spatial navigation
Zoom
Rotation
Point selection
Hover information
Semantic neighborhoods
🔗 Relationship-Aware Scene Graph

Relationships are represented as edges rather than independent nodes.

For example:

Person ───── riding ─────► Bicycle
   │
   └──────── near ───────► Tree

This provides a more natural representation of conventional scene graphs.

📉 Dimensionality Reduction

The projector supports multiple dimensionality-reduction approaches:

PCA
t-SNE
UMAP

These methods transform high-dimensional semantic representations into a visualization-friendly 3D space.

📁 Custom Scene Graph JSON Upload

Users can upload their own Scene Graph JSON files.

Example:

{
  "id": "sample_scene_graph_01",
  "title": "Person Riding Bicycle",

  "nodes": [
    {
      "id": "person_1",
      "label": "person",
      "type": "object"
    },
    {
      "id": "bicycle_1",
      "label": "bicycle",
      "type": "object"
    }
  ],

  "edges": [
    {
      "source": "person_1",
      "target": "bicycle_1",
      "relation": "riding"
    }
  ]
}

The uploaded graph can then be explored in the same 3D semantic environment.

Visualization Controls

The interface provides controls for:

Projection algorithm
Dark / light theme
Point size
Relationship visibility
Node labels
Search
Nearest semantic neighbors
Camera navigation
3D axes
Graph relationship inspection
Example Scene Graph

A scene graph can be represented as:

        riding
Person ─────────► Bicycle
  │
  │ near
  ▼
Tree

In the 3D semantic projector:

Person becomes a semantic point.
Bicycle becomes a semantic point.
Tree becomes a semantic point.
riding and near become labeled graph edges.
Project Structure
SGG-3D-Semantic-Projector/
│
├── index.html
├── sample_scene_graph.json
├── README.md
└── assets/
    └── images/
Getting Started

No backend server is required for the current version.

Clone the repository:

git clone https://github.com/<USERNAME>/SGG-3D-Semantic-Projector.git

Open:

index.html

in a modern web browser.

Alternatively, the project can be deployed directly using GitHub Pages.

Custom Scene Graph

To visualize your own graph:

Open the projector.
Select Upload JSON Scene Graph.
Select your .json file.
The graph is loaded into the projector.
Select the uploaded scene.
Run PCA, t-SNE, or UMAP.
Explore the resulting 3D semantic space.
Supported Scene Graph Format
Nodes

Each node contains:

{
  "id": "object_1",
  "label": "person",
  "type": "object"
}
Edges

Each relationship contains:

{
  "source": "object_1",
  "target": "object_2",
  "relation": "holding"
}

This follows the standard conceptual representation:

Subject → Predicate → Object

while rendering the predicate as an edge label.

Research Integration

The projector is designed to support research workflows involving:

Scene Graph Generation
Visual Relationship Detection
Graph Representation Learning
Transformer-based SGG
Vision Transformers
Semantic Embeddings
Graph Neural Networks
Multimodal Representation Learning
Dimensionality Reduction
Visual Analytics

A potential research pipeline is:

Image
  ↓
Visformer
  ↓
Multi-scale Visual Features
  ↓
MATAN / Transformer
  ↓
Object & Relationship Representations
  ↓
Scene Graph
  ↓
High-Dimensional Embeddings
  ↓
PCA / t-SNE / UMAP
  ↓
3D Semantic Visualization
Current Implementation

The current demonstration version uses browser-generated proxy embeddings to demonstrate the visualization workflow.

For research experiments, the intended next stage is to replace these proxy representations with actual learned embeddings generated by the SGG model.

For example:

MATAN / Visformer
       ↓
768-D Embedding
       ↓
PCA / UMAP / t-SNE
       ↓
3D Semantic Space
Future Development

Planned extensions include:

 Direct 768-D MATAN embedding import
 .npy embedding support
 CSV/TSV metadata import
 Real model-generated scene graphs
 Image bounding-box visualization
 Object-to-image region linking
 Predicate embedding visualization
 Cosine similarity search
 Euclidean nearest-neighbor search
 k-hop subgraph highlighting
 Cross-image semantic comparison
 PCA explained-variance visualization
 Configurable t-SNE parameters
 Configurable UMAP parameters
 Lasso / box selection
 Export projected coordinates
 Export visualization results
 GitHub Pages deployment
 WebGPU acceleration for large embeddings
Technologies
HTML5
CSS3
JavaScript
Three.js
PCA
t-SNE
UMAP
JSON
Interactive 3D visualization
Inspiration

The interaction model is inspired by TensorFlow Embedding Projector, particularly the concept of projecting high-dimensional representations into lower-dimensional spaces for interactive exploration.

License

Add an appropriate open-source license before public distribution, such as MIT, Apache-2.0, or another license compatible with the dependencies and intended research use.

Citation

If you use this visualization platform in academic research, please cite the corresponding project/repository.

Monesh S.
SGG 3D Semantic Projector:
Interactive Visualization of Scene Graph Embeddings
Using PCA, t-SNE, and UMAP.
