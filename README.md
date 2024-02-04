# Instagram Engagement Analysis

Projeto criado com o objetivo de gerar insights diagnósticos sobre as publicações que geram mais engajamento no Instagram de uma determinada empresa. Portanto, com o intuito de determinar o tipo de postagem que mais atrai o público dessa empresa, fazem-se as seguintes observações:

- Há a disponiblidade de uma base de dados com tipo de postagem (foto, reels, vídeo e IGTV)
- Há nela uma coluna que indica se há pessoas ou não na postagens
- Coluna que indica se trata-se de um Carrossel de postagens ou não
- Coluna que indica é uma postagem feita para uma campanha ou não
- Tags atribuídas de acordo com o assunto da postagem
- Colunas de interações, curtidas, comentários e visualizações
- Coluna de data da postagem
  
**O foco é analisar as colunas de curtidas, comentários, interações e tags para observar o melhor engajamento.**

Dessa forma, os seguintes passos foram adotados:
1. Importação da base de dados
2. Visualização da base de dados
3. Tratamento de erros
4. Análise para compreender a relação de curtidas, comentários e interações com o engajamento
5. Análise para compreender a relação das tags com o engajamento

Com a lista de passos em mãos, o desenvolvimento do código seguiu o seguinte raciocínio:<br/>
I) importação da biblioteca necessária para a análise: Pandas<br/>
II) leitura do arquivo<br/>
III) visualização da tabela<br/>
IV) retirada de colunas desnecessárias<br/>
V) tratamento da base ao atribuir o valor N para a coluna Carrossel que possuía muitos valores nulos que impactariam na análise<br/>
VI) tratamento da base ao fazer o mesmo do passo anterior para a coluna de Tags <br/>
VII) descrição estatística da base<br/>
VIII) visualização do comportamento das curtidas e comentários em gráficos de dispersão. Observa-se que não há um padrão notável, fazendo com que a análise das demais colunas sejam necessária<br/>
IX) análise inicial já demonstra a importância de pessoas e campanhas nas postagens, uma vez que as 5 melhores em curtidas tem pessoas e campanhas nelas, enquanto as 5 piores não tem nenhum dos 2 atributos<br/>
X) o agrupamento das colunas, mostra que postagens com pessoas e campanhas tem realmente um desempenho muito superior, como se pode observar pelos valores médios na tabela abaixo:<br/>

<table border="1">
    <caption><b>Relação de pessoas com curtidas e comentários</b></caption>
    <tr>
        <th>Pessoas</th>
        <th>Curtidas</th>
        <th>Comentários</th>
    </tr>
    <tr>
        <td>Sim</td>
        <td>14.664,55</td>
        <td>230,50</td>
    </tr>
    <tr>
        <td>Não</td>
        <td>4.256,67</td>
        <td>52,83</td>
    </tr>
</table>

<table border="1">
    <caption><b>Relação de campanhas com curtidas e comentários</b></caption>
    <tr>
        <th>Campanhas</th>
        <th>Curtidas</th>
        <th>Comentários</th>
    </tr>
    <tr>
        <td>Sim</td>
        <td>18.173,27	</td>
        <td>279,95</td>
    </tr>
    <tr>
        <td>Não</td>
        <td>7.928,33	</td>
        <td>123,17</td>
    </tr>
</table>

XI) o resultado da união de publicações com pessoas e campanhas é demonstrado abaixo
<table border="1">
    <caption><b>Relação de campanhas e pessoas com curtidas e comentários</b></caption>
    <tr>
        <th>Pessoas</th>
        <th>Campanhas</th>
        <th>Curtidas</th>
        <th>Comentários</th>
    </tr>
    <tr>
        <td>Sim</td>
        <td>Sim</td>
        <td>19.405,35</td>
        <td>303,20</td>
    </tr>
    <tr>
        <td>Não</td>
        <td>Não</td>
        <td>3.937,50</td>
        <td>53,90</td>
    </tr>
     <tr>
        <td>Sim</td>
        <td>Não</td>
        <td>9.923,75</td>
        <td>157,80</td>
    </tr>
     <tr>
        <td>Não</td>
        <td>Sim</td>
        <td>5.852,50</td>
        <td>47,50</td>
    </tr>
