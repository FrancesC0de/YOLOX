## Introduction

This repository contains the code for testing YOLOX-nano on a subset of 10 classes of the Google Open Images Dataset.<br/>
An example of final result:<br/><br/>
![Alt Text](https://github.com/FrancesC0de/YOLOX/blob/main/test_veges.gif)


## Installation

* download the library for collecting the selected classes from the Google Open Images Dataset

```
    !git clone https://github.com/EscVM/OIDv4_ToolKit
    !pip3 install -r requirements.txt
```

* download the train/validation/test sets

```
    !python3 main.py downloader --classes Coffee Broccoli Sushi Pizza Egg Lemon Carrot Grape Banana Cucumber --type_csv train --multiclasses 1
    !python3 main.py downloader --classes Coffee Broccoli Sushi Pizza Egg Lemon Carrot Grape Banana Cucumber --type_csv validation --multiclasses 1
    !python3 main.py downloader --classes Coffee Broccoli Sushi Pizza Egg Lemon Carrot Grape Banana Cucumber --type_csv test --multiclasses 1
```

* copy the downloaded images in your Google drive to this path:

```
    /content/drive/MyDrive/open-images-v4
```

* download the tool for VOC conversion

```
    !git clone https://github.com/AtriSaxena/OIDv4_to_VOC.git
    !pip3 install -r requirements.txt
```

* change the Google Open Image Dataset labels format from txt to separate xml files (VOC format)

```
    !python3 OIDv4_to_VOC.py --sourcepath Dataset/train/Coffee_Broccoli_Sushi_Pizza_Egg_Lemon_Carrot_Grape_Banana_Cucumber --dest_path      Dataset/train/Annotation/Coffee_Broccoli_Sushi_Pizza_Egg_Lemon_Carrot_Grape_Banana_Cucumber/xml
    !python3 OIDv4_to_VOC.py --sourcepath Dataset/validation/Coffee_Broccoli_Sushi_Pizza_Egg_Lemon_Carrot_Grape_Banana_Cucumber --dest_path Dataset/validation/Annotation/Coffee_Broccoli_Sushi_Pizza_Egg_Lemon_Carrot_Grape_Banana_Cucumber/xml
    !python3 OIDv4_to_VOC.py --sourcepath Dataset/test/Coffee_Broccoli_Sushi_Pizza_Egg_Lemon_Carrot_Grape_Banana_Cucumber --dest_path Dataset/test/Annotation/Coffee_Broccoli_Sushi_Pizza_Egg_Lemon_Carrot_Grape_Banana_Cucumber/xml
```

* convert from VOC to COCO json format

```
  !python voc2coco.py Dataset/train/Coffee_Broccoli_Sushi_Pizza_Egg_Lemon_Carrot_Grape_Banana_Cucumber/xml train.json
  !python voc2coco.py Dataset/validation/Coffee_Broccoli_Sushi_Pizza_Egg_Lemon_Carrot_Grape_Banana_Cucumber/xml train.json
  !python voc2coco.py Dataset/test/Coffee_Broccoli_Sushi_Pizza_Egg_Lemon_Carrot_Grape_Banana_Cucumber/xml train.json
```

* now you can run the YoloXnano_test notebook!
