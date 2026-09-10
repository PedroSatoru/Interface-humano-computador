# Entrega 2 — Público-alvo e análise de concorrência

**Data:** 09/09/2026
**Status:** [x] concluída
**Responsabilidade mínima:** cada integrante analisa pelo menos 1 concorrente/interface representativa; a equipe produz síntese comparativa.

## Objetivo da atividade

Compreender soluções do mesmo domínio **e também interfaces familiares ao público-alvo**. O objetivo não é copiar telas, mas identificar convenções, padrões, affordances percebidas, problemas recorrentes, expectativas e oportunidades de design.

> **Concorrente não precisa ser idêntico ao produto.** Pode atuar na mesma área, resolver objetivo semelhante ou disputar a mesma necessidade. Quando não houver concorrente direto, use produtos análogos e softwares que o público já utiliza.

## Entrada obrigatória da Entrega 1

A Entrega 1 identificou que o público prioritário do projeto de IHC — estudantes, pesquisadores, empresas e entusiastas de IA — já resolve problemas de raciocínio complexo hoje por meio de **chatbots conversacionais tradicionais** e, no caso de perfis mais técnicos, por meio de **assistentes de IA integrados ao fluxo de trabalho** (IDE, terminal, sistema operacional). Como o Ralph Wiggum Loop adaptado é, na prática, um harness de orquestração de agentes de IA que roda localmente e expõe seu raciocínio passo a passo, a equipe decidiu ampliar o mapa inicial de "chatbots" (Entrega 1, seção 6.1) para incluir também **ferramentas agenticas de linha de comando e de IDE**, que são a experiência mais próxima que existe hoje de "acompanhar uma IA executando tarefas em etapas com transparência de raciocínio".

| Item citado na Entrega 1 | Tipo | Por que foi citado | Status inicial | Decisão nesta entrega |
|---|---|---|---|---|
| Chatbots tradicionais (ChatGPT, Claude) | concorrente direto | Usados hoje pelo público-alvo para submeter perguntas complexas de forma direta | `[F]` | analisar (C03 — ChatGPT) |
| Playgrounds de LLM (OpenAI Playground) | análogo | Testam prompts e comparam modelos manualmente | `[H]` | descartado nesta rodada — a equipe optou por priorizar ferramentas agenticas com "linha do tempo de tarefas" visível, que são mais próximas do recorte de IHC (ver H01 na Entrega 1) do que um playground de teste de prompt isolado |
| Frameworks de agentes / prompt engineering | análogo | Implementam lógica de orquestração customizada via código | `[F]` | analisar como C01 (Claude Code) e C02 (GitHub Copilot), que são as materializações comerciais mais maduras desse padrão com interface de usuário |
| Assistentes de IA de sistema operacional | não citado na Entrega 1 | Surgiu durante a pesquisa desta entrega como interface "cotidiana" do público (Windows é o SO mais comum em notebooks acadêmicos e corporativos) | novo | analisar como C04 (Copilot do Windows) |

Esta entrega **confirma** a hipótese implícita na Entrega 1 (seção 6.5) de que chatbots padrão não expõem orquestração nem ciclos de reflexão visíveis ao usuário — ver síntese comparativa na seção 4. A hipótese `H01` (preferência por timeline vertical de subtarefas) permanece aberta e será investigada nas Entregas 6 e 13, mas os concorrentes C01 e C02 fornecem a primeira evidência de mercado de que **padrões de "linha do tempo de execução de agente" já existem e são utilizados por um público tecnicamente sofisticado**, o que é atualizado em [`../RASTREABILIDADE.md`](../RASTREABILIDADE.md).

## 1. Público-alvo desta análise

Conforme definido na Entrega 1 (seções 2.2 e 7.2): **estudantes, pesquisadores, empresas e entusiastas de IA** que precisam obter respostas de alta acurácia para perguntas complexas de raciocínio, e que se beneficiariam de acompanhar visualmente o processo de "pensamento" da IA para decidir se confiam no resultado.

Esse público já é usuário frequente de ferramentas de IA no cotidiano — seja para escrever código (desenvolvedores/pesquisadores técnicos), seja para produtividade geral (redação, pesquisa, e-mails). Por isso, os quatro concorrentes escolhidos representam as **três formas dominantes de interação com IA generativa que esse público já conhece**: (1) agente autônomo em terminal, (2) assistente integrado a IDE, (3) chat conversacional avulso e (4) assistente de sistema operacional de uso geral. Entender essas convenções é essencial porque a interface do harness do TCC (Entrega 1, seção 7.4) propõe um painel de "Open Thinking" que precisa competir, na cabeça do usuário, com a familiaridade que ele já tem com essas quatro experiências.

## 2. Concorrentes diretos/indiretos

### Análise C01 — Claude Code (CLI)

**Autor(a):** Vitor Monteiro Vianna — 22.223.085-6
**Tipo:** direto
**Link oficial:** https://claude.com/product/claude-code
**Data de acesso:** 09/09/2026

#### Contexto e proposta

`[F]` Claude Code é um agente de codificação da Anthropic operado via linha de comando (CLI), que roda diretamente no terminal do desenvolvedor, lê e edita arquivos do repositório, executa comandos de shell, testes e builds, e pode assumir tarefas de várias etapas de forma autônoma. Não é um "chat" isolado: ele opera sobre o contexto real do projeto do usuário (código, git, testes) e mantém uma sessão de trabalho que pode se estender por várias interações, reaproveitando contexto até que ele seja explicitamente limpo ou comprimido. É, entre os quatro concorrentes analisados, o mais próximo do domínio técnico do TCC: um harness de orquestração de IA que decompõe tarefas complexas e executa ciclos iterativos, distribuído hoje como produto comercial.

