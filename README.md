# Analysis of mathmatical equations using TrOCR model
## Introduction
The inspiration behind this research project was to find a way to translate images of mathematical equations into a format that is recognizable to softwares, such as the Braille translation software (Duxbury Systems). This research analyzes the result of training the TrOCR model to convert images of mathematical equations into LATEX Mathematical Symbols.

In order to achieve this, transformers were used as a neural network model because of its effectiveness for natural language processing tasks. TrOCR model incorporates image Transformer encoder and text Transformer decoder, which made it suitable for this project. LATEX Mathematical Symbols are used to represent the equations as texts, as it is widely used in academia. 
## Fine tuning the TrOCR model
### Data sets
Two different data sets were used to fine-tune the TrOCR model. The first data set A consists of 150 images of various typed mathematical equations including, fractions, summations, and logarithms, and their respective LATEX representations. The following [tutorial](https://github.com/NielsRogge/Transformers-Tutorials/blob/master/TrOCR/Fine_tune_TrOCR_on_IAM_Handwriting_Database_using_Seq2SeqTrainer.ipynb) was used to set up the Collab Notebook to train the model.

The second data set B consists of 36 equations from the data set that only contains simple equations with symbols that does not require the ' \ ' latex notation. This includes equations with addition, subtraction, and expoenents. 

The reasoning for having two different data sets is to observe how different concentrations of similar equation types could result in different accuracies for the preditiction of the latex notations.
### Batch size, steps, and epochs
With limited GPU runtime and memory, the following values of arguments were used:
```per_device_train_batch_size=1```
```per_device_eval_batch_size=1```
``` logging_steps=20```
``` save_steps=1200 #for set A, 280 for set B```
```eval_steps=20```
```num_train_epochs=10```

### Training loss, Validation loss, and Character error rate (CER)
The folder 'A results' contain images of a table to training losses and evaluation losses for data set A, and the file 'B results' is an image of a table of the same values for data set B.

|Data set  | Training loss| Validation loss| CER|
|-----|--------|-----|-------------|
|A|2.094900  |3.934913|0.817623
|B|0.310400|1.556969|0.329670
## Analysis of the model
## Conclusion
Data set B had a lower training lossvalidation loss, and character error rate than data set A, which could be due to two different reasons. First is that TrOCR is made to recognize handwritten texts, which makes it easier to recognize symbols that can be typed with a keyboard (without the '\' LATEX notation.). Another reason could be that data set B repeats equations that use the same symbols (+, =, etc.), which allows the model to learn the pattern repeatedly, whereas data set A contains a range of symbols (trigonomentry symbols, limits, fractions, summations) which are not repeated as much in the data set which makes it more difficult to model to recognize the pattern.

Form this, the conclusion for this project is that in order to fine-tune TrOCR to create a more accurate model that could handle different equations with a variety of mathematical symbols, a large number of data set which repeats the same LATEX symbols is required.
## Next steps
A more sophisicated model that consists of splitting an image of an equation to different components could be used to accurately predict complex equations, such as those that use fractions.Since TrOCR is created to recognize hand-written texts, if a data set containing images of hand-written equations are used, the model could be applied to translate handwritten equations to LATEX notations.
## References 
[Fine tuning tutorial of TrOCR by NielsRogge](https://github.com/NielsRogge/Transformers-Tutorials/blob/master/TrOCR/Fine_tune_TrOCR_on_IAM_Handwriting_Database_using_Seq2SeqTrainer.ipynb)
[Inference tutorial by NeilsRogge](https://github.com/NielsRogge/Transformers-Tutorials/blob/master/TrOCR/Inference_with_TrOCR_%2B_Gradio_demo.ipynb)
