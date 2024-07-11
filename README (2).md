
# PROJECT UAS PENGOLAHAN CITRA 2024







## Authors

- [@angelnatassya](https://www.github.com/angelnatassya)


## Aplikasi

 Menggunakan aplikasi Jupiter Notebook pada Anaconda Navigator.
 
 Library yang digunakan :
 ``` bash
import cv2
import matplotlib.pyplot as plt
import numpy as np 
```
1. Menampilkan Citra Asli
``` bash
image_path = 'pict.jpg'
image = cv2.imread(image_path)
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
```
``` bash
plt.imshow(image)
plt.title("Citra Asli")
plt.axis('off')
plt.show()
```