#### Funcionalidades relevantes

| Funcionalidade | Como é realizada | Evidência/print | Observação de IHC |
|---|---|---|---|
| Execução de tarefas em etapas autônomas | O agente planeja, executa comandos, lê resultados e decide o próximo passo sem que o usuário precise reformular o pedido a cada etapa | `../assets/02_concorrencia/...` | Reduz a carga de "prompting manual" repetido, mas cria risco de o usuário perder o controle do que está sendo feito — mitigado pelos modos de permissão |
| Modos de permissão (`ask`, `accept edits`, `plan`, `auto`, `bypass`) | O usuário alterna o nível de autonomia do agente com um atalho de teclado (Shift+Tab), controlando se cada ação (editar arquivo, rodar comando) precisa de aprovação explícita | `../assets/02_concorrencia/...` | `[F]` Padrão de controle de autonomia granular — relevante para o projeto, que também precisa comunicar "o que a IA vai fazer antes de fazer" nos critérios de aceite do Ralph Loop |
| Plan Mode (modo somente leitura) | Antes de alterar qualquer arquivo, o agente pode gerar um plano de execução revisável pelo usuário, que pode comentar trechos específicos do plano antes de aprovar | `../assets/02_concorrencia/...` | `[F]` Fonte: codewithmukesh.com, claudecode101.com (2026). É um padrão direto de "checkpoint humano antes de ação irreversível", equivalente conceitual aos critérios de aceite (✓/✗) do Ralph Wiggum Loop mencionados na Entrega 1 |
| Saída textual em stream no terminal (raciocínio + ações) | O progresso do agente aparece como texto corrido no terminal, misturando explicações, comandos executados e resultados | `../assets/02_concorrencia/...` | Não existe uma "timeline visual" estruturada por fases — todo o histórico é texto sequencial, o que dificulta escanear rapidamente o que já foi feito, um problema que a hipótese H01 do nosso projeto tenta evitar com timeline vertical segmentada |
| Contagem de uso/tokens vinculada ao plano de assinatura | O consumo do agente é contado contra os mesmos limites do plano Claude (Pro/Max), sem exibir custo granular por tarefa dentro da própria CLI | `../assets/02_concorrencia/...` | `[F]` Fonte: cloudzero.com, morphllm.com (2026). Ausência de visão clara de custo/token por etapa é uma lacuna que o nosso projeto pretende cobrir (Entrega 1, seção 5.5 e 9.2 — F04) |

#### Experiência do usuário e opiniões

`[F]` Fontes especializadas (claudecode101.com, vibecodingacademy.ai, 2026) descrevem o Plan Mode como "provavelmente o melhor padrão default para iniciar qualquer sessão" e recomendam um fluxo de trabalho onde o desenvolvedor gasta a maior parte do tempo revisando planos e supervisionando execução, e menos tempo escrevendo instruções repetidas. Isso indica que o público técnico já valoriza **transparência de plano antes da ação** como prática recomendada — reforça a hipótese H02 da Entrega 1 sobre a utilidade de sinalizadores de sucesso/falha antes de aceitar um resultado.

`[H]` Por ser uma interface 100% textual em terminal, sem elementos gráficos, a curva de aprendizado é maior para usuários não técnicos — algo que não se aplica diretamente ao nosso público prioritário (que inclui pesquisadores e entusiastas com menor familiaridade com terminal), reforçando a decisão de que a interface do TCC deve ser gráfica e visual, e não uma CLI.

#### Preço/modelo de negócio

`[F]` Claude Code não tem preço avulso: seu uso é incluído nos planos de assinatura Claude Pro (US$ 20/mês), Max 5x (US$ 100/mês) e Max 20x (US$ 200/mês), além de planos de equipe/empresa e cobrança por API sob demanda. Não há um nível gratuito permanente para uso contínuo da CLI. (Fonte: cloudzero.com, "Claude Code pricing in 2026", jul/2026)

#### Padrões e tendências percebidos

`[F]` Interação por "agente que trabalha em etapas visíveis, com pontos de checkpoint para aprovação humana" — este é o padrão de mercado mais próximo do modelo de interação que o harness do TCC (Ralph Wiggum Loop) propõe.

#### Pontos positivos, limitações e lições

| Ponto | Evidência | Implicação para nosso projeto |
|---|---|---|
| Modos de permissão com granularidade de autonomia (perguntar sempre / aceitar edições / somente planejar / autônomo) | `[F]` bitsminds.com, likeone.ai (2026) | Podemos oferecer um controle simples equivalente — por exemplo, escolher entre "acompanhar passo a passo" e "ver só o resultado final" — sem sobrecarregar o usuário com jargão técnico de permissões |
| Plan Mode como checkpoint revisável antes de agir | `[F]` codewithmukesh.com (2026) | Reforça o valor de exibir critérios de aceite (✓/✗) de forma clara antes de considerar uma tarefa concluída, como já planejado na Entrega 1 |
| Saída puramente textual/sequencial, sem estrutura visual por fase | `[H]` observação da equipe sobre a interface | Motiva a nossa proposta de timeline vertical segmentada por fases (Setup, Loop, Síntese) em vez de um log de texto corrido |
| Falta de visualização de custo/token por etapa dentro da ferramenta | `[F]` cloudzero.com (2026) | Valida a necessidade (F04, Entrega 1) de expor tokens consumidos e estado do contexto por card de tarefa, um diferencial claro do nosso projeto |

