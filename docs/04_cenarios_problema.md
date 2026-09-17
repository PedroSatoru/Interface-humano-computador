# Entrega 4 — Cenários de análise/problema

**Data:** 16/09/2026  
**Status:** 🟩 concluída  
**Responsabilidade:** 1 solução completa por integrante (4 integrantes: Pedro Correia, Vitor Vianna, Pedro Satoru e Hugo Nomura)

## Objetivo da atividade

Descrever situações atuais em que o usuário tenta alcançar um objetivo e encontra dificuldades no mundo real. O cenário de análise/problema torna visível **o contexto, os atores, as ações, as informações e as rupturas**, retratando a prática humana existente hoje **sem antecipar a interface ou a solução tecnológica** que será projetada no decorrer da disciplina.

> **Regra central:** O cenário de problema é a “história do problema”. Se o texto disser “o sistema mostra”, “o aplicativo resolve”, “o usuário clica no botão” ou descrever telas e componentes futuros, estará misturando problema com solução. A narrativa deve retratar fielmente como as pessoas executam suas tarefas hoje, com quais ferramentas lidam, onde ocorrem as falhas e quais as consequências dessas rupturas.

Cada cenário aprofunda e fundamenta situações concretas já identificadas na [Entrega 1](01_conhecendo_o_problema.md), na [Entrega 2](02_analise_concorrencia.md) e na modelagem das personas da [Entrega 3](03_personas_contexto_jornada.md), utilizando como substrato o domínio técnico do TCC **"Um Harness de IA para Resolução de Perguntas em Linguagem Natural: Adaptando o Ralph Wiggum Loop Além do Desenvolvimento de Software"** (FEI, 2026).

---

## Cenário C01 — Investigação e validação de premissas bioquímicas em questão de alta complexidade do benchmark GPQA

**Autor(a):** Pedro Henrique Correia de Oliveira — 22.222.009-7  
**Persona(s) relacionada(s):** P01 — Dra. Mariana Siqueira (Pesquisadora e Doutoranda em Bioinformática)  
**Necessidade relacionada:** R01 — Mitigar o decaimento de contexto (*context rot*) e obter alta acurácia lógica em deduções complexas de linguagem natural  
**Situação concreta da Entrega 1 relacionada:** Seção 4.5 (Caso de uso da pesquisadora resolvendo questão complexa de biologia molecular e sofrendo com alucinações e premissas esquecidas) e Seção 1.2 / 4.1  
**Hipóteses ainda presentes:** `H01` (preferência por formato de linha do tempo vertical para inspeção de etapas), `H02` (sinalização visual de critérios de aceite para validação rápida)

### 1. Cenário inicial

Mariana precisa validar uma questão avançada de pós-graduação sobre cinética enzimática e transdução de sinal em receptores GPCR com mutação alostérica, com o objetivo de incorporar a dedução formal em um capítulo de sua tese de doutorado. Ela abre o ChatGPT Plus no navegador de seu notebook, formula um enunciado longo contendo cinco restrições biológicas e físico-químicas específicas e envia a mensagem. O assistente gera uma resposta longa e detalhada. Conforme Mariana lê o texto corrido, percebe que a explicação parece coesa e convincente, mas desconfia do valor numérico final do equilíbrio de dissociação. Para tirar a dúvida, ela envia mensagens de acompanhamento pedindo para o modelo detalhar a terceira etapa. Após três trocas de mensagens na mesma conversa, o modelo apresenta uma nova equação que contradiz uma das premissas inibitórias estabelecidas no primeiro prompt. Mariana percebe que a ferramenta "esqueceu" a restrição inicial devido ao volume de texto acumulado no chat. Sentindo-se insegura, Mariana fecha a aba do navegador, abre seus livros de referência e cadernos de cálculo e passa a tarde inteira recalculando manualmente as constantes termodinâmicas no papel para ter certeza de não publicar um erro em sua qualificação.

### 2. Questões de refinamento

A tabela a seguir aplica a taxonomia de questões de análise de cenários (*Scenario-Based Design* — Rosson & Carroll, 2002; Barbosa & Silva, 2021) para revelar facetas críticas que estavam implícitas ou ausentes na narrativa inicial:

| # | Dimensão / Taxonomia | Questão | Por que precisa ser respondida | Fonte / forma de obter resposta |
|---|---|---|---|---|
| Q1 | **Contexto e Ambiente** | Em qual ambiente físico e operacional Mariana realiza essa atividade, com quais restrições de tempo e equipamentos periféricos? | Permite compreender se a atividade ocorre sob pressão de prazos acadêmicos, iluminação adversa e se há espaço de tela para leitura paralela de artigos. | [Entrega 3 (seção 1 — P01 e seção 3 — contexto)](03_personas_contexto_jornada.md); observação da rotina de pós-graduandos em laboratório. |
| Q2 | **Recursos e Informações** | Quais fontes de dados externas, artigos e anotações Mariana precisa confrontar com o texto gerado pelo chatbot para detectar a inconsistência? | Identifica os artefatos de informação de apoio (fórmulas, tabelas de constantes, artigos no Overleaf) necessários para o julgamento humano. | Literatura científica do domínio (benchmarks GPQA — Rein et al., 2023) e rotina de escrita científica em LaTeX. |
| Q3 | **Ações e Práticas** | Que estratégias ou "gambiarras" de engenharia de prompt Mariana adota atualmente para tentar contornar a perda de contexto no chat tradicional? | Revela as tentativas frustradas do usuário de forçar o modelo a manter o contexto (ex.: reescrever prompts com instruções em caixa alta ou abrir novas conversas). | [Entrega 3 (seção 2 — Mapa de Empatia de P01)](03_personas_contexto_jornada.md) e relatos de uso de LLMs em pesquisa acadêmica. |
| Q4 | **Rupturas e Falhas** | Como exatamente a falha do modelo se manifesta no texto e por que o formato monolítico do chat dificulta identificar o erro de imediato? | Torna visível a natureza insidiosa do *context rot*: a resposta é gramaticalmente polida e formal, camuflando a quebra da restrição física no meio de parágrafos extensos. | Literatura de *context rot* e *Lost in the Middle* (Liu et al., 2023; Hong et al., 2025; paper do TCC, seção II-B). |
| Q5 | **Consequências e Impacto** | Qual é o custo acadêmico, temporal e emocional desse retrabalho para o cronograma de Mariana e sua credibilidade profissional? | Dimensiona a severidade do problema no mundo real: perda de horas de pesquisa de bancada, atraso na submissão de artigo qualificado e ansiedade por falta de reprodutibilidade. | [Entrega 3 (seção 4 — Jornada de P01)](03_personas_contexto_jornada.md) e entrevistas informais da Entrega 1. |

