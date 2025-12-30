# 📑 Índice de Navegação - Agente Claude Code

## 🚀 Começar Rapidamente

1. **Primeiro Uso** → [`QUICKSTART.md`](QUICKSTART.md)
2. **Documentação Completa** → [`README.md`](README.md)
3. **Configurar MCP Servers** → [`.claude/MCP_SETUP.md`](.claude/MCP_SETUP.md)
4. **Personalizar para seu Projeto** → [`instructions/context/context_project.md`](instructions/context/context_project.md)

---

## 📚 Documentação

| Arquivo | Descrição | Quando Usar |
|---------|-----------|-------------|
| **[README.md](README.md)** | Documentação principal completa | Entender o agente e suas capacidades |
| **[QUICKSTART.md](QUICKSTART.md)** | Guia de início rápido em 5 minutos | Começar a usar imediatamente |
| **[ARCHITECTURE.md](ARCHITECTURE.md)** | Arquitetura técnica detalhada | Entender como funciona internamente |
| **[IMPLEMENTATION_SUMMARY.md](IMPLEMENTATION_SUMMARY.md)** | Resumo da implementação | Ver o que foi criado e próximos passos |
| **[INDEX.md](INDEX.md)** | Este arquivo - navegação rápida | Encontrar documentação específica |

---

## ⚙️ Configuração

| Arquivo | Descrição | Ação Necessária |
|---------|-----------|-----------------|
| **[.claude/mcp.json](.claude/mcp.json)** | Configuração MCP servers | ✅ Já configurado |
| **[.claude/MCP_SETUP.md](.claude/MCP_SETUP.md)** | Guia setup MCP servers | 📖 Ler para configurar Google Drive e Figma |
| **[.env.example](.env.example)** | Template variáveis de ambiente | 📝 Copiar para `.env` e preencher credenciais |
| **[.gitignore](.gitignore)** | Proteção de credenciais | ✅ Já configurado |

---

## 🧠 Sistema do Agente

### Núcleo

| Arquivo | Tipo | Descrição |
|---------|------|-----------|
| **[.claude/system_prompt.md](.claude/system_prompt.md)** | System Prompt | Identidade, persona e comportamento do agente |

### Comandos

| Comando | Arquivo | Descrição |
|---------|---------|-----------|
| `/write-spec` | [write-spec.md](.claude/commands/write-spec.md) | Escrever nova especificação funcional |
| `/update-spec` | [update-spec.md](.claude/commands/update-spec.md) | Atualizar especificação existente |
| `/write-pbi` | [write-pbi.md](.claude/commands/write-pbi.md) | Criar Product Backlog Item |
| `/update-pbi` | [update-pbi.md](.claude/commands/update-pbi.md) | Atualizar PBI existente |
| `/write-cr` | [write-cr.md](.claude/commands/write-cr.md) | Criar Change Request |
| `/update-cr` | [update-cr.md](.claude/commands/update-cr.md) | Atualizar CR existente |
| `/show-context` | [show-context.md](.claude/commands/show-context.md) | Mostrar contextos disponíveis |
| `/show-templates` | [show-templates.md](.claude/commands/show-templates.md) | Listar templates de output |

---

## 📖 Instruções

### Contexto

| Arquivo | Descrição | Editar? |
|---------|-----------|---------|
| **[context_project.md](instructions/context/context_project.md)** 🌟 | Contexto do projeto (links, nome projeto, etc.) | ✅ **SIM** - Edite aqui para mudar de projeto |
| **[context_task.md](instructions/context/context_task.md)** | Tipos de inputs e como usar | ⚠️ Apenas se necessário |

### Tarefas

| Arquivo | Status | Descrição |
|---------|--------|-----------|
| [task_write_spec.md](instructions/tasks/task_write_spec.md) | ✅ Completo | Instruções para escrever especificação |
| [task_update_spec.md](instructions/tasks/task_update_spec.md) | ✅ Completo | Instruções para atualizar especificação |
| [task_write_cr.md](instructions/tasks/task_write_cr.md) | ✅ Completo | Instruções para criar CR |
| [task_write_pbi.md](instructions/tasks/task_write_pbi.md) | 📝 Placeholder | A preencher com suas instruções |
| [task_update_pbi.md](instructions/tasks/task_update_pbi.md) | 📝 Placeholder | A preencher com suas instruções |
| [task_update_cr.md](instructions/tasks/task_update_cr.md) | 📝 Placeholder | A preencher com suas instruções |

### Templates

| Arquivo | Formato | Status | Exemplo |
|---------|---------|--------|---------|
| [template_US.md](instructions/templates/template_US.md) | User Stories | ✅ Completo | Ver arquivo |
| [template_SFR.md](instructions/templates/template_SFR.md) | Software Functional Requirements | ✅ Completo | Ver arquivo |
| [template_PFR.md](instructions/templates/template_PFR.md) | Product Functional Requirements | ✅ Completo | Ver arquivo |
| [template_CR.md](instructions/templates/template_CR.md) | Change Request | ✅ Completo | Ver arquivo |
| [template_RAF.md](instructions/templates/template_RAF.md) | RAF Specification | 📝 Placeholder | A preencher |

---

## 📂 Outputs