---

### Análise C02 — GitHub Copilot (integrado com IDE)

**Autor(a):** Vitor Monteiro Vianna — 22.223.085-6
**Tipo:** direto
**Link oficial:** https://github.com/features/copilot
**Data de acesso:** 09/09/2026

#### Contexto e proposta

`[F]` GitHub Copilot é um assistente de IA da GitHub/Microsoft integrado diretamente a IDEs (VS Code, Visual Studio, JetBrains, Neovim). Oferece autocompletar de código em tempo real, um painel de chat lateral, e um "Agent Mode" que assume tarefas completas de múltiplas etapas: planeja mudanças, edita vários arquivos, executa comandos de terminal, identifica e corrige erros de execução de forma autônoma (self-healing). Diferente do Claude Code, sua interface é predominantemente gráfica (painéis dentro do editor), não uma CLI pura.

#### Funcionalidades relevantes

| Funcionalidade | Como é realizada | Evidência/print | Observação de IHC |
|---|---|---|---|
| Agent Mode | O usuário descreve uma tarefa; o agente planeja, edita múltiplos arquivos, roda comandos e itera sobre os próprios resultados até concluir | `../assets/02_concorrencia/...` | `[F]` github.blog/newsroom (2026). Padrão de "descrever objetivo → IA decompõe em etapas → usuário revisa o resultado final", semelhante ao fluxo A01→A04 mapeado na Entrega 1 |
| Sugestões de comando de terminal editáveis inline | Comandos sugeridos pelo agente aparecem dentro da própria resposta de chat e podem ser editados pelo usuário antes de executar | `../assets/02_concorrencia/...` | `[F]` github.blog (2026). Bom padrão de "edição antes da confirmação", reduz erro por execução automática às cegas |
| Ações "Keep" / "Undo" por arquivo editado | Depois que o agente edita um arquivo, o usuário decide manter ou desfazer a mudança arquivo por arquivo, e a interface revela automaticamente o próximo arquivo alterado | `../assets/02_concorrencia/...` | `[F]` github.blog (2026). Padrão de feedback e recuperação de erro granular — relevante como inspiração para permitir aceitar/rejeitar aprendizados específicos de uma tarefa do Ralph Loop |
| Next Edit Suggestions / autocomplete | Sugestões de código aparecem enquanto o usuário digita, sem necessidade de prompt explícito | `../assets/02_concorrencia/...` | Fora do escopo do nosso projeto (não há "edição de código" na interface do harness), mas demonstra como IA pode se tornar "ambiente", não apenas "resposta a pedido" |
| Disponibilidade inconsistente entre IDEs | Agent Mode funciona plenamente no VS Code; em JetBrains, no momento da pesquisa, os recursos agenticos completos ainda não estavam disponíveis, apenas completions e chat padrão | `../assets/02_concorrencia/...` | `[F]` openaitoolshub.org (2026). Lição de IHC: fragmentação de funcionalidades entre plataformas gera expectativa quebrada — nosso projeto deve manter consistência entre estados/telas |

#### Experiência do usuário e opiniões

`[F]` Segundo avaliações agregadas (openaitoolshub.org, 2026, citando Trustpilot), usuários relatam **queda de qualidade de contexto em repositórios grandes** ("context drop-off") e sugestões que "produzem o resultado errado com confiança" — ou seja, a IA erra sem sinalizar incerteza. Esse é um paralelo direto com o problema central do TCC (*context rot*, Entrega 1, seção 1.2): mesmo um produto comercial maduro sofre do mesmo sintoma que o Ralph Wiggum Loop tenta mitigar, o que reforça a relevância do problema escolhido.

`[H]` A alternância entre "Keep" e "Undo" por arquivo é bem avaliada por reduzir a sensação de perda de controle, mas exige que o usuário revise várias vezes durante uma tarefa longa — pode gerar fadiga de decisão em tarefas com muitas subtarefas, um risco que nosso projeto deve evitar ao decidir a granularidade dos pontos de checkpoint na timeline.

#### Preço/modelo de negócio

`[F]` GitHub Copilot oferece um nível gratuito limitado (50 requisições de agente e 2.000 completions/mês) e planos pagos: Pro (US$ 10/mês), Pro+ (US$ 39/mês), Business (US$ 19/usuário/mês) e Enterprise (US$ 39/usuário/mês). Desde junho de 2026, a cobrança passou a ser baseada em "créditos de IA" em dólar por uso, substituindo o antigo modelo de cotas de "requisições premium". (Fonte: costbench.com, techjacksolutions.com, 2026)

#### Padrões e tendências percebidos

`[F]` Interação "dentro do fluxo de trabalho existente" (o editor de código), em vez de uma ferramenta separada — o usuário nunca precisa trocar de janela/app para interagir com a IA.

#### Pontos positivos, limitações e lições

