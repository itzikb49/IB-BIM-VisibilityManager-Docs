---
layout: default
title: "IB-BIM Visibility Manager — Perguntas Frequentes"
---

# Perguntas Frequentes (FAQ)

## 📑 Índice

1. [Perguntas Gerais](#general-questions)
2. [Fluxo de Trabalho e Operações](#workflow--operations)
3. [Filtros](#filters)
4. [Substituições VG](#vg-overrides)
5. [Exportar/Importar](#exportimport)
6. [Desempenho](#performance)
7. [Solução de Problemas](#troubleshooting)
8. [Licença e Suporte](#licensing--support)
9. [Dicas e Melhores Práticas](#tips--best-practices)

---

## Perguntas Gerais {#general-questions}

### P: Quais versões do Revit são compatíveis?
**R:** O Visibility Manager é compatível com Revit 2023, 2024, 2025 e 2026. Cada versão possui uma compilação dedicada e otimizada.

### P: Funciona com templates?
**R:** Sim! A ferramenta detecta automaticamente se uma vista usa um template e lê as configurações de filtros do template. Ao copiar filtros, você pode aplicar diretamente às vistas ou aos seus templates.

### P: Posso usar entre projetos diferentes?
**R:** Com certeza! Exporte filtros de um projeto e importe em qualquer outro projeto. A ferramenta lida automaticamente com parâmetros e padrões ausentes.

---

## Fluxo de Trabalho e Operações {#workflow--operations}

### P: Como funciona a função COPY?
**R:** COPY duplica os filtros ou substituições VG selecionados da sua vista atual para as vistas/templates de destino.

**Pontos-chave:**
- **Vista atual = Origem (apenas referência)** — Mostra o que copiar, mas NÃO é modificada
- **Colunas 2-3 = Destinos** — Para onde os filtros/substituições são copiados
- Funciona de forma idêntica para Filtros e Substituições VG

**Passo a passo:**
1. Abrir uma vista que tenha os filtros/substituições que deseja copiar (origem)
2. **Painel esquerdo**: Selecionar quais filtros ou substituições copiar
3. **Coluna 2**: Selecionar vistas de destino
4. **Coluna 3**: Selecionar templates de destino (opcional)
5. Clicar em **COPY**
6. Escolher resolução de conflitos se os itens já existirem:
   - **Merge** — Manter existentes, adicionar apenas novos
   - **Overwrite** — Substituir existentes pela configuração importada
   - **New Only** — Pular existentes, adicionar apenas novos

**Nota:** A vista atual nunca é modificada — é sua referência!

---

### P: Como funciona a função REMOVE?
**R:** REMOVE exclui os filtros ou substituições VG selecionados das vistas/templates de destino.

**Pontos-chave:**
- **Vista atual = Apenas referência** — Mostra o que remover, mas NÃO é modificada
- **Colunas 2-3 = Destinos** — De onde os filtros/substituições são removidos

**Caso de uso:** Limpar múltiplas vistas removendo filtros obsoletos ou incorretos de uma vez.

---

### P: O que acontece quando as vistas de destino usam templates?
**R:** A ferramenta **detecta templates automaticamente** e exibe um aviso com:
- Nomes dos templates detectados
- Número de vistas que usam cada template
- Total de vistas que serão afetadas

**Por quê?** No Revit, quando uma vista usa um template, as configurações de filtros/VG são controladas pelo template. Este é o comportamento do Revit, não uma limitação da ferramenta.

---

### P: Devo selecionar Vistas (Coluna 2) ou Templates (Coluna 3)?
**R:** Ambos funcionam:

**Coluna 2 — Vistas de destino:**
- Selecionar vistas por nome
- Se a vista usa template → a ferramenta aplica ao template (avisa primeiro)
- Se a vista não tem template → aplica apenas àquela vista

**Coluna 3 — Templates de destino:**
- Selecionar templates diretamente
- Mais eficiente para padronização em massa
- Intenção mais clara — você sabe que está modificando um template

---

## Exportar/Importar {#exportimport}

### P: Como funciona a exportação — qual vista é a origem?
**R:** A exportação captura filtros/substituições VG da **vista ativa atual** (Painel ❶).
- Selecione os itens necessários
- Clique em EXPORT
- Escolha o local de salvamento
- A vista atual não muda

### P: Como funciona a importação — qual vista é afetada?
**R:** A importação é aplicada à **vista ativa atual**:
- Se a vista usa template → aplica ao template, afeta todas as vistas que o usam
- Se a vista não tem template → aplica apenas àquela vista

**Diferença importante em relação ao COPY:**
- **COPY**: Seleciona múltiplas vistas de destino. Vista atual sem alterações
- **IMPORT**: Apenas a vista atual é o destino. A vista atual é alterada

### P: Por que a ferramenta exporta um arquivo .PAT junto com o Excel?
**R:** Os padrões de preenchimento do Revit são armazenados separadamente dos filtros. O arquivo .PAT contém:
- Todos os padrões de preenchimento usados nos seus filtros
- Definições de padrões (linhas, ângulos, espaçamento)
Isso garante que ao importar filtros para outro projeto, todos os padrões estejam disponíveis.

### P: O que acontece se o arquivo .PAT estiver ausente durante a importação?
**R:** A ferramenta exibe um aviso mas continua:
- Os filtros são importados com sucesso
- Você verá "Pattern not found" até carregar os padrões manualmente
- Recomendado: Sempre mantenha os arquivos .PAT e .XLSX juntos

### P: Posso editar o arquivo Excel antes de importar?
**R:** Sim! Você pode:
- ✓ Modificar nomes de filtros
- ✓ Alterar cores, espessuras de linha
- ✓ Atualizar valores de regras
- ⚠️ Não altere a estrutura de colunas ou nomes de cabeçalhos

### P: Excel ou CSV — qual devo usar?
**R:**
- **Excel (.xlsx)** — Recomendado! Melhor formatação, mais fácil de ler
- **CSV** — Para sistemas legados ou controle de versão (compatível com Git)

### P: Posso importar filtros criados em versões anteriores do Revit?
**R:** Sim! A ferramenta lida com as diferenças de API automaticamente. Filtros exportados do Revit 2023 funcionam perfeitamente no Revit 2026 e vice-versa.

---

## Desempenho {#performance}

### P: Quantos filtros posso copiar de uma vez?
**R:** Testado com mais de 100 filtros para mais de 50 vistas simultaneamente. Sem limite prático!

### P: Deixa o Revit lento?
**R:** Não. As operações são otimizadas e usam a API do Revit de forma eficiente. Copiar 50 filtros leva ~5 segundos.

---

## Solução de Problemas {#troubleshooting}

### P: A importação diz "Success" mas os filtros não aparecem na minha vista
**R:** Verifique:
1. Os filtros estão habilitados? (View → Visibility/Graphics → aba Filters)
2. Sua vista usa um template que não inclui esses filtros?
3. As categorias do filtro correspondem aos elementos da sua vista?

### P: Os filtros são importados mas mostram "Value" em vez dos valores reais
**R:** Foi um bug na v1.0.0, corrigido na v1.0.1. Atualize para a versão mais recente.

### P: Avisos "Pattern not found" após importar
**R:** O arquivo .PAT não foi importado ou está em um local diferente. Reimporte e certifique-se de que o arquivo .PAT esteja na mesma pasta do arquivo .XLSX.

### P: Parâmetros personalizados não foram criados durante a importação
**R:** Certifique-se de ter clicado em "Yes" na caixa de diálogo de parâmetros personalizados. Se clicou em "No", os parâmetros não serão criados.

---

**Para informações completas sobre licença, preços e termos:**
👉 **[Ver Guia de Licença e Preços](LICENSING.md)**

---

## Dicas e Melhores Práticas {#tips--best-practices}

### P: Alguma dica para organizar filtros?
**R:** Sim!
- Use nomes consistentes: prefixo por disciplina (ARCH_, STRUCT_, MEP_)
- Exporte conjuntos de filtros para Excel como documentação
- Crie templates mestres com todos os filtros padrão do escritório
- Use nomes descritivos, não "Filter1", "Filter2"

### P: Como configurar filtros para reuniões de coordenação?
**R:**
1. Criar conjuntos de filtros para cada disciplina
2. Exportar todos os conjuntos para Excel
3. Compartilhar arquivos Excel com a equipe de coordenação
4. Cada disciplina importa os filtros relevantes
5. Todos têm configurações de vista idênticas!

### P: Posso usar isso para templates do Revit?
**R:** Com certeza! Fluxo de trabalho comum:
1. Construir filtros perfeitos em projeto de teste
2. Exportar para Excel
3. Importar no template da empresa
4. Distribuir template para todos os projetos

---

## Ainda tem perguntas?

**Contato:** itzikb.bim@gmail.com

**Documentação:** [link]

**Tutoriais em vídeo:** [link]
