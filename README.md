English description below:



Treinamento de Modelo de Linguagem com TensorFlow

Neste projeto criei um model que é capaz de prever a próxima sequência de caracteres em textos de Shakespeare e também gerar novas frases com base em entradas fornecidas.

1. Download do Texto Base

Primeiramente, eu baixei o texto completo de Shakespeare, que é o dataset usado no treinamento.

2. Tokenização do Texto

Depois de obter o texto, eu o tokenizei em nível de caracteres. Isso significa que cada caractere foi tratado como um token único. 
Em seguida, criei um dicionário com todos os caracteres distintos e atribuí a cada um deles um índice numérico.

3. Codificação do Texto

Converti o texto original em uma sequência numérica usando os índices dos caracteres. Essa sequência foi dividida em duas partes:

Treinamento (80%)

Validação (20%)

4. Criação de Janelas de Sequências

Para preparar os dados de treinamento, separei o texto em pequenas janelas de sequência, onde cada janela contém um trecho do texto. 
Essas janelas servem para ensinar o modelo a prever o próximo caractere com base nos anteriores.

5. Preparação dos Dados

Organizei os dados em batches, o que ajuda a otimizar o treinamento. Também converti as sequências em formato one-hot.

6. Construção do Modelo

Criei o modelo usando camadas GRU.
A última camada do modelo usa a função softmax, que calcula a probabilidade de cada caractere ser o próximo na sequência.

7. Treinamento

Treinei o modelo utilizando a função de perda categórica esparsa (sparse_categorical_crossentropy). Para garantir um treinamento eficiente, utilizei callbacks como:

ModelCheckpoint: 

para salvar o modelo periodicamente.

EarlyStopping: 

para parar o treinamento caso o desempenho não melhore.

BackupAndRestore: 

para recuperar o progresso caso o treinamento seja interrompido.

8. Geração de Texto

Depois de treinar o modelo, usei uma função para gerar texto. Com uma entrada inicial, o modelo é capaz de prever o próximo caractere e continuar criando a sequência. 

Ajustei o nível de aleatoriedade na geração com o parâmetro de risco (risk).

9. Geração com GPT

Por curiosidade e comparação, integrei o modelo pré-treinado OpenAI GPT usando a biblioteca transformers. 

-------------------------------------------------------------------------------------------

Language Model Training with TensorFlow

In this project, I created a model capable of predicting the next character sequence in Shakespeare's texts and generating new sentences based on user inputs. 

Below, I outline the step-by-step process:

1. Downloading the Base Text

First, I downloaded the complete text of Shakespeare, which serves as the dataset for training.

2. Text Tokenization

After obtaining the text, I tokenized it at the character level, treating each character as a unique token.

Then, I created a dictionary of distinct characters and assigned a numeric index to each.

3. Text Encoding

I converted the original text into a numeric sequence using the character indices.

This sequence was divided into two parts:

Training (80%)

Validation (20%)

4. Creating Sequence Windows

To prepare the training data, I divided the text into small sequence windows, where each window contains a segment of the text.

These windows help the model learn to predict the next character based on the previous ones.


5. Data Preparation

I organized the data into batches, which optimize training.

The sequences were also converted to one-hot format.

6. Model Construction

I built the model using stacked GRU layers.

The model's final layer uses the softmax function, which calculates the probability of each character being the next in the sequence.

7. Training

I trained the model using the sparse categorical cross-entropy loss function. To ensure efficient training, I used callbacks such as:


ModelCheckpoint: 

saves the model periodically.

EarlyStopping: 

stops training if performance doesn’t improve.

BackupAndRestore: 

restores progress if training is interrupted.

8. Text Generation

After training the model, I used a function to generate text.

With an initial input, the model predicts the next character and continues creating the sequence.

The randomness of text generation is adjusted using the risk parameter.

9. GPT Integration

For curiosity and comparison, I integrated the pre-trained OpenAI GPT model using the transformers library.