| Ponto | Evidência | Implicação para nosso projeto |
|---|---|---|
| Ações granulares de aceitar/desfazer por unidade de trabalho (arquivo) | `[F]` github.blog (2026) | Inspira permitir que o usuário expanda um card de tarefa da timeline e avalie/aceite aprendizados específicos, não apenas o resultado final agregado (alinhado à possibilidade "Explicabilidade/detalhamento" da Entrega 1, seção 8) |
| Falha silenciosa de contexto em tarefas grandes, sem alertar o usuário | `[F]` openaitoolshub.org (2026) | Reforça a importância de tornar o *context rot* **visível** na interface (consumo de tokens, indicação de reinício de contexto), não apenas mitigado internamente pelo algoritmo |
| Fragmentação de recursos entre integrações/IDEs | `[F]` openaitoolshub.org (2026) | Alerta para manter uma experiência única e consistente na interface do TCC, em vez de funcionalidades parciais dependendo do "modo" selecionado |
| Modelo de cobrança por crédito de uso, difícil de prever | `[H]` observação da equipe a partir das fontes de pricing 2026 | Não se aplica diretamente ao harness (uso local/pessoal), mas confirma a importância de o painel de tokens/contexto (F04, Entrega 1) ajudar o usuário a entender custo de cada execução, evitando a opacidade que gera frustração nos concorrentes |

---

### Análise C03 — ChatGPT (chat online)

**Autor(a):** Vitor Monteiro Vianna — 22.223.085-6
**Tipo:** direto
**Link oficial:** https://chatgpt.com
**Data de acesso:** 09/09/2026

#### Contexto e proposta

`[F]` ChatGPT é o chatbot conversacional da OpenAI, acessado via navegador (ou apps dedicados), no formato clássico de "caixa de mensagem + histórico de conversa". É a interface mais familiar e mais usada do público-alvo, incluindo por perfis não técnicos (Entrega 1, seção 6.3 já cita ChatGPT/Claude como referência de interface conhecida). Também evoluiu para incluir recursos como Canvas (edição de documentos lado a lado), navegação web, análise de dados, geração de imagem e agora "Codex" para tarefas de código — mas o modo de interação permanece fundamentalmente **linear**: pergunta, resposta, próxima pergunta.

#### Funcionalidades relevantes

| Funcionalidade | Como é realizada | Evidência/print | Observação de IHC |
|---|---|---|---|
| Conversa em turnos lineares | Usuário digita, modelo responde em uma bolha de texto no mesmo fluxo de chat | `../assets/02_concorrencia/...` | `[F]` Padrão mais familiar ao público em geral; simples, porém não expõe nenhuma etapa intermediária de raciocínio de forma estruturada |
| Modos de raciocínio ("Thinking") | Para perguntas complexas, o usuário pode ativar um modo que faz o modelo "pensar mais" antes de responder, com tempo de espera maior | `../assets/02_concorrencia/...` | `[F]` metacto.com, cloudzero.com (2026). É o recurso mais próximo, em um chat comum, do conceito de "raciocínio em etapas" do Ralph Loop — mas o processo de pensamento não é exposto ao usuário como uma timeline, geralmente aparece resumido ou oculto |
| Deep Research | Executa pesquisas mais longas e autônomas na web, retornando um relatório consolidado ao final | `../assets/02_concorrencia/...` | `[F]` Também opera em várias etapas internas (buscar, ler, sintetizar), mas o usuário só vê o resultado final ou um resumo do progresso, não um log de subtarefas com critérios de aceite |
| Canvas | Abre um painel lateral de edição para documentos/código, permitindo iteração direta sobre o conteúdo gerado | `../assets/02_concorrencia/...` | Bom padrão de "duas colunas" (conversa + artefato em construção) que pode inspirar a divisão entre timeline de execução e painel de resposta final na interface do TCC |
| Memória entre conversas | O modelo retém preferências e fatos relevantes do usuário entre sessões distintas | `../assets/02_concorrencia/...` | Fora do escopo do harness (execuções são majoritariamente pontuais), mas relevante como padrão de "histórico" citado na Entrega 1, seção 8 (talvez aplicável) |

#### Experiência do usuário e opiniões

`[F]` Fontes especializadas (tldv.io, cloudzero.com, 2026) descrevem a Plus como o nível em que "ChatGPT se torna uma ferramenta profissional de verdade" — ou seja, a percepção de utilidade profissional aumenta com acesso a modos de raciocínio mais lentos e específicos, o que sugere que usuários avançados **já esperam trocar velocidade por qualidade** em tarefas difíceis, validando a proposta de valor do Ralph Wiggum Loop (mais lento, porém mais preciso).

`[H]` Por ser uma interface unicamente linear, sem uma visão estruturada por fases, é comum o usuário perder o fio de raciocínio em respostas muito longas ou precisar rolar a conversa inteira para entender como o modelo chegou a uma conclusão — esse é o problema central que a hipótese H01 (timeline vertical) tenta resolver.

#### Preço/modelo de negócio

`[F]` ChatGPT oferece seis níveis em 2026: Free (gratuito, com limites e anúncios "Sponsored Tips"), Go (US$ 8/mês), Plus (US$ 20/mês), um nível intermediário Pro de US$ 100/mês (lançado em abril de 2026), Pro completo (US$ 200/mês), além de Business (US$ 25/usuário/mês) e Enterprise (sob consulta). (Fonte: tldv.io, felloai.com, 2026)

#### Padrões e tendências percebidos

`[F]` Interação conversacional linear como formato universal, reconhecido até por usuários leigos — é o "menor denominador comum" de interface de IA que todo o público-alvo já domina.

#### Pontos positivos, limitações e lições

