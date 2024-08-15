# CoRE: LLM as Interpreter for Natural Language Programming of Agents

The rapid advancements in generative AI technologies, particularly in Large Language Models (LLMs), have paved the way for AI agents to tackle increasingly complex tasks. However, despite these innovations, current LLM agents often rely solely on their inherent knowledge and reasoning abilities, underutilizing valuable human expertise and detailed guidance. This limitation can result in suboptimal solutions, particularly in scenarios requiring nuanced understanding or specialized input. One promising approach to addressing this issue is through natural language programming, which allows human instructions to be effectively represented. In this paper, we introduce a novel system, Code Representation and Execution (CoRE), which leverages LLMs as interpreters to execute natural language programs. CoRE addresses key challenges in natural language programming by introducing structured syntax for logic representation, mechanisms for precise step-by-step execution, and components for information retrieval and tool usage. To overcome the limitations of LLMs, such as token constraints and domain-specific knowledge gaps, CoRE employs temporary memory for intermediate results and integrates external tools for enhanced problem-solving. Furthermore, CoRE ensures accurate task progression by requiring LLMs to evaluate current outputs before determining subsequent steps. This collaborative approach, combining human instructions with advanced AI, enhances the effectiveness and contextual accuracy of AI-driven problem-solving.

## Preparation

0. Clone this repo.

1. Create a conda virtual environment and install necessary packages:

```
conda create -n your_env_name python=3.9
conda activate your_env_name
pip install -r requirements.txt
```

2. Download the OpenAGI data from this [Google Drive link](https://drive.google.com/drive/folders/1AjT6y7qLIMxcmHhUBG5IE1_5SnCPR57e?usp=share_link), unzip it to the `CoRE` directory and rename it as `openagi_data`.

3. Download the [database](https://drive.google.com/file/d/1pF1Sw6pBmq2sFkJvm-LzJOqrmfWoQgxE/view?usp=drive_link) and unzip it to the `CoRE` directory (i.e., `your/path/CoRE`) and rename it as `travel_database`.
   
4. Make sure you are in the *CoRE/src* folder before running the codes. Otherwise,

```
cd src
```

## Programs in CoRE System

OpenAGI: in `src/info/OpenAGI/OpenAGI_Flow.txt`

TravelPlanner: in `sec/info/TravelPlanner/TravelPlanner_Flow.txt`

## Running Command Examples

OpenAGI on gpt-4-1106-preview:
```commandline
python main.py \
--flow_name=OpenAGI_Flow.txt \
--tool_name=tools.txt \
--task=OpenAGI \
--log_file_name=OpenAGI_gpt_log.txt \
--model_name=gpt-4-1106-preview \
--openai_key="YOUR OPENAI KEY"
```

OpenAGI on TheBloke/Mixtral-8x7B-Instruct-v0.1-GPTQ:
```commandline
python main.py \
--flow_name=OpenAGI_Flow.txt \
--tool_name=tools.txt \
--task=OpenAGI \
--log_file_name=OpenAGI_mixtral_log.txt \
--model_name=TheBloke/Mixtral-8x7B-Instruct-v0.1-GPTQ \
--openai_key="YOUR OPENAI KEY"
```

TravelPlanner on gpt-4-1106-preview:
```commandline
python main.py \
--flow_name=TravelPlanner_Flow.txt \
--tool_name=tools.txt \
--task=TravelPlanner \
--log_file_name=TravelPlanner_gpt_log.txt \
--results_name=gpt \
--model_name=gpt-4-1106-preview \
--openai_key="YOUR OPENAI KEY"
```

TravelPlanner on TheBloke/Mixtral-8x7B-Instruct-v0.1-GPTQ:
```commandline
python main.py \
--flow_name=TravelPlanner_Flow.txt \
--tool_name=tools.txt \
--task=TravelPlanner \
--log_file_name=TravelPlanner_mixtral_log.txt \
--results_name=mixtral \
--model_name=TheBloke/Mixtral-8x7B-Instruct-v0.1-GPTQ \
--openai_key="YOUR OPENAI KEY"
```

## Reference

- We leveraged the dataset of [OpenAGI](https://github.com/agiresearch/OpenAGI) and [TravelPlanner](https://github.com/OSU-NLP-Group/TravelPlanner/tree/main) projects to implement our experiment.
