# Guia de Início Rápido

## 🎯 Primeiros Passos (5 minutos)

### 1. Configure o Contexto do Projeto

Edite o arquivo que contém todas as informações específicas do seu projeto:

```bash
instructions/context/context_project.md
```

Atualize:
- Nome do projeto no Azure DevOps
- Links do Google Drive (RFP, Proposta, Specs)
- Links do Figma
- Qualquer contexto específico do produto

### 2. Configure os MCP Servers (Opcional mas Recomendado)

#### Azure DevOps
✅ **Já configurado!** Aponta para: `C:\Users\igorcarvalho\Desktop\MCP-Servers-Tests\Azure-DevOps\azure-devops-mcp`

#### Google Drive
Necessário para acessar RFP, Proposta e Specs completas.

1. Obtenha credenciais OAuth 2.0 (instruções em `.claude/MCP_SETUP.md`)
2. Crie arquivo `.env` na raiz:
   ```
   GDRIVE_CLIENT_ID=seu_client_id
   GDRIVE_CLIENT_SECRET=seu_client_secret
   ```

#### Figma
Necessário para consultar designs.

1. Gere token em https://www.figma.com/developers/api#access-tokens
2. Adicione ao `.env`:
   ```
   FIGMA_PERSONAL_ACCESS_TOKEN=seu_token
   ```

### 3. Reinicie o Claude Code

Para carregar as configurações:
```bash
# Feche e reabra o Claude Code
```

---

## 🚀 Usando o Agente

### Método 1: Slash Commands (Recomendado)

```
/write-spec
```
→ Agente pergunta sobre formato, inputs e cria a especificação

```
/write-cr
```
→ Agente lista funcionalidades alteradas, confirma e cria CRs

```
/show-templates
```
→ Lista todos os formatos de especificação disponíveis

### Método 2: Conversa Natural

```
"Preciso criar uma User Story para a funcionalidade de checkout"
```

```
"Atualiza a especificação do carrinho com os novos requisitos que recebi por email"
```

```
"Cria um Change Request para a alteração do comportamento de cache"
```

---

## 📋 Exemplo Completo: Criar Especificação

### Passo 1: Invoque o comando
```
/write-spec
```

### Passo 2: Agente Pergunta
- "Qual formato de especificação deseja? (US, SFR, PFR, RAF)"
- "Tem alguma estrutura base para seguir?"
- "Pode fornecer os inputs (issue, notas de reunião, figma)?"

### Passo 3: Você Fornece
```
Formato: User Stories
Inputs:
- Issue #12345 do DevOps
- Notas da reunião (colar aqui ou fornecer link)
- Link do Figma: https://figma.com/...
```

### Passo 4: Agente Executa
1. Consulta issue no Azure DevOps (via MCP)
2. Lê notas fornecidas
3. Consulta Figma (via MCP)
4. Lê contexto do projeto
5. Gera especificação conforme template
6. Salva em `outputs/specs/`
7. Apresenta como artefato

### Passo 5: Próximos Passos
Agente pergunta:
- "Deseja que eu crie um PBI no DevOps com esta spec?"
- "Precisa de algum ajuste?"

---

## 🎨 Formatos Disponíveis

| Formato | Quando Usar | Exemplo |
|---------|-------------|---------|
| **User Stories (US)** | Desenvolvimento ágil, histórias de utilizador | `template_US.md` |
| **SFR** | Requisitos de software detalhados com regras | `template_SFR.md` |
| **PFR** | Documentação de produto, visão geral | `template_PFR.md` |
| **RAF** | [A preencher quando completar template] | `template_RAF.md` |
| **CR** | Alterações em funcionalidades existentes | `template_CR.md` |

---

## 💡 Dicas Úteis

### Forneça Contexto Rico
Quanto mais contexto você fornecer, melhor a especificação:
- ✅ Issue ID do DevOps
- ✅ Notas de reunião completas
- ✅ Links do Figma
- ✅ Especificação atual (para updates)
- ✅ Prints ou documentos anexos

### Use Comandos Helper
```
/show-context     # Ver que tipos de contexto estão disponíveis
/show-templates   # Ver todos os formatos de spec
```

### Estrutura Base (Opcional)
Se tem uma estrutura específica que prefere:
```
"Use esta estrutura base:
1. Overview
2. Functional Requirements
   2.1 Entry Points
   2.2 Business Rules
3. Validations"
```

### Confirme Antes de Criar no DevOps
O agente sempre pergunta antes de criar work items externos.

---

## 🔍 Verificar se Está Funcionando

### Teste 1: System Prompt Carregado
Inicie conversa e veja se o agente se identifica como "Analista de Requisitos / Technical Writer"

### Teste 2: Slash Commands
Digite `/` e veja se aparecem os comandos customizados

### Teste 3: MCP Azure DevOps
```
"Lista os work items recentes do projeto SAPO"
```
Deve consultar o Azure DevOps via MCP

### Teste 4: Criar Especificação Simples
```
/write-spec

Formato: User Stories
Input direto no prompt:
"Funcionalidade: Utilizador pode adicionar produto ao carrinho.
Requisito: Validar stock antes de adicionar.
Requisito: Mostrar mensagem de confirmação."
```

---

## 📁 Onde Encontrar os Outputs

Todas as especificações geradas são salvas em:

```
outputs/
├── specs/     # Especificações funcionais
├── pbis/      # Product Backlog Items
└── crs/       # Change Requests
```

Nomenclatura sugerida:
- `2025-01-15_carrinho-compras_US.md`
- `PBI-12345_checkout-flow.md`
- `CR-34991_cache-behavior.md`

---

## ❓ Problemas Comuns

### "Não encontro o arquivo de instrução"
✅ Verifique se está em `instructions/tasks/task_*.md`

### "MCP não responde"
✅ Veja troubleshooting em `.claude/MCP_SETUP.md`

### "Agente não usa o template correto"
✅ Confirme que especificou o formato claramente

### "Quer mudar de projeto"
✅ Edite apenas `instructions/context/context_project.md`

---

## 📚 Próximos Passos

1. ✅ Complete este guia
2. 📝 Preencha os templates faltantes (task_write_pbi.md, etc.)
3. 🔧 Configure MCP servers restantes
4. 🎯 Teste criando sua primeira especificação
5. 🚀 Integre no seu workflow de desenvolvimento

---

**Dúvidas?** Consulte `README.md` para documentação completa ou `.claude/MCP_SETUP.md` para configuração de integrações.
