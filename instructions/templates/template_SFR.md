## Requisito de Software

### RQF-CART-001: Adicionar Produto ao Carrinho

**Descrição**

O utilizador deve poder adicionar produtos ao carrinho de compras a partir de diferentes pontos de entrada na aplicação.

**Pré-condições**

1. O utilizador está autenticado ou em sessão anónima.  
2. O produto está disponível (stock \> 0).  
3. O produto está ativo no catálogo.

**Regras de Negócio e Comportamentos**

1. **Pontos de Entrada**  
   1. Página de Detalhe do Produto \[Ver layout em Figma\]  
   2. Listagem de Produtos \[Ver layout em Figma\]  
   3. Quick View Modal \[Ver layout em Figma\]

2. **Validações**  
   1. A quantidade solicitada não pode exceder o stock disponível.  
   2. *Se* quantidade \> stock: exibir mensagem "Apenas X unidades disponíveis".  
   3. Produtos com variantes obrigatórias (tamanho, cor) devem ter variante selecionada antes de adicionar.  
   4. *Se* variante não selecionada: exibir mensagem "Selecione uma opção"  
      .  
3. **Comportamentos**  
   1. **Se o produto já existe no carrinho:**  
      1. Incrementar quantidade (respeitando limite de stock).  
   2. **Se o produto não existe no carrinho:**  
      1. Adicionar nova linha ao carrinho.  
   3. **Após adicionar com sucesso:**  
      1. Exibir *toast* de confirmação (3 segundos).  
      2. Atualizar contador do *mini-cart* no *header*.  
      3. Opcionalmente abrir *drawer* do carrinho.

**Pós-condições**

1. Produto adicionado ao carrinho.  
2. Sessão/cookie atualizado com estado do carrinho.  
3. Evento de analytics disparado (add\_to\_cart).

