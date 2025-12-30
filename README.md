# Agente Claude Code - Especificação Funcional

Agente especializado em criar e manter especificações funcionais, requisitos de produto e documentação técnica para projetos de software.

## 📋 Visão Geral

Este agente atua como um **Analista de Requisitos / Technical Writer**, auxiliando equipas de desenvolvimento na criação de:

- ✅ Especificações Funcionais (User Stories, SFR, PFR, RAF)
- ✅ Product Backlog Items (PBIs)
- ✅ Change Requests (CRs)
- ✅ Documentação de requisitos funcionais

## 🏗️ Arquitetura

```
instrucions-test-claude-code/
├── .claude/
│   ├── system_prompt.md          # Prompt principal do agente
│   ├── mcp.json                  # Configuração MCP servers
│   ├── MCP_SETUP.md              # Instruções de setup dos MCPs
│   └── commands/                 # Slash commands
│       ├── write-spec.md         # /write-spec
│       ├── update-spec.md        # /update-spec
│       ├── write-pbi.md          # /write-pbi
│       ├── update-pbi.md         # /update-pbi
│       ├── write-cr.md           # /write-cr
│       ├── update-cr.md          # /update-cr
│       ├── show-context.md       # /show-context
│       └── show-templates.md     # /show-templates
│
├── instructions/
│   ├── context/
│   │   ├── context_project.md    # Contexto do projeto (EDITE AQUI!)
│   │   └── context_task.md       # Tipos de inputs de tarefa
│   ├── tasks/
│   │   ├── task_write_spec.md    # Instruções: escrever spec
│   │   ├── task_update_spec.md   # Instruções: atualizar spec
│   │   ├── task_write_pbi.md     # Instruções: escrever PBI
│   │   ├── task_update_pbi.md    # Instruções: atualizar PBI
│   │   ├── task_write_cr.md      # Instruções: escrever CR
│   │   └── task_update_cr.md     # Instruções: atualizar CR
│   └── templates/
│       ├── template_US.md        # Template User Stories
│       ├── template_SFR.md       # Template Software Functional Req.
│       ├── template_PFR.md       # Template Product Functional Req.
│       ├── template_RAF.md       # Template RAF Specification
│       └── template_CR.md        # Template Change Request
│
├── outputs/                      # Artefatos gerados
│   ├── specs/                    # Especificações funcionais
│   ├── pbis/                     # Product Backlog Items
│   └── crs/                      # Change Requests
│
├── main_instructions.md          # [LEGACY] Índice original
└── README.md                     # Esta documentação
```

## 🚀 Como Usar

### Início Rápido

1. **Configure os MCP Servers** (primeira vez):
   ```bash
   # Leia as instruções em .claude/MCP_SETUP.md
   # Configure credenciais do Google Drive e Figma
   ```

2. **Inicie uma tarefa** usando slash commands:
   ```
   /write-spec
   /update-spec
   /write-cr
   ```

3. **Ou interaja naturalmente**:
   ```
   "Preciso criar uma especificação funcional para o carrinho de compras"
   "Atualiza o CR 34991 com os novos requisitos"
   ```

### Comandos Disponíveis

| Comando | Descrição |
|---------|-----------|
| `/write-spec` | Criar nova especificação funcional |
| `/update-spec` | Atualizar especificação existente |
| `/write-pbi` | Criar Product Backlog Item |
| `/update-pbi` | Atualizar PBI existente |
| `/write-cr` | Criar Change Request |
| `/update-cr` | Atualizar CR existente |
| `/show-context` | Mostrar contextos disponíveis |
| `/show-templates` | Listar templates de output |

### Fluxo de Trabalho Típico

1. **Invocar comando** ou descrever tarefa
2. **Agente consulta** arquivos de instrução e contexto
3. **Agente coleta** informações necessárias (MCP servers, inputs do utilizador)
4. **Agente pergunta** sobre detalhes faltantes (formato, estrutura, etc.)
5. **Agente gera** especificação conforme template
6. **Artefato salvo** em `outputs/` e apresentado no chat
7. **Confirmação** de próximos passos (criar no DevOps, etc.)

