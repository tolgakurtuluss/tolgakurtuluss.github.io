---
layout: post
title: "ghrepo - LangChain Text Chunker"
subtitle: An Interactive Tool for Splitting Text with Gradio
gh-repo: tolgakurtuluss/langchain-text-chunker
gh-badge: [star, fork, follow]
tags: [english, langchain, python, rag, gradio, llm, ai]
comments: true
author: Tolga
---

When working with Large Language Models (LLMs) and Retrieval-Augmented Generation (RAG) systems, splitting long documents into smaller "chunks" is essential for better performance. This project is a simple Gradio web app called LangChain Text Chunker. It lets users upload files (PDF, DOCX, TXT, HTML, Python code, Jupyter notebooks, CSV, etc.), extract the text, and try different LangChain text splitting methods interactively.You can adjust parameters like chunk size, overlap, and separators. The app shows the resulting chunks in JSON format, adds metadata (like start index), and generates ready-to-use Python code for each splitter. 

Supported splitters include RecursiveCharacterTextSplitter, CharacterTextSplitter, MarkdownHeaderTextSplitter, PythonCodeTextSplitter, and TokenTextSplitter.

This project is open-source, easy to run locally with python app.py, and has a live demo on [Hugging Face Spaces](https://huggingface.co/spaces/tolgadev/langchain-text-chunker).

<a href="https://github.com/tolgakurtuluss/langchain-text-chunker" target="_blank">
  <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" alt="View on GitHub" style="height: 40px; vertical-align: middle; margin-right: 10px; background: white; border-radius: 6px; padding: 5px;">
  View Repository on GitHub
</a>

 <a href="https://huggingface.co/spaces/tolgadev/langchain-text-chunker" target="_blank">
  <img src="https://upload.wikimedia.org/wikipedia/commons/d/d6/Hf-logo-with-title.svg" alt="Try Demo on Hugging Face" style="height: 40px; vertical-align: middle; margin-right: 10px;">
  Try the Live Demo on Hugging Face Spaces
</a>

