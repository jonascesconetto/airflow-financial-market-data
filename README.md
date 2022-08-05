## Pipeline para buscar dados de mercado financeiro
  Este repositório contém alguns arquivos e códigos utilizados durante curso de `Data Pipelines com Apache Airflow `.
### Requisitos
- Realizar buscas periodicas na API da empresa [Polygon.io](https://polygon.io).
## 💻 Principais Tecnologias, Softwares e Bibliotecas
- Docker
- Python
- Apache AirFlow (Data Pipeline)
## ⚙ Instalação e configuração de ambiente
### Docker
  - Seguir a [documentação](https://docs.docker.com/engine/install/) oficial
### Container - Apache AirFlow
  - `Observação: `Abra o terminal em um diretório raiz para subir seu container com Airflow, dessa forma não perdemos os arquivos de DAGs gerados caso seja necessário algumas reinstalação ou configuração adicional do container.
  - Crie container com seguinte comando em seu terminal:
    ```bash
    docker run -d -p 8080:8080 -v "$PWD/airflow/dags:/opt/airflow/dags/" \
    --entrypoint=/bin/bash \
    --name airflow apache/airflow:2.1.1-python3.8 \
    -c '(\
    airflow db init && \
    airflow users create --username <nome de usuário> --password <sua senha> --firstname <Seu nome> --lastname <Seu Nome> --role Admin --email <Seu e-mail>); \
    airflow webserver & \
    airflow scheduler\
    '
    ```
  - Verificando o container em execução.
    ```bash
    docker container ls
    ```
  - Verificando os logs do container
    ```bash
    docker container logs airflow
    ```
  - Se nenhum erro aparecer, acesse a interface web do Apache Airflow pelo endereço:
    
    **https://localhost:8080**