### Requisitos funcionais

| ID | Requisito | Verificação |
| --- | --- | --- |
| RF01 | Cadastrar mesas com número e capacidade. | Mesa aparece na listagem. |
| RF02 | Cadastrar itens do cardápio com nome, preço e categoria. | Item disponível em novos pedidos. |
| RF03 | Cadastrar clientes (nome, CPF, telefone, código). | Cliente armazenado no restaurante. |
| RF04 | Cadastrar funcionários (nome, CPF, telefone, cargo, salário). | Funcionário armazenado. |
| RF05 | Listar mesas com status livre/ocupada. | Status correto de cada mesa. |
| RF06 | Abrir pedido associado a uma mesa livre. | Pedido criado e mesa ocupada. |
| RF07 | Lançar itens do cardápio em um pedido. | Itens adicionados ao pedido. |
| RF08 | Calcular o total do pedido. | Total = soma dos preços. |
| RF09 | Avançar status: Pendente, Em Preparo, Pronto, Entregue. | Cada avanço muda para o estágio seguinte. |
| RF10 | Escolher forma de pagamento (cartão ou dinheiro/Pix). | Duas opções no fechamento. |
| RF11 | Calcular valor final com taxa ou desconto. | Cartão: total × 1,02. Dinheiro/Pix: total × 0,95. |
| RF12 | Liberar a mesa ao fechar a conta. | Mesa volta a livre. |
| RF13 | Exibir visão geral (mesas, ocupação, total de pedidos). | Três dados exibidos. |

### Requisitos não funcionais

| ID | Categoria | Requisito |
| --- | --- | --- |
| RNF01 | Desempenho | Operações respondem em até 1 s com até 500 pedidos em memória. |
| RNF02 | Usabilidade | Menu numerado e mensagens de erro claras. |
| RNF03 | Segurança | Dados pessoais encapsulados, acesso somente leitura (`property`). |
| RNF04 | Manutenibilidade | Pacotes `models`, `core`, `patterns`; State e Strategy permitem novos status e pagamentos sem alterar `Pedido` e `Pagamento`. |
| RNF05 | Portabilidade | Python 3.8+ sem dependências externas. |
| RNF06 | Confiabilidade | Entradas inválidas não encerram o programa. |

### Regras de negócio

| ID | Regra |
| --- | --- |
| RN01 | Uma mesa tem no máximo um pedido ativo; mesa ocupada não aceita novo pedido. |
| RN02 | Abrir pedido ocupa a mesa; fechar a conta a libera. |
| RN03 | Todo pedido nasce Pendente e avança só na ordem Pendente, Em Preparo, Pronto, Entregue. |
| RN04 | Cartão: +2% sobre o total. Dinheiro/Pix: −5%. |
| RN05 | A conta só é encerrada com o pedido Entregue. |
