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

Nosso TCC produz, melhora, analisa ou permite **orquestrar a resolução de perguntas complexas por meio de tarefas atômicas e aprendizados acumulados (*Fresh Context*), elevando a acurácia e a qualidade final das respostas dos modelos de linguagem**.

## 1.4 O que se espera que esteja diferente **para pessoas, organizações ou processos** se essa contribuição for bem-sucedida?

`[H]` **Acurácia e Confiabilidade:** Espera-se que usuários obtenham respostas significativamente mais precisas, lógicas e livres de alucinações para problemas complexos (como as questões avançadas do GPQA e MMLU) através do processo de orquestração e refinamento contínuo.

## 1.5 O que é mérito técnico/científico do TCC e o que seria uma possível aplicação prática?

| Mérito/contribuição técnica | Possível aplicação/valor em uso |
|---|---|
| Algoritmo de orquestração stateless inspirado no Ralph Wiggum Loop e sua avaliação empírica nos datasets MMLU/GPQA. | Sistemas corporativos de suporte à decisão, assistentes virtuais de auditoria técnica ou plataformas de resolução de problemas complexos multimétodo. |

---

# 2. Entendendo as pessoas envolvidas

## 2.1 Quem interage diretamente com o produto, se já existe interface prevista?

`[H]` **Estudantes, Pesquisadores, Empresas e Entusiastas de IA:** Usuários e organizações que submetem perguntas complexas de raciocínio (de múltipla escolha ou discursivas) e necessitam de respostas refinadas de alta qualidade e acurácia, com o auxílio de uma interface gráfica para selecionar o modelo, acompanhar a evolução da execução e verificar a coerência do resultado.

## 2.2 Quem poderia **usar, configurar, administrar, operar, interpretar ou tomar decisões** a partir da contribuição técnica?

| Perfil | Relação com a contribuição | O que faria | Status/evidência |
|---|---|---|---|
| Estudante / Pesquisador | Usuário final do sistema | Submete perguntas acadêmicas e científicas complexas para obter respostas sintetizadas de alta acurácia e qualidade | `[H]` |
| Empresa / Organização | Usuário corporativo e tomador de decisão | Utiliza o harness para resolver problemas lógicos de alta complexidade do seu domínio e seleciona o modelo de LLM adequado às suas demandas | `[H]` |
| Entusiasta de IA | Usuário explorador | Experimenta e avalia o ganho de qualidade e o desempenho do Ralph Wiggum Loop adaptado em comparação com inferências diretas | `[H]` |

## 2.3 Existem pessoas afetadas que não usariam a interface diretamente?

Não foram identificados stakeholders afetados que não utilizariam a interface diretamente.

<!-- | Stakeholder | Como é afetado | Usa interface? | Status/evidência |
|---|---|---|---|
| {{...}} | {{...}} | sim/não | {{...}} | -->

## 2.4 Que características desses perfis podem influenciar a interação?

`[H]` O público compreende estudantes, pesquisadores, empresas e entusiastas de IA que buscam respostas de alta fidelidade para problemas complexos.

## 3.1 O que o usuário está tentando conseguir no mundo real?

`[H]` Obter respostas de alta qualidade, acurácia e coerência lógica para perguntas de grande complexidade em linguagem natural.

## 3.2 Quais são as atividades mais importantes?

| ID | Atividade/objetivo | Quem realiza | Frequência/criticidade inicial | Status/evidência |
|---|---|---|---|---|
| A01 | Submeter a pergunta complexa para processamento no orquestrador | Estudantes, Pesquisadores, Empresas e Entusiastas | Alta frequência / Alta criticidade | `[F]` |
| A02 | Acompanhar a execução das fases de raciocínio e o progresso da geração da resposta | Estudantes, Pesquisadores, Empresas e Entusiastas | Alta frequência / Média criticidade | `[F]` |
| A03 | Selecionar o modelo de LLM que estamos utilizando | Empresas e Pesquisadores | Média frequência / Média criticidade | `[F]` |
| A04 | Melhorar as respostas dos modelos (decomposição, ciclos stateless e refinamento) | Projeto / Harness (Sistema) | Alta frequência / Alta criticidade | `[F]` |

