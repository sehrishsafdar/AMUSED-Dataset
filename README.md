# AMUSED-Dataset
This is the official repository of "AMUSED: A Multilingual Urdu English Stance and Fake News Detection Corpus"
# Dataset Description
AMUSED is a dataset designed for stance detection, focusing on multilingual comments related to news articles. It contains user comments with stance labels such as `agree`, `disagree`, `comment`, and `query`.
This dataset
contains information on 12 recent multi-domain events, 66 claims,
468 source posts, and 36,940 comments. The dataset is labeled
for stance detection and fake news detection. It includes all
relevant social context, user profiling, and news content features,
associated with the source posts.

- **Format:** CSV
- **Languages Covered:** Multiple languages.
# Usage
Use this Dataset only for research purposes.

## Usage
To load the dataset in Python:
```python
import pandas as pd

df = pd.read_csv("AMUSEDfinall.csv")
print(df.head())



