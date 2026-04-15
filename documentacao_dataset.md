# Documentação do Dataset — Student Alcohol Consumption (Matemática)

**Fonte:** UCI Machine Learning Repository / Kaggle  
**Arquivo:** `student-mat.csv`  
**Registros:** 395 alunos | **Atributos originais:** 33 colunas  

---

## 1. Visão Geral

O dataset foi coletado em duas escolas secundárias de Portugal durante o ano letivo de 2005–2006, abrangendo alunos da disciplina de **Matemática**. Os dados combinam informações escolares (notas, faltas, reprovações) com contexto socioeconômico, familiar e comportamental (consumo de álcool, uso de internet, relacionamento familiar). O objetivo original da pesquisa era compreender os fatores que influenciam o **desempenho acadêmico** e o **consumo de álcool** entre adolescentes.

---

## 2. Dicionário de Dados (Colunas em Português)

| Coluna (PT)                     | Coluna (EN original) | Tipo        | Descrição                                                                                     |
|---------------------------------|----------------------|-------------|-----------------------------------------------------------------------------------------------|
| `escola`                        | school               | Categórico  | Escola do aluno: GP = Gabriel Pereira, MS = Mousinho da Silveira                             |
| `sexo`                          | sex                  | Binário     | Sexo: F = Feminino, M = Masculino                                                             |
| `idade`                         | age                  | Numérico    | Idade do aluno (15–22 anos)                                                                   |
| `endereco`                      | address              | Binário     | Tipo de endereço: U = urbano, R = rural                                                       |
| `tamanho_familia`               | famsize              | Binário     | Tamanho da família: GT3 = mais de 3 membros, LE3 = até 3 membros                            |
| `status_pais`                   | Pstatus              | Binário     | Situação dos pais: T = juntos, A = separados                                                  |
| `educacao_mae`                  | Medu                 | Ordinal     | Escolaridade da mãe: 0 = nenhuma, 1 = Fund. I, 2 = Fund. II, 3 = Médio, 4 = Superior       |
| `educacao_pai`                  | Fedu                 | Ordinal     | Escolaridade do pai: mesma escala                                                             |
| `profissao_mae`                 | Mjob                 | Categórico  | Profissão da mãe: teacher, health, services, at_home, other                                  |
| `profissao_pai`                 | Fjob                 | Categórico  | Profissão do pai: mesma lista                                                                 |
| `motivo_escola`                 | reason               | Categórico  | Motivo da escolha da escola: home, reputation, course, other                                  |
| `responsavel`                   | guardian             | Categórico  | Responsável legal: mother, father, other                                                      |
| `tempo_deslocamento`            | traveltime           | Ordinal     | Tempo de deslocamento casa→escola: 1 = <15min … 4 = >1h                                     |
| `tempo_estudo`                  | studytime            | Ordinal     | Tempo de estudo semanal: 1 = <2h, 2 = 2–5h, 3 = 5–10h, 4 = >10h                           |
| `reprovacoes_anteriores`        | failures             | Numérico    | Nº de reprovações anteriores (0–4)                                                            |
| `apoio_escola`                  | schoolsup            | Binário     | Suporte educacional extra oferecido pela escola (yes/no)                                      |
| `apoio_familia`                 | famsup               | Binário     | Suporte educacional pela família (yes/no)                                                     |
| `aulas_pagas`                   | paid                 | Binário     | Aulas particulares pagas (yes/no)                                                             |
| `atividades_extracurriculares`  | activities           | Binário     | Participa de atividades extracurriculares (yes/no)                                            |
| `frequentou_creche`             | nursery              | Binário     | Frequentou creche/pré-escola (yes/no)                                                         |
| `deseja_ensino_superior`        | higher               | Binário     | Pretende cursar ensino superior (yes/no)                                                      |
| `acesso_internet`               | internet             | Binário     | Possui internet em casa (yes/no)                                                              |
| `relacionamento_romantico`      | romantic             | Binário     | Está em um relacionamento amoroso (yes/no)                                                    |
| `qualidade_rel_familiar`        | famrel               | Ordinal     | Qualidade do relacionamento familiar: 1 = muito ruim … 5 = excelente                        |
| `tempo_livre`                   | freetime             | Ordinal     | Tempo livre após a escola: 1 = muito pouco … 5 = muito                                       |
| `sair_com_amigos`               | goout                | Ordinal     | Frequência de saídas com amigos: 1 = muito pouco … 5 = muito                                 |
| `consumo_alcool_semana`         | Dalc                 | Ordinal     | Consumo de álcool nos dias úteis: 1 = muito baixo … 5 = muito alto                          |
| `consumo_alcool_fds`            | Walc                 | Ordinal     | Consumo de álcool nos fins de semana: 1 = muito baixo … 5 = muito alto                      |
| `saude`                         | health               | Ordinal     | Estado de saúde atual: 1 = muito ruim … 5 = muito bom                                       |
| `faltas`                        | absences             | Numérico    | Número de faltas escolares (0–93)                                                             |
| `nota_periodo_1`                | G1                   | Numérico    | Nota do 1º período (0–20)                                                                     |
| `nota_periodo_2`                | G2                   | Numérico    | Nota do 2º período (0–20)                                                                     |
| `nota_final`                    | G3                   | Numérico    | **Nota final** (0–20) — variável-alvo principal                                              |