| Ponto | Evidência | Implicação para nosso projeto |
|---|---|---|
| Formato de chat é extremamente familiar e reduz a barreira de entrada | `[F]` observação de mercado amplamente documentada | O campo de entrada de pergunta do harness (F01, Entrega 1) deve seguir essa convenção simples (caixa de texto única), mesmo que o restante da interface seja diferente de um chat |
| "Thinking mode" existe, mas o raciocínio interno raramente é exposto de forma estruturada ao usuário final | `[F]` metacto.com (2026) | Reforça a oportunidade de diferenciação do nosso projeto: tornar o raciocínio "visível e auditável" por fase, e não apenas indicar "pensando..." |
| Formato de conversa linear dificulta comparar duas respostas ou reconstruir "como" uma conclusão foi alcançada | `[H]` observação da equipe | Justifica a proposta de comparação de fluxos (F03, Entrega 1 — Ralph Loop × Inferência Simples) como diferencial de interface, algo que um chat tradicional não oferece nativamente |
| Canvas separa "conversa" de "artefato em elaboração" em duas colunas | `[F]` recurso documentado da OpenAI | Padrão de layout aplicável: manter a timeline de tarefas separada visualmente do painel de resposta final sintetizada |

---

### Análise C04 — Copilot (padrão do Windows)

**Autor(a):** Vitor Monteiro Vianna — 22.223.085-6
**Tipo:** indireto/análogo
**Link oficial:** https://www.microsoft.com/microsoft-copilot
**Data de acesso:** 09/09/2026

#### Contexto e proposta

`[F]` O Copilot do Windows é o assistente de IA de propósito geral embutido no sistema operacional, acessível pela barra de tarefas ("Ask Copilot"), com suporte a voz (ativação por comando "Hey, Copilot"), visão computacional sobre a tela do usuário (Copilot Vision) e integração com apps do sistema (Explorer, Configurações). Não é uma ferramenta de codificação; representa o público mais amplo e menos técnico dentro do perfil "entusiasta de IA" definido na Entrega 1 — a pessoa que usa IA no dia a dia sem necessariamente saber o que é um "prompt" ou uma "janela de contexto".

#### Funcionalidades relevantes

| Funcionalidade | Como é realizada | Evidência/print | Observação de IHC |
|---|---|---|---|
| "Ask Copilot" na barra de tarefas | Substitui a caixa de busca estática por uma entrada multimodal conversacional, sempre visível e a um clique de distância | `../assets/02_concorrencia/...` | `[F]` windowsforum.com (2026). Excelente exemplo de affordance de baixo esforço cognitivo: a IA está sempre "à mão", sem precisar abrir um app separado |
| Ativação por voz ("Hey, Copilot") | Palavra de ativação local, opcional (opt-in), habilitada nas configurações | `../assets/02_concorrencia/...` | `[F]` windowsforum.com (2026). Padrão de acessibilidade e conveniência, mas desligado por padrão — reforça a boa prática de manter captura de voz/tela como recurso opt-in explícito, relevante caso o projeto do TCC considere entradas alternativas no futuro |
| Copilot Vision | Usuário compartilha a tela e a IA "enxerga" o conteúdo para ajudar em uma tarefa em andamento | `../assets/02_concorrencia/...` | `[F]` windowsforum.com (2026). Fora do escopo do harness, mas ilustra a tendência de IA como "camada de assistência contínua" sobre o que o usuário já está fazendo, e não uma ferramenta isolada |
| Integração com apps do sistema (Explorer, Configurações) | A IA pode agir sobre arquivos e configurações do próprio sistema operacional, não apenas responder texto | `../assets/02_concorrencia/...` | `[F]` windowsforum.com (2026). Traz a discussão de governança: quanto mais ações autônomas a IA pode tomar sobre o ambiente do usuário, maior a necessidade de transparência e possibilidade de desfazer — tema central também no harness do TCC |
| Rollout gradual via Windows Insider (recurso experimental) | As funcionalidades mais recentes (voz, visão na barra de tarefas) ainda estão em fase de teste controlado, desligadas por padrão | `../assets/02_concorrencia/...` | `[F]` windowsforum.com (2026). Boa prática de introdução gradual de funcionalidades de IA, evitando sobrecarregar usuários não preparados |

#### Experiência do usuário e opiniões

`[H]` Por estar embutido no sistema operacional e ser "sempre visível", o Copilot do Windows tem a menor barreira de acesso entre os quatro concorrentes analisados, mas também é o que **menos expõe qualquer forma de raciocínio ou processo intermediário** — a experiência é a de um assistente que "simplesmente responde ou age", sem qualquer visualização de etapas, tarefas ou critérios de validação. Isso o torna o exemplo mais distante do padrão de transparência que o projeto do TCC busca oferecer, mas também o mais representativo de "como usuários leigos esperam que uma IA se comporte por padrão" (ação direta, sem necessidade de entender o processo).

`[?]` A equipe não localizou avaliações de usabilidade formais e específicas (estudos de UX publicados) sobre a experiência do Copilot na barra de tarefas do Windows, apenas cobertura jornalística de lançamento de recursos — item registrado como lacuna de evidência.

#### Preço/modelo de negócio

`[F]` O Copilot do Windows está incluído gratuitamente no sistema operacional para funcionalidades básicas de assistente; recursos avançados de produtividade (Microsoft 365 Copilot, com acesso a modelos como Claude Opus 4.8 e GPT-5.5 Reasoning dentro de Word/Excel/PowerPoint/Teams) exigem assinatura corporativa separada, tipicamente cobrada por usuário/mês dentro de planos Microsoft 365. (Fonte: techcommunity.microsoft.com, 2026)

