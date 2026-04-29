GPT-2 SMS Spam Classifier:

This project demonstrates how to fine-tune the GPT-2 (small) language model to perform text classification. Specifically, it focuses on identifying spam messages from the SMS Spam Collection v.1 dataset.

📌 Project OverviewWhile GPT-2 is originally designed as an auto-complete (causal) language model, this project adds a custom classification head (a linear layer) to adapt it for sentiment analysis and spam detection.

📊 Dataset

Name: SMS Spam Collection v.1

Size: 5,574 English messages

Distribution: 90% Training / 10% Validation

Source: UCI Machine Learning Repository / Hugging Face

🛠️ Technical Workflow

1. Tokenization: Using the GPT2Tokenizer to convert raw text into sequences of input IDs.

2. Custom Model Architecture: * Loads the base GPT2Model.

Extracts the hidden state of the last token in the sequence (a critical trick for causal models like GPT-2).

Passes this state through a new nn.Linear layer with 2 output features (Spam/Not Spam).

3. Partial Fine-Tuning: To save resources, only the last attention block and the custom output layer are trained; the rest of the model parameters are frozen.

4. Training: Optimized using AdamW with a learning rate of 5e-5 over 2 epochs.

🚀 Results

The model achieves high accuracy in classifying real-world messages, as seen in the prediction samples:

"Last a chance to win 1 Lakh, call at 5676 now!" --> Spam

"How are you doing?" --> Not Spam
