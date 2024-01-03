<!--
 * @Description: 
 * @Author: shenlei
 * @Modified: linhui
 * @Date: 2023-12-19 10:31:41
 * @LastEditTime: 2024-01-03 17:28:02
 * @LastEditors: shenlei
-->
<h1 align="center">BCEmbedding: Bilingual and Crosslingual Embedding for RAG</h1>

<div align="center">
    <a href="./LICENSE">
      <img src="https://img.shields.io/badge/license-Apache--2.0-yellow">
    </a>
    &nbsp;&nbsp;&nbsp;&nbsp;
    <a href="https://twitter.com/YDopensource">
      <img src="https://img.shields.io/badge/follow-%40YDOpenSource-1DA1F2?logo=twitter&style={style}">
    </a>
    &nbsp;&nbsp;&nbsp;&nbsp;
</div>
<br>

<p align="center">
  <strong style="background-color: green;">English</strong>
  |
  <a href="./README_zh.md" target="_Self">简体中文</a>
</p>

<details open="open">
<summary>Click to Open Contents</summary>

- <a href="#-bilingual-and-crosslingual-superiority" target="_Self">🌐 Bilingual and Crosslingual Superiority</a>
- <a href="#-key-features" target="_Self">💡 Key Features</a>
- <a href="#-latest-updates" target="_Self">🚀 Latest Updates</a>
- <a href="#-model-list" target="_Self">🍎 Model List</a>
- <a href="#-manual" target="_Self">📖 Manual</a>
  - <a href="#installation" target="_Self">Installation</a>
  - <a href="#quick-start" target="_Self">Quick Start</a>
- <a href="#%EF%B8%8F-evaluation" target="_Self">⚙️ Evaluation</a>
  - <a href="#evaluate-semantic-representation-by-mteb" target="_Self">Evaluate Semantic Representation by MTEB</a>
  - <a href="#evaluate-rag-by-llamaindex" target="_Self">Evaluate RAG by LlamaIndex</a>
- <a href="#-leaderboard" target="_Self">📈 Leaderboard</a>
  - <a href="#semantic-representation-evaluations-in-mteb" target="_Self">Semantic Representation Evaluations in MTEB</a>
  - <a href="#rag-evaluations-in-llamaindex" target="_Self">RAG Evaluations in LlamaIndex</a>
- <a href="#-youdaos-bcembedding-api" target="_Self">🛠 Youdao's BCEmbedding API</a>
- <a href="#-wechat-group" target="_Self">🧲 WeChat Group</a>
- <a href="#%EF%B8%8F-citation" target="_Self">✏️ Citation</a>
- <a href="#-license" target="_Self">🔐 License</a>
- <a href="#-related-links" target="_Self">🔗 Related Links</a>

</details>
<br>

**B**ilingual and **C**rosslingual **Embedding** (`BCEmbedding`), developed by NetEase Youdao, encompasses `EmbeddingModel` and `RerankerModel`. The `EmbeddingModel` specializes in generating semantic vectors, playing a crucial role in semantic search and question-answering, and the `RerankerModel` excels at refining search results and ranking tasks. 

`BCEmbedding` serves as the cornerstone of Youdao's Retrieval Augmented Generation (RAG) implmentation, notably [QAnything](http://qanything.ai) [[github](https://github.com/netease-youdao/qanything)], an open-source implementation widely integrated in various Youdao products like [Youdao Speed Reading](https://read.youdao.com/#/home) and [Youdao Translation](https://fanyi.youdao.com/download-Mac?keyfrom=fanyiweb_navigation). 

Distinguished for its bilingual and crosslingual proficiency, `BCEmbedding` excels in bridging Chinese and English linguistic gaps, which achieves
- **A high performence on <a href="#semantic-representation-evaluations-in-mteb" target="_Self">Semantic Representation Evaluations in MTEB</a>**;
- **A new benchmark in the realm of <a href="#rag-evaluations-in-llamaindex" target="_Self">RAG Evaluations in LlamaIndex</a>**.

