# Especificação Funcional - Inscrição em Feiras

**Feature:** INSCRIÇÃO EM FEIRAS
**Projeto:** APM_Test
**Formato:** User Stories

---

## Visão Geral

A funcionalidade de Inscrição em Feiras e Eventos permite à AP Madeira (APM) gerir a organização de eventos promocionais, facilitando a comunicação com os associados e simplificando o processo de candidatura e validação de participações.

---

## User Stories

---

### US-FEIRA-001: Criar Novo Evento

**Título:** Criar Novo Evento de Feira

* **Como** administrador da APM,
* **Eu quero** criar um novo evento de feira na plataforma,
* **Para que** os associados possam visualizar e candidatar-se ao evento.

**Critérios de Aceitação**

1. **Acesso à Criação de Evento (AC-FEIRA-001.1):** Dado que o administrador está autenticado na área de administração, Quando acede à secção de eventos, Então deve visualizar as opções "Criar Novo Evento" e "Consultar Eventos Criados".

2. **Formulário de Criação com Campos Obrigatórios (AC-FEIRA-001.2):** Dado que o administrador seleciona "Criar Novo Evento", Quando o formulário é apresentado, Então deve conter os seguintes campos obrigatórios: Nome do evento, Datas, Localização, Número de vagas, Tipo de Feira, Valor, Data para o fim de inscrições e Inscrição Externa (Sim/Não).

3. **Inscrição Interna - Opção "Não" (AC-FEIRA-001.3):** Dado que o administrador seleciona "Não" no campo Inscrição Externa, Quando submete o formulário com todos os campos obrigatórios preenchidos, Então o evento deve ser criado com inscrição via formulário interno da plataforma.

4. **Inscrição Externa - Opção "Sim" (AC-FEIRA-001.4):** Dado que o administrador seleciona "Sim" no campo Inscrição Externa, Quando o campo é selecionado, Então deve ser apresentado um campo adicional obrigatório para inserir o link externo de inscrição, e o evento só pode ser criado após o preenchimento deste link.

5. **Notificação Automática Após Criação (AC-FEIRA-001.5):** Dado que o evento foi criado com sucesso, Quando a criação é concluída, Então o sistema deve enviar notificações automáticas a todos os associados informando da disponibilidade do novo evento.

---

### US-FEIRA-002: Consultar Eventos Criados

**Título:** Consultar Lista de Eventos Criados

* **Como** administrador da APM,
* **Eu quero** consultar os eventos já criados,
* **Para que** possa gerir e acompanhar os eventos existentes.

**Critérios de Aceitação**

1. **Visualizar Lista de Eventos (AC-FEIRA-002.1):** Dado que o administrador está autenticado na área de administração, Quando acede à opção "Consultar Eventos Criados", Então deve visualizar uma lista com todos os eventos criados.

2. **Filtrar por Tipo de Inscrição (AC-FEIRA-002.2):** Dado que o administrador está na lista de eventos, Quando aplica filtros, Então deve poder visualizar separadamente os eventos com inscrição externa e os eventos com inscrição interna.

---

### US-FEIRA-003: Visualizar Eventos Disponíveis

**Título:** Visualizar Eventos Disponíveis para Inscrição

* **Como** associado da APM,
* **Eu quero** visualizar a lista de eventos ativos disponíveis para inscrição,
* **Para que** possa conhecer as oportunidades de participação em feiras.

**Critérios de Aceitação**

1. **Lista de Eventos Ativos (AC-FEIRA-003.1):** Dado que o associado está autenticado na sua área, Quando acede à secção de eventos, Então deve visualizar uma lista de eventos ativos abertos para inscrição.

2. **Aceder à Ficha do Evento (AC-FEIRA-003.2):** Dado que o associado visualiza a lista de eventos, Quando seleciona "Saber mais" num evento, Então deve aceder à ficha completa do evento com todas as informações inseridas pela APM (Nome, Datas, Localização, Número de vagas, Tipo de Feira, Valor, Data limite de inscrição).

3. **Botão de Inscrição Interna (AC-FEIRA-003.3):** Dado que o evento tem inscrição interna (Inscrição Externa = Não), Quando o associado visualiza a ficha do evento, Então deve ser apresentado um botão com o texto "Inscrição" que abre o formulário de candidatura na plataforma.

4. **Botão de Inscrição Externa (AC-FEIRA-003.4):** Dado que o evento tem inscrição externa (Inscrição Externa = Sim), Quando o associado visualiza a ficha do evento, Então deve ser apresentado um botão com o texto "Inscrição Externa" que redireciona para o link externo configurado pelo administrador.

