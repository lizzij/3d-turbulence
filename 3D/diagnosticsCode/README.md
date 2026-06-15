A.T.M: I am adding the hdf5 file containing 100 temporal snapshots of the dataset which is of size 128^3.

You can read it by:
```py
import h5py
f = h5py.File(pathToFile,'r')
fields = f['fields']
snapshots = 50
data = fields[:snapshots,:,:,:,:3]
```

Where snapshots is the number of snapshots you want to load (max is 100, and I choose 50 for my compression) and the last array is the number of fields in the data. The data has 3 components of velocity and 2 scalar fields. Total = 5.

Currently lets focus on just compressing the first 3 fields i.e. the velocity, which you can see in the code snippet above.

diagnosticsCode dir:

Inside this dir, create another dir called “diagnostics” as per the “computeDiagnostics.py” code.. Then run it after replacing the filepath. This should save the 3 diagnostic tests (which I use in my papers) in the diagnostics dir. Then run plot_all.py with the right path to plot the results.

The computeDiagnostics.py has 2 variables :  dns and mod. Dns is test data and mod is the model prediction, for which diagnostics are computed. Currently I am loading the test dat for both dns and mod. Replace mod with the output of your neural network, and everything else should work as intended. 

