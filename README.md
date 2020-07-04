# Auto-Colorization

All files contain such big images that github can't load them. 
please download and see them on Google colab.

dataset : flower102 <br />
you can download at https://www.kaggle.com/c/oxford-102-flower-pytorch/data <br>
If you are interested, you can try another dataset. However, you should change models(ex. change encoder structure for 102 categories to other).

##Execution order <br/>
we have 3 sequential steps to train each modules instead of traning the whole model at one step.    
 
  1. encoder
   - Link the dataset to use for training, validation, test.
   - It uses resnet50 as the baseline.
   - Encoder is defined as classification model for 102 categories. After training, encoder is assumed to make good feature vectors for images.
   
   
  2. generator
   - Use the trained encoder from 1. 
   - The model contains same structure for the encoder with 1. The decoder part is added for generating ab(NOT RGB) colors.
   - Generator structure
   <br><br>![generator](./_images/generator.jpg)
   
  3. GAN
   - Use the trained generator from 2.
   - L1 loss is added to GAN loss. This is for training stability, also the right color.
   - GAN structure
    <br/><br> ![gan](./_images/gan.jpg)

##Result
 ![cinoare](./_images/compare.jpg)
 <br>
 with L1 loss integrated to GAN, final model shows good performances : right color, good impression(색감) .
 