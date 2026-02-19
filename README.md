# A/B Testing Statistical Analysis — Marketing Campaign

Antes de tomar decisões estratégicas sobre campanhas digitais, **validar estatisticamente os resultados é indispensável**.
Este projeto aplica **estatística inferencial e análise exploratória** para avaliar o impacto real de um anúncio digital sobre a taxa de conversão dos usuários.

O objetivo é demonstrar domínio dos **fundamentos de experimentação, teste de hipóteses e interpretação estatística orientada a negócio**.

---

## Dataset

* **Fonte:** Kaggle
* **Nome:** *Marketing A/B Testing*
* **Link:** https://www.kaggle.com/datasets/faviovaz/marketing-ab-testing
* **Contexto:** experimento controlado para avaliar impacto de anúncio digital
* **Tamanho:** ~588.000 registros

O dataset representa um experimento A/B real, contendo usuários divididos entre grupo controle e grupo exposto ao anúncio.

---

## Objetivo

Realizar uma **análise estatística completa de um experimento A/B**, buscando responder:

* Existe diferença na taxa de conversão entre os grupos?
* A diferença observada pode ser atribuída ao acaso?
* O efeito é estatisticamente significativo?
* A magnitude do impacto justifica decisão estratégica?

---

## O que foi analisado

As análises foram conduzidas principalmente sobre:

* Grupo experimental (`ad` vs `psa`)
* Indicador de conversão (`converted`)
* Taxa de conversão por grupo
* Diferença absoluta e relativa entre proporções
* Tamanho das amostras
* Intervalo de confiança da diferença

---

## Abordagem Analítica

O projeto foi estruturado em duas etapas complementares:

### 1. Análise Exploratória

* Inspeção da estrutura do dataset
* Verificação de consistência e integridade
* Distribuição dos grupos
* Cálculo das taxas de conversão
* Avaliação preliminar das diferenças observadas
* Verificação das condições para aplicação do teste Z

Essa etapa garante entendimento sólido do experimento antes da inferência.

---

### 2. Inferência Estatística

Foram formuladas formalmente as hipóteses:

H₀: A taxa de conversão é igual entre os grupos.
H₁: A taxa de conversão é diferente entre os grupos.

Procedimentos aplicados:

* Teste Z para duas proporções
* Cálculo da estatística Z
* Cálculo do p-valor
* Construção de intervalo de confiança de 95%
* Decisão estatística com nível de significância de 5%

---

## Principais Insights

* A taxa de conversão do grupo exposto ao anúncio foi superior à do grupo controle.
* A diferença absoluta foi de aproximadamente **0,77 ponto percentual**.
* O aumento relativo observado foi de cerca de **43%**.
* O teste estatístico indicou **evidência robusta contra a hipótese nula**.
* O intervalo de confiança não inclui zero, reforçando a significância estatística.

---

## Interpretação

Os resultados indicam que a exposição ao anúncio aumentou a taxa de conversão de forma estatisticamente significativa.

Entretanto:

* A magnitude absoluta do efeito é moderada.
* O grande tamanho amostral contribui para elevado poder estatístico.
* Significância estatística não implica automaticamente relevância financeira.

A decisão estratégica deve considerar custo da campanha, retorno esperado e métricas complementares de negócio.

---

## Conclusão

Este projeto reforça a importância da **inferência estatística na validação de experimentos A/B**.

O trabalho demonstra não apenas execução técnica do teste estatístico, mas também:

* Estruturação adequada de hipóteses
* Aplicação correta de métodos inferenciais
* Interpretação crítica dos resultados
* Conexão entre evidência estatística e decisão de negócio

A experimentação controlada é uma ferramenta essencial para evitar decisões baseadas em variações aleatórias.


