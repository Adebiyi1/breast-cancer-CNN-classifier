# breast-cancer-CNN-classifier
For this project, I tackled the challenge of binary classification for histopathology images, aiming to distinguish between cancerous and non-cancerous tissue. The core problem was getting the model to perform well on new, unseen images without just memorizing the training data—a classic overfitting issue, especially with a limited medical image dataset.

### My Approach 🔬

To overcome this, I built a comprehensive training pipeline focused on generalization:

* Preprocessing: I started by standardizing everything. This involved fixing inconsistencies in the labels and normalizing pixel values to a 0-1 range to ensure the model could learn effectively.
* Data Augmentation: To make the most of my small dataset, I used data augmentation. By randomly flipping, rotating, and zooming the images, I effectively expanded the training set and made the model more robust to variations.
* Model Tuning: I designed a custom CNN architecture and added **Dropout** layers, which randomly "turn off" neurons during training to prevent the model from becoming too reliant on specific features. I also used the **Adam optimizer** with a scheduled learning rate and implemented **early stopping** to halt training once the validation performance stopped improving, a direct defense against overfitting.
* Balancing Classes: I noticed an imbalance in the number of cancerous and non-cancerous samples, so I used **class weighting** to ensure the model paid equal attention to both types, preventing it from just predicting the majority class.


### The Outcome 📊

Despite all these strategies, the results were a bit disappointing:

* Training Accuracy: The model performed fairly well on the data it had seen, reaching around **70%**.
* Validation Accuracy: However, its performance on new, unseen data quickly plateaued at **60-62%**.

My main takeaway from this was a clear case of overfitting. Increasing the model's complexity improved its training performance but made the validation accuracy worse, a textbook sign that it was memorizing the training data instead of learning general patterns.


### Key Takeaways ⚠️

* Dataset Size is Everything: My biggest insight is that even with robust augmentation, a small dataset is a significant bottleneck. It limits the ability of a CNN to learn truly meaningful and generalizable features.
* Overfitting is a Tough Problem: It’s a persistent challenge in this domain. The model consistently failed to generalize beyond the training set.
* Need for Transfer Learning: My results strongly suggest that a traditional CNN from scratch isn't enough for this task. The way forward is likely **transfer learning**—using a large pre-trained network like MobileNetV2, ResNet50, or EfficientNet. These models have already learned robust feature representations from massive datasets, which can then be fine-tuned for a specific task like histopathology image classification. 
