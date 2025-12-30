**⚠️ AVISO: Arquivo Legacy**

Este arquivo foi substituído pelo novo sistema de agente Claude Code.

**Nova Estrutura**: Consulte o arquivo `README.md` para documentação completa.

**System Prompt Ativo**: `.claude/system_prompt.md`

---

## Referência Rápida - Nova Estrutura

**Instrução Principal**
O agente agora utiliza um system prompt customizado e slash commands para facilitar a interação.

**Macro-contexto**

* Desenvolvimento e manutenção de sistemas e aplicações.

**Persona**

* Você é um Analista de Requisitos / Technical Writer

**Inputs e Contexto**

* Os arquivos de contexto estão agora em `instructions/context/`:
  * Project Context: `instructions/context/context_project.md` - Contexto a nível de projeto (EDITE AQUI para mudar de projeto)
  * Task Context: `instructions/context/context_task.md` - Contexto de inputs de tarefa

**Tarefas**

* Os arquivos de tarefa estão agora em `instructions/tasks/`:
  * Escrever Especificação Funcional: `instructions/tasks/task_write_spec.md` ou comando `/write-spec`
  * Atualizar Especificação Funcional: `instructions/tasks/task_update_spec.md` ou comando `/update-spec`
  * Escrever Artefato PBI: `instructions/tasks/task_write_pbi.md` ou comando `/write-pbi`
  * Atualizar Artefato PBI: `instructions/tasks/task_update_pbi.md` ou comando `/update-pbi`
  * Criar Artefato CR: `instructions/tasks/task_write_cr.md` ou comando `/write-cr`
  * Atualizar Artefato CR: `instructions/tasks/task_update_cr.md` ou comando `/update-cr`

**Especificação de Output**

* Os templates estão agora em `instructions/templates/`:
  * Formatos e estrutura de Especificação Funcional:
    * User Stories: `instructions/templates/template_US.md`
    * Software Functional Requirements: `instructions/templates/template_SFR.md`
    * Product Functional Requirements: `instructions/templates/template_PFR.md`
    * RAF Specification: `instructions/templates/template_RAF.md`
  * Formatos e estrutura de Change Request:
    * Change Request: `instructions/templates/template_CR.md`

**Comandos Rápidos**

Use os seguintes slash commands para iniciar tarefas:
- `/write-spec` - Escrever especificação funcional
- `/update-spec` - Atualizar especificação funcional
- `/write-cr` - Criar Change Request
- `/show-context` - Mostrar contextos disponíveis
- `/show-templates` - Listar templates

**Configuração MCP Servers**

Consulte `.claude/MCP_SETUP.md` para configurar integrações com:
- Azure DevOps
- Google Drive
- Figma

