*PROMPT 1*

Conecte-se ao projeto Power BI aberto via MCP. Antes de qualquer ação, leia o
arquivo de contrato do projeto na pasta (Cafeteria_Global_MD / README) e siga-o
à risca: não invente campos nem regras, não renomeie medidas existentes e use
apenas os nomes exatos definidos lá. Vamos trabalhar com as skills
$powerbi-dax-ultra e $dataviz-radar-ultra. Confirme que está conectado e que
leu o contrato.

*PROMPT 2*

Continue com $powerbi-dax-ultra.

Antes de qualquer medida, garanta a fundação do modelo em esquema estrela e
aplique diretamente as correções seguras:

- desative a Data/Hora automática e remova as LocalDateTable_*; ligue as datas
  na dw dim_calendario e marque-a como tabela de datas;
- garanta os relacionamentos ativos, muitos-para-um, unidirecionais dim→fato,
  incluindo dw dim_concorrente[loja_referencia_id] → dw dim_loja[loja_id];
- nas fatos mensais, relacione mes → dw dim_calendario[data];
- nenhuma relação fato-a-fato.

Explique a cardinalidade de cada relação, teste filtros combinados de período,
região e loja, e confirme que não há caminhos ambíguos. Só então seguimos para
as medidas.


*PROMPT 3*
Use $powerbi-dax-ultra.

Analise o projeto Power BI aberto considerando este contexto:

Negócio: Cafeteria Global — rede de 17 cafeterias em vários países
Público: diretoria e gestores regionais
Objetivo: decidir onde investir para capturar receita potencial ainda não realizada
Período relevante: diário, com leitura mensal e tendência de 30 dias
Entidades principais: lojas, concorrentes, mercado
KPIs esperados: receita, margem, gap potencial, percentual não capturado, distância competitiva

Antes de alterar o modelo, transforme o objetivo em perguntas de negócio claras.
Identifique o que o gestor precisa perceber, investigar e decidir. Não invente
regras ou campos ausentes. Apresente um diagnóstico curto e avance direto.

Perguntas centrais:
- Onde existe potencial de mercado ainda não capturado?
- Qual loja combina maior oportunidade com bom desempenho?
- Onde a pressão competitiva exige uma resposta?


*PROMPT 4*
Continue com $powerbi-dax-ultra.

Com o modelo já reconciliado e validado, crie as medidas seguindo o contrato
do projeto e usando os nomes exatos definidos lá. Antes de escrever DAX, defina
cada KPI: significado, fórmula, granularidade, unidade, filtros, comparador e
tratamento de vazios.

Crie em camadas e aplique diretamente no modelo:

1. Base: Vendas Liquidas, Margem Percentual, Venda Potencial.

2. Derivadas: Gap Potencial (Venda Potencial - Vendas Liquidas) e
   Percentual Não Capturado (Gap Potencial / Venda Potencial).

3. Inteligência temporal: Evolucao Vendas 30d (janela móvel de 30 dias
   encerrada na maior data do contexto vs os 30 dias anteriores).

4. Contexto e localização: concorrentes no entorno, evolução mensal,
   distância média/mínima e concorrente mais próximo.

5. Textos de exibição e tooltips (dicas de ferramenta). Prepare as medidas
   que vão compor os tooltips dos mapas, começando pela identificação da
   entidade e depois os KPIs em ordem de decisão:
   - Mapa Executivo: Loja analisada, Gap Potencial, Percentual Não Capturado,
     Vendas Liquidas, Margem Percentual, Ticket Médio, Taxa de Atraso.
   - Pressão Competitiva: Loja analisada, Gap Potencial da loja de referência,
     Distância Média, Distância Mínima, Vendas Liquidas da loja de referência.

Regras: use DIVIDE e VAR; formate moeda, percentual e distância no modelo;
não use FORMAT em medidas numéricas destinadas a gráficos; não esconda regra
de negócio em formatação. Ao final, liste as medidas criadas por camada com a
fórmula e o formato de cada uma.


*PROMPT 6*
Continue com $powerbi-dax-ultra.

Antes de criar o dashboard, valide as medidas em consultas DAX. Teste:
- total geral;
- uma loja conhecida;
- múltiplas lojas;
- um período fechado (ex.: julho/2026);
- período sem dados;
- divisão por zero (Percentual Não Capturado com potencial vazio);
- filtros combinados de região, mês e loja;
- coerência dos percentuais;
- comparação temporal (Evolucao Vendas 30d).