### 3. Cenário refinado

Mariana está em sua estação de trabalho no laboratório compartilhado de bioinformática da universidade, **[NOVO: trabalhando sob forte pressão pelo prazo final de submissão de um artigo para um periódico internacional qualificado e com a reunião de acompanhamento com seu orientador agendada para o dia seguinte]**. Ela utiliza um notebook corporativo acoplado a um monitor ultrawide de 34 polegadas, **[NOVO: mantendo na metade esquerda da tela o editor Overleaf com seu manuscrito em LaTeX e duas abas de PDFs abertas com dados empíricos de mutações em receptores GPCR]**. Para acelerar a dedução formal das constantes cinéticas de uma questão interdisciplinar estilo GPQA, Mariana acessa a interface web do ChatGPT Plus na metade direita da tela.

Ela digita um prompt minucioso e denso, contendo cinco premissas físico-químicas estritas sobre a ligação inibitória alostérica. **[NOVO: Como já vivenciou episódios anteriores em que o chatbot ignorou instruções, Mariana adota uma prática defensiva de prompting: escreve regras em caixa alta no final da mensagem, como "NÃO IGNORE A CONSTANTE DE DISSOCIAÇÃO Ki = 0.4 nM" e pede explicitamente para a IA listar o passo a passo de cálculo]**. O modelo gera um bloco extenso de quatro parágrafos em tom extremamente formal e confiante.

Ao conferir o resultado final contra os limites termodinâmicos tabulados no artigo de referência, Mariana nota uma incongruência sutil. Para investigar o cálculo, envia uma réplica no chat: *"Explique detalhadamente como você chegou à fração de ocupação do estado inativo na etapa 3"*. O assistente responde imediatamente com mais três parágrafos densos. Mariana envia uma terceira mensagem pedindo para reavaliar a concentração do ligante. **[NOVO: Nesse momento, ocorre a ruptura crítica provocada pelo acúmulo de contexto na sessão (*context rot*): a janela de atenção do modelo, sobrecarregada com os parágrafos anteriores de justificativas textuais, sofre degradação silenciosa; o modelo substitui inadvertidamente a constante inibitória Ki por uma taxa de ativação agonista Ka, sem emitir nenhum aviso de conflito ou mudança de premissa. O texto corrido esconde o erro sob uma prosa acadêmica impecável, com símbolos matemáticos elegantes em LaTeX, fazendo com que a fórmula pareça perfeita à primeira vista]**.

Mariana gasta cerca de quarenta minutos relendo os parágrafos anteriores até isolar exatamente onde a premissa foi corrompida. **[NOVO: A constatação provoca profunda exaustão mental e frustração: a pesquisadora percebe que o modelo não é capaz de manter coerência estrita quando submetido a diálogos que exigem rastreabilidade matemática contínua. Sem nenhuma forma de auditar se cada restrição foi formalmente checada antes da conclusão, ela desiste do assistente, fecha a janela do chat e passa três horas e meia refazendo as deduções à mão em um caderno pautado e planilhas eletrônicas. Esse retrabalho compromete a revisão dos demais tópicos do manuscrito daquele dia, força-a a estender a jornada até a madrugada e reforça seu receio de que alucinações sutis passem despercebidas em suas futuras publicações acadêmicas]**.

### 4. Elementos extraídos

| Elemento | Evidência no cenário |
|---|---|
| **Ator(es)** | Dra. Mariana Siqueira (29 anos, pesquisadora e doutoranda em Bioinformática). |
| **Objetivo(s)** | Resolver e validar uma dedução bioquímica complexa multidisciplinar (estilo benchmark GPQA) com rigor formal e sem inconsistências lógicas para embasar sua tese e artigo científico. |
| **Contexto** | Laboratório de bioinformática compartilhado da universidade; notebook com monitor externo ultrawide 34"; uso paralelo de Overleaf/LaTeX e leitores de PDF; pressão severa por prazos de publicação acadêmica. |
| **Recursos/informações** | Artigos científicos em PDF com dados empíricos de mutação GPCR; parâmetros cinéticos e termodinâmicos (Ki, concentrações); editor Overleaf/LaTeX; caderno de anotações; interface web comercial de chat (ChatGPT Plus). |
| **Ações** | Formulação de prompt longo com regras em caixa alta; envio de mensagens iterativas solicitando detalhamento de cálculos intermediários; leitura e escaneamento visual de blocos monolíticos de texto; conferência manual cruzada de equações no papel. |
| **Problemas/rupturas** | Decaimento progressivo de contexto (*context rot*) na conversa linear; o modelo esquece premissas inibitórias iniciais e troca variáveis silenciosamente; ausência total de validação formal por critérios de aceite; camuflagem de erros sob tom de escrita convincente e polido. |
| **Consequências** | Desperdício de mais de 3 horas de trabalho braçal refazendo contas à mão; atraso na finalização do manuscrito para submissão; estresse e esgotamento mental; insegurança metodológica perante a banca e pares acadêmicos. |

### 5. Implicações para as próximas entregas

