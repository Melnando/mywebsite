---
title: "Building Trust in V2X Communications: My Journey Developing a Deep Learning-Based Intrusion Detection System"
date: 2025-06-11
draft: false
tags: ["Zero Trust Architecture", "Deep Learning IDS", "Cybersecurity Research"]
---


During my final year at ESILV, I embarked on a research journey that merged cybersecurity, intelligent transportation systems (ITS), and deep learning. The goal? To create a lightweight, real-time trust evaluation system for Vehicle-to-Everything (V2X) communication, an area critical to the safety of connected and autonomous vehicles.

At first, the results were underwhelming. But persistence, experimentation, and hybrid architecture design changed everything.

## The Problem: Can You Trust Your Car's Data?
As modern vehicles become more connected, the attack surface grows. V2X systems constantly exchange data with surrounding infrastructure and other vehicles. A single spoofed or compromised signal can trigger dangerous behavior, from misdirected lane changes to full system compromise.

Traditional rule-based intrusion detection systems (IDS) are not equipped to handle this dynamic environment. That's why I explored machine learning-powered dynamic trust evaluation, where every piece of data is assessed in real time for its trustworthiness.

## From Zero Accuracy to 99% Accuracy: The Evolution of the Model
I started by training a standalone LSTM model using the ROAD dataset, which simulates realistic automotive CAN traffic including physical signal manipulation attacks. However, the LSTM on its own couldn’t learn meaningful patterns. Training accuracy stagnated at 50% and test accuracy was virtually 0%.

Here’s what changed:

1. **CNN + LSTM Hybrid Architecture**  
   I introduced 1D convolutional layers to extract spatial patterns from time-series signals—an essential step for identifying anomalous behavior in raw CAN data. Then, stacked LSTM layers captured the temporal evolution of those patterns.  
   <br/>  
   <br/>  

2. **Sliding Window Time-Series Conversion**  
   The raw CAN signals were transformed into overlapping windows of fixed time intervals using a high-resolution (10,000 Hz) resampling strategy. This enabled temporal pattern learning across multiple signals.  
   <br/>  
   <br/>   

4. **Model Optimization**  
   Using the Adam optimizer with gradient clipping, dropout layers for regularization, and a tuned architecture (Conv1D → MaxPooling → LSTM → Dense), the final model achieved:

- **Accuracy: 99.37%**

- **Precision: 86.59%**

- **Recall: 94.89%**

- **F1-Score: 90.55%**

These metrics are promising for real-world deployment where false positives and detection speed must be carefully balanced.

Why This Matters for Zero Trust in Automotive Systems
This project contributes to the development of Zero Trust Architectures (ZTA) in V2X environments. Instead of assuming that internal data is safe, every signal is continuously evaluated. This mindset aligns with modern cybersecurity standards and is crucial for future-proofing autonomous mobility.

The hybrid CNN-LSTM model I developed provides a dynamic, adaptive, and efficient framework for evaluating trust in real-time. It’s lightweight enough for embedded systems and scalable for integration into vehicular edge networks.

## What’s Next?

This is an ongoing project. I plan to:

- Integrate attention mechanisms for better interpretability  
- Test with other real-world CAN datasets for robustness  

**So far, I have only tested the system on one specific attack scenario: `correlated signal masquerade attack`.**  
To ensure broader reliability, the next step will be to evaluate the model on the other types of attacks included in the ROAD dataset. This will help assess the generalization capabilities of the architecture across diverse threat types.
