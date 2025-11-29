# Semana 3 – Matemática e Estatística para IA: Cálculo e Otimização

**Cronograma:** 03/02/2025 (início) a 09/03/2025 (entrega - domingo)

## Objetivos de aprendizagem
- Calcular derivadas e gradientes em funções de múltiplas variáveis.
- Compreender otimização convexa vs. não convexa e implicações para treinamento de modelos.
- Implementar e comparar algoritmos de otimização clássicos.

## Tópicos-chave
- Derivadas, gradientes e regra da cadeia.
- Otimização convexa e não convexa.
- Algoritmos de otimização: Gradiente Estocástico, Momentum, Adam, Algoritmos Genéticos (visão geral).

## Entregas
- Notebook com dedução de gradientes para funções simples e visualização de superfícies.
- Implementação comparando SGD, Momentum e Adam em um problema de regressão logística binária.
- Mini-relatório com análise de convergência e escolha de hiperparâmetros.

## Leituras sugeridas
- "Deep Learning" – Goodfellow, Bengio & Courville (cap. 4–8, focando em otimização).
- Notas de curso sobre convexidade e condições de Karush-Kuhn-Tucker (KKT) para referência.

## Exercício guiado
- Treine um classificador logístico em um dataset simples (ex.: `sklearn.datasets.make_moons`) usando SGD e Adam. Plote as curvas de perda, discuta estabilidade e sensibilidade a taxa de aprendizado.
