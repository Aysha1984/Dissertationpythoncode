Autoencoders pre-trained unsupervised initialized the network weights before fine-tuning them for classification tasks. The model effectively reduced noise in PET scans, creating cleaner, more interpretable images. Visualizing the latent space provided insights into the model’s ability to capture and differentiate features related to Alzheimer's stages.

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
We created dynamic architectures for the encoder and decoder with consistent configurations, then combined them to form the autoencoder. The encoder compresses the input data into a lower-dimensional latent space, preserving critical features while reducing noise. The decoder reconstructs the input from the latent space, allowing the model to learn representative patterns in the data.
Training and Validation
The model was trained and validated over multiple epochs. For each epoch, we performed:
1.	Training: The autoencoder learned representations by minimizing reconstruction loss using the AdamW optimizer and the Mean Squared Error (MSE) loss function.
2.	Validation: The model's performance was evaluated on unseen data to track generalization.
The training process aimed to map the input data to a meaningful latent space, reducing dimensionality while retaining key features.
Latent Space and Visualization
The latent space represents a compact, lower-dimensional encoding of the input data. Once training was complete, we used the latent space to create scatter plots that visualized the data distributions for different Alzheimer's stages. This analysis helped us assess whether the encoder effectively separated distinct categories in the latent space by making clusters. 

Hyperparameter Tuning
Various hyperparameters within the encoder and decoder were fine-tuned to improve the model's classification accuracy. This process enhanced the autoencoder's ability to distinguish between different stages of Alzheimer's disease.
Objectives
1	Develop autoencoders for Alzheimer's disease PET brain image dimensionality reduction. 
  2      Develop a classification algorithm leveraging low-dimensional Alzheimer diocese PET data.  


