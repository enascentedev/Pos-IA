# Semana 11 – Processamento de Linguagem Natural (NLP)

**Cronograma:** 10/11/2025 (início) a 23/11/2025 (entrega - domingo)

## Objetivos de aprendizagem
- Preparar texto com técnicas de tokenização, lematização e vetorização.
- Treinar modelos clássicos de NLP e redes neurais para sequências.
- Explorar modelos de linguagem modernos baseados em Transformer.

## Tópicos-chave
- Tokenização, Lemmatização, Stemização.
- Modelos de Linguagem (n-grams, word embeddings como Word2Vec/Glove).
- Redes neurais para NLP (RNN, LSTM, Transformer – visão geral).
- Tarefas: análise de sentimentos, tradução automática, classificação de texto.

## Entregas
- Notebook com pré-processamento de texto e treinamento de um classificador de sentimentos (ex.: dataset IMDB ou tweets).
- Experimento com embeddings pré-treinados vs. vetorização TF-IDF, comparando desempenho.
- Protótipo mínimo usando um Transformer pré-treinado (ex.: `bert-base-uncased` via `transformers`) para classificação ou extração de features.

## Leituras sugeridas
- "Speech and Language Processing" – Jurafsky & Martin (capítulos de modelagem de linguagem e redes neurais).
- Documentação da biblioteca `transformers` (Hugging Face) para uso básico de modelos pré-treinados.

## Exercício guiado
- Monte um pipeline de classificação de sentimentos comparando: (1) Regressão logística com TF-IDF, (2) LSTM com embeddings, (3) Transformer pré-treinado. Relate métricas e custo computacional.
