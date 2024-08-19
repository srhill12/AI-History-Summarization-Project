
# AI History Summarization Project

This project uses the `transformers` library to summarize the history of artificial intelligence (AI) using the `facebook/bart-large-cnn` model. The project leverages the model to generate both the most likely and more diverse summaries of the provided AI history text.

## Getting Started

To run this project in Google Colab:

### 1. Install Dependencies

To start, you need to install the `transformers` library:

```python
!pip install transformers
```

### 2. Initialize the Summarization Pipeline

After installing the necessary libraries, you can import and initialize the pipeline using the `facebook/bart-large-cnn` model for summarization:

```python
from transformers import pipeline

# Initialize the summarization pipeline
summarizer = pipeline("summarization", model="facebook/bart-large-cnn")
```

### 3. Load and Process the AI History Text

Load your AI history text data:

```python
filepath = "Resources/AI_history.txt"
with open(filepath) as f:
    ai_text = f.read().replace('\n', ' ')
```

### 4. Generate Summaries

You can generate both the most likely and a more diverse summary of the AI history text using the following code:

#### Most Likely Summary

```python
most_likely_summary = summarizer(ai_text, min_length=50, max_length=150, do_sample=False)

# Display the most likely summary
print(most_likely_summary[0]["summary_text"])
```

#### Diverse Summary

```python
diverse_summary = summarizer(ai_text, min_length=50, max_length=150, do_sample=True)

# Display the diverse summary
print(diverse_summary[0]["summary_text"])
```

### 5. Example Output

Here are example outputs for the most likely and diverse summaries:

#### Most Likely Summary

```
"The history of artificial intelligence (AI) began in antiquity, with myths, stories and rumors of artificial beings endowed with intelligence or consciousness by master craftsmen. The seeds of modern AI were planted by philosophers who attempted to describe the process of human thinking as the mechanical manipulation of symbols. Alan Turing was the first person to carry out substantial research in the field that he called Machine Intelligence. The field of AI research was founded at a workshop held on the campus of Dartmouth College, USA during the summer of 1956."
```

#### Diverse Summary

```
"The history of artificial intelligence (AI) began in antiquity, with myths, stories and rumors of artificial beings endowed with intelligence or consciousness by master craftsmen. Alan Turing was the first person to carry out substantial research in the field that he called Machine Intelligence. The field of AI research was founded at a workshop held on the campus of Dartmouth College, USA during the summer of 1956. In 1974, in response to the criticism from James Lighthill, the U.S. and British Governments stopped funding undirected research into artificial intelligence."
```

## Notes

- **Dependencies**: Ensure that all dependencies are correctly installed. The key dependency for this project is the `transformers` library from Hugging Face.
- **Text Data**: The text data used in this example is about the history of artificial intelligence. You can replace this with any other text data you are interested in summarizing.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

