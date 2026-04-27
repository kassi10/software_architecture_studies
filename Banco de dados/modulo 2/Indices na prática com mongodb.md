
Índices na prática com MongoDB. Neste momento, eu quero convidar você a navegar comigo pela documentação pública do MongoDB, para a gente verificar na prática a aplicação desses conceitos fundamentais que a gente discutiu até agora, sobre estruturas de indexação, métodos de acesso e os desafios de uso desses métodos e também daquele trade-off que nós vimos ali entre leitura, atualização e armazenamento, que está na conjectura RUM.

Nós vamos navegar pela documentação pública do MongoDB, inclusive que está em português, traduzida para o português aqui do Brasil. Eu quero principalmente convidar você a navegar comigo e começar a utilizar essa documentação como referência e usar durante a execução dos seus projetos. E esse mesmo raciocínio você vai aplicar para outros bancos de dados.

Então, se você estiver em um projeto utilizando o banco Oracle, nós vamos olhar na documentação do banco Oracle os seus tipos de indexação. Se estiver utilizando SQL Server, a mesma coisa. Vamos juntos nessa primeira olhada aqui na documentação pública do MongoDB sobre índices.

Vocês vão perceber que logo de cara nós já temos aqui a recapitulação de temas que estamos discutindo desde que começamos a falar de indexação. Primeiro, o objetivo dos índices, suporte à execução eficiente de consultas. Sem indexação, todos os documentos de uma coleção no MongoDB precisam ser verificados.

Lembra aquela história que nós falamos sobre o tempo de acesso ser logarítmico, tempo igual de acesso a um registro indexado, independente do seu tamanho? Nós temos aqui, exatamente, uma referência à documentação que remete a esse conceito. Ao invés de você navegar registro a registro, ou seja, documento a documento na coleção no MongoDB, com a indexação você vai direto aonde precisa. E, consequentemente, o tempo de acesso é muito menor.

Aqui também já vai ter um aviso para a gente sempre lembrar que os índices melhoram a consulta, mas como a gente viu lá na conjectura RUM, colocar um índice tem impacto negativo nas operações de gravação, operações de escrita.

A gente tem que estar muito atento se, na aplicação, existe essa característica de escrita. Temos que pensar com muita atenção se a gente quer colocar um índice, porque justamente a escrita vai ficar mais cara, vai ficar comprometida.

Casos de uso que a MongoDB sugere. Então, primeiro, consultas repetidas nos mesmos atributos serão candidatas a serem indexadas. Ok, vamos começar aqui pelo básico.

Exemplo: departamento de recursos humanos geralmente precisa procurar funcionários pela sua identificação. É muito comum a gente ter a coleção pessoa, com documento de pessoa física, e ali vai ter um CPF, identificador único, ou o próprio _id, que é o identificador único de um documento em MongoDB.

Para esse tipo de situação, é possível criar um índice neste campo de identificação, e esse índice é do tipo campo único. Esse aqui é o formato de indexação mais fundamental, mais básico. Você pega um atributo do seu documento e faz a indexação.

Segundo cenário de caso de uso que nós temos aqui é um vendedor precisando procurar informações do cliente pela sua localização, pelo seu endereço. Geralmente, um documento de cliente com endereço, o endereço é um subdocumento, ou um documento incorporado. É um tipo complexo de dados composto pelo nome da rua, pelo bairro, pelo estado, pela cidade, pelo CEP.

Assim, nessa estrutura de dados, que é algo que não é possível de ser feito em um banco relacional, que é ter um subdocumento dentro d 

Isso, que é ter um subdocumento dentro do documento, representa um relacionamento um para um. E, se tiver uma lista de documentos, é um para muitos. Nós podemos criar um índice diretamente no objeto de localização para melhorar o desempenho dessa consulta.

Aqui um detalhe que a MongoDB já destaca também na documentação. Se você cria um índice em um subdocumento ou documento incorporado, as queries têm que especificar todo o documento para utilizar esse índice. Uma query em um campo específico do documento não usa o índice. Então, caso tenha um campo específico naquele subdocumento, a gente precisa criar um índice exato para aquele atributo.

E aqui nós vamos ter um terceiro caso de uso, o gerente da mercearia, que quer pesquisar itens de estoque por nome e a quantidade para determinar quais itens estão com pouco estoque. Então, aqui nós já vamos mudar o conceito, é um índice composto, nos campos item e quantidade para esse tipo de busca.

Então, logo de cara, aqui no documento, já nos é introduzido três tipos: o campo único, o campo único no documento incorporado e o índice composto.

