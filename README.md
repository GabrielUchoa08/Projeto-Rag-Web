# Chat com seus documentos (RAG) com Transformers/LLM

Projeto desenvolvido na matéria de Aprendizagem de Máquina e Mineração de Dados (DCA0133), que tem como objetivo criar um modelo de RAG que responde perguntas com base em PDFs ou TXTs enviados pelo usuário. Ela combina dois modelos baseados em Transformers: um para encontrar os trechos relevantes (embeddings) e outro para escrever a resposta (LLM), com uma interface feita com Gradio para melhor visualização.

## Como funciona

```
documento → divide em trechos → embeddings → pergunta vira embedding
         → busca por similaridade → trechos + pergunta no prompt → LLM → resposta
```


## Tecnologias

- **Python**, **PyTorch** e **Hugging Face Transformers**
- **sentence-transformers** com `paraphrase-multilingual-MiniLM-L12-v2` (embeddings multilíngues)
- **Qwen2.5-3B-Instruct** como LLM (com GPU) ou **Qwen2.5-0.5B-Instruct** (sem GPU)
- **pypdf** para leitura de PDFs
- **Gradio** para a interface web

## Configurações

Os parâmetros ficam na célula 2 do notebook:

| Variável | Padrão | Função |
|---|---|---|
| `MODELO_EMBEDDING` | `paraphrase-multilingual-MiniLM-L12-v2` | Modelo usado na busca |
| `MODELO_LLM` | `Qwen2.5-3B-Instruct` (GPU) | Modelo que gera a resposta |
| `TAMANHO_TRECHO` | 800 | Caracteres por trecho |
| `SOBREPOSICAO` | 150 | Caracteres repetidos entre trechos vizinhos |
| `TOP_K` | 4 | Quantidade de trechos entregues ao LLM |
| `MAX_TOKENS_RESPOSTA` | 400 | Tamanho máximo da resposta |

## Limitações

- O modelo pode errar ou inventar informações mesmo com o contexto fornecido; confira a resposta nos trechos exibidos.
- PDFs escaneados (imagens) não têm texto extraível e precisariam de OCR.
- A qualidade das respostas depende do tamanho dos trechos e da qualidade do documento.
- O índice fica em memória e é perdido quando a sessão do Colab termina.

## Referências

- Vaswani, A. et al. *Attention Is All You Need*. NeurIPS, 2017.
- Lewis, P. et al. *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks*. NeurIPS, 2020.

## Autor

[Gabriel Uchôa e Sara Gabrielly] · [ Aprendizagem de Máquina e Mineração de Dados (DCA0133) / Departamento de Engenharia da Computação e Automação da UFRN] · 