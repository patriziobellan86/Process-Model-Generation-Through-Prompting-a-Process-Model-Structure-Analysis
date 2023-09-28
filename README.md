Process Model Generation Through Prompting: a Graph Structure Analysis
=====================================================================

In this repository we provide the material related to this research article.

We adopt the following conventions:
- Filenames correspond to the PET documents
- Folder in UPPERCASE correspond to the prompt template (parameter 1) used in experiments.

The file *activitylabels normalized.json* contains the list of the activity labels normalized.
The file has the following data-structure:
```json
    {DOC-NAME:
            {ACTIVITY-COORDINATE: activity label normalized,
            }
    }
```
where, *DOC-NAME* is the name of the corresponding PET document and *ACTIVITY-COORDINATE* indicate the sentence number and the index of the word within the sentence of the corresponding activty annotated in the PET dataset.
N.B. Sentence number indexes and word indexes start from 0.
For example,  coordinate (5 7) means sentence number 5, word number 7.

The folder *GoldStandard DFG models* contain the gold-standard DFG process models we created starting from the PET dataset annotations.
In folder *Predicted DFG models* we provide the DFG process models predicted by the LLM in both settings (Incremental  and Gold Standard).

The prompt templates we experiment with are provided in the folder *Prompts*.
Here we adopt the following name convention:
- **RAW** is the baseline prompt template;
- **RAW CONTEXT** is the baseline prompt template enhanced with problem-context information;
- **SHOTS** is the in-context learning prompt template we custominze with MIN, MAX, and COV training sets;
- **SHOTS CONTEXT** is the **SHOTS** prompt template enhanced with problem-context information.

The folder *Results* contains the predictions.
In task T1, the files has the following data-structure:
```json
    {doc-name:
        prompt-template-name:
            {
              "raw answer": The raw answer of the LLM,
              "extracted":  The prediction of the LLM after the extraction of the activity labels
            }
    }
```    
For task T2, files have the following data-structure:
```json
    {doc-name:
        {building strategy setting:
            {prompt-template-name:
                {
                  "raw answer": The raw answer of the LLM
                  "extracted":  The prediction of the LLM after the extraction of the activity relations
                }
           }
    }
```


To reproduce the results you could log into [OpenAI Playground](https://platform.openai.com/playground), copy and paste the prompt you want to test, fill the place-holders of the prompt with the right information,  and then run the LLM.
For example, if you are interested in running the RAW prompt template for task T1 for text *doc-1.1*, you should copy and paste the prompt template in the playground and substitute the place-holders with the text of the document *doc-1.1*.

The PET dataset is available on [HuggingFace](https://huggingface.co/datasets/patriziobellan/PETv11).