## 3.3 Qual atividade parece mais frequente? Por quê?

`[F]` **Acompanhar a execução e a geração da resposta (A02):** Após submeter a pergunta, o usuário acompanha a evolução do processamento em tempo real enquanto o sistema atua para construir a resposta sintetizada.

## 3.4 Qual parece mais crítica? Que consequência existe se for mal executada?

`[F]` **Melhora das respostas dos modelos (A04):** A atividade mais crítica do projeto é garantir o ganho efetivo de acurácia e a melhoria da qualidade das respostas dos LLMs. Se a orquestração do harness falhar em aplicar a decomposição e o ciclo de refinamento do Ralph Wiggum Loop, o modelo entregará respostas imprecisas ou com falhas lógicas ao usuário.

---

# 4. Entendendo o problema ou processo atual

## 4.1 Como essas atividades são realizadas hoje, antes da interface imaginada na disciplina?

`[F]` **Processo atual sem o harness:** Usuários submetem perguntas complexas a LLMs tradicionais em chatbots (como ChatGPT ou Claude) ou chamadas de API diretas. Nesses cenários lineares, conforme o raciocínio se estende em perguntas difíceis, a acurácia tende a cair, gerando respostas imprecisas ou alucinadas. O TCC foi concebido com o objetivo inicial de melhorar a qualidade dessas respostas desenvolvendo um harness de orquestração stateless baseado no Ralph Wiggum Loop adaptado; posteriormente, implementou-se uma interface gráfica para permitir a seleção de modelos, o acompanhamento visual da execução e a facilidade de verificação do resultado.

## 4.2 O que é difícil, demorado, confuso, repetitivo, arriscado ou pouco transparente?

`[F]` A dificuldade principal em problemas complexos é a queda na qualidade e na acurácia das respostas à medida que o raciocínio se prolonga de forma linear. Sem uma arquitetura de decomposição de tarefas e ciclos de refinamento (Ralph Loop), a IA não consegue autocorrigir erros intermediários para gerar respostas melhores.

## 4.3 Que informações o profissional precisa interpretar para tomar decisão?

`[H]` A resposta sintetizada final, a acurácia e coerência da solução apresentada, o modelo de LLM selecionado para o processamento e o estado de progresso das tarefas na linha do tempo da interface gráfica.

## 4.4 O que acontece quando a atividade falha ou quando o resultado é interpretado incorretamente?

`[F]` O modelo entrega uma resposta incorreta ou imprecisa devido à ausência de refinamento no raciocínio, o que leva estudantes, pesquisadores e empresas a tomarem decisões baseadas em conclusões falhas.

## 4.5 Conte uma situação concreta.

`[F]` **Caso de uso do Ralph Wiggum Loop:** Maria, uma pesquisadora (ou representante de empresa), precisa resolver uma questão lógica complexa de biologia molecular. Ao utilizar um chatbot tradicional, a IA comete erros lógicos e entrega uma resposta incorreta. Ao utilizar o orquestrador do TCC, a pergunta é dividida em tarefas atômicas executadas pelo Ralph Wiggum Loop adaptado, permitindo autocrítica e reflexão para melhorar a resposta final. Com a adição posterior da interface gráfica, Maria pode selecionar o modelo de LLM desejado, acompanhar o raciocínio em tempo real e decidir com segurança se a resposta gerada está correta.

## 4.6 Que evidência existe hoje?