- **Análise de Tarefas (Entrega 5):** Modelar com prioridade as tarefas de **"Submeter pergunta complexa com restrições lógicas explícitas"** e **"Auditar etapas intermediárias e validação de critérios de aceite"** (candidatas às técnicas HTA e CTT). A modelagem deve contemplar como o usuário decompõe mentalmente o problema em premissas e como necessita confirmar que nenhuma premissa foi esquecida.
- **Coleta de Dados e Restrições (Entregas 7 e 8):** Investigar o nível de tolerância de pesquisadores a tempos de espera mais longos quando há garantia explícita de verificação passo a passo, contrapondo velocidade superficial com acurácia rigorosa.
- **Diretrizes de Design (Entregas 9 a 11):** Não desenhar soluções agora, mas registrar que a interface futura não poderá depender de conversação linear contínua. Será indispensável prover meios de expor visualmente o cumprimento de critérios de aceite (✓/✗) e a certeza de que etapas avançadas operam com dados limpos (*Fresh Context*), evitando a sobrecarga de leitura de parágrafos densos.

---

## Cenário C02 — Auditoria de custos, consumo opaco de tokens e rastreabilidade de decisões em parecer técnico corporativo

**Autor(a):** Vitor Monteiro Vianna — 22.223.085-6  
**Persona(s) relacionada(s):** P02 — Carlos Eduardo Prado (Consultor Técnico e Arquiteto de Soluções de IA)  
**Necessidade relacionada:** R02 — Monitorar telemetria de tokens e janelas de contexto para eficiência de custos; R04 — Comprovar a validação de critérios de aceite antes da síntese final  
**Situação concreta da Entrega 1 relacionada:** Seção 4.4 (consequências de decisões baseadas em conclusões falhas), Seção 5.5 (necessidade de histórico, rastreabilidade e auditoria para fins comerciais) e Seção 2.2  
**Hipóteses ainda presentes:** `H01`, `H02`

### 1. Cenário inicial

Carlos precisa redigir um parecer técnico recomendando uma arquitetura de LLM para um grande cliente do setor financeiro que automatizará a análise preliminar de risco em operações de crédito para médias empresas. Para embasar sua recomendação entre modelos de diferentes portes, Carlos utiliza ferramentas comerciais e playgrounds de IA disponíveis no mercado. Ele submete um caso de teste com demonstrativos financeiros complexos e políticas de compliance do banco. O modelo retorna uma análise recomendando a aprovação do crédito com ressalvas. No entanto, quando o comitê de governança e auditoria do cliente questiona por que uma certidão negativa vencida não impediu a aprovação, Carlos não consegue demonstrar em qual etapa do processamento aquela regra foi checada. Além disso, ao consultar o painel de faturamento da API, Carlos se depara com um custo agregado de tokens muito superior ao estimado na proposta comercial, sem discriminação de quantos tokens foram gastos em planejamento, em raciocínio intermediário ou na saída final. Sem evidências auditáveis de conformidade e sem clareza de custos, Carlos precisa suspender a apresentação do parecer e refazer as simulações em planilhas manuais.

### 2. Questões de refinamento

A tabela a seguir aplica a taxonomia de questões de análise de cenários (*Scenario-Based Design* — Rosson & Carroll, 2002; Barbosa & Silva, 2021) para aprofundar os aspectos corporativos e regulatórios do problema de Carlos:

| # | Dimensão / Taxonomia | Questão | Por que precisa ser respondida | Fonte / forma de obter resposta |
|---|---|---|---|---|
| Q1 | **Atores e Papéis** | Quais stakeholders compõem o comitê do cliente e que exigências formais de compliance eles impõem sobre a consultoria de Carlos? | Revela a cadeia decisória corporativa (CFO, Diretor de Riscos, Compliance) e por que "confiança cega" em IA é inaceitável no setor financeiro. | [Entrega 3 (seção 1 — P02)](03_personas_contexto_jornada.md); normas regulatórias do setor bancário (LGPD, Basileia). |
| Q2 | **Recursos e Informações** | De quais métricas granulares de consumo de contexto e custos Carlos precisa para defender o retorno sobre investimento (ROI) da solução? | Mostra que métricas agregadas mensais de tokens (típicas de dashboards de nuvem) são insuficientes para calcular o custo unitário por parecer gerado. | Análise de concorrência com APIs e planos de assinatura ([Entrega 2, seção 2 — Claude Code e ChatGPT](02_analise_concorrencia.md)). |
| Q3 | **Ações e Práticas** | Como Carlos tenta rastrear manualmente o comportamento da IA hoje e correlacionar custos com acurácia? | Evidencia o processo penoso atual: exportar logs brutos em CSV, cruzar timestamps com a fatura da nuvem e tentar estimar gastos em planilhas Excel. | Prática comum de arquitetos de soluções em nuvem e engenharia de prompt corporativa. |
| Q4 | **Rupturas e Falhas** | Onde a caixa-preta dos modelos comerciais falha em fornecer explicabilidade para decisões de crédito de alto valor? | Aponta a ruptura central: os modelos tradicionais geram apenas a resposta final consolidada, omitindo se critérios eliminatórios foram avaliados e aprovados de forma estrita. | [Entrega 1 (seção 6.5 e 8 — Explicabilidade)](01_conhecendo_o_problema.md); literatura de governança de IA. |
| Q5 | **Consequências e Impacto** | Qual o prejuízo financeiro, contratual e de reputação sofrido pela consultoria caso o parecer seja rejeitado pelo comitê? | Evidencia o impacto no negócio: risco de rescisão de contrato de consultoria de alto valor, retrabalho de semanas e desgaste perante a diretoria executiva. | [Entrega 3 (seção 1 — P02, dores e motivadores)](03_personas_contexto_jornada.md). |

### 3. Cenário refinado

Carlos está em uma sala de reuniões corporativa, preparando a documentação final de um projeto de consultoria estratégica para um banco comercial de grande porte. **[NOVO: O projeto prevê a implementação de um fluxo automatizado de IA para subsidiar a tomada de decisão em operações de crédito empresarial de até R$ 5 milhões, exigindo conformidade rigorosa com normas do Banco Central e auditoria externa de modelos]**. Utilizando seu notebook corporativo ThinkPad de 14 polegadas conectado à rede corporativa, Carlos precisa provar ao Comitê de Risco e ao Diretor de Tecnologia (CTO) que o modelo de linguagem selecionado respeita as políticas regulatórias e possui viabilidade financeira previsível.

