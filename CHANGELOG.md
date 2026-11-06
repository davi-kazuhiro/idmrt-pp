# Histórico de versões

A lógica de cálculo (médias, faixas de nível, regra de priorização e critério de desempate) é **idêntica em todas as versões**. Por isso, as mesmas respostas produzem o mesmo perfil, os mesmos níveis e a mesma ordem de prioridade em qualquer versão, e aplicações feitas em versões diferentes continuam comparáveis.

## [2.2] — atual

- Tema escuro, escolhido automaticamente conforme o sistema ou manualmente. O relatório impresso ou salvo em PDF sai sempre no tema claro.

## [2.1]

- Ajustes de nomenclatura.

## [2.0] — versão final documentada da pesquisa

Refinamento derivado da avaliação da v1.0. Cada melhoria responde a uma limitação observada:

| Melhoria | O que mudou | Limitação tratada |
|---|---|---|
| M1 | Instrução de resposta reescrita: as opções indicam existência e formalização, não qualidade; na dúvida, escolher a opção mais baixa | Escala lida como nota de qualidade |
| M2 | Números 0 a 3 ocultados das opções, para não se confundirem com os níveis 1 a 4 | Escala lida como nota de qualidade |
| M3 | Exemplo curto de evidência sob cada opção de cada pergunta (80 exemplos) | Dúvidas sobre como classificar |
| M4 | Cinco enunciados reformulados (I1, I3, D3, F5, C1), cada um passando a descrever uma única prática observável | Dúvidas sobre os enunciados |
| M5 | Aviso de consistência antes de gerar o diagnóstico | Respostas concentradas nas opções mais altas |
| M6 | Tempo estimado ajustado de vinte para cerca de dez minutos | Tempo informado incompatível com o observado |
| M7 | Sinalização de nível limite (com as recomendações do nível vizinho) e de ordem pouco definida | Nível alterado por um único item |
| M8 | Regra de priorização, critério de desempate e restrição bloqueante exibidos no relatório | Regra de priorização não exibida |
| M9 | Perguntas de utilidade percebida, decisão e dificuldade ao final do relatório; exportação das respostas em CSV | Utilidade e uso do relatório não coletados |

Novos requisitos funcionais: RF10 (aviso de consistência), RF11 (sinalização de incerteza), RF12 (regras exibidas) e RF13 (coleta e exportação do retorno).

## [1.0]

Primeira versão funcional, usada na demonstração (aplicação real e reaplicação) e na avaliação.

- 20 itens em 4 dimensões, com escala de 4 pontos e a opção "Não sei".
- Cálculo automático das médias, classificação em 4 níveis, priorização com desempate e restrição bloqueante.
- 48 recomendações associadas aos pares dimensão–nível, classificadas quanto à origem.
- Bloqueio da geração com preenchimento parcial, impressão do relatório e histórico local para comparar aplicações.

## Próxima versão (planejada)

Refinamentos derivados da apreciação por especialista, que ainda **não** estão no instrumento. Os que preservam a lógica de cálculo:

- **E1:** reescrever as recomendações com ressalva do especialista.
- **E2:** complementar com exemplos concretos as recomendações aprovadas que receberam comentário.
- **E3:** incluir cuidados de proteção de dados (LGPD) nas ações que envolvem terceiros.
- **E4:** definir a origem por quem executa a ação, e não por haver pagamento, trocando o rótulo "Contratar" por "Apoio externo".
- **E5:** ordenar as recomendações na sequência em que devem ser executadas.

Os que dependem de nova evidência:

- **E6:** indicar custo e prazo qualitativos.
- **E7:** considerar a dependência entre dimensões na priorização.
- **E8:** calibrar as faixas com cerca de trinta empresas.
