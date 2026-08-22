# Entrega 1 — Conhecendo o projeto, o usuário e o problema

**Data:** 20/08/2026  
**Status:** [x] concluída  
**Responsabilidade:** 1 solução consolidada por equipe

## Objetivo da atividade

Reinterpretar o tema do TCC sob a perspectiva de Interação Humano-Computador e construir um **entendimento comum entre os integrantes da equipe**.

A disciplina utiliza preferencialmente o tema do TCC para os exercícios de IHC. Isso vale tanto para TCCs que já preveem uma interface quanto para trabalhos cujo resultado principal é algoritmo, modelo, API, biblioteca, análise de dados, infraestrutura, estudo experimental ou outro artefato técnico.

> **Importante:** a interface projetada na disciplina é um artefato de aprendizagem de IHC. Ela **não se torna automaticamente uma obrigação do TCC**. Sua incorporação ao trabalho de conclusão depende de decisão da equipe e do orientador.

Antes de preencher, leia [`../GUIA_ESCOPO_IHC.md`](../GUIA_ESCOPO_IHC.md).

Nesta primeira semana a equipe **não deve começar desenhando telas**. Primeiro deverá compreender:

- o que o TCC realmente produz;
- quem poderia obter valor dessa contribuição;
- quais pessoas interagem, administram, configuram, interpretam ou são afetadas;
- o que essas pessoas precisam alcançar;
- como atividades relacionadas acontecem hoje;
- problemas, limitações e contexto;
- alternativas existentes;
- qual recorte de interação fará sentido para a disciplina.

Ao final desta entrega, a equipe deve diferenciar:

- **tema do TCC** × **escopo formal do TCC** × **escopo de IHC da disciplina**;
- **objetivo do projeto** × **objetivo do usuário**;
- **problema do usuário** × **solução tecnológica**;
- **fato conhecido** × **hipótese** × **lacuna de conhecimento**;
- **capacidade técnica** × **forma de uso dessa capacidade**;
- **funcionalidade** × **atividade/resultado que o usuário precisa alcançar**;
- **usuário direto** × **stakeholders**.

---

## Como classificar as respostas

Sempre que a resposta fizer uma afirmação sobre usuários, problemas, atividades, necessidades, contexto ou mercado, use:

- **[F] Fato conhecido** — existe evidência/fonte.
- **[H] Hipótese** — afirmação plausível que ainda precisa ser investigada.
- **[?] Não sabemos ainda** — lacuna relevante.

Quando usar `[F]`, informe a origem. Hipóteses prioritárias devem receber IDs (`H01`, `H02`...) e também ser registradas em [`../RASTREABILIDADE.md`](../RASTREABILIDADE.md).

> **Exemplo:** `[H] H01 — DBAs considerariam útil comparar automaticamente o plano atual de execução com uma recomendação produzida pelo algoritmo.`

Uma hipótese explicitada é melhor do que uma suposição escondida.

---

# 0. Identificação do TCC e da equipe

## 0.1 Membros

