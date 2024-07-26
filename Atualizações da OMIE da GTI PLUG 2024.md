# O que já fizemos até o momento

1. Além de integrarmos o código EAN do produto, integramos também as informações do código ANVISA para produtos onde se aplica essa informação (medicamentos, equipamentos médicos, etc.);
2. Para Remessas de Produto que incluem a informação do Local de Estoque em cada item da Remessa do Produto, integramos como uma transferência entre armazéns do mesmo cliente;
3. Integração de Ordens de Produção: clientes que trabalham com ordem de produção agora podem contar com essa integração para imputar lançamentos sobre seu estoque que representam a transformação dos seus materiais através da produção;

# O que ainda iremos implementar

1. Sincronização do estoque: O cliente poderá sincronizar a informação do estoque existente no GTI PLUG com a informação do estoque da Omie, através de ajuste de inventário, solicitado pelo cliente
2. Faturamento de pedidos na Omie: Quando o pedido de venda é criado, o mesmo não possui nota fiscal, sendo que essa nota fiscal é gerada apenas quando o pedido de venda é faturado. Iremos alimentar a informação da Expedição com o número da nota fiscal quando o pedido de venda for faturado.
3. Iremos habilitar a integração de produtos do tipo KIT na Omie para GTI PLUG na mesma estrutura
4. Suporte ao evento de RecebimentoProduto.Revertido, através da geração de um novo recebimento no GTI PLUG