#### Padrões e tendências percebidos

`[F]` IA como "camada ambiente" do sistema operacional, sempre disponível e multimodal (texto, voz, visão), priorizando velocidade de acesso sobre profundidade de controle ou transparência de processo.

#### Pontos positivos, limitações e lições

| Ponto | Evidência | Implicação para nosso projeto |
|---|---|---|
| Acesso de um clique/comando de voz, sempre visível na barra de tarefas | `[F]` windowsforum.com (2026) | Não aplicável à arquitetura do harness (é uma aplicação web dedicada), mas reforça que o campo de entrada da pergunta (F01) deve estar imediatamente visível e sem etapas de navegação prévias |
| Recursos multimodais avançados desligados por padrão (opt-in) | `[F]` windowsforum.com (2026) | Boa prática de introdução gradual: se o projeto do TCC evoluir para incluir parâmetros avançados (ex.: seleção de modelo 405B, mais lenta/cara), esses devem ficar "escondidos" atrás de uma ação explícita, não como padrão |
| Nenhuma exposição de processo de raciocínio ou etapas intermediárias | `[H]` observação da equipe | Confirma que, entre os quatro concorrentes, nenhum oferece nativamente a "timeline de raciocínio por fases" proposta na Entrega 1 — reforça que esse é o principal espaço de diferenciação do projeto de IHC |
| Integração de ações diretamente sobre arquivos/configurações do usuário sem histórico visível de auditoria consultado nesta pesquisa | `[?]` lacuna de evidência | Reforça a importância que já havíamos identificado (Entrega 1, seção 5.5) de que toda execução do harness precise manter rastreabilidade auditável — um diferencial que nenhum dos quatro concorrentes demonstra de forma clara e acessível ao usuário final |

## 3. Softwares que o público-alvo usa no cotidiano

| Software | Por que o público usa | Padrões relevantes | Prints | O que aprender |
|---|---|---|---|---|
| VS Code (com GitHub Copilot) | IDE padrão de mercado para desenvolvimento, onde estudantes/pesquisadores/desenvolvedores já esperam ter assistência de IA integrada | Painel lateral de chat, sugestões inline, "Agent Mode" | (adicionar manualmente) | Layout de painel lateral persistente pode inspirar onde posicionar a timeline de execução em relação ao editor de pergunta |
| Terminal / linha de comando | Público técnico (pesquisadores, desenvolvedores, entusiastas avançados) já está habituado a interfaces de texto sequencial para tarefas de IA (Claude Code e ferramentas similares) | Saída em stream, cores para diferenciar tipos de mensagem, atalhos de teclado para controle de modo | (adicionar manualmente) | Uso de cores/ícones consistentes (✓/✗, status de execução) já é convenção aceita por esse público, reforçando a viabilidade da proposta de sinalizadores visuais (H02) |
| ChatGPT / Claude (apps e web) | Uso diário para tirar dúvidas, redigir textos, resumir, programar — é a porta de entrada mais comum de IA generativa para todo o público-alvo, inclusive perfis não técnicos | Chat linear, histórico de conversas na lateral, upload de arquivo | (adicionar manualmente) | O campo de entrada de texto (prompt) deve seguir a convenção já dominada por esse público: caixa única, botão de enviar, indicação clara de "carregando" |
| Windows 11 (com Copilot na barra de tarefas) | Sistema operacional mais comum em notebooks acadêmicos e corporativos no Brasil, cada vez mais embutindo IA como recurso padrão do SO | Assistente sempre acessível, multimodal, opt-in para recursos sensíveis (voz/visão) | (adicionar manualmente) | Reforça que o público já naturaliza a presença de IA no ambiente de trabalho cotidiano, o que reduz a necessidade de "explicar o que é IA" na interface do TCC e permite focar em explicar o diferencial do Ralph Loop |

## 3.1 Padrões de interface relevantes ao escopo de IHC

| Padrão observado | Produto(s) | Para qual tarefa serve | Vantagem percebida | Risco/limitação | Aplicável ao nosso escopo? |
|---|---|---|---|---|---|
| Checkpoint revisável antes de ação (Plan Mode) | Claude Code | Confirmar decisão da IA antes de mudanças irreversíveis | Reduz erro e aumenta confiança do usuário | Pode adicionar fricção/latência à interação se usado em excesso | sim — inspira exibir claramente os critérios de aceite (✓/✗) antes de considerar uma tarefa concluída |
| Aceitar/desfazer por unidade de trabalho | GitHub Copilot | Dar controle granular sobre mudanças geradas pela IA | Usuário não precisa aceitar "tudo ou nada" | Fadiga de decisão em tarefas com muitas subtarefas | talvez — pode ser aplicado a nível de card de tarefa na timeline, mas com moderação para não sobrecarregar o usuário |
| Modo de "pensar mais" (raciocínio estendido, oculto ou resumido) | ChatGPT | Sinalizar que a IA está em processamento mais profundo para perguntas difíceis | Comunicação simples de "vale a pena esperar" | Não expõe o processo de raciocínio de forma auditável | sim, parcialmente — nosso projeto vai além, expondo cada subtarefa da timeline, não apenas um indicador genérico de "pensando" |
| IA sempre visível como camada ambiente (barra de tarefas) | Copilot do Windows | Reduzir esforço de acesso à IA no fluxo de trabalho | Baixíssima barreira de entrada | Nenhuma transparência de processo/raciocínio | não — o harness é uma aplicação dedicada para análise aprofundada, não um assistente de acesso instantâneo; a proposta de valor está exatamente na transparência que esse padrão sacrifica |
| Histórico de conversas/execuções na lateral | ChatGPT, GitHub Copilot Chat | Retomar contexto de interações anteriores | Familiar e De baixo custo de implementação | Pode não ser prioritário no escopo inicial do harness (uso mais pontual) | talvez — já listado como "talvez" na Entrega 1 (seção 8, "Histórico com busca/filtros") |
| Dashboard/relatório consolidado | nenhum dos concorrentes analisados oferece nativamente para tarefas de raciocínio de IA | Visualizar o resultado final de forma clara | — | — | sim — já validado como F04/parte do escopo (painel de resultado + métricas de tokens/contexto), e é um diferencial claro em relação aos quatro concorrentes |

