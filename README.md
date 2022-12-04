# Analysis of mathmatical equations using TrOCR model
## Introduction
The inspiration behind this research project was to find a way to translate images of mathematical equations into a format that is recognizable to softwares, such as the Braille translation software (Duxbury Systems). This research analyzes the result of training the TrOCR model to convert images of mathematical equations into LATEX Mathematical Symbols.

In order to achieve this, transformers were used as a neural network model because of its effectiveness for natural language processing tasks. TrOCR model incorporates image Transformer encoder and text Transformer decoder, which made it suitable for this project. LATEX Mathematical Symbols are used to represent the equations as texts, as it is widely used in academia. 
## Training the TrOCR model
Data consisting of 150 images of various typed mathematical equations including, fractions, summations, and logarithms, and their respective LATEX representations were used to train the TrOCR model. The following tutorial was used to set up the Collab Notebook to train the model.
<https://github.com/NielsRogge/Transformers-Tutorials/blob/master/TrOCR/Fine_tune_TrOCR_on_IAM_Handwriting_Database_using_Seq2SeqTrainer.ipynb>
## Analysis of the model

## Conclusion
## Next steps
A more sophisicated model that consists of splitting an image of an equation to different components for fractions could be used to accurately predict complex equations, such as those that use fractions.
## References 
[tutorial]: <https://github.com/NielsRogge/Transformers-Tutorials/blob/master/TrOCR/Fine_tune_TrOCR_on_IAM_Handwriting_Database_using_Seq2SeqTrainer.ipynb>
