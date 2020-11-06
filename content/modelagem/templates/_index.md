---
title: Templates
weight: 1
bookToc: false
---

# Template de Projetos para Machine Learning

## Introdução

A fim de facilitar e padronizar a criação de projetos, criamos um [template de projetos](https://gitlab.com/servicos-semantix/datascience/templates/model-template) baseado no template [cookiecutter](https://drivendata.github.io/cookiecutter-data-science/). Este template estará sempre sendo melhorado pelos cientistas de dados da Semantix. Qualquer membro pode realizar uma sugestão de melhoria/atualização por meio de um merge-request.

O uso do template se dá pelo _cookiecutter_, que automatiza a criação de um diretório a partir de um template, e no nosso caso temos o nosso prórpio template. Ao executar o comando `cookiecutter https://gitlab.com/servicos-semantix/datascience/templates/model-template`, será criada uma pasta com toda a estrutura de diretórios, arquivos principais, assinaturas de funções e funções que servirão de base para um novo projeto de ciência de dados.

O template é apenas uma sugestão, cada projeto pode possuir suas particularidades e pode remover, agrupar ou adicionar novas funções, arquivos ou diretórios conforme ache necessário. O projeto foi criado para ser um tanto geral e apenas indicar a abordagem, não se sinta preso à estrutura vigente.

A característica mais marcante deste template é a estruturação em camadas. Podemos pensar que existem pelo menos 2 camadas que estão, até certo ponto, separadas.
    - A primeira é a camada de serviço, que é responsável por servir o modelo à algum fim. As formas de servir podem variar, podemos ter por exemplo uma API, que fica disponível para chamadas e responde com uma predição usando o modelo. Podemos também ter uma execução agendada para rodar um batch de predição. Esta camada utilizará mais esforços de engenharia de dados e desenvolvimento de software para ser desenvolvida.
    - A segunda camada é a de machine learning, que executará o treinamento ou definição do modelo. Esta parte do projeto envolve obter dados de treino, processá-los, treinar um modelo e avaliar as predições gerando as métricas aplicáveis. Aqui será onde o cientista de dados mais atuará.


## Estrutura

```
├── src
│   ├── app                     <- Módulo App: usado para servir o modelo em produção.
│   │   ├── api.py              <- Implementação via API.
│   │   ├── consumer.py         <- Implementação via consumidor de fila.
│   │   └── batch.py            <- Implementação de execução de batch.
│   ├── external_libs           <- Módulos genéricos utilizados em outros projetos.
│   └── ml                      <- Diretório com conteúdo de ciência de dados.
│       ├── code                <- Diretório para principais códigos para machine learning.
│       │   ├── data.py         <- Módulo usado para obtenção de dados brutos.
│       │   ├── features.py     <- Transformações dos dados brutos em features para treinamento.
│       │   ├── model.py        <- Implementação do modelo.
│       │   ├── train.py        <- Treinamento do modelo.
│       │   ├── predict.py      <- Geração de dados preditos pelo modelo
│       │   ├── evaluate.py     <- Avaliação dos dados preditos pela geração das métricas.
│       │   └── utils.py        <- Funções auxiliares.
│       ├── data
│       │   ├── external        <- Dados externos ao projeto.
│       │   ├── features        <- Representação intermediária das features para treinamento..
│       │   ├── logs            <- Logs gerados durante treinamento.
│       │   ├── metrics         <- Métricas coletadas para avaliação.
│       │   ├── predict         <- Dados preditos para avaliação.
│       │   ├── raw             <- Dados originais brutos.
│       │   └── snapshots       <- Retratos/backups de estados do projeto após treinamento.
│       ├── models              <- Diretório para modelos ou objetos treinados.
│       │   ├── evaluate        <- Modelos para avaliação.
│       │   └── full            <- Modelos para uso em produção.
│       ├── notebooks           <- Notebooks (jupyter) sobre o projeto.
│       ├── references          <- Dicionários de dados, manuais e outros materiais de apoio.
│       ├── reports             <- Análises e/ou apresentações em HTML, PDF, PPT etc.
│       │   └── figures         <- Figuras geradas para uso nos reports.
│       ├── environment.yml     <- Arquivo de configuração de ambiente Conda.
│       ├── gridsearch.sh       <- Script para iteração de parâmetros - gridsearch.
│       ├── README.md           <- LEIA-ME para a seção de machine learning.
│       ├── train.sh            <- Script para treinamento de modelo.
│       └── .public_env         <- Variáveis de ambiente para machine learning.
├── docs                        <- Diretório para documentação.
├── test                        <- Diretório para módulos de teste do projeto.
├── docker-compose.yml          <- Arquivo Docker-Compose para o serviço do app.
├── Dockerfile                  <- Arquivo Dockerfile para criar imagem para o app.
├── example.env                 <- Variáveis de ambiente para o app.
├── README.md                   <- LEIA-ME para o app e desenvolvedores no projeto.
└── requirements.txt            <- Requisitos para o projeto que serve o modelo.
```

{{< hint info >}}
A estrutura apresentada é apenas uma sugestão, cada projeto deve avaliar o que e como utilizar. Alguns scripts/módulso podem não fazer sentido numa aplicação em específico, e podem ser removidos/modificados conforme necessidade.
{{< /hint >}}
