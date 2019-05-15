Use [this link](https://mega.nz/#F!Z4Z3gAzb!KI48uGHJJza90DP7-Kz1kA) to download the precomputed representations for one of the datasets used in the paper.

### Compute:
#### Global Image Descriptors:

We used [NetVLAD](https://arxiv.org/abs/1511.07247) image descriptors to match the reference and query image datasets, and retrieve the top-N matches.

The source code is provided by the authors in [MATLAB](https://github.com/Relja/netvlad). There also exists a [Python](https://github.com/uzh-rpg/netvlad_tf_open) port of the same.

The *4096*-dimensional image descriptors for a given dataset are stored as an array in .npz format in `seq2single/precomputed/kpDesc_C5Tensor/`.


#### Dense Conv5 Tensor for Local Keypoint and Descriptor Extraction
We used [RefineNet](https://arxiv.org/abs/1611.06612) - trained on the Cityscapes dataset for semantic segmentation - to extract local keypoints and descriptors from its last convolutional layer, as described in [this paper](http://www.roboticsproceedings.org/rss14/p22.pdf).

The source code is provided by the authors in [MATLAB](https://github.com/guosheng/refinenet). There also exists a [Python](https://github.com/Attila94/refinenet-keras) port of the same.

The conv 3D tensor of shape: [*numRows,numCols,numFeatureMaps*] for every image in a dataset is stored separately in .npz format in `seq2single/precomputed/imgGlobalDesc/`.


#### Single-View Depth Estimation
We used [UnDEMon](https://arxiv.org/abs/1809.00969) - trained on KITTI dataset - for generating depth masks for the reference imagery.

The source code is provided by the authors in [Python](https://github.com/madhubabuv/undemon).

The predicted depth images have the same resolution as the input images and are stored as an array in .npz format in `seq2single/precomputed/depthData/`.
