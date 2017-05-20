# dark-vador-or-oby-wan
Program that detect if the image is Dark Vador or Oby Wan. Works with Tensorflow.
This readme is a personal memo. Tutorial can be found [here](https://www.youtube.com/watch?v=QfNvhPx5Px8)
### container
I used the [Tensorflow Docker container](https://hub.docker.com/r/tensorflow/tensorflow/):

```
docker run -it gcr.io/tensorflow/tensorflow:latest-devel
```
### dataset

After that, you need to download your datasets. They can be downloaded on Google Images. With the following [Chrome extension](https://chrome.google.com/webstore/detail/fatkun-batch-download-ima/nnjjahlikiabnchcpehcpkdeckfgnohf) you can download all the images on the page. You can do that, like me, with Dark Vador and Oby Wan pictures. But you can also download cat and dog pictures. It doesn't matter :).
Put every dataset in a different folder.

```
dataset
└──dark-vador
│  │  file1.jpg
│  │  file2.jpg
│  
└──oby-wan
   │  file1.jpg
   │  file2.jpg
```

### upload the dataset to the container
To upload the datasets to the container you can use the following command:

```
docker cp /path/to/folder/dataset containerid:/path/to/dataset

```
### retrain
To retrain the algorithm, run this command:

```
python /tensorflow/tensorflow/examples/image_retraining/retrain.py --bottleneck_dir=/path/to/bottleneck --how_many_training_steps 4000 --model_dir=/path/to/inception --output_graph=/path/to/retrained_graph.pb --output_labels=/path/to/retrained_labels.txt --image-dir /path/to/dataset
```
### run the code

```
python run.py /path/to/image/to/test.jpg /path/to/retrained_labels.txt /path/to/retrained_graph.pb
```
