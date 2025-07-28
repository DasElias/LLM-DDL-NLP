# Encoding of the Australian Telecommunications Consumer Protections Code (2012) in Defeasible Deontic Logic by LLMs

The repository [DDL-NLP](https://github.com/gvdgdo/DDL-NLP) contains the manually curated gold standard that was used as a benchmark for evaluating the here presented results.

The dataset in this repository has been used for: 
TODO


## Structure of the Repository
### Experiment 1 (Section 4.1)
This folder contains the comparison of the different LLMs in the base experiment.

- DeepSeek-R1
- DeepSeek-V3
- GPT-4o mini
- GPT-4o
- OpenAI o1
- OpenAI o3 mini (high)
- OpenAI o3
- OpenAI o4 mini (high)

### Experiment 2
#### Experiment 2_1 (Section 4.2.1)
This folder contains the results when the complete formalization history was incorporated in the form of alternating `user` and `assistant` messages.

- DeepSeek-R1
- DeepSeek-V3
- GPT-4o
- OpenAI o3
- OpenAI o4 mini (high)

OpenAI o1, OpenAI o3 mini (high) and GPT-4o mini were not considered in this experiment, as these models were already outdated at the time of the experiment or had demonstrated disappointing performance in the previous experiment.

#### Experiment 2_2 (Section 4.4.2)

This folder contains the results when all previously formalized atoms were provided collectively in a single `user` message, rather than replicating the entire previous dialog history.

- DeepSeek-R1
- DeepSeek-V3
- GPT-4o

#### Experiment 2_3 (Section 4.4.3)

This folder contains the results when the entire formalization happens in a single interaction. 

- DeepSeek-R1
- GPT-4o
- OpenAI o4 mini (high)

The models not listed were not further considered in this experiment, as—due to time constraints—only those that performed best in the first experiment were included. An exception to this is OpenAI’s o3 model, which was excluded because it generated output that did not adhere to the predefined XML structure.

### Experiment 3 (Section 4.3)

This experiment aimed to evaluate the effectiveness of fine-tuned models for the given task.

The sub-experiments 3_1, 3_2 and 3_3 refer to the Configurations 1, 2, 3 in the paper. The suffixes `-ft-chkpt-44`/`-ft-chkpt-11` denote the results obtained after the first epoch of fine-tuning, while the suffixes `-ft-chkpt-88` and `-ft-chkpt-22` indicate the results after the second epoch. If there is just the suffix `-ft`, this means that the results are about the final fine-tuned model.

### Experiment 4 (Section 4.4)

This experiment refers to the two-stage pipeline setup of the paper. Each sub-experiment evaluates the formalization step based on the atom extraction of a different LLM.

* Experiment 4_1: atom extraction using a GPT-4o finetune
* Experiment 4_2: atom extraction using DeepSeek-R1
* Experiment 4_3: atom extraction using OpenAI o3
* Experiment 4_4: atom extraction using OpenAI o4 mini (high)

## Structure of the result files

Each file has a `<Paragraphs>` element as root element, which in turn has several `<Paragraph>` child elements. They represent individual law snippets. Such an element contains the following children:
* `<RelevantText>` contains the law text that was fed to the LLMs for the formalization. 
* `<Rules>` contains the rules of the gold standard, with `<Original>` being the `<FormalRepresentation>` tag of the gold standard, while for the `<Simple>` tag, the atom names are transformed into camel case. 
* `<Generated>` contains the literal output of the LLM. 