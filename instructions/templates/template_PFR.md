**Funcionalidade**: Adicionar produtos ao carrinho  
O utilizador deve poder adicionar produtos ao carrinho a partir de múltiplos pontos da aplicação.

**Visão Geral**  
O carrinho de compras permite aos utilizadores acumular produtos antes de finalizar uma compra. É acessível através do ícone no *header* (mini-cart) e através de página dedicada.

---

#### Requisito Funcionais

1. **Pontos de Entrada**  
   A ação de adicionar ao carrinho deve estar disponível em:  
   1. Página de Detalhe do Produto (PDP)  
   2. Listagem de Produtos (PLP) \- via *quick add*  
   3. *Quick View* Modal  
   4. *Wishlist* (se implementada)  
   5. **Nota:** Para produtos com variantes (tamanho, cor), a adição a partir da listagem deve abrir seletor de variante ou redirecionar para PDP.

   

2. **Comportamento**  
   1. Ao adicionar um produto ao carrinho:  
      1. Se produto **já existe** no carrinho → incrementar quantidade  
      2. Se produto **não existe** → criar nova entrada  
      3. **Sempre** validar disponibilidade de stock

   2. **Feedback Visual**  
      1. Após adicionar com sucesso:  
      2. *Toast* de confirmação (*auto-dismiss* em 3s)  
      3. Atualização do contador no *header*  
      4. **Opcionalmente:** abertura do *mini-cart drawer*

3. **Disclaimer:** A abertura automática do *drawer* será A/B testada para avaliar impacto na conversão.

4. **Validações**

| Cenário | Comportamento |
| ----- | ----- |
| Stock insuficiente | Mensagem: "Apenas X disponíveis" |
| Produto indisponível | Botão desabilitado |
| Variante não selecionada | Mensagem: "Selecione uma opção" |
| Limite por cliente | Mensagem: "Máximo X por cliente" |

---

