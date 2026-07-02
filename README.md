# SDAB Group 9: Bot vs Human Classification Model

**Lab Group:** SDAB GROUP 9  
**Group Members:** Chan Chun Mun Aloycius, Aw Hongkai, Koh Tat Yao

---

##  Problem Statement
How can we use behavioural sequences and account metadata to develop a classification model that can better distinguish automated bots from human users?

##  Project Goal & Hypothesis
Automated bots on social media platforms have become increasingly sophisticated, blurring the lines between human and machine-generated content. This poses a significant threat to digital integrity by imitating human behavior and spreading misinformation. 

The aim of this project is to create a robust classification model capable of telling apart humans from bot accounts by analyzing various user behavior data and account metadata (digital footprints). The findings aim to produce an effective model capable of detecting bots across multiple platforms to safeguard online communities, with applications extending to E-commerce, cybersecurity, and financial services.

##  Data Sources
The project utilizes multi-source datasets representing different social media platforms:
1. **Dead Internet Theory Reddit Bot vs Human Dataset**: Provides a snapshot of Reddit comment activity, analyzing metadata like account age, user karma, reply delay, and word length.
2. **Twitter Human Bots Dataset**: Contains profile metadata for roughly 37,000 accounts to establish a baseline between automated and real account characteristics.
3. **Bots vs Users Dataset**: Includes detailed profile metadata and behavioral metrics (e.g., *avg_likes*, *completeness_score*) for 5,874 accounts from a Russian social media platform (VK).
4. **Twitter Analysis Dataset**: Contains 134,198 Twitter records with a mix of linguistic features, account metadata, and engagement statistics.

##  Methodology
* **Data Exploration & Cleaning**: Addressed data sparsity, handled zero-variance/high-cardinality columns, and engineered new features (e.g., `completeness_score` and `has_behavioral_data` to handle privacy-induced data gaps).
* **Statistical Analysis**: Validated features using Chi-Square Tests of Independence and Mann-Whitney U tests (e.g., confirming the lack of behavioral metrics is a strong indicator of automation).
* **Data Augmentation**: Applied Synthetic Minority Over-Sampling Technique (SMOTE) to address class imbalances without duplicating existing accounts.
* **Modeling**: Built a **Soft Voting Ensemble** combining the predictive power of three distinct **Random Forest Classifiers** trained on unique datasets to capture complex, non-linear boundaries across platforms.

##  Key Findings
* **Reply Delay**: Bots tend to respond significantly faster than humans (e.g., median of 6 seconds vs. ~29 minutes on Reddit).
* **Verbosity & Links**: Bots are consistently more verbose and are significantly more likely to include external links in their posts.
* **Engagement Metrics**: Low engagement (especially likes) acts as a robust universal signal of automation across platforms.
* **The "Minimalist Bot" Pattern**: Automated accounts typically fill out only a scripted, bare-minimum set of profile fields.
