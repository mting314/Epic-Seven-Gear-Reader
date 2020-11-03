# Epic Seven Gear Reader

## This project has moved
If you want what in my opinion is the best version, check out [this version](https://e7gears.herokuapp.com/index), which takes video input instead and is a lot more accurate thanks to [Tesseact training](https://tesseract-ocr.github.io/tessdoc/TrainingTesseract-4.00.html).

## Introduction

These programs use `pytesseract` to OCR screenshots of Epic Seven gear to help import your gear into Gear Optimizers like [u/HyrTheWinter's popular one ](https://eseo-8a854.firebaseapp.com/) or [this more recent Windows application one](https://github.com/Zarroc2762/E7-Gear-Optimizer/releases).

This is an older version of the Epic Seven Gear Reader project where I only been OCR'ing screenshots, not video. I've heard some people prefer it this way, and other want to mess around with the code themselves, so I'm creating this repository where I cleaned up some of my older code for this project and put it into Jupyter Notebooks so that people can mess around and follow along easier. There are two notebooks:

* `E7 Gear OCR Main.ipynb`, which you should use if you just want the code that will process all the screenshots in the `screenshots` folder
* `E7 Gear OCR Tutorial.ipynb`, which contains an indepth explanation of the condensed code in the Main notebook, and shows the intermediate steps of image processing like cropping and thresholding.

## Setup

1. Make sure you have have [Tesseract](https://github.com/UB-Mannheim/tesseract/wiki) installed.

2. Once you have Tesseract, you can install Python's Tesseract wrapper.

    ``pip install pytesseract``

    While you're at it, you'lll also need Python's OpenCV package as well.

    ``pip install pytesseract``

### If you're using the `Main` notebook

3. I recommend testing first before copying in all your screenshots, so in the directory `/screenshots`, just try copying in a single one, or use the one that I left as an example. Check that you can see the console logging things like 

    ```1 exported out of 1 valid item ```

    and that the resulting JSON matches what you see in your test image.

7. Delete the sample image in the screenshots folder (it defaults to ``/screenshots``, but you can change the variable ``screenshot_path`` variable to whatever you want) that we just tested the script on.

8. Copy your 2200x1080 gear screenshots to your screenshots folder from wherever you have them stored.

### If you're using the Tutorial notebook
3. I recommend against changing the example image I have in my notebook just because a lot of the parts where I say that an image processing thing doesn't come out right, might actually come out right, which would be weird in my discussyion around the cells haha.

4. So just run all the cells, one at a time if you prefer to follow along.

## Screenshots

* A very important point about how this script works is that you need screenshots that are 2200x1080. I normally use Nox which is nice because you can change the resolution, and I normally play at 1920x1080.

## Disclaimer

* OCR'ing is often prone to many mistakes, what with image noise or just something funky. Luckily most of these images are consistent, and there are checks in place in the code to make sure for instance the equipment rarity is not 0 or something. However, there are some error that are impossible to check, like random 7's being added onto the end of numbers, which seems to happen a lot. This could result in a speed substat of 2 being read as 27. Therefore, I suggest just going through the resulting JSON and making sure nothing looks fishy.