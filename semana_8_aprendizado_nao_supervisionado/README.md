# Semana 8 – Aprendizado Não Supervisionado

**Cronograma:** 28/07/2025 (início) a 31/08/2025 (entrega - domingo)

## Objetivos de aprendizagem
- Identificar padrões e estruturas ocultas em dados sem rótulos.
- Reduzir dimensionalidade preservando variância e interpretabilidade.
- Utilizar autoencoders como técnica não supervisionada.

## Tópicos-chave
- Clustering (K-means, DBSCAN, agrupamento hierárquico).
- Análise de Componentes Principais (PCA) e outras técnicas de redução de dimensionalidade.
- Autoencoders (estrutura básica, função de perda, reconstrução).

## Entregas
- Notebook aplicando K-means e DBSCAN a um dataset de pontos 2D e comparando resultados.
- Demonstração de PCA em dados de alta dimensionalidade (ex.: dígitos) com visualização 2D/3D.
- Implementação de um autoencoder simples em `keras` ou `pytorch` com avaliação de erro de reconstrução.

## Leituras sugeridas
- "An Introduction to Statistical Learning" – James et al. (capítulo de clustering e PCA).
- Artigos ou tutoriais sobre autoencoders e variacionais (visão introdutória).

## Exercício guiado
- Aplique PCA antes de rodar K-means em um dataset de imagens. Compare métricas de silhueta com/sem PCA e discuta impacto no tempo de treinamento.
