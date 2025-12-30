# Configuração dos MCP Servers

Este documento explica como configurar os MCP servers necessários para o agente funcionar corretamente.

## Servidores Configurados

### 1. Azure DevOps (ado)

**Status**: ✅ Já configurado e rodando localmente

**Localização**: `C:\Users\igorcarvalho\Desktop\MCP-Servers-Tests\Azure-DevOps\azure-devops-mcp`

**Uso**:
- Consultar work items (Issues, PBIs, CRs)
- Criar novos work items
- Atualizar work items existentes

**Configuração**: Não requer configuração adicional - já está apontando para o servidor local.

---

### 2. Google Drive (gdrive)

**Status**: ⚠️ Requer configuração de credenciais

**Uso**:
- Consultar RFP do projeto
- Consultar Proposta comercial
- Consultar Especificação Funcional completa
- Consultar Backlog (se armazenado no Drive)

**Passos de Configuração**:

1. **Criar credenciais OAuth 2.0 no Google Cloud Console**:
   - Acesse https://console.cloud.google.com/
   - Crie um novo projeto ou selecione um existente
   - Ative a Google Drive API
   - Vá para "Credenciais" > "Criar Credenciais" > "ID do cliente OAuth"
   - Tipo de aplicação: "Aplicativo para computador"
   - Copie o Client ID e Client Secret gerados

2. **Configurar variáveis de ambiente**:

   Crie um arquivo `.env` na raiz do projeto ou configure as variáveis de ambiente do sistema:

   ```bash
   GDRIVE_CLIENT_ID=seu_client_id_aqui
   GDRIVE_CLIENT_SECRET=seu_client_secret_aqui
   ```

3. **Primeira execução**:
   - Na primeira vez que usar o servidor, será solicitado autenticação no navegador
   - Autorize o acesso ao Google Drive
   - O token será salvo para uso futuro

**Links úteis fornecidos no context_project.md**:
- RFP: https://drive.google.com/drive/u/0/folders/1An523gNY0ZrkY4yCypgLqCvzvpCdMtnq
- Proposta: https://drive.google.com/drive/u/0/folders/1uQn30mgOmLLOd7ZlsjKVpANgTJ2lvzVJ
- Especificação Funcional: https://drive.google.com/drive/u/0/folders/1An523gNY0ZrkY4yCypgLqCvzvpCdMtnq

---

### 3. Figma (figma)

**Status**: ⚠️ Requer configuração de token

**Uso**:
- Consultar designs de funcionalidades
- Visualizar protótipos
- Extrair especificações visuais

**Passos de Configuração**:

1. **Gerar Personal Access Token no Figma**:
   - Acesse https://www.figma.com/developers/api#access-tokens
   - Faça login na sua conta Figma
   - Vá para Settings > Account > Personal Access Tokens
   - Clique em "Create new token"
   - Dê um nome descritivo (ex: "Claude Code Agent")
   - Copie o token gerado (importante: não será mostrado novamente!)

2. **Configurar variável de ambiente**:

   Adicione ao arquivo `.env` ou às variáveis de ambiente do sistema:

   ```bash
   FIGMA_PERSONAL_ACCESS_TOKEN=seu_token_aqui
   ```

---

## Verificar Configuração

Após configurar os MCP servers, você pode verificar se estão funcionando corretamente:

1. **Reinicie o Claude Code** para carregar as novas configurações

2. **Teste cada servidor**:

   ```
   # Testar Azure DevOps
   Liste os work items do projeto SAPO

   # Testar Google Drive
   Acesse o documento RFP no Google Drive

   # Testar Figma
   Mostre o design da funcionalidade X do Figma
   ```

---

## Troubleshooting

### Azure DevOps não responde
- Verifique se o servidor local está rodando
- Confirme o caminho em `.claude/mcp.json`

### Google Drive - Erro de autenticação
- Verifique se as credenciais OAuth estão corretas
- Tente remover e reautorizar
- Confirme que a Google Drive API está ativada no projeto

### Figma - Erro de token inválido
- Verifique se o token foi copiado corretamente (sem espaços)
- Gere um novo token se necessário
- Confirme que o token tem as permissões necessárias

---

## Desabilitar MCP Servers (Opcional)

Se não quiser usar algum MCP server temporariamente, edite `.claude/mcp.json` e altere:

```json
{
  "disabled": false  // Altere para true
}
```

---

## Segurança

⚠️ **IMPORTANTE**:
- Nunca commite o arquivo `.env` com credenciais
- Adicione `.env` ao `.gitignore`
- Mantenha tokens e secrets seguros
- Revogue tokens que não estão mais em uso