Mais para frente, eu quero também mostrar para vocês aqui que a própria MongoDB, publicamente, já fala que a estrutura de dados do índice é a árvore B, aqui, B-tree. Índices do MongoDB usam a estrutura de dados B-tree.

É por isso que nós tomamos muito cuidado de conversar até agora sobre estruturas fundamentais de dados, que é a árvore B, a variação B+, porque essas estruturas estão amplamente difundidas nos bancos de dados. E da mesma forma, agora, nós somos capazes de compreender o desafio de indexação, que é priorizar a leitura, onerando um pouco a escrita e onerando, talvez, um pouco o armazenamento, que é a conjectura RUM.

Uma coisa importante também para você levar em consideração, que eu recomendo, é você sempre procurar por limitações do índice do seu banco de dados. Toda documentação de banco de dados, em um determinado capítulo, fala dos seus índices, das suas características e das possíveis limitações.

Então, por exemplo, número de índices por coleção. Atualmente, 64 índices são suportados em uma coleção, ou o tamanho das chaves de índice. É sempre bom, ao longo do seu desenvolvimento, usar isso aqui como referência.

Aqui também nós temos o comentário sobre o índice padrão. Eu já disse algumas vezes que o MongoDB cria um índice único para todos os seus documentos, que é o campo _id. Aqui existe um mecanismo que impede que as aplicações clientes insiram dois documentos com o mesmo valor. Então, esse índice não pode ser descartado.

Uma outra coisa interessante, a nomenclatura. Como que o banco de dados nomeia os índices que você está criando para a sua aplicação. Então, aqui nós temos como regra que o nome padrão de um índice é a concatenação das chaves indexadas e a direção de cada chave no índice, que é 1 ou -1, indexadas e a direção de cada chave no índice, que é 1 ou -1.

Então, aquele índice que nós estamos procurando produtos em ordem alfabética, que estão no menor estoque, vai representar exatamente isso, item 1, quantidade -1, e a nomenclatura vai ser item_1_quantidade_-1. Essa daqui é a regra de nomenclatura de índices do MongoDB. Cada banco de dados vai ter a sua regra.

Importante, você não pode renomear o índice depois de criado. Então, se quiser renomear, você vai ter que excluir e depois recriar o índice. Fica atento, porque a recriação do índice pode ser um processo longo, consumir recursos do seu cluster, numa base de dados muito grande. Em um ambiente produtivo, é algo que tem que ser pensado com muito carinho.

Agora, eu queria comentar especificamente tipos de índice que nós podemos trabalhar em MongoDB. Então, eu vou avançar um pouquinho mais para você conhecer aqui na documentação que nós temos índices de campo único, que acabamos explorando mais aqui nessa introdução, índices compostos, multichave, textuais, coringa, geoespaciais e hash.

E mais para frente na documentação, nós vamos ver as propriedades do índice, que têm índices que não diferenciam maiúsculas de minúsculas, índices ocultos, parciais, esparsos, time to live e índices únicos.

Vamos olhar um pouquinho mais no detalhe o campo único. Então, a ideia do índice de campo único é a informação de um único campo de uma coleção. Todas as coleções vão ter o campo _id e depois você pode adicionar mais índices para outras queries e operações importantes.

Nós vamos ter aqui algumas características. Você pode aplicar isso no próprio documento, no subdocumento e nos campos dentro de subdocumento. Precisa definir uma ordem de classificação, então 1 classifica em valor crescente, ordem crescente, -1 em decrescente.

Comando para isso, bem tranquilo, db.coleção.createIndex, nome do campo e ordenamento. Aqui nós temos o comando de criação de índice para o score de maneira, a ordem crescente. Então, é isso que vai acontecer neste campo único. Bastante tranquilo da gente começar com indexação aqui em MongoDB.

Depois, nós vamos ter os índices compostos. A ideia aqui do índice composto é que nós vamos fazer uma ordenação pelo userId de maneira crescente e o score, a nota, de maneira decrescente. Então, observa aqui nessa estrutura de dados que nós vamos ter primeiro a aplicação da regra alfabética e depois da regra numérica. CA275, 55, ordem decrescente. E a estrutura de dados aqui na coleção, o score 30, userId.

O comando permanece o mesmo, db, nome da coleção, createIndex, porém estamos especificando o nome do campo e aquela ordem.

Depois nós vamos ter índices multichave. A ideia desse índice é classificar dados que contêm valores de array. Quando você tiver uma consulta dentro de uma estrutura de array, e o array dentro do documento significa um relacionamento um para muitos, geralmente, quando é um array de documentos, você pode ter esse índice aqui para a indexação.