> O objetivo não é concluir "todo concorrente tem dashboard, então teremos um". O padrão só será adotado se apoiar uma tarefa rastreável.

## 4. Síntese comparativa da equipe

| Critério | C01 (Claude Code) | C02 (GitHub Copilot) | C03 (ChatGPT) | Oportunidade para o projeto |
|---|---|---|---|---|
| Navegação | Terminal, comandos e atalhos de teclado (Shift+Tab para modos) | Painel lateral dentro do IDE, integrado ao editor | Chat linear em página única, histórico lateral | Interface web dedicada, com navegação simples entre entrada de pergunta, timeline e resultado — sem exigir conhecimento de atalhos de terminal |
| Feedback/estado | Texto em stream contínuo, sem estrutura visual por fase | Indicadores de "Keep/Undo" por arquivo, comandos editáveis inline | Indicador de "pensando"/"gerando", sem detalhamento de etapas | Timeline vertical estruturada por fase (Setup, Loop, Síntese), com status visível por card de tarefa (proposta já validada na Entrega 1) |
| Prevenção/recuperação de erro | Plan Mode como checkpoint antes de agir; modos de permissão graduais | Ações granulares de aceitar/desfazer por arquivo | Regenerar resposta; pouco controle sobre o processo interno | Critérios de aceite (✓/✗) visíveis por tarefa, permitindo entender exatamente onde e por que uma etapa falhou (H02) |
| Terminologia | Termos técnicos (permission mode, plan mode, tokens) | Termos técnicos de IDE (agent mode, edits, diffs) | Linguagem simples e conversacional, acessível a leigos | Traduzir conceitos técnicos do harness (Fresh Context, tarefas atômicas) para linguagem acessível ao público não puramente técnico (pesquisadores, empresas), como já indicado na Entrega 1 |
| Acessibilidade | Depende inteiramente de teclado e leitura de texto no terminal; sem suporte nativo a leitores de tela estruturados | Interface gráfica dentro do IDE, herda acessibilidade do editor host | Interface web com suporte razoável a leitores de tela e temas claro/escuro | Adotar boas práticas de acessibilidade web (contraste, navegação por teclado, textos alternativos para os ícones ✓/✗) desde a prototipação |
| Eficiência | Alta para usuários técnicos experientes com terminal; baixa curva de familiaridade para leigos | Alta dentro do fluxo já existente do desenvolvedor (sem trocar de app) | Alta para perguntas pontuais simples; baixa para acompanhar raciocínio longo/complexo | Buscar equilíbrio: interface visual que não exija conhecimento de terminal (como C01), mas que exponha profundidade de processo que C02/C03 não oferecem |

## 5. Recomendações derivadas

- **RC01:** Adotar uma timeline vertical estruturada por fases (Setup, Loop de Raciocínio, Síntese), com indicadores visuais de status por tarefa — derivada da ausência desse padrão estruturado em C01, C02 e C03, que apresentam raciocínio como texto corrido ou indicador genérico de "pensando".
- **RC02:** Exibir critérios de aceite (✓/✗) de forma clara antes de considerar uma etapa concluída, inspirado no Plan Mode de C01 (checkpoint revisável) e nas ações "Keep/Undo" de C02 (controle granular de aprovação).
- **RC03:** Expor consumo de tokens e estado de contexto por card de tarefa na interface, cobrindo uma lacuna identificada tanto em C01 (contagem de uso não granular na CLI) quanto em C02 (queda de qualidade de contexto sem alerta ao usuário) — reforça diretamente a necessidade F04 já registrada na Entrega 1.
- **RC04:** Manter o campo de entrada de pergunta como uma caixa de texto única e simples, seguindo a convenção já dominada pelo público em C03 (ChatGPT), evitando exigir conhecimento prévio de "prompt engineering" ou sintaxe de comando como em C01.
- **RC05:** Traduzir termos técnicos do harness (tarefas atômicas, Fresh Context, decaimento de contexto) para linguagem acessível ao público misto (técnico e não técnico) do projeto, evitando a terminologia excessivamente técnica observada em C01 e C02.
- **RC06:** Tornar a comparação entre fluxos (Ralph Wiggum Loop × Inferência Simples, já prevista como F03 na Entrega 1) um recurso visível na interface, já que nenhum dos quatro concorrentes analisados oferece comparação lado a lado de estratégias de raciocínio dentro da mesma sessão.
- **RC07:** Introduzir parâmetros avançados (ex.: seleção de modelo 405B, mais lento e caro) de forma opcional/expansível, e não como padrão inicial da tela — inspirado na prática de opt-in de recursos sensíveis observada em C04 (Copilot do Windows).

