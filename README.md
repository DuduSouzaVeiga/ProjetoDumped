# Projeto Dumped

Visando o desenvolvimento de uma lixeira inteligente e com alta interatividade, a equipe técnica buscou tecnologias capazes de executar o projeto. O [YOLOv5](https://github.com/ultralytics/yolov5) é a última release da família YOLO, que foi inicialmente introduzido ao mercado como o primeiro modelo de detecção de objetos que combinava previsão de bounding box e classificação de objetos em um único lugar. Com sua nova implementação no framework PyTorch, ficou muito mais leve e de fácil uso, por conta dessas características se tornou a base para o desenvolvimento do modelo de detecção de lixo eletrônico do projeto.

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
- Interação para a inferência na base de testes, feita através de input, simulando o momento onde a foto será tirada e o reconhecimento será feito.

![Graficos](https://drive.google.com/file/d/1CmgVHB1xYVAJ0-L4fsISb57HoGyfPIT9/view?usp=sharing)