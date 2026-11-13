---
name: powerbi-dax-ultra
description: Diagnostica, transforma e modela dados para Power BI com rigor analitico. Use para Power Query, esquema estrela, relacionamentos e cardinalidade, tabela calendario, regras de negocio, criacao, correcao ou otimizacao de medidas DAX, inteligencia temporal e validacao do modelo semantico. Nao use como fluxo principal quando o pedido for apenas acabamento visual.
metadata:
  short-description: Modelagem, Power Query e DAX com rigor
---

# PowerBI DAX Ultra

Construa uma camada analitica confiavel antes de produzir o dashboard. Trate a pergunta de negocio, a granularidade, o modelo e as medidas como um unico sistema verificavel.

## Roteamento obrigatorio

- Leia [references/rigorous-modeling-and-dax.md](references/rigorous-modeling-and-dax.md) em todo trabalho substantivo.
- Leia tambem [references/cafeteria-global-playbook.md](references/cafeteria-global-playbook.md) quando encontrar o banco `cafeteria_global`, tabelas `dw dim_*` ou `dw fato_*`, ou quando o pedido mencionar Cafeteria Global.
- Para layout, mapas, estilo, tooltips ou acabamento, conclua primeiro a camada semantica e entregue o trabalho para `$dataviz-radar-ultra`.

## Contrato de execucao

Siga esta ordem sem pular etapas:

1. Traduza o pedido em pergunta de negocio, decisao, publico e periodo.
2. Inspecione fontes, colunas, tipos, nulos, duplicidades, chaves, granularidade e cobertura temporal.
3. Proponha ou aplique tratamentos no Power Query preservando rastreabilidade.
4. Modele em estrela, valide cardinalidade e direcao de filtro e elimine caminhos ambiguos.
5. Crie ou ajuste a tabela calendario e valide relacionamentos de data.
6. Formalize cada KPI antes do DAX: definicao, formula, grao, filtros, comparador, unidade e excecoes.
7. Crie medidas em camadas: base, derivadas, temporais, contexto e exibicao.
8. Valide em consulta DAX ou visuais simples antes de montar o visual final.
9. Registre alteracoes, evidencias, limitacoes e proximo passo.

## Portoes de qualidade

Nao avance se algum portao falhar:

- **Dados:** fonte, grao, chaves, tipos e problemas relevantes estao conhecidos.
- **Modelo:** relacoes sao justificadas, sem fato-com-fato e sem ambiguidade silenciosa.
- **Metrica:** regra de negocio e comportamento de filtro estao definidos.
- **Validacao:** totais, subtotais, filtros, vazios e periodos limite foram testados.
- **Entrega:** nomes, formatos, pasta de exibicao e documentacao permitem reproducao.

## Regras rigidas

- Nunca invente tabela, coluna, chave, regra ou meta. Inspecione ou marque a lacuna.
- Nunca apague registros problematicos silenciosamente. Prefira flag, motivo e contagem de impacto.
- Nao relacione duas fatos diretamente. Use dimensao conformada, ponte ou medida explicita.
- Use filtro unidirecional da dimensao para a fato. Bidirecional exige necessidade demonstrada e teste de ambiguidade.
- Use relacionamento muitos-para-um com chave unica no lado `1`; valide duplicidades antes de criar.
- Relacione datas pela coluna de data adequada ao grao. Use relacoes inativas para papeis alternativos e `USERELATIONSHIP` de forma explicita.
- Prefira medidas a colunas calculadas quando o resultado depende do contexto de filtro.
- Em DAX, prefira `DIVIDE`, `VAR`, nomes claros e retorno `BLANK()` quando zero nao representa ausencia.
- Explique qualquer uso de `REMOVEFILTERS`, `ALL`, `TREATAS`, `CROSSFILTER` ou `USERELATIONSHIP`.
- Formate numeros no modelo. Medidas textuais ficam reservadas a narrativa e status.
- Use nomes tecnicos simples; textos visiveis ao usuario devem estar em portugues correto.

## Operacao no Power BI

Quando houver conexao com o modelo aberto, liste tabelas, colunas, medidas e relacionamentos antes de alterar. Aplique mudancas diretamente por MCP, ferramentas do modelo semantico ou arquivos PBIP/TMDL quando disponiveis. Se a interface exigir consentimento, aplicacao de alteracoes externas ou salvamento do PBIX, diga exatamente qual acao humana resta.

Em PBIP/TMDL:

- preserve alteracoes existentes e nunca substitua o projeto inteiro;
- altere somente objetos identificados;
- mantenha backup ou recuperacao antes de mudancas estruturais;
- reabra ou aplique alteracoes externas e valide o modelo no Power BI Desktop.

## Entrega minima

Entregue sempre:

- diagnostico objetivo da base e da pergunta de negocio;
- desenho do modelo e justificativa das relacoes;
- medidas criadas ou alteradas, com definicao e formato;
- matriz de testes executados e respectivos resultados;
- riscos, lacunas e acoes manuais restantes;
- contrato de dados para a camada visual.
