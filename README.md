# Segmentação de Imagens RGB

Este projeto descreve os passos para segmentação de imagens RGB utilizando o conjunto de dados [Visible Human](https://www.nlm.nih.gov/databases/download/vhp.html), cortesia da U.S. National Library of Medicine, que contém imagens de tomografia computadorizada (TC) e ressonância magnética obtidas a partir de um cadáver masculino, com o objetivo de separar a região da imagem correspondente ao corpo humano do plano de fundo. 

1. Para diminuir a densidade dos pixels em cada imagem, utilize o aplicativo Diferenca:

    1.1. Selecione as imagens do conjunto de dados [Visible Human](https://www.nlm.nih.gov/databases/download/vhp.html);
    
    1.2. Determine o deltaRGB: serão comparados os pixels de cada par de imagem em ordem, caso a soma dos módulos das diferenças de cada canal RGB do par de pixel em questão for igual ou menor o valor do Delta, os pixels passrão a possuir a cor branca. Para o conjunto de dados [Visible Human](https://www.nlm.nih.gov/databases/download/vhp.html) utilizou-se deltaRGB = 4;
    
    1.3. Execute o algoritmo.
    
Como resultado do algoritmo é obtida para cada entrada uma imagem:

- imgNome-normmax-deltaRGB-valorDoDelta.png: contém apenas os pixels cuja soma dos módulos das diferenças de cada canal RGB dos pares de pixels for maior que o valor do Delta.

2. AmostraRGB

    2.1. Utilizando o aplicativo AmostraRGB selecione a tonalidade de interesse que é compatível com os tons encontrados na região de interesse;

    2.2. Selecione as imagens resultantes do passo 1;
    
    2.3. Determine o tamanho da amostra; O tamanho utilizado foi 1024;

    2.4. Execute o algoritmo.

Como resultados do algoritmo são apresentados 3 arquivos para cada imagem de entrada:

- imgNome-amostra01-cent-med-dp.txt: Contém os valores do centróide da imagem, da média das distâncias do centroide para cada pixel e do desvio padrão das distâncias.
- imgNome-amostra01-distância.txt: Contém as distâncias de cada pixel ao centróide.
- imgNome-amostra01-RGB.txt: Contém as amostras das tonalidades com suas classificações;

3. PerceptrontRGB

    3.1. Utilizando o aplicativo PerceptrontRGB selecione os arquivos resultantes da AmostraRGB que contém as amostras das tonalidades e suas classificações;

    3.2. Determine a quantidade de épocas, o valor mínimo de acurácia e a taxa de aprendizagem; Utilizou-de a quantidade máxima de épocas, acurácia = 99 e taxa de aprendizagem = 0.1;
    
    3.3. Execute o algoritmo.

Como resutado do algoritmo é apresentado para cada arquivo de entrada um arquivo de texto:

- imgNome-perceptron01-planoRGB.txt: contém o plano de corte que será utilizado na classificação.

4. PerceptroncRGB

    4.1. Coloque os planos de corte obtidos durante o treinamento na pasta onde se encontra o executável do aplicativo PerceptroncRGB;
    
    4.2. Utilizando o aplicativo PerceptroncRGB selecione as mesmas imagens que foram utilizadas durante a amostragem;
    
    4.2. Execute o algoritmo.

Como resultado do algoritmo são obtidas duas imagens:

- imgNome-perceptron01-pos.png: contém os pixels que foram classificados como positivos;
- imgNome-perceptron01-neg.png: contém os pixels que foram classificados como negativos.


5. Refinamento dos resultados

    5.1. Utilizando o aplicativo Superelipse selecione as imagens, com os pixeis classificados como positivos, resultantes do PerceptroncRGB;
    
    5.2. Determine os valores de x0, a, m, y0, b e n em ordem e separados por vírgula, como no exemplo: x0 = 1030, a = 540, m = 2, y0 = 535, b = 480, n = 4. Caso deseje utilizar mais de uma superelipse mantenha os valores de cada uma em uma linha. Caso as elipses mudem para cada imagem utilizada, salve um arquivo txt contendo os valores das elipses para cada imagem utilizando o terceiro botão "Save Equation"; As superelipses utilizadas para cada imagem se encontram na pasta ```Superelipses```, para utilizá-las coloque os arquivos de texto na mesma pasta que o executável.
    
    5.2. Execute o algoritmo.

Como resultado do algoritmo é obtida para cada entrada uma imagem:

- imgNome-superelipse.png: contém os pixeis que se encontram dentro das elipses determinadas para cada imagem.


6. Para observar o resultado em um espaço tridimensional, utilize o aplicativo PLYaltura:

    6.1. Selecione as imagens resultantes da diminuição da densidade;
    
    6.2. Determine a altura inicial e a distância entre as imagens de entrada no espaço;
    6.3. Execute o algoritmo.
    
Como resultado do algoritmo é obtido um arquivo PLY para cada imagem de entrada que pode ser visualizado utilizando o Meshlab:

- imgNome-RGB2PLY-altura-valorDaAltura.ply: contém os pixels da imagem representados em um espaço tridimensional.


Ao completar todos os passos os resultados obtidos utilizando o conjunto de dados [Visible Human](https://www.nlm.nih.gov/databases/download/vhp.html) pode ser encontrado na pasta ````Resultados````.
Na mesma pasta enncontram-se os frames do resultado empilhados utilizando o Meshlab e um vídeo com os mesmo.


