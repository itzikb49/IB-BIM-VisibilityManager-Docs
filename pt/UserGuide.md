---
layout: default
title: "IB-BIM Visibility Manager — Guia do Usuário"

---

<div align="right" style="margin: 4px 0 6px 0;">
  <img src="../Images/IB-BIM_200X200.png" alt="IB-BIM" width="150" style="display:block;">
</div>


## Sobre o Complemento

Texto introdutório breve explicando o que o Visibility Manager faz,
para quem é e quais problemas resolve.

📺 **[Assistir Tutorial em Vídeo no YouTube](https://youtu.be/68-bxWQfsUg)** ← Veja a ferramenta em ação!

👉 **[Ir para o Guia Passo a Passo Completo](#complete-step-by-step-guide)**

---

## Guia Passo a Passo Completo {#complete-step-by-step-guide}


**Versão 1.0.0 | Última Atualização: Novembro 2025**

## 📑 Índice
- [Introdução](#getting-started)
- [Instalação](#installation)
- [Iniciar a Ferramenta](#launching-the-tool)
- [Visão Geral da Interface](#interface-overview)
- [Trabalhar com Filtros](#working-with-filters)
  - [Copiar Filtros](#copying-filters-between-views)
  - [Remover Filtros](#removing-filters-from-views)
  - [Exportar Filtros](#exporting-filters)
  - [Importar Filtros](#importing-filters)
- [Trabalhar com Substituições VG](#working-with-vg-overrides)
  - [Categorias Suportadas](#supported-categories)
  - [Copiar Substituições VG](#copying-vg-overrides)
  - [Remover Substituições VG](#removing-vg-overrides)
  - [Exportar Substituições VG](#exporting-vg-overrides)
  - [Importar Substituições VG](#importing-vg-overrides)
- [Recursos Avançados](#advanced-features)
- [Fluxos de Trabalho Reais](#real-world-workflows)
- [Solução de Problemas](#troubleshooting)

---

# Introdução {#getting-started}

## Instalação {#installation}

### Requisitos:
- Revit **2023, 2024, 2025 ou 2026**
- Windows 10 ou posterior
- Assinatura ativa (teste gratuito de 30 dias disponível)

### Passos de Instalação:

#### Download da Autodesk App Store:
1. Abrir a Autodesk App Store no navegador
2. Pesquisar **"Visibility Manager"**
3. Clicar em **"Start Trial"** ou **"Subscribe"**

#### Instalação Automática:
- A App Store baixa e instala automaticamente
- Reiniciar o Revit após a instalação

### Verificar Instalação:
1. Abrir o Revit
2. Procurar a aba **IB-BIM** na faixa de opções
3. Você deve ver o botão **Visibility Manager**

### Local de Instalação:
- A ferramenta é instalada em:
  `C:\ProgramData\Autodesk\ApplicationPlugins\`
- Arquivos de log salvos em:
  `C:\ProgramData\IB-BIM\VisibilityManager\Logs\`

---

# Iniciar a Ferramenta {#launching-the-tool}

## Duas Formas de Iniciar:

### Método 1: Pela Faixa de Opções
1. Clicar na aba **IB-BIM**
2. Clicar no botão **Visibility Manager**

### Método 2: Pela Aba Add-Ins
1. Ir para a aba **Add-Ins**
2. Encontrar **External Tools**
3. Clicar em **Visibility Manager**

> **Nota:** Você deve ter uma **vista aberta**.
> A ferramenta opera na **vista ativa atual**.

---

# Visão Geral da Interface {#interface-overview}

Ao iniciar o Visibility Manager, você verá uma janela dividida em três seções principais:

```
┌──────────────────────────────────────────────────────┐
│     Copiar/Remover Filtros e Substituições VG         │
│     Escolha itens da vista atual e aplique nos        │
│     destinos selecionados                             │
├─────────────┬─────────────┬──────────────────────────┤
│ ❶ Origem   │ ❷ Vistas   │ ❸ Templates Destino      │
│   (Atual)   │   Destino   │                          │
└─────────────┴─────────────┴──────────────────────────┘
```


![Interface Modo Filtros](../Images/Filter%20Screen.png)
*Figura 1: Interface modo filtros – mostrando o painel de Filtros ativo (verde).*

![Interface Substituições VG](../Images/VG%20Screen.png)
*Figura 2: Modo Substituições V/G – mostrando o painel de Substituições ativo (azul).*

Este painel exibe itens da sua **vista ativa atual**:

- **Botões de rádio no topo:**
  - ⦿ **Filters** - Trabalhar com filtros de visibilidade
  - ○ **V/G Overrides** - Trabalhar com substituições gráficas de categorias

- **Descrição do modo:**
  - Explica o que o modo atual faz
  - Referencia os painéis [2] e [3] como destinos

- **Caixa de pesquisa:**
  - Filtrar a lista por nome
  - Filtragem em tempo real ao digitar

- **Caixa Selecionar Tudo:**
  - Marcar/desmarcar todos os itens visíveis

- **Lista de itens:**
  - Mostra todos os filtros ou substituições VG na vista atual
  - Caixas de seleção para selecionar itens

- **Contador inferior:**
  - "X filters selected" ou "X categories selected"

**Código de cores:**
- **Fundo verde** = Modo Filtros
- **Fundo azul claro** = Modo Substituições V/G

---

#### **Painel ❷: Escolher Vistas Destino (Centro)**

Selecione em quais vistas aplicar as alterações:

- **Filtros de tipo de vista (Superior):**
  - ☑ 3D Views (10) - O número mostra o total no projeto
  - ☐ Floor Plans (7)
  - ☐ Elevations (4)
  - ☐ Ceiling Plans (2)
  - Marque um tipo para mostrar apenas essas vistas

- **Contador total:**
  - Mostra a contagem filtrada

- **Selecionar Tudo:**
  - Seleciona todas as vistas visíveis na lista

- **Caixa de pesquisa:**
  - Filtrar vistas por nome

- **Lista de vistas:**
  - Todas as vistas do projeto (filtradas pelas seleções de tipo)
  - Formato: "ViewType: View Name"
  - Exemplo: "3D: 3D View: A10 - Substructure"

---

#### **Painel ❸: Escolher Templates Destino (Direita)**

Selecione em quais templates de vista aplicar as alterações:

- **Filtros de tipo de template (Superior):**
  - ☑ Floor Plans (2)
  - ☐ Sections (2)
  - ☐ 3D Views (1)
  - ☐ Ceiling Plans (0)
  - ☐ Elevations (0)

- **Caixa de pesquisa:**
  - Filtrar templates por nome

- **Selecionar Tudo:**
  - Seleciona todos os templates visíveis

---

#### **Botões de Ação (Parte inferior da janela)**

**Lado esquerdo — Exportar/Importar:**
```
Export current view Filters        [EXPORT] [XLSX]
Import Filters to current view     [IMPORT]
```

- **EXPORT** - Cria arquivo .XLSX (e .PAT se necessário)
- **XLSX** - Cria arquivo .CSV em vez disso
- **IMPORT** - Importar de arquivo previamente exportado

**Lado direito — Copiar/Remover:**
```
Copy to selected targets    [COPY] (botão verde)
Remove from selected       [REMOVE] (botão laranja/vermelho)
                          [Cancel]
```

- **COPY** - Copiar itens selecionados do Painel ❶ para Painéis ❷+❸
- **REMOVE** - Remover itens selecionados dos Painéis ❷+❸
- **Cancel** - Fechar janela sem alterações

---

### Conceitos Básicos

#### **Vista Atual = Referência**

**Entendimento chave:**
- A vista aberta ao iniciar a ferramenta é sua **vista de referência**
- O Painel ❶ sempre mostra itens desta vista
- **Para COPIAR/REMOVER:** A vista atual NÃO é modificada (é a origem)
- **Para IMPORTAR:** A vista atual É modificada (é o destino)

#### **Destinos = Onde as Alterações São Aplicadas**

**Os Painéis ❷ e ❸ são seus destinos:**
- Selecione vistas e/ou templates onde deseja aplicar alterações
- Pode selecionar de ambos os painéis simultaneamente
- A ferramenta processará todas as seleções

#### **Filtros vs. Substituições VG**

**Filtros (Visibilidade baseada em regras):**
- Controlam quais elementos são visíveis com base em regras
- Exemplo: "Mostrar apenas paredes onde o Nome do Tipo contém 'Exterior'"
- Pode ter lógica complexa (condições AND/OR)
- Aplicados por vista ou através de template

**Substituições VG (Gráficos de categoria):**
- Controlam como categorias inteiras são exibidas
- Exemplo: "Todas as Paredes exibidas em vermelho com espessura 3"
- Sem lógica condicional — afeta TODOS os elementos da categoria
- Cores de linha, padrões, espessuras, padrões de preenchimento, transparência

**Ambos são gerenciados da mesma forma nesta ferramenta!**

#### **Templates de Vista**

**O que são Templates:**
- Configurações de vista reutilizáveis (incluindo filtros e substituições VG)
- Um template pode ser aplicado a múltiplas vistas
- Alterar um template afeta todas as vistas que o usam

**Como a ferramenta lida com Templates:**
- Detecta automaticamente quando vistas destino usam templates
- Exibe aviso com contagem de vistas
- Aplica alterações ao template (afetando todas as vistas)
- Este é o comportamento do Revit, não uma limitação da ferramenta

---

## Trabalhar com Filtros {#working-with-filters}

### Copiar Filtros entre Vistas {#copying-filters-between-views}

**Caso de uso:** Você configurou filtros perfeitos em uma vista e quer aplicá-los a mais 20 vistas.

**Passo a passo:**

1. **Abrir a vista de origem:**
   - Abrir no Revit a vista que tem os filtros que deseja copiar
   - Esta será sua vista de referência

2. **Iniciar o Visibility Manager:**
   - Aba IB-BIM → clicar no botão Visibility Manager

3. **Selecionar Modo Filtros:**
   - Painel ❶: Clicar no botão de rádio **Filters**
   - O painel muda para verde
   - Mostra todos os filtros na vista atual

4. **Selecionar filtros para copiar:**
   - Painel ❶: Marque os filtros que deseja copiar
   - Use **Pesquisa** para encontrar filtros específicos rapidamente
   - Ou clique em **Selecionar Tudo** para copiar todos
   - O contador mostra: "X filters selected"

5. **Selecionar vistas destino:**
   - Painel ❷: Marque **tipos de vista** para filtrar (opcional)
   - Use **Pesquisa** para encontrar vistas específicas
   - Marque as vistas onde deseja estes filtros
   - O contador mostra: "X views selected"

6. **Selecionar templates destino (opcional):**
   - Painel ❸: Marque templates se necessário
   - Pode selecionar tanto vistas quanto templates
   - O contador mostra: "X templates selected"

7. **Executar a cópia:**
   - Clicar no botão **[COPY]** (verde)

8. **Lidar com avisos de Template (se aplicável):**
   - Se as vistas selecionadas usam templates, exibe:
```
   ⚠️ Templates Detectados

   As seguintes vistas usam templates:
   • Template: Architectural Plan (15 vistas)
   • Template: MEP Coordination (8 vistas)

   Total de vistas que serão afetadas: 23

   Aplicar filtros afetará TODAS as vistas
   que usam estes templates.

   Deseja continuar?

   [Yes] [No]
```

   - Clicar **Yes** para prosseguir (fluxo normal)
   - Clicar **No** para cancelar e reconsiderar

9. **Resolução de conflitos (se aplicável):**
   - Se filtros com o mesmo nome já existem:
```
   Já existem filtros com o mesmo nome.
   Como deseja prosseguir?

   ○ Merge - Manter existentes, adicionar apenas novos
   ⦿ Overwrite - Substituir existentes pelos importados
   ○ New Only - Pular existentes, adicionar apenas novos

   [OK] [Cancel]
```

   - **Merge:** Opção segura, não altera o existente
   - **Overwrite:** Atualiza filtros com sua configuração
   - **New Only:** Ignora duplicados
   - Clicar em **OK** para prosseguir

10. **Confirmação:**
    - Mensagem de sucesso exibida
    - Mostra quantas vistas/templates foram atualizados
    - A vista atual não foi alterada

---

### Remover Filtros das Vistas {#removing-filters-from-views}

**Caso de uso:** Precisa remover filtros obsoletos de múltiplas vistas de uma vez.

**Passo a passo:**

1. **Abrir qualquer vista como referência:**
   - Abrir uma vista que mostre os filtros que deseja remover
   - Qualquer vista serve — é apenas uma referência

2. **Iniciar o Visibility Manager**

3. **Selecionar Modo Filtros:**
   - Painel ❶: Clicar no botão de rádio **Filters**

4. **Selecionar filtros para remover:**
   - Painel ❶: Marque os filtros que deseja remover
   - Isto é apenas referência — mostra o que será removido

5. **Selecionar vistas destino:**
   - Painel ❷: Marque as vistas de onde remover
   - Painel ❸: Marque os templates de onde remover (opcional)

6. **Executar a remoção:**
   - Clicar no botão **[REMOVE]** (laranja/vermelho)

7. **Confirmar a operação:**
```
   ⚠️ Confirmar Remoção

   X filtros serão removidos de Y vistas/templates.

   Esta ação não pode ser desfeita.

   Deseja continuar?

   [Yes] [No]
```

8. **Confirmação:**
   - Mensagem de sucesso
   - Mostra quantos itens foram removidos

**Importante:**
- NÃO exclui a definição do filtro do projeto
- Apenas remove o filtro das vistas selecionadas
- O filtro ainda existe e pode ser reaplicado depois

---

### Exportar Filtros {#exporting-filters}

**Caso de uso:** Salvar configurações de filtros em arquivo para backup, documentação ou importação em outro projeto.

**Passo a passo:**

1. **Abrir a vista para exportar:**
   - Abrir a vista que contém os filtros a exportar
   - Esta é sua origem

2. **Iniciar o Visibility Manager**

3. **Selecionar Modo Filtros:**
   - Painel ❶: Clicar no botão de rádio **Filters**

4. **Selecionar filtros para exportar:**
   - Painel ❶: Marque os filtros a exportar
   - Pode exportar todos ou apenas alguns
   - Use pesquisa para encontrar filtros específicos

5. **Escolher formato de exportação:**

   **Opção A: Excel (.xlsx) — Recomendado**
   - Clicar no botão **[EXPORT]**
   - Melhor formatação, mais fácil de ler

   **Opção B: CSV (.csv)**
   - Clicar no botão **[XLSX]** (apesar do nome, cria CSV)
   - Para sistemas legados ou controle de versão (compatível com Git)

6. **Escolher local de salvamento:**
   - Diálogo de arquivo aparece
   - Selecionar a pasta onde salvar
   - Formato de nome padrão: `Filters_[ViewType]_[HHMMSS]_[YYYYMMDD]_[ViewName].xlsx`
   - Exemplo: `Filters_3D_145351_20260109_Section View.xlsx`
   - **Importante:** Mantenha o prefixo `Filters_` — usado para identificar o conteúdo do arquivo durante a importação
   - Pode alterar o restante do nome como desejar

7. **Exportação concluída:**
```
   ✓ Exportação Bem-sucedida

   Itens exportados:
   • Filters_3D_145351_20260109_Section View.xlsx (15 filtros)
   • Filters_3D_145351_20260109_Section View.pat (padrões de preenchimento)

   Local: [pasta selecionada]

   [Open Folder] [OK]
```

8. **Arquivos gerados:**
   - **Arquivo Excel/CSV:** Contém todos os dados dos filtros (sempre gerado)
   - **Arquivo PAT:** Contém padrões de preenchimento/hachura usados nos filtros (gerado apenas se os filtros usam padrões personalizados)

**⚠️ Importante: Os nomes dos arquivos devem coincidir**
- O nome do arquivo PAT deve ser **exatamente igual** ao arquivo Excel/CSV (exceto a extensão)
- Exemplo: `Filters_3D_145351_20260109_Office.xlsx` precisa de `Filters_3D_145351_20260109_Office.pat`
- **Se renomear o arquivo Excel após exportar, deve renomear o arquivo PAT também**

**Conteúdo da exportação:**

**Colunas Excel/CSV:**
- Filter_Name
- Enable_Filter (Yes/No)
- Visibility (Yes/No)
- Categories (categorias onde o filtro se aplica)
- Rules (lógica do filtro — condições AND/OR)
- Line_Color, Line_Pattern, Line_Weight
- Fill_Foreground_Color, Fill_Foreground_Pattern
- Fill_Background_Color, Fill_Background_Pattern
- Cut_Line_Color, Cut_Line_Pattern, Cut_Line_Weight
- Cut_Fill_Foreground_Color, Cut_Fill_Foreground_Pattern
- Cut_Fill_Background_Color, Cut_Fill_Background_Pattern
- Transparency
- Halftone (Yes/No)
- Custom_Parameters (se existirem)

**Biblioteca de Padrões (arquivo .pat):**
- Contém todas as definições de padrões de preenchimento/hachura usados nos filtros
- Nome do arquivo coincide com o arquivo Excel
- **Gerado apenas se os filtros usam padrões de preenchimento personalizados**
- Necessário para que todas as definições de padrões sejam importadas corretamente
- Manter na mesma pasta do arquivo Excel/CSV

**Melhores práticas:**
- Exporte para um local de rede compartilhado para acesso da equipe
- Mantenha arquivos Excel/CSV e arquivos de padrões juntos na mesma pasta
- Ao renomear arquivos, **mantenha o prefixo `Filters_` ou `VGOverrides_`**
- **Ao renomear o arquivo Excel, sempre renomeie o arquivo de padrões (.pat ou .lin) para coincidir**
- Considere controle de versão (Git) para arquivos CSV

---

### Importar Filtros {#importing-filters}

**Caso de uso:** Carregar filtros de arquivos previamente exportados para seu projeto atual.

**Passo a passo:**

1. **Abrir a vista destino:**
   - Abrir a vista onde deseja os filtros
   - **Importante:** Esta vista SERÁ modificada
   - Se usa template, afetará TODAS as vistas que usam esse template

2. **Iniciar o Visibility Manager**

3. **Selecionar Modo Filtros:**
   - Painel ❶: Clicar no botão de rádio **Filters**

4. **Clicar em Importar:**
   - Clicar no botão **[IMPORT]**

5. **Selecionar arquivo:**
   - Diálogo de arquivo aparece
   - Navegar até o arquivo Excel ou CSV exportado previamente
   - Selecionar e clicar em Open
   - **Nota:** A ferramenta valida o conteúdo do arquivo — se tentar importar um arquivo de VG Overrides no modo filtros, exibirá mensagem de erro
   - Certifique-se de que o tipo de arquivo corresponde ao modo atual

6. **Aviso de Template (se aplicável):**
```
   ⚠️ Template Detectado

   Sua vista atual usa o template: "Architectural Plan"
   Este template é usado por 15 vistas.

   A importação afetará todas as 15 vistas.

   Deseja continuar?

   [Yes] [No]
```

7. **Verificação da Biblioteca de Padrões:**
   - A ferramenta lê o conteúdo do arquivo Excel para determinar se um arquivo de padrões é necessário
   - **Só verifica se os filtros realmente usam padrões personalizados**
   - Se padrões forem necessários, procura automaticamente um arquivo .pat correspondente
   - Nome esperado: mesmo nome do arquivo Excel com extensão .pat
   - Deve estar na mesma pasta do arquivo Excel
   - **Importante:** Se renomeou o arquivo Excel, renomeie o PAT também

   **Se o arquivo PAT estiver ausente (quando padrões são necessários):**
```
   ⚠️ Biblioteca de Padrões Não Encontrada

   Esperado: Filters_3D_145351_20260109_Section View.pat
   Local: [mesma pasta do Excel]

   Os filtros serão importados mas padrões de preenchimento
   personalizados podem estar ausentes.

   Continuar sem padrões?

   [Yes] [No]
```

8. **Diálogo de Parâmetros Personalizados (se aplicável):**
```
   ⚠️ Parâmetros Personalizados Detectados

   Os seguintes parâmetros não existem neste projeto:

   • Wall_Finish
     Tipo: Text
     Categoria: Walls

   • Room_Number_Custom
     Tipo: Text
     Categoria: Rooms

   Criar estes parâmetros?

   [Yes] [No] [Cancel]
```

   - **Yes:** A ferramenta cria os parâmetros automaticamente (recomendado)
   - **No:** Pular estes parâmetros (filtros que os usam falharão)
   - **Cancel:** Cancelar toda a importação

9. **Resolução de conflitos:**
```
   Já existem filtros com o mesmo nome:
   • Filter 1
   • Filter 2

   Como deseja prosseguir?

   ○ Merge - Manter existentes, adicionar apenas novos
   ⦿ Overwrite - Substituir existentes pelos importados
   ○ New Only - Pular existentes, adicionar apenas novos

   [OK] [Cancel]
```

10. **Importação concluída:**
```
    ✓ Importação Bem-sucedida

    15 filtros importados para:
    • Level 1 - Architectural

    Através do template: Architectural Plan
    Total de vistas afetadas: 15

    Parâmetros personalizados criados: 2

    [OK]
```

---

## Trabalhar com Substituições VG {#working-with-vg-overrides}

As Substituições VG (Visibility/Graphics) controlam como categorias inteiras são exibidas — cores, espessuras de linha, padrões, transparência. O fluxo de trabalho é idêntico ao dos Filtros, apenas com conteúdo diferente.

### Categorias Suportadas {#supported-categories}

O IB-BIM Visibility Manager suporta todos os tipos de categorias principais do Revit:

- ✅ **Categorias de Modelo** — Paredes, Portas, Janelas, elementos MEP, Estrutura, Terreno, etc.
- ✅ **Categorias de Anotação** — Cotas, Tags, Notas de Texto, Símbolos, Itens de Detalhe, etc.
- ✅ **Categorias Analíticas** — Cargas, Links, Nós, Condições de Contorno, etc.

**Exemplo (Revit 2025/2026):**
292 categorias principais suportadas:
- 96 categorias de Modelo
- 180 categorias de Anotação
- 16 categorias Analíticas

O aplicativo detecta e suporta automaticamente todas as categorias disponíveis na sua versão do Revit.

#### Escopo Atual (v1.0.0)

✅ **Suportado:**
- Todas as categorias principais (Modelo, Anotação, Analítica)
- Copiar e remover substituições VG
- Operações de Exportar/Importar

⚠️ **Limitações:**
- Subcategorias ainda não são suportadas (planejado para v2.0)

**O que significa:**
- ✅ Paredes (categoria principal) — Totalmente suportado
- ⚠️ Paredes > Exterior (subcategoria) — Disponível na v2.0

A maioria dos fluxos de trabalho BIM depende principalmente das substituições de categorias principais. Subcategorias são uma granularidade avançada usada em cenários específicos.


### Copiar Substituições VG {#copying-vg-overrides}

**Caso de uso:** Padronizar os gráficos de categorias em múltiplas vistas (todas as paredes vermelhas, todas as portas azuis, etc.)

**Passo a passo:**

1. **Abrir a vista de origem:**
   - Abrir a vista que tem as substituições VG que deseja copiar

2. **Iniciar o Visibility Manager**

3. **Selecionar modo V/G Overrides:**
   - Painel ❶: Clicar no botão de rádio **V/G Overrides**
   - O painel muda para azul claro
   - Mostra categorias com substituições na vista atual

4. **Selecionar categorias:**
   - Painel ❶: Marque as categorias que deseja copiar

5. **Selecionar destinos:**
   - Painel ❷: Selecionar vistas destino
   - Painel ❸: Selecionar templates destino (opcional)

6. **Executar a cópia:**
   - Clicar em **[COPY]** (botão verde)
   - Lidar com avisos de template se aplicável
   - Resolução de conflitos (Merge/Overwrite/New Only)

7. **Confirmação:**
   - Mensagem de sucesso mostrando quantas categorias foram copiadas para quantas vistas

---

### Remover Substituições VG {#removing-vg-overrides}

**Passo a passo:**

1. **Abrir vista de referência:**
   - Uma vista que mostre as categorias com substituições a remover

2. **Iniciar o Visibility Manager**

3. **Selecionar modo V/G Overrides:**
   - Painel ❶: Clicar no botão de rádio **V/G Overrides**

4. **Selecionar categorias:**
   - Marque as categorias cujas substituições deseja remover

5. **Selecionar destinos:**
   - Painel ❷: Vistas de onde remover
   - Painel ❸: Templates de onde remover

6. **Executar remoção:**
   - Clicar em **[REMOVE]** (botão laranja)
   - Confirmar a operação no diálogo
   - Lidar com avisos de template

**Resultado:**
- Substituições de categoria removidas das vistas destino
- As categorias voltam aos gráficos padrão

---

### Exportar Substituições VG {#exporting-vg-overrides}

**Passo a passo:**

1. **Abrir a vista de origem:**
   - A vista com as substituições VG a exportar

2. **Iniciar o Visibility Manager**

3. **Selecionar modo V/G Overrides:**
   - Painel ❶: Clicar no botão de rádio **V/G Overrides**

4. **Selecionar categorias:**
   - Marque as categorias a exportar
   - Ou selecionar tudo

5. **Exportar:**
   - Para Excel clique **[EXPORT]**
   - Para CSV clique **[XLSX]**

6. **Escolher local:**
   - Diálogo de arquivo aparece — selecionar a pasta desejada
   - Formato de nome padrão: `VGOverrides_[ViewType]_[HHMMSS]_[YYYYMMDD]_[ViewName].xlsx`
   - **Importante:** Mantenha o prefixo `VGOverrides_`

7. **Arquivos gerados:**
   - **Arquivo Excel/CSV:** Contém todos os dados de substituições VG (sempre gerado)
   - **Arquivo LIN:** Contém padrões de linha usados nas substituições (gerado apenas se padrões de linha personalizados são usados)

**⚠️ Importante: Os nomes dos arquivos devem coincidir**
- O nome do arquivo LIN deve ser **exatamente igual** ao arquivo Excel/CSV (exceto a extensão)
- **Ao renomear o arquivo Excel, renomeie também o arquivo LIN**

**Conteúdo da exportação:**
- Nome da categoria
- Visibilidade (Mostrar/Ocultar)
- Cores de linha, padrões, espessuras
- Cores e padrões de preenchimento frente/fundo
- Configuração de linhas de corte
- Configuração de preenchimento de corte
- Transparência
- Meio-tom

---

### Importar Substituições VG {#importing-vg-overrides}

**Passo a passo:**

1. **Abrir a vista destino:**
   - A vista onde deseja as substituições VG
   - **Esta vista SERÁ modificada**

2. **Iniciar o Visibility Manager**

3. **Selecionar modo V/G Overrides:**
   - Painel ❶: Clicar no botão de rádio **V/G Overrides**

4. **Clicar em Importar:**
   - Clicar no botão **[IMPORT]**

5. **Selecionar arquivo:**
   - Selecionar o arquivo VG Excel/CSV exportado previamente
   - **Nota:** A ferramenta valida o conteúdo do arquivo — se tentar importar um arquivo de filtros no modo VG Overrides, exibirá mensagem de erro

6. **Lidar com diálogos:**
   - Aviso de template (se aplicável)
   - Verificação de biblioteca de padrões (se arquivo .lin necessário)
   - Resolução de conflitos (Merge/Overwrite/New Only)

7. **Confirmação:**
   - Mensagem de sucesso
   - Gráficos importados aplicados às categorias

**Nota:** Substituições VG não usam parâmetros personalizados, então esse diálogo não aparecerá.

---

## Recursos Avançados {#advanced-features}

### Trabalhar com Templates de Vista

**Entender o comportamento dos Templates:**

Quando você seleciona uma vista que usa template como destino, a ferramenta aplica as alterações ao **template em si**, não apenas à vista. Isso afeta **TODAS as vistas** que usam esse template.

**Por que isso acontece?**
- É a arquitetura do Revit, não uma limitação da ferramenta
- Quando uma vista usa template, filtros e VG ficam "bloqueados" pelo template
- Não podem ser modificados na vista sem quebrar o vínculo do template

**Opções:**

**Opção 1: Continuar (fluxo normal)**
- Clicar em **[Yes]**
- Alterações aplicadas ao template
- Todas as vistas com esse template são atualizadas
- **Geralmente é isso que você quer!**

**Opção 2: Cancelar e reconsiderar**
- Clicar em **[No]**
- Sem alterações

**Opção 3: Trabalhar diretamente com Templates**
- Não selecione vistas no Painel ❷
- Em vez disso, selecione templates no Painel ❸
- Mais claro — você sabe que está modificando um template

**Opção 4: Quebrar o vínculo do template**
- Se deseja afetar apenas uma vista que usa template:
  1. Fechar o Visibility Manager
  2. No Revit: Abrir a vista
  3. Painel de Propriedades → View Template → `<None>`
  4. A vista agora é independente
  5. Iniciar Visibility Manager e aplicar alterações
  6. Apenas esta vista é afetada

---

### Pesquisa e Filtragem

A ferramenta fornece pesquisa e filtragem poderosas para trabalhar rapidamente com grandes quantidades de itens.

**Como a pesquisa funciona:**

- **Tempo real:** Resultados atualizam ao digitar
- **Insensível a maiúsculas:** "Wall" e "wall" ambos funcionam
- **Correspondência parcial:** Pesquisa dentro do nome, não apenas no início
- **Seleções mantidas:** Marcar itens não altera a pesquisa
- **Limpar pesquisa:** Ao apagar texto, todos os itens aparecem novamente

---

## Fluxos de Trabalho Reais {#real-world-workflows}

### Para Gerentes BIM

**Cenário 1: Padronização de Templates do Escritório**

**Objetivo:** Criar filtros padrão da empresa e distribuí-los para todos os projetos

**Passos:**

1. **Criar Filtros Mestres:**
   - Abrir template da empresa ou projeto bem configurado
   - Configurar todos os filtros padrão

2. **Exportar Biblioteca Mestre:**
   - Iniciar Visibility Manager
   - Selecionar Modo Filtros
   - Selecionar Tudo
   - Exportar para local de rede

3. **Documentar para a Equipe:**
   - Criar README na mesma pasta
   - Descrever o que cada filtro faz
   - Incluir instruções de importação

4. **Distribuir para Projetos:**
   - Membros da equipe abrem seu projeto
   - Iniciam o Visibility Manager
   - Importam do local de rede
   - Todos os filtros padrão aplicados ao projeto

---

### Para Coordenadores BIM

**Cenário 1: Preparação para Reunião de Coordenação**

**Objetivo:** Configurar conjuntos de filtros idênticos em todos os modelos de todas as disciplinas

**Passos:**

1. **Criar Conjunto de Filtros de Coordenação:**
   - Criar filtros no modelo de Arquitetura
   - Exportar

2. **Distribuir para a Equipe:**
   - Enviar arquivos Excel + PAT por e-mail
   - Ou colocar na pasta BIM compartilhada

3. **A Equipe Importa:**
   - Coordenador de Estruturas: Abre modelo de estruturas, importa filtros
   - Coordenador MEP: Abre modelo MEP, importa filtros
   - Todos têm os mesmos filtros

4. **Resultado da Reunião:**
   - Todos veem os mesmos elementos
   - Mesmos códigos de cor
   - Sem confusão "na minha tela aparece diferente"

---

## Solução de Problemas {#troubleshooting}

### Os filtros não aparecem na vista após importar

**Sintoma:**
- A importação reporta sucesso
- Mas os filtros não são visíveis em Visibility/Graphics

**Possíveis causas e soluções:**

**Causa 1: Filtros desativados**
- **Solução:** No Revit: View → Visibility/Graphics (VG) → aba Filters → verificar coluna "Visibility"

**Causa 2: A vista usa template sem estes filtros**
- **Solução:** Verificar Properties → View Template, importar em uma vista que usa esse template

**Causa 3: As categorias do filtro não correspondem à vista**
- **Solução:** Verificar categorias do filtro, confirmar que a vista pode exibir essas categorias

---

### "Value" aparece no lugar dos valores reais

**Sintoma:**
- Após importar, as regras do filtro mostram "Value" em vez dos valores reais

**Causa:**
- Bug na versão 1.0.0 da ferramenta

**Solução:**
- **Atualizar para a versão 1.0.1 ou posterior**
- Re-exportar do projeto de origem
- Re-importar para o projeto de destino

---

### Aviso "Pattern Not Found"

**Sintoma:**
- Aviso no Revit após importar
- **Para Filtros:** Filtros importados mas usando padrões de preenchimento padrão em vez dos personalizados
- **Para Substituições VG:** Categorias importadas mas usando padrões de linha padrão em vez dos personalizados

**Solução:**
1. Renomear o arquivo de padrões para coincidir com o arquivo Excel
2. Mover o arquivo de padrões para a mesma pasta do arquivo Excel
3. Carregar padrões manualmente no Revit
4. Aceitar padrões padrão se os personalizados não são críticos

---

### A operação COPY não faz nada

**Possíveis causas:**
1. Clicou em "No" no aviso de template
2. Ainda está olhando a vista original (abra uma vista destino)
3. Os filtros já existem e selecionou "New Only"

---

### Obter Ajuda

**Autoatendimento:**
1. Consultar este guia do usuário
2. Verificar FAQ.md
3. Assistir tutoriais em vídeo
4. Verificar logs de depuração

**Suporte por e-mail:**

📧 **itzikb.bim@gmail.com**

**Incluir:**
1. **Detalhe do erro da janela de resultados** (Ctrl+A, Ctrl+C para copiar)
2. Versão do Revit (2023/2024/2025/2026)
3. Versão da ferramenta (exibida na janela: "Ver: 1.0.0")
4. O que tentou fazer (passo a passo)
5. O que aconteceu vs. o esperado
6. Capturas de tela (opcional mas ajudam)

**Arquivos de log** (apenas se o suporte solicitar):
- Local: `C:\ProgramData\IB-BIM\VisibilityManager\Logs\`

---

## Apêndice

### Atalhos de Teclado

**Na janela do Visibility Manager:**
- `Ctrl+F` - Focar caixa de pesquisa (Painel ❶)
- `Tab` - Mover entre painéis
- `Space` - Marcar/desmarcar item selecionado
- `Ctrl+A` - Selecionar tudo (quando a lista está focada)
- `Esc` - Cancelar/fechar janela

### Locais dos Arquivos

**Logs de Depuração:**
```
C:\ProgramData\IB-BIM\VisibilityManager\Logs
```

**Locais de Arquivos (Exportar / Importar):**
```
Não há diretório de saída predefinido.
Ao exportar ou importar, o usuário seleciona a pasta
desejada através do diálogo padrão de arquivos.
A ferramenta não força nem assume um caminho de exportação padrão.
```

**Instalação:**
```
C:\ProgramData\Autodesk\ApplicationPlugins\VisibilityManager.bundle\
```

### Referência do Formato Excel

**Referência de colunas:**

| Coluna | Descrição | Exemplo |
|--------|-----------|---------|
| Filter_Name | Nome do filtro | "Exterior Walls - Phase New" |
| Enable_Filter | Ativado na vista | "Yes" ou "No" |
| Visibility | Mostrar ou Ocultar | "Yes" ou "No" |
| Categories | Nomes das categorias | "Walls; Doors; Windows" |
| Rules | Lógica do filtro | "(Phase Created = New) AND (Type Name Contains 'Ext')" |
| Line_Color | Cor da linha de projeção | "RGB(255,0,0)" ou "No Override" |
| Transparency | Porcentagem de transparência | "0"–"100" |
| Halftone | Meio-tom ligado/desligado | "Yes" ou "No" |

### Glossário
- BIM — Modelagem da Informação da Construção
- Filter — Regra de visibilidade baseada em condições para mostrar/ocultar elementos
- VG Overrides — Substituições de Visibility/Graphics ao nível de categoria
- View Template — Configuração de vista reutilizável que inclui filtros
- Custom Parameter — Parâmetro criado pelo usuário (não nativo do Revit)
- Pattern Library — Coleção de definições de padrões de preenchimento (arquivo .PAT)
- Conflict Resolution — Como lidar com itens duplicados (Merge/Overwrite/New Only)
- Current View — A vista ativa ao iniciar a ferramenta (referência do Painel ❶)
- Target Views — Vistas onde as alterações são aplicadas (Painel ❷)
- Target Templates — Templates onde as alterações são aplicadas (Painel ❸)

Fim do Guia do Usuário
Tem perguntas? E-mail: itzikb.bim@gmail.com
Última atualização: Novembro 2025
Versão: 1.0.0
