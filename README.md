# Auto-Tagging-Support-Tickets-Using-LLM
##Problem Statement
Automatically classify customer support tickets into predefined categories (e.g., Billing inquiry, Technical issue) using zero-shot, fine-tuned, and few-shot learning with transformer-based models.


##Dataset:  Free-text Support Ticket Dataset
labels:
- Billing inquiry  
- Cancellation request  
- Product inquiry  
- Refund request  
- Technical issue  


##Approaches Used

###1. **Zero-Shot Learning**
- Used a pre-trained transformer model (e.g., 'facebook/bart-large-mnli')  
- No training required  
- Model predicts ticket labels based on semantic similarity  
- Output: Top label prediction with confidence score  

###2. **Fine-Tuned Model**
- Fine-tuned a 'bert-base-uncased' model on the labeled dataset  
- Trained on full data for 3 epochs  
- Achieved **accuracy ≈ 19.6%**, with balanced precision/recall across labels  

###3. **Few-Shot Learning**
- Trained 'bert-base-uncased' on a small subset of the dataset (5% per class)  
- Slight performance improvement over zero-shot  
- Accuracy ≈ **19.66%**, showing potential in low-data environments  


##Results Summary

| Method       | Accuracy | Key Notes                                   |
|--------------|----------|----------------------------------------------|
| Zero-Shot    | ~19%     | Fastest, no training, but weakest accuracy   |
| Fine-Tuned   | ~19.6%   | Best performance overall                     |
| Few-Shot     | ~19.66%  | Slightly better than zero-shot, low-resource|

- All models suffer from class imbalance  
- Adding top-3 predictions helps mitigate low confidence  


##Top-3 Prediction Mode
Each model can output the **Top 3 most probable tags** per ticket with their confidence scores — useful for manual review or soft classification.


