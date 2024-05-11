Jaqueline Botaro Honorio acho que é bom a gente repassar esse lista e pensar melhor sobre ela, porque só é um monte de palavras que foram selecionadas ao acaso.

Vamos ver, riscaria exatamente desse tal "pacote básico":

1 - Servidor on premise: O que?? Grande parte das aplicações vivem na nuvem hoje em dia e só tem bare metal e on premise em casos muito específicos, quando não por inventação de moda. Servidor on premise não te dá velocidade de entrega, CDN fácil, pre configuração fácil. fora que a bronca é toda tua se der problema. 
2 - K8s, arquitetura de microsserviços, arquitetura async, gerenciador de filas: Risca esses três, porque muito provavelmente é totalmente desnecessário pra maioria das equipes. Substitua por monólitos. Acredite, microsservices não traz vantagem de segurança, velocidade e nem nada. É muito mais uma decisão de equipe/cultura do que técnica.
3 - Load Balancer, Gateway, Servidor de aplicação: Encheção de linguiça, porque tudo pode ser facilmente substituído por nginx ou por web servers, além do que o termo "Gateway" é ambíguo. Pode se referir tanto a um Gateway Interface de redes quanto a um API Gateway. Só demonstra a aleatoriedade do post.
4 - Back for front: decisão de cultura. Nada mais do que um middleware para prevenir overfetching, quando há prejuízos visíveis. Pode riscar a vontade.
5 - Micro frontends: esse é tão risivel que não me dou o trabalho nem de comentar.
6 - Jenkins: não existe somente Jenkins para automação de pipelines no mundo né. Fique a vontade pra escolher o que quiser. Risca.
7 - Smoke tests e carga: também riscaria. O pacote integração + unitário (com ressalvas) normalmente já cobre os casos necessários da maioria das aplicações. Teste de carga quer dizer, vai trabalhar com carga? Precisa de proteção contra negação de serviço? Melhor aplicado estudando redes e outras coisas de escalabilidade, mas estamos falando de pacote básico né?
8 - Ferramentas de monitoramento e observabilidade: Esqueceram os logs né? Só saber ler. No máximo um Sentry e básico ainda.
9 - Estrutura de dados e complexidade ciclomatica: por que separar em dois itens uma coisa que poderia ser só um (que é o básico de computação?)
10 - Clean Arch: pessimo, riscaria, porque quase nenhuma aplicação precisa disso, e grande parte das que afirmadamente precisam executam essa arquitetura de maneira péssima.
