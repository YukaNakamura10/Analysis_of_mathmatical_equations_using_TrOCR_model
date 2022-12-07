# Analysis of mathmatical equations using TrOCR model
## Introduction
The inspiration behind this research project was to find a way to translate images of mathematical equations into a format that is recognizable to softwares, such as the Braille translation software (Duxbury Systems). This research analyzes the result of training the TrOCR model to convert images of mathematical equations into LATEX Mathematical Symbols.

In order to achieve this, transformers were used as a neural network model because of its effectiveness for natural language processing tasks. TrOCR model incorporates image Transformer encoder and text Transformer decoder, which made it suitable for this project. LATEX Mathematical Symbols are used to represent the equations as texts, as it is widely used in academia. 
## Fine tuning the TrOCR model
### Data sets
Two different data sets were used to fine-tune the TrOCR model. The first data set A consists of 150 images of various typed mathematical equations including, fractions, summations, and logarithms, and their respective LATEX representations. The following [tutorial](https://github.com/NielsRogge/Transformers-Tutorials/blob/master/TrOCR/Fine_tune_TrOCR_on_IAM_Handwriting_Database_using_Seq2SeqTrainer.ipynb) was used to set up the Collab Notebook to train the model. With limited GPU and memory, the following values of arguments were used:
```per_device_train_batch_size=1```
```per_device_eval_batch_size=1```
``` logging_steps=200```
``` save_steps=1200```
```eval_steps=200```
```num_train_epochs=10```

The second data set B consists of 36 equations from the data set that only contains simple equations with symbols that does not require the ' \ ' latex notation. This includes equations with addition, subtraction, and expoenents. The following values of arguments were used for the second data set.
```per_device_train_batch_size=1```
```per_device_eval_batch_size=1```
``` logging_steps=20```
``` save_steps=280```
```eval_steps=20```
```num_train_epochs=10```

The values of logging steps and evaluation steps were increased for B to fine tune the model further to get a precise model that is catered for recognizing simple equations. The reasoning for having two different data sets is to observe how different concentrations of similar equation types could result in different accuracies for the preditiction of the latex notations.
### Batch size, steps, and epochs
With limited GPU rutntime and memory, the following values of arguments were used:
```per_device_train_batch_size=1```
```per_device_eval_batch_size=1```
``` logging_steps=20```
``` save_steps=1200 #for set A, 280 for set B```
```eval_steps=20```
```num_train_epochs=10```

### Training loss and Validation loss
## Analysis of the model
## Conclusion
## Next steps
A more sophisicated model that consists of splitting an image of an equation to different components for fractions could be used to accurately predict complex equations, such as those that use fractions.
## References 
[Fine tuning tutorial of TrOCR by NielsRogge](https://github.com/NielsRogge/Transformers-Tutorials/blob/master/TrOCR/Fine_tune_TrOCR_on_IAM_Handwriting_Database_using_Seq2SeqTrainer.ipynb)
[Inference tutorial by NeilsRogge](https://github.com/NielsRogge/Transformers-Tutorials/blob/master/TrOCR/Inference_with_TrOCR_%2B_Gradio_demo.ipynb)
