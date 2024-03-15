# S7
Session 7 files

## Basic expectations
- \> = 99.4% accuracy
- < = 8000
- < = 15 epochs

***Kept everything in 1 ipynb file for ease of trials on Colab. Did not keep multiple files to try multiple experiments***
***Can be easily converted to modular code once finalized***

## First step - Setup and Basic Skeleton: S6_1.ipynb

### Target:
- Setup
  - Get the set-up right
  - Set Transforms
  - Set Data Loader
  - Set Basic Working Code
  - Set Basic Training  & Test Loop
- Basic Skeleton

### Results:
- Epochs: 15
- Parameters: 350,600
- Training Batch size: 128
- Testing Batch size: 2048
- Training
  - Loss=0.0090
  - Batch_id=468
  - Accuracy=99.59%
- Testing
  - Average loss: 0.0340
  - Accuracy: 9900/10000 (99.00%)

### Analysis:
- Heavy Model for such a problem
- Model is slightly over-fitting, but consistent in the accuracy
- Testing acuracy not increasing though Training accuracy increasing showing overfitting
- Testing Accuracy is not near what we need
- Will change to lighter model in next run
- Later will try to remove overfitting with different options

## Step 2 - Lighter model: S7_2.ipynb

### Target:
- Make the model lighter having less number of parameters

### Results:
- Epochs: 15
- Parameters: 8,716
- Training Batch size: 128
- Testing Batch size: 2048
- Training
  - Loss=0.0229
  - Batch_id=468
  - Accuracy=98.84%
- Testing
  - Average loss: 0.0469
  - Accuracy: 9859/10000 (98.59%)

### Analysis:
- Model is the size of what is needed
- Accuracy is lower
- Model is overfitting slightly
- Next try Batch Normalization and Regularization and GAP

## Step 3 - Batch Normalization and Regularization and GAP: S7_3.ipynb

### Target:
- Batch Normalization after each step
- Regularization using Dropout after each step
- GAP replacing the Fully connected layer

### Results:
- Epochs: 15
- Parameters: 3,964
- Training Batch size: 128
- Testing Batch size: 2048
- Training
  - Loss=0.1836
  - Batch_id=468
  - Accuracy=92.91%
- Testing
  - Average loss: 0.1715
  - Accuracy: 9501/10000 (95.01%)

### Analysis:
- Model is reduced to half
- Accuracy has gone quite down
- Model accuracy is good - Testing acuuracy higher than Train accuracy
- Can try and increase the accuracy due to the same
- Will work on increasing capacity to increase accuracy
- Will work on Correcting MaxPooling location

## Step 4 - Increasing capacity and Correcting MaxPool location: S7_4.ipynb

### Target:
- Increase capacity based on the project params
- Correcting maxpool location based on the pixels

### Results:
- Epochs: 15
- Parameters: 7,548
- Training Batch size: 128
- Testing Batch size: 2048
- Training
  - Loss=0.0192
  - Batch_id=468
  - Accuracy=98.33%
- Testing
  - Average loss: 0.0288
  - Accuracy: 9922/10000 (99.22%)

### Analysis:
- Increased params to close to 8000
- Accuracy has gone up close to our target but still need to be improved
- Did not see any overfitting
- Look at images and put different image augmentation techniques
- Use an LR scheduler with auto adjustment of learning rate

## Step 5 - Image augmentation and adaptive LR scheduler: S7_5.ipynn

### Target:
- Look at images and use different image augmentations as per that to increase training complexity
  - Center Crop: 24 size crop to remove the outside 4 pixels to remove some edges
  - Image rotation: Checked and image rotation of +-20% seemed to be good
  - Random perspective change
  - Changes like brightness, contrast, saturation, hue, etc to have different types of images
- Use adaptive LR scheduler to help with adjusting learning rate with scaling factor of 0.2 (instead of 0.1 to learn a bit faster)
- Changed the batch size for training to 64 from 128 for it to backward propogate more times within same number of epochs
- Changed the model to have continuously increasing channels instead of increasing and decreasing
- Multiple trials to understand how to improve accuracy

### Results:
- Epochs: 15
- Parameters: 7,528
- Training Batch size: 64
- Testing Batch size: 64
- Training
  - Loss=0.0440
  - Batch_id=938
  - Accuracy=98.63%
- Testing
  - Average loss: 0.0189
  - Accuracy: 9940/10000 (99.40%)
LR Rate: 0.002 

### Analysis:
- Tried multiple techniques but need to have more tools and techniques to further improve
- Accuracy has gone up and consistently matching our target
- Did not see any overfitting
- Look at the test related data that is still not getting right accuracy and based on that take some steps
- Increase the dataset using augmentations to have various combinations and more steps with same batch size
- Not pursuing these for now due to lack of time
