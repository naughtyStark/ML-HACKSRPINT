# ML-HACKSRPINT
ML-HACKSPRINT DSC BVP tensorflow watch party hackathon code

## IDEA 
The theme chosen for this project was entertainment. 

Tensorflow's deep dreamer is famous for generating trippy and artistic images from as little definite information as random noise and works like a charm on actual images : 

![the-starry-night-800x450](https://user-images.githubusercontent.com/24889667/54002515-d9f16b00-4174-11e9-951f-5cad45c6fd85.jpg)

                                                     original image 

![dream_image_out](https://user-images.githubusercontent.com/24889667/54002526-e4ac0000-4174-11e9-8dac-bdd391860df3.jpg)

                                                     transformed image 

An audio file can be seen as an array. 1 second of an audio file generally has 44100 values which is = 210 x 210 ( From what I know, this is a complete coincidence.. or is it? (X files theme song starts playing in the background) )

I used the deep-dreamer as an adhoc "transformer". 

![original](https://user-images.githubusercontent.com/24889667/54002272-fd67e600-4173-11e9-9990-bac587a9e047.jpg)

Original audio, reshaped to 210x210x3. This image represnts a 3 second block of the audio file where each second forms either the R,G or B component (notice that there's very little color in these images. This may be because the "beats" tend to line up in time for the most part).

![transformed](https://user-images.githubusercontent.com/24889667/54002274-02c53080-4174-11e9-95cb-f5cc79db16a3.jpg)

transformed audio. The output retains most of the original pattern but does add some changes and at the same time brings in color. The color (in my opinion) represents the intentional slight mis-alignment of the beats. The blurring of the image adds a bit of noise(god only knows how I got away with that)

now the results aren't out of this world. Initially, it appears to simply be adding white noise (if you run it over the entire audio file). However, that may not necessarily be the case because in order to construct one RGB image, we look 3 seconds into the future( 3 seconds at a time are transformed ). When it performs a transformation, the transformation at the current time instant is in a way linked to the original value 1 second and 2 second into the future. This effect is more prominent (and appreciable) around beat drops. 

Do note that the method does not alter the underlying notes of the audio file.

# NOTE:
For best experience please use bass boosted earphones

## SCOPE OF USE : 
The applications for this are not limited to entertainment, however, this was created for the purposes of boosting the entertainment industry. This isn't a perfect end product yet (since I only have 0 hours of past experience in sound engineering). However, in the future, you could remix your music using image based AI to introduce new sounds into an already poppy song.  

## FUTURE USE :
Since Google DeepDream itself is a way for running the neural network , it is not tight to a specific architecture. It is an approach that you can achieve by any pre-trained deep convolutional neural network. The network may be trained later to perform more specific alterations while still working with the music as a sequence of images.

## HOW TO USE :
the code is not super user friendly just yet. You have to provide the audio file as a .wav file. The name of the file has to be given in the code itself. This can be changed easily in the future to take the name of the file from command line or if you have a gui, then from the gui. I didn't work on it because of the shortage of time.

You will require this package : https://pythonprogramming.net/static/downloads/machine-learning-data/deep_dreaming_start.zip
extract it and put it in your python working directory. Place the rest of these files in the extracted folder

Preferred song : Songs that sound like ODESZA - Loyal

STEP 1 : 
in the code, find the line :
data,fs = sf.read('',dtype='float32')
and place the name of the file in there along with the path if it isn't in the same directory

Tuning : the person creating the remix will have to adjust the delays/mix timings. This is the only thing they have to do, the rest is done by the algorithm.

STEP 2: 
execute the code from command line :
python main.py

STEP 3:
done. the audio file will be saved in the same directory as main.py


