
## Custom MNIST Digits.

```
This repository contains a sample(80) of Custom datasets generated using the following Process
```

### Generated Datasets 
- Data collection
- Steps taken for image creation:
  1. Utilized Microsoft Word version 10.
  2. Used the "draw with trackpad" option in the drawing tab of Microsoft Word.
  3. Screenshots of each digit were taken.
  4. Grouped screenshots into batches of 10.
  5. Each batch contained digits from 0 to 9.
  6. The name of the image was the gold label of the represented digit.For example 10 means the Image is of 1st batch and the digit is 0.
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

