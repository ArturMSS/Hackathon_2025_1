
# 🍽️ Food Waste Detection - Computer Vision System  

**Detecta e classifica restos de alimentos em pratos de restaurantes para reduzir desperdício**  

## 📋 Índice  
- [Visão Geral](#-visão-geral)  
- [Tecnologias](#-tecnologias)  
- [Pré-requisitos](#-pré-requisitos)  
- [Instalação](#-instalação)  
- [Como Usar](#-como-usar)  
- [Estrutura do Projeto](#-estrutura-do-projeto)  
- [Exemplos](#-exemplos)  
- [Licença](#-licença)  

## 🌟 Visão Geral  
Sistema de visão computacional que:  
✅ Identifica tipos de alimentos desperdiçados  
✅ Calcula confiança da detecção  
✅ Gera visualizações com bounding boxes  
✅ Pode ser integrado a sistemas de gestão de restaurantes  

## 🛠️ Tecnologias  
| Tecnologia | Função |  
|------------|--------|  
| ![Roboflow](https://img.shields.io/badge/Roboflow-FF3621?style=flat&logo=roboflow&logoColor=white) | Treinamento e deploy de modelos |  
| ![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat&logo=opencv&logoColor=white) | Processamento de imagens |  
| ![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white) | Lógica principal |  

## ⚙️ Pré-requisitos  
- Conta no [Roboflow](https://roboflow.com)  
- Python 3.8+  
- Google Colab ou Jupyter Notebook  

## 🚀 Instalação  
```bash
# Instale as dependências
!pip install roboflow inference-sdk opencv-python pillow matplotlib
```

## 💻 Como Usar  
### 1. Configuração Inicial  
```python
from roboflow import Roboflow

rf = Roboflow(api_key="sua_chave_aqui")
project = rf.workspace("seu_workspace").project("seu_projeto")
model = project.version(2).model
```

### 2. Processamento de Imagem  
```python
import cv2

def process_image(image_path):
    img = cv2.imread(image_path)
    img = cv2.resize(img, (640, 640))
    return cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

### 3. Execução Completa  
```python
# Upload da imagem
from google.colab import files
uploaded = files.upload()

# Análise
results = model.predict(list(uploaded.keys())[0], confidence=40).json()

# Visualização
for pred in results['predictions']:
    print(f"✅ {pred['class']} - {pred['confidence']:.0f}%")
```


## 📜 Licença  
MIT License - Consulte o arquivo [LICENSE](LICENSE) para detalhes.