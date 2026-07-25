---
title: Near-Complete List of 3D Reconstruction for Glossy and Transparent Objects
description: An attempt at creating an awesome page for the topic
slug: shiny_reconstruction
date: 2026-04-19 00:00:00+0000
categories:
    - Info
tags:    
    - Graphics
weight: 1
---

## Introduction
After we concluded our research on formal mathematics, I wanted to work on computer graphics for the second semester. For that, I contacted Assist. Prof. Berk Gökberk, and asked him if he has any research questions or any ongoing projects that I might be able to involve. He mentioned about 3D reconstruction, especially the reconstruction of shiny and/or transparent objects. 

Here is the definition of the problem: given a number of photographs (which may be as sparse as 12 images) taken around a transparent/glossy object, reconstruct the geometry and materialistic properties. The most recent and popular methods are Neural Radiance Fields (NeRF) and Gaussian Splatting (GS): 
- A NeRF represents a 3D scene continuously inside the weights of a *neural network*. It shoots imaginary light rays from a camera through every pixel of an image into the 3D space. For points along these rays, the neural network evaluates spatial coordinates and viewing angles to predict the local volume density and color. These predictions are then mathematically integrated along the ray to render the final 2D image. However, as you might have guessed, it is *computationally heavy* and impractical for realtime use cases.
- 3DGS replaces the continuous neural network with millions of discrete, semi-transparent 3D "ellipsoids" or "blobs" (Gaussians) distributed throughout the scene space. Each 3D Gaussian stores physical parameters: position, orientation, scale, opacity, and color (which changes based on viewing angle). During rendering, these 3D Gaussians are projected ("splatted") directly onto the 2D screen and sorted by depth, allowing a GPU to quickly rasterize and blend them into a final view. It is usually on-par or sometimes better than NeRF, and due to its design it is quite fast to train, enabling it for real time use cases.

My initial research was to get idea behind current methods, read a few papers, collect what techniques are prominent in the literature, who compares his/her work with who etc. However, I realized that even though there is a lot of work out there, there does not exist a proper *benchmark* to test the effectiveness of the methods. Almost every paper comes up with its own synthetic dataset during training, even though there are many synthetic datasets. Moreover, the evaluation on real world scenarios are so weak, that I sometimes do not believe the results. 

I strongly believe that we should have a proper real world benchmark for testing these, and maybe a survey paper that reimplements/uses the proposed techniques and compares them on the benchmark. Until then I'd like to post what I classified, read and find valuable. Note that the list is "near-complete" in the sense that I believe there are no more than 5-10 papers out there that slipped from may attention (of course at the time of writing this post (April of 2026) as new works may get published). However, if you think that is not the case, feel free to get in touch.

Now I present my readings in two formats as an **pdf documents** that provide comparison table, resulting images, and my personal thoughts as well as an **awesome list** .

## PDF versions

I share Google Drive links below:

- For glossy object reconstruction: https://drive.google.com/file/d/10rvdYToJgHr_JKR0NF_XruN-0G6wMklL/view?usp=sharing
- For transparent object reconstruction: https://drive.google.com/file/d/1kJO1E9ZK-GfMvY2P8FlhsttryeomAckJ/view?usp=sharing

## My near-complete awesome list
I present two separate lists for glossy/shiny and transparent/translucent objects. Note that I do not include works before NeRF at all. 

