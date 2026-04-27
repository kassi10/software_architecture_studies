Formato GeoJSON

Nas aplicações modernas, é muito comum nós precisarmos trabalhar com dados geográficos, dados georreferenciados, isto é, a localização dos elementos de negócio geograficamente. Então, precisamos conversar sobre GeoJSON. 

Aqui é interessante destacar o seguinte: nós já temos a notação de objeto JavaScript, que é o JSON, como um formato que ficou muito popular na interoperabilidade dos sistemas modernos, principalmente por meio de APIs. E, consequentemente, para tratar de coordenadas georreferenciadas, dados geográficos, nós também temos um formato que é o GeoJSON, que é o formato de intercâmbio de dados geoespaciais.

E aqui, basicamente, o que nós temos é uma convenção, isto é, uma padronização para diferentes tipos de objetos de JSON que vão representar estes elementos geoespaciais.

Aqui nós vamos detalhar, eu quero mostrar para vocês alguns exemplos de como esses objetos geoespaciais são representados nessa notação.

A unidade de referência, ou sistema de referência, que nós temos aqui para as coordenadas geográficas, é o World Geodetic System de 1984, com unidades de graus decimais.

O primeiro exemplo é um polígono GeoJSON. Então, como fica representado, em termos de JSON, esta figura geométrica?

Para a gente representar um triângulo circunscrito por outro triângulo, nós vamos perceber que cada um desses triângulos tem uma coordenada. Os seus vértices, suas pontas, têm coordenadas.

E, para a gente fazer uma representação, que inclusive aqui a gente já pegou pesado no primeiro exemplo, trazendo uma representação um pouco mais sofisticada, que são duas formas gráficas, dois polígonos, um dentro do outro, que é algo que nós vamos encontrar com relativa frequência nos casos de uso atuais, nós vamos perceber então que essas figuras são representadas por este formato em GeoJSON.

É importante destacar, e eu gostaria que você prestasse atenção aqui, que nós vamos ter dois elementos principais, dois atributos. O primeiro é o atributo do tipo type, que vai determinar que estamos trabalhando com um polígono.

Então, o nosso type é Polygon e este polígono tem aquele conjunto de coordenadas. Olha só que interessante: nós temos um array de dois arrays de coordenadas. Com esta forma, a gente consegue representar esta forma bastante sofisticada em um simples JSON.

Vamos aos demais elementos. Nós vamos ter o ponto GeoJSON, que são coordenadas na ordem XY, leste e norte para as coordenadas projetadas, ou longitude e latitude para coordenadas geográficas. Em termos de GeoJSON, permanece o primeiro atributo type, observe que agora mudou para o tipo Point, que é o ponto, com as coordenadas, que são um array de dois elementos, as duas coordenadas que a gente precisa para identificar este ponto.

Aqui nós temos uma reta. Então, a reta é um array de posições, é um conjunto de posições. O type também muda. Observe que o nosso atributo type agora é LineString, e a gente tem aqui um array de coordenadas. Então, é um array de arrays. São dois arrays representando esta linha.

Voltando aqui, detalhando um pouco mais o nosso polígono. Então, o polígono é um array de anel linear, é uma matriz de anel linear. O primeiro elemento da matriz representa o anel externo e quaisquer elementos subsequentes representarão anéis internos, ou os orifícios daquela figura.

Aqui a gente tem um polígono simples, que é o meu primeiro exemplo aqui à esquerda. Se a gente fosse resgatar aquela nossa figura, eu somente teria um triângulo. Olhando o nosso polígono da direita, é a representação daqueles dois triângulos que a gente viu no primeiro exemplo.

Nós também temos multipontos. Também é um array de posições. Aqui a gente observa que muda o type. O type está como MultiPoint. E também é um array de arrays de coordenadas.

Da mesma forma, aqui nós vamos observar agora multirretas. E o type muda para MultiLineString. E aqui a gente vê que tem um array de outros arrays de coordenadas.

Então, a gente vai percebendo que, num primeiro momento, pode parecer estranho, mas, na verdade, a gente tem aqui uma sofisticação de representação que fica muito simples.

Uma vez que a gente absorve essa lógica desses elementos, você vê que é um encadeamento dos arrays que estarão contidos no atributo coordinates, e sempre tendo a sua especificação confirmada pelo atributo type.

E o último elemento que eu trouxe aqui são multipolígonos, que é um array de polígonos. E os polígonos são arrays daquele conjunto de coordenadas que a gente viu lá no começo.

Então, um objeto do tipo multipolígono tem o seu type multipolygon e o seu conjunto de coordenadas, isto é, o atributo coordinates, exatamente neste encadeamento de arrays.




 