</table>

XII) postagens no formato carroussel não tiveram bom desempenho comparativamente com as que não eram nesse formato
<table border="1">
    <caption><b>Relação de carrossel com curtidas e comentários</b></caption>
    <tr>
        <th>Carrossel</th>
        <th>Curtidas</th>
        <th>Comentários</th>
    </tr>
    <tr>
        <td>Sim</td>
        <td>11.817,88	</td>
        <td>140,38</td>
    </tr>
    <tr>
        <td>Não</td>
        <td>13.776,36</td>
        <td>208,57</td>
    </tr>
</table>

XIII) entre o tipo de postagem, fotos e reels tiveram desempenho superior

<table border="1">
    <caption><b>Relação de tipo de postagem com curtidas e comentários</b></caption>
    <tr>
        <th>Tipo</th>
        <th>Curtidas</th>
        <th>Comentários</th>
    </tr>
    <tr>
        <td>Foto</td>
        <td>13.341,14</td>
        <td>193,42</td>
    </tr>
    <tr>
        <td>Vídeo</td>
        <td>8.141,50</td>
        <td>166,83</td>
    </tr>
    <tr>
        <td>IGTV</td>
        <td>6.833,40</td>
        <td>133,60</td>
    </tr>
    <tr>
        <td>Reels</td>
        <td>14.873,00</td>
        <td>244,40</td>
    </tr>
</table>

XIV) utilização das funções split e explode para tratar a coluna de Tags<br/>
XV) tags que envolvam "Promoções", "Datas Comemorativas" e "Trends" são as de melhor desempenho

<table border="1">
    <caption><b>Relação de Tags com curtidas e comentários</b></caption>
    <tr>
        <th>Tags</th>
        <th>Curtidas</th>
        <th>Comentários</th>
    </tr>
    <tr>
        <td>Promoções</td>
        <td>27.458,33</td>
        <td>531,00</td>
    </tr>
    <tr>
        <td>Datas Comemorativas</td>
        <td>20.752,25</td>
        <td>343,50</td>
    </tr>
    <tr>
        <td>Trends</td>
        <td>20.024,00</td>
        <td>352,25</td>
    </tr>
</table>

XVI) ao fazer o agrupamento das colunas de Pessoas/Tags e Campanhas/Tags, observa-se que o desempenho da Tag "Promoções" e da Tag "Novos Produtos" chega a ser mais do que o dobro do que quando não há a associação das mesmas com Pessoas e Campanhas, respectivamente
<br/>

**Resumo de conclusões:**
- postagens com pessoas engajam muito mais do que aquelas que não possuem ninguém (10 mil curtidas)
- postagens em épocas de campanha também possuem um ótimo engajamento (5.3 mil curtidas)
- postagens que agregam pessoas e campanhas tem em média 19.4 mil curtidas
- carrossel não foi um diferencial para melhorar o engajamento da marca
- a média de curtidas sem carrossel é maior do que com. Portanto, sugere-se focar em outros tipos de publicação que gerem melhor engajamento
- sugere-se postar apenas vídeos que agreguem pessoas e campanhas, pois apesar de poucos,tiveram desempenho próximo ao das fotos. Os que não apresentaram ambos não tiveram um bom desempenho 
- IGTV mesmo com pessoas não agradou 
- em todas as tags, quando há pessoas envolvidas o desempenho foi muito melhor
- campanhas ajudam na divulgação da marca
- promoções tiveram um desempenho muito superior do que qualquer outra tag (é uma tag que pode resultar em custo para a empresa = avaliar se vale a pena)
- conteúdo que estão em trends também ajudam na divulgação
- para novos produtos, a inclusão de pessoas é essencial (o dobro de desempenho)
- não há dados para cravar que a tag "Loja" não é boa, pois não há publicações com pessoas ou campanha. Sugere-se testar ambas
