# Matriz de rastreabilidade de IHC

A matriz deve ser atualizada ao longo do semestre. Ela ajuda a demonstrar que a interface não surgiu arbitrariamente e registra **como o conhecimento da equipe evoluiu**.

Para projetos cujo TCC não previa interface, esta matriz é especialmente importante: deve ficar visível a passagem da **contribuição técnica do TCC** para um **cenário de uso plausível**, e desse cenário para as decisões de interação.

## 1. Derivação do escopo de IHC a partir do TCC

| Elemento | Registro da equipe | Evidência/justificativa | Estado |
|---|---|---|---|
| Tema do TCC | Aprimoramento de outputs de IA por meio de orquestração multi-fase baseada no Ralph Wiggum Loop para mitigar o decaimento de contexto (*context rot*). | Artigo/Paper do TCC e documentação do backend | definido |
| Resultado técnico esperado | Um harness de orquestração de IA (serviço backend local) e benchmarks comparativos nos datasets MMLU/GPQA. | Arquitetura de código e scripts de benchmark | definido |
| O TCC previa interface? | sim | Documentação inicial e demo web demonstrativa integrada | definido |
| Capacidade/contribuição central | Orquestrar e isolar o contexto das chamadas de LLM por meio de tarefas atômicas e transferência de aprendizados (*Fresh Context*). | Algoritmo stateless de raciocínio | definido |
| Possíveis beneficiários/stakeholders | Pesquisadores, estudantes, analistas acadêmicos e profissionais que utilizam LLMs para tarefas de alta complexidade. | `[H]` Levantamento de perfil de público-alvo | H |
| Usuário escolhido para IHC | Pesquisador / Estudante / Analista de Explicabilidade | `[H]` Por necessitarem de explicabilidade nas respostas geradas pela IA | H |
| Objetivo principal do usuário | Submeter perguntas lógicas complexas e acompanhar as etapas de raciocínio da IA em tempo real para validar a veracidade da resposta. | `[H]` Necessidade de auditoria e mitigação de alucinações | H |
| Contexto de uso adotado | Ambientes de estudo acadêmico, laboratórios de pesquisa ou escritórios de análise de dados. | `[H]` Foco individual e necessidade de alta atenção aos detalhes | H |
| Interface/recorte de IHC | Dashboard interativo contendo entrada de dados, linha do tempo vertical de "Open Thinking" e monitoramento de tokens/contexto. | `[H]` Permite a visualização didática do loop de raciocínio em tempo real | proposta |
| Relação com o TCC | parte prevista | Interface demonstrativa oficial do projeto | definido |

> Se o escopo de IHC mudar ao longo do semestre, preserve a decisão anterior no histórico e registre **qual evidência motivou a mudança**.

## 2. Registro de hipóteses e lacunas da Entrega 1

Use esta tabela para itens importantes marcados como `[H]` ou `[?]`. Preserve o histórico: não apague uma hipótese refutada.

| ID | Afirmação / dúvida inicial | Tipo | Por que importa | Como/onde investigar | Evidência obtida | Estado atual | Impacto no projeto |
|---|---|---|---|---|---|---|---|
| H01 | Pesquisadores e estudantes preferem acompanhar a resolução lógica das subtarefas em formato de linha do tempo vertical (timeline) para validar e confiar na resposta final. | H | Define a estrutura visual principal da interface (Open Thinking). | Entrega 6 (Prototipação em papel) / Entrega 13 (Heurísticas) | PENDENTE | aberta | Alto |
| H02 | A sinalização de sucesso (✓) ou falha (✗) dos critérios de aceite na timeline é suficiente para indicar quando a IA corrigiu o raciocínio. | H | Evita a sobrecarga de leitura de logs longos pelo usuário. | Entrega 13 (Heurísticas) / Entrega 14 (Testes com usuários) | PENDENTE | aberta | Médio |

## 3. Rastreabilidade entre contribuição técnica, necessidades e artefatos

| ID | Capacidade do TCC utilizada | Necessidade/problema | Persona | Cenário problema | Objetivo/tarefa | HTA/GOMS/CTT | Cenário de interação / signos | MoLIC | Tela(s) Figma | Heurística / problema | Tarefa no teste | Decisão/melhoria |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R01 | Orquestração stateless (Ralph Loop) | Auditar o raciocínio intermediário do LLM | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE |
| R02 | Monitoramento de contexto/tokens | Identificar eficiência de custo e context rot | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE | PENDENTE |

## 4. Rastreabilidade de padrões de interface

Use esta tabela quando o projeto incorporar padrões como dashboard, relatório, histórico, filtros ou administração. O objetivo é **justificar o padrão**, não apenas listar telas.

| ID da tela/fluxo | Padrão de interface | Objetivo/tarefa que justifica | Informação/ação principal | Evidência de necessidade | Artefatos relacionados |
|---|---|---|---|---|---|
| F01 | dashboard / timeline | Visualizar o progresso de pensamento em tempo real | Exibição de cards de tarefas por fases (Setup, Loop, Síntese) | `[H]` Necessidade de auditoria e acompanhamento de tarefas da IA | PENDENTE |
| F02 | seletor / parametrização | Ajustar modelo e fluxo de forma simplificada | Botões de seleção de modelo (Llama 3.1 8B/70B/405B) e tipo de fluxo | `[F]` (demo já possui esse seletor inicial) | PENDENTE |

## 5. Registro de mudanças de escopo

| Data | O que mudou | Evidência/feedback que motivou | Artefatos afetados | Responsável |
|---|---|---|---|---|
| 22/08/2026 | Derivação inicial do escopo e hipóteses baseadas no TCC | Criação inicial do repositório da disciplina | README.md, docs/01_conhecendo_o_problema.md | Equipe de IHC |

## Como usar

- Use identificadores estáveis (`H01`, `P01`, `C01`, `T01`, `M01`, `F01`, `UT01`).
- Quando uma necessidade/problema tiver origem em hipótese da Entrega 1, cite o ID correspondente.
- Em TCC sem interface original, pelo menos uma linha deve mostrar claramente **como uma capacidade técnica chega até uma tarefa de usuário e uma tela/fluxo**.
- Uma linha pode se desdobrar quando um objetivo possui múltiplos caminhos.
- Não force relação inexistente: se algo ainda não foi modelado, marque `PENDENTE`.
- Ao remover uma funcionalidade, registre a decisão em vez de apagar silenciosamente o histórico.
- Dashboard, CRUD, filtros e relatórios só devem aparecer quando houver objetivo/tarefa que os justifique.
