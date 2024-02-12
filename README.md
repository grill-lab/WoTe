# Wizard of Tasks Dataset - extractive QA extension

## Intro

The dataset is a subset of the **Wizard of Tasks** dataset introduced by [Choi et al (2022)](https://aclanthology.org/2022.coling-1.310.pdf).

## Dataset

The dataset contains 826 different questions. It contains 
- 364 Cooking Questions
- 465 DIY Question

### What's from WoT?
Each question was originally crowdsourced by crowdworkers by Choi et al. We use the following information they include in each question and answer turn.
- question text
- free-text intent label
- binary relevancy label
- binary usefulness label

Each conversation includes the following useful information:
- document_url including a link to the current task

We combine the user question turn with next the answe turn by the agent to result in the following information:
- question text
- answer text
- binary answer usefulness
- binary answer relevancy
- document_url

### Filtering process

TO DO
... This results in 826 question-answer pairs

### What is new from us?

We include the following new fields for each QA pair:
- conversation_id
- question_id
- task title
- task steps
- task ingredients
- task description
- task domain (~cooking~ or ~diy~)
- annotated extracted answer span from context
- annotated question type labels from one or more of 7 question categories (confirmation, complex, causal, listing, history, navigation)
- data_split (if the question belongs to train, validation or test)
- history of the conversation before the question (in the format "student: ... | teacher: ..."), if applicable


An QA pair therefore contains the following fields:
```
{
    "conversation_id": "",
    "question_id": "",
    "question": "",
    "original_answer": "",
    "extracted_answer": "",
    "document_url": "",
    "task_data": {
        "title": "",
        "steps": [],
        "ingredients": [],
        "description": ""
    },
    "domain": "",
    "question_type": []
}
```

We share all data split into train, validation and test split in the three following files:
- train.json
- validation.json
- test.json

|          | Count |
|----------|-------|
| Test     | 412   |
| Train    | 248   |
| Validation | 167 |