Para simular o fluxo com as ferramentas atuais de mercado, Carlos utiliza o playground de uma API comercial de LLMs, submetendo um dossiê corporativo composto por demonstrativos contábeis, relatórios de auditoria e sete regras restritivas de crédito. **[NOVO: Como o playground opera como uma caixa-preta em chamada única de inferência, Carlos envia todo o material em um mega-prompt de entrada de 12.000 tokens e aguarda o retorno]**. O modelo gera um parecer favorável à concessão do crédito com taxa bonificada.

No entanto, ao analisar a fundamentação textual para preencher o formulário de aprovação, Carlos busca evidências de que a certidão de débitos tributários com apontamento restritivo foi efetivamente considerada. **[NOVO: A resposta do modelo é generalista e omite completamente qualquer menção à certidão tributária; no formato tradicional de resposta contínua, é impossível determinar se o modelo avaliou o critério e decidiu relevá-lo, se o dado foi descartado por compressão de contexto no meio do texto ou se a instrução simplesmente se perdeu. Carlos sabe que, se apresentar esse parecer ao comitê de compliance sem a comprovação formal de que o critério eliminatório foi verificado e reprovado (✗), a consultoria será sumariamente desqualificada por negligência de governança]**.

Para piorar o cenário, Carlos abre o painel financeiro da nuvem para tabular a estimativa de custos por parecer gerado. **[NOVO: A fatura da plataforma de IA exibe apenas uma cobrança consolidada de milhares de tokens, sem discriminar quanto foi gasto na ingestão do contexto inicial, quanto foi consumido no processo de raciocínio intermediário e quanto custou a geração do texto final. Sem telemetria segregada por fase, Carlos não consegue justificar na planilha orçamentária por que chamadas encadeadas custaram cinco vezes mais do que o previsto, nem consegue calcular o custo unitário por cliente para a diretoria financeira (CFO)]**.

**[NOVO: Diante do impasse a menos de 24 horas da reunião com o comitê, Carlos é forçado a cancelar a apresentação preliminar, arcar com o constrangimento profissional de solicitar dilação de prazo e passar o fim de semana inteiro criando planilhas manuais no Excel para auditar linha por linha os balanços dos clientes e reconstituir estimativas de custos de inferência. A falta de explicabilidade estruturada e a opacidade na telemetria de tokens transformam o uso da IA em um passivo de risco para sua consultoria, em vez de uma alavanca de produtividade]**.

### 4. Elementos extraídos

| Elemento | Evidência no cenário |
|---|---|
| **Ator(es)** | Carlos Eduardo Prado (38 anos, Consultor Técnico e Arquiteto de Soluções de IA Corporativa). |
| **Objetivo(s)** | Comprovar a viabilidade técnica e financeira da orquestração de LLMs e emitir parecer técnico com conformidade auditável e custos transparentes para tomada de decisão em concessão de crédito. |
| **Contexto** | Ambiente de consultoria corporativa e salas de reunião; notebook ThinkPad 14"; interação com comitês de risco bancário, conformidade e governança sob pressão por aprovação regulatória. |
| **Recursos/informações** | Dossiês financeiros empresariais (balanços, certidões fiscais); políticas de crédito do cliente; playground de API de modelos de IA comercial; dashboards consolidados de faturamento de tokens na nuvem; planilhas financeiras de ROI no Excel. |
| **Ações** | Submissão de mega-prompts com documentos anexados em APIs de modelos de linguagem; busca visual por evidências de conformidade em textos longos; exportação de relatórios agregados de fatura da nuvem; reconstrução manual de cálculos e auditoria em planilhas eletrônicas. |
| **Problemas/rupturas** | Opacidade total das decisões intermediárias (caixa-preta); impossibilidade de saber se critérios eliminatórios de compliance foram verificados ou ignorados; telemetria de tokens agregada e não granular (impossível saber o consumo de contexto vs raciocínio); risco de descumprimento regulatório. |
| **Consequências** | Cancelamento de reunião decisiva com diretoria de cliente financeiro; constrangimento profissional e risco de rescisão contratual; retrabalho manual exaustivo em planilhas de contingência; insegurança quanto à escalabilidade econômica da solução. |

### 5. Implicações para as próximas entregas

- **Análise de Tarefas (Entrega 5):** Modelar tarefas de **"Parametrizar modelo e avaliar compensação entre custo de inferência e acurácia"** e **"Auditar telemetria de tokens e cumprimento de critérios por etapa"** (HTA/GOMS em T02).
- **Engenharia de Usabilidade e Metas (Entrega 8):** Estabelecer metas claras de visibilidade do estado do sistema para métricas financeiras e de telemetria (ex.: discriminação imediata de tokens consumidos por chamada sem necessidade de consultar dashboards externos de faturamento).
- **Diretrizes de Design (Entregas 9 a 11):** A interface futura deverá prover recursos de visualização executiva colapsável (para que Carlos possa apresentar resultados limpos a diretores) combinados com detalhamento sob demanda (*progressive disclosure*) do consumo de tokens por subtarefa e chips visuais inequívocos de critérios de aceite auditáveis.

---

## Cenário C03 — Comparação empírica de desempenho e depuração de vazamento de contexto entre frameworks de agentes

**Autor(a):** Pedro Henrique Satoru Lima Takahashi — 22.123.019-6  
**Persona(s) relacionada(s):** P03 — Lucas Zanin (Engenheiro de Software Backend e Entusiasta de IA de Código Aberto)  
**Necessidade relacionada:** R03 — Avaliar experimentalmente o ganho de acurácia da orquestração stateless frente à inferência baseline (comparação de fluxos); R02 — Inspecionar a renovação limpa de contexto (*Fresh Context*)  
**Situação concreta da Entrega 1 relacionada:** Seção 6.1 e 9.2 (requisito F03 — alternar entre fluxos para comparar respostas refinadas com lineares comuns) e Seção 1.3 / 8  
**Hipóteses ainda presentes:** `H01` (preferência por timeline vertical estruturada frente a logs contínuos de terminal), `H02` (sinalização de sucesso/falha de critérios)

### 1. Cenário inicial

