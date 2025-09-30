# Arquitetura do Sistema Alerta Fortaleza

**Data:** 29/09/2025

## Diagrama de Arquitetura

# Arquitetura do Sistema Alerta Fortaleza

Este documento detalha a arquitetura de integração da API "Alerta Fortaleza", que atua como um *middleware* para conectar sistemas heterogêneos para o monitoramento de alagamentos.

## Diagrama de Arquitetura Conceitual

O diagrama ilustra o fluxo de dados em tempo real, desde a ingestão via MQTT até a distribuição de alertas via REST/HTTP.

```mermaid
graph TD
    subgraph Entrada de Dados
        A[Sensores Pluviométricos/IoT]
    end

    subgraph API de Integração (Seu Projeto - Middleware)
        B{Receptor MQTT} --> C[Lógica de Processamento e Alerta]
        C --> D[Endpoints REST/HTTP]
    end

    subgraph Consumo de Alerta
        E[Sistema Defesa Civil]
        F[Aplicativo de Notificação ao Morador]
    end

    A -- Publica Dados em Tempo Real (MQTT) --> B
    D -- 1. Envio de Alerta (POST REST) --> E
    D -- 2. Envio de Notificação (POST REST) --> F
    E -- 3. Consulta de Status (GET REST) --> D

## Definição dos Protocolos

1. REST/HTTP: Para o consumo de dados pela Defesa Civil.
2. MQTT: Para a ingestão de dados dos sensores.
...
