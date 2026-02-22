# Engenharia de Arquitetura de Contexto
## Arquitetura Cognitiva Híbrida para Claude Code + Cursor com Qualidade, Governança e Eficiência de Custos

---

## 1. Objetivo

Este documento define uma abordagem de **engenharia de contexto** para equipes que usam IA no ciclo de desenvolvimento, combinando:

- Modelos de alta capacidade (arquitetura e decisão)
- Modelos intermediários/baixos (produção e tarefas mecânicas)
- Contexto estático, operacional e dinâmico
- Regras, comandos e pipelines de execução

Objetivos centrais:

1. **Aumentar qualidade estrutural e consistência técnica**
2. **Reduzir custo de tokens por entrega**
3. **Diminuir retrabalho e ambiguidade operacional**
4. **Melhorar previsibilidade de tempo, custo e risco**

---

## 2. Princípio Arquitetural

A IA deve ser tratada como um **sistema distribuído de cognição**, não como uma ferramenta única.

Isso implica separar responsabilidades em duas camadas:

### 2.1 Camada Cognitiva (modelo forte)

Responsável por decisões de alto impacto:

- Arquitetura e decomposição de escopo
- Trade-offs técnicos
- Estratégia de testes e validação
- Priorização de riscos
- Definição de contratos e padrões

Exemplos de saída esperada:

- Plano de implementação por etapas
- ADRs (Architecture Decision Records)
- Checklist de qualidade
- Matriz de risco e mitigação

### 2.2 Camada Operacional (modelo intermediário/barato)

Responsável por execução previsível:

- Implementação orientada por plano
- Refatoração mecânica
- Criação/ajuste de testes
- Padronização e formatação
- Correções pontuais de baixo risco

Exemplos de saída esperada:

- PRs pequenos e objetivos
- Testes automatizados por módulo
- Ajustes locais com baixo consumo de tokens

---

## 3. Fundamentos da Arquitetura de Contexto

Arquitetura de Contexto responde 5 perguntas:

1. **O que** o modelo precisa saber?
2. **Quanto** precisa saber para executar bem?
3. **Quando** cada informação deve entrar na janela de contexto?
4. **Como** esse conhecimento é acessado?
5. **Qual** é a fonte de verdade canônica?

### 3.1 Benefícios diretos

Uma boa arquitetura de contexto reduz:

- Ambiguidade de instruções
- Leitura desnecessária de arquivos
- Iterações longas de ajuste
- Dependência de prompts extensos
- Custo médio por tarefa

### 3.2 Princípios operacionais

- **Minimalismo contextual:** só carregar o necessário para a etapa atual
- **Hierarquia de fontes:** política > arquitetura > código > contexto externo
- **Determinismo de execução:** prompts e comandos reutilizáveis
- **Rastreabilidade:** toda decisão relevante deve ser auditável

---

## 4. Camadas de Contexto

### 4.1 Contexto Base (estático)

Conjunto de regras estáveis e de longa duração:

- `CLAUDE.md` (ou equivalente)
- Convenções de arquitetura
- Padrões de nomenclatura
- Estratégia de testes
- Políticas de PR e revisão

**Características:**

- Baixa frequência de mudança
- Alto impacto no comportamento dos modelos
- Deve ser lido antes de qualquer tarefa

### 4.2 Contexto Operacional (de tarefa)

Conjunto mínimo para executar a entrega atual:

- Escopo da tarefa
- Arquivos-alvo
- Critérios de aceite
- Plano de implementação

**Regra de ouro:** limitar o raio de ação do modelo para reduzir exploração de código desnecessária.

### 4.3 Contexto Dinâmico (sob demanda)

Informação externa e atualizada:

- MCP (ex.: context7)
- Documentação oficial de framework
- Breaking changes de bibliotecas
- APIs externas

**Política recomendada:** ativar apenas quando houver incerteza técnica real.

---

## 5. ` /init ` e `CLAUDE.md` como Núcleo Cognitivo

### 5.1 Papel do `/init`

O comando `/init` acelera a formação de contexto inicial ao mapear:

- Estrutura do repositório
- Linguagens e frameworks
- Scripts comuns
- Dependências
- Convenções detectáveis

### 5.2 Papel do `CLAUDE.md`

O `CLAUDE.md` atua como **índice cognitivo condensado**.

Ganhos práticos:

- Menos exploração repetitiva
- Menos busca semântica ampla
- Menor risco de inconsistência
- Melhor desempenho de modelos menores

### 5.3 Estrutura recomendada para um bom `CLAUDE.md`

1. Missão do projeto
2. Arquitetura (camadas e limites)
3. Convenções de código
4. Estratégia de testes
5. Fluxo de desenvolvimento/PR
6. Anti-padrões proibidos
7. Playbook de incidentes comuns

---

## 6. Rules no Cursor: Padronização sem Repetição

Rules servem para transformar padrões em comportamento automático.

Exemplos de diretrizes que devem virar rule:

- “Sempre leia `CLAUDE.md` antes de alterar código”
- “Não criar endpoint sem teste de contrato”
- “Respeitar arquitetura em camadas (Controller → Service → Repository)”
- “Evitar mudanças fora do escopo explícito”

### 6.1 Resultado esperado

- Menos tokens em prompts recorrentes
- Menor variação entre entregas
- Redução de retrabalho de revisão

---

## 7. Comandos Personalizados (Skills/Commands)

Criar comandos em `.cursor/commands/` ajuda a encapsular processos repetitivos.

Exemplos úteis:

