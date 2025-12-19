---
layout: post
title: "ghrepo - ShinyChatGPT"
subtitle: A ChatGPT Clone Built with R and Shiny
gh-repo: tolgakurtuluss/shinychatgpt
gh-badge: [star, fork, follow]
tags: [english, r, shiny, chatgpt, openai, gpt, llm, ai]
comments: true
author: Tolga
---


ShinyChatGPT is a fully functional ChatGPT clone built entirely in R using the Shiny framework. It provides a clean, interactive web interface to OpenAI's Chat Completions API, allowing you to chat with models like GPT-3.5-turbo, GPT-4, and GPT-4o directly from your browser.

## Chat Screen (Dark Mode)
![](https://raw.githubusercontent.com/tolgakurtuluss/shinychatgpt/refs/heads/main/example1.jpg)

## Chat Screen (Light Mode)
![](https://raw.githubusercontent.com/tolgakurtuluss/shinychatgpt/refs/heads/main/example2.jpg)

## Chat Interface
![](https://raw.githubusercontent.com/tolgakurtuluss/shinychatgpt/refs/heads/main/example3.jpg)

Key Features:
- Modern chat interface with styled message bubbles
- Light/dark theme toggle (saved in browser)
- Adjustable parameters: temperature, max tokens, and custom system prompt
- Loading spinner during API responses
- Download chat history as a file
- Clear chat functionality
- Fully responsive design

The app is lightweight, requires only a few R packages (shiny, shinyjs, httr, jsonlite), and can be run locally in seconds. Just set your OpenAI API key as an environment variable and launch it.It's a great example of how to integrate powerful LLMs into R-based web applications without needing Python or JavaScript frameworks.Try the live demo or run it yourself!

<a href="https://github.com/tolgakurtuluss/shinychatgpt" target="_blank">
  <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" alt="View on GitHub" style="height: 40px; vertical-align: middle; margin-right: 10px; background: white; border-radius: 6px; padding: 5px;">
  View Repository on GitHub
</a>

 <a href="https://tolgakurtuluss.shinyapps.io/shinychatgpt/" target="_blank">
  <img src="https://upload.wikimedia.org/wikipedia/commons/b/bf/Shiny_hex_logo.svg" alt="Try Live Demo on shinyapps.io" style="height: 55px; vertical-align: middle; margin-right: 10px;">
  Try the Live Demo on shinyapps.io
</a>

