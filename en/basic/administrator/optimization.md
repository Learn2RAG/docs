## Optimization

Learn2RAG provides an optimization process to automatically find a suitable configuration for the RAG pipeline.

### How it works

The optimization process uses [SMAC](https://github.com/automl/smac3) to search through the available configurations. For each selected configuration, Learn2RAG runs the pipeline on the training data and evaluates the generated answers.
Based on these results, SMAC continues searching for better configurations. After the optimization completes, the best configuration found is saved and used by the pipeline.

### Training data

The optimization requires a training file containing example questions and their expected answers. A sample file can be found [here](/static/sample_data/training_data_sample.csv).