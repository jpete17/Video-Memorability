# Video-Memorability
Predicting long-term and short-term memorability scores for videos - MediaEval Dataset

This paper describes the 3 different approaches adopted to predict the long-term and short-term video memorability scores for the given videos. This predictability task is based on three propositions: Gestalt’s principle on Visual Memory, Frames with Human/object motion, and by analyzing the impact of sentimental analysis on captions using NLTK VADER. Ensemble techniques, XGBoost and Random Forest, and Artificial Neural Network - Multi-layer Perceptron were used to predict video memorability scores.

1.	*It has been studied that, emotional content is an influential factor in cognitive processing which includes perception, memory, and attention.*
2.	*Secondly, humans have shown a tendency to better memorize videos with human or object motion than a static image.* 
3.	*Furthermore, this paper has extended a segment of work [5] on gestalt’s principle in predicting video memorability Dublin University as four Gestalt’s principles: similarity, connectedness, proximity, and common region are reported to have a significant bearing on Visual Working Memory.*


3.	**APPROACH**

3.1	**Sentiment Analysis of Caption**

To implement the first proposition, Stanford’s Natural Language Toolkit (NLTK) VADER is used to perform sentiment analysis on the captions. To reduce the morphological variation, each token was lemmatized and further cleaned and only the compound feature was used, which is an overall descriptor of the sentiment analyzer, while the positive, negative, and neutral descriptors were removed due to high multicollinearity. Three models were run with the VADER descriptor.

•	MLP with One hot encoded caption – captions were tokenized and padded 
•	MLP with TF-IDF of captions to find the importance of keywords
•	An embedded Neural Network with Word embeddings – A vector representation using Global Vectors (GloVe) 

MLP architecture is designed with 3 layers, with Rectified Linear Unit (ReLu) as the activation function which overcomes the vanishing gradient drawback in sigmoid. L2 Regularization, Ridge Regression, is applied to the activation function on the input and hidden layers to reduce overfitting of the training data. Adamax (Adaptive Movement Estimation) is used as data is encoded and sparse in nature. 

3.2	**Predicting with living presence or motion**

High-level features such as Histogram of Moving Pattern’s and C3D were used as it reveals key information on moving objects and object detection. Ensemble learning techniques such as Random Forest Regressor with Decision Trees and XGBoost is used to predict both the short-term and long-term memorability. A test was performed with C3D and HMP’s of the middle frame independently and then a combined test was performed to evaluate the second proposition. Due to the high dimensionality of HMP, PCA was performed to reduce the dimensions. Finally, a grid search was performed to fine-tune the parameters. 

3.3	**Applying Gestalt’s Principle – Aesthetics and Color Histogram.**

By extending the work done by Dublin University [5], gestalt’s principle is applied by using Aesthetics and Color Histogram independently and as a combination. Aesthetics features were normalized and like the previous step, Ensemble learning – Random Forest and XGBoost are preferred. A grid search was performed to find the best parameters.




