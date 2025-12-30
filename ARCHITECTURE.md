# Arquitetura do Agente Claude Code

## 📐 Visão Geral da Arquitetura

```
┌─────────────────────────────────────────────────────────────────┐
│                         UTILIZADOR                               │
│                              ↓                                   │
│                    [Claude Code CLI]                             │
└─────────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────────┐
│                     AGENTE CLAUDE CODE                           │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │            System Prompt (.claude/system_prompt.md)      │   │
│  │  - Persona: Analista de Requisitos / Technical Writer   │   │
│  │  - Princípios de trabalho                               │   │
│  │  - Fluxo de execução de tarefas                          │   │
│  │  - Regras de validação                                   │   │
│  └──────────────────────────────────────────────────────────┘   │
│                               ↓                                  │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │      Slash Commands (.claude/commands/)                  │   │
│  │  /write-spec  /update-spec  /write-pbi  /update-pbi     │   │
│  │  /write-cr    /update-cr    /show-context  /show-templates│  │
│  └──────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────────┐
│                   CAMADA DE INSTRUÇÕES                           │
│  ┌────────────────┐  ┌────────────────┐  ┌─────────────────┐   │
│  │   CONTEXTO     │  │    TAREFAS     │  │   TEMPLATES     │   │
│  │                │  │                │  │                 │   │
│  │ context_       │  │ task_write_    │  │ template_US     │   │
│  │  project.md    │  │  spec.md       │  │ template_SFR    │   │
│  │                │  │ task_update_   │  │ template_PFR    │   │
│  │ context_       │  │  spec.md       │  │ template_RAF    │   │
│  │  task.md       │  │ task_write_    │  │ template_CR     │   │
│  │                │  │  pbi.md        │  │                 │   │
│  │                │  │ task_update_   │  │                 │   │
│  │                │  │  pbi.md        │  │                 │   │
│  │                │  │ task_write_    │  │                 │   │
│  │                │  │  cr.md         │  │                 │   │
│  │                │  │ task_update_   │  │                 │   │
│  │                │  │  cr.md         │  │                 │   │
│  └────────────────┘  └────────────────┘  └─────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────────┐
│                  INTEGRAÇÕES EXTERNAS (MCP)                      │
│  ┌─────────────┐    ┌──────────────┐    ┌────────────────┐     │
│  │   Azure     │    │   Google     │    │     Figma      │     │
│  │   DevOps    │    │    Drive     │    │                │     │
│  │             │    │              │    │                │     │
│  │ - Work Items│    │ - RFP        │    │ - Designs      │     │
│  │ - PBIs      │    │ - Proposta   │    │ - Protótipos   │     │
│  │ - CRs       │    │ - Specs      │    │ - Assets       │     │
│  │ - Issues    │    │ - Backlog    │    │                │     │
│  └─────────────┘    └──────────────┘    └────────────────┘     │
└─────────────────────────────────────────────────────────────────┘
                               ↓
┌─────────────────────────────────────────────────────────────────┐
│                        OUTPUTS                                   │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │ outputs/specs│  │ outputs/pbis │  │ outputs/crs  │          │
│  │              │  │              │  │              │          │
│  │ - US         │  │ - PBI docs   │  │ - CR docs    │          │
│  │ - SFR        │  │              │  │              │          │
│  │ - PFR        │  │              │  │              │          │
│  │ - RAF        │  │              │  │              │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🔄 Fluxo de Execução

### Exemplo: Criar Especificação Funcional

```
1. UTILIZADOR
   └─> Invoca: /write-spec

2. AGENTE
   └─> Carrega: .claude/commands/write-spec.md
       └─> Lê instrução: "Ler instructions/tasks/task_write_spec.md"

3. CAMADA DE INSTRUÇÕES
   └─> Lê: instructions/tasks/task_write_spec.md
       └─> Identifica necessidade de contexto
           ├─> Lê: instructions/context/context_project.md
           ├─> Lê: instructions/context/context_task.md
           └─> Identifica formato necessário

4. AGENTE
   └─> Pergunta ao utilizador:
       ├─> "Qual formato? (US, SFR, PFR, RAF)"
       ├─> "Tem estrutura base?"
       └─> "Quais inputs? (Issue, Notas, Figma)"

5. UTILIZADOR
   └─> Fornece:
       ├─> Formato: "User Stories"
       ├─> Input: "Issue #12345"
       └─> Input: "Link Figma: https://..."

