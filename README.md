# Peridot

This notebook implements PERIDOT, a quick execution time prediction tool for Spark Applications. Apart from extracting the model parameters required for PERIDOT, the script also provides a set of functions for extracting and analyzing different task features such as mean and median shuffle write time, executor deserialize CPU time, executor deaserialize time, scheduler delay, executor CPU run time and executor run time.

## Description
This script takes two inputs in Cell 23, `ref1` and `ref2`, as the path for the Spark log file of the two references required by PERIDOT and the `number of cores` on which the two experiments are run, which should preferably be the same. These two references should be run on two different data sizes to help identify the variable stages. Using these two references, the script extracts the number of stages in the application, the duration of each stage in the two references, the launch times of each stage and the number of tasks(partitions) in each stage. Based on these values, it identifies the variable, constant and parallel stages (if any) and then extracts the parameters needed to model execution time behavior of the application under study. These parameters involve the mean wave time of each of the variable stages and the aggregate time for the constant stages. For making predictions for an unknown experiment, it takes the `data size` and the `number of cores` required for the experiment as input and uses it to output the `execution time` that the application will take in the specified data-core configuration. Thus, PERIDOT can get execution time predictions for Spark in a matter of seconds.

## Experiment Data
The log files collected in our experiments are [available](https://drive.google.com/drive/folders/11q84KEDc_ozurvZgXhqOi5AuyK6G9gRk).

## Related Work
S. Shah, Y. Amannejad, D. Krishnamurthy, and M. Wang. ["Quick Execution Time Predictions for Spark Applications,"](https://pdfs.semanticscholar.org/e174/b68290e9ca9b81bf6ab8eb470c1955aa5d15.pdf) Proceedings of the 15th International Conference on Network and Service Management (CNSM 2019), Halifax, NS, October 2019. 

## Citation
```
@inproceedings{shah2019quick,
  title={Quick Execution Time Predictions for Spark Applications},
  author={Shah, Sarah and Amannejad, Yasaman and Krishnamurthy, Diwakar and Wang, Mea},
  booktitle={2019 15th International Conference on Network and Service Management (CNSM)},
  pages={1--9},
  year={2019},
  organization={IEEE}
}
  ```

 ## License
Free for academic research use, as long as proper attribution is given and this copyright notice is retained. Contact us for commercial use (or rather any use that is not academic research) (Email: sarah.shah1 at ucalgary domain dot ca).
  
 ## Attributions/Thanks
We also thank David Schulz for his support with the [ARC cluster](https://hpc.ucalgary.ca/quickstart/arc)
