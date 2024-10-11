# Interactive-room
The aim of this project is to provide a fully immersive experience where users can see themselves in any movie scene. Not only will their face be inserted into the scene, but the dialogue will also be spoken in their own voice! We have a Google Colab for users to try it out, and we've included several movie scenes for each gender.


# Model
This project consists of three models:

1- Gender Model: This model detects the user's gender and suggests appropriate movie scenes based on the result.

2- SimSwap Model: This model detects the user's face, swaps it with the actor's face, and aligns it within the scene.

3- Voice Model: This model clones the user's voice, allowing the actor's lines to be spoken in the user's voice.

# Process
We first trained the gender model using the pre-trained YOLOv10s model. Next, we trained the SimSwap model, and finally, we used the Coqui TTS model for voice cloning. Finally, we built an interface to host these models.

# Guidance
To begin, we have to set up the SimSwap environement. Firslty, you have to run these following commands to get the necessary files.

clone the repository

```
%cd zaka
```
```
!pip install -r requirements.txt
```
```
!git clone https://github.com/neuralchen/SimSwap 
```
```
!mkdir -p SimSwap/checkpoints
```
```
!mkdir -p SimSwap/insightface_func/models
```
```
!mkdir -p SimSwap/parsing_model/checkpoint
```
```
!gdown --id 1PsvCnILPVnfXSVplvbtfmYC4a6Wy2mZx
```
```
!mv ./79999_iter.pth SimSwap/parsing_model/checkpoint
```
```
!gdown --id 1eg5abGyFk-q5PbYiba4LbihwX4rNyEh-
```
```
!mv ./antelope.zip SimSwap/insightface_func/models
```
```
!unzip ./SimSwap/insightface_func/models/antelope.zip -d ./SimSwap/insightface_func/models/
```
```
!mkdir -p SimSwap/arcface_model
```
```
!gdown --id 1TLNdIufzwesDbyr_nVTR7Zrx9oRHLM_N -O SimSwap/arcface_model/arcface_checkpoint.tar
```
```
!mkdir ./SimSwap/checkpoints/people
```

## Note
We did not provide any pre-trained models, so you will need to use your own trained SimSwap and Gender models to proceed.

In the 'people' folder, move your trained SimSwap model to this directory and rename it as latest_net_G.pth for easier handling and use.

Navigate to SimSwap/util/reverse2original.py and convert all instances of np.float to float for compatibility.