Lucas deseja avaliar se a aplicação de um ciclo de decomposição de tarefas e autocrítica realmente supera uma inferência simples e direta para um conjunto de perguntas lógicas desafiadoras do benchmark MMLU utilizando o modelo Llama 3.1 8B rodando localmente. Para realizar essa comparação, ele abre o VS Code em seu computador com Linux e escreve scripts em Python utilizando uma biblioteca popular de agentes de IA (LangChain). Ele dispara a execução de um script no terminal integrado. O terminal começa a rolar centenas de linhas de log ininterruptas, exibindo mensagens intermediárias de pensamento, chamadas de funções e respostas do modelo. Ao final de dez minutos, o script conclui a tarefa e exibe uma resposta correta, mas Lucas nota que o modelo demorou muito mais do que o esperado nas últimas perguntas. Ao tentar depurar o log para entender se a resposta foi obtida por raciocínio dedutivo limpo ou se houve contaminação da memória entre as etapas, Lucas se depara com um arquivo de log monolítico de milhares de linhas, onde o histórico de prompts anteriores foi reenviado repetidamente acumulando ruído. Sem conseguir isolar visualmente o estado da janela de contexto de cada tarefa nem comparar lado a lado com a inferência direta, Lucas desiste de analisar a execução e sente que perdeu horas depurando código em vez de avaliar a técnica.

### 2. Questões de refinamento

A tabela a seguir aplica a taxonomia de questões de análise de cenários (*Scenario-Based Design* — Rosson & Carroll, 2002; Barbosa & Silva, 2021) para investigar o contexto de desenvolvimento e as dificuldades de instrumentação técnica de Lucas:

| # | Dimensão / Taxonomia | Questão | Por que precisa ser respondida | Fonte / forma de obter resposta |
|---|---|---|---|---|
| Q1 | **Contexto e Equipamento** | Qual é o setup de desenvolvimento de Lucas e quais ferramentas de sistema operacional e monitoramento ele emprega no dia a dia? | Compreende o ambiente de alta densidade técnica (monitores múltiplos, Linux, scripts shell, Ollama/vLLM) e a familiaridade do usuário com inspeção de dados. | [Entrega 3 (seção 1 — P03 e seção 3 — contexto)](03_personas_contexto_jornada.md). |
| Q2 | **Recursos e Informações** | Quais arquivos de estado intermediários, payloads JSON e variáveis de ambiente Lucas tenta inspecionar manualmente durante a execução dos scripts? | Mapeia os dados que o desenvolvedor busca auditar (tamanho da janela em tokens, payloads de entrada/saída, flags de critérios de aceite). | Arquitetura técnica do TCC (`apps/backend/src/application/usecases/chain_of_thought_usecase.py` e `docs/desenhos/fluxo_thinking_macro.md`). |
| Q3 | **Ações e Práticas** | Como Lucas tenta hoje realizar a comparação lado a lado entre uma chamada direta simples e a execução por agente? | Revela a fricção do fluxo atual: rodar scripts separados em abas diferentes do terminal, salvar saídas em arquivos de texto txt/json e usar comandos `diff` manualmente. | [Entrega 2 (seção 2 — Claude Code CLI)](02_analise_concorrencia.md) e observação de práticas de desenvolvedores backend. |
| Q4 | **Rupturas e Falhas** | Como o acúmulo de contexto nos frameworks de agentes convencionais gera o problema de vazamento silencioso (*memory leak* semântico) no terminal? | Explica o mecanismo de falha: frameworks comuns concatenam mensagens anteriores no histórico, inflando a janela até degradar a acurácia sem que o log indique onde ocorreu o vazamento. | Paper do TCC (seção I e seção II-A sobre limitações de agentes de mercado); Hong et al. (2025). |
| Q5 | **Consequências e Impacto** | Qual é o impacto do cansaço visual e da frustração decorrente da análise de logs brutos no progresso dos experimentos de Lucas? | Mostra a consequência prática: tempo excessivo gasto escrevendo código de instrumentação temporário, incerteza sobre a validade científica do benchmark e perda de entusiasmo com a tecnologia. | [Entrega 3 (seção 1 — P03, dores)](03_personas_contexto_jornada.md). |

### 3. Cenário refinado

Lucas está em seu escritório doméstico durante o fim de semana, com iluminação reduzida, **[NOVO: operando uma máquina desktop de alto desempenho com Linux Ubuntu e dois monitores de 27 polegadas calibrados em Dark Mode, rodando uma instância local do Llama 3.1 8B via Ollama para evitar custos de inferência em nuvem]**. Seu objetivo é validar empiricamente para sua equipe de microsserviços se a orquestração em tarefas independentes com contexto limpo realmente gera ganhos de acurácia que justifiquem a latência adicional, tomando como base uma questão de múltipla escolha capciosa sobre matrizes e números primos do dataset MMLU.

Para testar a abordagem atual, Lucas abre o VS Code no monitor principal e divide a tela com o terminal Linux. **[NOVO: Como não dispõe de uma interface pronta de orquestração comparativa, Lucas escreve um script temporário em Python utilizando o framework LangChain, configurando um agente com memória de conversação para tentar quebrar a pergunta em subtarefas. Em paralelo, em uma segunda aba do terminal, ele executa um script em cURL fazendo uma chamada de inferência direta simples ao mesmo modelo Llama 3.1 8B, salvando a resposta em um arquivo `baseline_output.txt`]**.

Lucas dispara o script do agente. O terminal começa a jorrar um fluxo desordenado de texto com logs brutos em formato ANSI colorido, misturando prompts intermediários, metadados internos da biblioteca e saídas parciais. **[NOVO: Para tentar monitorar se as subtarefas estão operando de forma isolada, Lucas espalhou diversos comandos `print(json.dumps(...))` pelo código Python. No entanto, o volume de texto no terminal ultrapassa rapidamente o buffer de rolagem. Na terceira subtarefa, Lucas nota que o modelo alucinou ao classificar o número 6 como primo. Ao tentar inspecionar o porquê do erro, depara-se com um log de mais de 8.000 linhas de texto contínuo: o framework de agentes acumulou silenciosamente todo o raciocínio das tarefas 1 e 2 no histórico do prompt da tarefa 3, gerando uma janela de contexto inchada e com ruído que induziu o modelo à falha (*context rot*)]**.

