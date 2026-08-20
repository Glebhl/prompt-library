# Roadmap Builder

This prompt creates learning roadmaps for any subject.

It produces a sequential learning plan. You can then use this roadmap as the basis for self-study—for example, by asking ChatGPT, Claude, or another language model to explain each topic in turn.

## Usage

Open the prompt file and fill in the four fields at the beginning:

- `SUBJECT` — the subject or topic you want to study;
- `CURRENT_LEVEL` — your current level of knowledge;
- `GOAL` — your desired outcome;
- `COMMENTS` — any additional requirements or constraints.

It is recommended to specify the desired roadmap size and depth explicitly in `COMMENTS`. Vague descriptions such as "a quick course" or "deep understanding" can be interpreted inconsistently by the model. Prefer concrete structural requirements, for example:

- `1 level with 2–3 short chapters on theory, followed by 1 level with 1 chapter on practice`;
- `5 in-depth levels of C++, from beginner to Middle`.

The prompt has been tested with GPT-5.6 Sol and is recommended for use with OpenAI models. Run it without memory or use it in a temporary chat to increase output quality, because information the model knows about the user may lead to excessive personalization of the learning roadmap.

## Example Output

````text
Chapter 1.2: Values and Types

Lesson 1.2.1: The Type System

```text
├── Dynamic typing [B]
├── A type belongs to a value, not a variable [B]
├── Primitive types [B]
│   ├── undefined [B]
│   ├── null [B]
│   ├── boolean [B]
│   ├── number [B]
│   ├── bigint [A]
│   ├── string [B]
│   └── symbol [A]
├── Object type [B]
└── The typeof operator [B]
    ├── Results for primitives [B]
    ├── Result for functions [B]
    └── The typeof null quirk [B]
```
````