### Colunas derivadas (criadas no pré-processamento)

| Coluna (PT)             | Derivação                                              | Finalidade                          |
|-------------------------|--------------------------------------------------------|-------------------------------------|
| `aprovado`              | `nota_final >= 10 → 1`                                 | Alvo para classificação             |
| `alcool_total`          | `(Dalc × 5 + Walc × 2) / 7`                           | Consumo médio ponderado             |
| `educacao_pais_media`   | `(educacao_mae + educacao_pai) / 2`                    | Proxy de capital educacional        |
| `progresso_notas`       | `nota_final − nota_periodo_1`                          | Evolução ao longo do ano            |

---

## 3. Qualidade dos Dados

| Aspecto                    | Resultado                                                 |
|----------------------------|-----------------------------------------------------------|
| Valores nulos              | **Nenhum** — dataset completo                            |
| Duplicatas                 | **Nenhuma**                                              |
| Notas fora do intervalo    | **Nenhuma** (todas dentro de 0–20)                       |
| Idades fora do intervalo   | **Nenhuma** (15–22 anos)                                 |
| Alunos com G3 = 0          | ~39 alunos (~10%) — prováveis desistências/ausências no exame final |

> **Observação:** Os alunos com `nota_final = 0` mas `nota_periodo_1 > 0` e `nota_periodo_2 > 0` provavelmente abandonaram a disciplina ou não compareceram ao exame. Dependendo do objetivo do modelo, pode ser interessante **excluí-los** ou tratá-los como uma categoria separada.

---

## 4. Distribuição da Variável-Alvo

- **Taxa de aprovação:** ~67% (G3 ≥ 10)  
- **Taxa de reprovação:** ~33%  
- **Nota média:** ~10.4 ± 4.6  
- **Distribuição:** bimodal — pico em torno de 10–12 e concentração no 0 (desistências)

> O dataset apresenta **leve desbalanceamento** entre aprovados e reprovados, porém não a ponto de exigir técnicas de oversampling como SMOTE de imediato. Monitorar durante a modelagem.

---

## 5. Principais Insights Exploratórios

### 5.1 Preditor mais forte: notas dos períodos anteriores
- `nota_periodo_1` e `nota_periodo_2` têm correlação muito alta com `nota_final` (r ≈ 0.80–0.90).
- Incluí-las é justificável em cenários preditivos onde os períodos já ocorreram.
- Para um modelo **prognóstico** (predição antes do ano letivo), devem ser **excluídas**, priorizando atributos demográficos e comportamentais.

### 5.2 Reprovações anteriores impactam fortemente
- Alunos com 3+ reprovações anteriores têm nota média abaixo de 7 e taxa de reprovação superior a 80%.
- É um dos preditores mais relevantes junto com as notas de período.

### 5.3 Tempo de estudo: relação positiva clara
- Alunos que estudam >10h/semana têm mediana ~13; os que estudam <2h têm mediana ~9.
- Importante, mas com forte interação com `reprovacoes_anteriores`.

### 5.4 Álcool: impacto mais evidente no fim de semana
- Consumo de álcool no fim de semana (`consumo_alcool_fds`) apresenta correlação negativa mais forte com a nota do que o consumo semanal (`consumo_alcool_semana`).
- Alunos com `consumo_alcool_fds` = 5 têm notas ~2 pontos menores em média.

### 5.5 Faltas: correlação moderadamente negativa
- Correlação com nota_final: r ≈ −0.25 a −0.30.
- Outliers com muitas faltas (>30) quase sempre reprovam.

### 5.6 Escolaridade dos pais: correlação positiva
- Quanto maior a escolaridade da mãe e do pai, maior a tendência de o aluno obter notas mais altas.
- Efeito mais pronunciado na mãe.

### 5.7 Desejo de ensino superior: forte sinal
- Alunos que desejam cursar ensino superior têm nota média ~3 pontos acima dos que não desejam.
- Provável proxy de motivação e engajamento.

### 5.8 Internet em casa: leve vantagem
- Alunos com internet em casa têm notas ligeiramente mais altas — correlação fraca mas consistente.

---

## 6. Atributos Relevantes para as Próximas Etapas

### 6.1 Definição do Problema de Modelagem

Recomenda-se trabalhar com **duas abordagens complementares**:

| Abordagem     | Variável-alvo      | Quando usar                                             |
|---------------|--------------------|---------------------------------------------------------|
| **Regressão** | `nota_final` (0–20)| Quando se deseja prever a nota exata                   |
| **Classificação** | `aprovado` (0/1) | Quando o foco é identificar alunos em risco de reprovação |

### 6.2 Features Recomendadas para o Modelo MLP

