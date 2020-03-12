# Receipt-Text-Extraction
Code to train your own Keras model on labelled receipt images collected from the wild.

Also releasing a pre-trained model bestext.hd5 which can be finetuned on your data.

1. How did you go about Pre-processing the data ?
A: The common operations were to binarize and remove the colour channel in both training and test images. In the final test images given by tonetag, I detected the text right out of the image using OpenCV functions descriptions for which are given in the respective cell heading.

2. Model and explanation.
A: Explained the model in the model cell heading and summary heading cells. 

3. Performance measuring of the model.
A: Since the images given were not labelled, I have no way measuring the performance for these ~900 images apart from manually checking each prediction file. But the validation accuracy from labelled images (which I collected) was arrived at using tthe CTC loss function the description for which has been updated in the relevant cell above.

4. Is there something I could have done better ?
A: There are a lots of things that can be further done to improve this whole pipeline. This notebook and the predictions submitted is the first approach I thought to try. While doing this project, there were multiple approaches I could think of, but given the time constraint, and already being half way through, trying other approaches wasn't feasible :

    Here are the alternative approaches in decreasing order of preference :


        a) Two different DL models for TEXT DETECTION , TEXT RECOGNITION. 
        PROS : Easier to tune.
        CONS : might be prone to overfitting to training data.

        b) An single model for end to end TEXT DETECTION + TEXT RECOGNITION
        PROS : Deep Learning would obviously be more robust to finding text boxes and predicting the text inside. 
        CONS : This approach would need 2-3X more data and 2-3X more training time and designing time (hyperparameter tuning) as the learning would be harder here.

        OTHERS :
            1. More labelled training data. 
            a) by generating textual data of words from a dictionary. 
            b) Collecting data apart from receipt images (I only used around 700 labelled receipt images data here)

            2. Data Augmentataion :
                a) Using standard keras datagen pre-processing steps like rotation, sheer etc.
            2. More num of epochs 
            Wouldve done it, but got GPU access pretty late. And Google Colab is very painful for Data I/O

            3. Hyperparameter tuning of the DL model
                 a)more layers, more neurons per layer, trying GRUs instead of LSTMs. 
                 b)Using a Global average pooling layer instead of flattening the CNN output. 
