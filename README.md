# NiftyNet_skullstripping

This github repo includes pre-trained niftynet models and config files for skull stripping MRIs.  
Information on how to use niftynet: https://niftynet.io

- Create the python environment: To use the models in this repository, you will need to create a conda environment on your local machine using python 3.6.10 and installing niftynet 0.6.0 in the environment.

"
conda create –n niftynet python=3.6
pip install tensorflow==1.15.*
pip install niftynet==0.6.0 
"

- Prepare your data: Prepare a folder with all cases in there. Make sure your input images have imagetype in the filename (i.e. ‘_T1GD’, or ‘_FLAIR’). You do not need to resample the images to a common voxel size, that should be done locally on your data as the niftynet pipeline will not change voxel spacing. Images will be resized to target imaging dimensions (240, 240, 64) as part of running the code. Update the configuration file to reflect where images are located and how images are labeled. To switch between FLAIR, T1Gd, or Multi input model, change 'image' argument in the configuration file.

- models: Download the model files and unzip files in your local machine. Update the configuration file to reflect path to model. Ideally your images match the imaging sequence that the model was trained on. To switch between FLAIR, T1Gd, or Multi models, change the model_dir argument in [SYSTEM] section to the appropriate path. In addition, adjust the inference_iter arguement in the [INFERENCE] section to the correct model iteration found in the model_dir.

- Running the model: In a terminal window, activate the python environment with niftynet, and run the following line:
 "source activate niftynet
 net_run inference -a niftynet.application.segmentation_application.SegmentationApplication -c <configfilepath>"

 
It should be noted that the Configuration file in this repository only includes parameters (and hyperparameters) that were specifically tuned in our experiment. Any parameter not specifically mentioned in the configuration file was left as the default value in niftynet. 


