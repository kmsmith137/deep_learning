
### Documentation

     - [Install](https://www.tensorflow.org/install/)
     - [Get started](https://www.tensorflow.org/get_started/)
     - [Programmer's guide](https://www.tensorflow.org/programmers_guide/)
     - [Tutorials](https://www.tensorflow.org/tutorials/)

### Install notes

   - `export TF_CPP_MIN_LOG_LEVEL=2` to suppress warning "Your CPU supports instructions that this TensorFlow binary was not compiled to use..."

### tensorflow/models

   Currently, [tensorflow/models](https://github.com/tensorflow/models/) is not an importable python module.
   A fix is [in the works](https://github.com/tensorflow/models/issues/917), but in the meantime I'm using
   the following hackery:
   ```
   # 'git clone' to git/tf_models/tf_models, with wrapper directory git/tf_models.
   # This will be convenient below.
   mkdir ~/git/tf_models
   cd ~/git/tf_models
   git clone https://github.com/tensorflow/models tf_models

   # Add empty __init__.py
   cd ~/git/tf_models/tf_models
   touch __init__.py

   # Probably want to put this in ~/.bashrc or ~/.bash_profile
   export PYTHONPATH=$PYTHONPATH:$HOME/git/tf_models

   # Test that it worked.  (After starting the tensorflow virtualenv!)
   # The MNIST data will be downloaded to /data/kmsmith/mnist, if it does not exist already.
   python
   import tf_models.official.mnist.dataset
   print tf_models.official.mnist.dataset.train('/data/kmsmith/mnist')
   print tf_models.official.mnist.dataset.test('/data/kmsmith/mnist')
   ```
