# 🔍 Digital Forensics Toolkit

*A multi-modal, evidence-based platform to combat digital misinformation through explainable AI.*

[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)](https://huggingface.co/)

## 🎯 Project Philosophy

**Moving beyond "black box" classifiers** - this toolkit acts as a comprehensive digital forensics lab that provides **evidence, context, and transparent reasoning** behind every analysis. We believe in empowering users with critical thinking tools rather than just binary "fake/real" scores.

## ✨ Key Features

### 🔤 Advanced Text Analysis
- **Cascading Evidence Retrieval**: Searches multiple knowledge bases for robust verification
- **RAG Pipeline**: State-of-the-art Retrieve-Augment-Generate system with FAISS vector search
- **Natural Language Inference**: Uses DeBERTa model for precise claim-evidence comparison
- **Human-Readable Explanations**: FLAN-T5 generates clear justifications for every verdict

### 🖼️ Comprehensive Image Forensics
- **Triple-Check System**: Authenticity, Context, and Content analysis
- **AI Detection**: Identifies AI-generated images with confidence scores
- **Error Level Analysis**: Forensic detection of image manipulation
- **Reverse Image Search**: Tracks image history across the web
- **In-Image OCR**: Extracts and analyzes text within images

### 🚀 Production-Ready Architecture
- **Full-Stack Application**: FastAPI backend with modern frontend
- **Containerized Deployment**: Ready for Hugging Face Spaces & cloud platforms
- **Optimized Performance**: Pre-loaded models with efficient lifecycle management
- **RESTful API**: Clean, documented endpoints for easy integration

## 🏗️ System Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Frontend      │    │   FastAPI        │    │   AI Models     │
│   (Vanilla JS)  │◄──►│   Backend        │◄──►│   & Services    │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                              │
                              │
                      ┌──────────────────┐
                      │   Data Sources   │
                      │  • Local KB      │
                      │  • Google API    │
                      │  • Web Search    │
                      └──────────────────┘
```

## 📦 Installation & Quick Start

### Prerequisites
```bash
Python 3.9+
Docker (optional)
Google Cloud Vision API key
```

### Local Development
```bash
# Clone the repository
git clone https://github.com/yourusername/digital-forensics-toolkit.git
cd digital-forensics-toolkit

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Add your API keys to .env

# Launch the application
uvicorn main:app --reload --port 8000
```

### Docker Deployment
```bash
# Build the image
docker build -t forensics-toolkit .

# Run the container
docker run -p 8000:8000 --env-file .env forensics-toolkit
```

Visit `http://localhost:8000` to access the application.

## 🔬 Technical Deep Dive

### Text Analysis Pipeline
1. **Cascading Evidence Retrieval**
   - Internal knowledge base (1M+ documents)
   - Google Fact Check API fallback  
   - Live web search as final resort

2. **Intelligent RAG System**
   - Embedding: `sentence-transformers/all-MiniLM-L6-v2`
   - Vector Store: FAISS for lightning-fast similarity search
   - Re-ranking: `cross-encoder/ms-marco-MiniLM-L-6-v2`
   - NLI Classification: `DeBERTa-v3-base-mnli-fever-anli`
   - Explanation: `google/flan-t5-base` summarization

### Image Analysis Modules
- **AI Detection**: `umm-maybe/AI-image-detector` model
- **Forensic Analysis**: Error Level Analysis with Pillow
- **Context Analysis**: Google Cloud Vision API (WEB_DETECTION, OCR, Safe Search)

## 🎨 User Interface

The frontend features a modern, responsive design with:
- **Dark theme** with animated gradient background
- **Glassmorphism** effects for professional appearance  
- **Dynamic report cards** for complex analysis results
- **Real-time loading** indicators and progress tracking

## 📊 Sample Output

### Text Analysis Report
```
✅ VERDICT: FALSE (92% confidence)

EVIDENCE:
• Fact-checkers at Reuters have confirmed this claim is inaccurate
• Official sources from the WHO contradict this statement
• Multiple independent investigations found no supporting data

EXPLANATION:
The claim contradicts established medical guidelines and has been 
debunked by multiple reliable sources. The evidence strongly supports 
that this information is misinformation.
```

### Image Analysis Report
```
🖼️ IMAGE ANALYSIS COMPLETE

Authenticity: 87% likely manipulated
AI Generation: 23% probability  
Web Context: Found 15 matching instances (first seen: 2019)
Extracted Text: "Click here for amazing offer!" (Sent for text analysis)
```

## 🔧 API Documentation

Once running, visit `/docs` for interactive API documentation featuring:
- Full endpoint specifications
- Request/response schemas
- Live testing interface

## 🌐 Deployment

### Hugging Face Spaces
```yaml
# See .github/workflows/deploy.yml for CI/CD pipeline
variables:
  HF_TOKEN: ${{ secrets.HF_TOKEN }}
  GOOGLE_API_KEY: ${{ secrets.GOOGLE_API_KEY }}
```

### Google Cloud Run
```bash
gcloud run deploy forensics-toolkit \
  --source . \
  --platform managed \
  --region us-central1 \
  --set-env-vars API_KEY=$GOOGLE_API_KEY
```

## 🤝 Contributing

We welcome contributions! 

## 📄 License

This project is licensed under the MIT License 

## 🙏 Acknowledgments

- Hugging Face for transformer models and hosting
- Google Fact Check Tools API
- FAISS team for vector search capabilities
- The open-source AI community

---

**Built with ❤️ for a more truthful digital world.**

*This tool is designed to assist critical thinking, not replace it. Always verify important information through multiple sources.*
