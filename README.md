# Projeto Dumped

Visando o desenvolvimento de uma lixeira inteligente e com alta interatividade, a equipe técnica buscou tecnologias capazes de executar o projeto. O [YOLOv5](https://github.com/ultralytics/yolov5) é a última release da família YOLO, que foi inicialmente introduzido ao mercado como o primeiro modelo de detecção de objetos que combinava previsão de bounding box e classificação de objetos em um único lugar. Com sua nova implementação no framework PyTorch, ficou muito mais leve e de fácil uso, por conta dessas características se tornou a base para o desenvolvimento do modelo de detecção de lixo eletrônico do projeto.

## Técnica aplicada em machine leaning
*Deep Neural Network* para visão computacional usando Yolov5 e Pytorch.

## Setup do YOLOv5: 

- Para criar a estrutura de arquivos necessária para o uso dessa ferramenta é preciso clonar o repositório da Ultralytics voltado especificamente para essa configuração.

- Instalação das dependências através de arquivo de texto requirements.txt baixado previamente no comando acima (`!pip install -qr requirements.txt`)

- Imports dessa etapa: Torch (aceleração baseada em GPU), Image e clear_output do IPython.display (dispor imagens) e gdrive_download (Para o download do modelo)


## Download da versão customizada de detecção de objetos do YOLOv5:

- Extração da base de dados já no formato PyTorch utilizando um link específico direto do Roboflow 

## Personalização da configuração de treinamento:

- Identificação e concatenação do arquivo data.yaml, personalizado previamente pelo Roboflow;
- Customização do writefile do IPython para a escrita de variáveis;

## Treino do modelo:

O treino é feito através do seguinte comando:<br>
`!python train.py --img 416 --batch 16 --epochs 100 --data '../data.yaml' --cfg ./models/custom_yolov5s.yaml --weights '' --name yolov5s_results  --cache`

As variáveis no comando são:
- Img: define o tamanho das imagens a serem treinadas (previamente definidas na etapa de tratamento de dados, aqui apenas apontada);
- batch: determina o tamanho do batch (número de unidades de treinamento a serem utilizadas em uma iteração)
- epochs: determina o número de epochs de treinamento (número de vezes que o algoritmo de aprendizado vai rodar, considerando todo o dataset); 
- data: indicador do caminho do arquivo yalm;
- weights: indicador do caminho do weight;
- name: nome personalizado da pasta de resultado do treino;
- nosave: salvar apenas o último checkpoint;
- cache: cache de imagens para treinamento mais rápido.


## Detecção da performance do modelo:

- Utilização da ferramenta TensorBoard para gerar gráficos acumulativos das vezes que o algoritmo foi rodado, mensurando sua precisão e recall;
- Visualização de alguns dados de treinamento com labels;

## Inferencia na base de teste:
Interação para a inferência na base de testes, feita através de input, simulando o momento onde a foto será tirada e o reconhecimento será feito.

## Gerando resultados com a inferência:

Foi alterada parte do código base de detecção do Yolov5 para que o mesmo gere um arquivo de texto contendo todos os lixos eletrônicos detectados até então. Depois do registro dos elementos identificados, ocorre um tratamento dos dados para verificar a quantidade de cada material e a criação de um Dataframe com os dados captados.
Através da biblioteca Seaborn, foi plotado um gráfico com as informações presentes na base de dados criada. Além disso, foram utilizados os métodos de “.head” e “.describe”  da biblioteca Pandas para facilitar o entendimento.

O método "Head'' mostra os materiais detectados e a quantidade de cada.

O método “Describe” vai mostrar estatísticas da coluna de quantidade, que contém valores inteiros. Entre os atributos mostrados, estão: média, desvio padrão, menor e maior valor.

## Resultados

Foram rodados vários testes, variando os números de batchs e epochs, mas, dessa vez, considerando os resultados dos parâmetros usados anteriormente, que indicavam 600 epochs como ideal para o treino deste modelo, para confirmar, foi rodado um teste maior, com 800 épocas e outro menor, para deixar visível a discrepância no resultado. Abaixo, imagem do teste mencionado, em laranja com aproximadamente 300 de epoch e em azul, com 800.

![Graficos](/Images/TrainTensorFlow.png)

## Contribuidores

<table>
  <tr>
    <td align="center"><a href="https://github.com/DuduSouzaVeiga"><img style="border-radius: 50%;" src="https://avatars.githubusercontent.com/u/54594204?v=4" width="100px;" alt=""/><br /><sub><b>Eduardo Souza</b></sub></a><br /><p>💻</p></td>
    <td align="center"><a href="https://github.com/gtborges"><img style="border-radius: 50%;" src="https://avatars.githubusercontent.com/u/49994586?v=4" width="100px;" alt=""/><br /><sub><b>Guilherme Borges</b></sub></a><br /><p>🎧</p></td>
    <td align="center"><a href="https://github.com/JoMaAlves"><img style="border-radius: 50%;" src="https://avatars.githubusercontent.com/u/50152498?v=4" width="100px;" alt=""/><br /><sub><b>João Marcelo Alves</b></sub></a><br /><p>🦖</p></td>
    <td align="center"><a href="https://github.com/OlavoFerraz"><img style="border-radius: 50%;" src="https://avatars.githubusercontent.com/u/51130831?v=4" width="100px;" alt=""/><br /><sub><b>Olavo Ferraz</b></sub></a><br /><p href="https://github.com/OlavoFerraz">🇧🇷</p></td>
  </tr>
</table>
