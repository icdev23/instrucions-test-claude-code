## User Story

### **Título:** Adicionar Produtos ao Carrinho de Compras

* **Como** utilizador (autenticado ou anónimo),  
* **Eu quero** adicionar um ou mais produtos ao meu carrinho de compras,  
* **Para que** eu possa finalizar a compra dos produtos selecionados na aplicação.

**Critérios de Aceitação**

1. **Adicionar Produto Novo ao Carrinho (AC-CART-1.1):** Dado que o produto está ativo e com stock disponível, e o utilizador está em sessão (autenticada ou anónima), Quando o utilizador adiciona o produto ao carrinho (a partir da Página de Detalhe, Listagem ou Quick View Modal), Então o produto deve ser adicionado como uma nova linha no carrinho e a sessão/cookie deve ser atualizada com o estado do carrinho.  
2. **Incrementar Quantidade de Produto Existente (AC-CART-1.2):** Dado que o produto já existe no carrinho e o stock disponível permite o incremento, Quando o utilizador adiciona o mesmo produto ao carrinho novamente, Então a quantidade na linha existente do carrinho deve ser incrementada (e não deve ser criada uma nova linha).  
3. **Validação de Stock (AC-CART-1.3):** Dado que o produto tem stock disponível (e.g., X unidades), Quando o utilizador tenta adicionar uma quantidade superior a X unidades, Então o produto não deve ser adicionado ou a quantidade não deve ser incrementada, e deve ser exibida a mensagem de erro: *"Apenas X unidades disponíveis"*.  
4. **Validação de Variante Obrigatória (AC-CART-1.4):** Dado que o produto possui variantes obrigatórias (ex: tamanho, cor), Quando o utilizador tenta adicionar o produto sem selecionar uma variante, Então o produto não deve ser adicionado ao carrinho, e deve ser exibida a mensagem de erro: *"Selecione uma opção"*.  
5. **Feedback e Atualização do Ecrã (Sucesso) (AC-CART-1.5):** Dado que o produto foi adicionado com sucesso ao carrinho, Quando a ação de adicionar é concluída, Então deve ser exibido um *toast* de confirmação por 3 segundos, o contador do *mini-cart* no cabeçalho deve ser atualizado com a nova contagem de itens, e o evento de analytics add\_to\_cart deve ser disparado. Opcionalmente, o *drawer* do carrinho pode ser aberto.  
6. **Produto Inativo ou Sem Stock (AC-CART-1.6):** Dado que o produto está inativo no catálogo ou com stock igual a zero, Quando o utilizador tenta adicionar o produto, Então o produto não deve ser adicionado, e o ponto de entrada (botão "Adicionar ao Carrinho") deve estar indisponível ou exibir uma mensagem de estado apropriada.