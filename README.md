[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/huangwl18/language-planner/blob/main/src/demo.ipynb)
## Language Models as Zero-Shot Planners:<br>Extracting Actionable Knowledge for Embodied Agents

#### [[Project Page]](https://huangwl18.github.io/language-planner/) [[Paper]](https://arxiv.org/pdf/2201.07207.pdf) [[Video]](https://www.youtube.com/watch?v=CkyugWI3_fc)

[Wenlong Huang](https://wenlong.page)<sup>1</sup>, [Pieter Abbeel](http://people.eecs.berkeley.edu/~pabbeel/)<sup>1</sup>, [Deepak Pathak](https://www.cs.cmu.edu/~dpathak/)\*<sup>2</sup>, [Igor Mordatch](https://scholar.google.com/citations?user=Vzr1RukAAAAJ&hl=en)\*<sup>3</sup> (*equal advising)

<sup>1</sup>University of California, Berkeley, <sup>2</sup>Carnegie Mellon University, <sup>3</sup>Google Brain<br/>

<img  src="images/action-translation.gif" width="550">

This is the official demo code for our [Language Models as Zero-Shot Planners](https://huangwl18.github.io/language-planner/) paper. The code demonstrates how Large Language Models, such as GPT-3 and Codex, can generate action plans for complex human activities (e.g. "make breakfast"), even without any further training. The code can be used with any available language models from [OpenAI API](https://openai.com/api/) and [Huggingface Transformers](https://huggingface.co/docs/transformers/index) with a common interface.

If you find this work useful in your research, please cite using the following BibTeX:

```bibtex
@article{huang2022language,
      title={Language Models as Zero-Shot Planners: Extracting Actionable Knowledge for Embodied Agents},
      author={Huang, Wenlong and Abbeel, Pieter and Pathak, Deepak and Mordatch, Igor},
      journal={arXiv preprint arXiv:2201.07207},
      year={2022}
    }
```

## Local Setup or [Open in Colab](https://colab.research.google.com/github/huangwl18/language-planner/blob/main/src/demo.ipynb)

### Requirements
- Python=3.6.13
- CUDA=11.3

### Setup Instructions
```Shell
git clone https://github.com/huangwl18/language-planner.git
cd language-planner/
conda create --name language-planner-env python=3.6.13
conda activate language-planner-env
pip install --upgrade pip
pip install -r requirements.txt
```

## Running Code

See [`demo.ipynb`](https://github.com/huangwl18/language-planner/blob/main/src/demo.ipynb) (or [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/huangwl18/language-planner/blob/main/src/demo.ipynb)) for a complete walk-through of our method. Feel free to experiment with any household tasks that you come up with (or any tasks beyond household domain if you provide necessary actions in [`available_actions.json`](https://github.com/huangwl18/language-planner/blob/main/src/available_actions.ipynb))!

**Note:**
- It is observed that best results can be obtained with larger language models. If you cannot run [Huggingface Transformers](https://huggingface.co/models?pipeline_tag=text-generation&sort=downloads) models locally or on Google Colab due to memory constraint, it is recommended to register an [OpenAI API](https://openai.com/api/) account and use GPT-3 or Codex (As of 01/2022, $18 free credits are awarded to new accounts and Codex series are free after [admitted from the waitlist](https://share.hsforms.com/1GzaACuXwSsmLKPfmphF_1w4sk30?)).
- Due to language models' high sensitivity to sampling hyperparameters, you may need to tune sampling hyperparameters for different models to obtain the best results.
- The code uses the list of available actions supported in [VirtualHome 1.0](https://github.com/xavierpuigf/virtualhome/tree/v1.0.0)'s [Evolving Graph Simulator](https://github.com/xavierpuigf/virtualhome/tree/v1.0.0/simulation). The available actions are stored in [`available_actions.json`](https://github.com/huangwl18/language-planner/blob/main/src/available_actions.json). The actions should support a large variety of household tasks. However, you may modify or replace this file if you're interested in a different set of actions or a different domain of tasks (beyond household domain).
- A subset of the [manually-annotated examples](http://virtual-home.org/release/programs/programs_processed_precond_nograb_morepreconds.zip) originally collected by the [VirtualHome paper](https://arxiv.org/pdf/1806.07011.pdf) is used as available examples in the prompt. They are transformed to natural language format and stored in [`available_examples.json`](https://github.com/huangwl18/language-planner/blob/main/src/available_examples.json). Feel free to change this file for a different set of available examples.