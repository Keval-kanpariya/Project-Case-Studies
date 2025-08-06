<div align="center">
  <img src="https://placehold.co/150x150?text=K8sGPT+Logo" alt="K8sGPT logo - AI-powered Kubernetes diagnostics tool" width="150"/> 
  <span style="font-size: 40px; margin: 0 20px; vertical-align: middle;">+</span>
  <img src="https://placehold.co/150x150?text=Ollama+Logo" alt="Ollama logo - Local LLM runtime for private AI processing" width="150"/>
</div>

<h1 align="center">Harness AI to Unlock Kubernetes' Full Potential</h1>

<div align="center">
  <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License">
  </a>
  <a href="https://github.com/k8sgpt-ai/k8sgpt">
    <img src="https://img.shields.io/badge/K8sGPT-v0.4.14-blue" alt="K8sGPT Version">
  </a>
  <a href="https://ollama.ai">
    <img src="https://img.shields.io/badge/Ollama-Local%20LLM-orange" alt="Ollama">
  </a>
</div>

<br/>

**K8sGPT + Ollama** provides AI-powered Kubernetes diagnostics that keeps your cluster data private by running large language models locally.

## 🚀 Quick Start

### Prerequisites
- Kubernetes cluster
- kubectl configured with cluster access

### Installation
```bash
# Install K8sGPT
curl -LO https://github.com/k8sgpt-ai/k8sgpt/releases/download/v0.4.14/k8sgpt_amd64.deb
sudo dpkg -i k8sgpt_amd64.deb

# Install Ollama
curl -fsSL https://ollama.com/install.sh | sh

# Download a model (e.g., llama2)
ollama pull llama2

# Configure K8sGPT to use Ollama
k8sgpt auth setup --model ollama --backend ollama
