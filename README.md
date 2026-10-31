# REaCT fine-tuning dataset for Mistral-7B-Instruct-v0.3

Finalist project, Mistral × Cerebral Valley hackathon, Station F, Paris, May 2024, team of three. I adapted the chemistry agent [ChemCrow](https://github.com/ur-whitelab/chemcrow-public) for Mistral and built a synthetic chemistry dataset using GPT-4/GPT-4o, filtered by a GPT-4 reviewer, for fine-tuning Mistral-7B-Instruct-v0.3. The goal: an open model instead of GPT-4, because pharma clients are cautious with closed APIs.

**Write-up:** [Create REaCT Fine-Tuning Dataset for Mistral-7b-Instruct-v0.3 with LangChain, GPT-4, and Self-Reflection](https://medium.com/@ahmet_celebi/create-react-fine-tuning-dataset-for-mistral-7b-instruct-v0-3-d6556bab7c56) (30 May 2024).

## How it works

1. `chemcrow/agents/mistral.py` wraps Mistral-7B-Instruct-v0.3 as a LangChain LLM, so ChemCrow can use it in place of GPT-4.
2. In `Tutorial_create_intruct_dataset.ipynb`, GPT-4 writes chemistry questions for the selected ChemCrow tools (`all_tools[4:]`).
3. ChemCrow on GPT-4o answers each question with REaCT steps (thought, action, observation).
4. A GPT-4 reviewer checks each answer: reasoning, final answer, tool choice and question quality. One "no" drops it.
5. The loop runs up to 20 times per tool. The kept examples are the dataset for [mistral-finetune](https://github.com/mistralai/mistral-finetune).

I trained the model with LoRA during the hackathon. I could not load the LoRA weights before the deadline, so the demo did not use the fine-tuned model. The repo and the article report no benchmark numbers.

## Status and credits

This is the tutorial version of the notebook, and it has known errors. `create_dataset` returns two values, but the loop unpacks three (cell line 636). The formatting step keeps only the first tool step of each trace (line 488). It pins `openai==0.27.8` and needs an OpenAI key.

The `chemcrow/` package is ChemCrow by Andres M. Bran, Sam Cox, Andrew White and Philippe Schwaller (MIT licence, White Laboratory, see `LICENSE`). This repo adds the Mistral adapter and the dataset notebook. Teammates: Clément Castelon (Mol-Instructions fine-tune and serving) and Phil Rohr (frontend and infrastructure). Commits in this repo: Clemspace.

<details>
<summary>Original README</summary>

# REaCT-FT-DATASET-TUTORIAL

This project was developed for a hackathon at Station F in Paris, hosted by Mistral and Cerebral Valley. The focus is on fine-tuning the Mistral-7b-Instruct-v0.3 with function-calling capabilities. This repository contains the implementation of ChemCrow with a Mistral backbone. The detailed steps and insights will be shared in an upcoming Medium article.

Once the fine-tuning dataset is created, refer to the [Mistral fine-tuning GitHub repository](https://github.com/mistralai/mistral-finetune). It is self-explanatory on how to fine-tune Mistral on the created dataset. Make sure to download the Mistral-7b-Instruct-v0.3 version to make it work.

Please note, this was a 20-hour hackathon project, so there might be some errors and certainly room for improvement.

## 👩‍💻 Installation

```
python setup.py install 
```

```bibtex
@misc{REaCT-FT-DATASET-TUTORIAL,
    author = "Ahmet Celebi",
    year = "2024",
    url = "https://github.com/AmT42/REaCT-FT-DATASET-TUTORIAL",
    email = "ahmet_celebi@hotmail.fr",
    company = "DeltaWave"
}
```
# REaCT-FT-DATASET-TUTORIAL

</details>
