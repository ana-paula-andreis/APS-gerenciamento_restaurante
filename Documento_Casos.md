Documentação dos casos de uso

**UC01 — Cadastrar Mesa** (RF01) · Ator: Gerente
- Pré-condição: sistema iniciado.
- Fluxo principal: 1) escolhe "Cadastrar Mesa"; 2) informa número e capacidade; 3) sistema cria a mesa livre; 4) confirma.
- Alternativo: 2a) valor não numérico → erro e nova solicitação.
- Pós-condição: mesa registrada e livre.

**UC02 — Cadastrar Item do Cardápio** (RF02) · Ator: Gerente
- Pré-condição: sistema iniciado.
- Fluxo principal: 1) escolhe "Cadastrar Item"; 2) informa nome, preço e categoria; 3) sistema adiciona ao cardápio; 4) confirma.
- Alternativo: 2a) preço inválido → erro e nova solicitação.
- Pós-condição: item disponível para pedidos.

**UC03 — Abrir Pedido** (RF05, RF06, RN01, RN02) · Ator: Atendente
- Pré-condição: existe ao menos uma mesa.
- Fluxo principal: 1) escolhe "Abrir Pedido"; 2) sistema lista mesas e status; 3) escolhe mesa livre e define o número do pedido; 4) executa UC04; 5) sistema registra o pedido Pendente e ocupa a mesa.
- Alternativos: 1a) sem mesas → informa e retorna; 3a) mesa inexistente → erro; 3b) mesa ocupada → erro.
- Pós-condição: pedido aberto (Pendente), mesa ocupada.

**UC04 — Lançar Itens** (RF07, RF08; incluído em UC03) · Ator: Atendente
- Pré-condição: pedido em abertura; cardápio com itens.
- Fluxo principal: 1) sistema exibe o cardápio indexado; 2) atendente informa índices; 3) sistema adiciona itens e soma o total; 4) exibe o acumulado.
- Alternativo: 3a) índice inválido → aviso, item ignorado.
- Pós-condição: itens e total registrados.

**UC05 — Avançar Status do Pedido** (RF09, RN03) · Ator: Atendente
- Pré-condição: existe ao menos um pedido.
- Fluxo principal: 1) escolhe "Avançar Status"; 2) sistema lista pedidos e status; 3) informa o número; 4) sistema delega a transição ao estado atual; 5) exibe o novo status.
- Alternativos: 3a) pedido não encontrado → erro; 4a) pedido já Entregue → status permanece.
- Pós-condição: pedido no estágio seguinte.

**UC06 — Fechar Conta e Pagar** (RF10, RF12, RN02, RN05) · Atores: Atendente e Cliente
- Pré-condição: pedido ativo com mesa ocupada.
- Fluxo principal: 1) escolhe "Fechar Conta"; 2) sistema lista pedidos ativos com subtotal; 3) seleciona o pedido; 4) cliente escolhe a forma de pagamento; 5) executa UC07; 6) leva o pedido a Entregue, se necessário; 7) libera a mesa e confirma.
- Alternativos: 2a) sem pedidos ativos → informa e retorna; 4a) forma inválida → operação cancelada.
- Pós-condição: pagamento Pago, mesa livre.

**UC07 — Aplicar Taxa ou Desconto** (RF11, RN04; incluído em UC06) · Ator: Sistema
- Pré-condição: forma de pagamento escolhida.
- Fluxo principal: 1) seleciona a estratégia; 2) calcula o valor final; 3) exibe o valor.
- Pós-condição: valor final calculado, pagamento Pago.

**UC08 — Consultar Visão Geral** (RF13) · Atores: Gerente e Atendente
- Pré-condição: sistema iniciado.
- Fluxo principal: 1) escolhe "Visão Geral"; 2) sistema exibe mesas, ocupação e total de pedidos.
- Alternativo: 2a) sem mesas → contagem zero.
- Pós-condição: nenhuma alteração de dados.