---

### US-FEIRA-004: Submeter Candidatura a Evento

**Título:** Submeter Candidatura a Evento com Inscrição Interna

* **Como** associado da APM,
* **Eu quero** submeter a minha candidatura a um evento através do formulário interno,
* **Para que** a minha participação fique registada e possa ser avaliada pela APM.

**Critérios de Aceitação**

1. **Formulário de Candidatura (AC-FEIRA-004.1):** Dado que o associado clica em "Inscrição" num evento com inscrição interna, Quando o formulário é apresentado, Então deve conter os campos: Empresa, Nome do responsável e Email.

2. **Submissão da Candidatura (AC-FEIRA-004.2):** Dado que o associado preencheu o formulário de candidatura, Quando submete o formulário, Então a inscrição deve ficar registada no sistema.

3. **Confirmação de Submissão (AC-FEIRA-004.3):** Dado que a candidatura foi submetida com sucesso, Quando a submissão é concluída, Então o associado deve receber confirmação do registo da sua candidatura.

---

### US-FEIRA-005: Consultar Histórico de Inscrições

**Título:** Consultar Histórico e Estado das Inscrições

* **Como** associado da APM,
* **Eu quero** consultar o histórico das minhas inscrições em eventos,
* **Para que** possa acompanhar o estado de cada candidatura.

**Critérios de Aceitação**

1. **Acesso à Área "Minhas Inscrições" (AC-FEIRA-005.1):** Dado que o associado está autenticado, Quando acede à área "Minhas Inscrições", Então deve visualizar o histórico de todas as inscrições efetuadas em eventos e feiras organizados pela APM.

2. **Visualizar Estado da Inscrição (AC-FEIRA-005.2):** Dado que o associado está na área "Minhas Inscrições", Quando consulta uma inscrição, Então deve visualizar o estado atual da mesma (pendente, aprovada, rejeitada).

3. **Âmbito das Inscrições Apresentadas (AC-FEIRA-005.3):** Dado que o associado consulta "Minhas Inscrições", Quando a lista é apresentada, Então deve conter apenas as inscrições em eventos organizados pela APM. As inscrições em eventos do Turismo de Portugal devem ser consultadas diretamente no respetivo site.

---

### US-FEIRA-006: Validar Inscrições de Associados

**Título:** Validar Candidaturas aos Eventos

* **Como** administrador da APM,
* **Eu quero** validar as inscrições recebidas para cada evento,
* **Para que** possa aprovar a participação dos associados consoante as vagas disponíveis.

**Critérios de Aceitação**

1. **Consultar Inscrições por Evento (AC-FEIRA-006.1):** Dado que o administrador acede a um evento criado, Quando seleciona o evento, Então deve poder consultar todas as inscrições recebidas para esse evento.

2. **Visualização em Lista (AC-FEIRA-006.2):** Dado que o administrador consulta as inscrições de um evento, Quando a informação é apresentada, Então as inscrições devem ser exibidas em formato de lista.

3. **Validar Participação (AC-FEIRA-006.3):** Dado que o administrador visualiza a lista de inscrições, Quando seleciona uma inscrição, Então deve poder validar (aprovar ou rejeitar) a participação do associado, respeitando o número de vagas abertas para o evento.

4. **Exportar Dados das Inscrições (AC-FEIRA-006.4):** Dado que o administrador está na lista de inscrições de um evento, Quando seleciona a opção "Ver dados", Então deve poder exportar todas as inscrições para um ficheiro Sheets, Excel ou formato equivalente.

5. **Notificação ao Associado (AC-FEIRA-006.5):** Dado que o administrador validou uma candidatura (aprovação ou rejeição), Quando a validação é confirmada, Então o sistema deve enviar uma notificação automática ao associado com o resultado da sua inscrição.

---

## Resumo das User Stories

| ID | Título | Ator |
|----|--------|------|
| US-FEIRA-001 | Criar Novo Evento | Administrador |
| US-FEIRA-002 | Consultar Eventos Criados | Administrador |
| US-FEIRA-003 | Visualizar Eventos Disponíveis | Associado |
| US-FEIRA-004 | Submeter Candidatura a Evento | Associado |
| US-FEIRA-005 | Consultar Histórico de Inscrições | Associado |
| US-FEIRA-006 | Validar Inscrições de Associados | Administrador |

---

*Especificação gerada com base no documento "APM - FUNCIONALIDADE INSCRIÇÃO EM FEIRAS"*
