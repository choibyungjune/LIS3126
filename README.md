# LIS3000

This repository includes the script files used in performing music proposal based on sentimental analysis with huggingface transformers and simple doc-to-doc model.
With lack of memory, the datafile used for the project now unavailable.

## Doc-to-Doc model

This model vectorizes each diary and lyrics with FastText, then find out matching songs based on vector. Rankings are based on cosine-similarity of those diary content and music lyrics.

## Sentiment-vector model

This model(s) extract sentiment vector from given diary, and does same sentiment extraction for music lyrics. For each diary given, system will extract sentiment vector, and try find out most relative lyrics, based on cosine-similarity between sentiment vectors. All music in library will have corresponding sentiment vectors in advance.

### model architecture

The model is whole from getting pre-trained models from HuggingFace, then fine-tuning with sentiment labeled corpus. Generally used BERT-based model, and tried various method such hyperparameter-tuning, data augmentation, k-fold, early-stopping, and so on. After trying various models, three best-performanced models has been chosen. Now it is named as model_1 to model_3, and could find its fine-tuning code from "Vectorize_sentiment" folder.

## Evaluation

Evaluation has been done with two layers: Validation, and human test.
Validation is automatically done with validation set. With code in "Vectorize_sentiment" folder could find exact mechanism.
Human test is conducted with participants, and each participants experienced the evaluation model, and chose best fit model from 4(sentiment 3 + doc2doc) models. "Integrated.ipynb" used in the test process, and it made each model to recommend same number of songs, shuffled them, and show it to test participants. Participants chose nice recommended songs from the shown music, and model with highest score(the number of song chosen from participants) considered better.
