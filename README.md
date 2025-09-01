# # Projeto: Geração de Texto com LSTM (Shakespeare)

## 📌 Descrição
Este projeto utiliza **Redes Neurais Recorrentes (RNNs)** com camadas **LSTM** para gerar texto inspirado nas obras de Shakespeare. O modelo é treinado a partir de um corpus de texto e avaliado em diferentes temperaturas para observar variação de criatividade.

---

## 🔧 Tecnologias
- Python  
- TensorFlow / Keras  
- NumPy  

---

## 📂 Etapas do Código

### 1. Download e Pré-processamento
- Baixa o dataset de Shakespeare.  
- Converte o texto para **minúsculas**.  
- Seleciona uma fatia do texto (`300k → 800k`).  
- Cria mapeamentos:
  - `char_to_index`: caractere → índice  
  - `index_to_char`: índice → caractere  

### 2. Geração das Sequências
- Define:
  - `sequence_length = 100`  
  - `step_size = 3`  
- Cria sequências de entrada (X) e saída (y) em **one-hot encoding**.  

### 3. Construção do Modelo
- Modelo **Sequential** com:
  - Camada `LSTM(256)`  
  - Camada `Dense(vocab_size, activation='softmax')`  
- Função de perda: `categorical_crossentropy`  
- Otimizador: `RMSprop(lr=0.01)`  

### 4. Treinamento
- Batch size: `128`  
- Épocas: `20`  
- Loss reduzido de **2.63 → ~1.95**.  

### 5. Geração de Texto
- Função `sample`: ajusta previsões com **temperature**.  
- Função `generate_text`: gera texto a partir de uma **semente aleatória**.  
- Temperaturas testadas:
  - **0.2** → texto mais conservador.  
  - **0.8** → mais criativo.  
  - **0.9** → ainda mais variável.  

---

## 📊 Resultados
- Modelo conseguiu capturar o estilo de Shakespeare.  
- **Temperatura baixa (0.2)** → frases mais coerentes.  
- **Temperatura alta (0.8–0.9)** → maior criatividade, porém mais erros.  

---

## 💾 Salvamento
- Modelo salvo como:  
  ```bash
  shaksp.kera