| Evidência/fonte | O que sustenta | Limitação |
|---|---|---|
| Literatura de LLMs e Benchmarks do TCC | A limitação na acurácia de LLMs em tarefas de raciocínio complexo e o ganho comprovado de qualidade com a orquestração do Ralph Loop nos datasets MMLU/GPQA. | Artigos da literatura e resultados dos testes de benchmark do projeto. |

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
| Chatbots tradicionais (ChatGPT, Claude) | Estudantes, pesquisadores, empresas e entusiastas | Submetem perguntas complexas de forma direta, mas enfrentam limitações de acurácia em raciocínios longos | `[F]` |
| Playgrounds de LLM (OpenAI Playground) | Empresas e pesquisadores | Testam prompts e comparam modelos de forma manual e sem ciclo de orquestração | `[F]` |
| Frameworks de Agentes / Prompt Engineering | Empresas e desenvolvedores | Implementam lógicas de prompt customizadas via código para tentar melhorar a qualidade das respostas | `[F]` |

## 6.2 Existem produtos que atuam na mesma área, mesmo sem serem equivalentes ao TCC?

`[F]` Frameworks de orquestração de agentes e ferramentas de engenharia de prompt / observabilidade de LLM.

## 6.3 Quais interfaces profissionais esse público já conhece?

`[F]` Interfaces de chat conversacional (ChatGPT, Claude), Playgrounds de IA e dashboards de acompanhamento de execução.

## 6.4 O que essas soluções parecem fazer bem?

`[F]` Responder a perguntas simples e diretas com alta velocidade e boa usabilidade.

## 6.5 O que parecem fazer mal, dificultar ou não atender?

`[H]` Não garantem a máxima acurácia em perguntas de raciocínio encadeado longo. Chatbots padrão não aplicam uma arquitetura de orquestração com ciclos de reflexão e autocorreção (Ralph Wiggum Loop) para assegurar que a resposta final seja a mais precisa possível. A visualização gráfica e o acompanhamento do pensamento ajudam o usuário a interpretar e validar o resultado, mas o diferencial central é a geração de respostas superiores.

## 6.6 Que padrões de interface ou vocabulário parecem familiares a esse público?

`[F]` Seleção de modelos de LLM, campo de entrada de texto (prompt), linhas de progresso (timeline de tarefas) e painéis de exibição de resultado sintetizado.

---

# 7. Derivando o escopo de IHC da disciplina

## 7.1 Escolha o caminho do projeto

### Caminho A — TCC já possui interface

Explique qual parte da interface será usada como recorte da disciplina e por que esse fluxo é relevante.

A interface demonstrativa web que exibe o fluxo do harness será o objeto principal. O recorte priorizado para IHC foca no monitoramento visual em tempo real das três fases de orquestração do loop (Setup, Loop de Raciocínio com reinicialização de contexto, e Síntese Final), permitindo ao usuário analisar visualmente e em detalhes como as tarefas atômicas mitigam o decaimento de contexto e o consumo de tokens correspondente a cada etapa.

## 7.2 Qual perfil será priorizado no projeto de IHC?

## 7.2 Qual perfil será priorizado no projeto de IHC?

Estudantes, Pesquisadores, Empresas e Entusiastas de IA.

**Por que esse perfil foi escolhido?** `[H]` Pois são as pessoas e organizações que utilizam o sistema para resolver problemas complexos e necessitam de respostas de alta acurácia sem sofrer degradação por *context rot*, beneficiando-se da seleção de modelos e do acompanhamento do fluxo de execução.

## 7.3 Qual objetivo desse usuário será priorizado?

Obter respostas com qualidade e acurácia superiores em perguntas complexas, acompanhando a evolução do raciocínio e a mitigação do decaimento de contexto através da interface.

## 7.4 Que interface será explorada na disciplina?

> **Para fins da disciplina de IHC, será projetada uma interface que permita a estudantes, pesquisadores, empresas e entusiastas utilizar o painel do Ralph Wiggum Loop adaptado para submeter perguntas, selecionar o modelo de LLM e acompanhar de forma transparente a decomposição, execução stateless e síntese de respostas de alta acurácia.**

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
| Respostas de LLMs com alta qualidade e acurácia, com acompanhamento visual do raciocínio | Dificuldade em obter respostas precisas em perguntas complexas e entender o fluxo de pensamento da IA para decidir se o resultado está correto | Estudantes, Pesquisadores, Empresas e Entusiastas | `[H]` |

