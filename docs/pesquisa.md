# Processo de pesquisa

Este documento resume como o IDMRT-PP foi projetado, demonstrado, avaliado e refinado segundo a Design Science Research Methodology (DSRM) de Peffers et al. (2007). O artigo completo está em elaboração e não faz parte deste repositório.

## Sumário

- [Problema e objetivo](#problema-e-objetivo)
- [Requisitos](#requisitos)
- [Escopo](#escopo)
- [Casos de uso](#casos-de-uso)
- [Critérios de avaliação](#critérios-de-avaliação)
- [Episódios de demonstração e avaliação](#episódios-de-demonstração-e-avaliação)
- [Resultado da avaliação da v1.0](#resultado-da-avaliação-da-v10)
- [Refinamento: da v1.0 para a v2.0](#refinamento-da-v10-para-a-v20)
- [Apreciação por especialista](#apreciação-por-especialista)
- [Princípios de projeto](#princípios-de-projeto)
- [Limitações e trabalhos futuros](#limitações-e-trabalhos-futuros)

## Problema e objetivo

**Pergunta de pesquisa:** como estruturar um instrumento de diagnóstico replicável que avalie a maturidade dos recursos técnicos de uma empresa de pequeno porte, simples o suficiente para ser autoaplicado e detalhado o bastante para orientar decisões de alocação de recursos na jornada de organização da IA?

**Lacunas na literatura que motivam o artefato:**
1. **Predomínio de estudos descritivos:** a literatura explica a adoção de IA, mas não entrega um método replicável de autoaplicação.
2. **Assimetria de porte:** os modelos de maturidade e de capacidades foram validados em organizações de médio e grande porte.
3. **Falta de granularidade:** os instrumentos existentes cobrem estratégia, cultura e governança ao mesmo tempo, sem diagnosticar especificamente os recursos técnicos que a alocação exige.

## Requisitos

### Funcionais

| Código | Requisito | Desde |
|---|---|---|
| RF01 | Apresentar os 20 itens agrupados por dimensão, com os descritores da escala visíveis | 1.0 |
| RF02 | Registrar cada resposta na escala de 0 a 3, incluindo "não sei" | 1.0 |
| RF03 | Calcular automaticamente a média de cada dimensão | 1.0 |
| RF04 | Converter cada média no nível de maturidade pelas faixas fixas | 1.0 |
| RF05 | Ordenar as dimensões pela regra de priorização, com critério de desempate | 1.0 |
| RF06 | Sinalizar à parte as restrições bloqueantes e os itens "não sei" | 1.0 |
| RF07 | Exibir as recomendações do nível identificado em cada dimensão | 1.0 |
| RF08 | Gerar o relatório em formato imprimível ou exportável | 1.0 |
| RF09 | Registrar a data da aplicação para comparar aplicações sucessivas | 1.0 |
| RF10 | Exibir o aviso de consistência, sem bloquear a geração, e registrar no relatório que ele apareceu | 2.0 |
| RF11 | Sinalizar as dimensões de nível limite (com as recomendações do nível vizinho) e a ordem pouco definida | 2.0 |
| RF12 | Exibir a regra de priorização, o critério de desempate e a definição de restrição bloqueante | 2.0 |
| RF13 | Coletar utilidade percebida, decisão e dificuldades, e exportá-las com as respostas em formato aberto | 2.0 |

### Não funcionais

| Código | Requisito |
|---|---|
| RNF01 | **Autoaplicação:** o preenchimento não exige conhecimento especializado nem consultoria |
| RNF02 | **Tempo:** o preenchimento completo leva até uma hora, em sessão única |
| RNF03 | **Linguagem:** itens e recomendações sem jargão técnico |
| RNF04 | **Determinismo:** as mesmas respostas produzem sempre o mesmo diagnóstico |
| RNF05 | **Baixo custo:** funciona sem software pago ou especializado |
| RNF06 | **Transparência:** faixas e regra de priorização documentadas e acessíveis ao usuário |
| RNF07 | **Aderência à alocação:** a saída serve diretamente como insumo da etapa de alocação de recursos |

## Escopo

O que o instrumento **não** faz, por decisão de recorte da pesquisa:
- avaliar estratégia, cultura, governança, ética ou conformidade regulatória;
- recomendar fornecedores ou produtos, ou estimar custos e retorno sobre o investimento;
- verificar de forma independente o que o respondente declara;
- substituir o plano de alocação de recursos, do qual ele é apenas o insumo.

## Casos de uso

| Código | Caso de uso | Ator principal |
|---|---|---|
| UC01 | Responder o autodiagnóstico | Gestor |
| UC02 | Calcular o perfil de maturidade (sem diagnóstico se o preenchimento estiver incompleto) | Instrumento |
| UC03 | Gerar o relatório | Instrumento |
| UC04 | Definir prioridades de alocação | Gestor |
| UC05 | Reaplicar e acompanhar a evolução | Gestor |
| UC06 | Avaliar o artefato | Pesquisador e especialista |

## Critérios de avaliação

Os critérios foram definidos **antes** da demonstração, para comparar o desempenho com metas fixadas de antemão.

| Critério | Requisitos | Condição de atendimento |
|---|---|---|
| C1. Tempo de aplicação | RNF02 | Preenchimento completo em até uma hora |
| C2. Clareza e autoaplicação | RNF01, RNF03 | Concluído sem intervenção do aplicador e sem dúvidas que alterem a forma de responder |
| C3. Determinismo | RNF04 | Respostas idênticas geram relatório idêntico, que coincide com o cálculo manual |
| C4. Estabilidade | Objetivo 4 | Mesmo nível em todas as dimensões e mesma primeira prioridade entre aplicações |
| C5. Acionabilidade | RF05 a RF07 | (a) Prioridades e recomendações geradas; (b) recomendações julgadas úteis pelo respondente |
| C6. Aderência à alocação | RNF07 | (a) Relatório com prioridades, restrições bloqueantes e origem das ações; (b) o gestor usa a saída para decidir |
| C7. Transparência e custo | RNF05, RNF06 | Execução sem software pago nem instalação; faixas e regra de priorização visíveis |

## Episódios de demonstração e avaliação

| Episódio | Natureza | Versão | Para que serviu |
|---|---|---|---|
| Aplicação real | Empresa de engenharia civil de pequeno porte, um respondente, com orientação do aplicador | 1.0 | Verificar o fluxo completo em uso real |
| Reaplicação | Mesmo respondente, mesmo dia, sem orientação | 1.0 | Observar, de forma exploratória, a estabilidade e o efeito da orientação |
| Variante sintética | Respostas hipotéticas | 1.0 e 2.0 | Exercitar as regras que o caso real não acionou: restrição bloqueante, desempate e "não sei" |
| Reprocessamento | Respostas reconstruídas a partir das somas observadas | 2.0 | Confirmar que a v2.0 preserva o cálculo e verificar as novas sinalizações |
| Apreciação | Um especialista em TI | 1.0 e 2.0 | Avaliar a qualidade do conteúdo: recomendações, escala, faixas e priorização |

O nome da empresa, do respondente e do especialista são omitidos por confidencialidade.

## Resultado da avaliação da v1.0

| Critério | Resultado |
|---|---|
| C1. Tempo | **Atendido.** Cerca de 5 minutos na aplicação e 2 na reaplicação |
| C2. Clareza | **Não atendido** na aplicação: houve dúvidas sobre os enunciados e a escala, e o aplicador interveio. **Parcialmente atendido** na reaplicação |
| C3. Determinismo | **Atendido.** Cálculo manual e relatório coincidem; as regras de borda funcionaram como especificado |
| C4. Estabilidade | **Parcialmente atendido.** A primeira prioridade se manteve, mas uma única resposta mudou o nível de uma dimensão |
| C5. Acionabilidade | (a) **Atendido**; (b) **não avaliado**, porque a utilidade percebida não foi coletada |
| C6. Aderência | (a) **Atendido**; (b) **não avaliado**, porque o uso na decisão não foi observado |
| C7. Transparência e custo | **Parcialmente atendido.** O custo foi atendido, mas a regra de priorização não era exibida |

O principal achado foi que o gargalo da autoaplicação **não estava no tamanho do questionário, e sim na interpretação da escala**: o respondente leu as opções como notas de qualidade, e não como registro de existência e formalização.

## Refinamento: da v1.0 para a v2.0

Duas regras guiaram o refinamento:
- **Rastreabilidade:** toda mudança responde a uma limitação observada.
- **Preservação do cálculo:** médias, faixas, priorização e desempate ficam idênticos, para que as aplicações continuem comparáveis.

| Limitação observada | Critério | Melhorias |
|---|---|---|
| L1. Escala lida como nota de qualidade | C2 | M1, M2 |
| L2. Dúvidas sobre enunciados e sobre como classificar | C2 | M3, M4 |
| L3. Respostas concentradas nas opções mais altas, sem conferência | C2, C4 | M5 |
| L4. Tempo informado incompatível com o observado | C1 | M6 |
| L5. Nível alterado por um único item; ordem baseada em diferenças pequenas | C4, C5 | M7 |
| L6. Regra de priorização não exibida | C7 | M8 |
| L7. Utilidade e uso do relatório não coletados | C5b, C6b | M9 |

A descrição de cada melhoria está no [CHANGELOG](../CHANGELOG.md).

**Decisões mantidas de propósito:**
- **Faixas de corte:** um único respondente não dá base para calibrá-las.
- **As 48 recomendações:** a revisão delas dependia da apreciação por especialista, feita depois.
- **Os 20 itens:** aumentar o número de itens reduziria a sensibilidade, mas também a simplicidade. A opção foi tornar a sensibilidade visível (M7).

**Verificação:** a v2.0 foi executada de forma automatizada no navegador com quatro conjuntos de respostas. Ela reproduziu as médias, os níveis e a ordem da v1.0 e gerou relatórios idênticos em execuções repetidas. Reprocessados na v2.0, os perfis observados teriam marcado como **nível limite** exatamente a dimensão que mudou de nível entre a aplicação e a reaplicação.

## Apreciação por especialista

Um especialista em tecnologia da informação, com quinze anos de experiência em consultoria, avaliou o conteúdo que a aplicação real não permitia avaliar:

| Aspecto | Resultado |
|---|---|
| Recomendações pertinentes à dimensão e ao nível | 42 de 48 |
| Recomendações claras para um gestor sem formação técnica | 44 de 48 |
| Origem (interna ou externa) adequada | 47 de 48 |
| Aprovadas nos três atributos | 38 de 48 |
| Pares dimensão–nível cobertos | 16 de 16 |
| Níveis correspondem a estágios reconhecíveis? | Em parte. A fronteira entre os níveis 2 e 3 é tênue |
| Faixas de corte razoáveis? | Em parte. Recomenda calibrar com cerca de 30 empresas e rever o corte de 1,50 |
| Regra de priorização adequada? | Em parte. Ignora a dependência entre dimensões, por exemplo dados antes de ferramentas |

**Lacunas apontadas:**
- jargão nas recomendações que tratam diretamente de IA;
- falta de cuidados de proteção de dados nas ações que envolvem terceiros;
- ambiguidade do rótulo "Contratar" quando o recurso é gratuito;
- falta de indicação de custo, prazo e sequência de execução.

Dessas lacunas derivam os refinamentos E1 a E8, listados no [CHANGELOG](../CHANGELOG.md#próxima-versão-planejada).

## Princípios de projeto

Contribuição prescritiva da pesquisa. São hipóteses a testar em novas aplicações, porque vêm de um único caso.

| | Princípio |
|---|---|
| P1 | Medir existência e formalização, e não qualidade |
| P2 | Não agregar as dimensões em uma nota única |
| P3 | Usar regras determinísticas e expostas ao usuário |
| P4 | Comunicar a incerteza, em vez de alongar o questionário |
| P5 | Redigir as recomendações por dimensão e nível, em linguagem gerencial e com a origem definida por quem executa a ação |
| P6 | Embutir a coleta de retorno no próprio instrumento |

## Limitações e trabalhos futuros

**Limitações:**
- **Base de evidências:** uma empresa, um respondente, um especialista e um setor. Os resultados indicam viabilidade de funcionamento, não eficácia.
- **Autodeclaração:** as respostas não foram verificadas de forma independente, e a primeira aplicação foi afetada pela orientação do aplicador.
- **Ordem das evidências:** as melhorias de clareza da v2.0 ainda não foram testadas com respondentes reais.

**Trabalhos futuros:**
1. Aplicar a versão refinada em cerca de 30 empresas de perfis variados, sem orientação, para calibrar as faixas.
2. Comparar mais de um respondente por empresa ou fazer verificação independente.
3. Acompanhar reaplicações espaçadas no tempo e as decisões de alocação efetivamente tomadas.
4. Ampliar a apreciação para um painel que inclua gestores de pequenas empresas.

## Referências

- Arroyabe, M. F. et al. (2024). Analyzing AI adoption in European SMEs: A study of digital capabilities, innovation, and external environment. *Technology in Society*, 79, 102733.
- Hansen, H. F. et al. (2024). Understanding artificial intelligence diffusion through an AI capability maturity model. *Information Systems Frontiers*, 26, 2147–2163.
- Jacobides, M. G., Brusoni, S., Candelon, F. (2021). The evolutionary dynamics of the artificial intelligence ecosystem. *Strategy Science*, 6, 412–435.
- Mikalef, P., Gupta, M. (2021). Artificial intelligence capability: Conceptualization, measurement calibration, and empirical study on its impact on organizational creativity and firm performance. *Information & Management*, 58, 103434.
- Peffers, K. et al. (2007). A design science research methodology for information systems research. *Journal of Management Information Systems*, 24, 45–77.
- Robertson, J. et al. (2025). Managing change when integrating artificial intelligence (AI) into the retail value chain: The AI implementation compass. *Journal of Business Research*, 189, 115198.
- Solaimani, S., Swaak, L. (2023). Critical success factors in a multi-stage adoption of artificial intelligence: A necessary condition analysis. *Journal of Engineering and Technology Management*, 69, 101760.
- Uren, V., Edwards, J. S. (2023). Technology readiness and the organizational journey towards AI adoption: An empirical study. *International Journal of Information Management*, 68, 102588.
- Weber, M. et al. (2023). Organizational capabilities for AI implementation: Coping with inscrutability and data dependency in AI. *Information Systems Frontiers*, 25, 1549–1569.
