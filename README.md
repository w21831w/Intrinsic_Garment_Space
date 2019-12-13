### Learning an Intrinsic Garment Space for Interactive Authoring of Garment Animation

***



### Overview

***

This is the demo code for training a motion invariant encoding network. The following diagram provides an overview of the network structure.

For more information, please visit http://geometry.cs.ucl.ac.uk/projects/2019/garment_authoring/ 

<img src=".\resource\network.png" alt="network" width=600 />



### Structure

***

The project's directory is shown as follows. The data set is in the `data_set` folder, including cloth mesh(generated by Maya Qualoth), garment template, character animation and skeletons. Some supporting files can be found in `support`. The shape feature descriptor and motion invariant encoding network are saved in `nnet`.



```
├─data_set
│  ├─anim
│  ├─case
│  ├─garment
│  ├─skeleton
│  └─Maya
├─nnet
│  ├─basis
│  └─mie
├─support
│  ├─eval_basis
│  ├─eval_mie
│  ├─info_basis
│  └─info_mie
└─scripts
```



In the `scripts` folder, there are several python scripts which implement the training process. We also provide a data set for testing, generated from a sequence of dancing animation and a skirt.



### Data Set

***

The data set includes not only the meshes and garment template, but also some supporting information. You can check the animation in the `Maya` folder. The animation information is saved in the `anim` folder. In the `case` folder, there are many meshes generated by Qualoth in different simulation parameters. The garment template is in the `garment` folder.  

<img src=".\resource\1.png" alt="network" width=800 />   



### Installation

***

- Clone the repo:

```
git clone https://github.com/YuanBoot/Intrinsic_Garment_Space.git
```

- Install PyTorch
- Install  tqdm (https://tqdm.github.io/)





### Model Training

***



#### Shape Descriptor

After all preparing works done, you can start to train the network. In `scripts` folder, some scripts named `basis_*` are used for training shape descriptor. 

Run them as follows:

`01.basis_prepare.py` (data preparing)

`02.basis_train.py` (training)

`03.basis_eval.py` (evaluation)

After running 01 and 02 scripts, there will be a `*.net` file in the `nnet/basis` folder. It is the shape feature descriptor.

The result of a specific frame after running `03.basis_eval.py` script. The yellow skirt is our output and the blue one is the ground truth. If the loss of the descriptor is low enough, these two skirt are almost overlap.

<img src=".\resource\f2.png" alt="f2" width=300 />



#### Motion Invariant Encoding

Then, you can run `mie_*.py` scripts to get the motion invariant encoding network. 

`04.mie_prepare.py` (data preparing)

`05.mie_train.py` (training)

`06.mie_eval.py` (evaluation)

If everything goes well, the exported mesh would be like the following figures. For the output from`06.mie_eval.py` is painted by red and the green one is the ground truth.

<img src=".\resource\f3.png" alt="f3" width=300 />