**[NOVO: Para conseguir contrastar a resposta do agente com a saída direta do arquivo `baseline_output.txt`, Lucas precisa abrir uma terceira janela de terminal e executar o utilitário `diff -u` entre os arquivos de log gerados, tentando decifrar manualmente se a divergência entre as respostas decorreu de um erro lógico na formulação do plano ou do vazamento indevido de contexto entre as etapas intermediárias]**.

**[NOVO: Após duas horas de trabalho árduo inspecionando strings de JSON no terminal e recalculando contagens de tokens por estimativa manual, Lucas encerra a sessão sentindo enorme fadiga visual e frustração. Ele constata que gastou 80% do seu tempo depurando a infraestrutura opaca do framework e formatando logs de terminal, e apenas 20% analisando o valor conceitual da técnica. Sem um mecanismo que permita alternar fluxos com facilidade e inspecionar visualmente se o contexto de cada etapa foi efetivamente reinicializado de forma limpa (*Fresh Context*), Lucas fica impossibilitado de demonstrar de forma inequívoca à sua equipe técnica as vantagens da arquitetura de orquestração]**.

### 4. Elementos extraídos

| Elemento | Evidência no cenário |
|---|---|
| **Ator(es)** | Lucas Zanin (25 anos, Engenheiro de Software Backend e Entusiasta de IA de código aberto). |
| **Objetivo(s)** | Comparar experimentalmente o ganho de acurácia de um ciclo agentico com decomposição de tarefas em relação a uma inferência direta simples (baseline) para perguntas complexas do MMLU, inspecionando o isolamento de contexto entre as etapas. |
| **Contexto** | Estação de desenvolvimento pessoal com desktop Linux Ubuntu e dois monitores de 27" em tema escuro; execução local de LLMs (Ollama) e scripts em Python. |
| **Recursos/informações** | Modelos open-source Llama 3.1 8B; scripts em Python com LangChain; chamadas via terminal cURL; arquivos de log txt e JSON; utilitários de sistema (`diff`, `grep`); questões do benchmark MMLU. |
| **Ações** | Redação de scripts de instrumentação; execução concorrente em abas de terminal; inserção de `print` statements para depurar payloads; rolagem exaustiva de logs textuais de terminal; execução de comandos de comparação (`diff`) entre arquivos de saída. |
| **Problemas/rupturas** | Logs em terminal excessivamente verbosos e não estruturados por fases; vazamento silencioso de histórico entre tarefas em frameworks convencionais de agentes (acúmulo de contexto sem limpeza); falta de um meio integrado e direto para alternar e comparar dois fluxos de inferência; esforço cognitivo exaustivo de depuração. |
| **Consequências** | Desperdício de horas de lazer e estudo em tarefas braçais de infraestrutura e formatação de logs; fadiga visual decorrente de leitura de logs monolíticos; incapacidade de comprovar cientificamente para sua equipe o impacto positivo da renovação de contexto. |

### 5. Implicações para as próximas entregas

- **Análise de Tarefas (Entrega 5):** Modelar tarefas de **"Alternar entre fluxos de inferência (Ralph Loop vs Inferência Simples)"** e **"Inspecionar sob demanda detalhes de execução e estado de renovação de contexto"** (candidatas às modelagens GOMS e CTT, destacando as regras de seleção entre modos de visualização).
- **Modelo Conceitual e Signos (Entrega 9):** Mapear com precisão signos que comuniquem claramente ao usuário quando uma janela de contexto foi reinicializada (*Fresh Context* / reset) e quando aprendizados anteriores foram reutilizados, eliminando a ambiguidade de caixas-pretas de agentes.
- **Diretrizes de Design (Entregas 9 a 11):** A interface futura deverá contemplar um controle evidente de alternância de fluxo e prover opções visuais distintas (ex.: visão de linha do tempo hierárquica versus modo transcrição contínua), garantindo que dados técnicos avançados possam ser inspecionados sem poluir a visão semântica principal.

---

## Cenário C04 — Dificuldade na compreensão e validação passo a passo de exercícios complexos de lógica e matemática discreta

**Autor(a):** Hugo Emílio Nomura — 22.123.051-9  
**Persona(s) relacionada(s):** P04 — Beatriz Fagundes (Estudante de Graduação em Engenharia da Computação e Estagiária de Desenvolvimento)  
**Necessidade relacionada:** R01 — Mitigar alucinações lógicas e obter respostas corretas em problemas difíceis; R04 — Validar a resolução através de critérios de aceite didáticos e transparentes  
**Situação concreta da Entrega 1 relacionada:** Seção 2.2 (estudantes usando IA para estudo autônomo), Seção 3.1 e Seção 4.1 (falhas em raciocínios encadeados longos em chatbots de mercado)  
**Hipóteses ainda presentes:** `H01` (preferência por organização sequencial em linha do tempo), `H02` (sinalização clara de critérios de sucesso ✓ e falha ✗)

### 1. Cenário inicial

Beatriz está estudando à noite para uma prova decisiva de Matemática Discreta e Teoria dos Grafos em seu quarto universitário. Ela tenta resolver uma questão de exame anterior envolvendo congruência modular, números primos e restrições de conjuntos, mas suas anotações de aula estão incompletas. Sem a presença de professores ou monitores naquele horário, Beatriz abre o aplicativo de chat do Copilot no Windows em seu notebook de 14 polegadas e digita o enunciado completo da questão, solicitando ajuda para entender como chegar à resposta final. O assistente responde em poucos segundos com um parágrafo conciso e a indicação de que a alternativa correta é a letra "B". Ao tentar acompanhar a resolução proposta pela IA, Beatriz não consegue entender como o modelo pulou da análise de números pares para a conclusão final, omitindo a verificação dos números primos maiores que dois. Em dúvida se ela própria não entendeu a teoria ou se a IA cometeu um erro, Beatriz tenta formular novas perguntas no chat pedindo explicações adicionais, mas o modelo gera apenas respostas repetitivas com o mesmo raciocínio circular. Sem saber em qual passo a explicação se perdeu e com medo de memorizar uma fórmula incorreta na véspera da prova, Beatriz encerra os estudos desmotivada e com alta ansiedade.

