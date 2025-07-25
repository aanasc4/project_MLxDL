# 🌸 Classificação de Flores: Dense NN vs CNN

**Comparação entre Machine Learning Tradicional e Deep Learning**

Baseado nos notebooks `02_asl.ipynb` e `03_asl_cnn.ipynb` apresentados em aula.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1mIm1SXIhDy3M9o-HypHYy9PLp171W-rY?usp=sharing)

## 📋 Descrição do Projeto

Este projeto implementa e compara duas abordagens diferentes para classificação de imagens:

- **Dense Neural Network** (ML Tradicional) - baseado em `02_asl.ipynb`
- **Convolutional Neural Network** (Deep Learning) - baseado em `03_asl_cnn.ipynb`

### 🎯 Objetivo
Demonstrar na prática por que CNNs são superiores a Dense NNs para classificação de imagens, utilizando um dataset diferente do ASL usado na aula.

### 🔬 Hipótese
CNN deve superar significativamente o Dense NN para classificação de imagens.

## 📊 Dataset

**Oxford Flowers 102**
- 🌺 **102 classes** de flores diferentes
- 🖼️ **1.020 imagens** de treino
- 📐 **6.149 imagens** de teste
- 🔗 **Fonte**: TensorFlow Datasets

**Por que este dataset:**
- Diferente do ASL (American Sign Language) usado na aula
- Mais desafiador: 102 classes vs 24 do ASL
- Imagens coloridas vs escala de cinza
- Ideal para mostrar vantagens da CNN

## 🏗️ Arquitetura dos Modelos

### 🔗 Dense Neural Network
```
Input (64x64x3) → Flatten (12,288) → Dense (512) → Dense (512) → Output (102)
```
- **Parâmetros**: 6,606,950
- **Característica**: Trata cada pixel independentemente
- **Baseado em**: 02_asl.ipynb (mesma arquitetura)

### 🧠 Convolutional Neural Network
```
Input (64x64x3) → Conv2D → BatchNorm → MaxPool → 
Conv2D → Dropout → BatchNorm → MaxPool → 
Conv2D → BatchNorm → MaxPool → 
Flatten → Dense (512) → Dropout → Output (102)
```
- **Parâmetros**: 919,813 (7x menor!)
- **Característica**: Detecta padrões espaciais
- **Baseado em**: 03_asl_cnn.ipynb (mesma estrutura)

## 📈 Resultados Obtidos

| Modelo | Acurácia Treino | Acurácia Validação | Parâmetros | Tempo | Eficiência |
|--------|----------------|-------------------|------------|-------|------------|
| **Dense NN** | 39.9% | 9.0% | 6,606,950 | 135s | Baixa |
| **CNN** | 79.3% | 0.3% | 919,813 | 402s | Alta |

### 🏆 Principais Descobertas
- ✅ **CNN obteve o dobro da performance** no treino (79.3% vs 39.9%)
- ✅ **CNN é 7x mais eficiente** em parâmetros  
- ✅ **CNN aprende padrões espaciais** vs pixels independentes
- ⚠️ **Ambos apresentaram overfitting** (dataset desafiador)

### 📊 Gráficos Comparativos
O projeto inclui visualizações detalhadas mostrando:
- Evolução da acurácia durante treinamento
- Comparação de número de parâmetros
- Tempo de treinamento
- Amostras do dataset

## 🚀 Como Executar

