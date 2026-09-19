# SGG 3D Semantic Projector

An interactive browser-based visualization platform for exploring **Scene Graph Generation (SGG)** representations in a high-dimensional semantic embedding space.

The system is inspired by the visualization workflow of TensorFlow Embedding Projector and is designed to transform scene graph entities into an interactive 3D semantic space using **PCA, t-SNE, and UMAP**.

---

## Overview

Scene Graph Generation represents an image as a structured graph consisting of:

- Objects / entities
- Semantic relationships
- Subject-predicate-object triples

This project provides an interactive environment for visualizing these semantic structures in a 3D semantic embedding space.

Unlike representations where predicates are treated as independent nodes, this projector represents relationships as directed edges between semantic entities.

### Conceptual Pipeline

```text
Image
  |
  v
Scene Graph Generation
  |
  +-- Objects / Entities
  +-- Relationships
          |
          v
   Semantic Embeddings
          |
          v
 PCA / t-SNE / UMAP
          |
          v
   3D Semantic Space
          |
          v
 Interactive Exploration
```

---

# Key Features

## Image-Based Scene Graph Visualization

Select an example image and explore its corresponding scene graph representation.

The visualization provides a connection between:

```text
Image -> Objects -> Relationships -> Semantic Space
```

## 3D Semantic Embedding Space

Scene graph entities are projected into an interactive 3D coordinate space.

The visualization provides:

- X/Y/Z axes
- 3D spatial navigation
- Zoom
- Rotation
- Point selection
- Hover information
- Semantic neighborhoods
- Camera controls
- Interactive graph exploration

## Relationship-Aware Scene Graph

Relationships are represented as **edges rather than independent nodes**.

Example:

```text
Person ---- riding ----> Bicycle
   |
   +------ near -------> Tree
```

Here:

- `Person` -> semantic node
- `Bicycle` -> semantic node
- `Tree` -> semantic node
- `riding` -> relationship edge
- `near` -> relationship edge

This provides a natural representation of the conventional Scene Graph structure:

```text
Subject -> Predicate -> Object
```

---

# Dimensionality Reduction

The projector supports multiple dimensionality-reduction approaches.

### PCA

**Principal Component Analysis (PCA)** provides a linear projection of high-dimensional representations into a lower-dimensional space.

### t-SNE

**t-distributed Stochastic Neighbor Embedding (t-SNE)** provides nonlinear visualization emphasizing local semantic neighborhoods.

### UMAP

**Uniform Manifold Approximation and Projection (UMAP)** provides nonlinear dimensionality reduction while attempting to preserve local and broader manifold structure.

The resulting representations are projected into:

```text
High-Dimensional Embedding
            |
            v
     Dimensionality Reduction
            |
            v
        X, Y, Z
            |
            v
      3D Semantic Space
```

---

# Custom Scene Graph JSON Upload

Users can upload their own Scene Graph JSON files and visualize them directly in the semantic space.

### Example JSON

```json
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
```

The uploaded scene graph can then be explored using the same interactive 3D semantic environment.

---

# Visualization Controls

The interface provides controls for:

- Projection algorithm
- PCA
- t-SNE
- UMAP
- Dark / light theme
- Point size
- Relationship visibility
- Node labels
- Semantic search
- Nearest semantic neighbors
- Camera navigation
- 3D axes
- Graph relationship inspection
- Interactive rotation
- Zoom
- Semantic point selection

---

# Theme Support

The projector supports both:

- Light theme
- Dark theme

The 3D semantic space adapts to the selected theme, including:

- Background
- Grid
- Axes
- Labels
- Graph relationships
- Semantic points

---

# Semantic Search and Nearest Neighbors

Users can search for semantic entities within the projected space.

Selecting a node provides information about:

- Entity label
- Entity type
- Embedding information
- Connected relationships
- Neighboring semantic entities
- Scene graph relationships

This enables interactive exploration of semantic neighborhoods.

---

# Example Scene Graph

A scene graph can be represented as:

```text
                 riding
Person ----------------------> Bicycle
  |
  | near
  v
 Tree
```

In the 3D semantic projector:

```text
Person  -> Semantic Point
Bicycle -> Semantic Point
Tree    -> Semantic Point

riding  -> Relationship Edge
near    -> Relationship Edge
```

Predicates are therefore not treated as independent semantic nodes.

---

# Project Structure

```text
SGG-3D-Semantic-Projector/
|
+-- index.html
+-- sample_scene_graph.json
+-- README.md
|
+-- assets/
    +-- images/
```

---

# Getting Started

No backend server is required for the current version.

### Clone the repository

```bash
git clone https://github.com/<USERNAME>/SGG-3D-Semantic-Projector.git
```

### Open the application

Open:

```text
index.html
```

in a modern web browser.

The application runs directly in the browser.

The project can also be deployed using GitHub Pages.

---

# Custom Scene Graph Workflow

To visualize your own scene graph:

1. Open the projector.
2. Select **Upload JSON Scene Graph**.
3. Select your `.json` Scene Graph file.
4. The graph is loaded into the projector.
5. Select the uploaded scene.
6. Choose PCA, t-SNE, or UMAP.
7. Explore the resulting 3D semantic space.

---

# Supported Scene Graph Format

## Nodes

Each node contains an identifier, semantic label, and type.

```json
{
  "id": "object_1",
  "label": "person",
  "type": "object"
}
```

## Edges

Each relationship contains the source node, target node, and relationship.

```json
{
  "source": "object_1",
  "target": "object_2",
  "relation": "holding"
}
```

