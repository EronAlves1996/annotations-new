- [ ] Fazer o hoisting do commandParam para evitar passar objetos para baixo
- [x] Testes indo
	- [x] Tentar integrar uma remessa sem cadastrar associações de local de estoque
		- Resultado: não integra com mensagem informativa
	- [x] Integrar uma remessa com local de estoque de entrada
		-  Resultado: sucesso com expedição de transferência
	- [x] sem local de estoque de entrada
		- Resultado: sucesso, cria expedição sem transferência
	- [x] Com algum produto sem local de estoque de entrada
		- Resultado: sucesso, porém ignora o produto sem local de estoque de entrada. É inclusa mensagem informativa em orientações
	- [x] Alterar uma remessa com local de estoque de entrada
		- AVISO: pode ser que no momento da alteração haja remoção de um dos produtos, onde uma das expedições criadas deixem de ser atualizadas. Neste caso, caso haja um chamado no suporte quanto a Remessa de produto que esteja ligada a expedição de transferência que não está sendo concluída, convém analisar se há uma expedição que 'ficou para trás', excluí-la e enviar o webhook novamente 
	- [x] Tentar criar remessa com destinatário que não tem armazém
		- Resultado: não integra com mensagem informativa
	- [x] Tentar integrar uma remessa onde um dos locais de estoque de entrada não esteja associado
		- Resultado: não integra com mensagem informativa
	- [x] Integra uma Remessa, cria duas transferências, modifica essa remessa para ser uma única transferência
		- Resultado: A transferência excedente será excluída
	- [x] Integra uma Remessa, cria uma expedição, modifica para ser transferência
		- Resultado: a expedição normal tem que ser excluida e sobra só a de transferência
	- [x] Integra uma Remessa, cria duas transferências, modifica remessa para ser expedição
		- Resultado: As expedições de transferência serão excluídas e sobrará apenas a expedição normal
- [x] Testes voltando
	- [x] Criar remessa para 2 expedições transferencia, finaliza apenas uma
		- Irá alterar os dados de rastreabilidade de apenas um produto, visto que, em remessas, não é possível remover produto via API
	- [x] Criar remessa para 2 expedições transferencia, finaliza as duas
		- Não poderá finalizar a Remessa, pois o Local de Estoque deverá ser de terceiros
- [ ] Rever HTTPClient para passar um `map` de parametros ao inves de hardcodear o token