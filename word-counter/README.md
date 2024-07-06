

# Example usage
pdf_path = "example.pdf"
extracted_text = extract_text_from_pdf(pdf_path)
print(extracted_text)

```

This code provides a function `extract_text_from_pdf` that takes a PDF file path as input and returns the extracted text. Here's a breakdown of how it works:

1. It uses PyPDF2 to read the PDF file and iterate through its pages.
2. For each page, it first attempts to extract text using PyPDF2's built-in method.
3. If PyPDF2 fails to extract text (which can happen with scanned documents or complex layouts), it uses an AI-based OCR (Optical Character Recognition) model from Hugging Face's Transformers library.
4. The extracted text from all pages is combined and returned.

To use this code, you'll need to install the required libraries:

```
pip install PyPDF2 transformers torch
```

Please note that this code assumes you have a way to convert PDF pages to images for the AI-based OCR. In a real implementation, you'd need to add this step, possibly using a library like pdf2image.

Also, the AI model used here (microsoft/trocr-base-handwritten) is just an example. You might want to experiment with different models depending on your specific needs and the types of PDFs you're working with.
