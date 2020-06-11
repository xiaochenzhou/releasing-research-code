# My Paper Title

This repository is the official implementation of [Federated Kernel k-Means: A Privacy Preserving and Communication Efficient Approach]. 


## Requirements

To install requirements:

```setup
pip install -r requirements.txt
```


## Training and Evaluation

In the experiment of this paper, one Coordinator process and five Worker processes are generated to simulate the cloud server and five users' devices, respectively.

To prepare a dataset (e.g., the Mushrooms dataset) for training, the features of the dataset needs to be partitioned into five parts  (and the label are partitioned accordingly). Each part is saved as a '.npy' file (e.g., one part of the features is saved as 'mushroom_feature1.npy' and the corresponding part of the labels is saved as 'mushroom_label1.npy'). These files are stored in a path whose name is the name of the dataset (e.g., the files of the Mushrooms dataset are stored in the path ./mushroom/).

To train the model over the Mushrooms dataset, run this command:

```train
mpiexec -n 6 python train.py --n_clusters 2 --n_components 15 --n_nodes 5 --gamma 0.011935614675340699 --dataset mushroom --index 0 --n_dim 4 --n_iterations 50
```

To train the model over the MNIST dataset, run this command:

```train
mpiexec -n 6 python train.py --n_clusters 10 --n_components 200 --n_nodes 5 --gamma 0.0028533628985793905 --dataset mnist --index 0 --n_dim 12 --n_iterations 50
```

To train the model over the Covtype dataset, run this command:

```train
mpiexec -n 6 python train.py --n_clusters 7 --n_components 30 --n_nodes 5 --gamma 0.05098145937100924 --dataset covtype --index 0 --n_dim 10 --n_iterations 50
```
The evaluation part is included in `train.py`, and it will output a normalzed mutual inforation (NMI) score of the trained model.
## Results

Our model achieves the following average NMI socres after 50 iterations:

| Dataset name       |  Mushrooms  |    MNIST    |   Covtype   |
| ------------------ |-------------|-------------|-------------|
| Average NMI score  |    0.545    |    0.473    |    0.141    |


