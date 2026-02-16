# A/B Testing — Avaliação Estatística de Campanha de Marketing

Antes de escalar uma campanha de marketing, é fundamental validar se o impacto observado é real ou apenas fruto do acaso.

Este projeto aplica **estatística inferencial** para avaliar um experimento A/B real, verificando se a exposição a um anúncio aumentou significativamente a taxa de conversão dos usuários.

Aqui, o foco não é modelagem preditiva.
O objetivo é demonstrar domínio de **teste de hipóteses, inferência estatística e interpretação orientada a negócio**.

---

## Dataset

Fonte: Kaggle
Nome: Marketing A/B Testing
Contexto: experimento controlado de campanha digital
Estrutura: ~588 mil registros

Principais variáveis:

* `test group` — grupo experimental (ad vs psa)
* `converted` — indicador de conversão (0 ou 1)
* `total ads` — quantidade de anúncios exibidos
* `most ads day` — dia com maior exposição

O dataset já representa um cenário real de teste A/B, ideal para aplicação de métodos estatísticos.

---

## Objetivo

Avaliar se existe diferença estatisticamente significativa na taxa de conversão entre:

* Grupo controle (PSA)
* Grupo exposto ao anúncio (AD)

A pergunta central do projeto é:

A campanha teve impacto real na conversão?

---

## Abordagem Analítica

O projeto foi estruturado em duas etapas complementares:

### 1. Análise Exploratória

* Verificação de estrutura e qualidade dos dados
* Distribuição dos grupos
* Cálculo das taxas de conversão
* Diferença absoluta e relativa entre grupos
* Verificação das condições para aplicação do teste Z

Essa etapa garante entendimento do experimento antes da inferência.

---

### 2. Inferência Estatística

Foram formuladas explicitamente as hipóteses:

H₀: Não há diferença na taxa de conversão entre os grupos.
H₁: Existe diferença na taxa de conversão entre os grupos.

Procedimentos aplicados:

* Teste Z para duas proporções
* Cálculo do p-valor
* Intervalo de confiança de 95%
* Decisão estatística com α = 0,05

---

## Principais Resultados

Taxa de conversão:

* Controle (PSA): ~1,78%
* Exposto ao anúncio (AD): ~2,55%

Diferença absoluta: ~0,77 ponto percentual
Aumento relativo: ~43%

O teste estatístico indicou p-valor inferior a 0,05, permitindo rejeitar a hipótese nula.

O intervalo de confiança não inclui zero, reforçando a evidência estatística.

---

## Interpretação

Os resultados indicam que a exposição ao anúncio aumentou a taxa de conversão de forma estatisticamente significativa.

Entretanto:

* A diferença absoluta é pequena.
* O grande tamanho amostral aumenta o poder do teste.
* Significância estatística não implica automaticamente relevância financeira.

A decisão estratégica deve considerar custo da campanha e retorno sobre investimento.

---

## Limitações

* Não foi analisado custo por aquisição.
* Não houve segmentação por perfil de usuário.
* A análise assume randomização adequada do experimento.
* Outras variáveis comportamentais não foram exploradas em profundidade.

---

## Conclusão

Este projeto demonstra aplicação prática de estatística inferencial em um cenário real de negócio.

Mais do que executar fórmulas, o trabalho evidencia:

* Capacidade de estruturar um problema
* Escolha adequada de teste estatístico
* Interpretação crítica de resultados
* Conexão entre evidência estatística e decisão estratégica

A inferência estatística é uma ferramenta essencial para evitar decisões baseadas apenas em variações aleatórias.
