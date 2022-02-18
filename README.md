# Experimentos Controlados na Web

![teste de um componente](https://media-exp1.licdn.com/dms/image/C4E12AQGXOeXrG8bhfg/article-cover_image-shrink_720_1280/0/1620761719931?e=1650499200&v=beta&t=mfBMIYGBNNvI-MSTFL070lTCgafc_NZR10yzQhgGiZ0)

**JOMAR A. CARDOSO**

¹Universidade Feevale – RS 239, 2755 – 93.525-075 – Novo Hamburgo – RS - Brazil

***ABSTRACT**. The web offers an unprecedented opportunity to quickly evaluate ideas using controlled experiments, the A / B tests, split tests, control / treatment tests, multivariate tests (MVT), and parallel flights. Controlled experiments incorporate the best way to establish a causal relationship between changes and their influence on user-observable behavior. We analyze the important ingredients of running controlled experiments and discuss their limitations. We focus on a number of critical areas for experimentation, including statistical power, sample size, and variance reduction techniques.*

**RESUMO.** A web oferece uma oportunidade sem precedentes de avaliar idéias rapidamente usando experimentos controlados, os, testes A/B, testes divididos, testes de controle/tratamento, testes multivariáveis (MVT) e voos paralelos. Experimentos controlados incorporam a melhor forma de estabelecer uma relação causal entre mudanças e sua influência no comportamento observável pelo usuário. Analisamos os ingredientes importantes da execução de experimentos controlados e discutimos suas limitações. Nos concentramos em várias áreas críticas para a experimentação, incluindo poder estatístico, tamanho da amostra e técnicas para redução de variância. 

**Palavras chave:** A/B, OEC, variante, experimento, teste.

## 1. Introdução

Experimentos controlados na web geralmente geram grandes quantidades de dados, que podem ser analisados usando técnicas de mineração de dados para obter um entendimento mais profundo dos fatores que influenciam o resultado, levando a novas hipóteses e criando um ciclo de melhorias (Kohavi et al. 2004). As organizações que adotam experimentos controlados com critérios de avaliação claros podem evoluir seus sistemas com otimizações automatizadas e análises em tempo real. 

Uma medida precisa vale mais que mil opiniões de especialistas - Almirante Grace Hopper nos anos 1700, o capitão de um navio britânico observou a falta de escorbuto entre os marinheiros que serviam nos navios da marinha dos países mediterrânicos, onde frutas cítricas faziam parte de suas rações. Ele então deu metade de sua tripulação (grupo de tratamento) enquanto a outra metade (grupo de controle) continuou com sua dieta regular. Apesar de muitas queixas entre a equipe do grupo de tratamento, o experimento foi um sucesso, mostrando que o consumo de laranjas evitava o escorbuto. Embora o capitão não tenha percebido que a doença é uma consequência da deficiência de vitamina C e que os limões também são ricos nisso, a intervenção funcionou. Os marinheiros britânicos acabaram sendo obrigados a consumir frutas cítricas regularmente, uma prática que deu origem aos laboratórios (Rossi et al. 2003, Marks 2000).

Quase 300 anos depois, Greg Linden, da Amazon, criou um protótipo para mostrar recomendações personalizadas com base nos itens do carrinho de compras (Linden 2006a,b). O cliente adiciona um item, as recomendações aparecem, adicione outro item, diferentes recomendações aparecerão. Linden observa que, embora o protótipo tenha sido promissor, um vice-presidente sênior de marketing estava contrário a ele, alegando que isso iria distrair as pessoas no checkout. Mesmo proibido de continuar seus trabalhos, o experimento controlado já havia mostrado resultados e não o exibir seria um desperdício para a Amazon. Assim, foram lançadas as recomendações para o carrinho de compras.

A cultura da experimentação na Amazon, onde os dados superam a intuição, permitiu à ela inovar de maneira rápida e eficaz (Kohavi et al. 2004). Neste artigo, descrevemos várias arquiteturas com suas vantagens e desvantagens e que os experimentos controlados têm um ótimo retorno sobre o investimento (ROI) e que a construção da infraestrutura apropriada pode acelerar a inovação (Thomke 2003).

## 2. Desenvolvimento

A web oferece uma oportunidade sem precedentes de avaliar idéias rapidamente usando experimentos controlados (Moran 2007; Quarto-vonTivadar 2006). Na manifestação mais simples de tais experimentos, os usuários ao vivo são designados aleatoriamente para uma de duas variantes: o controle, que geralmente é a versão "existente" e o tratamento, que geralmente é uma nova versão com novos itens sendo avaliados. Métricas de interesse que variam de desempenho em tempo de execução a comportamentos implícitos e explícitos do usuário e dados de pesquisa são coletados. Os testes estatísticos são então conduzidos através dos dados coletados para avaliar se há uma diferença estatisticamente significante entre as duas variantes nas métricas de interesse (Box et al. 2005), permitindo reter ou rejeitar a hipótese de que não há diferença entre as versões. Em muitos casos, a busca detalhada por segmentos de usuários usando técnicas de aprendizado de máquina e data mining, permite entender quais subpopulações apresentam diferenças significativas, ajudando assim a melhorar o entendimento e o progresso com uma idéia (Kohavi et al. 2004).

Segundo Keppel a maioria das organizações tem muitas idéias, mas o retorno do investimento (ROI) para muitas pode não ser claro e a avaliação em si pode ser cara (Keppel et al. 1992, p. 5–6). No entanto, mesmo pequenas alterações podem fazer uma grande diferença e geralmente de maneiras inesperadas. Um experimento ao vivo, possui na verdade, um longo caminho para fornecer orientações quanto ao valor da ideia.

No experimento controlado mais simples, o Teste A/B, os usuários são aleatoriamente expostos a uma das duas variantes: controle (A) ou tratamento (B), como mostrado na Figura 1 e na Figura 2. Os usuários são distribuídos aleatoriamente e nenhum fator pode influenciar a decisão. Com base nas observações coletadas, é derivado um Critério de Avaliação Geral (OEC) (Roy 2001) para cada variante. O OEC pode ser a taxa de conversão, unidades compradas, receita, lucro, vida útil esperada valor ou alguma combinação ponderada destes, como na Figura 3. Em seguida, é feita uma análise para determinar se a diferença no OEC para as variantes é estatisticamente significativa. Se o experimento foi projetado e executado adequadamente, a única coisa diferente entre as duas variantes é a alteração entre o controle e o tratamento, portanto, quaisquer diferenças no OEC é inevitavelmente o resultado dessa tarefa (Weiss 1997, p. 215).

**Figura 1: Amostra de teste A/B**

![image](https://user-images.githubusercontent.com/27368585/154770081-38707bd8-43d9-460b-81de-984874c30a12.png)

Fonte: autor, 2019  

**Figura 2 - Controle e variantes**

![image](https://user-images.githubusercontent.com/27368585/154770166-92643c8c-3d8b-4043-a18c-522c730ba13d.png)

Fonte: autor, 2019

### 2.1 Terminologia

A terminologia para experimentos controlados varia amplamente na literatura. Abaixo, estão definidos os termos-chave usados neste artigo, observando os termos alternativos mais usados. 

Critério de Avaliação Geral (OEC) (Roy 2001). Uma medida quantitativa do objetivo da experiência. Nas estatísticas, isso costuma ser chamado de variável dependente do respondente, (Mason et al. 1989), outros sinônimos incluem resultado, avaliação métrica, métrica de desempenho ou função de aptidão (Quarto-vonTivadar 2006). Os experimentos podem ter vários objetivos, Figura 3, e esses podem ter pesos diferentes na avaliação (Kaplan e Norton, 1996), uma única métrica, pode ser uma combinação ponderada dos objetivos (Roy 2001, p. 50). Um bom OEC não deve ser focado a curto prazo (por exemplo, cliques), pelo contrário, deve incluir fatores que prevejam objetivos de longo prazo, como visitas repetidas.

**Figura 3: OEC**

![image](https://user-images.githubusercontent.com/27368585/154770254-bcb6e21e-b8c3-4b07-8002-70a8d3b8e47d.png)

Fonte: autor

Fatores. Uma variável experimental controlável que se acredita influenciar o OEC. Os fatores são chamados algumas vezes de variáveis. Em testes A/B simples, há um fator único com dois valores: A e B (Nielsen 2005). 

Variante. Uma experiência do usuário sendo testada através da atribuição de níveis aos fatores. Há as variantes de tratamento e de controle, que é a original, sem modificações. No caso de um erro, por exemplo, o experimento é abortado e todos os usuários devem ver somente a de controle (Nielsen 2005).

Unidade experimental. A entidade sobre a qual as métricas são calculadas antes da média de toda a experiência para cada variante (Nielsen 2005). Na web, o usuário é uma unidade experimental comum, embora algumas métricas possam ter exibições de sessão do usuário ou página como unidades experimentais. É importante que o usuário receba uma experiência consistente durante todo o experimento e isso é comumente alcançado por meio de identificação com base nos IDs de usuário armazenados nos cookies.

Hipótese nula. A hipótese, muitas vezes referida como H0, onde os OECs para as variantes não são diferentes e que qualquer diferença observada durante o experimento são devidas a flutuações aleatórias (Nielsen 2005).

Nível de confiança. A probabilidade de não rejeitar (ou seja, reter) a hipótese nula quando verdadeira.

Poder. A probabilidade de rejeitar corretamente a hipótese nula, quando é falsa. O poder consegue medir a capacidade de detectar uma diferença quando ela realmente existe (Box et al. 2005).

Teste A/A. Em vez de um teste A/B, você exercita o sistema de experimentação atribuindo usuários a um de dois grupos, mas os expõe exatamente à mesma experiência (Peterson 2004). Um teste A/A pode ser usado para coletar dados e avaliar sua variabilidade para cálculos de potência, e testar o sistema de experimentação.

Desvio padrão: Uma medida de variabilidade, geralmente indicada por σ ou s.

![image](https://user-images.githubusercontent.com/27368585/154770339-a2b3d818-8030-44d1-b521-2dca6ac2881b.png)

Erro padrão. Para uma estatística, é o desvio padrão da distribuição amostral da estatística da amostra (Mason et al. 1989). Para uma média de observações independentes.

![image](https://user-images.githubusercontent.com/27368585/154770361-dba042c2-d1e7-4441-9dd0-2d337a65a3c2.png)

### 2.2 Teste de hipóteses e tamanho da amostra

Para avaliar se um dos tratamentos é diferente do controle, um teste estatístico pode ser feito. Segundo Keppel é aceito um tratamento como significativamente diferente se o teste rejeitar a hipótese nula, que é de que os OECs não sejam diferentes (Keppel et al. 1992).

Os fatores que impactam o teste:

1. Nível de confiança. Geralmente definido como 95%, este nível implica que 5% das ocorrências concluirá incorretamente (Box et al. 2005). Na figura 4 mostra um teste com resultado de 96%, sendo abaixo de 95% inconclusivo.
2. Poder. Geralmente é de cerca de 80 a 95%, embora não seja diretamente controlado (Box et al. 2005). Se a hipótese não for nula, ou seja, houver uma diferença nos OECs, o poder é a probabilidade de determinar se a diferença é estatisticamente significativa.
3. Erro padrão. Quanto menor o erro padrão, mais poderoso o teste (Mason et al. 1989; Keppel et al. 1992). Existem três maneiras úteis de reduzir o erro padrão:
4. O OEC estimado de uma média de amostras grandes. Conforme mostrado na seção 2.1, o erro padrão de uma média é inversamente proporcional à raiz quadrada do tamanho da amostra, sendo assim aumentar a amostra (executar o experimento por mais tempo), reduz o erro padrão.
5. Usar componentes OEC que possuam variabilidade inerentemente mais baixa, ou seja, o desvio padrão menor. Por exemplo, a probabilidade de conversão (0 a 100%) geralmente tem um desvio padrão mais baixo do que o número de unidades de compra (geralmente inteiros pequenos), que por sua vez tem um desvio padrão mais baixo que a receita (Kohavi 2003).
6. Reduzir a variabilidade do OEC filtrando os usuários que não foram expostos às variantes, mas que ainda estavam incluídos no OEC. Por exemplo, se você alterar para a página de checkout, faça a análise apenas dos usuários que acessaram a página, pois todo mundo adiciona ruído, aumentando a variabilidade (Kohavi 2003).
7. Efeito. A diferença nos OECs para as variantes, isto é, a média do tratamento menos a média do controle. Diferenças maiores são mais fáceis de detectar, portanto, é improvável que sejam perdidas grandes diferenças.

Duas fórmulas são úteis para compartilhar neste contexto. O primeiro é o t-test, usado em teste A/B (testes de hipótese de fator único):

![image](https://user-images.githubusercontent.com/27368585/154770471-48b2cc16-3451-422f-b16f-e11eb2557095.png)

onde OA e OB são os valores estimados do OEC (por exemplo, médias), d é o desvio padrão estimado da diferença entre os dois OECs e o resultado do teste. Com base no nível de confiança, um limite é estabelecido e como o valor absoluto de t é maior que o limite, rejeita-se a hipótese nula, alegando que o OEC do tratamento é estatisticamente diferente do OEC do controle, assumindo que as amostras são grandes o suficiente para que seja seguro assumir que os meios têm uma distribuição normal pelo teorema do limite central (Boos e Hughes-Oliver 2000).

Uma segunda fórmula é um cálculo para o tamanho mínimo da amostra, em que o nível de confiança desejado seja de 95% e a potência desejada seja de 80% (van Belle 2002, p. 31)

![image](https://user-images.githubusercontent.com/27368585/154770505-8e79aede-e534-485e-8c1a-cbe61ff99e77.png)

onde é assumido o número de usuários em cada variante e as variantes de tamanho igual, σ² é a variante do OEC e é a sensibilidade ou a quantidade de alteração que você deseja detectar. O coeficiente de 16 na fórmula fornece 80% de potência, ou seja, tem 80% de probabilidade de rejeitar a hipótese nula de que existe uma diferença entre o tratamento e o controle se a média verdadeira for diferente do controle verdadeiro. Mesmo uma estimativa aproximada do desvio padrão na Fórmula 2 pode ser útil no planejamento de um experimento. Substituir o 16 por 21 na fórmula acima para aumentar a potência para 90%.

Uma fórmula mais conservadora para o tamanho da amostra (com 90% de potência) foi sugerida (Wheeler 1974):

![image](https://user-images.githubusercontent.com/27368585/154770520-9489439c-1b1a-4492-a915-ad5c6a9ae38b.png)

Onde r é o número de variantes (assumido como aproximadamente igual em tamanho). A fórmula é uma aproximação e intencionalmente conservadora para explicar vários problemas de comparação ao conduzir uma análise de variância com o fator de múltiplas variantes (Wheeler 1975).

**Figura 4: Confiança do resultado**

![image](https://user-images.githubusercontent.com/27368585/154770580-e4a728f3-c53d-4538-bbea-cdfd3bd07d64.png)

Fonte: autor, 2019

#### 2.2.1 A escolha do OEC deve ser feita com antecedência.

Ao executar experimentos, é importante decidir com antecedência o OEC, uma comparação planejada, um objetivo. Caso contrário, há um risco aumentado de encontrar o que parece ser resultados significativos por acaso (Keppel et al. 1992).

### 2.3 Efeito dos robôs nos resultados experimentais

Os robôs podem introduzir distorções significativas nas estimativas, o suficiente para tornar valiosas as suposições. Para fins de experimentação, é especialmente importante remover alguns tipos de robôs, aqueles que interagem com o ID do usuário. Para alguns sites, acredita-se que os robôs ofereçam até metade das exibições de página no site (Kohavi et al. 2004). Como muitos robôs têm as mesmas características que os usuários humanos, é difícil delinear claramente entre os dois.

#### 2.3.1 Robôs que rejeitam cookies

É recomendado excluir solicitações não identificadas na análise, para que os robôs que rejeitam cookies não façam parte dos resultados experimentais (Kohavi 2003). Se a atribuição de tratamento e a coleta de dados forem baseadas apenas em usuários com um ID de usuário armazenado no cookie, esses robôs não serão contados no número de usuários ou nos dados coletados no comportamento do usuário.

#### 2.3.2 Robôs que aceitam cookies

Se um robô aceita cookies e não os exclui, o efeito pode ser profundo, especialmente se o robô tiver um grande número de ações no site. Geralmente há um número relativamente pequeno desses robôs, mas sua presença no tratamento ou controle pode influenciar seriamente a comparação. Qualquer teste de hipótese comparando tratamento e controle quando esses robôs estão presentes pode ser muito enganador. Esses robôs não apenas influenciam a estimativa do efeito, mas também aumentam o desvio padrão de muitas métricas, reduzindo assim a potência (Kohavi 2003). 

### 2.4 Configuração on-line

Várias medidas para experiências controladas básicas são possíveis em uma configuração on-line (web ou app).

#### 2.4.1 Aceleração do tratamento

Um experimento pode ser iniciado com uma pequena porcentagem de usuários atribuídos ao(s) tratamento(s) e em seguida, essa porcentagem pode ser aumentada gradualmente. Por exemplo, se você executar um teste A/B a 50%/50%, poderá começar executando em 1% dos usuários e aumentar o tratamento para 2,5% a 5% a 10% a 50%. Em cada etapa, que pode durar, por exemplo, algumas horas, você pode analisar os dados para garantir que não haja problemas negativos com o tratamento antes de expô-los a mais usuários (Kohavi et al. 2004). O fator quadrado na fórmula do poder implica que esses erros podem ser detectados rapidamente em pequenas populações e o experimento pode ser abortado antes que muitos usuários sejam expostos ao tratamento ruim (Kohavi et al. 2004).

#### 2.4.2 Automação

Uma vez que uma organização possui um OEC claro, ela pode executar experimentos para otimizar determinadas áreas passíveis de pesquisa automática. Por exemplo, os slots na página inicial da Amazon são otimizados automaticamente (Kohavi et al. 2004). Se for necessário tomar decisões rapidamente, elas podem ser tomadas com níveis mais baixos de confiança, porque o custo do erro é menor (Maron and Moore 1994).

#### 2.4.3 Migrações de software

Os experimentos podem ser usados para ajudar na migração de software. Se um recurso ou sistema estiver sendo migrado para um novo back-end, novo banco de dados ou um novo idioma, mas não for esperado alterar os recursos visíveis ao usuário, um teste A/B poderá ser executado com o objetivo de manter a hipótese nula, que é aquela onde as variantes não são diferentes. Uma migração não deve ser declarada concluída, se um teste A/B mostrar diferenças significativas nas principais métricas. Como o objetivo é manter a hipótese nula, é crucial garantir que o experimento tenha poder estatístico suficiente para realmente rejeitar a hipótese nula, caso seja falsa.

### 2.5 Limitações

Apesar das vantagens significativas que os experimentos controlados oferecem em termos de causalidade, eles possuem limitações que precisam ser entendidas (Rossi et al. 2003, p. 252–262; Weiss 1997). Algumas limitações que encontramos certamente valem a pena serem observadas.

1. Métricas quantitativas, mas sem explicações. É possível saber qual variante é melhor e por quanto, mas não por quê. No exemplo da Figura 5 o resultado do teste apontou para o botão vermelho, mas se isso foi influenciado pelo destaque da cor, pela harmonia da paleta de cores ou do contraste, não há como comprovar em experimentos controlados (Nielsen 2005).
2. Um OEC incompleto. Quando criando um OEC ele deve ser composto por todos os impactos que o teste pode causar (Quarto-vonTivadar 2006; Nielsen 2005), por exemplo um usuário ser exposto a uma modal pedindo cadastro do seu email, deve ser incluso no OEC a possibilidade os abandonos da página.
3. Efeitos a curto prazo contra efeitos a longo prazo. Experimentos controlados medem o efeito no OEC durante o período de experimentação, geralmente algumas semanas (Nielsen 2005). Metas de longo prazo devem fazer parte do OEC. 
4. Efeitos de primazia e novidade. Esses são efeitos opostos que precisam ser reconhecidos. Se você alterar a navegação em um site, os usuários poderão ser menos eficientes até se acostumarem com a nova navegação, dando assim uma vantagem inerente ao controle. Por outro lado, quando um novo design ou recurso é introduzido, alguns usuários o investigam, clicam em todos os lugares e assim, introduzem um viés de “novidade”, explicado pelo efeito de Hawthorne (Adair 1984). As preocupações de primazia e novidade implicam que alguns experimentos precisam ser realizados por várias semanas. Uma análise que pode ser feita é calcular o OEC apenas para novos usuários das diferentes variantes, pois elas não são afetadas por nenhum dos fatores.
5. Os recursos devem ser implementados. Um experimento controlado ao vivo precisa expor alguns usuários a um tratamento diferente do site atual (controle). O recurso pode ser um protótipo que está sendo testado em uma pequena porção ou pode não abranger todos os casos (Nielsen 2005) (por exemplo, o experimento pode excluir intencionalmente 20% dos tipos de navegadores que iriam exigir testes significativos). No entanto, o recurso deve ser implementado e ter qualidade suficiente para expor os usuários a ele.
6. Lançamento de eventos e anúncios de mídia. Se houver um grande anúncio sobre um novo recurso, de modo que o recurso seja anunciado à mídia, todos os usuários precisarão vê-lo (Moran 2007).

**Figura 5: Variante vencedora**

![image](https://user-images.githubusercontent.com/27368585/154770832-91b7e140-c141-4d68-b4de-25ca10565049.png)

Fonte: autor

### 2.6 Explorar os dados

Um experimento controlado fornece mais do que apenas a informação sobre se a diferença nos OECs é estatisticamente significativa (Linden 2006b). Geralmente, são coletados dados ricos que podem ser analisados usando técnicas de aprendizado de máquina e mineração de dados. Por exemplo, um experimento não mostrou diferença significativa no geral, mas uma população de usuários com uma versão específica do navegador foi significativamente pior para o tratamento.

### 2.7 Cultura e negócios

#### 2.7.1 Concordar com o OEC antecipadamente

Um dos poderes das experiências controladas é que ele pode medir objetivamente o valor de novos recursos para os negócios (Linden 2006a). No entanto, ele serve melhor a esse propósito quando as partes interessadas concordam em como uma experiência deve ser avaliada antes da execução do experimento.

Embora essas recomendações possam parecer óbvias, elas raramente são aplicadas porque a avaliação de muitos recursos on-line está sujeita a vários objetivos, muitas vezes concorrentes. Podem ser medidas combinadas, que transformam vários objetivos, na forma de observações experimentais, em uma única métrica. Ao formular um OEC, uma organização é forçada a medir o valor de várias entradas e decidir sua importância relativa (Roy 2001). Uma boa técnica é avaliar o valor da vida útil dos usuários e de suas ações. Por exemplo, uma pesquisa de um novo usuário pode valer mais do que uma pesquisa adicional de um usuário existente. Embora uma métrica única não seja necessária para a execução de experimentos, esse trabalho inicial e duro pode alinhar a organização e esclarecer metas.

#### 2.7.2 Cuidado com o lançamento de recursos que “não prejudicam” os usuários

Quando um experimento não produz diferença estatisticamente significante entre as variantes, isso pode significar que realmente não há diferença entre as variantes ou que o experimento não tem poder suficiente para detectar a mudança (Peterson 2004). Diante de um resultado "sem diferença significativa", às vezes é tomada a decisão de iniciar a mudança de qualquer maneira "porque não prejudica nada". É possível que o experimento seja negativo, mas com pouca potência.

#### 2.7.3 Medir os custos de manutenção do recurso

Um experimento pode mostrar uma diferença estatisticamente significante entre as variantes, mas optar por iniciar a nova variante ainda pode não ser justificado devido a problemas de manutenção. Um pequeno aumento no OEC pode não compensar o custo de manutenção do recurso (Peterson 2004).

#### 2.7.4 Mudar para uma cultura orientada a dados

A execução de algumas experiências on-line pode fornecer excelentes informações sobre como os clientes estão usando um recurso. A realização de experimentos frequentes e o uso de resultados experimentais como entrada principal para as decisões da empresa e o planejamento de produtos podem ter um impacto dramático na cultura da empresa. Como Mike Moran disse em seu livro “Faça errado rapidamente” (Moran 2007). As empresas de software que vendem softwares clássicos desenvolveram uma cultura em que as características são completamente projetadas antes da implementação. No mundo da web, podemos integrar o feedback do cliente diretamente através de protótipos e experimentação. Se uma organização fez um trabalho árduo para concordar com um OEC e examinou um sistema de experimentação, a experimentação pode fornecer dados reais e levar a cultura a atingir objetivos compartilhados (Keppel et al. 1992).

## 3. Conclusão

Os experimentos controlados neutralizam variáveis que podem gerar confusão, distribuindo-as igualmente sobre todos os valores através de atribuição aleatória (Keppel et al. 1992), estabelecendo assim uma relação causal entre as mudanças feitas nas diferentes variantes e as medidas de interesse, incluindo o Critério de Avaliação Geral (OEC). O uso de técnicas de mineração de dados nessa configuração pode fornecer informações extremamente valiosas, como a identificação de segmentos que se beneficiam de um recurso introduzido em um experimento controlado, levando a um ciclo virtuoso de melhorias nos recursos e melhor personalização. A descoberta do conhecimento e a mineração de dados fornecem insights (Thomke 2001).

Atualmente, os recursos de software dos produtos são geralmente determinados pela mesma maneira que a medicina foi prescrita antes da Segunda Guerra Mundial: por pessoas que eram consideradas especialistas, não usando métodos científicos, como experimentos controlados. Hoje podemos fazer melhor, especialmente com o acesso ao comportamento do cliente.

Muitas organizações têm gerentes fortes, com opiniões fortes, mas sem dados, concordamos e acreditamos que as empresas podem acelerar a inovação por meio da experimentação, porque são as experiências do cliente que importam e devemos ouví-los.

## Referências

Box GEP, Hunter JS, Hunter WG (2005) Statistics for experimenters: design, innovation, and discovery,2nd edn. Wiley, ISBN: 0471718130

Boos DD, Hughes-Oliver JM (2000) How large does n have to be for Z and t intervals? Am Statist 121–128. Disponível em: https://sci-hub.se/10.2307/2686030

Adair, J. G. (1984). The Hawthorne effect: A reconsideration of the methodological artifact. Journal of Applied Psychology, 69(2), 334–345. https://sci-hub.se/10.1037/0021-9010.69.2.334

Kaplan RS, Norton DP (1996) The balanced scorecard: translating strategy into action. Harvard BusinessSchool Press, ISBN: 0875846513

Keppel G, Saufley WH, Tokunaga H (1992) Introduction to design and analysis, segunda edição. W.H. Freemanand Company

Kohavi R, Parekh R (2003) Ten supplementary analyses to improve e-commerce web sites. WebKDD. Disponível em: https://pdfs.semanticscholar.org/2bd4/abce170d4bcf5e3e03ac076f28697ae4e303.pdf

Kohavi R, Round M (2004) In: Sterne J (ed) analista frontend da Amazon.com. Santa Barbara, CA. Disponível em: http://ai.stanford.edu/~ronnyk/emetricsAmazon.pdf

Kohavi R et al (2004) Lessons and challenges from mining retail e-commerce data. Machine Learn. Disponível em: http://ai.stanford.edu/~ronnyk/lessonsInDM.pdf

Linden G (2006a) Early Amazon: shopping cart recommendations. Geeking with Greg. Disponível em: http://glinden.blogspot.com/2006/04/early-amazon-shopping-cart.html

Linden G (2006b), Make data useful. Disponível em: https://vdocuments.mx/make-data-useful-by-greg-linden-amazoncom.html

Maron O, Moore AW (1994) Hoeffding races: accelerating model selection search for classification and function approximation. Disponível em: https://www.semanticscholar.org/paper/Hoeffding-Races%3A-Accelerating-Model-Selection-for-Maron-Moore/2b31b23e0cb60fbc857728d6b16bc5d61f71a643

Marks HM (2000) The progress of experiment: science and therapeutic reform in the united states, 1900–1990. Cambridge University Press, ISBN: 978-0521785617

Mason RL, Gunst RF, Hess JL (1989) Statistical design and analysis of experiments with applications to engineering and science. Wiley, ISBN: 047185364X

Moran M (2007) Do it wrong quickly: how the web changes the old marketing rules. IBM Press, ISBN:0132255960

Nielsen J (2005) Putting A/B testing in its place. Useit.com Alertbox. Disponível em: http://www.useit.com/alertbox/20050815.html

Peterson ET (2004) Web analytics demystified: a marketer’s guide to understanding how your web site affects your business. Celilo Group Media and CafePress, ISBN: 0974358428

Quarto-vonTivadar J (2006) AB testing: too little, too soon. Future Now. Disponível em: Disponível em https://persuasion.typepad.com/architect/2006/03/ab_testing_too_.html

Rossi PH, Lipsey MW, Freeman HE (2003) Evaluation: a systematic approach, sétima edição. Sage Publications, Inc., ISBN: 0-7619-0894-3

Roy RK (2001) Design of experiments using the taguchi approach: 16 steps to product and process improvement. Wiley, ISBN: 0-471-36101-1

Thomke S (2001) Enlightened experimentation: the new imperative for innovation, Feveiro 2001. Disponível em: https://hbr.org/2001/02/enlightened-experimentation-the-new-imperative-for-innovation

van Belle G (2002) Statistical rules of thumb. Wiley, ISBN: 0471402273. Disponível em: http://vanbelle.org/presentations/CHSTalkNoPictures.pdf

Weiss CH (1997) Evaluation: methods for studying programs and policies, segunda edição. Prentice Hall, ISBN: 0-13-309725-0

Wheeler RE (1974) Portable power. Technometrics 16:193–201. Disponível em: https://sci-hub.se/10.1080/00401706.1974.10489174

Wheeler RE (1975) The validity of portable power. Technometrics 17(2):177–179. Disponível em: https://sci-hub.se/10.1080/00401706.1975.10489300













