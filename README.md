# Healthcare-Claim-classifcation

## Dataset
Pubhealth dataset is a comprehensive dataset for explainable automated fact-checking of public health claims. Each instance in the PUBHEALTH dataset has an associated veracity label (true, false, unproven, mixture). Furthermore each instance in the dataset has an explanation text field. The explanation is a justification for which the claim has been assigned a particular veracity label.

Link to the dataset - https://huggingface.co/datasets/health_fact

## Task
The task here is implement a text classification model to classify the healthcare claims into the above mention four classes.
The entire solution has been developed on the free Cloud GPU instances of Google Colab
* ### Approach A -  Using the RoBERTa model for text classification


    *  In this part, I will be using the sequence classification model from hugging face for RoBERTa to classify the medical claims
    *   The model will be finetuned on the training dataset comprising of 9k samples

* ### Approach B -  Using the embeddings of the model for training an unsupervised learning algortihm (KNN)

  *   In the previous approach, I observed that the majority of the test samples were having tokens > 512 (maximum number of tokens the model can work with) 
  *   In the previous approach, the extra tokens were discarded, whcih was loss of crucial information.
  *  So, to overcome that, this apporach is used
  * In this approach, the extra tokens are passed to the model as sections comprising of 512 tokens, to obtain the embeddings
  * once the embeddings was obtained, for a large text the, there were mmore than one embedding vectors.
  * to overcome that, the average of all these vectors was taken to obtain a single embedding.
  * these vectors are then used by the K-Nearest neighbor model to obtain train and predict the outputs of the unknown (test data).  
  * A key point to note here is that the model that has been used for this section, has not been finetuned on the dataset.

##update: 
For the apporach B, where a KNN model was used on top of RoBERTa embeddings, earlier the model was not fine tuned on the dataset, it the recent update, I have used the model that was finetuned on the dataset in the approach A for the approach B and have been abale to acheive better results. These are present in the results folder.
