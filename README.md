# Análise Estatística de Experimento A/B Campanha de Marketing Digital

> **Quantificando o impacto causal de um anúncio digital na taxa de conversão por meio de inferência estatística rigorosa.**

---

## Resumo Executivo

Uma empresa realizou um experimento controlado expondo usuários a um anúncio digital (`ad`) ou a um Anúncio de Serviço Público neutro (`psa`). Este projeto entrega uma análise estatística completa da validação da qualidade dos dados ao teste de hipótese formal, análise de poder e estimativa de impacto de negócio.

**Principal resultado:** O anúncio digital aumentou a conversão em **+0,77 ponto percentual** (+43% de lift relativo). O resultado é estatisticamente significativo ao nível de 1% (z = 7,37, p ≈ 1,7 × 10⁻¹³) e robusto a todas as verificações de qualidade.

---

## Problema de Negócio

Campanhas de marketing digital exigem decisões de investimento baseadas em evidências. Executar uma campanha sem validação estatística expõe o negócio a dois riscos:

- **Falsos positivos:** declarar uma campanha eficaz quando a diferença é ruído aleatório → orçamento desperdiçado
- **Falsos negativos:** descartar uma campanha eficaz por falta de evidência → receita perdida

Este projeto demonstra como o **teste A/B com metodologia estatística rigorosa** elimina o achismo das decisões de campanha uma competência central em organizações orientadas a dados.

---

## Desenho do Experimento

