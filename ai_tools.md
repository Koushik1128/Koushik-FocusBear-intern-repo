# AI Tools for Development

## Which AI tools did I try?

I tried two: **GitHub Copilot** (inline suggestions + Copilot Chat in VS Code) and **Claude** (conversational, used directly in chat). I picked these two because Copilot is the standard "in editor" assistant and Claude is what I already reach for when I need something explained properly, so it made sense to compare them side by side rather than install a third tool just to tick a box.

## What worked well? What didn't?

**Generating code snippets**

I asked both tools for the same thing: a function to remove duplicate rows and fill missing values with the column mean.

Copilot's version was short and looked right at a glance:

``` python
def clean_data(df):
    df = df.drop_duplicates()
    for col in df.columns:
        if df[col].isnull().sum() > 0:
            df[col] = df[col].fillna(df[col].mean())
    return df
```

Claude's version did the same thing but restricted the mean filling to numeric columns only, and added a doc string.

I actually ran both against a test Data Frame with a text column that had a missing value, and Copilot's version crashed with `Cannot perform reduction 'mean' with string dtype`. Claude's didn't, because it filtered to numeric columns first. That was a good reminder that Copilot's suggestions look clean but are written for the "happy path": they don't automatically account for edge cases unless the prompt is more specific. It's fast, but you still need to test it, not just accept it on sight.

**Debugging**

I wrote a deliberately broken `average()` function that throws a `ZeroDivisionError` when given an empty list, and asked Copilot Chat to explain and fix it.

Copilot didn't just patch the bug, it rewrote the function to raise a `ValueError` with a clear message if the list is empty, and wrapped the call in a `try/except` to show how to handle it. That's arguably better practice than the quick fix I had in mind (just returning `0` for an empty list), since silently returning 0 could hide a real bug further down the line. This was the point where the AI's suggestion was genuinely better than my first instinct, not just a different way of doing the same thing.

**Explaining a new concept**

I asked both for a basic intro to big data, since I'm covering it in Big Data Processing this semester.

Claude gave more of a narrative and explained *why* big data needs distributed storage and computation in the first place, and walked through the difference between MapReduce and Spark. Copilot's answer was more like a dense reference list: volume/velocity/variety, then a rundown of tools (HDFS, Spark, Kafka, cloud platforms) and related skills, without explaining how any of them actually differ from each other.

Neither answer was wrong, but they suit different situations. Claude's was better for actually learning the concept from scratch. Copilot's was better as a quick refresher once you already understand the basics and just want the vocabulary.

## When do I think AI is most useful for coding?

Based on this, I'd say:

**Inline tools like Copilot** are most useful for boilerplate and repetitive code where you already know what "correct" looks like and just want to save typing, but you still need to actually check the output, because it optimists for the common case and can miss edge cases.

**Conversational tools like Claude** are more useful when you need to actually understand *why* something works, are debugging something tricky, or are learning a new concept. The back and forth and the reasoning behind the answer matters more than speed there.

In practice they complement each other rather than replacing one another: Copilot in the editor for the moment to moment coding, and a conversational assistant on the side for anything that needs real thinking through.

The main thing I took away is that AI generated code isn't automatically correct just because it runs. The duplicate removal function was a clear example of that. Testing edge cases still matters, AI or not.
