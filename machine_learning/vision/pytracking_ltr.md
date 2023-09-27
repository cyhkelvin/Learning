# pytracking-LTR(learning tracking representations)

* [Overview](#overview)
* [Training your own networks](#training-your-own-networks)
* [HCAT as an example tracker](#HCAT-as-an-example-tracker)
   * [HCAT](#HCAT)

## Overview

## Training your own networks
To train a custom network using the toolkit, the following components need to be specified in the train settings.
For reference, see [atom.py](https://github.com/visionml/pytracking/blob/master/ltr/train_settings/bbreg/atom.py).  
- Datasets: The datasets to be used for training. A number of standard tracking datasets are already available in ```dataset``` module.
- Processing: This function should perform the necessary post-processing of the data, e.g. cropping of target region, data augmentations etc.  
- Sampler: Determines how the frames are sampled from a video sequence to form the batches.  
- Network: The network module to be trained.  
- Objective: The training objective.  
- Actor: The trainer passes the training batch to the actor who is responsible for passing the data through the network correctly, and calculating the training loss.  
- Optimizer: Optimizer to be used, e.g. Adam.  
- Trainer: The main class which runs the epochs and saves checkpoints. 
### execution
 `python run_training.py <train_module> <train_name>`
  - call run() function in module: ltr.train_setting.<train_module>.<train_name>
  - store training procedure in directory checkpoints/ltr/<train_module>/<train_name>
 `run() function in train_setting module`
  - announce **settings** struct
  - **data** initial/compose/processing  
    (ltr.datasets.<dataset_module>, ltr.data.transforms, ltr.data.processing)
  - initial **sampler**  (ltr.data.sampler)
  - initial **Loader**  (ltr.data.LTRLoader)
  - initial **Actor**  (ltr.actors.tacking.<actor_name>)
  - initial **LTRTrainer**
  - start trainer.train()

## HCAT as an example tracker
  * [HCAT github](https://github.com/chenxin-dlut/HCAT/tree/main)
  * [LaSOT HuggingFace download page](https://huggingface.co/datasets/l-lt/LaSOT/tree/main)
  I migrate HCAT to pytracking LTR training framework as an example with LaSOT dataset training
  
  - step 1. set up training procedure
    - ltr/train_setting/hcat/hcat.py
      - initial settings
    - call datasets module (lasot), data augmentation (transfoms), data processing
    - initial **hcat sampler**
    - initial LTRLoader
    - initial **net** (model structure also need **backbone**) and **objective** (loss) to initial **hcat Actor**
    - initial trainer(LTRTrainer) with actor, dataloader, optimizer(torch), lr_scheduler
  - step 2. build up hcat sampler
  - step 3. build up hcat net and objective(loss)
  - step 4. build up hcat actor
  - step 5. modified hcat training procedure which is different from pytracking ltr framework