- `/implement_feature`
- `/refactor_module`
- `/generate_tests`
- `/harden_validation`
- `/apply_clean_architecture`

### 7.1 Estrutura mínima de um comando

- Objetivo
- Entradas necessárias
- Passos de execução
- Critérios de sucesso
- Saída esperada

### 7.2 Benefícios

- Menor ambiguidade
- Mais previsibilidade
- Redução de prompts manuais extensos

---

## 8. Teams Agents: Economia de Tokens por Estratégia

### 8.1 Por que o consumo cresce

Agentes de modo autônomo tendem a:

- Explorar muitos arquivos
- Usar busca semântica ampla
- Executar ciclos longos de tentativa
- Acumular histórico extenso

### 8.2 Política de uso eficiente

1. Começar em **Ask Mode** para planejar
2. Executar em **Agent Mode** somente com escopo fechado
3. Evitar “analise todo o projeto”
4. Quebrar tarefas grandes em subtarefas
5. Desativar automações quando não agregarem valor

---

## 9. MCP (contexto externo) com Governança

### 9.1 Quando usar

- API nova ou recente
- Mudança de versão relevante
- Dúvida sobre comportamento oficial
- Dependências sujeitas a breaking changes

### 9.2 Quando evitar

- Tarefas locais sem dependência externa
- Problemas já cobertos por contexto base
- Ajustes simples de implementação

### 9.3 Regra prática

> Primeiro exaurir contexto interno canônico; depois acionar contexto externo.

---

## 10. Fluxo Operacional Recomendado (end-to-end)

### Fase 1 — Planejamento (modelo forte)

- Definir escopo e restrições
- Criar plano incremental
- Mapear riscos
- Definir estratégia de testes

### Fase 2 — Preparação de contexto

- Atualizar `CLAUDE.md` (se necessário)
- Garantir rules ativas
- Selecionar arquivos do escopo

### Fase 3 — Execução (modelo intermediário)

- Implementar por lotes pequenos
- Criar testes por unidade funcional
- Validar critérios de aceite

### Fase 4 — Ajustes mecânicos (modelo barato)

- Formatação
- Limpeza de comentários
- Refactors triviais
- Correções de baixo risco

### Fase 5 — Verificação final

- Rodar checks de qualidade
- Revisar diffs por impacto
- Publicar PR com rastreabilidade

---

## 11. Modelo de Decisão por Tipo de Trabalho

| Tipo de atividade | Modelo recomendado | Observação |
|---|---|---|
| Arquitetura e trade-off | Forte | Evitar decisões críticas em modelo barato |
| Planejamento técnico | Forte | Produzir plano validável |
| Implementação padrão | Intermediário | Seguir checklist e contratos |
| Padronização/mecânico | Barato | Maximiza custo-benefício |
| Pesquisa de versão/API | Modelo + MCP | Uso pontual e direcionado |

---

## 12. Métricas para Gestão de Custo e Qualidade

Para evoluir a arquitetura de contexto, acompanhar:

- **Tokens por tarefa** (mediana e p95)
- **Taxa de retrabalho por PR**
- **Tempo de ciclo** (planejamento → merge)
- **Defeitos pós-merge**
- **Cobertura de testes por módulo crítico**
- **Taxa de aderência às rules**

### 12.1 Indicadores de alerta

- Crescimento contínuo de tokens sem aumento de escopo
- PRs grandes e difusos
- Reincidência de erros de padrão
- Dependência frequente de contexto externo para tarefas simples

---

## 13. Anti-padrões Comuns

1. **Prompt gigante para qualquer tarefa**
2. **Agent Mode para trabalho simples**
3. **Ausência de fonte de verdade (sem CLAUDE.md confiável)**
4. **Rules genéricas demais e sem enforcement**
5. **Misturar planejamento e execução no mesmo ciclo longo**

---

## 14. Blueprint de Implementação em 7 Dias

### Dia 1

- Rodar `/init`
- Revisar e enriquecer `CLAUDE.md`

### Dia 2

- Definir rules globais e por projeto
- Publicar convenções de engenharia

### Dia 3

- Criar comandos personalizados críticos
- Testar comandos em tarefas pequenas

### Dia 4-5

- Adotar fluxo híbrido em 2-3 features
- Medir tokens e tempo de ciclo

### Dia 6

- Ajustar rules/comandos com base em fricções

### Dia 7

- Consolidar playbook
- Formalizar governança de contexto

---

## 15. Templates Operacionais

### 15.1 Template de planejamento (modelo forte)

```md
## Objetivo
## Escopo
## Fora de escopo
## Riscos
## Estratégia de testes
## Plano por etapas
## Critérios de aceite
```

### 15.2 Template de execução (modelo intermediário)

```md
- Ler CLAUDE.md
- Implementar etapa X
- Criar/ajustar testes Y
- Validar lint/test/build
- Reportar diffs e riscos residuais
```

### 15.3 Template de PR

```md
## Contexto
## O que mudou
## Como validar
## Riscos e mitigação
## Próximos passos
```

---

## 16. Conclusão

A combinação de **arquitetura cognitiva híbrida + engenharia de contexto** transforma o uso de IA em um processo técnico governável.

Resultado esperado:

- Maior qualidade arquitetural
- Menor custo operacional
- Menos retrabalho
- Melhor previsibilidade de entrega
- Escalabilidade de práticas para times

Princípio final:

> IA não é apenas acelerador de código; é infraestrutura cognitiva que precisa de arquitetura, governança e observabilidade.
