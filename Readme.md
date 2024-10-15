### What you need to do:

You are expected to deliver the following:

* **Correct implementations** and **evaluations** of **the methods** required by this project specifications.
* **Write-up** about the **retrieval methods** used, including:
  - **description** of the method you implemented.
  - **evaluation settings** with explanation followed.
  - **discussion** of the findings.

Both the implementations and write-ups must be documented within this Jupyter notebook.

In this Project-Part 2, you are required to perform the following implementations and evaluations, also ilustrated below:
<center>
<img src="project2-task.svg" alt="project2-task" width="500" title="Fig.2 IR Project-2-Illustration"/>
</center>

### Required Methods to Implement

* Indexing
  - **Pyserini index command**: You first need to index the new collection used in this project. You should be familiar with how to use the command to build an index for the given collection from `week1-week3`.
* IR models
  - **Pyserini BM25**: (traditional) Using the Pyserini API to ***retrieve*** top-k documents. Check `week2`.
  - **Standard DPR Dense Retriever** (neural): Using standard DPR to ***retrieve*** top-k documents. Check `week9`.
  - **TILDEv2** (neural): Using TILDEv2 to ***retrieve*** top-k documents. Check `week9`.
  - **TinyLlama** (generative): Using TinyLlama to implement RAG. Check `week10`.

***N.B.***

In this assignment, we aim to **retrieve (full-rank)** documents rather than **rerank** them, which is different from the `week9` prac.


### Required Evaluations to Perform
In this project, we provide a dataset sampled from the original MS-MARCO passage collection. Your first task is to check this dataset and get familiar with the size, content, format, and consider how to process it.

**Task-1**: *Traditional model vs. Neural models*
1. Run your **BM25** with the default k,b settings on the given dataset (k=1.3, b=0.75) to retrieve the top-10 passages as the **baseline**.
2. Run your **DPR** and **TILDEv2** on the given dataset to **retrieve** top-10 passages. Compare the results from each method to the BM25 baseline separately (*Note: Only reranking the BM25 top documents using DPR or TILDEv2 will result in a 0 mark*).
3. Conduct **statistical significance tests** on the models’ retrieval effectiveness.
4. Summarise the results in a table, including the statistical significance.
5. Create a **gain-loss plot** comparing each neural models against the BM25 baseline at the query level.


**Task-2**: *Exploring Generative models*
1. Use TinyLlama (or any other LLMs of your choice) to do RAG on each query by taking the top-3 retrieved documents from both traditional & neural methods, and generating answers for the query separately.

2. Design **two** methods/measures to evaluate the RAG-generated answers for each query. You can define them by yourself or implement from other papers. Provide a detailed explaination for the methods or measures you choose. Ensure that you first understand the query and the relevant passages from the dataset, then determine what the correct answer to each query should be.

 Some papers to start with:
 - [The Workbench for Neural Retrieval Research](https://arxiv.org/pdf/2405.13177)
 - [Evaluating Generative Ad Hoc Information Retrieval](https://arxiv.org/abs/2311.046949)

3. Document the methods and measures you used, as well as your analysis of the results for each query. Explain the measure scores you assign to the generated answers and justify your reasoning for each score.

4. Create a **correlation plot** for each RAG evaluation measure. Each plot should display the correlation between the differences in retrieval performance (NDCG@3) and the differences in the RAG evaluation measure, comparing the results derived from the best Task-1 model (either DPR or TILDEv2) with the results derived from BM25. You can find an example of this plot in the corresponding section below.

***Bonus Tasks*** (5 marks each, contribute to your final course mark in (capped)100):
- Implement **point-wise** and **pair-wise** reranking with an LLM on top-10 results from the best model identified in task-1 based on NDCG@3. These results should also be included into the Task-1 evalaution requirements (e.g. table, stat test, gain-loss plot).
- Design **two additional** methods to evaluate RAG generated answers. These measures must be different from those already devised in Task-2 and should address a different aspect of the information need. Provide a detailed explanation of the methods/measures you choose. Follow the Task-2 evaluation requirements (including result analysis for each query, correlation plots).


### Discussions
**Task-1**: *Traditional model vs. Neural models*
1. Comment on **trends and differences** observed in your results. Is there a method that **consistently outperforms** others on all the queries for the dataset?

**Task-2**: *Exploring Generative models*
1. Perform the **correlation** ploting and answer the question: How does retrieval effectiveness impact the quality of the generated responses, and why?

### Evaluation Measures
Evaluate the retrieval methods using the following measures:

**Task-1**: *Traditional model vs. Neural models*
- **NDCG at 3** (`ndcg_cut_3`): Use this as the measure for comparing and reporting results from traditional and neural methods.

**Task-2**: *Exploring Generative models*
- **customised**: Use this as the measure for evaluating LLM generated results.

All **gain-loss plots** should be produced with respect to **nDCG at 3**.

For **statistical significance analysis**, use the **paired t-test** and distinguish between **p < 0.05** and **p < 0.01**.

### How to submit

Submit **one** `.zip` file containing:

1. this notebook in `.ipynb` format
2. this notebook saved as a <mark> .pdf </mark> by navigating to the menu and selecting `File -> Save and Export Notebook As -> HTML`, then open and `Print`as with your browser.


***N.B.***
(**<mark>Penalty Applied</mark>**)
- Ensure that the code is executable. Include all your discussions and analysis within this notebook, **<mark>not as a separate file**</mark>.
- **<mark>Code without evidence that it runs (e.g. results)**</mark> will **<mark>not be considered**</mark>.
- **<mark>Don't add any runs, indexes</mark> in the zip file!**

- **<mark>Optimize your report length</mark>, don't exceed 200 pages! (+another 50 pages if you implement the bonus parts)**

- Submit the file via the link on the INFS7410 course site on BlackBoard by **<mark>18 October</mark> 2024, <mark>16:00</mark> Eastern Australia Standard Time**, unless you have received an extension according to UQ policy, which must be requested **before** the assignment due date.