> **Legend:** [📄] Paper | [🌐] Website | [🎥] Video | [💻] Code
### Glossy Object Reconstruction
- **TraceFlow: Dynamic 3D Reconstruction of Specular Scenes Driven by Ray Tracing** (2025) [[📄](https://arxiv.org/abs/2512.10095)]

- **GlossyGS: Inverse Rendering of Glossy Objects With 3D Gaussian Splatting** (2025, TVCG) [[📄](https://arxiv.org/abs/2410.13349) | [🌐](https://letianhuang.github.io/glossygs/)]

- **RGS-DR: Deferred Reflections and Residual Shading in 2D Gaussian Splatting** (2025, 3DV 2026) [[📄](https://arxiv.org/abs/2504.18468) | [💻](https://github.com/gkouros/RGS-DR) | [🎥](https://gkouros.github.io/projects/RGS-DR/)]

- **Spec-Gloss Surfels and Normal-Diffuse Priors for Relightable Glossy Objects** (2025, WACV 2026 Oral) [[📄](https://arxiv.org/abs/2510.02069) | [💻](https://github.com/gkouros/SpecGloss-GS) | [🎥](https://www.youtube.com/watch?v=Wo4CBEQQyWc) | [🌐](https://gkouros.github.io/projects/SpecGloss-GS/)]

- **NeRSP: Neural 3D Reconstruction for Reflective Objects with Sparse Polarized Images** (2024, CVPR) [[📄](https://arxiv.org/abs/2406.07111) | [💻](https://github.com/PRIS-CV/NeRSP) | [🎥](https://www.youtube.com/watch?v=Sf3q-p8XPbM) | [🌐](https://yu-fei-han.github.io/NeRSP-project/)]

- **GlossGau: Efficient Inverse Rendering for Glossy Surface with Anisotropic Spherical Gaussian** (2025) [[📄](https://arxiv.org/abs/2502.14129)]

- **Inverse Rendering of Translucent Objects Using Physical and Neural Renderers (HomoTranslucent)** (2023, CVPR) [[📄](https://arxiv.org/abs/2305.08336) | [💻](https://github.com/ligoudaner377/homo_translucent) | [🎥](https://www.youtube.com/watch?v=rWZLU_YqacE) | [🌐](https://ligoudaner377.github.io/homo_translucent/)]

- **Looking Through the Glass: Neural Surface Reconstruction Against High Specular Reflections (NeuS-HSR)** (2023, CVPR) [[📄](https://arxiv.org/abs/2304.08706) | [💻](https://github.com/JiaxiongQ/NeuS-HSR) | [🎥](https://www.youtube.com/watch?v=lwHd-GJAmMA)]

- **Inverse Rendering of Glossy Objects via the Neural Plenoptic Function and Radiance Fields (NeP)** (2024, CVPR) [[📄](https://arxiv.org/abs/2403.16224) | [💻](https://github.com/onpix/NeP) | [🌐](https://www.whyy.site/paper/nep)]

- **RISE-SDF: A Relightable Information-Shared Signed Distance Field for Glossy Object Inverse Rendering** (2024, 3DV 2025) [[📄](https://arxiv.org/abs/2409.20140) | [💻](https://github.com/dehezhang2/RISE-SDF) | [🎥](https://www.youtube.com/watch?v=7JQNCMPR5_0) | [🌐](https://dehezhang2.github.io/RISE-SDF/)]

- **GS-ROR²: Bidirectional-guided 3DGS and SDF for Reflective Object Relighting and Reconstruction** (2024, ACM TOG 2025) [[📄](https://arxiv.org/abs/2406.18544) | [💻](https://github.com/NK-CS-ZZL/GS-ROR) | [🌐](https://nk-cs-zzl.github.io/projects/gsror/)]

- **GraspNeRF: Multiview-based 6-DoF Grasp Detection for Transparent and Specular Objects Using Generalizable NeRF** (2023, ICRA) [[📄](https://arxiv.org/abs/2210.06575) | [💻](https://github.com/PKU-EPIC/GraspNeRF) | [🎥](https://pku-epic.github.io/GraspNeRF/) | [🌐](https://pku-epic.github.io/GraspNeRF/)]

- **NeRF-DS: Neural Radiance Fields for Dynamic Specular Objects** (2023, CVPR) [[📄](https://arxiv.org/abs/2303.14435) | [💻](https://github.com/JokerYan/NeRF-DS) | [🌐](https://jokeryan.github.io/projects/nerf-ds/)]

- **GaussianShader: 3D Gaussian Splatting with Shading Functions for Reflective Surfaces** (2023, CVPR) [[📄](https://arxiv.org/abs/2311.17977) | [💻](https://github.com/Asparagus15/GaussianShader) | [🌐](https://asparagus15.github.io/GaussianShader.github.io/)]

- **SpecNeRF: Gaussian Directional Encoding for Specular Reflections** (2024, CVPR) [[📄](https://arxiv.org/abs/2312.13102) | [🎥](https://www.youtube.com/watch?v=3nUooe3pVA0) | [🌐](https://limacv.github.io/SpecNeRF_web/)]

- **Spec-Gaussian: Anisotropic View-Dependent Appearance for 3D Gaussian Splatting** (2024, NeurIPS) [[📄](https://arxiv.org/abs/2402.15870) | [💻](https://github.com/ingra14m/Specular-Gaussians) | [🌐](https://ingra14m.github.io/Spec-Gaussian-website/)]

- **GS-Octree: Octree-based 3D Gaussian Splatting for Robust Object-level 3D Reconstruction Under Strong Lighting** (2025, TPAMI) [[📄](https://arxiv.org/abs/2406.18199) | [💻](https://github.com/city-super/Octree-GS) | [🌐](https://city-super.github.io/octree-gs/)]

- **GS³: Efficient Relighting with Triple Gaussian Splatting** (2024, SIGGRAPH Asia) [[📄](https://arxiv.org/abs/2410.11419) | [💻](https://github.com/gsrelight/gs-relight) | [🌐](https://gsrelight.github.io/)]

- **MS-NeRF: Multi-Space Neural Radiance Fields** (2025, TPAMI) [[📄](https://arxiv.org/abs/2305.04268) | [💻](https://github.com/ZX-Yin/ms-nerf) | [🌐](https://zx-yin.github.io/msnerf/)]

- **Ref-NeRF: Structured View-Dependent Appearance for Neural Radiance Fields** (2022, CVPR) [[📄](https://arxiv.org/abs/2112.03907) | [💻](https://github.com/google-research/multinerf) | [🎥](https://www.youtube.com/watch?v=qrdRH9irAlk) | [🌐](https://dorverbin.github.io/refnerf/)]

- **Geometry-aware Gaussian Splatting of Transparent Object Reconstruction (G-GSTR)** (2026) [[📄](https://www.sciencedirect.com/science/article/pii/S0952197626000680)]

- **Decoupling Geometry and Appearance in Gaussian Splatting for Reflective Surface Reconstruction: A Glossy Image Prior-Guided Approach (GIP-GS)** (2026) [[📄](https://www.sciencedirect.com/science/article/pii/S0893608026001152)]

- **SpectroMotion: Dynamic 3D Reconstruction of Specular Scenes** (2025, CVPR) [[📄](https://arxiv.org/abs/2410.17249) | [💻](https://github.com/cdfan0627/SpectroMotion) | [🌐](https://cdfan0627.github.io/spectromotion/)]

- **Nerfstudio: A Modular Framework for Neural Radiance Field Development** (2023) [[📄](https://arxiv.org/abs/2302.04264)]

- **NeRO: Neural Geometry and BRDF Reconstruction of Reflective Objects from Multiview Images** (2023) [[📄](https://arxiv.org/abs/2305.17398)]

- **ENVIDR: Implicit Differentiable Renderer with Neural Environment Lighting** (2023) [[📄](https://arxiv.org/abs/2303.13022)]

- **GS-2DGS: Geometrically Supervised 2DGS for Reflective Object Reconstruction** (2025) [[📄](https://arxiv.org/abs/2506.13110) | [💻](https://github.com/hirotong/GS2DGS)]

- **Scaffold-GS: Structured 3D Gaussians for View-Adaptive Rendering** (2023) [[📄](https://arxiv.org/abs/2312.00109)]

- **TensoSDF: Roughness-aware Tensorial Representation for Robust Geometry and Material Reconstruction** (2024) [[📄](https://arxiv.org/abs/2402.02771)]

- **Mip-NeRF: A Multiscale Representation for Anti-Aliasing Neural Radiance Fields** (2021) [[📄](https://arxiv.org/abs/2103.13415)]

- **SSR-GS: Separating Specular Reflection in Gaussian Splatting for Glossy Surface Reconstruction** (2026) [[📄](https://arxiv.org/abs/2603.05152)]

- **NeRS: Neural Reflectance Surfaces for Sparse-view 3D Reconstruction in the Wild** (2021) [[📄](https://arxiv.org/abs/2110.07604)]

- **Factored-NeuS: Reconstructing Surfaces, Illumination, and Materials of Possibly Glossy Objects** (2023) [[📄](https://arxiv.org/abs/2305.17929) | [💻](https://github.com/yiqun-wang/Factored-NeuS) | [🌐](https://yiqun-wang.github.io/Factored-NeuS/)]

- **SS-NeRF: Shine-sphere Rendering for Neural Radiance Fields** (2026) [[📄](https://www.sciencedirect.com/science/article/pii/S0031320325012646)]

- **GPSNeRF: Generalizable Neural Radiance Field Reconstruction via Geometric, Photometric, and Semantic Fusion** (2025) [[📄](https://www.sciencedirect.com/science/article/pii/S0263224125033858) | [💻](https://github.com/jjjano/GPSNeRF)]

- **M-NeuS: Volume Rendering Based Surface Reconstruction and Material Estimation** (2024) [[📄](https://www.sciencedirect.com/science/article/pii/S0167839624000621)]

- **FGS-NeRF: A Fast Glossy Surface Reconstruction Method Based on Voxel and Reflection Directions** (2025) [[📄](https://www.sciencedirect.com/science/article/pii/S0262885625000435) | [💻](https://github.com/yosugahhh/FGS-nerf)]

- **FE-GS: 3D Feature-Embedded Gaussian Splatting with Geometric Regularizations for High-Fidelity Rendering** (2026) [[📄](https://www.sciencedirect.com/science/article/pii/S0950705125019938)]

- **RS-SpecSDF: Reflection-Supervised Surface Reconstruction and Material Estimation for Specular Indoor Scenes** (2025) [[📄](https://www.sciencedirect.com/science/article/pii/S1524070325000244)]

- **RAGS: Roughness-Aware Gaussian Splatting for Reflective Objects Surface Reconstruction** (2025) [[📄](https://www.sciencedirect.com/science/article/pii/S0950705126005812)]

- **APS-NeuS: Adaptive Planar and Skip-Sampling for 3D Object Surface Reconstruction in High-Specular Scenes** (2025) [[📄](https://www.sciencedirect.com/science/article/pii/S0262885625002537) | [💻](https://github.com/ujsjl/APS-NeuS)]

- **Glossy Object Reconstruction with Cost-effective Polarized Acquisition** (2025) [[📄](https://ieeexplore.ieee.org/document/11091854) | [🌐](https://bojianwu.github.io/projects/NePR/)]

- **LIRM: Large Inverse Rendering Model for Progressive Reconstruction of Shape, Materials and View-dependent Radiance Fields** (2025) [[📄](https://ieeexplore.ieee.org/document/11092485) | [🌐](https://lzqsd.github.io/LIRM.github.io/)]

- **GUS-IR: Gaussian Splatting With Unified Shading for Inverse Rendering** (2025) [[📄](https://ieeexplore.ieee.org/document/11045434)]

- **NeISF++: Neural Incident Stokes Field for Polarized Inverse Rendering of Conductors and Dielectrics** (2025) [[📄](https://ieeexplore.ieee.org/document/11094863) | [💻](https://github.com/sony/NeISF) | [🌐](https://sony.github.io/NeISF/)]

- **Ref-GS: Directional Factorization for 2D Gaussian Splatting** (2024) [[📄](https://arxiv.org/abs/2412.00905) | [💻](https://github.com/YoujiaZhang/Ref-GS) | [🌐](https://ref-gs.github.io/)]

- **RefracGS: Novel View Synthesis Through Refractive Water Surfaces with 3D Gaussian Ray Tracing** (2026) [[📄](https://arxiv.org/abs/2603.21695)]

- **RCTrans: Transparent Object Reconstruction in Natural Scene via Refractive Correspondence Estimation** (2025) [[📄](https://dl.acm.org/doi/10.1145/3757377.3763859)]

- **RefRef: A Synthetic Dataset and Benchmark for Reconstructing Refractive and Reflective Objects** (2025) [[📄](https://arxiv.org/abs/2505.05848)]

- **RT-GS: Gaussian Splatting with Reflection and Transmittance Primitives** (2026) [[📄](https://arxiv.org/abs/2604.00509)]

- **GLINT: Modeling Scene-Scale Transparency via Gaussian Radiance Transport** (2026) [[📄](https://arxiv.org/abs/2603.26181)]

### Transparent Object Reconstruction
- **TransparentGS: Fast Inverse Rendering of Transparent Objects with Gaussians** (2025, SIGGRAPH) [[📄](https://arxiv.org/abs/2504.18768) | [💻](https://github.com/LetianHuang/transparentgs) | [🎥](https://www.youtube.com/watch?v=HfHC0wNYry8) | [🌐](https://letianhuang.github.io/transparentgs)]

- **DiffTrans: Differentiable Geometry-Materials Decomposition for Reconstructing Transparent Objects** (2024) [[📄](https://arxiv.org/abs/2603.00413) | [💻](https://github.com/lcp29/DiffTrans)]

- **From Transparent to Opaque: Rethinking Neural Implicit Surfaces with α-NeuS** (2024) [[📄](https://arxiv.org/abs/2411.05362) | [💻](https://github.com/728388808/alpha-NeuS) | [🎥](https://lcs.ios.ac.cn/~houf/pages/alphaneus/index.html) | [🌐](https://lcs.ios.ac.cn/~houf/pages/alphaneus/index.html)]

- **TRAN-D: 2D Gaussian Splatting-based Sparse-view Transparent Object Depth Reconstruction via Physics Simulation for Scene Update** (2025) [[📄](https://arxiv.org/abs/2507.11069) | [💻](https://github.com/728388808/alpha-NeuS) | [🎥](https://www.youtube.com/watch?v=R_Ixk3i_09g) | [🌐](https://jeongyun0609.github.io/TRAN-D/)]

- **Polarimetric Inverse Rendering for Transparent Shapes Reconstruction (TransPIR)** (2022) [[📄](https://arxiv.org/abs/2208.11836) | [💻](https://github.com/shaomq2187/TransPIR)]

- **NeTO: Neural Reconstruction of Transparent Objects with Self-Occlusion Aware Refraction-Tracing** (2023) [[📄](https://arxiv.org/abs/2303.11219) | [💻](https://github.com/shaomq2187/TransPIR) | [🌐](https://www.xxlong.site/NeTO/)]

- **NeRRF: 3D Reconstruction and View Synthesis for Transparent and Specular Objects with Neural Refractive-Reflective Fields** (2023) [[📄](https://arxiv.org/abs/2309.13039) | [💻](https://github.com/JunchenLiu77/NeRRF)]

- **TranSplat: Surface Embedding-guided 3D Gaussian Splatting for Transparent Object Manipulation** (2025) [[📄](https://arxiv.org/abs/2502.07840) | [💻](https://github.com/jeongyun0609/TranSplat) | [🎥](https://www.youtube.com/watch?v=O_atdUlaF4I)]

- **NU-NeRF: Neural Reconstruction of Nested Transparent Objects with Uncontrolled Capture Environment** (2023) [[📄](https://drive.google.com/drive/folders/1DP_aQ5GRow-Se4LpImYLjX3mah2__PSh) | [💻](https://github.com/78ij/NU-NeRF) | [🌐](http://geometrylearning.com/NU-NeRF/)]

- **TSGS: Improving Gaussian Splatting for Transparent Surface Reconstruction via Normal and De-lighting Priors** (2025) [[📄](https://arxiv.org/abs/2504.12799) | [💻](https://github.com/longxiang-ai/TSGS) | [🌐](https://longxiang-ai.github.io/TSGS/)]

- **Hash-NURF: Efficient Nested Transparent Object Reconstruction Using Multi-Resolution Hash Encoding** (2026) [[📄](https://www.scopus.com/pages/publications/105031429573) | [💻](https://github.com/SyouSanGin/Hash-NURF)]

- **TORM: Transparent Objects Reconstruction and Manipulation With Multi-View Segmentation** (2026) [[📄](https://www.scopus.com/pages/publications/105021962476)]

- **A Novel Multi-Cooperative Neural Radiance Field Reconstruction Method Based on Optical Properties for 3D Reconstruction of Scenes Containing Transparent Objects** (2026) [[📄](https://www.scopus.com/pages/publications/105031248685)]

- **NeRF-THO: Neural Radiance Fields for Transparent and Highlighted Objects** (2025) [[📄](https://www.scopus.com/pages/publications/105013352509)]

- **GlassMolder: Transparent Object Reconstruction With Silhouette-Guided Object-Centric Diffusion** (2025) [[📄](https://www.scopus.com/pages/publications/105006689247)]

- **Efficient Multi-Bounce Ray Tracing for Specular and Transparent Materials in NeRF** (2025) [[📄](https://www.scopus.com/pages/publications/105000445896)]

- **MMPNeRF: Multi-Modal Neural Rendering of Transparent Objects Using Color and Polarimetric Images** (2024) [[📄](https://www.scopus.com/pages/publications/105001501409)]

- **Differentiable Neural Surface Refinement for Modeling Transparent Objects** (2024) [[📄](https://www.scopus.com/pages/publications/85207259027)]

- **Novel View Synthesis Of Transparent Object From a Single Image** (2023) [[📄](https://www.scopus.com/pages/publications/85141129574)]

- **GlassGaussian: Extending 3D Gaussian Splatting for Realistic Imperfections and Glass Materials** (2025) [[📄](https://ieeexplore.ieee.org/document/10884729)]

- **α-Surf: Implicit Surface Reconstruction for Semi-Transparent and Thin Objects with Decoupled Geometry and Opacity** (2024) [[📄](https://ieeexplore.ieee.org/document/11125620)]

- **NEMTO: Neural Environment Matting for Novel View and Relighting Synthesis of Transparent Objects** (2023) [[📄](https://ieeexplore.ieee.org/document/10377001)]

- **NeuralTO: Neural Reconstruction and View Synthesis of Translucent Objects** (2024) [[📄](https://dl.acm.org/doi/10.1145/3658186)]

- **GLINT: Modeling Scene-Scale Transparency via Gaussian Radiance Transport** (2026) [[📄](https://arxiv.org/abs/2603.26181) | [💻](https://github.com/youngju-na/GLINT) | [🌐](https://youngju-na.github.io/GLINT/)]

- **RCTrans: Transparent Object Reconstruction in Natural Scene via Refractive Correspondence Estimation** (2025) [[📄](https://dl.acm.org/doi/10.1145/3757377.3763859)]

- **RefRef: A Synthetic Dataset and Benchmark for Reconstructing Refractive and Reflective Objects** (2025) [[📄](https://arxiv.org/abs/2505.05848) | [💻](https://github.com/YueYin27/refref) | [🌐](https://yueyin27.github.io/refref-page/)]


## Conclusion
Paper names all look similar, no? I guess we need a new SOTA technique other than NeRF and GS...

Hope it helps!

