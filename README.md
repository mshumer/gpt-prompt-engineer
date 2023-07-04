# gpt-prompt-engineer
[![Twitter Follow](https://img.shields.io/twitter/follow/mattshumer_?style=social)](https://twitter.com/mattshumer_)

## Overview

Prompt engineering is kind of like alchemy. There's no clear way to predict what will work best. It's all about experimenting until you find the right prompt. `gpt-prompt-engineer` is a tool that takes this experimentation to a whole new level.

**Simply input a description of your task and some test cases, and the system will generate, test, and rank a multitude of prompts to find the ones that perform the best.**

## Features

- **Prompt Generation**: Using GPT-4 and GPT-3.5-Turbo, `gpt-prompt-engineer` can generate a plethora of prompts based on a provided use-case and test cases.

- **Prompt Testing**: The real magic happens after the generation. The system tests each prompt against all the test cases, comparing their performance and ranking them using an ELO rating system.

- **ELO Rating System**: Each prompt starts with an ELO rating of 1200. As they compete against each other in generating responses to the test cases, their ELO ratings change based on their performance. This way, you can easily see which prompts are the most effective.

## Setup
1. Open this colab LINK LINK.

2. Add your OpenAI API key to the line `openai.api_key = "ADD YOUR KEY HERE"`.

3. If you have GPT-4 access, you're ready to move on. If not, change `model='gpt-4'` inside `generate_candidate_prompts` to `model='gpt-3.5-turbo'`.

## How to Use

1. Define your use-case and test cases. The use-case is a description of what you want the AI to do. Test cases are specific prompts that you would like the AI to respond to.

2. Choose how many prompts to generate. Keep in mind, this can get expensive if you generate many prompts. 10 is a good starting point.

3. Call `generate_candidate_prompts(description, test_cases, number_of_prompts)` to generate a list of potential prompts.

4. Pass the generated prompts to `test_candidate_prompts(test_cases, description, prompts)` to test and rate their performance.

5. The final ELO ratings will be printed in a table, sorted in descending order. The higher the rating, the better the prompt.

## Conclusion

With `gpt-prompt-engineer`, your search for the best possible prompt becomes a structured and efficient process. It's an experimentation tool that brings a method to the madness, a compass in the uncharted territory of prompt engineering. Happy experimenting!
