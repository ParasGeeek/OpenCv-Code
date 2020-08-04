https://divyanshushekhar.com/lane-detection-opencv-python/

https://divyanshushekhar.com/motion-detection-opencv/

https://divyanshushekhar.com/line-detection-opencv-python/

https://divyanshushekhar.com/background-subtraction-opencv/

https://divyanshushekhar.com/transition-effect-opencv/

https://divyanshushekhar.com/image-blending-opencv/

https://divyanshushekhar.com/contours-opencv-python/

https://divyanshushekhar.com/blob-detection-opencv-python/

https://divyanshushekhar.com/object-tracking-opencv/

https://divyanshushekhar.com/mouse-events-opencv/

https://divyanshushekhar.com/background-subtraction-opencv/

https://divyanshushekhar.com/trackbar-opencv-python/

https://divyanshushekhar.com/live-sketch-opencv-python/

https://divyanshushekhar.com/image-manipulation-opencv-python/


************Converstion from image database into csv file*********
from PIL import Image
import numpy as np
import sys
import os
import csv

def createFileList(myDir, format='.jpg'):
    fileList = []
    print(myDir)
    for root, dirs, files in os.walk(myDir, topdown=False):
        for name in files:
            if name.endswith(format):
                fullName = os.path.join(root, name)
                fileList.append(fullName)
    return fileList

# load the original image
myFileList = createFileList('/home/paras/PycharmProjects/HelloWorld/cropped_face')

for file in myFileList:
    print(file)
    img_file = Image.open(file)
    width, height = img_file.size
    format = img_file.format
    mode = img_file.mode
    img_grey = img_file.convert('L')

    value = np.asarray(img_grey.getdata(), dtype=np.int).reshape((img_grey.size[1], img_grey.size[0]))
    value = value.flatten()
    print(value)
    with open("image_to_csv_again.csv", 'a',newline='') as f:
        writer = csv.writer(f)
        writer.writerow(value)
