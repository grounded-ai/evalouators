## GroundedEval by GroundedAI

### Overview

The `grounded-eval` package is a powerful tool developed by GroundedAI to evaluate the performance of large language models (LLMs) and their applications. It leverages small language models and adapters to compute various metrics, providing insights into the quality and reliability of LLM outputs.

### Features

- **Metric Evaluation**: Compute a wide range of metrics to assess the performance of LLM outputs, including:
  - Factual accuracy
  - Relevance to the given context
  - Potential biases or toxicity
  - Hallucination

- **Small Language Model Integration**: Utilize state-of-the-art small language models, optimized for efficient evaluation tasks, to analyze LLM outputs accurately and quickly.

- **Adapter Support**: Leverage GroundedAI's proprietary adapters, such as the `phi3-toxicity-judge` adapter, to fine-tune the small language models for specific domains, tasks, or evaluation criteria, ensuring tailored and precise assessments.

- **Flexible Input/Output Handling**: Accept LLM outputs in various formats (text, JSON, etc.) and provide evaluation results in a structured and easily consumable manner.

- **Customizable Evaluation Pipelines**: Define and configure evaluation pipelines to combine multiple metrics, weights, and thresholds based on your specific requirements.

- **Reporting and Visualization**: Generate comprehensive reports and visualizations to communicate evaluation results effectively, facilitating decision-making and model improvement processes.

### Getting Started

Install the `grounded-eval` package:

```
pip install grounded-eval
```

### Example Usage: Toxicity Evaluation

The `ToxicityEvaluator` class is used to evaluate the toxicity of a given text. Here's an example of how to use it:

```python
from grounded_eval.evaluators import ToxicityEvaluator

base_model_id = "microsoft/Phi-3-mini-4k-instruct"
groundedai_eval_id = "grounded-ai/phi3-toxicity-judge"

# Initialize the ToxicityEvaluator
evaluator = ToxicityEvaluator(base_model_id, groundedai_eval_id, quantization=True)

# Load the base model and the GroundedAI adapter
evaluator.load_model(base_model_id, groundedai_eval_id)

# Define the data to be evaluated
data = [
    "That guy is so stupid and ugly",
    "Bunnies are so fluffy and cute"
]

# Evaluate the data for toxicity
response = evaluator.evaluate(data)

# Output
# {'toxic': 1, 'non-toxic': 1, 'percentage_toxic': 50.0}
print(response)
```

In this example, we initialize the `ToxicityEvaluator` with the base model ID (`microsoft/Phi-3-mini-4k-instruct`) and the GroundedAI adapter ID (`grounded-ai/phi3-toxicity-judge`). The `quantization` parameter is set to `True` to enable quantization for faster inference.

We then load the base model and the GroundedAI adapter using the `load_model` method.

Next, we define a list of texts (`data`) that we want to evaluate for toxicity.

Finally, we call the `evaluate` method with the `data` list, and it returns a dictionary containing the number of toxic and non-toxic texts, as well as the percentage of toxic texts.

In the output, we can see that out of the two texts, one is classified as toxic, and the other as non-toxic, resulting in a 50% toxicity percentage.

### Documentation

Detailed documentation, including API references, examples, and guides, coming soon at [https://groundedai.tech/api](https://groundedai.tech/api).

### Contributing

We welcome contributions from the community! If you encounter any issues or have suggestions for improvements, please open an issue or submit a pull request on the [GroundedAI grounded-eval GitHub repository](https://github.com/GroundedAI/grounded-eval).

### License

The `grounded-eval` package is released under the [MIT License](https://opensource.org/licenses/MIT).