# How to Do Good Research

**TRADUZIDO COM AI, DESCULPA SE TIVER UM ERRO!**

![banner.png.png](Como%20fazer%20uma%20boa%20Research/banner.png.png)

# **Summary**

Ignoring the **obvious** name, this blogpost is not tips that will help you “exploit” a bug or give you tips on how to find awesome bugs, it is obvious that you need technical knowledge. However, in this blogpost I will detail my experience doing research, without much preparation. And how I stayed focused and kept hope even when everything went wrong.

Recently I decided to focus on understanding not only technical fundamentals, but also the “mindset” (sorry for using this word hehehehe) of people who do research and are able to find vulnerabilities in widely used software. And I decided to spend a few months studying and improving this skill, from AI assistance to how to stay focused during research.

![researchmeme.png](Como%20fazer%20uma%20boa%20Research/researchmeme.png)

# What is doing Research after all?

In this context, it is necessary to understand that doing Research is not a linear process, it is a slow and totally orthogonal process, you can go back one **step**, move **forward**, give up, **come back** another day. For the sake of example, look at the image below

![MAIS.png](Como%20fazer%20uma%20boa%20Research/MAIS.png)

You will not always find the bug on your first day, sometimes it takes months, sometimes even years. But of course, the important thing is not to give up and stay focused!

# Choosing the Target!

So let's start.... Obviously you need a target to begin doing research, whether harder ones like a browser or even something simpler like a gameboy emulator. Just pick something you would like to research and start.  **But after all, how do I know if I really want to do research on this target?**

- Questions you should ask yourself....
    - Do I like this target?
    - Do I know this target well enough?
    - Do I have motivation and discipline to stay months on this target?

If at least 2 of these answers are **“YES”,** you have a good target that you can look at. But of course depending on the difficulty it will be much more work... But of course it is never **“impossible”**

# Choosing an attack-surface!

Imagine your target not as a final application, but as a set of several subcomponents, and this is (maybe) the most important part of research, because if you choose a good attack surface you **move one house forward**, a bad one makes you lose days or even months on a **bad target (wasting time).** This is a slow and lengthy process, it should not be fast. What I like to do is map all good attack surfaces, but it is important to evaluate all your options before anything else, and besides that: a good attack surface is something that meets these requirements:

- Poorly audited
- Complex
- Has a lot of new code or code that changed recently
- Handles user input in some way (parsing, deserialization, etc)
- Has a history of previous bugs (where there was 1 bug there are probably more)

Think like this: if a component has already been audited by 500 people and had 200 CVEs in recent years, **maybe** the easiest bugs are already gone. But if you find a corner of the code that nobody looked at properly, that is complex and processes external data... then yes you have **gold**.

# Understanding the code

Alright, you already chose your target and your attack surface. Now comes the part many people skip (and should not): **understanding the code for real**. I am not talking about reading superficially and thinking you understood it. I am talking about sitting down, opening the source code, and understanding the **flow** of data from input to where it is processed.

I know it sounds boring (and sometimes it is hehehe), but this step is what separates people who find bugs from people who only keep trying. Some things I do at this stage:

- I read the project **documentation** (yes, documentation matters)
- I identify the main **entry points** (where user data enters)
- I trace the data path through the code, writing down each transformation
- I look for **dangerous patterns**: type conversions, manual memory allocations, custom parsing, bounds-checking logic
- I write down **everything** that looks weird, even if I do not understand it at the time

You do not need to understand 100% of the code on the first day. In reality, you probably **will not** understand. And that is okay. Understanding comes with time, and every time you come back to the code you see things that previously went unnoticed.

One thing that helped me **a lot** was using code navigation tools like **Source Insight**, **Ghidra**, or even good old **grep**. Having the ability to jump between functions and references quickly makes an absurd difference when you are trying to understand a big codebase.

# Taking notes (this is ESSENTIAL)

I cannot emphasize this enough: **TAKE NOTES**. About everything. Literally everything. Every crazy idea you had, every weird function you saw, every hypothesis you want to test later. Write it down.

Why? Because research is long. You will sleep, wake up the next day and **forget** that brilliant idea you had at 3 AM. Or you will come back after a week and not remember why you marked that function as suspicious.

I personally use a mix of **Notion** and **notes in the code itself** (comments). But use whatever works for you, it can be a txt file, a physical notebook, whatever. The important thing is that it is **recorded**.

The format I like to use in my notes:

- **What I looked at today**: brief summary of what I analyzed
- **Suspicious things**: functions, patterns, strange behaviors
- **Hypotheses**: what I think can bug and why
- **Next steps**: what I want to look at tomorrow

This sounds silly but it makes a **huge** difference in research continuity. You do not lose context between days and you can maintain steady progress.

# Dealing with frustration

This is the elephant in the room that nobody talks about. Doing research is **frustrating**. There are days when you will spend 8 hours looking at code and find **nothing**. There are weeks when you think you are on the right path and discover that the "bug" you found is not exploitable. There are months when you simply find nothing.

And you know what? **This is normal**. It is part of the process. The best researchers in the world go through this too, the difference is that they **do not give up**.

Some things that help me deal with frustration:

- **Remember that every hour of research makes you better**, even if you find nothing. You are learning the codebase, training your eye, accumulating knowledge.
- **Talk to other people** who do research. Exchanging ideas with someone who understands the pain makes a big difference.
- **Take breaks**. Seriously. Sometimes the best thing you can do for your research is close the computer and go do something else. Many times the solution comes when you are **not** actively thinking about the problem.
- **Celebrate small wins**. Understood a complex function? Win. Mapped a new entry point? Win. It does not need to be a CVE to count as progress.

# Using AI as assistance

Yes, I use AI in research and I am not ashamed to say it. But it is important to understand **how** to use it. AI will not find the bug for you (at least not yet hehehe), but it can help you with several things:

- **Understanding complex code**: throw in a code snippet and ask it to explain what it does
- **Brainstorming attack vectors**: "given this component that does X, what possible attack vectors could there be?"
- **Automating repetitive tasks**: fuzzing scripts, log parsers, etc
- **Rubber duck debugging**: sometimes just by explaining the problem to AI you already notice the answer

But be careful: **do not blindly trust** what AI tells you. It can be wrong, it can hallucinate, it can give you a false sense of security. Always **validate** what it tells you against the real code.

With this I hope you can find some bugs hehehe
