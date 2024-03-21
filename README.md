# gpt-prompt-engineer
[![Twitter Follow](https://img.shields.io/twitter/follow/mattshumer_?style=social)](https://twitter.com/mattshumer_) [![Open Main Version In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mshumer/gpt-prompt-engineer/blob/main/gpt_prompt_engineer.ipynb) [![Open Classification Version In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/16NLMjqyuUWxcokE_NF6RwHD8grwEeoaJ?usp=sharing)

## Overview

Prompt engineering is kind of like alchemy. There's no clear way to predict what will work best. It's all about experimenting until you find the right prompt. `gpt-prompt-engineer` is a tool that takes this experimentation to a whole new level.

**Simply input a description of your task and some test cases, and the system will generate, test, and rank a multitude of prompts to find the ones that perform the best.**

## *New 3/20/24: The Claude 3 Opus Version*
I've added a new version of gpt-prompt-engineer that takes full advantage of Anthropic's Claude 3 Opus model. This version auto-generates test cases and allows for the user to define multiple input variables, making it even more powerful and flexible. Try it out with the claude-prompt-engineer.ipynb notebook in the repo!

## *New 3/20/24: Claude 3 Opus -> Haiku Conversion Version*
This notebook enables you to build lightning-fast, performant AI systems at a fraction of the typical cost. By using Claude 3 Opus to establish the latent space and Claude 3 Haiku for the actual generation, you can achieve amazing results. The process works by leveraging Opus to produce a collection of top-notch examples, which are then used to guide Haiku in generating output of comparable quality while dramatically reducing both latency and cost per generation. Try it out with the opus-to-haiku-conversion.ipynb notebook in the repo!

## Features

- **Prompt Generation**: Using GPT-4, GPT-3.5-Turbo, or Claude 3 Opus, `gpt-prompt-engineer` can generate a variety of possible prompts based on a provided use-case and test cases.

- **Prompt Testing**: The real magic happens after the generation. The system tests each prompt against all the test cases, comparing their performance and ranking them using an ELO rating system.
<img width="1563" alt="Screen Shot 2023-07-04 at 11 41 54 AM" src="https://github.com/mshumer/gpt-prompt-engineer/assets/41550495/f8171cff-1703-40ca-b9fd-f0aa24d07110">

- **ELO Rating System**: Each prompt starts with an ELO rating of 1200. As they compete against each other in generating responses to the test cases, their ELO ratings change based on their performance. This way, you can easily see which prompts are the most effective.

- **Classification Version**: The `gpt-prompt-engineer -- Classification Version` notebook is designed to handle classification tasks. It evaluates the correctness of a test case by matching it to the expected output ('true' or 'false') and provides a table with scores for each prompt.
<img width="1607" alt="Screen Shot 2023-07-10 at 5 22 24 PM" src="https://github.com/mshumer/gpt-prompt-engineer/assets/41550495/d5c9f2a8-97fa-445d-9c38-dec744f77854">

- **Claude 3 Version**: The claude-prompt-engineer notebook is designed to work with Anthropic's Claude 3 Opus model. It auto-generates test cases and allows for multiple input variables, making it even more powerful and flexible.

- **Claude 3 Opus -> Haiku Conversion Version**: Designed to preserve Opus' quality for your use-case while getting the speed + cost benefits of using Haiku.

- **[Weights & Biases](https://wandb.ai/site/prompts) Logging**: Optional logging to [Weights & Biases](https://wandb.ai/site) of your configs such as temperature and max tokens, the system and user prompts for each part, the test cases used and the final ranked ELO rating for each candidate prompt. Set `use_wandb` to `True` to use. 

- **[Portkey](https://portkey.ai)**: Optional tool to log and trace all the prompt chains and their responses. Set `use_portkey` to `True` to use.

## Setup
1. [Open the notebook in Google Colab](https://colab.research.google.com/github/mshumer/gpt-prompt-engineer/blob/main/gpt_prompt_engineer.ipynb) or in a local Jupyter notebook. For classification, use [this one.](https://colab.research.google.com/drive/16NLMjqyuUWxcokE_NF6RwHD8grwEeoaJ?usp=sharing). For the Claude 3 version, use [this one.](https://colab.research.google.com/drive/1likU_S4VfkzoLMPfVdMs3E54cn_W6I7o?usp=sharing)

2. Add your OpenAI API key to the line `openai.api_key = "ADD YOUR KEY HERE"`. If you're using the Claude 3 version, add your Anthropic API key to the line `ANTHROPIC_API_KEY = "ADD YOUR KEY HERE"`.

## How to Use

1. If you are using the GPT-4 version, define your use-case and test cases. The use-case is a description of what you want the AI to do. Test cases are specific prompts that you would like the AI to respond to. For example:

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

For the classification version, your test cases should be in the format:

```
test_cases = [
    {
        'prompt': 'I had a great day!',
        'output': 'true'
    },
    {
        'prompt': 'I am feeling gloomy.',
        'output': 'false'
    },
    // add more test cases here
]
```

For the Claude 3 version, you can define input variables in addition to the use-case description:

```
description = "Given a prompt, generate a personalized email response."

input_variables = [
    {"variable": "SENDER_NAME", "description": "The name of the person who sent the email."},
    {"variable": "RECIPIENT_NAME", "description": "The name of the person receiving the email."},
    {"variable": "TOPIC", "description": "The main topic or subject of the email. One to two sentences."}
]
```

The test cases will be auto-generated based on the use-case description and input variables.

3. Choose how many prompts to generate. Keep in mind, this can get expensive if you generate many prompts. 10 is a good starting point.

4. Call `generate_optimal_prompt(description, test_cases, number_of_prompts)` to generate a list of potential prompts, and test and rate their performance. For the classification version, just run the last cell. For the Claude 3 version, call `generate_optimal_prompt(description, input_variables, num_test_cases, number_of_prompts, use_wandb)`.

5. The final ELO ratings will be printed in a table, sorted in descending order. The higher the rating, the better the prompt.
<img width="1074" alt="Screen Shot 2023-07-04 at 11 48 45 AM" src="https://github.com/mshumer/gpt-prompt-engineer/assets/41550495/324f90b8-c0ee-45fd-b219-6c44d9aa281b">

For the classification version, the scores for each prompt will be printed in a table (see the image above).

## Contributions are welcome! Some ideas:
- have a number of different system prompt generators that create different styles of prompts, to cover more ground (ex. examples, verbose, short, markdown, etc.)
- automatically generate the test cases
- expand the classification version to support more than two classes using tiktoken

## License

This project is [MIT](https://github.com/your_username/your_repository/blob/master/LICENSE) licensed.

## Contact

Matt Shumer - [@mattshumer_](https://twitter.com/mattshumer_)

Project Link: [https://github.com/mshumer/gpt-prompt-engineer](url)

Lastly, if you want to try something even cooler than this, sign up for [HyperWrite Personal Assistant](https://app.hyperwriteai.com/personalassistant) (most of my time is spent on this). It's basically an AI with access to real-time information that a) is incredible at writing naturally, and b) can operate your web browser to complete tasks for you.
