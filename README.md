```

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

# Adding the counting function. 
```
# Example usage
pdf_path = "example.pdf"
extracted_text = extract_text_from_pdf(pdf_path)
word_count = count_words(extracted_text)

print(extracted_text)
print(f"\nTotal word count: {word_count}")

```

I've updated our code to include a new function `count_words` that counts the number of words in the extracted text. Here's an explanation of the changes:

1. We've added a new import at the top: `import re`. This is for using regular expressions in our word counting function.

2. The new `count_words` function does the following:
   - It removes special characters and digits from the text using regular expressions. This ensures that we're only counting actual words.
   - It splits the text into words using the `split()` method, which by default splits on whitespace.
   - It returns the length of the resulting list of words, which gives us our word count.

3. In the example usage section, we now call `count_words` on our extracted text and print the result.

This implementation provides a basic word count, but keep in mind a few considerations:

- It treats hyphenated words as separate words.
- It doesn't handle contractions in any special way (e.g., "don't" would be counted as two words).
- It removes all numbers, so "42" would not be counted as a word.

You can adjust the regular expressions in the `count_words` function if you need different behavior for these cases.
