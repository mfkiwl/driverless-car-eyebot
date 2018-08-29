# driverless-eyebot
**Note:This project is based on eyebot system develop by The Univ. of Western Australia, so if you want to use it you should replace the eyebot API code(controlling the motor) by your own function.**

Carolo-Cup is an international autonomous driving competition held in German annually. Student teams need to compete with each other about the new ideas and actual performance of their driverless model vehicles. The test platform built by Technische Universität Braunschweig contains different scenarios, so it can well simulate the real-life situation. In other words, although this is a model, the experience gained from solving problems in the model world can be very helpful to the realistic environment and this is the most fascinating part of this game.This project has done the lane detection, traffic sign detection and classification and communication between eyebots and base station.

## prepare for building
1. make sure you have install cmake.
2. download `dlib` from https://github.com/davisking/dlib/tree/7ef7ba84b32651ae920f32935baf1a15fb65e204, and put it in your root folder.


## How to build
1. stand in your root folder
2. run `mkdir build`
3. run `sh make`
4. if you want to add new source file add it in `CMakeList`. And the source file should be included in `src` folder.
5. the executing file will be stored in the `build` folder. 

## Mark signs on traffic sign images
1. Compile `imglab`:

```
cd dlib/tools/imglab
mkdir build
cd build
cmake ..
cmake --build .
```

2. Create XML from sample images:

```
dlib/tools/imglab/build/imglab -c images/pare/training.xml images/pare/train/*.(jpg|jpeg|png)
dlib/tools/imglab/build/imglab images/pare/training.xml
dlib/tools/imglab/build/imglab -c images/pare/testing.xml images/pare/test/*.(jpg|jpeg|png)
dlib/tools/imglab/build/imglab images/pare/testing.xml
```

3. Use `shift+click` to draw a box around signs.

## Train the fHOG detector

To train a fHOG detector, run `build/hog_detector`. For example, to run the detector on the `image/stop/` folder in the verbose mode,  execute the following command: 

```
build/hog_detector -v images/stop/
```

The detector will be saved to the file `detector.svm`. To change the file, use the `--detector-name` option.

Run `build/hog_detector -h` for more details.

## if you want to view traffic sign detection results on computer

use the parameter `--wait` to wait for user input to show next image.

```
build/detect --wait exam/*.jpg
```

lane detection;

traffic sign detection and classification;

using cmake to compile;

