Índice agrupado e índice não agrupado, também conhecidos como Clustered Index e Non-Clustered Index.

Nós vamos perceber que os nossos índices em bancos de dados podem estar classificados, primeiro, em índice agrupado ou clustered index, que tem as seguintes características.

Reordena a maneira como os registros são armazenados fisicamente. Então, isso aqui é bem interessante porque a lógica que é colocada na criação do índice, por exemplo, ordenar com base em um sequencial inteiro que vai do menor para o maior. Então, esta lógica de indexação fará com que o posicionamento de cada um dos registros fisicamente no dispositivo siga a mesma ordem.

Isso aqui é bem interessante. O clustered index, ou índice agrupado, reordena a maneira como os registros estão armazenados fisicamente. Seja um disco mecânico, que vai ter aquele movimento de rotação do disco, ou um disco sólido, que vai ter uma operação elétrica para fazer a identificação do endereço onde está posicionada aquela informação.

O índice agrupado não armazena registros aleatoriamente ou na ordem em que foram inseridas, ele está sempre reordenando conforme a lógica do índice. 

Então, isso é justamente uma reorganização para estarem alinhados com essa ordem do índice e daí o termo agrupado. Os atributos que nós vamos utilizar especificamente para essa organização, para determinar essa ordenação, são chaves clusterizadas.

Vamos a um exemplo. Aqui o arranjo dos dados determina a ordem física desses dados em disco e aqui a gente pode entender uma coisa que eu chamei aqui de lógica da lista telefônica.

Aqui nós vamos ver que temos uma classificação por sobrenome e depois nome, e os números de telefone e o respectivo endereço são armazenados com o índice ordenado. Se você é uma pessoa que nasceu, que chegou no mundo, quando não existiam mais listas telefônicas em papel, impressas, que parecem um livro, listas telefônicas em papel, impressas, que parecem um livro, é dessa lista telefônica que eu estou me referindo.

A experiência de você ter as pessoas todas registradas por sobrenome e depois o nome e após esta chave de indexação a gente encontra o número de telefone e o endereço.

Aqui nós vamos ver que nós temos na nossa árvore aqui, com o nosso índice agrupado, nós temos as chaves. Então, chave 4791 como a chave pai, à esquerda nós vamos encontrar chaves menores, 2738 é o ponto de divisão dessa chave, à esquerda do 2738 temos a chave 1582, e chegamos finalmente com o registro do e-mail do Alex. A mesma coisa com o Bob. Então, essa aqui é a regra de divisão, de segmentação, e consequentemente a maneira como esses registros que nós temos aqui são gravados fisicamente no disco vai seguir exatamente essa lógica.

Coisas interessantes para comentar do índice agrupado. Os dados físicos podem ser classificados em apenas uma ordem. Então, nós vamos definir que é uma ordem, por exemplo, número inteiro sequencial do menor para o maior.

E depois temos que ficar atentos que mudar, alterar, adicionar um índice clusterizado é uma operação demorada, porque isso implica em reorganizar fisicamente tudo aquilo que foi escrito.

Precisamos também selecionar a chave clusterizada com cuidado. Uma chave sequencial exclusiva é algo como boa prática, algo benéfico, porque ela vai evitar entradas duplicadas e também minimizar divisões de página na inserção de novos registros.

Em muitos bancos de dados, a restrição de chave primária que nós comentamos em aulas anteriores automaticamente gera um índice clusterizado nessa coluna.

Agora, vamos para o índice não agrupado ou non-clustered index.

Esse índice é como se fosse o índice que a gente encontra no final do livro, aquele índice que nós temos palavras-chave associadas com a página na qual aquela palavra é mencionada no livro.

Então, nós temos aqui as entradas deste índice vinculadas às páginas de dados. A página de dados é o local onde esse dado está fisicamente gravado, armazenado.

Aqui nós vamos ver que nós temos uma estrutura maior, que é o índice clusterizado, que é complementado por um índice do tipo non-clustered.

Esse índice tem, aqui no caso, nós estamos usando o e-mail como suporte a esse índice e, consequentemente, um índice não agrupado é um índice secundário. Nós vamos, na aula seguinte, falar sobre isso, mas vamos navegar nesse exemplo.

Se eu estou procurando o e-mail b@c.com, eu sei que o B vem antes da letra T, então vai cair na letra T à esquerda. Então, eu tenho o nó C. Como eu estou buscando B, eu sei que o B também está à esquerda de C. E B, que é o que eu estou buscando, vai estar à direita deste nó, porque ele é maior do que B. Então, eu vou encontrar o endereço 2354, que é onde eu vou encontrar a resposta, o meu registro completo.

Vamos fazer a navegação agora pelo lado direito, numa busca pelo e-mail g@rh.com. Eu sei que G vai estar à direita de T, porque eu vou encontrar ali H. H vai estar, mais uma vez, fazendo uma divisão entre os nossos registros. Então, G vai ficar à esquerda de H e eu vou conseguir encontrar ele na chave 9624.

Esse aqui é o mecanismo de navegação de um índice não agrupado.

Então, coisas interessantes aqui. O índice não agrupado é armazenado separadamente dos dados. Aqui, até fazer uma lembrança importante, dados são gravados em arquivos, ou seja, o conteúdo do nosso banco de dados gera um arquivo e, geralmente, o índice gera um outro arquivo com o respectivo endereçamento desses dados.

Aqui no índice não agrupado, a ordem física dos dados não é igual à ordem lógica estabelecida pelo índice. O acesso aos dados envolve pelo menos duas leituras de disco. Isso é uma coisa bem importante para relembrar.

Então, índices secundários, sempre que estamos utilizando especificamente índices não agrupados, nós temos pelo menos duas leituras de disco. Uma para acessar o índice e a outra para finalmente acessar os dados.

Já no índice clusterizado, índice e dados são a mesma coisa. Um ponto de atenção aqui, uma diferenciação bem importante entre esses tipos de índice.

É possível utilizar vários índices não clusterizados, cada um sendo para diferentes tipos de consultas. Benéfico para consultas que não usam colunas no índice clusterizado. Então, geralmente colunas que não são chaves primárias nós vamos indexar com este mecanismo e também, consequentemente, melhora o desempenho dessas consultas que não têm a chave clusterizada e que também não exigem verificação de um intervalo de dados.

Aquele mecanismo de eu verificar o dado entre o 10 e o número 20, que era este intervalo de dados.

Ponto também interessante para a gente comentar desse tipo de índice é que as operações de leitura são aceleradas. Porém, temos que ficar atentos, porque existe ali um atraso: as operações de gravação, de escrita, vão ficar mais lentas, porque toda a operação de inserção de dados vai ter que atualizar esse índice.

Novamente aqui eu vou falar de novo sobre a mágica de a gente encontrar um equilíbrio. Nós temos que encontrar um equilíbrio que vai justamente trazer a melhor experiência para as pessoas que usam a nossa aplicação, para decidir exatamente o número e o tipo de índices não clusterizados que vão suportar a nossa aplicação.




 