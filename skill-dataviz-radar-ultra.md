---
name: dataviz-radar-ultra
description: Cria, revisa e otimiza dashboards Power BI modernos, clean e orientados a decisao. Use para arquitetura visual, escolha de graficos, KPIs, cards, filtros, mapas e ArcGIS, tooltips, interacoes, acessibilidade, tema, layout PBIR e QA visual. Exige medidas validadas e preserva acuracia; nao substitui modelagem ou DAX de negocio.
metadata:
  short-description: Visual executivo moderno e orientado a decisao
---

# DataViz Radar Ultra

Transforme medidas confiaveis em uma interface que permita ao gestor perceber sinal, contexto, causa e proxima acao em poucos segundos. "Radar" significa varredura orientada a decisao; nao obriga o uso de grafico radar.

## Roteamento obrigatorio

- Leia [references/design-system-and-visual-qa.md](references/design-system-and-visual-qa.md) em todo trabalho substantivo.
- Leia tambem [references/cafeteria-global-visual-playbook.md](references/cafeteria-global-visual-playbook.md) no projeto Cafeteria Global ou quando houver paginas de potencial geografico e pressao competitiva.
- Use [assets/radar-ultra-theme.json](assets/radar-ultra-theme.json) apenas como ponto de partida. Adapte a marca sem sacrificar contraste e semantica.
- Se medidas, relacionamentos ou granularidade nao estiverem validados, pause a camada final e chame `$powerbi-dax-ultra`.

## Contrato de execucao

Siga esta ordem:

1. Confirme publico, decisao, pergunta principal e medidas validadas.
2. Defina a narrativa: sinal executivo, contexto, diagnostico e detalhe.
3. Escolha cada visual pela pergunta, nao pela aparencia.
4. Aplique grade, hierarquia, tipografia, cores e formatos consistentes.
5. Configure filtros, interacoes, estados vazios, titulos dinamicos e tooltips.
6. Valide leitura, numeros, filtros, acessibilidade, desempenho e comportamento em gravacao/publicacao.

## Regras rigidas

- Nenhum visual entra sem responder a uma pergunta de negocio.
- Nao esconda regra de negocio em HTML, JavaScript, cor ou configuracao do visual.
- Prefira visuais nativos. Use ArcGIS quando a geografia muda a decisao e houver autorizacao do locatario.
- Nao use visual externo, CDN, API, imagem remota ou biblioteca de terceiros sem autorizacao explicita.
- Nunca use cor como unico portador de significado. Combine texto, icone, seta ou rotulo.
- Evite arco-iris, 3D, sombras pesadas, bordas excessivas, casas decimais irrelevantes e titulos gerados automaticamente.
- Use unidades e escalas honestas. Barras devem partir de zero salvo excecao explicada.
- Tooltips devem identificar primeiro a entidade analisada e depois os KPIs em ordem de decisao.
- Mapas precisam de latitude/longitude validadas, contexto geografico, legenda compreensivel e nivel de zoom util.
- Nao confunda mapa de calor analitico com decoracao. Raio e intensidade devem representar a concentracao relevante.

## Automacao pela IA

Quando PBIP/PBIR, MCP ou ferramentas do modelo estiverem disponiveis, execute diretamente o maximo seguro:

- criar e posicionar visuais nativos;
- vincular campos e medidas existentes;
- configurar formatos, titulos, tooltips e interacoes;
- aplicar tema e padroes de pagina;
- validar estrutura e gerar evidencias.

Reserve ao usuario somente consentimentos, selecoes visuais que a ferramenta nao exponha, aplicacao de alteracoes externas e salvamento do PBIX. Explique cada acao manual de forma reproduzivel para o video.

## Seguranca em PBIP/PBIR

- Preserve arquivos e objetos fora do escopo.
- Nao regrave paginas inteiras quando uma alteracao localizada basta.
- Valide o JSON/PBIR antes de pedir aplicacao de alteracoes externas.
- Mantenha caminho de recuperacao e informe o que foi alterado.
- Reabra, aplique alteracoes externas e teste interacoes no Power BI Desktop.

## Entrega minima

Entregue:

- pergunta respondida por cada visual;
- layout, tema e componentes aplicados;
- campos, medidas, tooltips e interacoes configurados;
- QA numerico e visual, incluindo estados filtrados e vazios;
- dependencias externas, consentimentos e custos potenciais;
- acoes manuais restantes e roteiro curto de reproducao.
