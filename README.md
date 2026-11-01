# REaCT fine-tuning dataset for Mistral-7B-Instruct-v0.3

Finalist project, Mistral × Cerebral Valley hackathon, Station F, Paris, May 2024. I adapted the chemistry agent [ChemCrow](https://github.com/ur-whitelab/chemcrow-public) for Mistral and built a synthetic chemistry dataset using GPT-4/GPT-4o, filtered by a GPT-4 reviewer, for fine-tuning Mistral-7B-Instruct-v0.3.

**Write-up:** [Create REaCT Fine-Tuning Dataset for Mistral-7b-Instruct-v0.3](https://medium.com/@ahmet_celebi/create-react-fine-tuning-dataset-for-mistral-7b-instruct-v0-3-d6556bab7c56) (30 May 2024).

## How it works

1. `chemcrow/agents/mistral.py` lets ChemCrow use Mistral-7B-Instruct-v0.3 in place of GPT-4.
2. GPT-4 writes chemistry questions for ChemCrow's tools.
3. ChemCrow on GPT-4o answers them with REaCT steps (thought, action, observation).
4. A GPT-4 reviewer keeps the examples it accepts.
5. The kept examples train Mistral with [mistral-finetune](https://github.com/mistralai/mistral-finetune).

## Credits

`chemcrow/` is ChemCrow by Bran, Cox, White and Schwaller (MIT, White Laboratory). Team: Clément Castelon and Phil Rohr. Tutorial code from 2024.

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
