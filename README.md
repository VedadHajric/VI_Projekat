# VI_Projekat
Project for the Artificial Intelligence course, ETF Sarajevo, 'Medical Image Deblurring'

Project: Medical Image Deblurring 

1. Project Overview
  This project presents a Deep Learning system designed to deblur medical images, with a specific focus on dermoscopic (skin lesion) images. Blurriness in medical    imaging can obscure critical diagnostic details, and this system aims to restore image sharpness, thereby enhancing visual quality and diagnostic potential. The    core of the solution is a custom Attention U-Net model trained on a dataset of paired blurry and sharp images. Despite the challenge of a small dataset (~200       images), the model achieves significant improvements in standard image quality metrics.
2. Key Features & Technologies
  Core Architecture: Attention U-Net, which allows the model to focus on the most relevant image features during reconstruction.
  Architectural Enhancements: The model was improved with:
      BatchNormalization for stable and faster training.
      UpSampling2D + Conv2D for high-quality upscaling, avoiding checkerboard artifacts.
      HeNormal initializer for optimal weight initialization with ReLU activations.
      Advanced Loss Function: A combined loss function was implemented to optimize for multiple aspects of image quality:
      L1 Loss: For pixel-wise accuracy.
      SSIM Loss: For preserving structural similarity.
      Perceptual Loss (VGG19): For realistic textures and high-frequency details.
      Data Augmentation: On-the-fly data augmentation (flips, rotations) was critical to prevent overfitting on the small dataset.
      Technologies: Python, TensorFlow/Keras, OpenCV, Google Colab (GPU for training).
3. Algorithm Flow
   Input: The system takes a blurry 256x256 RGB image as input.
   Preprocessing: The input image is normalized to a pixel value range. During training, the dataset is augmented in real-time.
   Model Inference: The preprocessed image is passed through the trained Attention U-Net model. The model's encoder extracts features, while the decoder with                            attention mechanisms reconstructs the sharp image.
   Output: The model outputs a deblurred 256x256 RGB image, representing the restored version of the input.
4. Performance & Results
   The final model ("UNET V5" with the combined L1+SSIM+Perceptual loss) was evaluated on a held-out test set. The results show a significant improvement over the  baseline (the original blurry images).
   Metric	Baseline (Blurry vs. Sharp)	Model Performance (Deblurred vs. Sharp)
   PSNR	34.36 dB	38.69 dB (+4.33 dB)
   SSIM	0.9562	0.9685 (+0.0123)
   Conclusion: The model successfully learned to restore sharpness, significantly increasing both the PSNR and SSIM scores, which quantitatively confirms the enhanced image quality.
