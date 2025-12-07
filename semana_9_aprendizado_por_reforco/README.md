# Semana 9 – Aprendizado por Reforço

**Cronograma:** 01/09/2025 (início) a 05/10/2025 (entrega - domingo)

## Objetivos de aprendizagem
- Entender o loop agente-ambiente e formulação de MDPs.
- Implementar Q-learning em um ambiente simples.
- Explorar extensões de Deep Q Networks (DQN) e possíveis aplicações.

## Tópicos-chave
- Fundamentos de Aprendizado por Reforço (MDP, política, recompensa, valor).
- Q-learning, exploração vs. exploração (ε-greedy), atualização de valores.
- Deep Q Networks: replay buffer, target network (visão geral).
- Aplicações do Aprendizado por Reforço em controle e recomendação.

## Entregas
- Notebook implementando Q-learning em um ambiente tabular (ex.: FrozenLake do `gymnasium`).
- Relatório curto com análise de convergência e gráfico de recompensa acumulada.
- Esboço conceitual (diagrama) de uma arquitetura DQN e discussão sobre estabilidade.

## Leituras sugeridas
- "Reinforcement Learning: An Introduction" – Sutton & Barto (cap. 1–6).
- Tutoriais oficiais do `gymnasium`/`OpenAI Gym` sobre Q-learning.

## Exercício guiado
- Ajuste taxa de exploração (epsilon) e taxa de aprendizado em Q-learning para observar impacto na convergência. Documente os melhores valores e explique o comportamento observado.
