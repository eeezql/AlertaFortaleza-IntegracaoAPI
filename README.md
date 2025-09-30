# 🌊 Alerta Fortaleza: Sistema de Integração para Monitoramento de Alagamentos

## [cite_start]1. Objetivo do Trabalho [cite: 77]

Este projeto visa desenvolver uma API de integração de sistemas heterogêneos para mitigar os riscos de alagamentos nos bairros costeiros de Fortaleza. Através da centralização de dados de sensores pluviométricos, a API automatiza a emissão de alertas em tempo real para a Defesa Civil e para a população, gerando um **impacto social positivo** ao aumentar a segurança e a capacidade de resposta da comunidade.

## 2. Descrição Funcional da Solução 

A API atua como um *middleware* que recebe dados em tempo real (via MQTT) dos sensores de chuva instalados nas áreas de risco. Ao identificar que o volume de precipitação atingiu um limiar crítico, a API dispara uma requisição REST/HTTP para o sistema da Defesa Civil e para um sistema de notificação, garantindo que as autoridades e os moradores sejam alertados imediatamente.

### Requisitos Técnicos Atendidos:

* **Integração de Múltiplos Sistemas:** Integra o Sistema de Sensores (MQTT) e o Sistema de Defesa Civil (REST).
* **Endpoints Funcionais:** Possui pelo menos dois endpoints REST (ex: `POST /data` e `GET /status/{bairro}`).
* **Múltiplos Protocolos:** Utiliza **MQTT** (para ingestão de dados de sensores) e **REST/HTTP** (para consultas e alertas).
* **Tratamento de Erros:** Inclui lógica para tratar dados inválidos ou falhas na comunicação com os sistemas externos.
* **Testes Unitários:** Possui testes unitários para a lógica de alerta e para os endpoints principais

## 3. Arquitetura da API e Diagrama 

A arquitetura se baseia em um **Design Orientado a Eventos** (para dados MQTT) e **Microsserviços** (para a API REST).

**Infelizmente não consegui concluir o diagrama.**

### Protocolos de Comunicação:

1.  **MQTT (Message Queuing Telemetry Transport):** Usado para a comunicação entre os sensores (publishers) e a API (subscriber). Ideal para dados de IoT em tempo real.
2.  **REST/HTTP:** Usado para a comunicação entre a API e os sistemas de destino (Defesa Civil e Notificações).

## 4. Instruções Detalhadas para Execução (Postman/Insomnia) 

Para testar a API localmente, siga os passos abaixo:

1.  **Infelizmente não consegui concluir a estruturação de pastas obrigatorias nem o "architecture.md":**
   

## 5. Documentação das Rotas da API [cite: 80]

| Método | Rota | Descrição | Parâmetros de Entrada (Body) | Resposta de Sucesso (200) |
| :--- | :--- | :--- | :--- | :--- |
| **POST** | `/api/v1/sensors/data` | Recebe dados do sensor de chuva (ingestão). **É aqui que a lógica de alerta é acionada.** | `{ "sensor_id": "PIRAMBU-01", "level_mm": 120, "timestamp": "..." }` | `{ "message": "Data processed. Alert status: OK/CRITICAL" }` |
| **GET** | `/api/v1/status/{bairro}` | Consulta o status de alagamento de uma área específica. (Usado pela Defesa Civil). | *(Path Param: bairro)* | `{ "area": "Mucuripe", "status": "ALERTA MODERADO", "last_update": "..." }` |
| **GET** | `/api/v1/status/critical` | Retorna uma lista de todas as áreas com status CRÍTICO. | *(Nenhum)* | `[ { "area": "Praia do Futuro", "status": "CRÍTICO" }, ... ]` |

## 6. Papéis e Responsabilidades da Equipe 

| Membro (Nome Completo) | Matrícula | Papel no Projeto | Tarefas Principais |
| :--- | :--- | :--- | :--- |
| [Ezequiel da Silva Cardoso] | [2316161] | **Arquiteto e idealista do projeto** | Elaboração do README, Design da Arquitetura, Definição dos Protocolos (MQTT), Integração com Protocolo MQTT  |

---

