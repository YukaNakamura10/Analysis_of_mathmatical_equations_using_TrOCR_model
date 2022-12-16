# Analysis of mathmatical equations using TrOCR model
## Introduction
The inspiration behind this research project was to find a way to translate images of mathematical equations into a format that is recognizable to many software. This research analyzes the result of training the TrOCR model to convert images of mathematical equations into LATEX Mathematical Symbols.

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
|A|2.094900  |3.934913|0.817623|
|B|0.310400|1.556969|0.329670|
## Analysis of the model
Model A is a model that was generated from fine-tuning the TrOCR model with data set A, whereas model B is a model that was genrated from fine-tuning the TrOCR model with data set B.

The graph bellow compares the text outputted from both models with the given input of the image of the equation. The equations are from the 
|Equation |Original model| Model A| Model B| Correct notation|
|-----|--------|-----|----|-----|
|![equation1](https://user-images.githubusercontent.com/92125894/206562398-0da6ae01-d32e-4c28-b738-8606d25b8cb6.jpg)||11121  |1+1=2|1+1=2|
|![equation2](https://user-images.githubusercontent.com/92125894/206562555-b0efceb9-ba58-474a-ab6a-b068bcfc9b1c.jpg)||y===1=111|y=x+1|y=x+1|
|![equation4](https://user-images.githubusercontent.com/92125894/206562600-6191b648-9595-4d83-88ea-2ac4b81d64ce.jpg)||3 |3-2=1 |3-2=1|
|![equation6](https://user-images.githubusercontent.com/92125894/206562686-ddd4072f-be6c-447f-b2c6-ab98c5e2e3e2.jpg)||3xxx2xx15x21522|3(2+2) = 5 |3(x+2)=15|
|![equation11](https://user-images.githubusercontent.com/92125894/206563981-3a33cec5-1005-4668-b477-0a9e58ef8ccf.jpg)||xxx2xx +xx = + +x + + + 0 + +2 + + 4 + +| x^2 + 2x + 4 = 0|x^2 +2x+ 6 = 0|


Model B had a far more accurate output compared to model A.

The graph bellow shows the text outputted from model A with complex equations containing ' \ ' LATEX notations.

|Equation |Original model| Model A| Correct notation|
|-----|--------|--------|-------|
|![equation7](https://user-images.githubusercontent.com/92125894/206566861-bd6dad03-327d-4aba-a077-c526c0750878.jpg) |VX - 4| \x|\sqrt(x)=4|
|![equation19](https://user-images.githubusercontent.com/92125894/206566913-5bdc5810-9941-41c7-9e0c-287211915f03.jpg)|cos2 0 4sin2 0 - 1| a = = =^ = =|\cos^2 \theta + \sin^2 \theta = 1|
|![equation20](https://user-images.githubusercontent.com/92125894/206567003-8b0fa9ce-9222-4ed0-9498-df400ccfe304.jpg)|loga-log b.| \loglloga-log b.oglog \log|\log a = \log b|
|![equation21](https://user-images.githubusercontent.com/92125894/208016925-6ba1552b-f138-4b03-9490-45bc4a938ad4.jpg)|a lim-explo ) -|\\\xxxtoxxexpxtotoxexpexpxx}xtoexpxexp}xx|\lim\limits_{x \to n-1} \exp(x) = 0|
|![equation62](https://user-images.githubusercontent.com/92125894/206567172-646a7340-7d50-4600-92b1-58fe754b319f.jpg)|T.| \frac4|\frac{\pi^4}{15}|
|![equation75](https://user-images.githubusercontent.com/92125894/206567242-5496447f-ec64-4e45-933e-284d38773dee.jpg)|1 S.C| 1q|1\leq x|

Model A was not Able to generate accurate LATEX notations.

## Conclusion
Comparing model A and model B, model B generated a more accurate LATEX notation of equations. In addition, Model B had a lower training loss, validation loss, and character error rate than model A which couldd be due to two different reasons. First is that TrOCR is made to recognize handwritten texts, which makes it easier to recognize symbols that can be typed with a keyboard (without the '\' LATEX notation.). Another reason could be that model B repeats equations that use the same symbols (+, =, etc.), which allows the model to learn the pattern repeatedly, whereas model A contains a range of symbols (trigonomentry symbols, limits, fractions, summations) which are not repeated as much in the data set which makes it more difficult to model to recognize the pattern.

Form this, the conclusion for this project is that in order to fine-tune TrOCR to create a more accurate model that could handle different equations with a variety of mathematical symbols, a large number of data set which repeats the same LATEX symbols is required.
## Next steps
A more sophisicated model that consists of splitting an image of an equation to different components could be used to accurately predict complex equations, such as those that use fractions.Since TrOCR is created to recognize hand-written texts, if a data set containing images of hand-written equations are used, the model could be applied to translate handwritten equations to LATEX notations.
## References 
[Fine tuning tutorial of TrOCR by NielsRogge](https://github.com/NielsRogge/Transformers-Tutorials/blob/master/TrOCR/Fine_tune_TrOCR_on_IAM_Handwriting_Database_using_Seq2SeqTrainer.ipynb)<br>
[Inference tutorial by NeilsRogge](https://github.com/NielsRogge/Transformers-Tutorials/blob/master/TrOCR/Inference_with_TrOCR_%2B_Gradio_demo.ipynb)
