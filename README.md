# 📡 Projeto 4 — Classificação de Radar Ionosférico com Rede Adaline

**Disciplina:** PAM0466 – Sistemas Inteligentes  
**Semestre:** 2026.1  
**Docente:** Pedro Thiago Valério de Souza  
**Instituição:** Universidade Federal Rural do Semi-Árido (UFERSA) — Centro Multidisciplinar Pau dos Ferros  
**Discentes:** Maria Karoline e Moisés Guilherme

---

## 📋 Descrição

Este projeto implementa uma **Rede Adaline** para classificação automática de retornos de radar ionosférico, distinguindo sinais com estrutura eletrônica coerente (*good*, classe +1) daqueles sem estrutura (*bad*, classe −1), a partir do dataset Ionosphere da UCI.

---

## 📁 Estrutura do Repositório

```
├── adaline_ionosfera.ipynb   # Notebook principal com código e respostas
├── ionosphere.data           # Dataset (baixado automaticamente pelo notebook)
└── README.md                 # Este arquivo
```

---

## 📦 Dataset

O projeto utiliza o [Ionosphere Dataset (UCI)](https://archive.ics.uci.edu/ml/datasets/Ionosphere), coletado pelo sistema de radar Goose Bay (Canadá) e contribuído pelo Laboratório de Física Aplicada da Universidade Johns Hopkins.

- **351 amostras** de retornos de radar
- **34 atributos** contínuos (valores complexos de autocorrelação de pulsos de radar)
- **Rótulo binário:** `good` (+1) — estrutura ionosférica detectada | `bad` (−1) — sem estrutura coerente
- Distribuição: 225 amostras *good* / 126 amostras *bad*

O dataset é baixado automaticamente pela primeira célula do notebook. Caso falhe, baixe manualmente em:  
`https://archive.ics.uci.edu/ml/machine-learning-databases/ionosphere/ionosphere.data`

---

## ⚙️ Instalação das Dependências

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

---

## 🚀 Como Executar

1. Clone o repositório:
```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
```

2. Instale as dependências:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

3. Abra o notebook:
```bash
jupyter notebook adaline_ionosfera.ipynb
```

4. Execute todas as células em ordem (**Executar Tudo**).

---

## 📌 Atividades Desenvolvidas

### Atividade 1 — Preparação dos Dados
- Recodificação: *good* → +1, *bad* → −1
- Verificação de valores ausentes e atributos constantes
- Normalização Z-score
- **Resposta:** Justificativa algébrica da necessidade da normalização para estabilidade da regra Delta

### Atividade 2 — Adaline e Estudo da Taxa de Aprendizagem
- Divisão estratificada 80% treino / 20% teste
- Treinamento com η ∈ {10⁻⁴, 10⁻³, 10⁻², 5×10⁻², 10⁻¹} e N=200 épocas
- Curvas de convergência da função de perda por época
- Escolha do melhor η

### Atividade 3 — Avaliação do Modelo
- Matriz de confusão no conjunto de teste
- Acurácia global, precisão, recall e F1-score por classe

### Atividade 4 — Análise do Erro Crítico
- **Resposta:** Identificação do erro mais crítico (falso negativo para *bad*) e justificativa para priorizar o recall da classe *bad* em aplicações de monitoramento real

---

## 📊 Resultados Principais

| Métrica | Valor |
|---------|-------|
| Melhor η | 0,01 |
| Acurácia no teste | ~85–90% |
| Erro mais crítico | Falso Negativo (*bad* classificado como *good*) |

---

## 🔍 Conclusões

A Adaline mostrou boa adequação para este problema de classificação binária. A normalização Z-score foi essencial para a estabilidade da regra Delta. Em aplicações de monitoramento ionosférico real, o recall da classe *bad* deve ser priorizado, pois falhar na detecção de ausência de estrutura pode resultar em perda de comunicações ou falha em sistemas de GPS.
