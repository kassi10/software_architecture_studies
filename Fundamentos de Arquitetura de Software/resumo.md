# Fitness functions

Fitness functions são metricas que mede um software ao longo do tempo
Coloca-se uma escala de pontuação para cada métrica
- Adicionar um peso para cada categoria
- Fazer uma média ponderada
- Criar planilhas com datas para ver a evolução do software (uma pra cada métrica e uma geral)


# Acoplamento aferente e eferente
Aferente significa que outros componentes dependem dele
Quanto mais aferente mais critico
Eferente: quantos componentes ele depende
Quanto mais eferente menos estavel

# Metrificando a instabilidade por componente
- Fun in -> aferente
- Fun out -> eferente
instabilidade = Fun out/ (Fun in + Fun out)
Entre 0 e 1
Quanto menor o valor mais estavel

# Lei de postel

- Seja conservador no que faz mas seja liberal do que voce aceita dos outros
- Criar sistemas que sigam padroes ao enviar informacoes;
- Flexivel ao receber informacoes dos outros

# Leis de Lehman
- Mudanca continua: um software deve se adapdat as mudancas do ambiente
- Lei do crescimento da complexidade: a complexidade tende a aumentar a menosnque haja um esforco explicito para diminui-la.
- Lei da conservacao da familiaridade: manter um software deve ser familiar para todos os desenvolvedores
- Lei da conservacao do esforco: quanto maior o software vai ficando mais esforco vai tendo se nao conservar o esforco.