Reconcilie Vendas Liquidas e Gap Potencial com a fonte. Corrija qualquer
divergência. Ao final, entregue o contrato para a camada visual: medidas
aprovadas, formatos, filtros permitidos, comportamento esperado das
interações e limitações conhecidas.


*PROMPT 7*
Continue com $dataviz-radar-ultra. O mapa ArcGIS da página "Mapa Executivo"
já está pronto e validado. Agora construa o RESTANTE da mesma página, sem
tocar no mapa, usando só medidas do contrato validado.

Header executivo (faixa escura, largura total no topo):
- Título "📊 Painel de Indicadores" + subtítulo "Potencial geográfico -
  Receita, margem e oportunidades"
- Bloco à direita "CAFETERIA GLOBAL" + [Data Atualizacao Painel]

Filtros (segmentações logo abaixo do header): Região (dw dim_loja[regiao]),
Mês (dw dim_calendario[ano_mes]) e Loja (dw dim_loja[nome_loja]).

Três cards (novo) na faixa de KPIs:
- "Receita líquida no período" = [Receita líquida no período], com
  [Tendencia Vendas 30d] como contexto abaixo
- "Percentual das vendas após custos" = [Percentual das vendas após custos]
- "Venda estimada ainda não capturada" = [Venda estimada ainda não capturada],
  com [Percentual Não Capturado - Exibição] abaixo

Gráfico de barras "Vendas líquidas por loja": eixo dw dim_loja[nome_loja],
valor [Vendas Liquidas], ordenado decrescente, à esquerda do mapa.

Layout limpo e executivo: grade consistente, cores semânticas, tudo alinhado.
Configure as interações para que Região, Mês e Loja filtrem cards, ranking e
mapa em conjunto. Reserve pra mim só aplicar alterações externas e salvar.


*PROMPT 8*
Continue com $dataviz-radar-ultra. A página "Mapa Executivo" está pronta.
Crie agora a segunda página, "Pressão Competitiva", respondendo
"Onde a pressão competitiva ameaça nosso potencial?", usando só medidas
do contrato validado e o mesmo padrão visual da página 1.

Header executivo: título "📊 Painel de Indicadores" + subtítulo
"Pressão competitiva - Concorrência, proximidade e risco"; bloco
"CAFETERIA GLOBAL" + [Data Atualizacao Painel] à direita.

Filtros: Região (dw dim_loja[regiao]), Loja (dw dim_loja[nome_loja]) e
Mês (dw dim_calendario[ano_mes]).

Três cards (novo):
- "Concorrentes no entorno no mês" = [Concorrentes no entorno no mês],
  com [Tendencia Concorrentes 30d] abaixo
- "Concorrente mais próximo" = [Concorrente Mais Próximo] + [Distância Mínima]
- "Venda estimada ainda não capturada" = [Venda estimada ainda não capturada]

Gráfico de barras "Distância média por marca": eixo dw dim_concorrente[marca],
valor [Distância Média], à esquerda do mapa.

Mapa ArcGIS (esriVisual, sem Azure/legado), mapa de calor dos concorrentes:
- Localização: dw dim_concorrente[marca]
- Latitude/Longitude: dw dim_concorrente[latitude] / [longitude]
- Tamanho: [Concorrentes Entorno Mes]
- Tooltip: Loja analisada, Gap Potencial Loja Referencia, Distância Média,
  Distância Mínima, Vendas Liquidas Loja Referencia

Reserve pra mim só aplicar alterações externas e salvar.


*PROMPT 9*
Continue com $dataviz-radar-ultra. No mapa de concorrentes da página
"Pressão Competitiva", ao selecionar uma única loja o ArcGIS não reenquadra
nos concorrentes locais porque a medida de tamanho está preenchida para todas
as coordenadas globais. Ajuste a medida para retornar vazio nos concorrentes
que não pertencem à loja selecionada (respeitando a relação
dw dim_concorrente[loja_referencia_id] → dw dim_loja[loja_id]), de modo que,
com uma única loja, o mapa mostre e enquadre apenas os concorrentes daquela loja.
Mantenha 112 no total geral e não altere os cards.