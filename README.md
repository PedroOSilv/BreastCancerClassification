
# Utilização de Redes Neurais Perceptron Multicamadas Para Classificação de Câncer de Mama

**Autor:** Pedro Paulo Araújo de P. e Silva  
**Instituição:** Universidade Federal de Mato Grosso do Sul  
**Curso:** Ciência da Computação  
**Data:** 4 de Setembro de 2024

---

## Introdução

Este trabalho aplica técnicas de redes neurais perceptron multicamadas (Multilayer Perceptron, MLP) em uma base de dados de casos de câncer de mama, bem como discute e compara resultados entre técnicas, indicando qual obteve resultados mais satisfatórios.

### Objetivos

1. Construir uma MLP para classificação dos tipos de cânceres e analisar resultados.
2. Construir uma segunda MLP com conjunto de atributos reduzidos (apenas atributos muito impactantes) e analisar resultados.

### Descrição da Base de Dados

A base de dados utilizada está disponível no site oficial da UCI desde 1995, e contém dados de casos de câncer de mama. As características foram calculadas a partir de uma imagem digitalizada de um aspirado de agulha fina (FNA) de uma massa mamária. A base possui 699 instâncias, sendo 458 do tipo benigno e 241 do tipo maligno. Os atributos são os seguintes:

1. Espessura do Aglomerado - Clump Thickness
2. Uniformidade do tamanho da célula - Uniformity of Cell Size
3. Uniformidade do formato da célula - Uniformity of Cell Shape
4. Perda de adesão marginal - Marginal Adhesion
5. Aumento do tamanho celular - Single Epithelial Cell Size
6. Núcleos soltos - Bare Nuclei
7. Cromatina “branda” - Bland Chromatin
8. Nucléolo normal - Normal Nucleoli
9. Mitoses - Mitoses

Cada instância pode ser classificada em dois tipos: benigno (0) e maligno (1).

## Metodologia

Para estudar qual MLP melhor se encaixa neste cenário, duas tentativas foram realizadas:

1. **Primeira MLP:**  
   - Camada de entrada com 9 neurônios com função de ativação leaky ReLU;
   - Seis camadas ocultas com neurônios variando de 8 a 3, todas com função de ativação leaky ReLU;
   - Camada de saída com 2 neurônios e função de ativação softmax.
   
2. **Segunda MLP:**  
   - Camada de entrada com 4 neurônios com função de ativação leaky ReLU;
   - Uma camada oculta com 3 neurônios com função de ativação leaky ReLU;
   - Camada de saída com 2 neurônios e função de ativação softmax.

Passos tomados para ambas as MLPs:

1. Importação da base de dados e conversão para o formato numpy.
2. Conversão para o formato tensor da biblioteca PyTorch.
3. Imputação de dados ausentes com o algoritmo KNN.
4. Treinamento do modelo.
5. Geração das métricas.

## Resultados e Discussões

### MLP 1

- Separação dos grupos: 20% para teste, 16% para validação e 64% para treino.
- O modelo apresentou menor erro de 0.3444 na época 9059 e uma taxa de acerto de 0.9571.
- Métricas do modelo:
  - Precisão: 0.8723
  - Revocação: 1.0
  - F1-score: 0.9318

### MLP 2

- A separação dos grupos foi realizada de forma idêntica à MLP 1.
- Com uma rede menor e selecionando os melhores atributos, o modelo convergiu mais rápido, com um erro de validação de 0.3454 na época 10846.
- Taxa de acerto de 0.9357.
- Métricas do modelo:
  - Precisão: 0.8478
  - Revocação: 0.9512
  - F1-score: 0.8965

## Conclusão

Apesar da redução dos atributos de 9 para 4 e das camadas da rede de 8 para 4, a diferença na taxa de acertos no conjunto de testes entre os dois modelos foi de apenas 0.0214. Isso justifica a etapa de pré-processamento de dados e seleção dos atributos corretos para o treinamento do modelo.

## Agradecimento

Agradeço especialmente ao meu primo Pedro A. de Abreu, estudante de medicina, pelo auxílio na identificação das características de maior influência no câncer de mama.