6. INTEGRAÇÕES (MCP)
   └─> Consulta Azure DevOps
       └─> Obtém detalhes do Issue #12345
   └─> Consulta Figma
       └─> Obtém informações do design

7. AGENTE
   └─> Processa informações
       └─> Lê template: instructions/templates/template_US.md
       └─> Aplica instruções de task_write_spec.md
       └─> Gera especificação

8. OUTPUT
   └─> Salva: outputs/specs/2025-01-15_funcionalidade_US.md
   └─> Apresenta artefato no chat

9. AGENTE
   └─> Pergunta próximos passos:
       └─> "Deseja criar PBI no DevOps?"
```

---

## 🏗️ Componentes da Arquitetura

### 1. System Prompt (Cérebro)
**Arquivo**: `.claude/system_prompt.md`

**Função**: Define identidade, comportamento e conhecimento base do agente

**Contém**:
- Persona (Analista de Requisitos / Technical Writer)
- Princípios de trabalho (clareza, precisão, português PT)
- Estrutura de instruções (onde encontrar tarefas, contextos, templates)
- Comandos disponíveis
- Integrações MCP
- Fluxo de trabalho geral
- Validações importantes

**Quando é carregado**: Automaticamente ao iniciar conversa no diretório

---

### 2. Slash Commands (Interface)
**Diretório**: `.claude/commands/`

**Função**: Fornecer interface user-friendly para invocar tarefas

**Arquivos**:
- `write-spec.md` → `/write-spec`
- `update-spec.md` → `/update-spec`
- `write-pbi.md` → `/write-pbi`
- `update-pbi.md` → `/update-pbi`
- `write-cr.md` → `/write-cr`
- `update-cr.md` → `/update-cr`
- `show-context.md` → `/show-context`
- `show-templates.md` → `/show-templates`

**Como funcionam**:
1. Utilizador digita `/write-spec`
2. Claude Code carrega conteúdo de `write-spec.md`
3. Agente lê instrução: "Leia task_write_spec.md e execute"
4. Agente processa a tarefa

---

### 3. Camada de Instruções (Conhecimento)

#### 3.1 Contexto (`instructions/context/`)

**context_project.md** 🌟 **ARQUIVO CENTRAL**
- Links do Google Drive (RFP, Proposta, Specs)
- Nome do projeto no Azure DevOps
- Links do Figma
- Contexto específico do produto
- **EDITE ESTE ARQUIVO para mudar de projeto**

**context_task.md**
- Tipos de inputs que podem ser fornecidos
- Como usar cada tipo de input
- Quando consultar MCP servers

#### 3.2 Tarefas (`instructions/tasks/`)

Cada tarefa tem um arquivo dedicado:
- `task_write_spec.md` - Como escrever especificação
- `task_update_spec.md` - Como atualizar especificação
- `task_write_pbi.md` - Como escrever PBI (placeholder)
- `task_update_pbi.md` - Como atualizar PBI (placeholder)
- `task_write_cr.md` - Como escrever CR
- `task_update_cr.md` - Como atualizar CR (placeholder)

**Estrutura típica de um arquivo de tarefa**:
1. Descrição e objetivo
2. Fluxo da tarefa (passo a passo)
3. Especificação de output
4. Instruções específicas

#### 3.3 Templates (`instructions/templates/`)

Formatos de especificação disponíveis:
- `template_US.md` - User Stories
- `template_SFR.md` - Software Functional Requirements
- `template_PFR.md` - Product Functional Requirements
- `template_RAF.md` - RAF Specification (placeholder)
- `template_CR.md` - Change Request

---

### 4. MCP Servers (Integrações)
**Arquivo**: `.claude/mcp.json`

**Servidores configurados**:

#### Azure DevOps (ado)
- **Status**: ✅ Configurado
- **Path**: Local (`C:\Users\igorcarvalho\Desktop\MCP-Servers-Tests\...`)
- **Uso**: Consultar/criar work items

#### Google Drive (gdrive)
- **Status**: ⚠️ Requer credenciais OAuth
- **Uso**: Acessar documentação do projeto
- **Setup**: Ver `.claude/MCP_SETUP.md`

#### Figma (figma)
- **Status**: ⚠️ Requer token de acesso
- **Uso**: Consultar designs e protótipos
- **Setup**: Ver `.claude/MCP_SETUP.md`

---

### 5. Outputs (Artefatos)
**Diretório**: `outputs/`

**Estrutura**:
- `outputs/specs/` - Especificações funcionais geradas
- `outputs/pbis/` - Product Backlog Items gerados
- `outputs/crs/` - Change Requests gerados

**Nomenclatura sugerida**:
- `YYYY-MM-DD_nome-funcionalidade_[formato].md`
- `PBI-XXXXX_titulo.md`
- `CR-XXXXX_titulo.md`

---

## 🔐 Segurança

### Proteção de Credenciais

**`.gitignore`**:
- Bloqueia commit de `.env` (credenciais)
- Protege cache de MCP servers
- Exclui arquivos sensíveis

**`.env.example`**:
- Template de variáveis de ambiente
- Sem credenciais reais
- Serve como documentação

---

## 🎯 Princípios de Design

### 1. Modularidade
Cada componente é independente e pode ser atualizado sem afetar outros.

### 2. Separação de Responsabilidades
- **System Prompt**: Identidade e comportamento
- **Commands**: Interface do utilizador
- **Instructions**: Conhecimento e regras
- **MCP**: Integrações externas
- **Outputs**: Artefatos gerados

### 3. Configuração Centralizada
Contexto do projeto em **um único arquivo** (`context_project.md`)

### 4. Extensibilidade
Fácil adicionar:
- Novas tarefas (criar arquivo + comando)
- Novos templates (criar arquivo)
- Novas integrações MCP (adicionar ao mcp.json)

### 5. Documentação Como Código
Instruções em Markdown, versionáveis e editáveis

---

## 🔄 Ciclo de Vida de uma Tarefa

```
┌─────────────────┐
│  1. INVOCAÇÃO   │  Utilizador: /write-spec
└────────┬────────┘
         ↓
