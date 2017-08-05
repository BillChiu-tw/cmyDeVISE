# mscoco-search extends devise-rnn

## Changes to the devise-rnn branch to train an image search engine using mscoco dataset.

The project uses the following python packages over the conda python stack:
- tensorflow 1.1.0
- keras 2.0.6
- tensorboard 1.0.0a6
- opencv 3.2.0

### SETUP
````
bash SETUP.sh

python extract_word_embeddings.py glove.6B.300d.txt processed_features/embeddings.h5

python scrape_and_save.py /var/coco/annotations/captions_train2014.json TRAIN EVERYTHING

## Ensure DS_Store files are not in the image folders.

python clean_data.py /var/coco/images/train2014

python extract_features_and_dump.py -weights_path vgg16_weights_th_dim_ordering_th_kernels.h5 -images_path /var/coco/images/train2014_clean  -dump_path processed_features/features.h5

## Repeat the above for Validation data.

rm snapshots/* ## Optional.

rm logs/* ## Optional.

python rnn_model.py TRAIN
````

### Changes required:
- scrape_and_save.py pre-process annotations DONE
- extract_features_and_dump.py NO CONCEPT OF CATAGORY, or CLASS DONE
- extract_features_and_dump.py DATA_GENERATOR DONE
- scrape_and_save.py Update the dicts and pkls DONE
- rnn_model.py UPDATES?? DONE
- FIX validation_script.py - TESTING : mscoco_priyam
