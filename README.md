# AMUSED Dataset

**AMUSED** (A Multilingual Urdu/English Stance and Fake News Detection Corpus) is a multi-platform, multilingual dataset designed for **stance detection** and **fake news detection**.  
It contains **Urdu and English** content from Facebook, Instagram, and Twitter, collected around real-world events.

This dataset includes:

- **12** recent multi-domain events  
- **66** claims  
- **468** source posts  
- **36,940** comments  

It is labeled for stance detection (`agree`, `disagree`, `comment`, `query`) and fake news detection, and includes **social context**, **user profiling**, and **news content features**.

---

## 📂 Dataset Structure

### 1. Original Folder-Based Structure

```
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
```

- **`claims.xlsx`** → List of event-specific claims (Urdu & English)  
- **Facebook/Instagram/Twitter folders** → Platform-specific posts & comments  

---

### 2. Consolidated CSV/Excel Version

For easier use, a **single consolidated file** is provided with **4 sheets**:

| Sheet Name        | Description |
|-------------------|-------------|
| **claims**        | All claims with text, language, labels, metadata, and unique IDs |
| **posts**         | Post content, platform info, labels, and associated claim IDs |
| **comments**      | Comment content, metadata, and associated post IDs |
| **user_features** | Account-level features of users (followers, engagement metrics, etc.) |

---

## 🔗 Data Relationships

```
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
```

- **claims → posts**: Each post links to a claim via `claim_id`  
- **posts → comments**: Each comment links to a post via `post_id`  
- **posts → user_features**: Each post’s author links to user features via `user_id`  

---

## 📊 Example Use Cases

- **Stance Detection** — Classify posts/comments as supporting, opposing, neutral, or questioning a claim  
- **Fake News Detection** — Identify misinformation across platforms  
- **Cross-Language Analysis** — Compare Urdu vs English patterns  
- **Cross-Platform Spread** — Study claim diffusion on Facebook, Instagram, and Twitter  

---

## 💻 Loading the Dataset in Python

```python
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
```

---

## 📜 Citation

If you use the AMUSED dataset in your research, please cite:

```
@inproceedings{safdar2025amused,
  title={AMUSED: A Multilingual Urdu/English Stance and Fake News Detection Corpus},
  author={Safdar, Sehrash and Wasim, Muhammad and Rehman, Abdur and Ghani, Muhammad Usman},
  booktitle={2025 International Conference on Emerging Technologies in Electronics, Computing, and Communication (ICETECC)},
  pages={1--6},
  year={2025},
  organization={IEEE}
}