## 🔧 Configuração

### Personalizar para seu Projeto

**IMPORTANTE**: Para adaptar o agente ao seu projeto, edite apenas:

📝 **`instructions/context/context_project.md`**

Este arquivo contém todas as informações específicas do projeto:
- Links do Google Drive (RFP, Proposta, Specs)
- Nome do projeto no Azure DevOps
- Links do Figma
- Contexto específico do produto

**Não é necessário editar outros arquivos** - toda personalização de projeto está centralizada aqui.

### MCP Servers

O agente integra-se com:

- **Azure DevOps**: Consultar/criar work items
- **Google Drive**: Acessar documentação do projeto
- **Figma**: Consultar designs e protótipos

Veja instruções completas em `.claude/MCP_SETUP.md`

## 📝 Princípios do Agente

O agente segue estes princípios:

✅ **Clareza e Concisão** - Linguagem simples e direta
✅ **Português de Portugal** - Todo output em PT-PT
✅ **Apenas Requisitos Funcionais** - Não inventa requisitos técnicos
✅ **Não Inventa Informação** - Especifica apenas o explicitamente solicitado
✅ **Pergunta Quando em Dúvida** - Sempre confirma antes de assumir
✅ **Dupla Audiência** - Escreve para clientes e desenvolvedores

## 📚 Formatos de Especificação

### User Stories (US)
Formato ágil com critérios de aceitação. Ver `instructions/templates/template_US.md`

### Software Functional Requirements (SFR)
Requisitos estruturados com pré-condições, regras e pós-condições. Ver `instructions/templates/template_SFR.md`

### Product Functional Requirements (PFR)
Documentação orientada a produto com visão geral e requisitos funcionais. Ver `instructions/templates/template_PFR.md`

### RAF Specification
[A preencher - adicione descrição quando completar o template]

### Change Request (CR)
Especificação de alterações com contexto, comportamento atual e novo comportamento. Ver `instructions/templates/template_CR.md`

## 🔄 Manutenção

### Adicionar Nova Tarefa

1. Criar arquivo de instrução em `instructions/tasks/task_nova_tarefa.md`
2. Criar slash command em `.claude/commands/nova-tarefa.md`
3. Atualizar `system_prompt.md` listando a nova tarefa

### Adicionar Novo Template

1. Criar template em `instructions/templates/template_NOVO.md`
2. Atualizar `system_prompt.md` listando o novo formato
3. Atualizar instruções das tarefas relevantes

### Atualizar Contexto do Projeto

Edite apenas: `instructions/context/context_project.md`

## 🐛 Troubleshooting

### Agente não encontra instruções
- Verifique se os arquivos estão em `instructions/tasks/` e `instructions/templates/`
- Confirme nomenclatura: `task_*.md` e `template_*.md`

### MCP Servers não funcionam
- Consulte `.claude/MCP_SETUP.md`
- Verifique credenciais em variáveis de ambiente
- Teste cada servidor individualmente

### Outputs não são salvos
- Verifique permissões do diretório `outputs/`
- Confirme que subdiretórios existem: `specs/`, `pbis/`, `crs/`

## 📖 Arquivos Legacy

- `main_instructions.md` - Mantido por compatibilidade, mas substituído pelo system prompt

## 🤝 Contribuir

Para melhorar o agente:

1. Edite instruções em `instructions/tasks/`
2. Adicione exemplos nos templates em `instructions/templates/`
3. Expanda contexto em `instructions/context/context_task.md`
4. Documente mudanças neste README

## 📄 Licença

[Adicione sua licença aqui]

---

**Desenvolvido para**: Análise de Requisitos e Technical Writing
**Alimentado por**: Claude Code + MCP Servers
**Versão**: 1.0.0
