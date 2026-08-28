# Farol do Portfólio

Protótipo de painel para um investidor equity acompanhar 10 empresas do portfólio, em dois níveis de profundidade — mais um esboço técnico de referência para o nível de dados por baixo dos dois.

Site estático, sem backend e sem dependências externas além das fontes do Google Fonts — três páginas HTML com CSS e JavaScript embutidos, sem build.

## Os dois níveis

- **[`index.html`](https://malneto.github.io/farol-portfolio/) — Farol, nível 1, estratégia macro.** KPIs do portfólio (capital investido, valuation, MOIC, LTV/CAC médio ponderado, empresas em alerta), a grade das 10 empresas com status e gargalo principal, evolução de MRR e CAC vs. LTV por empresa, e a recomendação (Investir mais / Manter / Observar / Reestruturar / Sair) com justificativa.
- **[`auditoria.html`](https://malneto.github.io/farol-portfolio/auditoria.html) — Ação & Auditoria, nível 2, por empresa.** Financeiro detalhado (ARR, margem bruta, ARPU, payback de CAC, NRR, caixa, queima mensal), contas a pagar/receber em aberto, documentos & conciliação contábil (balancete cruzado contra extrato bancário via Open Finance, com divergências sinalizadas), tabela mês a mês e plano de ação com dono e prazo por gargalo. Cada empresa do Farol linka direto para o seu nível 2.
- **Fora de escopo por ora:** o nível 3 — extrato linha a linha, folha de pagamento, dados de trabalhadores individuais. É o dado no nível mais baixo possível e não entra neste protótipo.

## Referência técnica

[`arquitetura.html`](https://malneto.github.io/farol-portfolio/arquitetura.html) não é uma tela do sócio-investidor — é o esboço de engenharia de como a camada de dados por baixo dos dois níveis acima funcionaria: as três fontes possíveis (extrato bancário via Open Finance, balancete/DRE lido por IA, planilha manual como fallback), como seriam conciliadas entre si, e por onde pilotar primeiro.

## Dados

Todos os números são **fictícios**, criados para validar o formato com o sócio-investidor antes de plugar dados reais. `index.html` e `auditoria.html` usam exatamente a mesma base de dados (mesmas seeds do gerador), então os números batem entre as duas páginas para a mesma empresa.

## Próximos passos possíveis

- Trocar o gerador de dados fictícios (`genSeries`) por uma fonte real, seguindo o esboço em `arquitetura.html`.
- Plugar extrato bancário via Open Finance (Pluggy/Belvo) nas empresas em "Observar"/"Reestruturar"/"Sair", para conferir caixa reportado contra caixa real.
- Ligar a leitura de documentos (hoje simulada) a um backend real de extração por IA.
- Avaliar se/quando faz sentido abrir o nível 3 (extrato linha a linha, folha, trabalhadores) para alguma empresa específica.
- Histórico de rodadas / cap table por empresa.
