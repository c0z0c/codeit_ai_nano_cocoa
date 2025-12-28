
# 🎨 소상공인을 위한 AI 광고 콘텐츠 생성 서비스 (나노 코코아)

![Python](https://img.shields.io/badge/Python-3.11-blue)
![Streamlit](https://img.shields.io/badge/Streamlit-1.28-red)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0-orange)
![GCP](https://img.shields.io/badge/GCP-L4%20GPU-green)

> **"디자인 전문 지식 없이도, 클릭 몇 번으로 우리 가게 홍보물 완성!"**
> 생성형 AI(Generative AI)를 활용하여 소상공인의 마케팅 진입 장벽을 낮추는 원스톱 콘텐츠 제작 솔루션입니다.

---

## 📅 프로젝트 정보
* **팀 명**: sprint-ai-chunk2-03 (3팀)
* **기간**: 2025.12.29 ~ 2026.01.29
* **목표**: 소상공인 대상 마케팅 콘텐츠(이미지, 문구) 자동 생성 웹 서비스 구현

---

## 🛠 주요 기능 (Features)

| 기능 | 설명 | 사용 모델/기술 |
| :--- | :--- | :--- |
| **📢 광고 문구 생성** | 상품 특징과 톤앤매너를 입력하면 매력적인 카피라이팅 제안 | `GPT-4o mini` / `Fine-tuned LLM` |
| **🖼️ 홍보 이미지 생성** | 텍스트 프롬프트로 고퀄리티 제품/홍보 이미지 생성 | `Stable Diffusion XL` / `LoRA` |
| **🎨 배경 합성 (In-painting)** | 제품 사진은 유지하고 배경만 어울리는 장소로 변경 | `ControlNet` / `In-painting` |
| **✏️ 스케치 완성** | 대략적인 손그림을 고품질 일러스트/사진으로 변환 | `Sketch-to-Image` |

*(※ 실제 구현 확정된 기능 위주로 수정해주세요)*

---

## 🏗️ 아키텍처 및 기술 스택 (Tech Stack)

### Infrastructure
* **Cloud**: Google Cloud Platform (GCP)
* **GPU**: NVIDIA L4 (24GB VRAM)
* **OS**: Ubuntu 22.04 LTS

### AI & Modeling
* **Framework**: PyTorch, HuggingFace Diffusers
* **Base Models**: Stable Diffusion, OpenAI API
* **Techniques**: LoRA Fine-tuning, ControlNet, Prompt Engineering

### Service & Frontend
* **UI**: Streamlit
* **Deployment**: GCP VM (Port 8501)

---

## 📂 디렉토리 구조 (검토중 예)

```bash
sprint-ai-chunk2-03-project/
├── 📂 assets/          # 리소스 파일 (이미지, 로고 등)
├── 📂 data/            # 데이터셋 (샘플)
├── 📂 models/          # 모델 가중치 또는 로드 스크립트
├── 📂 src/             # 소스 코드
│   ├── app.py          # Streamlit 메인 실행 파일
│   ├── generation.py   # 생성 모델 관련 로직
│   └── utils.py        # 유틸리티 함수
├── .gitignore          # Git 제외 파일 목록
├── requirements.txt    # 의존성 패키지 목록
└── README.md           # 프로젝트 설명 문서

```

---

## 🚀 설치 및 실행 가이드 (Getting Started)

### 1. 환경 설정 (Prerequisites)

이 프로젝트는 **Python 3.11** 환경에서 동작합니다. `conda` 가상환경 사용을 권장합니다.

```bash
# 가상환경 생성 및 활성화
conda create -n ai-ad-service python=3.11
conda activate ai-ad-service

```

### 2. 패키지 설치 (Installation)

```bash
pip install -r requirements.txt

```

### 3. API 키 설정

프로젝트 루트 경로에 `.env` 파일을 생성하고 키를 입력하세요.

```env
OPENAI_API_KEY=sk-proj-...
HUGGINGFACE_TOKEN=hf_...

```

### 4. 실행 (Run)

```bash
streamlit run src/app.py

```

브라우저에서 `http://localhost:8501`로 접속하여 서비스를 확인합니다.

---

## 👥 팀원 소개 (Members)

| 역할 | 이름 (ID) | 담당 업무 | Github |
| --- | --- | --- | --- |
| **PM** | 박지윤(spai0000) | 일정 관리, 기획 총괄, 데이터 수집 | [@id](https://github.com/) |
| **xx** | 김명환 (spai0433) | 이미지 생성 모델 파인튜닝, 성능 평가 | [@id](https://c0z0c.github.io/) |
| **xx** | 이영희 (spai0000) | 모델 최적화, 추론 파이프라인 구축 | [@id](https://github.com/) |
| **xx** | 박민수 (spai0000) | Streamlit UI 개발, 백엔드 연동 | [@id](https://github.com/) |

---

## 📝 산출물 (Outputs)

* [📄 최종 보고서 (PDF)](https://www.google.com/search?q=./reports/Final_Report.pdf) *(링크 연결 예정)*
* [📊 발표 자료 (PPT)](https://www.google.com/search?q=./reports/Presentation.pptx) *(링크 연결 예정)*
* [의심스러운 링크 삭제됨] *(선택 사항)*

---

### License

This project is licensed under the MIT License.

---

### 💡 추가 팁: 리포지토리 초기 설정 시 주의사항

1.  **`.gitignore` 파일 필수 생성**:
    * Github에 올리면 안 되는 파일들을 자동으로 제외해 줍니다.
    * Python 프로젝트용 `.gitignore` 템플릿을 사용하고, 특히 **`.env` (API 키)**, **`__pycache__/`**, **대용량 모델 파일(.pt, .safetensors)**이 올라가지 않도록 주의하세요.

2.  **`requirements.txt` 관리**:
    * 팀원들이 동일한 환경에서 작업하려면 설치된 라이브러리 목록을 공유해야 합니다.
    * 생성 명령어: `pip freeze > requirements.txt`

3.  **스크린샷 추가**:
    * 추후 개발이 진행되면 `README.md` 상단에 서비스 구동 화면 스크린샷(GIF 또는 이미지)을 넣으면 프로젝트의 완성도가 훨씬 높아 보입니다.