### 2. Questões de refinamento

A tabela a seguir aplica a taxonomia de questões de análise de cenários (*Scenario-Based Design* — Rosson & Carroll, 2002; Barbosa & Silva, 2021) para aprofundar as restrições cognitivas e contextuais de Beatriz:

| # | Dimensão / Taxonomia | Questão | Por que precisa ser respondida | Fonte / forma de obter resposta |
|---|---|---|---|---|
| Q1 | **Contexto e Ambiente** | Em quais condições físicas e psicológicas Beatriz realiza essa sessão de estudos (horário, cansaço acumulado, ambiente)? | Mostra que o estudo ocorre tarde da noite após jornada integral de estágio e aulas, sob estresse de notas e com fadiga cognitiva. | [Entrega 3 (seção 1 — P04 e seção 3 — contexto)](03_personas_contexto_jornada.md). |
| Q2 | **Recursos e Informações** | Quais materiais didáticos e registros de aula Beatriz consulta simultaneamente para tentar decifrar a resposta da IA? | Identifica os artefatos de estudo (caderno universitário, listas de exercícios, slides de aula) que entram em conflito com o output do chatbot. | Rotina de graduandos de Engenharia da Computação da FEI. |
| Q3 | **Ações e Práticas** | Como Beatriz interage com o assistente conversacional para tentar forçá-lo a ser mais didático e analítico? | Revela as tentativas usuais de estudantes: enviar comandos como "explique passo a passo para um leigo" ou "mostre as contas de cada item". | [Entrega 2 (seção 2 — Copilot no Windows)](02_analise_concorrencia.md) e observações empíricas da Entrega 1. |
| Q4 | **Rupturas e Falhas** | Por que a interface conversacional padrão falha como instrumento pedagógico para questões com múltiplas etapas de dedução? | Explica a ruptura didática: chatbots tendem a colapsar raciocínios encadeados em um texto superficial único, "pulando" validações intermediárias essenciais para o aprendizado conceitual. | [Entrega 1 (seção 4.2 e 4.4)](01_conhecendo_o_problema.md); literatura sobre tutores inteligentes e LLMs na educação. |
| Q5 | **Consequências e Impacto** | Qual é o perigo pedagógico e emocional de confiar acriticamente em explicações parciais ou incorretas fornecidas pelo chat? | Aponta a consequência grave: assimilação de regras matemáticas falsas, risco de reprovação na disciplina, perda de tempo de estudo e sentimento de incapacidade intelectual. | [Entrega 3 (seção 1 — P04, dores e motivadores)](03_personas_contexto_jornada.md). |

### 3. Cenário refinado

É quinta-feira, 23h30. Beatriz está sentada à sua mesa de estudos no quarto, **[NOVO: física e mentalmente esgotada após uma rotina que começou às 7h da manhã no estágio de desenvolvimento, seguida por quatro horas de aulas presenciais na faculdade de engenharia]**. Ela está no 8º semestre e precisa de uma nota alta na prova de Matemática Discreta da manhã seguinte para garantir a aprovação sem necessidade de exame final. Sobre a mesa, iluminada apenas por uma luminária articulada, ela divide o espaço entre seu notebook Dell Inspiron de 14 polegadas, **[NOVO: um caderno espiral com anotações manuscritas de aula e uma lista impressa de exercícios de exames anteriores do Enade e do benchmark MMLU]**.

Beatriz empaca no exercício 4 da lista: uma questão teórica que exige avaliar três propriedades simultâneas sobre o conjunto de números `{2, 4, 6}` (se são primos, se são pares e se são estritamente maiores que 2) e determinar a interseção correta entre as alternativas de múltipla escolha. Como suas anotações de aula sobre o tema estão fragmentadas e não há colegas online naquele horário, Beatriz decide recorrer à IA.

Ela clica no atalho do assistente Copilot na barra de tarefas do Windows. **[NOVO: Confiando na familiaridade da caixa de texto do chat, digita o enunciado do problema e acrescenta o pedido: "Por favor, resolva passo a passo e explique a regra de cada alternativa para eu entender para a prova"]**. Ela clica em enviar e aguarda.

Três segundos depois, o assistente retorna uma resposta em um único bloco de texto: afirma de forma categórica que os números primos do conjunto são apenas `{2}`, que todos são pares `{2, 4, 6}`, e finaliza afirmando bruscamente que a resposta correta é a **Alternativa B**, sem detalhar a condição `n > 2` nem efetuar a interseção dos subconjuntos. **[NOVO: Beatriz franze a testa e tenta conferir contra suas anotações: pela sua dedução preliminar, o número 2 não é maior que 2, o que resultaria em um conjunto vazio e levaria à Alternativa D ("Nenhuma das anteriores"). No entanto, a segurança do texto gerado pela IA faz a estudante duvidar de sua própria capacidade lógica: "O modelo tem bilhões de parâmetros, ele não erraria uma conta boba dessa... eu que devo estar confundindo a regra do conjunto vazio", pensa ela consigo mesma]**.

Tentando esclarecer a contradição, Beatriz digita uma réplica no chat: *"Mas o número 2 é maior que 2? Como a alternativa B pode estar certa?"*. **[NOVO: O assistente responde reformulando a mesma frase com outras palavras: "Sim, como 2 é o único primo e está presente no conjunto, a alternativa B é a melhor escolha". O modelo simplesmente ignora a contradição da desigualdade matemática estrita e reafirma a resposta errada com assertividade absoluta. Como a interface do chat é apenas uma sequência linear de balões de mensagens, não há nenhuma separação visual entre as tarefas parciais, nenhum registro de critérios formais de aceite e nenhuma indicação de que o modelo atropelou uma das restrições do problema]**.

**[NOVO: Beatriz passa a hora seguinte relendo desesperadamente o mesmo parágrafo confuso e folheando livros didáticos em PDF, tentando conciliar a falácia do assistente com as definições formais de matemática discreta. Às 00h45, exausta e em crise de ansiedade, ela desiste de estudar, sem ter certeza sobre a matéria e correndo o risco iminente de errar a questão na prova por ter confiado em uma dedução alucinada e opaca de um chatbot conversacional]**.

