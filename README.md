# Dashboard para Acompanhamento de Frequecia
Este repositório traz o arquivo **Acompanhamento Diário.pbix**, um relatório do Power BI focado em **acompanhamento diário da frequência de alunos**. O objetivo é oferecer uma visão rápida de presença por **curso**, **dia da semana** e **horário**, além de métricas agregadas para apoiar decisões.

> **Como abrir**: baixe o arquivo `Acompanhamento Diário.pbix` e abra no **Power BI Desktop** (Windows). Use a planilha **acompanhameto_diário_alunos.xlsx** para modificar os dados e use o botão **Atualizar** para carregar os dados mais recentes.

---

## Estrutura do relatório (Abas)

### 1) Geral
Visão executiva com KPIs, distribuição e segmentação para explorar o comportamento de presença.

**Principais visuais desta aba:**
- Card: Cartão com agregação mínima do campo **Alunos.Aluno** (representa o menor valor alfabético).
- Card: Cartão com agregação mínima do campo **Alunos.Curso em aberto** (menor valor alfabético).
- Pie chart: Distribuição de **Alunos.Frequência** com eixo de categorias e contagem de valores não nulos.
- Card: Cartão com a medida **Alunos.Média de TotalPresencas por Horário**.
- Treemap: Hierarquia por **Alunos.Curso em aberto** com **Count(Alunos.Aluno)**.
- Slicer: Segmentador por **DimDiaSemana.Dia da Semana**.
- Line chart: Série temporal/categórica: **DimDiaSemana.Dia da Semana** (eixo) × **Alunos.Média de TotalPresencas por Horário** (valores).
- Advanced slicer: Segmentador avançado por **OrdemHorario.Horário**.

**Como usar:**
- Use o **segmentador por Dia da Semana** para filtrar toda a página.
- Utilize o **segmentador avançado por Horário** para focar nos períodos de interesse.
- Observe a **pizza de Frequência** para entender a distribuição de registros/flags de presença.
- O **treemap por Curso em aberto** ajuda a comparar cursos pelo número de alunos.

> **Observação**: os cartões configurados com **agregação mínima** (Min) para campos textuais exibem o **menor valor alfabético**. Se o objetivo for apresentar **contagens** (ex.: total de alunos ou de cursos), considere trocar a agregação desses cartões para **Contagem** ou **Contagem Distinta**, ou utilizar medidas DAX dedicadas.

---

### 2) Frequência
Foco na evolução/variação de presença (**TotalPresencas**) por diferentes dimensões.

**Principais visuais desta aba:**
- Line chart: Eixo **DimDiaSemana.Dia da Semana** × valores **Alunos.TotalPresencas**.
- Line chart: Eixo **Alunos.Curso em aberto** × valores **Alunos.TotalPresencas**.
- Line chart: Eixo **OrdemHorario.Horário** × valores **Alunos.TotalPresencas**.

**Como usar:**
- Compare **dias da semana** para identificar o padrão de presença ao longo da semana.
- Compare **cursos** para identificar quais concentram mais/menos presenças.
- Compare por **horário** para encontrar janelas com maior engajamento.

---

## Campos e medidas utilizadas (referenciadas nos visuais)
- **Alunos.Aluno**
- **Alunos.Curso em aberto**
- **Alunos.Frequência**
- **Alunos.TotalPresencas**
- **Alunos.Média de TotalPresencas por Horário**
- **DimDiaSemana.Dia da Semana**
- **OrdemHorario.Horário**
- **Count(Alunos.Aluno)**
- **CountNonNull(Alunos.Frequência)**
- **Min(Alunos.Aluno)** / **Min(Alunos.Curso em aberto)**

---

## Atualização dos dados
- Clique em **Atualizar** no Power BI Desktop para recarregar as tabelas conforme a planilha **acompanhameto_diário_alunos.xlsx**.
- Caso haja **parâmetros** (credenciais, caminhos, etc.), o Power BI solicitará os ajustes na primeira execução.
- Para publicar no **Power BI Service**, use **Publicar** no Desktop e configure o **agendamento de atualização** (se aplicável).

---