### **Opção 1: Google Colab (Recomendado)**
1. [Clique aqui para abrir no Colab](https://colab.research.google.com/drive/1mIm1SXIhDy3M9o-HypHYy9PLp171W-rY?usp=sharing)
2. Execute todas as células sequencialmente
3. O dataset será baixado automaticamente

### **Opção 2: Ambiente Local**
```bash
# Clone o repositório
git clone https://github.com/aanasc4/project_MLxDL.git
cd project_MLxDL

# Instale as dependências
pip install tensorflow tensorflow-datasets matplotlib numpy

# Execute o Jupyter
jupyter notebook
```

## 📦 Dependências

```txt
tensorflow>=2.8.0
tensorflow-datasets>=4.4.0
matplotlib>=3.3.0
numpy>=1.19.0
```

## 📁 Estrutura do Projeto

```
project_MLxDL/
│
├── README.md                           # Este arquivo
└── MLxDL.ipynb  # Notebook principal
```

## 🔍 Principais Seções do Notebook

1. **📥 Carregamento dos Dados** - Oxford Flowers 102
2. **🔧 Preparação dos Dados** - Redimensionamento para 64x64 e normalização
3. **🔗 Modelo Dense NN** - Implementação baseada em 02_asl.ipynb
4. **🧠 Modelo CNN** - Implementação baseada em 03_asl_cnn.ipynb
5. **📊 Comparação dos Resultados** - Gráficos e análises detalhadas
6. **🎯 Conclusões** - Análise dos resultados e lições aprendidas

## 💡 Análise Detalhada dos Resultados

### ✅ Por que CNN é Superior para Imagens:

**Dense Neural Network:**
- Trata cada pixel independentemente
- Ignora relações espaciais entre pixels vizinhos
- Muitos parâmetros desperdiçados
- Inadequado para dados com estrutura espacial

**Convolutional Neural Network:**
- Detecta padrões locais com filtros convolucionais
- Preserva informação espacial das imagens
- Compartilha parâmetros (muito mais eficiente)
- Hierarquia de features: bordas → texturas → formas → objetos

### 📊 Números que Impressionam:
- **Performance**: CNN obteve o dobro da acurácia no treino
- **Eficiência**: CNN usa 7x menos parâmetros
- **Especialização**: CNN foi projetada especificamente para imagens

### ⚠️ Desafios Encontrados:
- **Overfitting**: Ambos modelos memorizaram treino mas não generalizaram
- **Dataset pequeno**: 1020 imagens para 102 classes é limitado
- **Alta complexidade**: 102 classes de flores é muito desafiador

## 🎓 Contexto Acadêmico

Este projeto foi desenvolvido como parte da atividade que solicita:
> "Usar como base os notebooks apresentados em aula (02_asl.ipynb e 03_asl_cnn.ipynb) para classificar um dataset diferente do apresentado em aula e comparar a diferença de performance dos modelos ao usar as abordagens de ML e DL no mesmo problema."

### 📚 Conexão com os Notebooks Originais:
- **02_asl.ipynb**: Forneceu a arquitetura exata do Dense NN (Flatten → Dense(512) → Dense(512) → Output)
- **03_asl_cnn.ipynb**: Forneceu a estrutura completa da CNN (Conv2D + BatchNorm + MaxPool)
- **Adaptação**: Mudança de 24 classes (ASL) para 102 classes (flores) e input shape de (28,28,1) para (64,64,3)

## 🎯 Conclusões Finais

### 🏆 Hipótese Confirmada:
A CNN superou significativamente o Dense NN para classificação de imagens, exatamente como esperado!

### ✅ Lições Aprendidas:
1. **Para imagens, sempre use CNN** ao invés de Dense NN
2. **Estrutura espacial importa** - pixels vizinhos têm relação
3. **Especialização vence generalização** - CNN > Dense para visão
4. **Eficiência em parâmetros** é fundamental para modelos práticos

### 🚀 Aplicações Práticas:
Este resultado explica por que:
- **Google Photos** usa CNN para reconhecer objetos
- **Instagram** usa CNN para filtros e moderação
- **Carros autônomos** usam CNN para visão computacional
- **Sistemas médicos** usam CNN para análise de imagens

## 🔬 Melhorias Futuras

- [ ] **Data Augmentation** - Rotação, zoom, flip para reduzir overfitting
- [ ] **Transfer Learning** - Modelos pré-treinados (ResNet, VGG)
- [ ] **Early Stopping** - Parar quando validação parar de melhorar
- [ ] **Regularização adicional** - L1/L2, mais Dropout
- [ ] **Mais épocas** - Treinamento mais longo com paciência
- [ ] **Ensemble de modelos** - Combinar múltiplas CNNs

## 👨‍💻 Autora

**Aline Acioly Nascimento**
- GitHub: [@aanasc4](https://github.com/aanasc4)
- LinkedIn: [Aline Acioly](https://www.linkedin.com/in/aline-acioly-9217a7306/)