| Diretório | Conteúdo | Nomenclatura Sugerida |
|-----------|----------|----------------------|
| [outputs/specs/](outputs/specs/) | Especificações funcionais | `YYYY-MM-DD_nome-funcionalidade_[US\|SFR\|PFR\|RAF].md` |
| [outputs/pbis/](outputs/pbis/) | Product Backlog Items | `PBI-XXXXX_titulo.md` |
| [outputs/crs/](outputs/crs/) | Change Requests | `CR-XXXXX_titulo.md` |

---

## 🔗 Integrações (MCP Servers)

| Servidor | Status | Configuração | Uso |
|----------|--------|--------------|-----|
| **Azure DevOps** | ✅ Configurado | Local path já definido | Consultar/criar work items |
| **Google Drive** | ⚠️ Requer setup | [MCP_SETUP.md](.claude/MCP_SETUP.md) | Acessar RFP, Proposta, Specs |
| **Figma** | ⚠️ Requer setup | [MCP_SETUP.md](.claude/MCP_SETUP.md) | Consultar designs |

---

## ✅ Checklist de Início

- [ ] 1. Leia [QUICKSTART.md](QUICKSTART.md)
- [ ] 2. Edite [context_project.md](instructions/context/context_project.md) com informações do seu projeto
- [ ] 3. Configure MCP servers (Google Drive e Figma) - ver [MCP_SETUP.md](.claude/MCP_SETUP.md)
- [ ] 4. Copie `.env.example` para `.env` e preencha credenciais
- [ ] 5. Reinicie Claude Code
- [ ] 6. Teste com `/show-context`
- [ ] 7. Crie sua primeira especificação com `/write-spec`
- [ ] 8. Preencha placeholders de tarefas conforme necessário:
  - [ ] [task_write_pbi.md](instructions/tasks/task_write_pbi.md)
  - [ ] [task_update_pbi.md](instructions/tasks/task_update_pbi.md)
  - [ ] [task_update_cr.md](instructions/tasks/task_update_cr.md)
  - [ ] [template_RAF.md](instructions/templates/template_RAF.md)

---

## 🆘 Ajuda e Troubleshooting

### Problemas Comuns

| Problema | Solução |
|----------|---------|
| Comandos não aparecem | Reinicie Claude Code |
| MCP não funciona | Ver [MCP_SETUP.md](.claude/MCP_SETUP.md) → Troubleshooting |
| Agente não segue instruções | Verifique se arquivos estão em `instructions/` |
| Quer mudar de projeto | Edite **apenas** [context_project.md](instructions/context/context_project.md) |

### Onde Pedir Ajuda

1. **Documentação**: [README.md](README.md) - Seção "Troubleshooting"
2. **MCP Setup**: [MCP_SETUP.md](.claude/MCP_SETUP.md)
3. **Arquitetura**: [ARCHITECTURE.md](ARCHITECTURE.md) - Para entender internamente

---

## 📋 Estrutura Visual

```
instrucions-test-claude-code/
│
├── 📘 DOCUMENTAÇÃO
│   ├── README.md                    ← Documentação principal
│   ├── QUICKSTART.md                ← Guia de início rápido
│   ├── ARCHITECTURE.md              ← Arquitetura técnica
│   ├── IMPLEMENTATION_SUMMARY.md    ← Resumo da implementação
│   └── INDEX.md                     ← Este arquivo
│
├── ⚙️ CONFIGURAÇÃO
│   ├── .claude/
│   │   ├── system_prompt.md         ← Prompt do agente
│   │   ├── mcp.json                 ← Config MCP servers
│   │   ├── MCP_SETUP.md             ← Guia setup MCP
│   │   └── commands/                ← Slash commands (8 arquivos)
│   ├── .env.example                 ← Template credenciais
│   └── .gitignore                   ← Proteção de secrets
│
├── 📖 INSTRUÇÕES
│   └── instructions/
│       ├── context/
│       │   ├── context_project.md   ← 🌟 EDITE AQUI (projeto)
│       │   └── context_task.md      ← Tipos de inputs
│       ├── tasks/                   ← 6 arquivos de tarefas
│       └── templates/               ← 5 templates de formato
│
└── 📁 OUTPUTS
    └── outputs/
        ├── specs/                   ← Especificações geradas
        ├── pbis/                    ← PBIs gerados
        └── crs/                     ← CRs gerados
```

---

## 🎯 Fluxos Rápidos

### Criar Especificação
```
1. /write-spec
2. Escolher formato (US, SFR, PFR, RAF)
3. Fornecer inputs (Issue, Notas, Figma)
4. Revisar output em outputs/specs/
```

### Criar Change Request
```
1. /write-cr
2. Fornecer inputs com alterações
3. Confirmar lista de funcionalidades alteradas
4. Revisar CRs gerados
5. (Opcional) Criar no DevOps
```

### Consultar Informações
```
/show-context     → Ver contextos disponíveis
/show-templates   → Ver formatos de especificação
```

---

## 🔄 Manutenção

| Tarefa | Arquivo(s) a Editar | Frequência |
|--------|---------------------|------------|
| Mudar de projeto | [context_project.md](instructions/context/context_project.md) | Por projeto |
| Adicionar tarefa | `tasks/` + `commands/` + `system_prompt.md` | Conforme necessário |
| Adicionar template | `templates/` + `system_prompt.md` | Conforme necessário |
| Atualizar MCP | [mcp.json](.claude/mcp.json) | Raramente |

---

**Versão**: 1.0.0
**Data**: 2025-01-15
**Status**: ✅ Pronto para uso

**Próximo passo**: Leia [QUICKSTART.md](QUICKSTART.md) e comece a usar! 🚀
