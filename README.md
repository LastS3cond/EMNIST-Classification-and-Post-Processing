# Post-processing in Text Recognition

This repository contains code for applying post-processing techniques to improve the accuracy of text recognition models while reducing computational requirements during inference. The core idea is to leverage efficient post-processing algorithms on the raw model outputs to correct errors and increase overall accuracy.

## Overview

The project focuses on the task of recognizing text in images and converting it to machine-readable text. While state-of-the-art models like Convolutional Neural Networks (CNNs) can achieve high accuracy, they often require significant computational resources during inference, making them difficult to deploy in real-time or resource-constrained environments.

This work explores the use of post-processing techniques to mitigate this issue. It trains several models (Naive Bayes, Random Forest, K-Nearest Neighbors, and a custom CNN) on the EMNIST dataset for character recognition. Then, it applies different levels of post-processing on the raw model outputs to improve word and character accuracy:

1. **Level 0**: Raw model output
2. **Level 1**: Word vs. number classification
3. **Level 2**: Dictionary lookup for word validity
4. **Level 3**: Spell correction with 1 edit distance
5. **Level 4**: Spell correction with 2 edit distances for longer words
6. **Level 5**: Spell correction with 3 edit distances for very long words

The post-processing techniques leverage efficient algorithms like dictionary lookups, spell-checking, and edit distance calculations to correct errors in the model outputs.

## Results

The code evaluates the models on a dataset of paragraphs, measuring word accuracy, character accuracy, and time across different processing levels. The results show that post-processing can significantly improve the accuracy of all models, with up to ~30% increase in word accuracy and ~5% increase in character accuracy for higher processing levels.

Furthermore, the post-processing techniques are computationally efficient, adding only ~140ms on average per sentence for higher processing levels. This makes post-processing a viable approach to achieve high accuracy while keeping inference time and computational requirements low.

## Usage

The code is provided as two Python notebooks (`MethodComparison.ipynb and CNN.ipynb`). To run it, you'll need to have the required dependencies installed (listed in the `requirements.txt` file).

1. Install the dependencies:
pip install -r requirements.txt
2. Download the datasets:
The random paragraphs can be found at https://www.kaggle.com/datasets/nikitricky/random-paragraphs/
The EMNIST dataset can be found at https://www.kaggle.com/datasets/crawford/emnist
3. Run the scripts:
   
MethodComparison.ipynb, which trains Naive Bayes, Random Forest, K Nearest Neighbors, and a CNN and compares their accuracies over a variety of post-processing.

CNN.ipynb, which solely trains the Convolutional Neural Network and compares a variety of minimum viable probabilities with resulting accuracies

## License

This project is licensed under the [MIT License](LICENSE).

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvement, please 
