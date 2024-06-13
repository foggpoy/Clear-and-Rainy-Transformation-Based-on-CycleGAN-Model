# Clear-and-Rainy-Transformation-Based-on-CycleGAN-Model
The goal of this project is to use a CycleGAN model to perform the conversion between rainy images and clear images. 
# Introduction
With the continuous development of autonomous driving technology, driving scenarios in bad weather conditions have been one of the important challenges faced by autonomous driving systems. Severe weather conditions such as rain, snow or haze can seriously affect sensor performance and reduce image quality, resulting in reduced reliability for critical tasks such as target detection, road recognition and vehicle tracking. Therefore, in order to improve the robustness of the autopilot system in bad weather conditions, we try to implement a rainy-clear conversion. 

We will explore in depth the design principle of CycleGAN model and its performance in rainy-clear conversion tasks. Through the research of this project, we hope to provide new insights and solutions for the further application of rainy-clear conversion technology in intelligent transportation systems. Ultimately, we expect this work to lead to substantial improvements in the reliability and safety of autonomous driving systems in a variety of weather conditions.
# File Description
We have a total of five code folders and two of our main files: test.py and train.py.

## train.py
General-purpose training script for image-to-image translation.

It first creates model, dataset, and visualizer given the option.

It then does standard network training. During the training, it also visualize/save the images, print/save the loss plot, and save models.
```
python train.py --dataroot ./dataset/rainy_to_clear --name rainy_to_clear --model cycle_gan --use_wandb
```
## test.py
General-purpose test script for image-to-image translation.

Once you have trained your model with train.py, you can use this script to test the model.
It will load a saved model from '--checkpoints_dir' and save the results to '--results_dir'.

It first creates model and dataset given the option. It will hard-code some parameters.
It then runs inference for '--num_test' images and save results to an HTML file.
```
python test.py --dataroot ./dataset/rainy_to_clear/testA --name rainy_to_clear --model test --no_dropout
```
```
python test.py --dataroot ./dataset/rainy_to_clear/testB --name rainy_to_clear --model test --no_dropout
```
## Others
`data`    This package includes all the modules related to data loading and preprocessing.  

In template_dataset.py,  
    modify_commandline_options:　Add dataset-specific options and rewrite default values for existing options.  
    __init__: Initialize this dataset class.  
    __getitem__: Return a data point and its metadata information.  
    __len__: Return the number of images.  
  
`dataset`    This has our own dataset rainy_to_clear(from BDD100k dataset).  

`models`    This package contains modules related to objective functions, optimizations, and network architectures. 

In template_model.py,  
    modify_commandline_options:　Add model-specific options and rewrite default values for existing options.  
    __init__: Initialize this model class.  
    set_input: Unpack input data and perform data pre-processing.  
    forward: Run forward pass.This will be called by both optimize_parameters and test.  
    optimize_parameters: Update network weights; it will be called in every training iteration.  
    
`options`    This package options includes option modules: training options, test options, and basic options (used in both training and test).  

`util`    This package includes a miscellaneous collection of useful helper functions.
## Tech used
![image]("C:\Users\lenovo\Desktop\1718299056834.jpg")
