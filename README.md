# Interactive-room
The aim of this project is to have a fully emerged experience where the user can see themselves in  any movie scene, and not only the face, but also the scenes lines will be spelled by the user's voice! It has a google colab to try it, we attached some movie scenes for each gender.


# Model
This project consists of three models:

1- The first one is the gender model where it will detect the user's gender and proposes movie scenes based on it.

2- The second model is the SimSwao model where it will detect the face, swap it and align it on the scene.

3- The voice model will have to clone the user's voice so the words of the actor will be said by the user's voice.

# Process
We firstly trained the gender model using Yolov10s pre-trained model, then we tested the SimSwap model but we considered training it for better result and finally we used Coquii TTS model for voice cloning.

# Guidance
To begin, we have to set up the SimSwap environement, since we already have our gender model. To use it, you have to run these following commands to get the necessary files

clone the repository
%cd zaka
!git clone https://github.com/neuralchen/SimSwap 
!mkdir -p SimSwap/checkpoints
!mkdir -p SimSwap/insightface_func/models
!mkdir -p SimSwap/parsing_model/checkpoint

!gdown --id 1PsvCnILPVnfXSVplvbtfmYC4a6Wy2mZx
!mv ./79999_iter.pth SimSwap/parsing_model/checkpoint

!gdown --id 1eg5abGyFk-q5PbYiba4LbihwX4rNyEh-
!mv ./antelope.zip SimSwap/insightface_func/models

!unzip ./SimSwap/insightface_func/models/antelope.zip -d ./SimSwap/insightface_func/models/

!mkdir -p SimSwap/arcface_model
!gdown --id 1TLNdIufzwesDbyr_nVTR7Zrx9oRHLM_N -O SimSwap/arcface_model/arcface_checkpoint.tar
!mkdir ./SimSwap/checkpoints/people

!gdown --id 1-NwyIz9prIuRD1HSnLHxlxCSLP_1y5EK
!mv ./latest_net_G.pth ./SimSwap/checkpoints/people #this is our 390K steps model, it is named as 'latest' so we do not need to specify "which epoch" in
the command of SimSwap

Go to "SimSwap/util/reverse2original.py" and convert all 'np.float' to float.
