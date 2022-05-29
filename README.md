# Segmentacao

Este projeto descreve a implementação de um classificador linear, na forma da rede neural Perceptron com duas camadas, com o propósito de obter o melhor plano de corte que será utilizado em tarefas de segmentação de imagens digitais. O conjunto de dados utilizado durante os testes foi o Visible Man, que contém imagens de tomografia computadorizada (TC) e ressonância magnética obtidas a partir de um cadáver masculino. A região de interesse é a parte que corresponde ao corpo humano em cada imagem digital e a rede neural é aplicada para separar essa região de interesse do plano de fundo da imagem. 
Para alcançar os objetivos, deve-se seguir os seguintes passos:

1. Amostragem01

    1.1. Utilizando o aplicativo AmostraRGB selecione a tonalidade de interesse que é compatível com os tons encontrados na região de interesse;

    1.2. Selecione as imagens que serão segmentadas;
    
    1.3. Determine o tamanho da amostra;

    1.4. Execute o algoritmo.

Como resultados do algoritmo são apresentados arquivos 3 arquivos para cada imagem de entrada:

- img-amostra01-cent-med-dp.txt: Contém os valores do centróide da imagem, da média das distâncias do centroide para cada pixel e do desvio padrão das distâncias.
- img-amostra01-distância.txt: Contém as distâncias de cada pixel ao centróide.
- img-amostra01-RGB.txt: Contém as amostras das tonalidades com suas classificações;

2. Treinamento do Perceptron01

    2.1. Utilizando o aplicativo PerceptrontRGB selecione os arquivos resultantes da amostragem01 que contém as amostras das tonalidades e suas classificações;

    2.2. Determine a quantidade de épocas, o valor mínimo de acurácia e a taxa de aprendizagem;
    
    2.3. Execute o algoritmo.

Como resutado do algoritmo é apresentado para cada arquivo de entrada um arquivo com o plano de corte que será utilizado na classificação.

3. Classificação do Perceptron01

    3.1. Coloque os planos de corte obtidos durante o treinamento na pasta onde se encontra o executável do aplicativo PerceptroncRGB;
    
    3.2. Utilizando o aplicativo PerceptroncRGB selecione as mesmas imagens que foram utilizadas durante a amostragem;
    
    3.2. Execute o algoritmo.

Como resultado do algoritmo são obtidas duas iamgens uma com os pixels que foram classificados como positivos e outra com os negativos.

4. Amostragem02

    4.1. Utilizando o aplicativo AmostraXYd selecione as imagens resultantes da classificação do Perceptron01;

    4.2. Determine o valor de k: o valor de k é utilizado na determinação da classificação dos pixeis durante a amostragem. Os pixeis cuja distância ao centroide é menor que a distância média somado a k multiplicado pelo desvio padrão das distâncias, participarão do conjunto de amostras positivas, os demais pixeis participarão do conjunto de amostras negativos;
    
    4.3. Determine o tamanho da amostra;

    4.4. Execute o algoritmo.

Como resultados do algoritmo é obtida um arquivo contendo as amostras das distâncias com suas classificações.

5. Treinamento do Perceptron02

    5.1. Utilizando o aplicativo PerceptrontXYd selecione os arquivos resultantes da amostragem02;

    5.2. Determine a quantidade de épocas, o valor mínimo de acurácia e a taxa de aprendizagem;
    
    5.3. Execute o algoritmo.

Como resutado do algoritmo é apresentado para cada arquivo de entrada um arquivo com o plano de corte que será utilizado na classificação.

6. Classificação do Perceptron02

    3.1. Coloque os planos de corte obtidos durante o treinamento na pasta onde se encontra o executável do aplicativo PerceptroncXYd;
    
    3.2. Utilizando o aplicativo PerceptroncXYd selecione as mesmas imagens que foram utilizadas durante a amostragem;
    
    3.2. Execute o algoritmo.

Como resultado do algoritmo são obtidas duas iamgens uma com os pixels que foram classificados como positivos e outra com os negativos.

7. Refinamento dos resultados

    7.1. Utilizando o aplicativo Superelipse selecione as imagens resultantes da classificação do Perceptron02;
    
    7.2. Determine os valores de x0, a, m, y0, b e n em ordem e separados por vírgula, como no exemplo: x0 = 1030, a = 540, m = 2, y0 = 535, b = 480, n = 4. Caso deseje utilizar mais de uma superelipse mantenha os valores de cada uma em uma linha. Caso as elipses mudem para cada imagem utilizada, salve um arquivo txt contendo os valores das elipses para cada imagem utilizando o terceiro botão "Save Equation";
    
    7.2. Execute o algoritmo.

Como resultado do algoritmo é obtida para cada entrada uma imagem contendo os pixeis que se encontram dentro das elipses determinadas para cada imagem.

8. Para diminuir a densidade dos pixels em cada imagem, utilize o aplicativo Diferenca:

    8.1. Selecione as imagens resultantes do refinamento;
    
    8.2. Determine o deltaRGB: serão comparados os pixels de cada par de imagem em ordem, caso a soma dos módulos das diferenças de cada canal RGB do par de pixel em questão for igual ou menor o valor do Delta, os pixels passrão a possuir a cor branca;
    
    8.3. Execute o algoritmo.
    
Como resultado do algoritmo é obtida para cada entrada uma imagem contendo apenas os pixels cuja soma dos módulos das diferenças de cada canal RGB dos pares de pixels for maior que o valor do Delta.

9. Para observar o resultado em um espaço tridimensional, utilize o aplicativo PLYaltura:

    9.1. Selecione as imagens resultantes da diminuição da densidade;
    
    9.2. Determine a altura inicial e a distância entre as imagens de entrada no espaço;
    
    9.3. Execute o algoritmo.
    
Como resultado do algoritmo é obtido um arquivo PLY para cada imagem de entrada que pode ser visualizado utilizando o Meshlab.


Ao completar todos os passos os resultados obtidos utilizando o conjunto de dados Visible Human pode ser encontrado na pasta ````Resultados````.



