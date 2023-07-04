# gpt-prompt-engineer
[![Twitter Follow](https://img.shields.io/twitter/follow/mattshumer_?style=social)](https://twitter.com/mattshumer_)

## Overview

Prompt engineering is kind of like alchemy. There's no clear way to predict what will work best. It's all about experimenting until you find the right prompt. `gpt-prompt-engineer` is a tool that takes this experimentation to a whole new level.

**Simply input a description of your task and some test cases, and the system will generate, test, and rank a multitude of prompts to find the ones that perform the best.**

## Features

- **Prompt Generation**: Using GPT-4 and GPT-3.5-Turbo, `gpt-prompt-engineer` can generate a variety of possible prompts based on a provided use-case and test cases.

- **Prompt Testing**: The real magic happens after the generation. The system tests each prompt against all the test cases, comparing their performance and ranking them using an ELO rating system.
<img width="1563" alt="Screen Shot 2023-07-04 at 11 41 54 AM" src="https://github.com/mshumer/gpt-prompt-engineer/assets/41550495/f8171cff-1703-40ca-b9fd-f0aa24d07110">

- **ELO Rating System**: Each prompt starts with an ELO rating of 1200. As they compete against each other in generating responses to the test cases, their ELO ratings change based on their performance. This way, you can easily see which prompts are the most effective.

## Setup
1. Open this colab LINK LINK.

2. Add your OpenAI API key to the line `openai.api_key = "ADD YOUR KEY HERE"`.

3. If you have GPT-4 access, you're ready to move on. If not, change `model='gpt-4'` inside `generate_candidate_prompts` to `model='gpt-3.5-turbo'`.

## How to Use

1. Define your use-case and test cases. The use-case is a description of what you want the AI to do. Test cases are specific prompts that you would like the AI to respond to.

2. Choose how many prompts to generate. Keep in mind, this can get expensive if you generate many prompts. 10 is a good starting point.

3. Call `generate_optimal_prompt(description, test_cases, number_of_prompts)` to generate a list of potential prompts, and test and rate their performance.

4. The final ELO ratings will be printed in a table, sorted in descending order. The higher the rating, the better the prompt.
```+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+
|                                                                                                                                                                                                                                                                                                  Prompt                                                                                                                                                                                                                                                                                                  |       Rating       |
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+
|                                                                                         Your task is to generate a catchy and engaging headline for a landing page. You will be given a brief description of the product, service, or concept that needs to be promoted. Your headline should be persuasive, concise, and highlight the unique selling point or main benefit of what's being promoted. Remember, a good headline can make a significant difference in attracting potential clients or customers.                                                                                         | 1233.4753616256708 |
|                                                                            Given a brief sentence or phrase describing a product, service, or theme, your task is to generate a catchy, persuasive headline for a landing page. The headline should not only encapsulate the main idea succinctly but should also inspire curiosity, interest, and excitement in potential customers or audience members. Remember, a powerful headline is the first impression and the doorway to the content or offering you're promoting.                                                                             | 1190.2438134923411 |
| Your task is to generate a compelling and attention-grabbing headline for a landing page. You'll be given a brief description or prompt about the subject, such as a new product, service, blog, or app. Your headline should succinctly capture the essence of the subject and stimulate the interest of potential visitors or customers. Use your creativity and marketing skills to create headlines that appeal to your audience's needs, desires, or curiosity. Please remember that your output should be a single sentence that effectively communicates the unique selling point of the subject. | 1176.280824881988  |
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------+```

## Contributions are welcome!!