## 9.2 Que ações o usuário deverá conseguir realizar?

| ID | O usuário precisa conseguir... | Para alcançar... | Prioridade inicial |
|---|---|---|---|
| F01 | Enviar uma pergunta complexa em linguagem natural | Disparar o orquestrador para gerar a resposta de alta qualidade | Alta |
| F02 | Selecionar o modelo de LLM (Llama 3.1 8B, 70B, 405B) | Escolher o modelo de linguagem mais adequado às necessidades do problema | Alta |
| F03 | Alternar entre o fluxo "Ralph Wiggum Loop" e "Inferência Simples" | Comparar a resposta refinada e estruturada com a resposta linear comum | Alta |
| F04 | Acompanhar a execução por etapas e métricas do fluxo | Visualizar a evolução do pensamento da IA e confirmar se a resposta final está correta | Alta |

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
| H01 | Estudantes, pesquisadores, empresas e entusiastas preferem acompanhar a resolução lógica das subtarefas em formato de linha do tempo vertical (timeline) para entender a geração da resposta. | Define a arquitetura de informação e a disposição visual da tela principal (Open Thinking). | Prototipação em papel (Entrega 6) e avaliação heurística (Entrega 13). |
| H02 | A sinalização de sucesso (✓) ou falha (✗) dos critérios de aceite na timeline é suficiente para indicar a autocorreção e o refinamento da resposta do modelo. | Evita a sobrecarga cognitiva do usuário ao ler logs de texto longos de autocrítica do modelo. | Avaliação heurística (Entrega 13) e testes de usabilidade com usuários (Entrega 14). |


---

# 11. Síntese da equipe

| Pergunta | Síntese atual |
|---|---|
| Qual é a contribuição central do TCC? | O aprimoramento de outputs de LLMs via Ralph Wiggum Loop adaptado, mitigando o decaimento de contexto. |
| O TCC já previa interface? | Sim, uma interface de visualização do fluxo. |
| Quem é o usuário prioritário de IHC? | Estudantes, pesquisadores, empresas e entusiastas de IA. |
| O que ele precisa alcançar? | Obter respostas de alta qualidade e acurácia em perguntas complexas de linguagem natural. |
| Qual problema/atividade será estudado? | A mitigação do decaimento de contexto (*context rot*) e a melhoria das respostas dos LLMs através da orquestração stateless. |
| Como isso acontece hoje? | Leitura de respostas textuais diretas em chatbots comuns (ChatGPT, Claude), que sofrem perda de qualidade em contextos longos. |
| Qual é o contexto de uso? | Ambientes de estudo acadêmico, pesquisa, escritórios corporativos e testes de entusiasmo tecnológico. |
| Que interface/recorte será explorado? | Painel de entrada de perguntas, seletor de modelos de LLM e linha do tempo de "Open Thinking" em tempo real. |
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


1. **Problema/atividade humana:** Estudantes, pesquisadores e empresas enfrentam o decaimento de qualidade das respostas de IA em perguntas complexas quando a conversa ou contexto fica longo demais (*context rot*).
2. **Contribuição técnica do TCC:** O TCC desenvolve um harness de orquestração stateless baseado no Ralph Wiggum Loop adaptado que divide a pergunta em tarefas atômicas e limpa o contexto a cada etapa, melhorando significativamente a acurácia do resultado final.
3. **Como uma pessoa poderia utilizar essa contribuição:** O usuário seleciona o modelo de LLM, envia sua pergunta complexa na interface gráfica e obtém uma resposta de alta precisão, podendo acompanhar em tempo real o progresso de execução e a evolução do raciocínio.

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