O que é interessante? Não é preciso especificar o tipo das chaves. Quando você cria um índice em um campo que contém um array, o MongoDB vai definir automaticamente esse índice como do tipo multichave.

Então, vamos olhar aqui o comando. Nós vamos perceber que não muda nada. É createIndex, o nome do campo, ordenação. Porém, na estrutura, nós vamos ver que a gente tem aqui o atributo de endereço, que é o address. E dentro dele, nós temos o array, que é essa abertura aqui dos colchetes.

E o subdocumento que começa com o CEP, que é o ZIP. Então, para esse tipo de estrutura, a gente vai criar um índice basicamente dando o endereço desse atributo, que é addr.zip. O MongoDB vai entender isso e vai criar o índice do tipo multichave.

Índices de texto. Aqui é um ponto interessante. Índices textuais é para a gente fazer busca de texto em conteúdo de string. Por padrão, uma coleção só pode ter um índice de texto, mas esse índice pode cobrir vários campos.

Aqui eu estou falando especificamente do índice textual tradicional de MongoDB, que nós vamos encontrar no MongoDB Community. Todo o MongoDB on-premises suporta esse tipo de indexação. O comando permanece como createIndex, atributo do tipo text. E esse índice é o índice do tipo text, que vai suportar o operador $text.

Então, aqui é importante lembrar o seguinte, isso aqui vai valer para implementações on-premises, que você mesmo faz a gestão do seu MongoDB. Quando você trabalhar no Atlas, você vai ter um índice adicional, que é um índice chamado Atlas Search, e este índice é baseado no mecanismo do Apache Lucene.

Vamos relembrar que Apache Lucene é a biblioteca mais popular de indexação textual. Quando você estiver no Atlas, a recomendação que eu faço para você não é utilizar o índice textual com o operador $text, e sim utilizar, para conteúdos que você quer indexar textualmente, o índice Atlas Search, que vai estar criando uma estrutura de Apache Lucene para você, e o operador vai ser o $search.

E para fechar o meu comentário aqui de índices textuais, lembra que o Apache Lucene é o motor de indexação que é utilizado no Elasticsearch, no OpenSearch, no Solr e em outras implementações populares que a gente encontra por aí, que são baseadas em Apache Lucene.

Índices coringa. Aqui nós temos o suporte aos esquemas flexíveis, que vai permitir que, ao longo do tempo, os atributos mudem de nome ou não sejam exatamente os mesmos em todos os documentos. Então, com o operador $**, a gente cria um índice que vai suportar campos desconhecidos. Essa é a principal característica.

Um outro índice importante, muito comum, são índices geoespaciais. Então, a gente já percebeu, ao longo da evolução da interoperabilidade entre sistemas com APIs, que usam JSON como padrão, e dentro dos JSONs a gente trafega dados geoespaciais, surge um padrão de indústria que é o GeoJSON.

Então, o GeoJSON permite identificar pontos, linhas e polígonos, e é uma rede coordenada. E, consequentemente, se nós estamos armazenando esse tipo de estrutura, precisamos de uma estrutura de indexação para a leitura adequada, para a leitura em tempo rápido disso.

O MongoDB tem dois tipos de índices geoespaciais: o índice de esferas, então queries que vão interpretar a geometria em uma esfera, e o índice 2D, que vai suportar queries que interpretam a geometria de uma superfície plana.

Aqui nós vamos ver que existem operadores, inclusive, do MongoDB, que exigem esses índices, que é o caso do $near, $nearSphere e do Aggregation Framework com o $geoNear. Esse tipo de operador vai trazer uma riqueza de busca na sua aplicação para aquele caso de uso em que você está rastreando deslocamento de uma carga ao longo do tempo, ao longo do espaço, ao longo da sua rota entre o ponto A e o ponto B.

Tudo que estiver relacionado com coordenadas geoespaciais, a gente usa esse índice e esses operadores.

E também vamos ter o índice com hash. Então, nós vimos lá que o hash é uma função, um algoritmo aplicado sobre o conteúdo de um atributo, e este conteúdo gera um valor de tamanho fixo. E, especificamente para o MongoDB, nós vamos gerar os hashes para a chave de fragmentação, ou chave de sharding.

Nós temos um conceito de crescimento horizontal do banco MongoDB, que é a fragmentação, ou sharding, do seu cluster. Então, para isso, você vai usar esse índice, que é um índice do tipo hash, e, consequentemente, você vai conseguir distribuir fisicamente a sua informação, os documentos da sua coleção, em um cluster shardado.






 