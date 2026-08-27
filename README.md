# Projeto de Interação Humano-Computador (IHC)

## Identificação

**Título do projeto de IHC:** Interface de Visualização e Controle para o Ralph Wiggum Loop Adaptado  
**TCC/projeto de origem:** Um Harness de IA para Resolução de Perguntas em Linguagem Natural: Adaptando o Ralph Wiggum Loop Além do Desenvolvimento de Software  
**Orientador(a):** Prof. Charles Henrique Porto Ferreira  
**Disciplina:** Interação Humano-Computador  
**Instituição:** Centro Universitário FEI  
**Semestre:** 2026 / 8º Semestre

### Equipe

| Nome completo | Matrícula | GitHub | Responsabilidade principal |
|---|---:|---|---|
| Hugo Emílio Nomura | 22.123.051-9 | [@HG0304](https://github.com/HG0304) | Front-end e Integração da Interface |
| Pedro Henrique Correia de Oliveira | 22.222.009-7 | [@PedroHCorreia](https://github.com/PedroHCorreia) | Design de Interação e Protótipos |
| Pedro Henrique Satoru Lima Takahashi | 22.123.019-6 | [@PedroSatoru](https://github.com/PedroSatoru) | Arquitetura de Software e Fluxo de Dados |
| Vitor Monteiro Vianna | 22.223.085-6 | [@VitorMonteiroVianna](https://github.com/VitorMonteiroVianna) | Avaliação de Usabilidade e Testes |

## Relação entre TCC e projeto de IHC

| Item | Descrição |
|---|---|
| Tema central do TCC | Aprimoramento de outputs de IA por meio de sistemas compostos (harnesses) utilizando ciclos iterativos de raciocínio, decomposição de tarefas e refinamento de respostas, baseado no Ralph Wiggum Loop, visando mitigar o decaimento de contexto (*context rot*). |
| Resultado técnico esperado do TCC | Um harness de orquestração de IA (serviço backend local para integração interna de fluxos) e benchmarks de acurácia com modelos Llama 3.1 no MMLU e GPQA. |
| O TCC já previa interface? | sim |
| Capacidade técnica que pode gerar valor para pessoas | Permite visualizar detalhadamente e interativamente o processo interno de pensamento (thinking), decomposição em tarefas, validação de critérios de aceite e síntese de respostas dos LLMs, tornando os processos de raciocínio da IA transparentes e controláveis. |
| Usuário principal adotado em IHC | Pesquisadores, estudantes e analistas acadêmicos/profissionais que necessitam acompanhar e auditar a resolução de tarefas lógicas complexas passo a passo. |
| Objetivo principal desse usuário | Compreender como a IA decompôs o problema, acompanhar as decisões tomadas em cada subtarefa e verificar a acurácia do raciocínio lógico intermediário e do consumo de tokens. |
| Interface/recorte explorado na disciplina | Um dashboard web interativo contendo painel de entrada de perguntas, visualização do "Open Thinking" em tempo real com a linha do tempo das tarefas (fases A, B e C), monitoramento de tokens/contexto e painel de resultado final. |
| Relação com o escopo formal do TCC | parte prevista |

## Resumo do projeto pela perspectiva do usuário

**Pesquisadores, estudantes e analistas acadêmicos** precisam **auditar e validar o processo de raciocínio de sistemas compostos de IA** em **tarefas complexas de linguagem natural**. Atualmente enfrentam a **falta de transparência nas etapas intermediárias de raciocínio (caixa-preta) e o decaimento progressivo da qualidade das respostas devido ao acúmulo de contexto (*context rot*)**, utilizando **chatbots clássicos de forma linear direta**. O tema do TCC investiga **a orquestração stateless do Ralph Wiggum Loop adaptado para linguagem natural, mitigando o context rot**. Para fins da disciplina de IHC, será explorada uma interface que permita **submeter a pergunta complexa em linguagem natural, acompanhar visualmente o ciclo de planejamento, execução e síntese das tarefas em tempo real na linha do tempo, e monitorar o tamanho do contexto e o uso de tokens por etapa**.

Se alguma afirmação ainda não estiver sustentada por evidência, registre-a como hipótese na [Entrega 1](docs/01_conhecendo_o_problema.md).

## Por que pensar em interface mesmo em TCCs técnicos?

Algoritmos, modelos, APIs, análises de datasets e componentes de infraestrutura podem não exigir interface como resultado acadêmico do TCC. Porém, quando essas contribuições são transferidas para uma situação real, normalmente existem pessoas que:

- configuram parâmetros;
- fornecem ou selecionam dados;
- iniciam ou acompanham processamento;
- interpretam resultados;
- comparam alternativas;
- tomam decisões;
- administram usuários e permissões;
- consultam histórico;
- geram relatórios;
- investigam erros;
- auditam mudanças.

Essas atividades fornecem um campo legítimo para exercitar IHC.

Possibilidades de interface incluem **dashboards, telas administrativas, configuração, relatórios, histórico com filtros, comparação de resultados, visualização de dados, acompanhamento de processamento, gestão de perfis e permissões, CRUDs justificados pelo domínio, alertas, auditoria e ajuda contextual**. Nenhuma dessas telas é obrigatória por si só: deve existir uma tarefa e um objetivo de usuário que a justifique.

## Relação com apresentação e potencial de aplicação

A reflexão sobre usuários ajuda a equipe a explicar o projeto para públicos externos, inclusive em eventos como a **INOVA**. Em vez de comunicar apenas a técnica implementada, a equipe pode apresentar:

**problema humano → contribuição computacional → forma de uso → impacto potencial**.

O protótipo de IHC pode, portanto, funcionar como uma demonstração do potencial de mercado, transferência tecnológica ou impacto extensionista do tema do TCC, sem necessariamente integrar a implementação final do trabalho de conclusão.

## Como usar este repositório

1. Leia o [Guia de uso e apresentação](GUIA_DE_USO.md).
2. Leia o [Guia de definição de escopo de IHC](GUIA_ESCOPO_IHC.md), especialmente se o TCC não previa interface.
3. Preencha as entregas na ordem em que forem trabalhadas na disciplina.
4. Em toda entrega individual, **identifique o autor**.
5. Salve imagens, diagramas e evidências em [`assets/`](assets/README.md).
6. Mantenha a [Matriz de rastreabilidade](RASTREABILIDADE.md) atualizada.
7. Na Entrega 1, diferencie **[F] fatos**, **[H] hipóteses** e **[?] lacunas de conhecimento**.
8. Antes de cada entrega, revise o checklist do arquivo e o [Checklist final](CHECKLIST_FINAL.md).
9. Sempre que uma evidência posterior contrariar uma hipótese inicial, **revise o projeto**. IHC é um processo iterativo.

## Entregas

| # | Entrega | Quantidade mínima / responsabilidade | Status |
|---:|---|---|---|
| 1 | [Conhecendo o projeto, o usuário e o problema](docs/01_conhecendo_o_problema.md) | 1 solução consolidada por equipe | ⬜ |
| 2 | [Público-alvo e análise de concorrência](docs/02_analise_concorrencia.md) | no mínimo 1 concorrente/interface representativa por integrante + síntese | ⬜ |
| 3 | [Personas, empatia, contexto e jornada](docs/03_personas_contexto_jornada.md) | 1 persona por integrante; demais artefatos consolidados | ⬜ |
| 4 | [Cenários de análise/problema](docs/04_cenarios_problema.md) | 1 solução completa por integrante | ⬜ |
| 5 | [Análise de tarefas: HTA, GOMS e CTT](docs/05_analise_tarefas.md) | cada integrante: pelo menos 1 HTA + 1 GOMS + 1 CTT | ⬜ |
| 6 | [Prototipação em papel](docs/06_prototipacao_papel.md) | 1 protótipo integrado por equipe | ⬜ |
| 7 | [Coleta de dados e aspectos éticos](docs/07_coleta_dados.md) | soluções individuais + técnicas distintas; questionário entre as técnicas | ⬜ |
| 8 | [Ciclo de vida e engenharia de usabilidade](docs/08_engenharia_usabilidade.md) | 1 solução consolidada por equipe | ⬜ |
| 9 | [Modelo conceitual e design centrado na comunicação](docs/09_modelo_conceitual.md) | soluções individuais + consolidação de objetivos/signos | ⬜ |
| 10 | [MoLIC](docs/10_molic.md) | 1 diagrama completo por integrante | ⬜ |
| 11 | [Protótipo no Figma](docs/11_figma.md) | 1 protótipo integrado por equipe, cobrindo fluxos modelados | ⬜ |
| 12 | [Planejamento da avaliação — DECIDE](docs/12_planejamento_avaliacao.md) | 1 plano consolidado por equipe | ⬜ |
| 13 | [Avaliação heurística](docs/13_avaliacao_heuristica.md) | 1 avaliação completa por integrante, todas as telas/estados e 10 heurísticas | ⬜ |
| 14 | [Avaliação por observação de usuários](docs/14_observacao_usuario.md) | avaliação consolidada; nº de participantes finais = nº de integrantes | ⬜ |

> Se o docente definir quantidade diferente para a turma/semestre, a orientação da disciplina prevalece.

## Visão de continuidade

O projeto deve formar uma cadeia de evidências:

**tema/contribuição do TCC → possível aplicação → usuários/stakeholders → objetivos → problema/contexto → alternativas → necessidades → personas → cenários → tarefas → modelo conceitual → MoLIC → protótipo → planejamento → inspeção → teste com usuários → melhorias**.

Uma entrega não deve “reiniciar” o projeto. Se o escopo de IHC foi criado para um DBA, por exemplo, as personas, tarefas, MoLIC, protótipo e avaliação devem permanecer coerentes com esse perfil, salvo quando novas evidências justificarem a revisão.

## Documentos de apoio

- [Guia de uso e apresentação](GUIA_DE_USO.md)
- [Guia para definir o escopo de IHC a partir do TCC](GUIA_ESCOPO_IHC.md)
- [Matriz de rastreabilidade](RASTREABILIDADE.md)
- [Checklist final](CHECKLIST_FINAL.md)
- [Bibliografia de IHC](BIBLIOGRAFIA.md)
- [Orientações de contribuição no GitHub](CONTRIBUTING.md)
- [Instrumentos reutilizáveis](instrumentos/README.md)
