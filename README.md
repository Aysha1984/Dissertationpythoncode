AI-BASED ANALYSIS OF MEDICAL IMAGING DATA FOR EARLY DETECTION OF ALZHEIMER’S DISEASE

Problem Statement
How Artificial Intelligence (AI) can help classify early stages of Alzheimer’s by using the PET Medical Imaging dataset? 
   Objectives
1	Develop autoencoders for Alzheimer's disease PET brain image dimensionality reduction. 
  2      Develop a classification algorithm leveraging low-dimensional Alzheimer diocese PET data.  
   Use of Autoencoders
We can use several techniques to classify the early stages of Alzheimer’s such as transformers and Graph Neural Networks including autoencoders and PCA. 
We used Unsupervised Autoencoders and CNN because PET imaging medical data is high dimensional and autoencoder reduces the dimensionality reduction by encoding the PET data into a compressed latent space. It helps us to see the subtle patterns and changes in the brain and remove the noise from PET images. This helps improve the accuracy of diagnoses and provides valuable insights into early detection and progression to classify Alzheimer's stages.
Dataset and Preprocessing
We used a dataset of 250 NIfTI (nii) files categorized into five groups:
•	AD (Alzheimer's Disease),
•	CN (Cognitively Normal),
•	MCI (Mild Cognitive Impairment),
•	EMCI (Early Mild Cognitive Impairment),
•	LMCI (Late Mild Cognitive Impairment).

Each category contains 50 files, each corresponding to a different patient. Each NIfTI file consists of 91 PET brain slices per patient. Images with 30% or more black pixels were filtered out, as they were deemed uninformative. All NIfTI files were converted to png format for easier compatibility with the autoencoder model.
We resized the images to 128*128 pixels, converted them into tensors, and normalized the pixel values. The images were then classified into one of the five categories (AD, CN, MCI, EMCI, and LMCI) and split into training and validation datasets using an 80/20 ratio.

Model Architecture
We created model architectures for the encoder and decoder with consistent configurations, then combined them to form the autoencoder. The encoder compresses the input data into a lower-dimensional latent space, preserving critical features while reducing noise. The decoder reconstructs the input from the latent space, allowing the model to learn representative patterns in the data.
Training and Validation
The model was trained and validated over multiple epochs. For each epoch, we performed:
1.	Training: The autoencoder learned representations by minimizing reconstruction loss using the AdamW optimizer and the Mean Squared Error (MSE) loss function.
2.	Validation: The model's performance was evaluated on unseen data to track generalization.
The training aimed to map the input data to a meaningful latent space, reducing dimensionality while retaining key features.
Latent Space and Visualization
The latent space represents a compact, lower-dimensional encoding of the input data. Once training was complete, we used the latent space to create scatter plots that visualized the data distributions for different Alzheimer's stages. This analysis helped us assess whether the encoder effectively separated distinct categories in the latent space by making clusters or not.
                 

Hyperparameter Tuning
Various hyperparameters within the encoder and decoder were fine-tuned to improve the model's classification accuracy. This process helps the autoencoder's ability to distinguish between different stages of Alzheimer's disease. These hyperparameters are significant because they define the model's ability to learn from and generalise the data. The learning rate defines the speed of updating weights that the model follows during training. 


Evaluation
The clustering of the data did not produce the level of separation required to classify AD across its various stages and we could only manage to classify AD and CN. In the latent space, data was overlapping clusters, making it harder to classify stages. 
However, the remaining three categories, Mild Cognitive Impairment (MCI), Early Mild Cognitive Impairment (EMCI), and Late Mild Cognitive Impairment (LMCI) could not be effectively segregated during the experiments. To address this, it would be necessary to redesign the autoencoder to classify all five stages of AD, or also change the structure of CNN by adding extra layers or fine-tuning the hyperparameter. Alternatively, we can also explore the use of transformers instead of autoencoders as a model. Transformers may offer a better approach to the PET imaging dataset. 

Reasons
1-	Data-Related Issues
            This may be due to the small medical imaging dataset and the inability to characterise Alzheimer’s stages.
2-	Autoencoder Architecture
            The autoencoder architecture may not be sufficiently complex to capture the subtle, non-linear patterns
3-	Cluster Overlap
            Due to cluster overlapping, High-dimensional data often results in overlapping clusters, making it harder to classify stages of Alzheimer. 

