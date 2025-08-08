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

#📂 Dataset Structure
#1. Original Folder-Based Structure
AMUSED/
│
├── Events/
│   ├── Event_1/
│   │   ├── claims.xlsx
│   │   ├── Facebook/
│   │   │   ├── posts.xlsx
│   │   │   ├── comments.xlsx
│   │   ├── Instagram/
│   │   │   ├── posts.xlsx
│   │   │   ├── comments.xlsx
│   │   ├── Twitter/
│   │       ├── posts.xlsx
│   │       ├── comments.xlsx
│   │
│   ├── Event_2/
│   │   ├── ...
│   │
│   └── ...

#2. Consolidated CSV/Excel Version
For easier use, the dataset is also provided in a single file with 4 sheets:
| Sheet Name         | Description                                                                                            |
| ------------------ | ------------------------------------------------------------------------------------------------------ |
| **claims**         | Contains all claims, their text, metadata, and unique IDs.                                             |
| **posts**          | Contains post content, platform information, and associated claim IDs.                                 |
| **comments**       | Contains comment content, metadata, and associated post IDs.                                           |
| **user\_features** | Contains account-level features of users who authored the posts (followers, engagement metrics, etc.). |

#Data relationships
[ Claim ]
   ↑
   │ claim_id
   │
[ Post ]
   ↑
   │ post_id
   │
[ Comment ]
   ↑
   │ user_id
   │
[ User Features ]
#💻 Loading the Dataset in Python
import pandas as pd

# Path to the consolidated version
dataset_path = "AMUSED_consolidated.xlsx"

# Load sheets
claims = pd.read_excel(dataset_path, sheet_name="claims")
posts = pd.read_excel(dataset_path, sheet_name="posts")
comments = pd.read_excel(dataset_path, sheet_name="comments")
user_features = pd.read_excel(dataset_path, sheet_name="user_features")

# Example: Get all posts for a claim
claim_id = 1
related_posts = posts[posts["claim_id"] == claim_id]

# Example: Get all comments for a post
post_id = related_posts.iloc[0]["post_id"]
related_comments = comments[comments["post_id"] == post_id]

print(related_posts.head())
print(related_comments.head())
#If you use the AMUSED dataset in your research, please cite:
@inproceedings{safdar2025amused,
  title={AMUSED: A Multilingual Urdu/English Stance and Fake News Detection Corpus},
  author={Safdar, Sehrash and Wasim, Muhammad and Rehman, Abdur and Ghani, Muhammad Usman},
  booktitle={2025 International Conference on Emerging Technologies in Electronics, Computing, and Communication (ICETECC)},
  pages={1--6},
  year={2025},
  organization={IEEE}
}