The representation follows the conventional conceptual structure:

```text
Subject -> Predicate -> Object
```

while rendering the predicate as an edge label in the visualization.

---

# Research Integration

The projector is designed to support research workflows involving:

- Scene Graph Generation
- Visual Relationship Detection
- Graph Representation Learning
- Transformer-based SGG
- Vision Transformers
- Semantic Embeddings
- Graph Neural Networks
- Multimodal Representation Learning
- Dimensionality Reduction
- Visual Analytics

---

# Research Pipeline

A potential research pipeline using the projector is:

```text
                         Input Image
                              |
                              v
                          Visformer
                              |
                              v
                   Multi-scale Visual Features
                              |
                              v
                    MATAN / Transformer
                              |
                              v
              Object & Relationship Representations
                              |
                              v
                         Scene Graph
                              |
                              v
                   High-Dimensional Embeddings
                              |
                    +---------+---------+
                    |         |         |
                    v         v         v
                   PCA      t-SNE      UMAP
                    |         |         |
                    +---------+---------+
                              |
                              v
                     3D Semantic Space
                              |
                              v
                  Interactive Visualization
```

---

# MATAN Integration

The projector is particularly suitable for analyzing learned representations generated by MATAN / Visformer-based Scene Graph Generation models.

Potential workflow:

```text
MATAN / Visformer
       |
       v
   768-D Embedding
       |
       +---------+---------+
       |         |         |
       v         v         v
      PCA      UMAP      t-SNE
       |         |         |
       +---------+---------+
                 |
                 v
        3D Semantic Space
```

---

# Current Implementation

The current demonstration version uses **browser-generated proxy embeddings** to demonstrate the visualization workflow.

These embeddings are intended for visualization and interface demonstration and are **not actual MATAN/Visformer learned embeddings**.

For research experiments, the intended next stage is to replace the proxy representations with actual learned embeddings generated by the SGG model.

This distinction is important when interpreting distances, clusters, and semantic neighborhoods in the current demonstration.

---

# Future Development

Planned extensions include:

- [ ] Direct 768-D MATAN embedding import
- [ ] `.npy` embedding support
- [ ] CSV/TSV metadata import
- [ ] Real model-generated scene graphs
- [ ] Image bounding-box visualization
- [ ] Object-to-image region linking
- [ ] Predicate embedding visualization
- [ ] Cosine similarity search
- [ ] Euclidean nearest-neighbor search
- [ ] k-hop subgraph highlighting
- [ ] Cross-image semantic comparison
- [ ] PCA explained-variance visualization
- [ ] Configurable t-SNE parameters
- [ ] Configurable UMAP parameters
- [ ] Lasso selection
- [ ] Box selection
- [ ] Export projected coordinates
- [ ] Export visualization results
- [ ] GitHub Pages deployment
- [ ] WebGPU acceleration for large embeddings
- [ ] Direct integration with trained SGG models

---

# Architecture

```text
+---------------------------------------------+
|              Input / Data Layer             |
|                                             |
|  Images | Scene Graph JSON | Embeddings     |
+-----------------------+---------------------+
                        |
                        v
+---------------------------------------------+
|             Scene Graph Layer               |
|                                             |
|        Nodes + Relationship Edges           |
+-----------------------+---------------------+
                        |
                        v
+---------------------------------------------+
|          Embedding / Projection Layer       |
|                                             |
|       PCA | t-SNE | UMAP                    |
+-----------------------+---------------------+
                        |
                        v
+---------------------------------------------+
|             3D Visualization Layer          |
|                                             |
|   Three.js + Axes + Nodes + Graph Edges     |
+-----------------------+---------------------+
                        |
                        v
+---------------------------------------------+
|            Interactive Analysis             |
|                                             |
| Search | Neighbors | Selection | Inspection |
+---------------------------------------------+
```

---

# Motivation

Scene Graph Generation provides a structured representation of visual content, but high-dimensional learned representations are difficult to interpret directly.

This project provides a visual interface for investigating questions such as:

- Which objects have similar semantic representations?
- Which scene entities form semantic clusters?
- How do different images occupy the embedding space?
- How do relationships connect semantically related entities?
- How does the choice of dimensionality-reduction algorithm affect visualization?
- How do learned SGG representations change across different scenes?

The overall goal is to provide an interactive environment for visual analysis of learned scene representations.

---

# Inspiration

The interaction model is inspired by TensorFlow Embedding Projector, particularly its concept of projecting high-dimensional representations into lower-dimensional spaces for interactive exploration.

This project adapts that general visualization philosophy specifically for Scene Graph Generation and visual relationship representations.

---

# Technologies

The project uses:

- HTML5
- CSS3
- JavaScript
- Three.js
- PCA
- t-SNE
- UMAP
- JSON
- Interactive 3D visualization

---

# License

Add an appropriate open-source license before public distribution, such as:

- MIT License
- Apache License 2.0
- BSD License

The selected license should be compatible with the project's dependencies and intended research usage.

---

# Citation

If you use this visualization platform in academic research, please cite the corresponding project or repository.

```text
Monesh S.

SGG 3D Semantic Projector:
Interactive Visualization of Scene Graph Embeddings
Using PCA, t-SNE, and UMAP.
```


# Project Tagline

**SGG 3D Semantic Projector**

From Scene Graphs to Semantic Space.

```text
Image
  |
  v
Scene Graph
  |
  v
Embedding
  |
  v
Projection
  |
  v
3D Semantic Space
  |
  v
Visual Understanding
```
