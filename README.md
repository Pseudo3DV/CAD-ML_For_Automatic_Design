# CAD-ML For Automatic Design

- 2D/3D 자동 설계를 위한 CAD-ML 논문 리뷰 및 실험

## Purpose ✨

- 현업에서의 2D/3D 설계를 진행할 때 반복적인 작업을 해결하기위해 서포트할 수 있는 AI 연구개발
- 리뷰한 논문의 방법론에 얽혀 생각하지 않고 여러 관점에서 구현 가능한 다른 방법론을 떠올리고 공유할 수 있는 역량
- 오픈 소스가 존재하는 논문을 간단히 수정하여 실험해볼 수 있는 역량
- AI 설계한 결과를 3D 프린트 출력 대행을 통해 실체화 및 실용
- 장기적인 스터디를 진행할 경우 워크샵/논문 투고를 계획

## Activity Period ⏰

- 첫 모임: 9월 13일 / 오후 9시 / #Room-YB
- 정기 모임: 매주 토요일 오후 9시, #Room-YB

## Papers 📚

1.  [**CAD 모델 표현 학습 (CAD Model Representation Learning)**](#1-cad-모델-표현-학습-cad-model-representation-learning)
    * [암시적 표현 학습 (Implicit Representation Learning)](#11-암시적-표현-학습-implicit-representation-learning)
    * [위상 및 경계 표현 학습 (Topological & Boundary Representation Learning)](#12-위상-및-경계-표현-학습-topological--boundary-representation-learning)
    * [절차적 시퀀스 표현 학습 (Procedural Sequence Representation Learning)](#13-절차적-시퀀스-표현-학습-procedural-sequence-representation-learning)
2.  [**CAD 재구성 (CAD Reconstruction)**](#2-cad-재구성-cad-reconstruction)
    * [이미지 기반 재구성 (From Images)](#21-이미지-기반-재구성-from-images)
    * [포인트 클라우드 기반 재구성 (From Point Clouds)](#22-포인트-클라우드-기반-재구성-from-point-clouds)
    * [도면 및 스케치 기반 재구성 (From Drawings & Sketches)](#23-도면-및-스케치-기반-재구성-from-drawings--sketches)
3.  [**CAD 생성 및 편집 (CAD Generation & Manipulation)**](#3-cad-생성-및-편집-cad-generation--manipulation)
    * [순차적/파라메트릭 생성 (Sequential & Parametric Generation)](#31-순차적파라메트릭-생성-sequential--parametric-generation)
    * [직접 3D 모델 생성 (Direct 3D Model Generation)](#32-직접-3d-모델-생성-direct-3d-model-generation)
4.  [**대규모 언어 모델 활용 (Leveraging Large Language Models)**](#4-대규모-언어-모델-활용-leveraging-large-language-models)
    * [텍스트 기반 CAD 생성 및 편집 (Text-to-CAD Generation & Editing)](#41-텍스트-기반-cad-생성-및-편집-text-to-cad-generation--editing)
    * [대화형 설계 에이전트 (Conversational & Interactive Agents)](#42-대화형-설계-에이전트-conversational--interactive-agents)
    * [CAD 모델 분석 및 검토 (Analysis & Review)](#43-cad-모델-분석-및-검토-analysis--review)

### 1. CAD 모델 표현 학습 (CAD Model Representation Learning)

3D CAD 모델의 복잡한 구조를 딥러닝 모델이 효과적으로 처리할 수 있는 형태로 변환하는 연구들입니다.

#### 1.1. 암시적 표현 학습 (Implicit Representation Learning)
연속적인 함수(SDF, Occupancy 등)를 사용해 점이 형상 내/외부에 있는지 판별하는 방식으로 3D 모델을 표현합니다.

| Papers | Venue | Links | Cited by | Github |
| :--- | :--- | :--- | :--- | :--- |
| DeepSDF: Learning Continuous Signed Distance Functions for Shape Representation | CVPR 2019 | [Link](https://arxiv.org/abs/1901.05103) | 3583 | [Link](https://github.com/facebookresearch/DeepSDF) |
| Occupancy networks: Learning 3d reconstruction in function space | CVPR 2019 | [Link](https://arxiv.org/abs/1812.03828) | 2655 | [Link](https://github.com/autonomousvision/occupancy_networks) |
| A-SDF: Learning Disentangled Signed Distance Functions for Articulated Shape Representation | ICCV 2021 | [Link](https://arxiv.org/abs/2104.07645) | 260 | [Link](https://jitengmu.github.io/A-SDF/) |

#### 1.2. 위상 및 경계 표현 학습 (Topological & Boundary Representation Learning)
CAD 모델의 고유한 B-rep(경계 표현) 구조(면, 모서리, 정점 간의 관계)를 직접 학습하여 위상적 정보를 보존합니다.

| Papers | Venue | Links | Cited by | Github |
| :--- | :--- | :--- | :--- | :--- |
| BrepNet: A topological message passing system for solid models | CVPR 2021 | [Link](https://arxiv.org/pdf/2104.00706) | 185 | [Link](https://github.com/AutodeskAILab/BRepNet) |
| UV-Net: Learning Unoriented Voxel-wise Normal for 3D Shape Analysis | NeurIPS 2021 | [Link](https://arxiv.org/abs/2006.10211) | 165 | [Link](https://github.com/AutodeskAILab/UV-Net) |

#### 1.3. 절차적 시퀀스 표현 학습 (Procedural Sequence Representation Learning)
CAD 모델이 생성되는 '과정' 또는 '순서'를 학습하여, 설계 의도와 이력을 표현합니다.

| Papers | Venue | Links | Cited by | Github |
| :--- | :--- | :--- | :--- | :--- |
| Inferring CAD Modeling Sequences Using Zone Graphs | SIGGRAPH 2021 | [Link](https://arxiv.org/abs/2104.03900) | 133 | [Link](https://github.com/brownvc/zone-graphs) |

---

### 2. CAD 재구성 (CAD Reconstruction)

다양한 형태의 데이터로부터 3D CAD 모델을 자동으로 생성(역설계)하는 연구들입니다.

#### 2.1. 이미지 기반 재구성 (From Images)
| Papers | Venue | Links | Cited by | Github |
| :--- | :--- | :--- | :--- | :--- |
| CSG-Net: Neural Shape Parser for Constructive Solid Geometry | CVPR 2018 | [Link](https://arxiv.org/abs/1712.08290) | 275 | [Link](https://github.com/Hippogriff/CSGNet) |
| Img2CAD | ECCV 2024 | [Link](https://arxiv.org/abs/2410.03417) | 6 | [Link](https://github.com/qq456cvb/Img2CAD) |

#### 2.2. 포인트 클라우드 기반 재구성 (From Point Clouds)
| Papers | Venue | Links | Cited by | Github |
| :--- | :--- | :--- | :--- | :--- |
| PointNet: Deep Learning on Point Sets for 3D Classification and Segmentation | CVPR 2017 | [Link](https://arxiv.org/abs/1612.00593) | 20042 | [Link](https://github.com/charlesq34/pointnet) |
| PointNet++: Deep Hierarchical Feature Learning on Point Sets in a Metric Space | NeurIPS 2017 | [Link](https://arxiv.org/abs/1706.02413) | 12920 | [Link](https://github.com/charlesq34/pointnet2) |
| PIE-Net: Parametric Inference of B-spline Curves and Surfaces | CVPR 2020 | [Link](https://arxiv.org/abs/2007.04883) | 134 | [Link](https://github.com/wangxiaogang866/PIE-NET) |
| ParSeNet: A Parametric Surface Fitting Network for B-Rep Solid Model Reconstruction | ACM Transactions on Graphics 2021 | [Link](https://arxiv.org/pdf/2003.12181) | 114 | [Link](https://hippogriff.github.io/parsenet/) |

#### 2.3. 도면 및 스케치 기반 재구성 (From Drawings & Sketches)
| Papers | Venue | Links | Cited by | Github |
| :--- | :--- | :--- | :--- | :--- |
| Drawing2CAD: A Benchmark for Sketch-Based CAD | ICCV 2023 | [Link](https://arxiv.org/html/2508.18733v1) | 21 | [Link](https://github.com/lllssc/Drawing2CAD) |
| From 2D CAD Drawings to 3D Parametric Models: A Vision-Language Approach | ArXiv 2024 | [Link](https://arxiv.org/abs/2412.11892) | 0 | [Link](https://manycore-research.github.io/CAD2Program/) |

---

### 3. CAD 생성 및 편집 (CAD Generation & Manipulation)

딥러닝 생성 모델을 이용해 새로운 CAD 모델을 만들거나 기존 모델을 수정하는 연구들입니다.

#### 3.1. 순차적/파라메트릭 생성 (Sequential & Parametric Generation)
설계 명령어 시퀀스나 파라메트릭 스케치를 자동 회귀(Autoregressive) 방식으로 생성하여, 설계 과정 자체를 모델링합니다.

| Papers | Venue | Links | Cited by | Github |
| :--- | :--- | :--- | :--- | :--- |
| SketchGraphs: A Large-Scale Dataset for Modeling Relational Geometry in Computer-Aided Design | CVPR 2020 | [Link](https://arxiv.org/abs/2007.08506) | 162 | [Link](https://github.com/PrincetonLIPS/SketchGraphs) |
| DeepCAD: A Deep Generative Network for Computer-Aided Design Models | ICCV 2021 | [Link](https://arxiv.org/abs/2105.09492) | 129 | [Link](https://github.com/rundiwu/DeepCAD) |
| SkexGen: Autoregressive Generation of CAD Construction Sequences with Disentangled Codebooks | ECCV 2022 | [Link](https://arxiv.org/abs/2207.04632) | 52 | [Link](https://samxuxiang.github.io/skexgen/) |
| Vitruvion: A Generative Model of Parametric CAD Sketches | SIGGRAPH Asia 2022 | [Link](https://arxiv.org/abs/2109.14124) | 47 | [Link](https://github.com/PrincetonLIPS/vitruvion) |
| Engineering Sketch Generation for Computer-Aided Design | ArXiv 2021 | [Link](https://arxiv.org/abs/2104.09621) | 31 | N/A |
| Hierarchical Neural Coding for Controllable CAD Model Generation | ICML 2023 | [Link](https://arxiv.org/abs/2307.00149) | 49 | [Link](https://github.com/samxuxiang/hnc-cad) |

#### 3.2. 직접 3D 모델 생성 (Direct 3D Model Generation)
설계 과정을 건너뛰고, 조건(텍스트, 이미지 등)에 맞는 3D 모델 형상을 직접 생성합니다.

| Papers | Venue | Links | Cited by | Github |
| :--- | :--- | :--- | :--- | :--- |
| GenCAD-3D | ArXiv 2024 | [Link](https://arxiv.org/abs/2509.15246) | 0 | [Link](https://gencad3d.github.io/) |

---

### 4. 대규모 언어 모델 활용 (Leveraging Large Language Models)

LLM을 CAD 설계 프로세스에 접목하여 다양한 작업을 자동화하고 지원하는 연구들입니다.

#### 4.1. 텍스트 기반 CAD 생성 및 편집 (Text-to-CAD Generation & Editing)
자연어 설명, 지시, 대화 등을 입력받아 3D 모델을 생성하거나 수정합니다.

| Papers | Venue | Links | Cited by | Github |
| :--- | :--- | :--- | :--- | :--- |
| CLIP-Forge: Towards Zero-Shot Text-to-Shape Generation | CVPR 2022 | [Link](https://arxiv.org/abs/2110.02624) | 390 | [Link](https://github.com/AutodeskAILab/Clip-Forge) |
| Text2CAD: A Text-driven Platform for 3D CAD Model Generation and Manipulation | SIGGRAPH Asia 2022 | [Link](https://arxiv.org/abs/2409.17106) | 26 | [Link](https://github.com/SadilKhan/Text2CAD) |
| CADCrafter: A Bi-directional Transformer for Text-to-CAD | CVPR 2024 | [Link](https://arxiv.org/abs/2504.04753) | 22 | N/A |
| CAD-GPT: A Generative Foundational Model for Computer-Aided Design | ArXiv 2024 | [Link](https://arxiv.org/abs/2412.19663) | 0 | [Link](https://openiwin.github.io/CAD-GPT/) |

#### 4.2. 대화형 설계 에이전트 (Conversational & Interactive Agents)
대화형 인터페이스를 통해 사용자의 설계 작업을 돕거나, 사람과 협력하여 설계를 진행하는 에이전트를 개발합니다.

| Papers | Venue | Links | Cited by | Github |
| :--- | :--- | :--- | :--- | :--- |
| CADTalk: A Conversational Agent for CAD | ArXiv 2023 | [Link](https://arxiv.org/abs/2311.16703) | 11 | [Link](https://enigma-li.github.io/CADTalk/) |

#### 4.3. CAD 모델 분석 및 검토 (Analysis & Review)
LLM을 이용해 설계된 CAD 모델의 문제점을 분석하거나, 설계 요구사항을 충족하는지 자동으로 검토합니다.

| Papers | Venue | Links | Cited by | Github |
| :--- | :--- | :--- | :--- | :--- |
| CADReview: An LLM-based Review Agent for CAD Models | ArXiv 2024 | [Link](https://arxiv.org/abs/2505.22304) | 4 | [Link](https://cgl-pro.github.io/cadreview/) |

---

### Survey

- [Geometric Deep Learning for Computer-Aided Design: A Survey](https://arxiv.org/html/2402.17695v2)
- [Large Language Models for Computer-Aided Design: A Survey](https://arxiv.org/html/2505.08137v1)
- [A Survey on Deep Learning in 3D CAD Reconstruction](https://www.mdpi.com/2076-3417/15/12/6681)

<h2>Contributors 😃</h2>
<a href="https://github.com/Pseudo3DV/CAD-ML_For_Automatic_Design/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Pseudo3DV/CAD-ML_For_Automatic_Design" />
</a>
<br><br>

<h2>License 🗞</h2>

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).
