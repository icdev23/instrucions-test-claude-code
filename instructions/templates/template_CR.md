# Change Requests

---

### OVERVIEW

Um Change Request é um artefato que especifica uma alteração de requisito, regra de negócio ou comportamento de uma ou mais partes da aplicação/produto.  
---

### TEMPLATE

**Título**  
Breve descrição do CR em uma frase

**Contexto**  
Explicação do contexto. Informação essencial para o entendimento do comportamento atual, breve explicação da solicitação ou origem/motivo da alteração. 

**Comportamento Actual**  
Descrição do comportamento, requisitos ou regras atuais.

**Novo Comportamento Proposto**  
Especificação do novo comportamento, requisitos ou regras.

**Escopo**  
Especificação de em quais áreas da aplicação ou funcionalidades a alteração deve ser aplicada. Este bloco é aplicável apenas quando o escopo da alteração não está implícito do CR.   
---

### SAMPLE

**CHANGE REQUEST 34991**  
Bloco Exclusivos do Parceiro | Fallback para artigos sem imagem.

**Contexto**  
O bloco exclusivo do parceiro consome diretamente do endpoint do SAPO o conteúdo (artigos) e os elementos (imagem e título) necessários para montar o card de pré-visualização do artigo. No entanto, alguns artigos estão a ser recebidos sem imagem.

**Comportamento Atual**  
O cartão de pré-visualização do artigo exibe a imagem e o título diretamente dos dados recebidos do endpoint, sem fallback em caso de falha no recebimento.

**Novo Comportamento**  
O card do preview do artigo (e a correta exibição dos componentes previstos em design), deve ser composto pelos dados recebidos na resposta do endpoint:

1. **Título**  
   1. **Descrição**: Título do artigo exibido no card.  
   2. **Atributo**: Corresponde ao atributo title da resposta do endpoint.  
   3. **Campo obrigatório**: Caso não seja recebido, o artigo não deve ser exibido no bloco.

2. **Imagem**  
   1. **Descrição**: Imagem do artigo exibido no card.  
   2. **Atributo**: Corresponde ao atributo image da resposta do endpoint.  
   3. **Campo opcional \[fallback 1\]**: Caso não seja recebido, a imagem de logo do parceiro (fonte do artigo \- partner) deve ser utilizada como imagem do card.   
   4. **\[Fallback 2\]**: Se não for possível obter a imagem de logo do parceiro, então deve ser utilizada uma imagem placeholder (a definir em Design) como imagem do card.

3. **Link**   
   1. **Descrição**: Link para o artigo no site do parceiro   
   2. **Atributo**: Corresponde ao atributo url da resposta do endpoint  
   3. **Campo obrigatório**:Caso não seja recebido, o artigo não deve ser exibido no bloco.

---

### SAMPLE

**CHANGE REQUEST 34536**  
Controlar carregamento do conteúdo das áreas após navegação entre tabs.

**Contexto**  
Ao navegar entre as diferentes áreas da aplicação, em particular ao sair de uma área (Jornais, Feed ou Destaques) e regressar, o conteúdo da área não deve ser automaticamente recarregado. A aplicação deverá manter em cache o conteúdo já renderizado, carregando novos conteúdos apenas após a sua expiração.

**Comportamento Actual**  
Atualmente, quando o utilizador sai de uma área e navega para outra área (tabs), ao retornar, a aplicação atualiza o ecrã automaticamente, carregando novos conteúdos.

**Novo Comportamento**  
Ao sair de uma área e navegar para outra área, a aplicação deverá manter em cache o conteúdo já renderizado bem como a posição de scroll actual. Ao retornar, se a cache for ainda válida, o utilizador deverá voltar ao ponto exacto onde saiu. Caso a cache já tenha expirado, então o ecrã deverá ser actualizado (refresh). O refresh deve ser realizado somente se a aplicação tiver conexão com internet. Em modo offline, tanto os dados em cache quanto os conteúdos já renderizados devem ser mantidos. 

**Escopo**  
Este comportamento deve ser aplicado para as 3 áreas (tabs) de conteúdo da app: **Jornais**, **Feed** e **Destaques**. Deve ser respeitado o tempo de expiração de cache definido para cada área. 

---

