<h1 align="center">🎯 YouTube Video Category Classification  
<br>(Phân loại video YouTube theo thể loại dựa trên mô tả video)</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10-blue?style=for-the-badge&logo=python" />
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge" />
  <img src="https://img.shields.io/badge/NLP-Vietnamese-yellow?style=for-the-badge" />
  <img src="https://img.shields.io/badge/TFIDF-Strong%20Baseline-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/PhoBERT-Embedding-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/E5-BGE%20Embedding-purple?style=for-the-badge" />
  <img src="https://img.shields.io/badge/SVM-RandomForest-blueviolet?style=for-the-badge" />
</p>

---

# 🧩 1. Introduction (Giới thiệu)

This project focuses on classifying **YouTube video categories** using only the **video description**.  
*(Dự án phân loại thể loại video YouTube dựa trên phần mô tả.)*

Motivations:

- YouTube descriptions contain rich semantic context  
- Video categories help improve recommendations & content moderation  
- Vietnamese YouTube data is noisy → needs strong preprocessing

Dataset:

- 10,000 raw videos  
- After cleaning: **6,750 valid Vietnamese descriptions** across 15 categories  
- Collected using **YouTube Data API v3**

---

# 🧼 2. Preprocessing (Tiền xử lý)

Steps applied:

1. Remove URLs, emojis, ads text, hashtags  
2. Language filtering using `langdetect` → keep only Vietnamese  
3. Tokenization using **Underthesea**  
4. Remove stopwords (global + per-category stopwords)  
5. Remove short descriptions (< 20 chars)  
6. Standardize text + lowercasing

Output:  

- `tokenized_text`  
- `category_id`

---

# 🧠 3. Text Representations (Biểu diễn văn bản)

We evaluate **5 embedding methods**:

### 🔹 1. TF-IDF  
*(Phương pháp thống kê tần suất – baseline mạnh nhất)*

### 🔹 2. PhoBERT  
*(Mô hình pre-trained cho tiếng Việt)*

### 🔹 3. BGE (BAAI General Embedding)  
*(Embedding tối ưu hóa semantic similarity)*

### 🔹 4. E5  
*(Instruction-based embedding – mạnh cho short text)*

### 🔹 5. Sup-SimCSE PhoBERT  
*(PhoBERT + supervised contrastive learning – embedding ngữ nghĩa tốt nhất)*

---

# 🤖 4. Machine Learning Models (Mô hình học máy)

We use 4 classifiers:

- **Logistic Regression**
- **Linear SVM**  
- **Random Forest**
- **Naive Bayes**

Due to high-dimensional embeddings, SVM works best for semantic vectors.

---

# 📊 5. Results & Comparison (Kết quả & So sánh)

## ⭐ **Best Overall Model**
### 👉 **TF-IDF + Random Forest**  
- **Accuracy = 0.744**  
- **Weighted F1 = 0.737**  
*(Mạnh nhất vì mô tả video ngắn, giàu từ khóa → TF-IDF hoạt động cực tốt.)*

---

# 🏆 6. Algorithm Comparison Table  
### *(Bảng so sánh thuật toán – đẹp & rõ ràng)*

| Embedding | Best Model | Accuracy | Macro F1 | Weighted F1 | Nhận xét |
|-----------|------------|----------|----------|--------------|----------|
| **TF-IDF** | 🎯 Random Forest | **0.744** | 0.588 | **0.737** | Mạnh nhất cho mô tả ngắn |
| **PhoBERT** | SVM | 0.624 | 0.545 | 0.620 | Tốt nhưng chưa fine-tune |
| **BGE** | SVM | 0.623 | 0.557 | 0.620 | Ngữ nghĩa khá tốt |
| **E5** | SVM | 0.640 | 0.585 | 0.638 | Hiểu ngữ cảnh tốt |
| **Sup-SimCSE PhoBERT** | ⭐ SVM | 0.647 | **0.561** | 0.646 | Embedding ngữ nghĩa mạnh nhất |

---

# 📈 7. Visualizations (Trực quan hoá)

Project includes:

- Confusion matrix for all embeddings  
- Performance bar charts  
- Cross-validation comparison  
- Error analysis across 15 categories  

---

# 📚 8. Key Findings (Phát hiện quan trọng)

### ✔ TF-IDF is still king for Vietnamese short descriptions  
### ✔ Sup-SimCSE PhoBERT gives best semantic understanding  
### ✔ Linear SVM generalizes best for semantic vectors  
### ✔ Random Forest exploits TF-IDF features effectively  
### ✔ Data imbalance strongly affects smaller classes  

---

# 🚀 9. Applications (Ứng dụng)

- YouTube content moderation  
- Category prediction for new videos  
- Improving recommendation pipelines  
- Vietnamese content analytics  
- Tagging & auto-labeling systems  

---

# 👨‍🏫 10. Team (Nhóm thực hiện)

- **Hà Thế Anh**  
- **Nguyễn Nhật Nam**  
- **Hoàng Quang Minh**  
**Supervisor:**  
- **Lê Nhật Tùng – HUTECH University**

---

---

# 🏁 12. Conclusion (Kết luận)

- TF-IDF remains the strongest baseline for short Vietnamese text  
- Semantic embeddings (E5, Sup-SimCSE) show promising performance  
- SVM is consistently stable across all vector spaces  
- Future improvements require **fine-tuning Vietnamese embeddings**

---

# 🔭 13. Future Work (Hướng phát triển)

- Fine-tune PhoBERT / E5 / SimCSE on YouTube dataset  
- Apply deep learning (BiLSTM, Transformer fine-tuned)  
- Use class-balancing techniques (SMOTE, focal loss)  
- Combine TF-IDF + embedding (hybrid representation)  

# 📎 11. Files in Repository (Các file trong repo)

