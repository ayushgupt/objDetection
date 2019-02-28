# Instructions for running on test data to get MAP values
- Need to convert data in '.record' format which can be done using line below:   
  python generate_tfrecord.py --csv_input=data/train_labels.csv  --output_path=./train.record --image_dir=data/img
- Download trained model zip from owncloud into 'trainingfolder'
- Change the number of images to be evaluated in the config file in trainingfolder  
- Use eval.py like this:   
  python3 eval.py --checkpoint_dir=./models/train/ --eval_dir=./legacyEval/ --pipeline_config_path=./ssd_mobilenet_v1_coco.config
  

### More Code snippets used
- export PYTHONPATH=$PYTHONPATH:/home/satbigvm/cleanedDataset/objDetection/models/research:/home/satbigvm/cleanedDataset/objDetection/models/research/slim
- python3 train.py --logtostderr --train_dir=./models/train --pipeline_config_path=ssd_mobilenet_v1_coco.config
- python3 export_inference_graph.py --input_type image_tensor --pipeline_config_path ./ssd_mobilenet_v1_coco.config --trained_checkpoint_prefix ./models/train/model.ckpt-996 --output_directory ./fine_tuned_model_996
### Code details
Almost the whole of code is taken from https://github.com/tensorflow/models/ and changes are done to config files as per need.  
The file to change csv to record format is taken from https://github.com/datitran/raccoon_dataset  
