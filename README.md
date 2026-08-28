# Farol do Portfólio

Protótipo de painel para um investidor equity acompanhar as 10 empresas do portfólio: MRR, CAC, LTV, LTV/CAC, churn, runway, margem bruta, NRR e caixa — com recomendação (Investir mais / Manter / Observar / Reestruturar / Sair) e o gargalo principal de cada uma.

Site estático, sem backend e sem dependências externas além das fontes do Google Fonts — um único `index.html` com CSS e JavaScript embutidos.

## Ver o painel

**No ar:** https://malneto.github.io/farol-portfolio/

Ou abra `index.html` direto no navegador. O deploy é automático via GitHub Pages a cada push na branch `master`.

## O que tem

- **Visão geral**: KPIs do portfólio (capital investido, valuation atual, MOIC, LTV/CAC médio ponderado, empresas em alerta).
- **Grade das 10 empresas**: status, sparkline de MRR, métricas-chave e o gargalo principal — filtrável por status, ordenável por prioridade/crescimento/LTV-CAC/runway.
- **Detalhe por empresa** (URL própria via `#id-da-empresa`, ex. `#nortek`): evolução de MRR, CAC vs. LTV, indicadores financeiros (ARR, margem bruta, ARPU, payback de CAC, NRR, caixa, queima mensal), tabela mês a mês, gargalos, recomendação justificada e uma área de **documentos & conciliação contábil** (balancete simulado cruzado contra o extrato bancário, com divergências sinalizadas nas empresas mais problemáticas).
- **Tabela comparativa** completa, ordenável por qualquer coluna.

## Dados

Todos os números são **fictícios**, criados para validar o formato do painel com o sócio-investidor antes de plugar dados reais. Em produção, a fonte seria o reporte financeiro de cada investida (planilha mensal, integração contábil ou extrato via Open Finance para as posições que exigem mais confiança no caixa reportado).

## Camada de dados

[`arquitetura.html`](https://malneto.github.io/farol-portfolio/arquitetura.html) é o esboço de como a camada por baixo do painel funcionaria de verdade: as três fontes possíveis (extrato bancário via Open Finance, balancete/DRE lido por IA, planilha manual como fallback), como seriam conciliadas entre si, e por onde pilotar primeiro.

## Próximos passos possíveis

- Trocar o gerador de dados fictícios (`genSeries`) por uma fonte real, seguindo o esboço em `arquitetura.html`.
- Plugar extrato bancário via Open Finance (Pluggy/Belvo) nas empresas em "Observar"/"Reestruturar"/"Sair", para conferir caixa reportado contra caixa real.
- Ligar a leitura de documentos (hoje simulada no painel) a um backend real de extração por IA.
- Histórico de rodadas / cap table por empresa.