┌─────────────────┐
│  2. CARREGAMENTO│  Agente carrega command → task → context
└────────┬────────┘
         ↓
┌─────────────────┐
│  3. COLETA      │  Agente pergunta informações faltantes
└────────┬────────┘
         ↓
┌─────────────────┐
│  4. INTEGRAÇÃO  │  Agente consulta MCP servers se necessário
└────────┬────────┘
         ↓
┌─────────────────┐
│  5. PROCESSAMENTO│ Agente aplica template + instruções
└────────┬────────┘
         ↓
┌─────────────────┐
│  6. GERAÇÃO     │  Agente cria especificação
└────────┬────────┘
         ↓
┌─────────────────┐
│  7. PERSISTÊNCIA│  Salva em outputs/ + apresenta artefato
└────────┬────────┘
         ↓
┌─────────────────┐
│  8. CONFIRMAÇÃO │  Agente pergunta próximos passos
└─────────────────┘
```

---

## 📊 Diagrama de Dependências

```
system_prompt.md
    ↓
    ├─> commands/*.md
    │       ↓
    │       └─> tasks/*.md
    │               ↓
    │               ├─> context/context_project.md
    │               ├─> context/context_task.md
    │               └─> templates/*.md
    │
    └─> mcp.json
            ↓
            ├─> Azure DevOps MCP
            ├─> Google Drive MCP
            └─> Figma MCP
```

---

## 🚀 Pontos de Extensão

### Adicionar Nova Tarefa

1. Criar `instructions/tasks/task_nova_tarefa.md`
2. Criar `.claude/commands/nova-tarefa.md`
3. Adicionar referência em `system_prompt.md`
4. Documentar em `README.md`

### Adicionar Novo Formato de Spec

1. Criar `instructions/templates/template_NOVO.md`
2. Atualizar tarefas relevantes (write-spec, update-spec)
3. Adicionar referência em `system_prompt.md`
4. Documentar em `README.md`

### Adicionar Nova Integração MCP

1. Adicionar configuração em `.claude/mcp.json`
2. Documentar credenciais em `.claude/MCP_SETUP.md`
3. Atualizar `context_task.md` com exemplos de uso
4. Adicionar variáveis ao `.env.example`

---

## 🎓 Padrões Arquiteturais Aplicados

1. **Separation of Concerns**: Cada camada tem responsabilidade única
2. **Single Source of Truth**: Contexto do projeto centralizado
3. **Command Pattern**: Slash commands encapsulam ações
4. **Template Method**: Templates definem estrutura, conteúdo varia
5. **Strategy Pattern**: Diferentes formatos de spec = diferentes estratégias
6. **Facade Pattern**: System prompt simplifica complexidade interna

---

**Versão da Arquitetura**: 1.0.0
**Data**: 2025-01-15
**Status**: ✅ Implementado e Documentado
