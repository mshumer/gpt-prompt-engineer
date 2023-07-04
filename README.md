# gpt-prompt-engineer
[![Twitter Follow](https://img.shields.io/twitter/follow/mattshumer_?style=social)](https://twitter.com/mattshumer_) [![Open In Colab]([https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/12-tefxwf2VvZp5F-XJA0xQh9mSX4RE9L?usp=sharing)

## Overview

Prompt engineering is kind of like alchemy. There's no clear way to predict what will work best. It's all about experimenting until you find the right prompt. `gpt-prompt-engineer` is a tool that takes this experimentation to a whole new level.

**Simply input a description of your task and some test cases, and the system will generate, test, and rank a multitude of prompts to find the ones that perform the best.**

## Features

- **Prompt Generation**: Using GPT-4 and GPT-3.5-Turbo, `gpt-prompt-engineer` can generate a variety of possible prompts based on a provided use-case and test cases.

- **Prompt Testing**: The real magic happens after the generation. The system tests each prompt against all the test cases, comparing their performance and ranking them using an ELO rating system.
<img width="1563" alt="Screen Shot 2023-07-04 at 11 41 54 AM" src="https://github.com/mshumer/gpt-prompt-engineer/assets/41550495/f8171cff-1703-40ca-b9fd-f0aa24d07110">

- **ELO Rating System**: Each prompt starts with an ELO rating of 1200. As they compete against each other in generating responses to the test cases, their ELO ratings change based on their performance. This way, you can easily see which prompts are the most effective.

## Setup
1. [Open the notebook in Google Colab](https://colab.research.google.com/drive/12-tefxwf2VvZp5F-XJA0xQh9mSX4RE9L?usp=sharing) or in a local Jupyter notebook.

2. Add your OpenAI API key to the line `openai.api_key = "ADD YOUR KEY HERE"`.

3. If you have GPT-4 access, you're ready to move on. If not, change `model='gpt-4'` inside `generate_candidate_prompts` to `model='gpt-3.5-turbo'`.

## How to Use

1. Define your use-case and test cases. The use-case is a description of what you want the AI to do. Test cases are specific prompts that you would like the AI to respond to. For example:

```
description = "Given a prompt, generate a landing page headline." # this style of description tends to work well

test_cases = [
    {
        'prompt': 'Promoting an innovative new fitness app, Smartly',
    },
    {
        'prompt': 'Why a vegan diet is beneficial for your health',
    },
    {
        'prompt': 'Introducing a new online course on digital marketing',
    },
    {
        'prompt': 'Launching a new line of eco-friendly clothing',
    },
    {
        'prompt': 'Promoting a new travel blog focusing on budget travel',
    },
    {
        'prompt': 'Advertising a new software for efficient project management',
    },
    {
        'prompt': 'Introducing a new book on mastering Python programming',
    },
    {
        'prompt': 'Promoting a new online platform for learning languages',
    },
    {
        'prompt': 'Advertising a new service for personalized meal plans',
    },
    {
        'prompt': 'Launching a new app for mental health and mindfulness',
    }
]
```

3. Choose how many prompts to generate. Keep in mind, this can get expensive if you generate many prompts. 10 is a good starting point.

4. Call `generate_optimal_prompt(description, test_cases, number_of_prompts)` to generate a list of potential prompts, and test and rate their performance.

5. The final ELO ratings will be printed in a table, sorted in descending order. The higher the rating, the better the prompt.
<img width="1074" alt="Screen Shot 2023-07-04 at 11 48 45 AM" src="https://github.com/mshumer/gpt-prompt-engineer/assets/41550495/324f90b8-c0ee-45fd-b219-6c44d9aa281b">


## Contributions are welcome!!

## License

This project is [MIT](https://github.com/your_username/your_repository/blob/master/LICENSE) licensed.

## Contact

Matt Shumer - [@mattshumer_](https://twitter.com/mattshumer_)

Project Link: [https://github.com/mshumer/gpt-prompt-engineer](url)
