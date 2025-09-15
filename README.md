# DSPA-MIL
"Dual Selective Gleason Pattern-Aware Multiple Instance Learning with Uncertainty Regularization for Grade Group Prediction in Histopathology Images"  
Submit to Medical Image Analysis (MedIA)  
Incomplete version

### 🔨 **Code Framework**
`DSPA-MIL` is constructed by the following parts：
- `/configs:` DSPA-MIL defines MIL models through a YAML configuration file.
- `/modules:` Defined the network architectures of different MIL models.
- `/process:` Defined the training frameworks for different MIL models.
- `/split_scripts:` Supports different dataset split methods.
- `/datasets:` User-Datasets path information.
- `/utils:` Framework's utility scripts.
- `train_mil.py:` Train Entry function of the framework.
- `test_mil.py:` Test Entry function of the framework.

### :fire: **Train/Test MIL**
#### **Yaml Config**
You can config the yaml-file in `/configs`. For example, our `DSPA-MIL`: `/configs/STA_MIL.yaml`, A detailed explanation has been written in  `/configs/STA_MIL.yaml`. 
#### **Train & Test**
Then, `/train_mil.py` will help you like this:
``` shell
python train_mil.py --yaml_path /configs/STA_MIL.yaml 
```
We also support dynamic parameter passing, and you can pass any parameters that exist in the `/configs/STA_MIL.yaml` file, for example:
``` shell
python train_mil.py --yaml_path /configs/STA_MIL.yaml --options General.seed=2024 General.num_epochs=20 Model.in_dim=768
```
The `/test_mil.py` will help you test pretrained MIL models like this:
``` shell
python test_mil.py --yaml_path /configs/STA_MIL.yaml --test_dataset_csv /your/test_csv/path --model_weight_path /your/model_weights/path --test_log_dir /your/test/log/dir
```
You should ensure the `--test_dataset_csv` contains the column of `test_slide_path` which contains the `/path/to/your_pt.pt`. If `--test_dataset_csv` also contains the 'test_slide_label' column, the metrics will be calculated and written to logs.
