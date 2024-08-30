Downloading a paper from the internet and interacting with its content involves several steps and third-party libraries. Since you're just starting with Python, I'll outline a high-level approach and provide some simple code snippets to get you started.

1. **Download the Paper**: You can use libraries like `requests` to download a PDF.
2. **Extract Text**: To extract and process text from a PDF, you can use libraries like `PyMuPDF` or `PyPDF2`.
3. **Ask Questions**: Interacting with the content would involve natural language processing (NLP). A basic approach would be to use simple keyword matching, but more advanced querying would require machine learning models. For simplicity, I’ll illustrate keyword matching.

Let’s focus on the first two steps with some simple code snippets. Please note that to run this code, you need to install some packages. You can install them using pip:

```
pip install requests PyMuPDF
```

Here’s how you could get started:

1. **Download the Paper**:

```python
import requests

url = "https://arxiv.org/pdf/1706.03762.pdf"  # URL of "Attention is All You Need" paper
response = requests.get(url)

with open("attention_is_all_you_need.pdf", "wb") as file:
    file.write(response.content)

print("PDF downloaded successfully.")
```

2. **Extract Text from PDF**:

```python
import fitz  # PyMuPDF

pdf_document = "attention_is_all_you_need.pdf"
pdf = fitz.open(pdf_document)

text = ""
for page_num in range(pdf.page_count):
    page = pdf.load_page(page_num)
    text += page.get_text()

with open("extracted_text.txt", "w") as text_file:
    text_file.write(text)

print("Text extracted and saved successfully.")
```

3. **Simple Keyword Matching for Questions**:

```python
def search_for_keyword(text, keyword):
    lines = text.split('\n')
    results = [line for line in lines if keyword.lower() in line.lower()]
    return results

keyword = input("Enter a keyword to search for: ")
with open("extracted_text.txt", "r") as file:
    paper_text = file.read()

search_results = search_for_keyword(paper_text, keyword)

if search_results:
    for result in search_results:
        print(result)
else:
    print("Keyword not found in the paper.")
```

This code reads the text from the paper and searches for lines containing the keyword you input. This is a basic approach and doesn't involve any sophisticated NLP techniques.

This should get you started with downloading, extracting, and searching the text from a PDF paper. For more advanced question-answering, you would need to explore NLP libraries like spaCy or transformer models like those from Hugging Face's `transformers` library.

Let me know if you need further clarification or more detailed code!