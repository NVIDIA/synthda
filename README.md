 # AutoSynthDa, under Project SynthDa  
Pose-Level Synthetic Data Augmentation for Action Recognition (Research Purposes Only)  
=============================================================
  
#### Licensed under NSCLv2, where users can use this noncommercially (which means research or evaluation purposes only) on NVIDIA Processors.
This project will download and install additional third-party open source software projects. Review the license terms of these open source projects before use.

![detailed_synthdablog-demo](https://github.com/user-attachments/assets/7ae09f18-2338-4cf2-ae52-fd569f31380a)
<a href="https://huggingface.co/spaces/nvidia/synthda-demo"><img 
      src="https://huggingface.co/datasets/huggingface/badges/resolve/main/open-in-hf-spaces-md-dark.svg" 
      alt="Open in Spaces" 
      style="height:20px;" /></a>
<a href="https://github.com/NVIDIA/synthda/blob/main/colab/brev_demo_generateSynthDa.ipynb"><img 
    src="https://img.shields.io/badge/Launch-Colab-yellow.svg" 
    alt="Launch Colab" 
    style="height:20px;" /></a>

**SynthDa** (aka **AutoSynthDa**) is an open-source toolkit that generates class-balanced, kinematically valid video clips by automatically **interpolating human poses** rather than rendering full photorealistic frames. The framework is designed to mitigate the issue of imbalanced datasets by creating synthetic data for minority action classes in action-recognition datasets without the need for additional sensors/modality. This only uses RGB videos to generate synthetic videos.  

Each component of our proposed framework can be swapped with models of your choice or components of your choice. For the augmentation optimization loop, we have used [action recognition net](https://github.com/NVIDIA/tao_tutorials/tree/main/notebooks/tao_launcher_starter_kit/action_recognition_net) from NVIDIA TAO Toolkit. We provided each of the components to be used individually or stringed together/automated for your specific use case. Our purpose is to enable improved synthetic data generation for human actions.

![image](https://github.com/user-attachments/assets/1fde62ce-67a6-4673-9341-78da4daa31e4)

### See our wiki pages for the full [set up instructions](https://github.com/NVIDIA/synthda/wiki/1.-Setting-Up-SynthDa) and [customization options](https://github.com/NVIDIA/synthda/wiki/2.-Customizing-SynthDa)

---

**Project By:**  Megani Rajendran (NVIDIA), Chek Tien Tan (SIT), Aik Beng Ng (NVIDIA), Indriyati Atmosukarto (SIT), Joey Lim Jun Feng (SIT), Triston Chan Sheen (SIT), Simon See (NVIDIA)  

An NVAITC APS project (NVIDIA). Co-supervised by Singapore Institute of Technology, a collaboration between NVAITC-APS and Singapore Institute of Technology  

**Special thanks:** Andrew Grant (NVIDIA)

---

## Why Pose-Level Augmentation?

| Capability                                                | **AutoSynthDa (Pose)**            |
|-----------------------------------------------------------|-----------------------------------|
| Fine-grained motion control                               | ✅ Improved on prior works         |
| Independence from textures                                | ✅ Improved on prior works         |
| Maintaining semantic labels and kinematic plausibility    | ✅ Improved on prior works         |

*Pose-level synthesis potentially keeps the joint semantics explicit, reduces visual artifacts, and allows customizable generation speed and quality on NVIDIA GPUs.*

Note that this code has only been developed and tested with NVIDIA Processors.

---

## Related Publications

| Year | Reference                                                                                  | Link |
|------|--------------------------------------------------------------------------------------------|------|
| 2026 | AutoPose: Pose-Mixing for Rare Human Video Data Augmentation to Enhance Recognition (MMM '26) | [Link]([https://developer.nvidia.com/blog/improving-synthetic-data-augmentation-and-human-action-recognition-with-synthda/](https://link.springer.com/chapter/10.1007/978-981-95-6960-1_44))|
| 2025 | NVIDIA TechBlog: Improving Synthetic Data Augmentation and Human Action Recognition with SynthDa  | [Link](https://developer.nvidia.com/blog/improving-synthetic-data-augmentation-and-human-action-recognition-with-synthda/)|
| 2024 | Designing a Usable Framework for Diverse Users in Synthetic Human Action Data Generation (Siggraph Asia '24) | [Link](https://dl.acm.org/doi/full/10.1145/3681758.3697986) |
| 2024 | Review on synergizing the Metaverse and AI-driven synthetic data: enhancing virtual realms and activity recognition in computer vision (Springer) | [Link](https://link.springer.com/article/10.1007/s44267-024-00059-6) |
| 2023 | SynthDa: Exploiting Existing Real-World Data for Usable and Accessible Synthetic Data Generation (Siggraph Asia '23) | [Link](https://dl.acm.org/doi/abs/10.1145/3610543.3626168) |
| 2023 | Exploring Domain Randomization’s Effect on Synthetic Data for Activity Detection (MetaCom '23) | [Link](https://ieeexplore.ieee.org/abstract/document/10271896) |
| 2022 | SynDa: a novel synthetic data generation pipeline for activity recognition (ISMAR '22) | [Link](https://ieeexplore.ieee.org/abstract/document/9974180) |

---

## Repository Structure  
## Minimal Setup Checklist

| Step | Command / Action | Notes |
|------|------------------|-------|
| **1 Install deps** | `pip install -r requirements.txt` | CUDA-enabled PyTorch recommended |
| **2 Clone sub-repos** | `git clone` the five required repos *(see list below)* | Keep the folder names unchanged |
| **3 Create `.env`** | Add your OpenAI key and paths to each repo | No key provided, you will need to add your own |
| **4 Download models** | Grab all checkpoints from [**setup wiki**](https://github.com/NVIDIA/synthda/wiki/Setting-Up-SynthDa) | Place files exactly as instructed |
| **5 Smoke-test** | Run each repo’s test script once | Fail-fast before running the full pipeline |
| **6 Automate Pipeline for your own use case** | Select your choice of CV model for the optimization loop and automate it using our components | Full pipeline automation as designed by user as each use case is different |


### Required External Repositories

```text
StridedTransformer-Pose3D/
text-to-motion/
joints2smpl/
SlowFast/
Blender-3.0.0/          (binary drop)
