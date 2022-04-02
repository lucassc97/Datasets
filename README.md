# Datasets

Detecção e identificação de ataques DDoS de aprendizado de máquina a partir da telemetria de computação em nuvem

Conjuntos de dados disponíveis:
- Treinamento = https://github.com/lucassc97/Datasets/blob/main/training.rar
- Teste = https://github.com/lucassc97/Datasets/blob/main/test.rar

- sob_ataque:

0 - Não ataque

1 - Ataque

- Código-ML = https://github.com/lucassc97/Datasets/blob/main/ml.py
- Code-selectKBest = https://github.com/lucassc97/Datasets/blob/main/selectKBest.py
- Kubernetes com Apache = https://github.com/lucassc97/Datasets/tree/main/apache_kube
- Netdata contêiner = https://github.com/lucassc97/Datasets/tree/main/netdata_container

# Implantação e Uso
1 - Instalar o Docker Desktop

2 - Nas configurações do Docker habilitar a integração com Kubernetes

3 - via terminal, instanciar o kubernetes (onde o apache ficará disponível na porta 8083)
- kubectl apply -f apache_kube/deployment.yaml
- kubectl apply -f apache_kube/service.yaml

4 - via terminal, instanciar o Netdata
docker-compose up -d

5 - Siege
5.1 - Instalação:
apt-get update
apt install siege

5.2 - Uso: via terminal, executar o Siege (ferramenta que simula cliente)

- sudo siege -t30m -c250 -d3s 127.0.0.1:8083

OBS1: "-c250" significa 250 clientes

OBS2: "-d3s" significa que será criada requisição num intervalor aleatório de 0 a 3 segundos.

6 - Hping3
6.1 - Instalação:
- apt-get update
- apt install hping3

6.2 - Uso: via terminal, executar o Hping3 (ferramenta que simula ataque)
- sudo hping3 -S --flood 127.0.0.1 -p 8083
- sudo hping3 -S -i u300 127.0.0.1 -p 8083
- sudo hping3 -S -i u250 127.0.0.1 -p 8083

OBS1: "-i u300" significa taxa de ataque de 300 microsegundos.

OBS2: "-i u250" significa taxa de ataque de 250 microsegundos.

OBS3: "--flood" taxa maxima de ataque.
