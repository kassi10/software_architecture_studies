Conjectura RUM. Para compreendermos melhor o tema dos índices, nós precisamos conversar sobre métodos de acesso. RUM significa Read, Update e Memory. Ou a leitura, a atualização, e aqui podemos entender a atualização como escrita dos dados em disco, e memória como o respectivo armazenamento.

Então, nós temos métodos de acesso aos dados, e estes métodos estão sujeitos às características de hardware e da carga de trabalho que nós temos rodando nas nossas aplicações. Alterações na carga de trabalho ou no hardware nos levam a repensar métodos de acesso a esses dados.

E aqui, dando contexto, vamos relembrar que índices em bancos de dados são métodos de acesso mais eficientes aos dados que estão armazenados nesse banco de dados.

Então, os desafios fundamentais para nós conseguirmos desenhar métodos de acesso são tempos de leitura, que vai corresponder à letra R, custo de atualização, que corresponde à letra U. E por custo de atualização, vamos sempre relacionar com a escrita desta informação. E aqui lembrando que as estruturas de dados de escrita são diferentes das estruturas de dados otimizadas para leitura.

Por exemplo, a estrutura básica de um banco de dados é um arquivo sequencial chamado heap file. É um arquivo que vai guardando os dados em blocos de armazenamento. Esses blocos são chamados de páginas e esse armazenamento não necessariamente é ordenado. Na verdade, o armazenamento vai acontecendo ao final de cada bloco, conforme os blocos vão sendo completados.

E o terceiro elemento é justamente esta sobrecarga de memória ou armazenamento, que corresponde à letra M. Então, R, leitura, U, atualização, M para memória ou armazenamento.

Com isso, nós temos o nosso RUM, no tema de métodos de acesso, estruturas de acesso para os nossos dados. E com isso, nós vamos chegar na conjectura RUM, que significa o seguinte. Ler, atualizar e armazenar, sendo que a otimização de dois destes pilares leva às custas do terceiro.

Ou seja, é o trade-off, é uma contrapartida. Se você otimiza atualizações e leituras, você está perdendo em armazenamento. O armazenamento é maior.

Então, sempre que você tiver esses três elementos, que é o desafio constante de métodos de acesso, você somente consegue otimizar dois. O terceiro elemento vai custar mais caro.

Mundo ideal, solução ideal. Método de acesso que sempre fornece o menor custo de leitura, menor custo de atualização e não requer memória extra ou armazenamento extra sobre os dados básicos que estamos armazenando. Na prática, as estruturas de dados são projetadas para comprometer entre estes três elementos, ou seja, dois estarão mais otimizados e um vai custar mais caro.

E entre os vários fatores que vão determinar este desempenho, nós temos a característica de hardware sobre o qual estamos rodando a nossa estrutura de dados, o tipo da carga de trabalho e também expectativas de tempo das pessoas usuárias dessas estruturas de dados que estão sendo utilizadas pelas aplicações finais.

Vamos dar uma olhada nisso graficamente. Nós vamos ter aqui neste triângulo os três vértices: leitura otimizada, escrita otimizada e espaço ou armazenamento otimizado. Aqui eu tomei o cuidado de trazer para você exatamente como está no paper original da conjectura RUM.

Então, vamos observar essa imagem, vamos ler essa imagem juntos. Na leitura otimizada, nós vamos encontrar estruturas como hash, como a árvore B, tree e skip list. O que nós temos aqui de comum nessas estruturas? Tempo de acesso constante. Lembra que nós conversamos sobre tempo logarítmico? Então, não importa o tamanho da base de dados, o tempo de acesso para um registro indexado nessas estruturas será constante.

Como consequência, será utilizado mais espaço de armazenamento, tanto em disco quanto em memória, para carregar essa estrutura, e a escrita também será mais lenta.

Escrita otimizada. Aqui nós temos um outro conjunto de estruturas fundamentais de dados que estão otimizadas para escrita. Como acontece essa otimização? Existem estruturas secundárias diferenciais, ou seja, uma estrutura que vai guardar a operação de atualização que aconteceu em relação ao tempo inicial, ou seja, em relação à primeira escrita.

Então, existe uma estrutura adicional de armazenamento que vai guardando todas as operações de atualização e, em determinado momento, a estrutura original é atualizada de forma massiva, que é o formato bulk. Esses updates são consolidados e são aplicados na estrutura original de dados.

Estruturas comuns otimizadas à escrita: PDT, que corresponde ao Position Differential Tree, então, a árvore de posição diferencial; LSM, que é o Log-Structured Merge Tree, ou árvore de mesclagem de log estruturado; o MAM, que é o Materialized Sort-Merge; e o PBT, que é o Partitioned B-Tree, ou árvore B particionada.

E a terceira aresta do nosso triângulo é justamente a otimização de armazenamento, ou espaço otimizado. Então, aqui nós temos índices esparsos, como nós comentamos, o sparse index, Bloom filter e bitmap. O que caracteriza, o que tem em comum nessas estruturas? O que caracteriza, o que tem em comum nessas estruturas? Primeiro, técnicas de registro de dados, e sim, nós temos ponteiros que vão apontar para o começo do bloco dos dados. Esse tipo de técnica vai favorecer o armazenamento nessas estruturas.




 