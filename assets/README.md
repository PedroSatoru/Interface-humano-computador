# Organização de evidências e imagens

Use as pastas abaixo para manter o repositório navegável:

- `02_concorrencia/` — prints e comparações visuais.
- `03_personas/` — personas, mapa de empatia e jornada.
- `05_tarefas/` — oito SVGs da Entrega 5 (quatro HTAs e quatro CTTs) e gerador; os quatro GOMS são textuais no relatório.
- `06_prototipos/` — protótipos em papel e registros de walkthrough.
- `09_modelo_conceitual/` — mapa de objetivos e esquemas.
- `10_molic/` — diagramas MoLIC e fontes editáveis.
- `11_figma/` — prints de telas/estados do protótipo, incluindo quando pertinentes dashboard, relatórios, histórico/filtros, administração, CRUDs e estados de erro/processamento.
- `13_heuristica/` — prints anotados das violações.
- `14_testes/` — fluxograma, imagens autorizadas e materiais não sensíveis.

**Não publique dados pessoais ou gravações sem autorização.** Links de vídeo podem ser registrados no documento da entrega em vez de armazenar arquivos pesados no Git.

## Artefatos da Entrega 5

| Tarefa | HTA | CTT |
|---|---|---|
| T01 | [hta_t01.svg](05_tarefas/hta_t01.svg) | [ctt_t01.svg](05_tarefas/ctt_t01.svg) |
| T02 | [hta_t02.svg](05_tarefas/hta_t02.svg) | [ctt_t02.svg](05_tarefas/ctt_t02.svg) |
| T03 | [hta_t03.svg](05_tarefas/hta_t03.svg) | [ctt_t03.svg](05_tarefas/ctt_t03.svg) |
| T04 | [hta_t04.svg](05_tarefas/hta_t04.svg) | [ctt_t04.svg](05_tarefas/ctt_t04.svg) |

A fonte editável é o [relatório da Entrega 5](../docs/05_analise_tarefas.md), incluindo os GOMS. O [gerador](05_tarefas/gerar_diagramas.mjs) lê suas tabelas: `node assets/05_tarefas/gerar_diagramas.mjs` regenera os SVGs; acrescentar `--check` verifica estrutura e sincronização. Execute na raiz. `hta_transferencia.svg` é exemplo do guia, não modelo desta entrega. Arquivos temporários de renderização não integram seus artefatos.


Para TCCs sem interface prevista originalmente, não use imagens de telas para “provar” que o escopo faz sentido. A justificativa deve estar nas entregas e na rastreabilidade; os assets apenas documentam as soluções produzidas depois dessa derivação.
