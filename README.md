1. INTRODUÇÃO 
O presente relatório descreve o desenvolvimento de um protótipo de sistema de busca e 
gerenciamento de inventário para a empresa MegaStore. O objetivo principal foi solucionar 
o problema de lentidão na indexação de produtos em larga escala, utilizando estruturas de 
dados avançadas que garantem performance constante, independentemente do volume de 
dados. 
2. ARQUITETURA E ESTRUTURAS DE DADOS 
Para atender aos requisitos de escalabilidade e segurança de memória, foram escolhidas as 
seguintes implementações: 
● Tabela Hash (std::collections::HashMap): Utilizada como o "índice remissivo" 
principal. A escolha do HashMap permite que a busca por nome de produto ocorra 
em tempo constante, ou seja, Complexidade $O(1)$. Isso resolve o gargalo de 
performance em catálogos com milhões de itens. 
● Grafos (petgraph::UnGraph): Os produtos são armazenados como nós em um 
grafo não-direcionado. Essa estrutura foi implementada para permitir futuras 
expansões do sistema, como algoritmos de recomendação baseados em relações 
entre categorias ou produtos complementares. 
● UUID (Universally Unique Identifier): Em vez de IDs sequenciais simples, utilizei a 
biblioteca uuid para gerar identificadores de 128 bits. Isso garante que, em um 
cenário de Big Data, não ocorram colisões de IDs entre diferentes bancos de dados. 
3. FUNCIONALIDADES DO SISTEMA 
O software foi desenvolvido com uma interface de linha de comando (CLI) interativa, 
oferecendo as seguintes opções ao usuário: 
1. Cadastro Dinâmico: Permite a inserção de novos produtos em tempo de execução, 
alimentando simultaneamente o Grafo e a Tabela Hash. 
2. Busca Otimizada: Localiza qualquer produto instantaneamente através da chave de 
busca (nome do produto), com tratamento de case-insensitivity (ignora 
maiúsculas/minúsculas). 
3. Listagem de Inventário: Exibe todos os itens cadastrados em um formato tabular 
organizado, facilitando a auditoria do catálogo. 
5. CONCLUSÃO 
O protótipo demonstrou ser altamente eficaz. Nos testes realizados, a busca por produtos 
manteve-se instantânea mesmo após o cadastro de múltiplos itens. A combinação de 
Grafos para representação estrutural e Tabela Hash para acesso rápido provou ser a 
arquitetura ideal para os desafios de escalabilidade da MegaStore. 
6. PASSO A PASSO 
1. Abrir o Terminal 
No VS Code, use o atalho Ctrl + ' (ou vá em Terminal > New Terminal no menu 
superior). Certifique-se de que o caminho que aparece no terminal termina na pasta do seu 
projeto (Projeto Mercado). 
2. Rodar o Programa (Modo Interativo) 
Digite o comando abaixo e aperte Enter: 
cargo run 
● O que acontece: O Rust vai compilar seu código e abrir o menu com as opções 
(Cadastrar, Buscar, Listar). 
● Dica: Use a opção 3 logo de cara para ver os produtos que já deixamos 
pré-cadastrados. 
3. Rodar os Testes (Validação Técnica) 
Para garantir que a lógica de busca está 100% correta antes de entregar, digite: 
cargo test 
O que observar: O terminal deve exibir a mensagem test result: ok. 1 passed; 0 
failed. Isso é a prova de que o sistema é confiável. 
7. PRINT DOS TESTES 
Lista Completa incluída no código 
Pesquisa Filtrada por nome 
