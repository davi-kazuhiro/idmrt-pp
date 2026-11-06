# IDMRT-PP

**Instrumento de Diagnóstico de Maturidade de Recursos Técnicos para Adoção de IA em empresas de Pequeno Porte**

> Vinte perguntas, cerca de dez minutos, sem instalação e sem conhecimento técnico. Ao final, a empresa recebe o nível de maturidade de cada recurso técnico, a ordem em que deve investir e o que fazer em cada caso, separando o que pode ser feito internamente do que tende a ser mais viável contratar.

**[Usar o instrumento online](https://davi-kazuhiro.github.io/idmrt-pp/)** · [Versão 1.0](https://davi-kazuhiro.github.io/idmrt-pp/versoes/v1.0/) · [Especificação completa](docs/instrumento.md) · [Processo de pesquisa](docs/pesquisa.md)

Este repositório hospeda o **artefato** de uma pesquisa aplicada conduzida sob o paradigma da **Design Science Research (DSR)**, na disciplina de Pesquisa Aplicada do Bacharelado em Ciência da Computação da PUCPR. O artigo da pesquisa está em elaboração e não faz parte deste repositório.

---

## O problema

Empresas de pequeno porte costumam iniciar projetos de inteligência artificial sem saber se têm os recursos técnicos para sustentá-los. Os modelos de maturidade e de capacidades de IA existentes na literatura têm duas limitações para esse público:
- foram construídos e validados em organizações de médio e grande porte;
- exigem tempo, coordenação entre áreas e especialização que uma empresa pequena não tem.

O IDMRT-PP é um instrumento **autoaplicável** que responde à pergunta anterior a qualquer investimento: **em que estágio estão os recursos técnicos da empresa e o que priorizar a partir daí?** O resultado serve de insumo para a etapa de *plano de alocação de recursos* da frente de organização da IA.

## Como usar

1. Abra o [instrumento online](https://davi-kazuhiro.github.io/idmrt-pp/). Para usar sem internet, baixe o arquivo [`index.html`](index.html) e abra em qualquer navegador, no computador ou no celular.
2. Opcionalmente, preencha o nome da empresa, quem responde e a data.
3. Leia o quadro "Como responder" e escolha, em cada pergunta, a opção que descreve a situação **de hoje**, não a desejada.
4. Clique em **Gerar diagnóstico**.
5. Salve o relatório em PDF, guarde a aplicação para comparar com aplicações futuras ou exporte as respostas em CSV.

**Privacidade:** o instrumento roda inteiramente no navegador. Nenhuma resposta é enviada para servidor algum. O histórico de aplicações fica só no armazenamento local do navegador de quem respondeu.

## Como funciona

O instrumento tem três camadas: entrada (questionário), processamento (cálculo) e saída (relatório).

### Entrada: 20 itens em 4 dimensões

| Dimensão | O que avalia | Itens |
|---|---|---|
| **Infraestrutura** | Equipamentos, nuvem, rede, backup e controle de acesso | I1 a I5 |
| **Dados** | Registro, centralização, padronização, histórico e responsabilidade | D1 a D5 |
| **Ferramentas** | Sistemas em uso, integração, exportação e automação | F1 a F5 |
| **Competências** | Orientação, responsável, experiência, tempo e apoio externo | C1 a C5 |

Cada item descreve uma prática observável, e não um conceito técnico. A escala mede **existência e formalização da prática, e não sua qualidade**:

| Opção | Significado | Valor no cálculo |
|---|---|---|
| Não existe | A empresa não tem essa prática | 0 |
| Informal | Existe, mas depende da iniciativa de alguém e não está escrita | 1 |
| Padronizado | Existe e está registrada por escrito, mas ninguém confere se é seguida | 2 |
| Acompanhado | Existe, está registrada e alguém confere com regularidade | 3 |
| Não sei | O gestor não conhece a situação do recurso | 0, sinalizado à parte |

A lista completa de itens, com os 80 exemplos de evidência e as 48 recomendações, está em [`docs/instrumento.md`](docs/instrumento.md).

### Processamento: regras determinísticas

- **Pontuação:** média simples dos 5 itens de cada dimensão, de 0,00 a 3,00, sem pesos.
- **Sem nota única:** o instrumento não calcula uma nota global, porque uma média agregada esconderia a dimensão atrasada, que é justamente a informação que orienta onde investir.
- **Níveis:**
  - Nível 1, Inicial: até 0,74.
  - Nível 2, Emergente: de 0,75 a 1,49.
  - Nível 3, Estruturado: de 1,50 a 2,24.
  - Nível 4, Avançado: a partir de 2,25.
- **Priorização:** a dimensão de menor média vem primeiro. Em caso de empate, a precedência é Dados, Infraestrutura, Ferramentas e Competências, porque a qualidade dos dados condiciona qualquer uso de IA.
- **Restrição bloqueante:** toda dimensão no Nível 1 é marcada como algo a resolver antes de contratar qualquer ferramenta de IA.

As mesmas respostas sempre produzem o mesmo relatório, independentemente de quem aplica. Todas as regras são exibidas ao usuário no próprio relatório.

**Comunicação da incerteza** (incluída na v2.0). Com apenas 5 itens por dimensão, uma única resposta diferente muda a média em 0,20. Em vez de alongar o questionário, o relatório deixa essa sensibilidade visível:
- **Nível limite:** marca a dimensão cuja média está a menos de 0,20 de um corte entre níveis e mostra também as recomendações do nível vizinho.
- **Ordem pouco definida:** marca as dimensões consecutivas na prioridade que diferem em até 0,20.
- **Aviso de consistência:** antes de gerar o diagnóstico, alerta quando a média geral fica em 2,50 ou mais, ou quando todas as respostas são iguais, e convida o respondente a revisar.

### Saída: relatório de diagnóstico

1. **Perfil de maturidade:** média e nível de cada dimensão.
2. **Leitura do perfil:** o que cada nível significa, em linguagem não técnica, com os alertas de nível limite e de "não sei".
3. **Prioridades:** a ordem de investimento, as restrições bloqueantes e a regra usada para ordenar.
4. **Recomendações:** três ações por dimensão, de acordo com o nível, cada uma marcada como *Fazer internamente* ou *Contratar*.
5. **Avaliação do respondente:** se o diagnóstico ajuda a decidir, qual dimensão o gestor pretende tratar primeiro e que pergunta foi difícil. Essas respostas são exportáveis em CSV para alimentar a pesquisa.

O instrumento **não** avalia estratégia, cultura, governança ou conformidade regulatória. Também não recomenda fornecedores nem estima custos, e se baseia no que o respondente declara, sem verificação técnica independente.

## Fundamentação

| Decisão de projeto | Base na literatura |
|---|---|
| Quatro dimensões de recursos técnicos | Capacidade organizacional de IA (Mikalef e Gupta, 2021); dados como dimensão própria pela dependência de dados na implementação de IA (Weber et al., 2023) |
| Escala de quatro estágios | Modelos de maturidade e de prontidão para IA (Hansen et al., 2024; Uren e Edwards, 2023) |
| Avaliação por dimensão, sem nota agregada | Avaliação articulada entre frentes (Uren e Edwards, 2023) |
| Recomendações diferentes por nível | Fatores críticos de sucesso que variam conforme o estágio de adoção (Solaimani e Swaak, 2023) |
| Separação entre fazer internamente e contratar | Dependência do ecossistema externo de IA (Jacobides, Brusoni e Candelon, 2021; Robertson et al., 2025) |
| Restrições do pequeno porte como requisito de projeto | Adoção de IA em pequenas e médias empresas (Arroyabe et al., 2024) |

## Processo de pesquisa (DSR)

O artefato foi construído e avaliado seguindo a metodologia DSRM de Peffers et al. (2007). Os critérios de avaliação foram definidos **antes** da demonstração.

| Etapa | O que aconteceu | Versão |
|---|---|---|
| Projeto e desenvolvimento | Requisitos RF01 a RF09 e RNF01 a RNF07, casos de uso e critérios de avaliação | 1.0 |
| Demonstração | Aplicação real numa empresa de engenharia civil de pequeno porte, com reaplicação no mesmo dia | 1.0 |
| Avaliação | 7 critérios: tempo, clareza, determinismo, estabilidade, acionabilidade, aderência à alocação e transparência | 1.0 |
| Refinamento | 7 limitações tratadas por 9 melhorias rastreáveis, com a lógica de cálculo preservada | 2.0 |
| Apreciação por especialista | As 48 recomendações, a escala, as faixas e a regra de priorização avaliadas por um especialista em TI | 1.0 e 2.0 |

Principais resultados:
- **Tempo:** cerca de 5 minutos na aplicação e 2 na reaplicação, contra o limite de 1 hora.
- **Determinismo:** os valores do relatório coincidem com o cálculo manual. As regras de bloqueio, desempate e "não sei" funcionam como especificado.
- **Clareza:** a escala foi lida como nota de qualidade. Esse foi o principal gargalo da autoaplicação e motivou a v2.0.
- **Apreciação:**
  - 42 das 48 recomendações foram julgadas pertinentes, 44 claras e 47 com a origem (interna ou externa) adequada;
  - os 16 pares dimensão–nível foram considerados cobertos.

**Alcance das evidências:** foram um caso, um respondente e um especialista. Os resultados indicam que o instrumento **funciona como especificado**, não que ele **melhore** as decisões de alocação. O detalhamento de cada etapa, dos requisitos e da agenda de refinamentos está em [`docs/pesquisa.md`](docs/pesquisa.md).

## Estrutura do repositório

```
idmrt-pp/
├── index.html              # Versão 2.2, a versão atual (arquivo único, sem dependências)
├── versoes/
│   └── v1.0/index.html     # Versão 1.0, usada na demonstração e na avaliação
├── docs/
│   ├── instrumento.md      # Itens, exemplos, níveis e as 48 recomendações
│   └── pesquisa.md         # Requisitos, critérios, evidências e refinamentos (DSR)
├── CHANGELOG.md            # O que mudou em cada versão
└── README.md
```

Cada versão é um único arquivo HTML, com CSS e JavaScript embutidos. Não há build, dependências nem chamadas de rede. Os arquivos estão neste repositório exatamente como foram usados na pesquisa.

## Autores

Davi Kazuhiro Natume, Eduardo Teodoro Moreira de Souza, Lucas Maciel Cardoso e Pedro Henrique Valente Favero. Grupo 5, Pesquisa Aplicada, Bacharelado em Ciência da Computação, PUCPR.

## Licença

Ainda não há uma licença definida. Até que os autores escolham uma, todos os direitos estão reservados. Para usar ou adaptar o instrumento, entre em contato com os autores.
