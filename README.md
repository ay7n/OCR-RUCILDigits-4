
## Custom MNIST Digits.

```
This repository contains a sample(80) of Custom datasets generated using the following Process
```

### Generated Datasets 
- Data collection
- Steps taken for image creation:
  - Utilized Microsoft Word version 10.
  - Used the "draw with trackpad" option in the drawing tab of Microsoft Word.
  - Screenshots of each digit were taken.
  - Grouped screenshots into batches of 10.
  - Each batch contained digits from 0 to 9.
  - The name of the image was the gold label of the represented digit.For example 10 means the Image is of 1st batch and the digit is 0.
- Data Preprocessing
- Steps to ensure accuracy and clarity of the handwritten number image:
   - Convert image to binary format (black or white pixels) using "L" mode
   - Create a 28x28 white canvas, the standard size for MNIST images
   - Resize the image to a maximum dimension of 20 pixels while maintaining proportions
   - Apply antialias function to improve image quality and smooth jagged edges
   - Paste resized image onto the white canvas, centering it with 4 pixels from the top or side
   - Adjust pixel values to a range of 0 to 1, with 1 representing black and 0 representing white
- Resulting image is clear, accurate, and easier to analyze and process.


### Requirements
```
Python3
PIL library
Microsoft Word
```

### To View the image use the following code
```
import numpy as np
from matplotlib import pyplot as plt

zero = np.load("10.npy")
zero  = zero.reshape(28,28)

plt.imshow(zero)
plt.show()
```


### Sample digit visualization
<img src = "https://github.com/ay7n/OCR-RUCILDigits-4/blob/main/zero.png">

### To Convert images to numpy format
```
def imageprepare(argv):
    """
    This function returns the pixel values.
    The input is a file location.
    """
    im = Image.open(argv).convert('L')# Load the image of my handwritten number and Convert the image to black and white
    width = float(im.size[0])
    height = float(im.size[1])
    newImage = Image.new('L', (28, 28), (255))  # creates white canvas of 28x28 pixels

    if width > height:  # check which dimension is bigger
        # Width is bigger. Width becomes 20 pixels.
        nheight = int(round((20.0 / width * height), 0))  # resize height according to ratio width
        if (nheight == 0):  # rare case but minimum is 1 pixel
            nheight = 1
            # resize and sharpen
        img = im.resize((20, nheight), Image.ANTIALIAS).filter(ImageFilter.SHARPEN)
        wtop = int(round(((28 - nheight) / 2), 0))  # calculate horizontal position
        newImage.paste(img, (4, wtop))  # paste resized image on white canvas

    else:
        # Height is bigger. Heigth becomes 20 pixels.
        nwidth = int(round((20.0 / height * width), 0))  # resize width according to ratio height
        if (nwidth == 0):  # rare case but minimum is 1 pixel
            nwidth = 1
            # resize and sharpen
        img = im.resize((nwidth, 20), Image.ANTIALIAS).filter(ImageFilter.SHARPEN)
        wleft = int(round(((28 - nwidth) / 2), 0))  # caculate vertical pozition
        newImage.paste(img, (wleft, 4))  # paste resized image on white canvas #getdata() Returns the contents of this image as a sequence object containing pixel values.

    tv = list(newImage.getdata())  # get pixel values
    tva = [(255 - x) * 1.0 / 255.0 for x in tv]
    return tva
```