## 🌐 Bilingual and Crosslingual Superiority

Existing embedding models often encounter performance challenges in bilingual and crosslingual scenarios, particularly in Chinese, English and their crosslingual tasks. `BCEmbedding`, leveraging the strength of Youdao's translation engine, excels in delivering superior performance across monolingual, bilingual, and crosslingual settings.

`EmbeddingModel` supports ***Chinese (ch) and English (en)*** (more languages support will come soon), while `RerankerModel` supports ***Chinese (ch), English (en), Japanese (ja) and Korean (ko)***.

## 💡 Key Features

- **Bilingual and Crosslingual Proficiency**: Powered by Youdao's translation engine, excelling in Chinese, English and their crosslingual retrieval task, with upcoming support for additional languages.

- **RAG-Optimized**: Tailored for diverse RAG tasks including **translation, summarization, and question answering**, ensuring accurate **query understanding**. See <a href="#rag-evaluations-in-llamaindex" target="_Self">RAG Evaluations in LlamaIndex</a>.

- **Efficient and Precise Retrieval**: Dual-encoder for efficient retrieval of `EmbeddingModel` in first stage, and cross-encoder of `RerankerModel` for enhanced precision and deeper semantic analysis in second stage.

- **Broad Domain Adaptability**: Trained on diverse datasets for superior performance across various fields.

- **User-Friendly Design**: Instruction-free, versatile use for multiple tasks without specifying query instruction for each task.

- **Meaningful Reranking Scores**: `RerankerModel` provides relevant scores to improve result quality and optimize large language model performance.

- **Proven in Production**: Successfully implemented and validated in Youdao's products.

## 🚀 Latest Updates