| Nome completo | Matrícula | GitHub |
|---|---:|---|
| Hugo Emílio Nomura | 22.123.051-9 | [@HG0304](https://github.com/HG0304) |
| Pedro Henrique Correia de Oliveira | 22.222.009-7 | [@PedroHCorreia](https://github.com/PedroHCorreia) |
| Pedro Henrique Satoru Lima Takahashi | 22.123.019-6 | [@PedroSatoru](https://github.com/PedroSatoru) |
| Vitor Monteiro Vianna | 22.223.085-6 | [@VitorMonteiroVianna](https://github.com/VitorMonteiroVianna) |

## 0.2 Título atual do TCC

Um Harness de IA para Resolução de Perguntas em Linguagem Natural: Adaptando o Ralph Wiggum Loop Além do Desenvolvimento de Software

## 0.3 Orientador(a)

Prof. Charles Henrique Porto Ferreira

## 0.4 Qual é o resultado principal atualmente previsto no TCC?

- [x] sistema/aplicação interativa;
- [x] algoritmo;
- [ ] modelo de IA/ML/LLM;
- [ ] biblioteca/API/framework;
- [ ] análise de dataset;
- [x] estudo/benchmark/avaliação experimental;
- [x] infraestrutura/backend;
- [ ] componente embarcado/IoT;
- [ ] outro.

**Descrição:** O resultado principal do TCC é um harness de orquestração de IA (serviço backend) que implementa o Ralph Wiggum Loop adaptado para linguagem natural, mitigando o decaimento de contexto (*context rot*) por meio de um ciclo stateless de tarefas atômicas e transferência estruturada de aprendizados (*Fresh Context*). A contribuição técnica é validada de forma quantitativa através de benchmarks de acurácia comparativa utilizando a família de modelos Llama 3.1 nos datasets MMLU e GPQA.

## 0.5 O TCC já previa desenvolvimento de interface com usuário?

- [x] Sim, a interface já faz parte do TCC.
- [ ] Parcialmente; existe alguma interação, mas ainda não está bem definida.
- [ ] Não. O TCC é predominantemente técnico e não previa interface.

**Explique o que está formalmente previsto no TCC:** Está prevista a criação de uma aplicação demonstrativa que sirva de interface para a execução do harness de orquestração de IA. A interface permite que o usuário envie uma pergunta e visualize em tempo real a decomposição em tarefas, o ciclo de raciocínio (thinking), a validação de critérios de aceite e a geração do resultado final (síntese), além de monitorar dados de infraestrutura como tokens consumidos e tamanho da janela de contexto.

---

# 1. Entendendo a contribuição do projeto

## 1.1 Explique o TCC em uma frase, sem citar linguagem de programação, framework ou banco de dados.

O projeto propõe um orquestrador que divide perguntas complexas para LLMs em tarefas isoladas e iterativas para evitar o decaimento de contexto.

## 1.2 Qual situação, atividade ou problema do mundo real motivou o TCC?

`[F]` **Decaimento de contexto (*context rot*):** Em execuções e interações longas com LLMs, o histórico acumulado na janela de contexto gera ruído e degrada a acurácia das respostas intermediárias e finais.

## 1.3 Qual é a **capacidade/contribuição central** produzida pelo TCC?

Nosso TCC produz, melhora, analisa ou permite **orquestrar e isolar o contexto das chamadas de LLM por meio de tarefas atômicas e aprendizados pontuais acumulados (*Fresh Context*), mitigando a degradação de contexto durante o raciocínio complexo**.

## 1.4 O que se espera que esteja diferente **para pessoas, organizações ou processos** se essa contribuição for bem-sucedida?

`[H]` **Acurácia e Confiabilidade:** Espera-se que usuários obtenham respostas significativamente mais precisas, lógicas e livres de alucinações para problemas complexos (como as questões avançadas do GPQA e MMLU) sem que o sistema sofra degradação de desempenho à medida que o raciocínio se estende.

## 1.5 O que é mérito técnico/científico do TCC e o que seria uma possível aplicação prática?

| Mérito/contribuição técnica | Possível aplicação/valor em uso |
|---|---|
| Algoritmo de orquestração stateless inspirado no Ralph Wiggum Loop e sua avaliação empírica nos datasets MMLU/GPQA. | Sistemas corporativos de suporte à decisão, assistentes virtuais de auditoria técnica ou plataformas de resolução de problemas complexos multimétodo. |

---

# 2. Entendendo as pessoas envolvidas

## 2.1 Quem interage diretamente com o produto, se já existe interface prevista?

`[H]` **Estudantes, Pesquisadores e Analistas Acadêmicos/Profissionais:** Usuários que submetem perguntas complexas (de múltipla escolha ou discursivas) e precisam de uma resposta de alta acurácia, com a possibilidade de acompanhar e auditar o passo a passo do raciocínio da IA para fins de transparência e verificação de alucinações.

## 2.2 Quem poderia **usar, configurar, administrar, operar, interpretar ou tomar decisões** a partir da contribuição técnica?

| Perfil | Relação com a contribuição | O que faria | Status/evidência |
|---|---|---|---|
| Pesquisador / Estudante | Usuário final do sistema | Submete a pergunta complexa e consome a resposta final | `[H]` |
| Analista / Auditor | Avaliador da explicabilidade | Acompanha a execução das tarefas e a validação lógica na timeline para auditar se o raciocínio foi correto | `[H]` |
| Operador do Sistema | Usuário de monitoramento | Visualiza o consumo de tokens e o fluxo de novas janelas de contexto geradas | `[H]` |

## 2.3 Existem pessoas afetadas que não usariam a interface diretamente?

Não foram identificados stakeholders afetados que não utilizariam a interface diretamente.

<!-- | Stakeholder | Como é afetado | Usa interface? | Status/evidência |
|---|---|---|---|
| {{...}} | {{...}} | sim/não | {{...}} | -->

## 2.4 Que características desses perfis podem influenciar a interação?

`[H]` O perfil priorizado compreende usuários acadêmicos e profissionais que possuem familiaridade com métricas de IA, mas que necessitam de uma visualização didática e transparente para auditar o raciocínio das respostas sem precisar interagir com códigos ou logs brutos. A interface precisa de clareza conceitual na linha do tempo das tarefas lógicas e legibilidade imediata das métricas de contexto e tokens.

---

# 3. Entendendo objetivos e atividades

## 3.1 O que o usuário está tentando conseguir no mundo real?

`[H]` Validar se o processo de raciocínio de um modelo de linguagem para uma determinada questão de alta complexidade foi executado de forma estruturada e se o resultado final de fato obedece aos critérios lógicos esperados, garantindo a audibilidade do sistema de IA.

## 3.2 Quais são as atividades mais importantes?

| ID | Atividade/objetivo | Quem realiza | Frequência/criticidade inicial | Status/evidência |
|---|---|---|---|---|
| A01 | Submeter a pergunta complexa para processamento no orquestrador | Pesquisador / Estudante | Alta frequência / Alta criticidade | `[F]` |
| A02 | Acompanhar a execução das fases de raciocínio intermediárias (Setup, Loop, Síntese) em tempo real | Pesquisador / Auditor | Alta frequência / Alta criticidade (auditoria) | `[F]` |
| A03 | Monitorar o consumo acumulado de tokens e o fluxo de contextos | Pesquisador / Operador | Média frequência / Média criticidade | `[F]` |

## 3.3 Qual atividade parece mais frequente? Por quê?

`[F]` **Acompanhar a execução das fases de raciocínio (A02):** Como o processo do Ralph Wiggum Loop envolve múltiplos ciclos de verificação e reflexão da IA, o pesquisador ou analista passará a maior parte do tempo observando a linha do tempo do progresso das tarefas e como os aprendizados estão sendo processados a cada janela de contexto limpa.

## 3.4 Qual parece mais crítica? Que consequência existe se for mal executada?

`[H]` **Auditar a fidelidade do raciocínio lógico (A02):** Se a visualização for confusa ou omitir as reais tentativas de correção da IA, o usuário não conseguirá confiar na resposta final gerada e poderá tomar decisões baseadas em alucinações não detectadas.

---

# 4. Entendendo o problema ou processo atual

## 4.1 Como essas atividades são realizadas hoje, antes da interface imaginada na disciplina?

`[F]` Geralmente, o usuário submete perguntas a chatbots tradicionais (como ChatGPT ou Claude) de forma linear e direta, recebendo apenas o bloco de texto final sem qualquer visibilidade do raciocínio interno ou das validações feitas sob o capô.

## 4.2 O que é difícil, demorado, confuso, repetitivo, arriscado ou pouco transparente?

`[F]` A ausência de transparência (caixa-preta) impede que o usuário saiba se o modelo de linguagem alucinou em alguma etapa intermediária, se o contexto excessivo degradou a lógica aplicada ou se as premissas adotadas pela IA foram validadas individualmente antes do encerramento.

## 4.3 Que informações o profissional precisa interpretar para tomar decisão?

`[H]` Qual tarefa está ativa, quais critérios individuais passaram ou falharam, o conteúdo da reflexão do modelo, o acumulado de tokens gerados e se a janela de contexto foi reinicializada corretamente para manter a mente limpa.

## 4.4 O que acontece quando a atividade falha ou quando o resultado é interpretado incorretamente?

`[F]` O usuário aceita respostas que parecem plausíveis mas contêm erros lógicos internos indetectáveis, levando a decisões equivocadas em análises científicas ou acadêmicas.

## 4.5 Conte uma situação concreta.

`[F]` **Caso de uso do Ralph Wiggum Loop:** Maria, uma pesquisadora acadêmica, precisa responder a uma questão complexa de biologia molecular. Ela submete a pergunta em nossa interface e acompanha a linha do tempo do "Open Thinking" em tempo real. Ela observa a Fase A criar 3 tarefas atômicas. Durante a Fase B, ela acompanha a execução da Tarefa 2 (validação de membrana celular) e visualiza um sinalizador de erro (✗) de uma premissa incorreta na primeira iteração, seguido pela correção imediata (✓) em um novo contexto limpo. Ao final, a Fase C exibe a resposta sintetizada. Graças à visualização gráfica das etapas de raciocínio, Maria pôde confiar na resposta sabendo exatamente quais caminhos a IA trilhou.

## 4.6 Que evidência existe hoje?

| Evidência/fonte | O que sustenta | Limitação |
|---|---|---|
| Dificuldade de auditoria de modelos de linguagem | A necessidade de enxergar graficamente e em tempo real as fases A, B e C de raciocínio e validação. | Relatos informais de usuários e literatura de explicabilidade em IA. |

---

# 5. Entendendo o contexto de uso

## 5.1 Onde e em quais situações a interação poderia ocorrer?

`[H]` Em ambientes de estudo acadêmico, laboratórios de pesquisa ou escritórios de análise de dados, enquanto o profissional ou estudante formula e avalia perguntas complexas.

## 5.2 Em quais dispositivos/equipamentos?

`[F]` Computadores desktop e notebooks (telas de alta resolução/widescreen), pois a visualização de painéis complexos e logs detalhados exige espaço em tela.

## 5.3 Existem condições físicas relevantes?

`[H]` Uso compartilhado de tela em reuniões de design de prompt, alta necessidade de foco e interrupções frequentes que exigem que o histórico de execução seja facilmente legível para o usuário retomar o raciocínio.

## 5.4 Existem fatores sociais ou organizacionais?

Não foram identificados fatores sociais ou organizacionais relevantes para o escopo do projeto, visto que o uso é de caráter individual e focado na auditoria da resposta.

## 5.5 Existe necessidade de histórico, rastreabilidade ou auditoria?

`[F]` Sim. Cada execução do harness precisa de total rastreabilidade sobre a árvore de decisão, prompts enviados, tokens consumidos e o ciclo de validação para fins de auditoria acadêmica e comercial.

## 5.6 Um erro pode produzir consequência relevante? Qual?

`[H]` Sim. Um erro ou inconsistência no processo lúdico/de validação do loop pode fazer com que o sistema entregue uma resposta incorreta ou alucinada para o usuário final, comprometendo a integridade de sua pesquisa ou análise.

---

# 6. Entendendo mercado e alternativas existentes

## 6.1 Como pessoas resolvem problemas semelhantes hoje?

| Alternativa atual | Quem usa | Para quê | Status/evidência |
|---|---|---|---|
| LangSmith / Langfuse | Engenheiros de IA | Rastreamento e visualização de cadeias de execução (chains) de LLM. | `[F]` (ferramentas amplamente adotadas no mercado) |
| Console do OpenRouter / OpenAI Playground | Desenvolvedores | Testes manuais lineares e acompanhamento de chamadas brutas. | `[F]` |

## 6.2 Existem produtos que atuam na mesma área, mesmo sem serem equivalentes ao TCC?

`[F]` Ferramentas de observabilidade de LLM (LLMOps) focadas em rastreamento de traces de agentes e monitoramento de custos de tokens.

## 6.3 Quais interfaces profissionais esse público já conhece?

`[F]` VS Code (IDEs), interfaces de chat clássicas (ChatGPT, Claude), dashboards de monitoramento (Grafana, Datadog) e plataformas de desenvolvimento de prompt.

## 6.4 O que essas soluções parecem fazer bem?

`[F]` Exibir detalhadamente cada chamada HTTP feita aos LLMs e o tempo de resposta.

## 6.5 O que parecem fazer mal, dificultar ou não atender?

`[H]` Falham em representar fluxos de raciocínio específicos baseados em reinicialização de contexto e ciclos de feedback baseados em histórias do Ralph Wiggum Loop, dificultando a visualização didática e focada na mitigação de *context rot*.

## 6.6 Que padrões de interface ou vocabulário parecem familiares a esse público?

`[F]` Gráficos de linha do tempo (timelines), painéis laterais (split panels), badges indicadoras de status (sucesso/erro), métricas de tokens (tk), e representações em árvore ou grafos.

---

# 7. Derivando o escopo de IHC da disciplina

## 7.1 Escolha o caminho do projeto

### Caminho A — TCC já possui interface

Explique qual parte da interface será usada como recorte da disciplina e por que esse fluxo é relevante.

A interface demonstrativa web que exibe o fluxo do harness será o objeto principal. O recorte priorizado para IHC foca no monitoramento visual em tempo real das três fases de orquestração do loop (Setup, Loop de Raciocínio com reinicialização de contexto, e Síntese Final), permitindo ao usuário analisar visualmente e em detalhes como as tarefas atômicas mitigam o decaimento de contexto e o consumo de tokens correspondente a cada etapa.

## 7.2 Qual perfil será priorizado no projeto de IHC?

Pesquisador / Estudante / Analista de Explicabilidade.

**Por que esse perfil foi escolhido?** `[H]` Pois são as pessoas que utilizam o sistema para obter respostas precisas e necessitam da transparência do processo (visualização de tarefas, aprendizados, contexto) para validar a resposta final sem precisar lidar com código ou logs brutos.

## 7.3 Qual objetivo desse usuário será priorizado?

Auditar a eficácia do Ralph Wiggum Loop adaptado na resolução de uma pergunta complexa, analisando o comportamento das tarefas lógicas, os aprendizados e o consumo de tokens associado a cada janela de contexto.

## 7.4 Que interface será explorada na disciplina?

> **Para fins da disciplina de IHC, será projetada uma interface que permita a pesquisadores e estudantes utilizar o painel de visualização do Ralph Wiggum Loop adaptado para acompanhar de forma transparente e interativa a decomposição, execução stateless e síntese de respostas de LLMs, no contexto de auditoria e verificação de acurácia de modelos.**

## 7.5 Qual é a relação dessa interface com o TCC?

- [x] Já fazia parte do TCC.
- [ ] É um aprofundamento de algo parcialmente previsto.
- [ ] É uma extensão conceitual criada para a disciplina.
- [ ] É um protótipo demonstrativo de aplicação potencial.
- [ ] Outra.

> **Declaração:** a interface desenvolvida nesta disciplina é um artefato de aprendizagem de IHC baseado no tema do TCC. Sua inclusão ou implementação no TCC somente ocorrerá se isso for posteriormente decidido pela equipe e pelo orientador.

---

# 8. Levantando possibilidades de interação — sem desenhar ainda

Marque apenas as que parecem plausíveis e explique o objetivo correspondente.

| Possibilidade | Pode fazer sentido? | Objetivo/tarefa que justificaria | Evidência atual |
|---|---|---|---|
| Dashboard/visão geral | talvez | Ver o status e estatísticas gerais dos benchmarks executados. | `[H]` |
| Configuração/parametrização | sim | Escolher de forma simplificada o fluxo (inferência simples ou Ralph Wiggum Loop) e o tamanho do modelo Llama 3.1 (8B, 70B, 405B) antes de executar. | `[F]` (demo possui esses seletores na tela inicial) |
| Entrada/upload/seleção de dados | sim | Enviar perguntas complexas para serem processadas pelo harness. | `[F]` (demo possui campo de input) |
| Acompanhamento de processamento | sim | Visualizar em tempo real cada subtarefa sendo executada e avaliada lógicamente. | `[F]` (demo possui painel timeline) |
| Relatório/resultados | sim | Visualizar a síntese final da resposta consolidada no final do loop. | `[F]` (demo possui painel de resultado) |
| Histórico com busca/filtros | talvez | Consultar execuções de perguntas passadas e comparar com novas execuções. | `[H]` |
| Comparação de resultados | talvez | Comparar lado a lado o fluxo com o Ralph Wiggum Loop versus uma chamada direta simples. | `[F]` (demo prevê alternar fluxos) |
| Explicabilidade/detalhamento | sim | Expandir um card de tarefa para ver os aprendizados extraídos e os critérios de aceite que passaram ou falharam. | `[F]` (demo possui tags e badges) |
| Administração/configurações globais | não | O harness é de uso pessoal/local do desenvolvedor. | `[H]` |
| Usuários/perfis/permissões | não | Sem necessidade de múltiplos usuários no escopo atual. | `[H]` |
| CRUD de entidade do domínio | não | Não aplicável ao domínio de orquestração. | `[H]` |
| Auditoria/logs | sim | Mostrar a contagem de tokens consumidos e o estado do contexto a cada etapa. | `[F]` (demo exibe consumo tk e status de novas janelas) |
| Alertas/ocorrências | sim | Indicar graficamente quando uma tarefa falha em um critério e precisa de nova tentativa. | `[F]` (demo tem verificação ✓/✗) |
| Ajuda/documentação | talvez | Oferecer documentação de ajuda contextual sobre como configurar as estratégias de orquestração. | `[H]` |

---

# 9. Benefícios e ações iniciais

## 9.1 Qual benefício concreto o projeto de IHC pretende oferecer?

| Benefício esperado | Problema/necessidade | Usuário | Status/evidência |
|---|---|---|---|
| Transparência e facilidade na auditoria de respostas de IA | Compreender o processo lógico adotado pela IA e monitorar se o consumo de tokens e a janela de contexto foram eficientes | Pesquisador / Estudante | `[H]` |

## 9.2 Que ações o usuário deverá conseguir realizar?

| ID | O usuário precisa conseguir... | Para alcançar... | Prioridade inicial |
|---|---|---|---|
| F01 | Enviar uma pergunta complexa em linguagem natural | Disparar a execução do loop de raciocínio da IA | Alta |
| F02 | Alternar entre o fluxo "Ralph Wiggum Loop" e "Inferência Simples" | Comparar a resposta estruturada com a resposta linear | Alta |
| F03 | Selecionar o modelo (Llama 3.1 8B, 70B, 405B) | Avaliar a execução do raciocínio em diferentes escalas de modelo | Alta |
| F04 | Visualizar cards detalhados por etapa com tags e contagem de tokens | Auditar o consumo e o isolamento de contexto (*Fresh Context*) | Alta |

## 9.3 Tecnologias/restrições já definidas no TCC

A tecnologia aparece **agora**, depois do entendimento do uso.

| Tecnologia/restrição | Por que existe | Possível impacto na interação |
|---|---|---|
| React 18 / TypeScript / Vite | Stack tecnológica padrão da equipe para desenvolvimento ágil e responsivo de front-ends modernos. | Permite atualizações em tempo real (streaming) na linha do tempo sem recarregar a página. |
| Comunicação por SSE (Server-Sent Events) | O processamento das fases do loop pelo backend é demorado, exigindo comunicação assíncrona. | Obriga o front-end a exibir estados parciais e carregamentos (stream de dados) de forma limpa ao usuário. |

---

# 10. Hipóteses e dúvidas prioritárias

| ID | Hipótese/dúvida | Por que importa | Como poderá ser investigada |
|---|---|---|---|
| H01 | Pesquisadores e estudantes preferem acompanhar a resolução lógica das subtarefas em formato de linha do tempo vertical (timeline) para validar e confiar na resposta final. | Define a arquitetura de informação e a disposição visual da tela principal (Open Thinking). | Prototipação em papel (Entrega 6) e avaliação heurística (Entrega 13). |
| H02 | A sinalização de sucesso (✓) ou falha (✗) dos critérios de aceite na timeline é suficiente para indicar quando a IA corrigiu o raciocínio. | Evita a sobrecarga cognitiva do usuário ao ler logs de texto longos de autocrítica do modelo. | Avaliação heurística (Entrega 13) e testes de usabilidade com usuários (Entrega 14). |


---

# 11. Síntese da equipe

| Pergunta | Síntese atual |
|---|---|
| Qual é a contribuição central do TCC? | O aprimoramento de outputs de LLMs via Ralph Wiggum Loop adaptado, mitigando o decaimento de contexto. |
| O TCC já previa interface? | Sim, uma interface de visualização do fluxo. |
| Quem é o usuário prioritário de IHC? | Pesquisadores, estudantes e analistas acadêmicos/profissionais. |
| O que ele precisa alcançar? | Compreender e auditar o processo de raciocínio de múltiplas fases do loop. |
| Qual problema/atividade será estudado? | A auditoria do fluxo de raciocínio e visualização dos custos e contexto das chamadas de LLM. |
| Como isso acontece hoje? | Leitura de respostas textuais diretas e opacas (caixa-preta) em chatbots comuns. |
| Qual é o contexto de uso? | Ambientes de estudo acadêmico, pesquisa e análise científica. |
| Que interface/recorte será explorado? | Painel de entrada de perguntas e linha do tempo de "Open Thinking" em tempo real. |
| Como a interface se relaciona ao TCC? | É a aplicação demonstrativa/visual integrada oficialmente no escopo do TCC. |
| Quais pontos ainda são hipóteses? | H01 e H02 (preferência por timeline e eficácia dos sinalizadores visuais ✓/✗). |

### Delimitação

**Dentro do escopo de IHC:** Visualização interativa da linha do tempo das tarefas, exibição de tokens/contexto por card, alertas visuais de loop/falha de critérios e seleção de modelo/fluxo.  
**Fora do escopo de IHC:** Persistência de banco de dados, chat generalista sem foco no Ralph Loop, controle fino de infraestrutura local de servidores (Ollama/LM Studio).  
**Dentro do escopo formal do TCC:** O algoritmo de orquestração do Ralph Loop adaptado, o serviço backend local, os testes de benchmark e o front-end web básico de controle.  
**Interface da disciplina será implementada no TCC?** sim — A interface projetada em IHC servirá diretamente como a demo web oficial do TCC.
---

# 12. Como esta entrega alimenta as próximas

- **Entrega 2:** verifica mercado, concorrentes e interfaces profissionais representativas.
- **Entrega 3:** detalha perfis e contexto.
- **Entrega 4:** aprofunda situações problemáticas.
- **Entrega 5:** modela tarefas centrais.
- **Entrega 6:** experimenta alternativas em baixa fidelidade.
- **Entrega 7:** investiga hipóteses com dados.
- **Entrega 8:** define restrições e metas de usabilidade.
- **Entregas 9–11:** transformam o recorte em modelo de interação e protótipo.
- **Entregas 12–14:** avaliam a interface construída na disciplina.

A Entrega 1 é uma **fotografia inicial do conhecimento**. Ela pode e deve ser revisada quando surgirem evidências.

---

# 13. Relação com INOVA e comunicação do projeto


1. **Problema/atividade humana:** Desenvolvedores e pesquisadores têm dificuldade em entender e auditar como a inteligência artificial chegou a uma resposta em tarefas lógicas complexas, além de sofrerem com a perda de qualidade quando a conversa fica longa demais (*context rot*).
2. **Contribuição técnica do TCC:** O TCC desenvolve um orquestrador que quebra a pergunta em tarefas de objetivo único, reinicializa o contexto a cada etapa para manter a mente do modelo limpa e valida logicamente os critérios de aceite de cada resposta antes de entregá-la.
3. **Como uma pessoa poderia utilizar essa contribuição:** O usuário interage com um dashboard em que envia sua pergunta complexa e acompanha em tempo real, através de uma linha do tempo intuitiva, como cada subtarefa foi planejada, executada, corrigida e compilada na resposta final.

---

# Checklist de qualidade

- [x] Está clara a diferença entre tema do TCC, escopo formal do TCC e escopo de IHC.
- [x] A equipe declarou se o TCC já previa interface.
- [ ] Se não previa, foi derivado um usuário plausível e um objetivo de uso.
- [x] A interface de IHC não foi apresentada como obrigação automática do TCC.
- [x] A contribuição do TCC foi descrita sem começar por tecnologias de implementação.
- [x] Usuários diretos e stakeholders foram diferenciados.
- [x] Foram considerados profissionais que configuram, administram, interpretam ou decidem, quando pertinente.
- [x] Objetivo do usuário não foi confundido com objetivo do projeto.
- [x] Processo/problema atual foi descrito antes da solução.
- [x] Existe situação concreta de uso/problema.
- [x] Contexto físico, social/organizacional, dispositivos e consequências de erro foram considerados.
- [x] Mercado/alternativas existentes foram levantados inicialmente.
- [x] Possibilidades como dashboard, relatório, histórico, filtros e CRUD foram tratadas como hipóteses de solução, não como requisitos automáticos.
- [x] Cada possibilidade de interface tem um objetivo/tarefa que poderia justificá-la.
- [x] Afirmações relevantes estão marcadas `[F]`, `[H]` ou `[?]`.
- [x] Hipóteses prioritárias receberam IDs e foram para a rastreabilidade.
- [x] O recorte de IHC é viável para modelar, prototipar e avaliar no semestre.
- [x] A equipe consegue explicar problema humano → contribuição computacional → forma de uso.
