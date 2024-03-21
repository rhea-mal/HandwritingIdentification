# HandwritingIdentification ✍️

## Overview
HandwritingIdentification is a comprehensive project aimed at exploring and implementing state-of-the-art techniques in handwriting analysis and writer identification. Utilizing the CSAFE Handwriting Database provided by the Center for Applications in Forensic Evidence, this project leverages a dataset comprising contributions from 90 writers, totaling 2430 handwriting samples. Each writer has submitted 27 scanned documents, providing a rich dataset for analysis.

## Objective
HandwritingIdentification accurately identifies writers based on their handwriting characteristics. By preserving unique features such as pen stroke irregularities and thickness, we differentiate writers more effectively than existing methods which primarily use RNN classification for soft biometrics classification (Age, gender, and handedness).

## Preprocessing
Preprocessing plays a crucial role in preparing the handwriting samples for feature extraction and analysis. Our preprocessing pipeline includes:
- **Conversion to Grayscale:** All samples are converted to grayscale to normalize pixel values.
- **Noise Removal:** Baseline noise is reduced using a 3x3 median filter.
- **Binarization:** OTSU thresholding is applied for binarization, effectively separating ink from paper.
- **Skeletonization:** Each document image is skeletonized, preserving essential stroke information while eliminating variations due to pen type or pressure.

## Feature Extraction
Feature extraction is at the heart of our analysis, enabling the capture of character-specific attributes and global document characteristics:
- **Text Line Irregularity:** Variance in line heights across the document is measured using projection profiles.
- **Edge Detection (Canny and Sobel):** Identifies character and stroke boundaries.
- **Skeleton Endpoints:** Assesses handwriting complexity through the number of skeleton endpoints.
- **Thickness:** Evaluates stroke thickness to infer writing pressure.
- **Black and White Pixel Percentage:** Reflects ink density and stroke weight.
- **Local Binary Pattern (LBP):** Analyzes handwriting texture to capture stroke dynamics.
- **Histogram of Oriented Gradients (HOG):** Captures shape and orientation of strokes.
- **Curvature Analysis:** Derives stroke curvature, representing handwriting angularity.

## Machine Learning Models
To classify and identify handwriting, we explored various machine learning models:
- **K-means Clustering:** Initially applied to group similar handwriting samples.
- **Hierarchical Clustering:** Tested but found less effective than K-means.
- **Recurrent Neural Networks (RNN):** The complexity of handwriting identification prompted the need for a more sophisticated approach, leading to the adoption of RNNs for better performance.

## Results
The project introduces a custom metric to assess the accuracy of handwriting identification. Our findings include:
- **Variable Accuracy:** Accuracy varies by corpus, with higher accuracy observed in documents with more content.
- **Content and Length Impact:** Longer texts correlate with higher identification accuracy, highlighting the importance of content amount for effective analysis.
- **Clustering Challenges:** K-means clustering showed limitations, particularly when combining corpora. Accuracy significantly improved when analysis was restricted to a single corpus, emphasizing the need for content normalization.
- **Optimal Sample Configuration:** The analysis suggests that increasing the number of samples from the same writer improves accuracy, while a larger variety of writers introduces noise, complicating cluster identification.

Ultimately, HandwritingIdentification provides a nuanced approach to writer identification: machine learning models + k-means approach lays the groundwork for further advancements in handwriting-based authentication, identificaiton, and forensics.
