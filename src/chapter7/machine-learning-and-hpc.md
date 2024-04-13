# Machine Learning & HPC

## What is Machine Learning?

Machine learning is a subset of artificial intelligence that involves developing AI models that enable computers to learn from and make predictions or decisions based on vast amounts of data. It pertains to training the model on these large datasets to identify patterns and insights, and automatically learn about these data to predict results from new, unseen data. The training datasets contain pre-determined outputs and their respective inputs, allowing the ML model to pick up patterns that enable these outputs to occur.

## How a ML model is trained

During the training phase of a ML algorithm, it uses the training dataset to predict the output, and then compares the predicted output to the actual output to measure the disparity and compute the loss. Next, the gradient of the loss against the model parameters is calculated and used to update the model parameters via gradient descent. This process is repeated for a specific number of times or until the loss is below a certain threshold.
Since ML algorithms often deal with massive training datasets and complex models, the training usually takes a very long time and requires significant computational resources. HPC provides a way to speed this process up by distributing the dataset or model across different nodes/GPUs. There are two main forms of parallelism - Data Parallelism and Model Parallelism.

## Data Parallelism

Data parallelism involves dividing and distributing the training dataset across multiple nodes/GPUs. Each node receives a copy of the ML model, and they individually process their portion of the data to compute the gradient. The gradients are then averaged and the weights in all the models in all the nodes are appropriately tuned. Data parallelism is more suited for instances where the training dataset is massive and the individual samples can be processed independently, such as CNNs.

## Model Parallelism

Model parallelism involves partitioning the layers of the model across nodes/GPUs, allowing different parts of the model to process different batches of data simultaneously. Each node receives a layer of the ML model, and these nodes are aligned in a way that the output of one node is an input to another. These nodes individually process a different batch of data simultaneously, and then pass the data and activations to the next node. The same batch of data is passed from one node to another, with the next batch following right after. Model parallelism is more suited for models with large memory requirements or complex architectures, such as NLPs.
