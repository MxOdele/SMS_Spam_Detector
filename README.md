# SMS_Spam_Detector

<div align='center'>
    <img src='https://images.pexels.com/photos/5999793/pexels-photo-5999793.jpeg' height='350' title='A business woman concentrates on her smartphone as she stands outside (image courtesy of Pexels)' alt='A businesswoman in a suit concentrates on her phone as she stands outside in front of a building that is blurred in the background' />

*Gradio SMS Text Classification*[^1]

**Module 21 Challenge**
</div>

## Table of Contents

* [Overview](#Overview)
* [Execution](#Execution)

---

## Overview

### *The Assignment*

The Module 21 Challenge 

### *Written in*

Jupyter Notebook using Python v3.10.13, Pandas, scikit-learn, and Gradio

### *Accessing the notebook*

To access the notebook, simply download the `.ipynb` file `gradio_sms_text_classification.ipynb`, and the `Resources` folder with the `.csv` file `SMSSpamCollection.csv`, into a local directory, then load the `gradio_sms_text_classification.ipynb` file into Jupyter Notebook through your terminal.

---

## Execution

### *How to use*

Simply `Run All Cells` to execute the code in every cell of the notebook in sequence. Alternatively, each cell may be `Run` on its own, though it is still recommended to run them in order. Once run, text messages may be loaded into the launched app in the `input` field (labeled `"What is the text message you want to test?"`), then press `Submit` to generate the predicted `output`.

### *Breaking down the code*

Below is a more in-depth explanation of the various cells coded within the `gradio_sms_text_classification.ipynb` notebook.

| Cell | Notes[^2] |
| ---: | :--- |
| 1[^3] | Importing libraries and dependencies <br> <br> Setting maximum column width for readability when viewing the text message data |
| 2 | Defining the `sms_classification()` function; <br> *Parameter:* `sms_text_df`, a DF containing `text_message` and `label` features for SMS classification <br> *Returns:* `text_clf`, a fitted pipeline model for SMS classification <br> <br> *Contained Code;* <br> <br> Declaring `X` as the `text_message` feature of the passed DataFrame (DF) <br> <br> Declaring `y` as the `label` feature of the passed DF <br> <br> Splitting the data into training and testing sets, with `test_size` set to **33%** <br> <br> Declaring `text_clf` as a `Pipeline` of `TfidVectorizer` and `LinearSVC` to transform the training dataset <br> *Note: The* `dual=True` *argument was passed into the* `LinearSVC` *model to prevent a warning from being thrown in **Cell 4*** <br> <br> Fitting the `text_clf` model to the training dataset[^4] <br> *Note: This was removed from the* `return` *portion of the* `def` *function to allow for comparison  to the test dataset before passing the DF out of the function* <br> <br> Comparing the training and testing datasets by scoring the accuracy of the model on both[^4] <br> *Note: This was added due to the instructions calling for a comparison of the datasets, while the starter code provided no such space for these two lines of code* <br> <br> Returning the model[^4] |
| 3 | Importing data to the DF `sms_text_df` <br> <br> Displaying a sample of the data |
| 4 | Declaring `text_clf` as calling the `sms_classification` function on the `sms_text_df` DF <br> *Note: The training and testing accuracy scores display during the execution of this cell* |
| 5 | Defining the `sms_prediction()` function; <br> *Parameter:* `text`, a text message to be classified <br> *Returns:* `str`, a message indicating whether `text` was classified as spam or not <br> <br> *Contained Code;* <br> <br> Declaring `new_msg` as the `text_clf` model's prediction based on the passed `text` parameter <br> <br> Retuning a message based on a conditional on the prediction from `new_msg` <br> **if** `new_msg` returns 'ham', `sms_prediction` returns that the message is not spam <br> **else**, `sms_prediction` returns that the message is spam |
| 6 | Declaring `app` as a Gradio `Interface` built on the `sms_prediction` function and with `inputs` and `outputs` set to `Textbox` <br> <br> Launching `app` |

### *Testing Results*

Based on used of the app, the provided messages to test were classified as follows;

| SMS Message | Classification |
| :--- | :--- |
| You are a lucky winner of $5000! | ham |
| You won 2 free tickets to the Super Bowl. | ham |
| You won 2 free tickets to the Super Bowl text us to claim your prize. | spam |
| Thanks for registering. Text 4343 to receive free updates on medicare. | spam |

[^1]: Image courtesy of the free source image site, <a href='https://www.pexels.com/photo/crop-concentrated-ethnic-businesswoman-with-smartphone-5999793/' title='Link to Pexels listing for image'>Pexels</a>

[^2]: Markdown cells for instructions not annotated

[^3]: Denotes cells with completed code provided, no student coding contained

[^4]: Denotes lines of code by student diverging from provided prompts due to ambiguous instructions, commented prompts differ from provided starter code