- ***2024-01-03***: **Model Releases** - [bce-embedding-base_v1](https://huggingface.co/maidalun1020/bce-embedding-base_v1) and [bce-reranker-base_v1](https://huggingface.co/maidalun1020/bce-reranker-base_v1) are available.
- ***2024-01-03***: **Eval Datasets** [[CrosslingualMultiDomainsDataset](https://huggingface.co/datasets/maidalun1020/CrosslingualMultiDomainsDataset)] - Evaluate the performence of RAG, using [LlamaIndex](https://github.com/run-llama/llama_index).
- ***2024-01-03***: **Eval Datasets** [[Details](./BCEmbedding/evaluation/c_mteb/Retrieval.py)] - Evaluate the performence of crosslingual semantic representation, using [MTEB](https://github.com/embeddings-benchmark/mteb).

## 🍎 Model List

| Model Name | Model Type | Languages | Parameters | Weights |  
|:-------------------------------|:--------:|:--------:|:--------:|:--------:|  
| bce-embedding-base_v1 | `EmbeddingModel` | ch, en | 279M | [download](https://huggingface.co/maidalun1020/bce-embedding-base_v1) |  
| bce-reranker-base_v1 | `RerankerModel` | ch, en, ja, ko | 279M | [download](https://huggingface.co/maidalun1020/bce-reranker-base_v1) |  

## 📖 Manual

### Installation

First, create a conda environment and activate it.
```bash
conda create --name bce python=3.10 -y
conda activate bce
```

Then install `BCEmbedding`:
```bash
pip install BCEmbedding
```

Or install from source:
```bash
git clone git@github.com:netease-youdao/BCEmbedding.git
cd BCEmbedding
pip install -v -e .
```

### Quick Start

Use `EmbeddingModel` by `BCEmbedding`, and `cls` [pooler](./BCEmbedding/models/embedding.py#L24) is default.

```python
from BCEmbedding import EmbeddingModel

# list of sentences
sentences = ['sentence_0', 'sentence_1', ...]

# init embedding model
model = EmbeddingModel(model_name_or_path="maidalun1020/bce-embedding-base_v1")

# extract embeddings
embeddings = model.encode(sentences)
```

Use `RerankerModel` by `BCEmbedding` to calculate relevant scores and rerank:

```python
from BCEmbedding import RerankerModel

# your query and corresponding passages
query = 'input_query'
passages = ['passage_0', 'passage_1', ...]

# construct sentence pairs
sentence_pairs = [[query, passage] for passage in passages]

# init reranker model
model = RerankerModel(model_name_or_path="maidalun1020/bce-reranker-base_v1")

# method 0: calculate scores of sentence pairs
scores = model.compute_score(sentence_pairs)

# method 1: rerank passages
rerank_results = model.rerank(query, passages)
```

## ⚙️ Evaluation

### Evaluate Semantic Representation by MTEB

We provide evaluation tools for `embedding` and `reranker` models, based on [MTEB](https://github.com/embeddings-benchmark/mteb) and [C_MTEB](https://github.com/FlagOpen/FlagEmbedding/tree/master/C_MTEB).

#### 1. Embedding Models

Just run following cmd to evaluate `your_embedding_model` (e.g. `maidalun1020/bce-embedding-base_v1`) in **monolingual, bilingual and crosslingual settings** (e.g. `["en", "zh", "en-zh", "zh-en"]`).

```bash
python BCEmbedding/tools/eval_mteb/eval_embedding_mteb.py --model_name_or_path maidalun1020/bce-embedding-base_v1 --pooler cls
```

The total evaluation tasks contain ***114 datastes*** of **"Retrieval", "STS", "PairClassification", "Classification", "Reranking" and "Clustering"**.

***NOTE:***
- All models are evaluated in their **recommended pooling method (`pooler`)**. "jina-embeddings-v2-base-en", "m3e-base" and "m3e-large" use `mean` pooler, while the others use `cls`.
- "jina-embeddings-v2-base-en" model should be loaded with `trust_remote_code`.
```bash
python BCEmbedding/tools/eval_mteb/eval_embedding_mteb.py --model_name_or_path {moka-ai/m3e-base | moka-ai/m3e-large} --pooler mean

python BCEmbedding/tools/eval_mteb/eval_embedding_mteb.py --model_name_or_path jinaai/jina-embeddings-v2-base-en --pooler mean --trust_remote_code
```

#### 2. Reranker Models

Run following cmd to evaluate `your_reranker_model` (e.g. "maidalun1020/bce-reranker-base_v1") in **monolingual, bilingual and crosslingual settings** (e.g. `["en", "zh", "en-zh", "zh-en"]`).

```bash
python BCEmbedding/tools/eval_mteb/eval_reranker_mteb.py --model_name_or_path maidalun1020/bce-reranker-base_v1
```

The evaluation tasks contain ***12 datastes*** of **"Reranking"**.

#### 3. Metrics Visualization Tool

We proveide a one-click script to sumarize evaluation results of `embedding` and `reranker` models as [Embedding Models Evaluation Summary](./Docs/EvaluationSummary/embedding_eval_summary.md) and [Reranker Models Evaluation Summary](./Docs/EvaluationSummary/reranker_eval_summary.md).

```bash
python BCEmbedding/evaluation/mteb/summarize_eval_results.py --results_dir {your_embedding_results_dir | your_reranker_results_dir}
```

### Evaluate RAG by LlamaIndex

[LlamaIndex](https://github.com/run-llama/llama_index) is a famous data framework for LLM-based applications, particularly in RAG. Recently, the [LlamaIndex Blog](https://blog.llamaindex.ai/boosting-rag-picking-the-best-embedding-reranker-models-42d079022e83) has evaluated the popular embedding and reranker models in RAG pipeline and attract great attention. Now, we follow its pipeline to evaluate our `BCEmbedding`.

First, install LlamaIndex:
```bash
pip install llama-index==0.9.22
```

Export your "openai" and "cohere" app keys to env:
```bash
export OPENAI_API_KEY={your_openai_api_key}
export COHERE_APPKEY={your_cohere_api_key}
```


#### 1. Metrics Definition

- Hit Rate:

  Hit rate calculates the fraction of queries where the correct answer is found within the top-k retrieved documents. In simpler terms, it's about how often our system gets it right within the top few guesses. ***The larger, the better.***

- Mean Reciprocal Rank (MRR):
  
  For each query, MRR evaluates the system's accuracy by looking at the rank of the highest-placed relevant document. Specifically, it's the average of the reciprocals of these ranks across all the queries. So, if the first relevant document is the top result, the reciprocal rank is 1; if it's second, the reciprocal rank is 1/2, and so on. ***The larger, the better.***

#### 2. Reproduce [LlamaIndex Blog](https://blog.llamaindex.ai/boosting-rag-picking-the-best-embedding-reranker-models-42d079022e83)

In order to compare our `BCEmbedding` with other embedding and reranker models fairly, we provide a one-click script to reproduce results of the LlamaIndex Blog, including our `BCEmbedding`:
```bash
# There should be two GPUs available at least.
CUDA_VISIBLE_DEVICES=0,1 python BCEmbedding/tools/eval_rag/eval_llamaindex_reproduce.py
```

Then, sumarize the evaluation results by:
```bash
python BCEmbedding/tools/eval_rag/summarize_eval_results.py --results_dir BCEmbedding/results/rag_reproduce_results
```

Results Reproduced from the LlamaIndex Blog can be checked in ***[Reproduced Summary of RAG Evaluation](./Docs/EvaluationSummary/rag_eval_reproduced_summary.md)***, with some obvious ***conclusions***:
- In `WithoutReranker` setting, our `bce-embedding-base_v1` outperforms all the other embedding models.
- With fixing the embedding model, our `bce-reranker-base_v1` achieves the best performence.
- ***The combination of `bce-embedding-base_v1` and `bce-reranker-base_v1` is SOTA.***

#### 3. Broad Domain Adaptability

The evaluation of [LlamaIndex Blog](https://blog.llamaindex.ai/boosting-rag-picking-the-best-embedding-reranker-models-42d079022e83) is **monolingual, small amount of data, and specific domain** (just including "llama2" paper). In order to evaluate the **broad domain adaptability, bilingual and crosslingual capability**, we follow the blog to build a multiple domains evaluation dataset (includding "Computer Science", "Physics", "Biology", "Economics", "Math", and "Quantitative Finance". [Details](./BCEmbedding/tools/eval_rag/eval_pdfs/)), named [CrosslingualMultiDomainsDataset](https://huggingface.co/datasets/maidalun1020/CrosslingualMultiDomainsDataset), **by OpenAI `gpt-4-1106-preview` for high quality**.

First, run following cmd to evaluate the most popular and powerful embedding and reranker models:

```bash
# There should be two GPUs available at least.
CUDA_VISIBLE_DEVICES=0,1 python BCEmbedding/tools/eval_rag/eval_llamaindex_multiple_domains.py
```

Then, run the following script to sumarize the evaluation results:
```bash
python BCEmbedding/tools/eval_rag/summarize_eval_results.py --results_dir BCEmbedding/results/rag_results
```

The summary of multiple domains evaluations can be seen in <a href="#1-multiple-domains-scenarios" target="_Self">Multiple Domains Scenarios</a>.

## 📈 Leaderboard

### Semantic Representation Evaluations in MTEB

#### 1. Embedding Models

| Model | Retrieval | STS | PairClassification | Classification | Reranking | Clustering | Avg |  
|:-------------------------------|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|:--------:|  
| bge-base-en-v1.5 | 37.14 | 55.06 | 75.45 | 59.73 | 43.05 | 37.74 | 47.20 |  
| bge-base-zh-v1.5 | 47.60 | 63.72 | 77.40 | 63.38 | 54.85 | 32.56 | 53.60 |  
| bge-large-en-v1.5 | 37.15 | 54.09 | 75.00 | 59.24 | 42.68 | 37.32 | 46.82 |  
| bge-large-zh-v1.5 | 47.54 | 64.73 | **79.14** | 64.19 | 55.88 | 33.26 | 54.21 |  
| jina-embeddings-v2-base-en | 31.58 | 54.28 | 74.84 | 58.42 | 41.16 | 34.67 | 44.29 |  
| m3e-base | 46.29 | 63.93 | 71.84 | 64.08 | 52.38 | 37.84 | 53.54 |  
| m3e-large | 34.85 | 59.74 | 67.69 | 60.07 | 48.99 | 31.62 | 46.78 |  
| ***bce-embedding-base_v1*** | **57.60** | **65.73** | 74.96 | **69.00** | **57.29** | **38.95** | ***59.43*** |  

***NOTE:***
- Our ***bce-embedding-base_v1*** outperforms other opensource embedding models with various model size.
- ***114 datastes*** of **"Retrieval", "STS", "PairClassification", "Classification", "Reranking" and "Clustering"** in `["en", "zh", "en-zh", "zh-en"]` setting.
- The [crosslingual evaluation datasets](./BCEmbedding/evaluation/c_mteb/Retrieval.py) we released belong to `Retrieval` task.
- More evaluation details please check [Embedding Models Evaluation Summary](./Docs/EvaluationSummary/embedding_eval_summary.md).

#### 2. Reranker Models

| Model | Reranking | Avg |  
|:-------------------------------|:--------:|:--------:|  
| bge-reranker-base | 57.78 | 57.78 |  
| bge-reranker-large | 59.69 | 59.69 |  
| ***bce-reranker-base_v1*** | **60.06** | ***60.06*** |  

***NOTE:***
- Our ***bce-reranker-base_v1*** outperforms other opensource reranker models.
- ***12 datastes*** of **"Reranking"** in `["en", "zh", "en-zh", "zh-en"]` setting.
- More evaluation details please check [Reranker Models Evaluation Summary](./Docs/EvaluationSummary/reranker_eval_summary.md).

### RAG Evaluations in LlamaIndex

#### 1. Multiple Domains Scenarios

<img src="./Docs/assets/rag_eval_multiple_domains_summary.jpg">

***NOTE:***
- In `WithoutReranker` setting, our `bce-embedding-base_v1` outperforms all the other embedding models.
- With fixing the embedding model, our `bce-reranker-base_v1` achieves the best performence.
- **The combination of `bce-embedding-base_v1` and `bce-reranker-base_v1` is SOTA**.

## 🛠 Youdao's BCEmbedding API

For users who prefer a hassle-free experience without the need to download and configure the model on their own systems, `BCEmbedding` is readily accessible through Youdao's API. This option offers a streamlined and efficient way to integrate BCEmbedding into your projects, bypassing the complexities of manual setup and maintenance. Detailed instructions and comprehensive API documentation are available at [Youdao BCEmbedding API](https://ai.youdao.com/DOCSIRMA/html/aigc/api/embedding/index.html). Here, you'll find all the necessary guidance to easily implement `BCEmbedding` across a variety of use cases, ensuring a smooth and effective integration for optimal results.

## 🧲 WeChat Group

Welcome to scan the QR code below and join the WeChat group.

<img src="./Docs/assets/Wechat.jpg" width="20%" height="auto">

## ✏️ Citation

If you use `BCEmbedding` in your research or project, please feel free to cite and star it:

```
@misc{youdao_bcembedding_2023,
    title={BCEmbedding: Bilingual and Crosslingual Embedding for RAG},
    author={NetEase Youdao, Inc.},
    year={2023},
    howpublished={\url{https://github.com/netease-youdao/BCEmbedding}}
}
```

## 🔐 License

`BCEmbedding` is licensed under [Apache 2.0 License](./LICENSE)

## 🔗 Related Links

[Netease Youdao - QAnything](https://github.com/netease-youdao/qanything)

[FlagEmbedding](https://github.com/FlagOpen/FlagEmbedding)

[MTEB](https://github.com/embeddings-benchmark/mteb)

[C_MTEB](https://github.com/FlagOpen/FlagEmbedding/tree/master/C_MTEB)

[LLama Index](https://github.com/run-llama/llama_index) | [LlamaIndex Blog](https://blog.llamaindex.ai/boosting-rag-picking-the-best-embedding-reranker-models-42d079022e83)