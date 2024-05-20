# Metacognitive Span Categorization
This is a project to develop a tool for classifying contructed responses from students about their study strategies. Our dataset comprises 1,355 responses from students asking them what study strategies they used to study for a test. These responses were coded by expert raters into eight categories:
- Rewrite
- Highlight
- Summarize
- Quizzing
- Examples
- Comparisons
- Explain
- MA

We have two goals in this project:
 1. Develop a multilabel classification tool for identifying metacognitive strategies.
 2. Develop a span categorization tool to identify the precise character indices where the discussion of the metacognitive strategies.

## Multi-label classification
We finetuned a multilabel classification tool from DeBERTa-v3-large using Huggingface. We used an 80/20 train/validation split without withholding any data for a test set. Because we have a smaller dataset, we did not withhold any of the data for a test set. Instead, we will test the model for generalizability on data which will be coded at a later date.

### Hyperparameter tuning
We used Weights and Biases to tune hyperparameters before training, using the recommended hyperparameters from [the paper released by the DeBERTa-v3 team](https://arxiv.org/pdf/2111.09543).

The results of the hyperparemeter tuning are in the figure below:

![hptuning results](/assets/hptuning.JPG)

The best model used the following hyperparameters:
- epochs: 10
- learning_rate: 9.946303722432942e-06
- warmup_steps: 500
- weight_decay: 0.01

The zero-information baseline accuracy (accuracy if we always predict no for every category) is 0.843. Results from the best performing model on the training data are in the figure below:

![hp results](/assets/hptuning-best_res.JPG)