| Parâmetro | Valor |
|-----------|-------|
| **Dataset** | Marketing A/B Testing ([Kaggle](https://www.kaggle.com/datasets/faviovaz/marketing-ab-testing)) |
| **Total de usuários** | 588.101 |
| **Tratamento (ad)** | 564.577 usuários (96%) |
| **Controle (psa)** | 23.524 usuários (4%) |
| **Métrica de resultado** | Conversão binária (converteu: sim/não) |
| **Variáveis auxiliares** | Total de anúncios, dia da semana, horário do dia |

### Grupos

- **`ad`** Usuários que viram um anúncio digital com intenção comercial
- **`psa`** Usuários que viram um Anúncio de Serviço Público (controle, sem conteúdo comercial)

---

## Metodologia

### Fase 1 Validação da Qualidade dos Dados (`01_exploratory_analysis.ipynb`)

Antes de qualquer análise, realizamos validações formais:

| Verificação | Justificativa |
|-------------|--------------|
| Remoção da coluna de índice | `Unnamed: 0` é artefato de exportação CSV, não uma variável |
| Valores nulos | Ausências diferenciais entre grupos indicam censura informativa |
| Linhas duplicadas | Inflam o tamanho amostral → deflacionam erros padrão → falsos positivos |
| User IDs duplicados | Violam o pressuposto de independência do teste Z |
| Contaminação entre grupos | Usuários em ambos os grupos invalidam o isolamento experimental |

Todas as verificações aprovadas. Dataset limpo.

### Fase 2 Validação Formal da Randomização

Além de inspeção visual, aplicamos **testes qui-quadrado de homogeneidade** para verificar formalmente o balanceamento de covariáveis:

- **Distribuição por dia da semana:** teste χ² com 7 categorias
- **Distribuição por horário:** teste χ² com 24 categorias
- **Equivalência de exposição:** teste Mann-Whitney U (não paramétrico, adequado para `total ads` com distribuição assimétrica)

### Fase 3 Análise de Dose-Resposta

Segmentamos o grupo de tratamento por faixas de exposição para investigar se maior quantidade de anúncios correlaciona com maior conversão fornecendo insumo para otimização da frequência de mídia.

### Fase 4 Teste de Hipótese (`02_hypothesis_testing.ipynb`)

**Por que unilateral?** A pergunta de negócio é direcional: *"O anúncio aumenta a conversão?"* Um teste bilateral desperdiçaria poder estatístico testando se o anúncio também poderia *diminuir* a conversão o que levaria à mesma decisão de negócio ("não veicular"). O teste unilateral (direita) é o enquadramento estatisticamente correto.

| Componente | Valor |
|------------|-------|
| **H₀** | p_ad ≤ p_psa |
| **H₁** | p_ad > p_psa |
| **Teste** | Teste Z unilateral para duas proporções |
| **α** | 0,05 |
| **Valor crítico** | z = 1,645 |

### Fase 5 Tamanho do Efeito e Análise de Poder

- **Cohen's h** quantifica a magnitude do efeito independentemente do tamanho amostral
- **Análise de poder post-hoc** confirma que a amostra foi adequada
- **Cálculo de tamanho mínimo amostral** mostra o que um design balanceado exigiria

---

## Principais Resultados

### Resultados Estatísticos

| Métrica | Valor |
|---------|-------|
| Taxa de conversão (ad) | 2,55% |
| Taxa de conversão (psa) | 1,79% |
| **Lift absoluto** | **+0,77 p.p.** |
| **Lift relativo** | **+43%** |
| IC 95% para o lift | [+0,60 p.p., +0,94 p.p.] |
| Estatística Z | 7,37 |
| P-valor (unilateral) | ≈ 1,7 × 10⁻¹³ |
| Cohen's h | 0,053 (pequeno) |
| Poder estatístico | > 99% |

### Qualidade da Randomização

Ambos os testes qui-quadrado (dia da semana e horário) não encontraram diferença estatisticamente significativa na distribuição entre os grupos. O processo de randomização não introduziu confundimento temporal.

### Dose-Resposta

A exposição ao anúncio e a conversão apresentam relação **não linear**. Frequências muito altas (100+ anúncios) não produzem conversão proporcionalmente maior sugerindo possível fadiga publicitária em exposições extremas.

### Impacto de Negócio

| Alcance | Conversões Adicionais |
|---------|----------------------|
| 100 mil usuários | ~770 |
| 1 milhão de usuários | ~7.700 |
| 10 milhões de usuários | ~77.000 |

> A projeção de receita requer dados de custo por impressão não disponíveis neste dataset. Tomadores de decisão devem comparar o CPM da campanha com a receita por conversão para determinar o limiar de rentabilidade.

---

## Conclusão

O anúncio digital aumenta comprovada e significativamente a taxa de conversão. A evidência é robusta:

1. **Estatisticamente significativo:** p ≈ 10⁻¹³, muito abaixo de qualquer limiar α convencional
2. **Praticamente relevante:** +43% de lift relativo gera milhares de conversões em escala
3. **Causalmente suportado:** validação formal da randomização descarta confundimento temporal
4. **Bem dimensionado:** poder alcançado > 99% risco mínimo de Erro Tipo II

**Recomendação:** Veicular a campanha de anúncios. Priorizar exposição na faixa de 6 a 60 anúncios (pico da dose-resposta) e monitorar rendimentos decrescentes acima de 100 impressões por usuário.

---

## Estrutura do Projeto

```
marketing-ab-testing-statistical-inference/
├── data/
│   └── marketing_AB.csv                  # Dataset bruto (588K linhas)
├── notebooks/
│   ├── 01_exploratory_analysis.ipynb     # Qualidade dos dados + EDA + randomização
│   └── 02_hypothesis_testing.ipynb       # Teste Z + poder + impacto de negócio
├── outputs/
│   ├── group_distribution.png
│   ├── randomizacao_dia.png
│   ├── randomizacao_hora.png
│   ├── distribuicao_exposicao.png
│   ├── dose_resposta.png
│   ├── curva_poder.png
│   ├── impacto_negocio.png
│   └── conversion_rate_by_group.png
└── README.md
```

---

## Tecnologias

| Categoria | Ferramentas |
|-----------|-------------|
| **Linguagem** | Python 3.10+ |
| **Manipulação de dados** | pandas, numpy |
| **Testes estatísticos** | scipy.stats, statsmodels |
| **Visualização** | matplotlib, seaborn |
| **Ambiente** | Jupyter Notebook |

---

## Como Executar

```bash
# Clonar o repositório
git clone https://github.com/Leticia0587/marketing-ab-testing-statistical-inference.git
cd marketing-ab-testing-statistical-inference

# Instalar dependências
pip install pandas numpy scipy statsmodels matplotlib seaborn jupyter

# Abrir os notebooks
jupyter notebook notebooks/
```

Execute `01_exploratory_analysis.ipynb` primeiro, depois `02_hypothesis_testing.ipynb`.

---

## Fonte dos Dados

**Marketing A/B Testing** Favio Vázquez  
Disponível em: https://www.kaggle.com/datasets/faviovaz/marketing-ab-testing
