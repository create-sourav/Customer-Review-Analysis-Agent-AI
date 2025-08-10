import pandas as pd

# Make pandas display full text without truncating
pd.set_option('display.max_colwidth', None)
pd.set_option('display.max_columns', None)
pd.set_option('display.width', None)

# Process all reviews into structured dicts
structured_reviews = [llmchain.invoke({"review": review}).model_dump() for review in reviews]

# Create DataFrame
df = pd.DataFrame(structured_reviews)

# Show DataFrame (like screenshot format)
display(df)