### 4. Elementos extraídos

| Elemento | Evidência no cenário |
|---|---|
| **Ator(es)** | Beatriz Fagundes (22 anos, Estudante de Engenharia da Computação e Estagiária de Desenvolvimento). |
| **Objetivo(s)** | Compreender o encadeamento dedutivo passo a passo de um exercício complexo de matemática discreta/lógica (estilo MMLU) e confirmar a alternativa correta sem dúvidas conceituais para sua prova. |
| **Contexto** | Mesa de estudos no quarto tarde da noite; iluminação artificial; notebook de 14 polegadas; alta fadiga física e mental após estágio e aulas; proximidade imediata de avaliação acadêmica decisiva. |
| **Recursos/informações** | Caderno universitário com anotações de aula; lista impressa de exercícios de exames; livros-texto em PDF; aplicativo conversacional comercial (Copilot no Windows); enunciados com múltiplas restrições. |
| **Ações** | Digitação do enunciado com pedido de explicação didática passo a passo; leitura e interpretação de texto corrido em balão de chat; envio de perguntas de esclarecimento; folheamento manual de anotações para conferência cruzada. |
| **Problemas/rupturas** | O assistente pula etapas dedutivas intermediárias; afirma com certeza indevida uma conclusão logicamente inválida; ignora restrições matemáticas do enunciado em conversas subsequentes; formato linear de chat não expõe critérios de verificação nem pontos de falha. |
| **Consequências** | Insegurança intelectual severa (duvidar da própria capacidade cognitiva em favor da autoridade ilusória da máquina); desperdício de tempo precioso de descanso na véspera da prova; risco real de memorizar conceitos errados e ser reprovada na disciplina acadêmica. |

### 5. Implicações para as próximas entregas

- **Análise de Tarefas (Entrega 5):** Modelar tarefas de **"Submeter pergunta com entrada em linguagem natural simples"** e **"Acompanhar resolução sequencial com status explícito de critérios de aceite"** (candidatas às modelagens HTA e CTT, com ênfase na facilidade de interpretação do estado de sucesso/falha de cada passo).
- **Modelo Conceitual e Terminologia (Entrega 9):** Garantir que os termos de interface sejam amigáveis e didáticos para estudantes em formação, evitando terminologia hermética de engenharia de backend e priorizando clareza em "Critérios Verificados", "Etapas Concluídas" e "Resposta Final".
- **Diretrizes de Design (Entregas 9 a 11):** A interface futura não deve se comportar como um chat conversacional caótico. Deve proporcionar uma estrutura visual límpida, onde cada subtarefa possua limites claros e exiba crachás/badges inequívocos de verificação (✓ Aprovado / ✗ Reprovado), eliminando a ansiedade de travamento e facilitando a conferência didática do raciocínio lógico.

---

## Síntese comparativa da equipe — Cenários de análise/problema

A tabela abaixo consolida as quatro práticas problemáticas investigadas pela equipe na Entrega 4, demonstrando a complementaridade dos perfis e a consistência na identificação das dores no estado da arte atual:

| Dimensão | C01 (Pedro Correia) | C02 (Vitor Vianna) | C03 (Pedro Satoru) | C04 (Hugo Nomura) |
|---|---|---|---|---|
| **Ator / Persona** | Dra. Mariana Siqueira (P01 — Pesquisadora) | Carlos Eduardo Prado (P02 — Consultor) | Lucas Zanin (P03 — Desenvolvedor) | Beatriz Fagundes (P04 — Estudante) |
| **Ambiente de Uso Atual** | Laboratório acadêmico, Overleaf e PDFs | Escritório corporativo e comitês de risco | Desktop Linux pessoal e terminal/CLI | Quarto universitário tarde da noite |
| **Ferramenta Atual Utilizada** | ChatGPT Plus (navegador web) | Playground de API e dashboards de nuvem | LangChain, scripts Python e terminal | Copilot no Windows (aplicativo de chat) |
| **Objetivo Humano Real** | Validar dedução científica do GPQA para tese | Provar conformidade e viabilidade de LLMs | Comparar loops com baseline no MMLU | Aprender resolução de exercício para prova |
| **Ruptura Central Identificada** | *Context rot*: perda de premissas em chat longo | Caixa-preta sem auditoria e custos opacos | Vazamento silencioso de contexto e log bruto | Pulo de etapas dedutivas e alucinação |
| **Impacto no Mundo Real** | 3h+ de recálculo manual e risco acadêmico | Reunião cancelada e risco de perder cliente | Foco desviado para depuração de infraestrutura | Dúvida conceitual e risco de reprovação |
| **Necessidade Rastreável** | R01 (mitigação de *context rot*) | R02 (telemetria) e R04 (critérios de aceite) | R03 (comparação de fluxos) e R02 | R01 (acurácia) e R04 (didática passo a passo) |
| **Tarefa Derivada para Entrega 5** | Auditar premissas e subtarefas intermediárias | Parametrizar modelo e auditar telemetria | Alternar fluxos e inspecionar Fresh Context | Submeter pergunta e acompanhar verificação |

---

## Checklist

- [ x ] Há um cenário completo por integrante.
- [ x ] Cada cenário tem título, ator, objetivo, contexto e problema.
- [ x ] O cenário possui origem rastreável na Entrega 1 ou justifica claramente a inclusão de uma nova situação.
- [ x ] O texto descreve a situação atual, sem antecipar a solução.
- [ x ] Para TCC sem interface original, o cenário descreve uma prática humana plausível relacionada à contribuição técnica, e não “a falta de uma tela”.
- [ x ] Questões de refinamento acrescentam informação nova.
- [ x ] O refinamento mostra claramente o que foi adicionado/alterado.
- [ x ] Cenários são diferentes o suficiente para cobrir objetivos/problemas relevantes.
- [ x ] Cada cenário está ligado a persona/necessidade na matriz de rastreabilidade.
