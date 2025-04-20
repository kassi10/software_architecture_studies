Olá, pessoal, tudo bem? Hoje a gente vai ter uma aula fantástica do nosso MBA com o Natan Pasquarelli. O Natan é Head de Engenharia no Itaú e tem uma experiência muito grande com sistemas bancários. Ele já passou por trabalhos com sistemas desde mainframes até os mais modernos que os bancos utilizam hoje em dia.

Como você pode imaginar, entender de arquitetura de software numa situação dessas é extremamente importante, porque apesar de os bancos rodarem sistemas desde 1980 ou algo do tipo, esses sistemas perduram até hoje. Isso significa que, de uma forma ou de outra, com todas as limitações e restrições que possam ter, estamos falando de sistemas com 40 anos de idade.

Então, como você, desenvolvedor, conseguiria desenvolver um sistema que pudesse durar 40 anos? Já pensou nisso? Quais são as implicações? O que você deve considerar ao arquitetar um sistema dessa forma? E o mais interessante possível. Como os sistemas modernos conseguem se comunicar com os antigos de maneira desacoplada, para que também possam perdurar por muito tempo?

Desenvolver software é algo muito caro. Imagine um banco, ao desenvolver software, a quantidade de profissionais na área de tecnologia, principalmente sêniores, que precisam ter para rodar operações críticas. Imagine o nível de operação que um Itaú da vida, onde o Natan trabalha, deve ter para que você consiga realizar suas operações no dia a dia. Sistemas de back office, sistemas para cada tipo de produto que o banco oferece.

Hoje, teremos uma baita aula com o Natan para entender como desenvolver e manter sistemas legados, e quais pontos considerar ao projetar um sistema que precisa durar muito tempo. Vou trazer o Natan aqui, o palco é dele. Também traremos algumas discussões. 

Deixa eu trazer o Natan. Fala, grande Natan, firme e forte?

— Falo, Wesley. Tudo bem por aí? Tudo tranquilo?

— Natan, se apresenta um pouco. Eu já falei de você, mas sei que sistemas legados são algo natural no seu dia a dia. Começar um sistema ou projeto novo não é tão comum quando se trabalha em uma grande empresa, correto?

— Na verdade, hoje em dia, dentro dos bancos, temos muitos sistemas legados, que ainda pagam nossas contas. Eles seguraram a bronca até agora, mas, há uns quatro anos, passamos por uma grande jornada de mudança. Mesmo com sistemas novos, sempre temos que conversar com os antigos, desacoplar e repensar a arquitetura. É um ambiente bem complexo, com muitas conexões. Você trabalha tanto com o que há de mais novo quanto com sistemas de 40, 50 anos. Mas essa parte mais antiga está bem menor agora. Fizemos uma grande jornada para limpar isso.

— Natan, vou colocar sua apresentação e deixar o palco com você. Quando for pertinente, eu volto, a gente discute esses pontos, que, sem dúvida, vão enriquecer muito nosso curso. E não tenho dúvidas de que vou aprender bastante com você também. 

— Espero pelo menos contar onde já errei para que a gente não erre de novo. Vamos juntos!

— Então vamos nessa, o palco é seu.

— Antes de ser Head de Tecnologia, quem é essa pessoa falando com vocês? Comecei a programar cedo, aos 14 anos. Fiz muito front-end e vendia sites. Isso dava dinheiro na época. Tenho 35 anos, então, quem tem essa idade lembra do boom de venda de websites. Mais tarde, entrei no mercado de trabalho com eletrônica, depois fiz faculdade de engenharia da computação e passei em um processo de trainee para um banco. Fiquei dois anos nesse banco e depois fui para o Itaú.

No Itaú, há 12 anos, começamos a desenvolver um sistema em COBOL. Na época, o sistema era considerado moderno, e a arquitetura que desenvolvemos ainda é moderna, apesar da linguagem. Isso mostra que a arquitetura não depende tanto da tecnologia, mas sim do que você quer resolver.

Tecnologias são ferramentas para nos ajudar, não obstáculos. Vamos usá-las a nosso favor. Caso vocês queiram me seguir no instagram é: @natampf , lá podemos compartilhar conhecimentos e se conhecer um pouco mais.

Fora isso, teve um momento da minha carreira em que eu decidi começar a compartilhar o que eu tinha de conhecimento, o que eu já tinha passado, algumas coisas, dentro de um site. Então, eu criei o natan.pf.com para falar sobre tecnologia, escrever artigos, etc. Hoje em dia, esse site conta com alguns outros integrantes, tem algumas pessoas que escrevem para ele também. Surgiu também o Eureka TI, que foi um pedido da galera que acessa o site, e é um podcast que está lá no Spotify, Eureka TI. Se vocês quiserem dar uma ouvida, tem alguns episódios; preciso retomar e fazer mais alguns, mas já tem alguma coisinha lá. E tem mais um, o code, que é uma iniciativa da qual eu participo e que também convido vocês a conhecer. É uma ONG dedicada a compartilhar conhecimento com quem não tem condições de pagar por esse conhecimento, então a gente ajuda as pessoas a entrarem na área de tecnologia, especialmente aquelas que têm mais dificuldade e menor renda. É um projeto bem bacana, uma iniciativa legal. Então, se vocês quiserem conhecer fiquem a vontade, estão convidados.