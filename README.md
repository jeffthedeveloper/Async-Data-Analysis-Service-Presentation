# Apresentação: Serviço de Análise de Dados Assíncrono

Este repositório contém o código-fonte de uma *landing page* (site de apresentação) estática e responsiva para um projeto de microsserviços chamado **Async Data Analysis Service**.

O site é uma página única (Single-Page Application) desenvolvida com **HTML, Tailwind CSS e JavaScript (para internacionalização)**. O objetivo desta página é apresentar a arquitetura, as funcionalidades e as tecnologias de um sistema de backend complexo projetado para processamento de dados em segundo plano.

## Funcionalidades do Site de Apresentação

  * **Design Moderno (Dark Mode):** Construído com Tailwind CSS, apresentando um tema escuro, cartões com efeito de "vidro" (`.glass-effect`) e textos em gradiente (`.gradient-text`).
  * **Navegação (Single-Page):** Utiliza navegação interna com rolagem suave (`.scroll-smooth`) para seções como Visão Geral, Arquitetura e Tecnologias.
  * **Internacionalização (i18n):** Inclui um botão de alternância (PT/EN) que, via JavaScript, traduz dinamicamente todo o conteúdo do site sem recarregar a página.

## Arquitetura do Serviço (Descrita na Página)

A página `index.html` descreve um serviço de backend com a seguinte arquitetura e funcionalidades:

### 1\. O Problema Solucionado

A lentidão e os *timeouts* em APIs que executam análises de dados pesadas diretamente em requisições HTTP.

### 2\. A Solução Proposta

Desacoplar a recepção da requisição do seu processamento. A API responde instantaneamente com um `job_id`, enquanto a análise é enfileirada e executada em segundo plano por *workers* dedicados.

### 3\. Componentes da Arquitetura

1.  **API (Gateway):** Recebe requisições, autentica (JWT/OAuth2) e publica jobs.
2.  **RabbitMQ:** Message Broker que gerencia as filas de tarefas e Dead Letter Queues (DLQ) para tratar falhas.
3.  **Worker:** Consome mensagens da fila e executa a análise.
4.  **MongoDB:** Armazena os dados brutos e os resultados processados.

### 4\. Tecnologias do Backend (Descritas)

  * **Python & FastAPI:** Para a API de alta performance.
  * **RabbitMQ:** Para o enfileiramento de mensagens.
  * **MongoDB:** Como banco de dados NoSQL.
  * **Docker & Docker Compose:** Para containerização e orquestração.
  * **Pytest:** Para testes automatizados.
  * **GitHub Actions:** Para CI/CD.

## Estrutura do Repositório

```
/
│
└── index.html      # A página de apresentação completa (HTML, Tailwind e JS)
└── README.md       # Este arquivo
```

## Como Usar

Este é um projeto estático. Não é necessário um servidor ou processo de *build*.

1.  **Clone ou baixe o repositório.**
2.  **Abra o arquivo `index.html`** diretamente em qualquer navegador web moderno para visualizar a apresentação.
