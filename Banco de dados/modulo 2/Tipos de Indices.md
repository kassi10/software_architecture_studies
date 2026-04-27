Tipos de índices

Vamos conversar sobre os tipos mais comuns de índices que vamos encontrar nos diferentes bancos de dados na nossa jornada profissional.

Vamos começar pelo clássico índice primário, Primary Index. Aqui nós temos uma organização dos dados que será baseada nas chaves primárias, ou seja, nos identificadores únicos dos nossos registros. Aqui nós temos a unicidade das chaves primárias, também temos uma recuperação dos dados bastante acelerada naquilo que nós estamos buscando pelas chaves primárias, e essas chaves primárias geralmente são sequenciais numéricos. E o índice primário pode ser denso ou esparso.

Lembrando aqui que o índice denso é aquele índice que tem exatamente a mesma quantidade de entradas que temos de registros. E o índice esparso é aquele índice que tem uma quantidade menor, como se fossem blocos.

Índice secundário, secondary index. Aqui nós temos os dados organizados com base em atributos ou colunas que não são chaves primárias. Nós temos, consequentemente, buscas eficientes a partir dessas colunas. Não existe uma garantia de dados únicos ou de unicidade, como acontece no índice primário, e o índice secundário também pode ser denso ou esparso.

Índice agrupado, o cluster index. Aqui nós vimos que os registros são armazenados fisicamente na ordem que está especificada na lógica deste índice. Frequentemente, a nossa chave primária serve como índice agrupado, porque ela justamente tem esse mecanismo de ser um sequencial e, consequentemente, força a gravação dos dados nesta sequência, fisicamente no dispositivo de armazenamento. Mas também o índice agrupado pode acontecer em qualquer outro atributo do nosso registro, ou qualquer conjunto de atributos.

Índice de texto completo, ou Full Text Search. Aqui nós temos um tipo de indexação que é usada para pesquisas de texto em grandes blocos de texto, como documentos, artigos, blogs. Aqui nós vamos encontrar aqueles recursos como palavras-chave, frases, proximidade e relevância.

Temos também índices de hash, ou hash index. Aqui nós temos um caso de uso bem interessante. O hash index é ideal para igualdades exatas. Não é um índice que vai trabalhar bem com aquela busca de intervalos entre o 10 e o 20. O que vai acontecer aqui?

Este índice vai buscar os registros usando uma função de hash, que é aquela função que vai receber uma entrada, que é a sua chave, um conteúdo, e vai transformar em um valor de tamanho fixo, que é o valor do hash. A comparação de valores de hash é uma operação extremamente rápida. Então, como consequência, é ideal para essas igualdades exatas que nós estamos buscando.

Índice de bitmap, ou bitmap index. Aqui nós temos uma otimização para consultas que têm atributos com um número limitado de valores distintos. Deixa eu tentar dar um exemplo. Gênero masculino e feminino, estado civil, solteiro, casado, divorciado, viúvo. Esse tipo de consulta que está buscando esse número limitado de valores distintos pode ser acelerada por um índice do tipo bitmap.

Esse índice faz operações de conjunto, intersecção, união, diferença, de uma maneira muito eficiente, como operações bitwise, que são aquelas operações bit a bit. É como se cada atributo fosse convertido em um vetor de bits, em um array de bits, e essas operações 0 ou 1 são feitas de maneira rápida, essas operações lógicas. Consequentemente, para esse tipo de consulta, com um número limitado de valores distintos, nós temos uma otimização bem interessante.

Índice geoespacial, o Spatial Index. Aqui nós temos o armazenamento e a respectiva consulta de informações geográficas, que são as coordenadas de latitude e longitude. Nós temos operações especiais, como busca de pontos em uma área específica, cálculo de distância entre dois pontos. Então, para operações geoespaciais, esse tipo de índice é altamente recomendável.

E também índice de vetor, ou vector search. Aqui, um assunto super atual. Desde 2023, aqui no Brasil, eu tenho acompanhado as discussões de IA generativa, ou GNI, Generative Artificial Intelligence, que vai fazer com que dados como os nossos textos, vídeos, áudios e imagens sejam convertidos em vetores multidimensionais.

Uma vez que a gente utiliza esse mecanismo, nós precisamos ter um lugar para guardar o vetor gerado e também um mecanismo de busca. Quando a gente tem esse tipo de dado, que são dados multidimensionais, e nós vamos fazer aquelas buscas por semelhança ou vizinhança, o índice de vetor é altamente recomendável. E nós vamos utilizar isso em todo o app que está utilizando Generative AI como parte da stack de tecnologia para entregar a experiência final aos nossos queridos usuários.

 