#### Cenário A — Predição em tempo real (notas de período disponíveis)
> Alta acurácia esperada. Útil para intervenção no final do ano.

| Feature                   | Justificativa                                 |
|---------------------------|-----------------------------------------------|
| `nota_periodo_1`          | Correlação r ≈ 0.80 com G3                    |
| `nota_periodo_2`          | Correlação r ≈ 0.90 com G3                    |
| `reprovacoes_anteriores`  | Forte impacto negativo nas notas              |
| `faltas`                  | Indicador de engajamento                      |
| `tempo_estudo`            | Hábito de estudo                              |
| `alcool_total`            | Comportamento de risco                        |
| `deseja_ensino_superior`  | Proxy de motivação                            |
| `educacao_pais_media`     | Capital educacional familiar                  |
| `acesso_internet`         | Recurso de estudo                             |
| `apoio_escola`            | Suporte institucional                         |

#### Cenário B — Predição precoce (sem notas de período)
> Menor acurácia, porém mais útil para intervenção preventiva no início do ano.

| Feature                   | Justificativa                                 |
|---------------------------|-----------------------------------------------|
| `reprovacoes_anteriores`  | Histórico escolar                             |
| `tempo_estudo`            | Hábito declarado                              |
| `educacao_mae`            | Contexto socioeconômico                       |
| `educacao_pai`            | Contexto socioeconômico                       |
| `deseja_ensino_superior`  | Motivação acadêmica                           |
| `faltas`                  | (se disponível no início do ano)              |
| `consumo_alcool_fds`      | Comportamento de risco                        |
| `acesso_internet`         | Recurso cognitivo                             |
| `sair_com_amigos`         | Indicador de distração                        |
| `qualidade_rel_familiar`  | Suporte emocional                             |

---

## 7. Sugestões para a Modelagem (Etapa 3)

### 7.1 Arquitetura MLP Sugerida

```
Entrada → [Dense(64, relu)] → [Dropout(0.3)] → [Dense(32, relu)] → [Dropout(0.2)] → Saída
```

| Parâmetro          | Classificação                   | Regressão                      |
|--------------------|----------------------------------|--------------------------------|
| Camada de saída    | Dense(1, sigmoid)               | Dense(1, linear)               |
| Loss               | binary_crossentropy              | mean_squared_error             |
| Otimizador         | Adam (lr=0.001)                 | Adam (lr=0.001)                |
| Métricas           | accuracy, AUC                   | MAE, RMSE                      |
| Épocas sugeridas   | 50–100                          | 50–100                         |
| Batch size         | 32                              | 32                             |

### 7.2 Pré-processamento para a rede
- **Normalização:** aplicar `StandardScaler` ou `MinMaxScaler` nas features numéricas contínuas (`faltas`, `alcool_total`, `educacao_pais_media`).
- **Variáveis ordinais** (tempo_estudo, consumo_alcool_*, saude etc.): já são numéricas — normalizar junto.
- **Variáveis binárias** (0/1): não precisam de normalização.
- **Split sugerido:** 70% treino / 15% validação / 15% teste (ou cross-validation com k=5 dado o tamanho pequeno do dataset).

### 7.3 Atenção ao Overfitting
O dataset tem apenas 395 amostras — redes neurais tendem a overfittar com facilidade. Usar:
- `Dropout` entre camadas densas
- `EarlyStopping` com `patience=10`
- `L2 regularization` se dropout não for suficiente
- Cross-validation para avaliação mais robusta

---

## 8. Métricas Recomendadas (Etapa 4)

### Classificação (aprovado/reprovado)

| Métrica    | Por que usar                                                                |
|------------|-----------------------------------------------------------------------------|
| Accuracy   | Visão geral — útil dado o leve desbalanceamento (~67/33)                   |
| Precision  | Evitar falsos positivos (classificar reprovado como aprovado)              |
| Recall     | Evitar falsos negativos (perder alunos em risco)                           |
| F1-Score   | Equilíbrio entre precision e recall                                         |
| AUC-ROC    | Robustez a limiares de decisão                                              |
| Matriz de confusão | Visualização clara dos erros de classificação                     |

### Regressão (nota final)

| Métrica | Por que usar                                       |
|---------|----------------------------------------------------|
| MAE     | Erro médio em pontos de nota — interpretável       |
| RMSE    | Penaliza mais erros grandes                        |
| R²      | Percentual da variância explicada pelo modelo      |

---

## 9. Arquivos Gerados

| Arquivo                        | Descrição                                                   |
|--------------------------------|-------------------------------------------------------------|
| `student-mat.csv`              | Dataset original                                            |
| `student_limpo.csv`            | Dataset após limpeza, transformação e feature engineering   |
| `analise_exploratoria.py`      | Script Python completo de EDA                               |
| `graficos/01_*.png` … `13_*.png` | Gráficos gerados pela análise exploratória               |
| `documentacao_dataset.md`      | Este documento                                              |

---

*Documentação elaborada para o PBL 4 — Inteligência Artificial.*
