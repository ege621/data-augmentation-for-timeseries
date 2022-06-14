# data-augmentation-for-timeseries

This pipeline augments a data in the form of X = (batch size , sequence length , number of features) and y = (batch size , number of classes) by generating a randomly distributed noise matrix.

The matrix is created freshly for every instance to ensure proper randomness. 

The noise matrix is multiplied with X elementwise and added to X. 

Considering that y is one hot encoded, it is repeated consecutively for every instance of X.

# How to use

1. If you are going to use this augmentation technique for machine learning tasks (which is most probably), be sure that your original data is randomly distributed. This pipeline cannot make a non-normally distributed data normally distributed.

2. Pick your values for mu and sigma, which are the average value and standard deviation values for the noise matrix to be created. If your original data is skewed, you might want to try bringing it to mu = 0 by introducing a non-zero value for mu while augmenting. The standard deviation basically determines the aggressiveness of the augmentation. Do not pick a large value for this as it can make your data fall beyond the bounds of [-1,1].

3. Determine for how many iterations you want to augment by setting the iterations variable. The resulting dataset will contain a batch size of iterations * batch size.

4. After you have loaded your dataset as X and y, run and observe the shapes.

# Important things to note while using

The augmented dataset is stored purely on RAM before saving it. You might need to do some trial runs for the iterations variable before your RAM explodes. 

Mind the structure of your folders and dataset file extensions. This pipeline will search for X and y under a folder called dataset, and it will search purely for previously saved numpy arrays with the extension .npy. It will save as .npy also. 

You can try with a dummy dataset that I provided. Be sure to adjust your folder structure as described in the previous step. 

