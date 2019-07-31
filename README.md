# MyAILibrary
 
This is my version of Keras, because I wanted more wiggle room while developing my models. Not designed to be user friendly, just to let you know. 

## Dependencies
```
tensorflow vs. 2.0
numpy
pickle (pre-installed)
csv (pre-installed)
os (pre-installed)

Utility (included in the repo)
DataStructure (included in the repo)
```

## API

### Direct Functions

```
unpickle(filedir)
```
This extracts your pickle object


```
accuracy(predictionmatrix, onehotvector)
```
This will return the accuracy of the prediction as a decimal

```
record_error(data, labels, predictions)
```
this returns a list containing the right and wrong predicted datapoints


### Classes
```
Logging()
```
Class functions:

```
___init__(base directory, print step, summary step, save step)
```
This establishes the base directory for logging (needs slash) and the epoch steps

```
log_train(prediction, label, loss, l2loss, big_list)
```
call this every epoch and it will log cross entropy loss, accuracy. THIS MUST BE RUN INSIDE TF SUMMARY SCOPE

```
make_confusion_matrix(prediction, label)
```
returns confusion matrix

```
test_log(prediction, label)
```
This will make and save a confusion matrix as well as test set accuracy


```
log_valid(validation accuracy, step)
```
logs validation accuracy (wrapper function)


The following classes have a very similar structure
```
Convolve()
Pool()
Flatten()
Dropout()
Softmax()
Combine_add()
FC()
ResNetChunk()
Inceptionv1Chunk_naive()
Inceptionv1Chunk()
```

All of these classes have a call() function where an input goes in and an output is calculated. THESE MUST BE RUN AS A @TF.FUNCTION AND UNDER GRADIENT TAPE TO BE READ

Some of these classes: Convolve, FC, ResNetChunk, Inceptionv1Chunk_naive, Inceptionv1Chunk have init, build, and build-model_from_pickle calls. These simply build up the model, and you can find out how they work by looking at the code. Essentially, you initialize all tf.variables in the build functions and the __init__ has some important metadata. Build_model_from_pickle is when you need to restore a session. 
