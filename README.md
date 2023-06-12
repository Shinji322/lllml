# LLLMML (Temp Name)

This is meant to be a markup language for interacting with LLM models, similar to [Hero ML](https://github.com/hero-page/hero-ml). This is written from the ground up with simplicity, minimalism, and power usage in mind.

Core features currently include:
* Variables!
    * These can be from a user supplied dictionary or special variables like: `$1`
* Control flow!


Included in this repo is a python library for compiling this script and using it with your own programs. Here is a simple example script:


```
# You can write comments like this! All blank lines are ignored.
> Create a fictional title for the $MOVIE_ADJECTIVE movie ever! This should not be a real movie; only supply me with the title.

> Write a comprehensive anlaysis of $1, discussing the following details: $ANALYSIS_DETAILS. Make sure to sound as pedantic as possible.

! if 'masterpiece' in $2
> Someone approaches you and says $1 is the worst movie ever made. How do you respond?
! elif 'worst' in $2  # regex supported here!
> Some subhuman piece of garbage online actually thinks that $1 is the best movie made. How do you respond?
! else
> Someone has different thoughts about $1 compared to you. What do you respond with?
```

The script could be called like so:

```py
compile(llmml, llm_call, {
    "MOVIE_ADJECTIVE": "worst",
    "ANALYSIS_DETAILS": ["themes", "characters", "music"]
})
```

* `lmmml` is a `lmmml` object
    * Don't worry; this function just requires a string from the file to be constructed
* `llm_call` is a `Callable` that returns a string from your LLM
* The dictionary at the end is used for other variables.


# Optional TODO:

* [ ] Implement other cooler control flow
    * Again, may or may not be necessary but it might be cool
