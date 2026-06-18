<div align="center">
<img src="https://i.ibb.co/n8kcfR4T/Screenshot-2025-12-05-085957.png" alt="TRINETRA banner" border="0">

# TRINETRA

**AI-Powered Geospatial Natural Language Interpretation (GeoNLI) for Remote Sensing Imagery**

[![Live Demo](https://img.shields.io/badge/Live%20Demo-TRINETRA-2ea44f?style=flat-square)](https://trinetra-silk.vercel.app/)
[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=flat-square&logo=next.js)](https://nextjs.org/)
[![Python](https://img.shields.io/badge/Python-3.12-blue?style=flat-square&logo=python)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-Mixed%20OSS-orange?style=flat-square)](#license--acknowledgments)

</div>

---

## Overview

**TRINETRA** is an AI-powered conversational platform built for **Geospatial Natural Language Interpretation (GeoNLI)** across remote sensing imagery of multiple modalities — including **Optical**, **False Color Composite (FCC)**, and **Synthetic Aperture Radar (SAR)**.

The platform delivers clear, context-aware insights directly tied to geospatial data through three core tasks:

- **Captioning** — Generate detailed, descriptive captions for satellite imagery.
- **Grounding** — Locate and outline objects with oriented bounding boxes (OBB).
- **Visual Question Answering (VQA)** — Answer binary, numeric, and semantic questions about an image.

In addition to these core capabilities, TRINETRA offers:

- **AgriChat** — A dedicated module for agriculture-specific queries.
- **GEO Compare** — Temporal comparison that lets users analyze changes between two images of the same location over time.

---

## Key Features

| Capability | Description |
| --- | --- |
| 🛰️ **Multi-Modal Support** | Works across Optical, FCC, and SAR imagery. |
| 💬 **Conversational Interface** | Real-time streaming chat for natural geospatial analysis. |
| 🖼️ **Captioning & VQA** | Instant captioning plus grounded visual question answering. |
| 🎯 **Object Grounding** | Oriented bounding boxes with SAM-based mask refinement. |
| 🌾 **AgriChat** | Specialized agriculture analysis with rich, formatted output. |
| 🔀 **GEO Compare** | Side-by-side temporal comparison of two locations or timestamps. |

---

## Architecture

TRINETRA uses a decoupled architecture with a modern web frontend and a two-tier inference backend.

```
┌──────────────┐      ┌───────────────────┐      ┌──────────────────┐
│   TRINETRA   │────▶ │  Flask Backend    │────▶ │   Modal Server   │
│  (Next.js)   │      │  (orchestration)  │      │  (GPU inference) │
│              │ ◀────│  YOLO · Supabase  │ ◀────│  VLMs · SAM · LLM│
└──────────────┘      └───────────────────┘      └──────────────────┘
```

- **Frontend (`TRINETRA/`)** — Next.js 15 application providing the chat UI, map selection, and comparison views.
- **Backend (`backend/`)** — A Flask API server for request orchestration, image classification, and pre/post-processing, paired with a Modal-hosted FastAPI server running the Vision-Language Models on GPU.

---

## Repository Structure

```txt
.
├── TRINETRA/              # Next.js frontend application
├── backend/              # Flask + Modal inference backend
├── deployment_script.sh  # End-to-end deployment helper
├── user_guide.pdf        # Detailed user guide
└── README.md
```

Each of the `TRINETRA/` and `backend/` directories contains its own detailed `README.md` with component-specific setup instructions.

---

## Prerequisites

- **Node.js** `v22.18.0` — for the frontend.
- **Python** `v3.12.4` — for the backend.
- A **Modal** account (GPU inference), **Supabase** project (image storage), and **MapTiler** API key (map search).

---

## Quick Start

The repository is split into two main components — `TRINETRA` (frontend) and `backend`. Each has its own `README.md` with detailed, step-by-step instructions. Follow both to get the full application running.

### Automated Deployment

A helper script is provided to deploy the backend (Modal + Flask) and frontend in sequence:

```bash
./deployment_script.sh
```

### Manual Setup

1. **Backend** — Deploy the Modal GPU server, then start the Flask API. See [`backend/README.md`](backend/README.md).
2. **Frontend** — Install dependencies and run the dev server. See [`TRINETRA/README.md`](TRINETRA/README.md).

For a complete walkthrough of the platform's features, refer to [`user_guide.pdf`](user_guide.pdf).

---

## License & Acknowledgments

This project integrates multiple open-source models and libraries. Each component retains its original license:

| Component | License | Notes |
| --- | --- | --- |
| **Qwen3** | Apache 2.0 | Free commercial use, modification, and distribution. |
| **LLaMA 3.1** | LLaMA 3.1 Community License | Commercial use and redistribution subject to user-cap restrictions and attribution. |
| **YOLO v11** | AGPL-3.0 | Derivative open-source software must use the same license; enterprise use requires a separate commercial license. |
| **SAM 2.1** | Apache 2.0 | Permissive license for both code and model weights. |
| **SAM 3** | Custom Meta License | Non-exclusive, royalty-free license subject to attribution and compliance terms. |
| **RemoteCLIP** | Apache 2.0 | Free commercial use, modification, and distribution. |

Please refer to the individual documentation files for specific citations and acknowledgments.

---