## Referências

- Claude Code — página oficial do produto. Disponível em: https://claude.com/product/claude-code. Acesso em: 09/09/2026.
- CloudZero. "Claude Code pricing in 2026: every plan, the real monthly costs, and which one is worth it." Disponível em: https://www.cloudzero.com/blog/claude-code-pricing/. Acesso em: 09/09/2026.
- codewithmukesh.com. "Claude Code Plan Mode for .NET Developers." Disponível em: https://codewithmukesh.com/blog/plan-mode-claude-code/. Acesso em: 09/09/2026.
- claudecode101.com. "Claude Code Plan Mode." Disponível em: https://claudecode101.com/en/mechanics/plan-mode. Acesso em: 09/09/2026.
- BitsMinds. "Claude Code's Five Permission Modes, Explained." Disponível em: https://www.bitsminds.com/news/claude-code-permission-modes-explained-2026. Acesso em: 09/09/2026.
- GitHub Copilot — página oficial do produto. Disponível em: https://github.com/features/copilot. Acesso em: 09/09/2026.
- GitHub Changelog. "Inline agent mode in preview and more in GitHub Copilot for JetBrains IDEs." Disponível em: https://github.blog/changelog/2026-04-24-inline-agent-mode-in-preview-and-more-in-github-copilot-for-jetbrains-ides/. Acesso em: 09/09/2026.
- GitHub Newsroom. "GitHub Copilot Introduces Agent Mode and Next Edit Suggestions." Disponível em: https://github.com/newsroom/press-releases/agent-mode. Acesso em: 09/09/2026.
- OpenAIToolsHub. "GitHub Copilot Agent Mode: Tested for Real Dev Workflows." Disponível em: https://www.openaitoolshub.org/en/blog/github-copilot-agent-mode-review. Acesso em: 09/09/2026.
- costbench.com. "GitHub Copilot Pricing 2026." Disponível em: https://costbench.com/software/ai-coding-assistants/github-copilot/. Acesso em: 09/09/2026.
- ChatGPT — página oficial do produto. Disponível em: https://chatgpt.com. Acesso em: 09/09/2026.
- tldv.io. "ChatGPT Pricing: My Honest Take on the 2026 Plans." Disponível em: https://tldv.io/blog/chatgpt-pricing/. Acesso em: 09/09/2026.
- CloudZero. "ChatGPT pricing in 2026." Disponível em: https://www.cloudzero.com/blog/how-much-does-chatgpt-cost/. Acesso em: 09/09/2026.
- metacto.com. "ChatGPT Pricing 2026: Plans, API Costs & Tiers." Disponível em: https://www.metacto.com/blogs/understanding-chatgpt-costs-usage-setup-integration-and-maintenance. Acesso em: 09/09/2026.
- Microsoft Copilot — página oficial do produto. Disponível em: https://www.microsoft.com/microsoft-copilot. Acesso em: 09/09/2026.
- Windows Forum. "Ask Copilot on Windows 11: Taskbar AI, Vision, and Voice Unveiled." Disponível em: https://windowsforum.com/threads/ask-copilot-on-windows-11-taskbar-ai-vision-and-voice-unveiled.385048/. Acesso em: 09/09/2026.
- Windows Latest. "Microsoft tests a Windows 11 taskbar feature that lets AI see your open apps." Disponível em: https://www.windowslatest.com/2026/02/22/microsoft-tests-a-windows-11-taskbar-feature-that-lets-ai-see-your-open-apps-when-you-share-window/. Acesso em: 09/09/2026.
- Microsoft Tech Community. "What's New in Microsoft 365 Copilot | June 2026." Disponível em: https://techcommunity.microsoft.com/blog/microsoft365copilotblog/what%E2%80%99s-new-in-microsoft-365-copilot--june-2026/4529572. Acesso em: 09/09/2026.

## Checklist

- [x] O mapa inicial de alternativas da Entrega 1 foi revisitado e aprofundado.
- [x] Hipóteses relevantes sobre mercado/padrões foram atualizadas na rastreabilidade quando surgiram evidências.
- [x] Há pelo menos uma análise completa por integrante. *(nesta rodada, as quatro análises foram conduzidas por Vitor Monteiro Vianna; os demais integrantes podem revisar/complementar conforme a divisão de trabalho da equipe)*
- [ ] Cada análise contém prints legíveis da interface. *(prints serão adicionados manualmente pela equipe, conforme solicitado)*
- [ ] Prints mostram telas/estados relevantes, não apenas logos/homepage.
- [x] Foram analisados concorrentes e/ou interfaces representativas ao público.
- [x] Em TCC sem interface original, foram investigadas ferramentas profissionais análogas às atividades do usuário escolhido. *(neste caso o TCC já previa interface, mas ainda assim foram investigadas ferramentas análogas de mercado, conforme seção 6 da Entrega 1)*
- [x] Padrões como dashboard, relatório, filtros e CRUD foram analisados como soluções para tarefas, não como requisitos automáticos.
- [x] Opiniões de UX têm fonte.
- [x] A síntese compara critérios comuns e produz recomendações.
- [x] Não há "copiar porque o concorrente faz"; há justificativa de adequação ao público/contexto.
