# Previsão de Carga Elétrica no Sistema Interligado Nacional (SIN) com Redes LSTM

Para o artigo completo, acesse o arquivo `final_report.pdf`.

## Visão Geral
Este projeto implementa um modelo de redes neurais LSTM para prever a carga de energia elétrica no Sistema Interligado Nacional (SIN) do Brasil. A previsão de carga é essencial para otimizar o planejamento energético e garantir eficiência e segurança no sistema elétrico do país.

## Dados
Os dados foram obtidos a partir da plataforma aberta do Operador Nacional do Sistema Elétrico (ONS), compreendendo registros diários de carga desde 01/01/2016 até 30/04/2024. Cada registro representa a carga média diária (MWmed) no SIN, considerando todos os quatro subsistemas: Norte, Nordeste, Sudeste/Centro-Oeste e Sul.

## Modelo LSTM
A arquitetura LSTM foi escolhida para capturar a natureza sequencial dos dados de séries temporais. A rede foi configurada da seguinte forma:
- **Camadas**: LSTM (50 units), Dense (25 units) e Dense (1 unit de saída)
- **Configurações testadas**: seis modelos variando `time steps` (30, 60, 90 dias) e `batch size` (32 e 64)
- **Desempenho**: O melhor modelo (Model4) obteve MAE de 1441 MWmed e MAPE de 1.95%, utilizando `time steps = 60` e `batch size = 32`

## Resultados
Os seis modelos treinados foram comparados usando as métricas MAE e MAPE. O Model4 apresentou o melhor desempenho, com uma precisão satisfatória para o contexto de previsão de carga elétrica no SIN.

| Modelo   | Time Steps | Batch Size | MAE (MWmed) | MAPE (%) |
|----------|------------|------------|-------------|----------|
| Model1   | 90         | 64         | 1779.60     | 2.33     |
| Model2   | 90         | 32         | 1478.09     | 1.99     |
| Model3   | 60         | 64         | 1570.52     | 2.10     |
| Model4   | 60         | 32         | 1441.23     | 1.95     |
| Model5   | 30         | 64         | 1653.74     | 2.21     |
| Model6   | 30         | 32         | 1797.96     | 2.40     |

## Conclusão e Trabalhos Futuros
Este projeto demonstra o potencial das redes LSTM para previsão de carga elétrica em sistemas complexos como o SIN. Futuras melhorias incluem:
- Aumento de camadas LSTM e número de units por camada
- Experimentação com GRUs e modelos estatísticos tradicionais
- Inclusão de novas variáveis, como temperatura e indicadores macroeconômicos, para aumentar a precisão preditiva

## Referências
1. ONS - Operador Nacional do Sistema Elétrico.
2. ANEEL - Agência Nacional de Energia Elétrica.
3. TensorFlow - Biblioteca usada para a implementação dos modelos LSTM.
