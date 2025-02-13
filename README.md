
# PROJECT UAS PENGOLAHAN CITRA 2024






## Authors

- [@angelnatassya](https://www.github.com/angelnatassya)

## Geometrix Citra
Geometrix citra adalah cabang dalam pengolahan citra digital yang berkaitan dengan transformasi geometris atau perubahan bentuk dan orientasi dari objek dalam citra. Tujuan utama dari geometri citra adalah untuk mengubah tampilan atau representasi geometris dari suatu objek dalam citra, baik secara lokal maupun global, tanpa mengubah informasi konten atau struktur esensial dari objek tersebut.

1. Konsep Dasar Geometri Citra:
     - Transformasi Geometris: Melibatkan perubahan posisi, rotasi, skala, dan pergeseran objek dalam citra. Transformasi ini dapat dilakukan untuk menyesuaikan citra dengan sistem koordinat lain atau untuk mengoreksi distorsi geometris        yang disebabkan oleh faktor fisik seperti perspektif.
     
     - Penggabungan Citra (Image Warping): Proses mengubah bentuk atau orientasi objek dalam citra menggunakan transformasi yang sesuai. Contoh umum termasuk transformasi affine untuk memperbaiki distorsi perspektif atau transformasi           non-linear untuk mengoreksi distorsi lensa.
     
     - Registrasi Citra (Image Registration): Proses menyesuaikan dan memadukan dua atau lebih citra dari sudut pandang yang berbeda atau dengan resolusi yang berbeda. Ini dapat melibatkan transformasi geometris untuk mencocokkan fitur         atau objek yang serupa di antara citra-citra tersebut.
  
2. Aplikasi Geometrix Citra:
    - Pemetaan dan Navigasi: Dalam pemetaan digital dan sistem navigasi, geometri citra digunakan untuk mengoreksi distorsi dan mengintegrasikan citra dari berbagai sumber.
      
    - Augmented Reality (AR): Di AR, geometri citra digunakan untuk menyatukan elemen virtual dengan citra dari dunia nyata, membutuhkan koordinasi dan transformasi yang presisi.
      
    - Rekonstruksi 3D: Dalam rekonstruksi citra untuk mendapatkan model 3D dari objek atau lingkungan, geometri citra memainkan peran penting dalam mengatur perspektif dan geometri objek.
      
    - Koreksi dan Enhance Citra: Geometri citra digunakan untuk koreksi distorsi optik dalam fotografi digital atau untuk meningkatkan representasi visual yang lebih akurat dari objek dalam citra.

3. Teknik dan Algoritma:
   - Transformasi Affine: Menerapkan rotasi, translasi, dan skala terhadap objek dalam citra.
    
   - Transformasi Perspektif: Mengoreksi distorsi perspektif untuk menciptakan tampilan datar atau bidang dari objek yang difoto dari sudut pandang yang miring.
    
   - Warping Non-linear: Menggunakan fungsi non-linear untuk mengubah bentuk objek dalam citra, seperti dalam transformasi Morfologi Matematis.
    
   - Registrasi Multi-modal: Menggunakan teknik seperti transformasi Fourier untuk mencocokkan dan memadukan citra dari berbagai modalitas atau waktu yang berbeda.

## Aplikasi

Menggunakan aplikasi Jupiter Notebook pada Anaconda Navigator.

## Project UAS

## Gambar yang Diimport
![[pict.jpg](https://github.com/angelnatassya/uaspcdimages/commit/89cb69b44386ed06f7da8ce197c2270545cdf93f)
](https://github.com/angelnatassya/uaspcdimages/blob/main/pict.jpg)
## Lokasi Pengambilan Gambar
![photo_2024-07-11_18-19-41.jpg](https://github.com/angelnatassya/uaspcdimages/blob/89cb69b44386ed06f7da8ce197c2270545cdf93f/photo_2024-07-11_18-19-41.jpg)

## Source Code dan Penjelasan 
 Library yang digunakan :
 ``` bash
import cv2
import matplotlib.pyplot as plt
import numpy as np 
```
Dokumentasi :

![[image.png](https://github.com/angelnatassya/uaspcdimages/commit/5a782e529352529b6a618173e3b7a239046bc072)
](https://github.com/angelnatassya/uaspcdimages/blob/main/image.png)


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


Dokumentasi :

![https://github.com/angelnatassya/uaspcdimages/blob/main/Screenshot%202024-07-11%20183856.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/Screenshot%202024-07-11%20183856.png)


Penjelasan :
- image_path = 'pict.jpg': Menyimpan path ke gambar yang ingin dibaca. 
- image = cv2.imread(image_path): Membaca image dari path yang telah ditentukan. OpenCV membaca image dalam format BGR (Blue, Green, Red).
- image = cv2.cvtColor(gambar, cv2.COLOR_BGR2RGB): Mengkonversi gambar dari format BGR (default OpenCV) ke format RGB (Red, Green, Blue) yang lebih umum digunakan dalam visualisasi.

  
Output :

![https://github.com/angelnatassya/uaspcdimages/blob/main/Screenshot%202024-07-11%20184000.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/Screenshot%202024-07-11%20184000.png)


2. Gambar Rotasi
``` bash
def rotate_image(image, angle):
    (h, w) = image.shape[:2]
    center = (w / 2, h / 2)
    M = cv2.getRotationMatrix2D(center, angle, 1.0)
    rotated_image = cv2.warpAffine(image, M, (w, h))
    return rotated_image
```
``` bash
rotated_image = rotate_image(image, 45)
plt.imshow(rotated_image)
plt.title("After Rotated")
plt.axis('on')
```

Dokumentasi :

![https://github.com/angelnatassya/uaspcdimages/blob/main/sc%20rotasi.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/sc%20rotasi.png)


Penjelasan :
- image.shape memberikan dimensi gambar dalam bentuk (height, width, channels). image.shape[:2] mengambil dua nilai pertama yaitu tinggi (h) dan lebar (w) gambar.
- center adalah titik pusat rotasi gambar. Ini dihitung sebagai setengah dari lebar dan tinggi gambar.
- cv2.getRotationMatrix2D(center, angle, scale) membuat matriks transformasi untuk rotasi.
- center: Titik pusat rotasi.
- angle: Sudut rotasi dalam derajat.
- scale: Skala gambar setelah rotasi. 1.0 berarti ukuran gambar tetap.
- cv2.warpAffine(image, M, (width, height)) menerapkan transformasi affine yang didefinisikan oleh matriks M pada gambar image.
- (w, h): Ukuran output gambar yang diputar.


Output :

![https://github.com/angelnatassya/uaspcdimages/blob/main/output%20rotasi.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/output%20rotasi.png)


3. Resizing Image
``` bash
def resize_image(image, size):
    resized_image = cv2.resize(image, size)
    return resized_image
```
``` bash
resized_image = resize_image(image, (80, 550))
plt.imshow(resized_image)
plt.title("After Resized")
plt.axis('on')
```

Dokumentasi :


![https://github.com/angelnatassya/uaspcdimages/blob/main/sc%20resized.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/sc%20resized.png)


Penjelasan :
- image: Parameter pertama adalah gambar yang ingin diubah ukurannya.
- size: Parameter kedua adalah tupel (width, height) yang menentukan ukuran baru gambar setelah resize.
- cv2.resize(image, size): Fungsi ini dari OpenCV digunakan untuk mengubah ukuran gambar.
- resized_image: Variabel yang menyimpan gambar yang sudah diubah ukurannya.
- return resized_image: Mengembalikan gambar yang sudah diresize.
- resized_image = resize_image(image, (80, 550)): Memanggil fungsi resize_image dengan gambar image dan ukuran baru (80, 550).
- plt.imshow(resized_image): Menampilkan gambar yang sudah diubah ukurannya.
- plt.title("After Resized"): Menambahkan judul "After Resized" di atas gambar.
- plt.axis('on'): Menampilkan sumbu koordinat di sekitar gambar.
- plt.show(): Menampilkan semua elemen plot di jendela grafik.

  
Output :

![https://github.com/angelnatassya/uaspcdimages/blob/main/output%20resized.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/output%20resized.png)


4. Cropped Image
``` bash
def crop_image(image, start_x, start_y, width, height):
    cropped_image = image[start_y:start_y+height, start_x:start_x+width]
    return cropped_image
```
``` bash
cropped_image = crop_image(image, 0, 0, 70, 100)
plt.imshow(cropped_image)
plt.title("After Cropped")
plt.axis('on')
```


Dokumentasi :

![https://github.com/angelnatassya/uaspcdimages/blob/main/sc%20cropped.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/sc%20cropped.png)


Penjelasan :
- image: Parameter pertama adalah gambar yang ingin dipotong.
- start_x, start_y: Koordinat titik awal (titik kiri atas) dari area yang ingin dipotong.
- width, height: Lebar dan tinggi dari area yang ingin dipotong.
- image[start_y:start_y+height, start_x:start_x+width]: Ini adalah operasi slicing pada array NumPy (gambar dalam format NumPy array). Ini mengambil bagian gambar dari baris start_y hingga start_y + height dan dari kolom start_x hingga start_x + width.
- cropped_image: Variabel yang menyimpan gambar yang sudah dipotong.
- return cropped_image: Mengembalikan gambar yang sudah dipotong.
- cropped_image = crop_image(image, 0, 0, 70, 100): Memanggil fungsi crop_image dengan gambar image, dimulai dari koordinat (0, 0) dengan lebar 70 piksel dan tinggi 100 piksel.
- plt.imshow(cropped_image): Menampilkan gambar yang sudah dipotong.
- plt.title("After Cropped"): Menambahkan judul "After Cropped" di atas gambar.
- plt.axis('on'): Menampilkan sumbu koordinat di sekitar gambar.
- plt.show(): Menampilkan semua elemen plot di jendela grafik.

  
Output :

![https://github.com/angelnatassya/uaspcdimages/blob/main/output%20cropped.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/output%20cropped.png)


5. Flip Image
``` bash
def flip_image(image):
    flipped_image = cv2.flip(image, 1)
    return flipped_image
```
``` bash
flipped_image = flip_image(image)
plt.imshow(flipped_image)
plt.title("After Flipped")
plt.axis('on')
```


Dokumentasi :

![https://github.com/angelnatassya/uaspcdimages/blob/main/sc%20fliiped.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/sc%20fliiped.png)


Penjelasan :
- image: Parameter pertama adalah gambar yang ingin dibalik.
- cv2.flip(image, 1): Fungsi dari OpenCV untuk membalik (flip) gambar.
- 1 menunjukkan flip horizontal. Jika diganti menjadi 0, itu akan menjadi flip vertikal.
- flipped_image: Variabel yang menyimpan gambar yang sudah dibalik.
- return flipped_image: Mengembalikan gambar yang sudah dibalik.
- flipped_image = flip_image(image): Memanggil fungsi flip_image dengan gambar image.
- plt.imshow(flipped_image): Menampilkan gambar yang sudah dibalik.
- plt.title("After Flipped"): Menambahkan judul "After Flipped" di atas gambar.
- plt.axis('on'): Menampilkan sumbu koordinat di sekitar gambar.
- plt.show(): Menampilkan semua elemen plot di jendela grafik.

  
Output :

![https://github.com/angelnatassya/uaspcdimages/blob/main/output%20fliiped.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/output%20cropped.png)


6. Translated Image
``` bash
def translate_image(image, x, y):
    (h, w) = image.shape[:2]
    M = np.float32([[1, 0, x], [0, 1, y]])
    translated_image = cv2.warpAffine(image, M, (w, h))
    return translated_image
```
``` bash
translated_image = translate_image(image, 100, 30)
plt.imshow(translated_image)
plt.title("After Translated")
plt.axis('on')

plt.tight_layout()
plt.show()
```


Dokumentasi :

![https://github.com/angelnatassya/uaspcdimages/blob/main/sc%20translated.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/sc%20translated.png)


Penjelasan :
- image: Parameter pertama adalah gambar yang ingin diterjemahkan.
- x, y: Parameter kedua dan ketiga adalah pergeseran dalam koordinat x dan y.
- (h, w) = image.shape[:2]: Mendapatkan tinggi (h) dan lebar (w) gambar.
- np.float32([[1, 0, x], [0, 1, y]]): Matriks transformasi affine untuk translasi.
  - [1, 0, x] menggeser gambar sebesar x piksel ke kanan.
  - [0, 1, y] menggeser gambar sebesar y piksel ke bawah.
- cv2.warpAffine(image, M, (w, h)): Menerapkan transformasi affine yang didefinisikan oleh matriks M pada gambar image.
- (w, h): Ukuran output gambar setelah translasi.
- translated_image: Variabel yang menyimpan gambar yang sudah diterjemahkan.
- return translated_image: Mengembalikan gambar yang sudah diterjemahkan.
- translated_image = translate_image(image, 100, 30): Memanggil fungsi translate_image dengan gambar image, menerjemahkan gambar sebesar 100 piksel ke kanan (x) dan 30 piksel ke bawah (y).
- plt.imshow(translated_image): Menampilkan gambar yang sudah diterjemahkan.
- plt.title("After Translated"): Menambahkan judul "After Translated" di atas gambar.
- plt.axis('on'): Menampilkan sumbu koordinat di sekitar gambar.
- plt.tight_layout(): Mengatur tata letak plot agar lebih rapi.
- plt.show(): Menampilkan semua elemen plot di jendela grafik.

  
Output :

![https://github.com/angelnatassya/uaspcdimages/blob/main/output%20translated.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/output%20translated.png)


7. Show All Images
``` bash
fig, axs = plt.subplots(2, 3, figsize=(15, 10))

axs[0, 0].imshow(image)
axs[0, 0].set_title("Citra Asli")
axs[0, 0].axis('on')

axs[0, 1].imshow(rotated_image)
axs[0, 1].set_title("After Rotated")
axs[0, 1].axis('on')

axs[0, 2].imshow(resized_image)
axs[0, 2].set_title("After Resized")
axs[0, 2].axis('on')

axs[1, 0].imshow(cropped_image)
axs[1, 0].set_title("After Cropped")
axs[1, 0].axis('on')

axs[1, 1].imshow(flipped_image)
axs[1, 1].set_title("After Flipped")
axs[1, 1].axis('on')

axs[1, 2].imshow(translated_image)
axs[1, 2].set_title("After Translated")
axs[1, 2].axis('on')

plt.tight_layout()
plt.show()
```


Dokumentasi :

![https://github.com/angelnatassya/uaspcdimages/blob/main/show%20all.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/show%20all.png)


Penjelasan :
- plt.subplots(2, 3, figsize=(15, 10)): Membuat grid subplot dengan ukuran 2 baris dan 3 kolom dengan ukuran gambar 15x10 inci.
- axs[0, 0]: Menampilkan gambar asli di subplot pertama (baris 0, kolom 0).
- imshow(image): Menampilkan gambar image di subplot tersebut.
- set_title("Citra Asli"): Memberikan judul "Citra Asli" untuk subplot tersebut.
- axis('on'): Menampilkan sumbu koordinat.
- axs[0, 1]: Menampilkan gambar yang sudah diputar di subplot kedua (baris 0, kolom 1).
- imshow(rotated_image): Menampilkan gambar rotated_image di subplot tersebut.
- set_title("After Rotated"): Memberikan judul "After Rotated" untuk subplot tersebut.-
- axis('on'): Menampilkan sumbu koordinat.
- axs[0, 2]: Menampilkan gambar yang sudah diresize di subplot ketiga (baris 0, kolom 2).
- imshow(resized_image): Menampilkan gambar resized_image di subplot tersebut.
- set_title("After Resized"): Memberikan judul "After Resized" untuk subplot tersebut.
- axis('on'): Menampilkan sumbu koordinat.
- axs[1, 0]: Menampilkan gambar yang sudah dipotong di subplot keempat (baris 1, kolom 0).
- imshow(cropped_image): Menampilkan gambar cropped_image di subplot tersebut.
- set_title("After Cropped"): Memberikan judul "After Cropped" untuk subplot tersebut.
- axis('on'): Menampilkan sumbu koordinat.
- axs[1, 1]: Menampilkan gambar yang sudah diflip di subplot kelima (baris 1, kolom 1).
- imshow(flipped_image): Menampilkan gambar flipped_image di subplot tersebut.
- set_title("After Flipped"): Memberikan judul "After Flipped" untuk subplot tersebut.
- axis('on'): Menampilkan sumbu koordinat.
- axs[1, 2]: Menampilkan gambar yang sudah diterjemahkan di subplot keenam (baris 1, kolom 2).
- imshow(translated_image): Menampilkan gambar translated_image di subplot tersebut.
- set_title("After Translated"): Memberikan judul "After Translated" untuk subplot tersebut.
- axis('on'): Menampilkan sumbu koordinat.
- tight_layout(): Menyusun ulang tata letak subplot agar lebih rapi.
- show(): Menampilkan semua elemen plot di jendela grafik.

  
Output :

![https://github.com/angelnatassya/uaspcdimages/blob/main/display%20all.png
](https://github.com/angelnatassya/uaspcdimages/blob/main/display%20all.png)


## Jurnal dan Referensi

Jurnal Terkait :

1. IEEE Transactions on Image Processing - Jurnal ini memuat berbagai penelitian tentang pemrosesan citra, termasuk topik tentang transformasi geometris dan pengolahan geometris citra.

2. Computer Vision and Image Understanding - Fokus utama jurnal ini adalah visi komputer dan pemahaman citra, mencakup penelitian dalam geometri citra untuk registrasi, rekonstruksi 3D, dan aplikasi lainnya.

3. Pattern Recognition - Jurnal ini mempublikasikan penelitian dalam pengenalan pola dan analisis citra, termasuk teknik geometri citra untuk ekstraksi fitur dan pengolahan citra.

4. International Journal of Computer Vision - Menyajikan penelitian terkait visi komputer, termasuk pemrosesan geometris citra untuk pencocokan citra, segmentasi, dan rekonstruksi 3D.

5. Journal of Mathematical Imaging and Vision - Fokus jurnal ini adalah pada pemodelan matematis dan pengolahan citra, termasuk transformasi geometris dan analisis geometris citra.

Referensi :

1. Rafael C. Gonzalez, Richard E. Woods. "Digital Image Processing". Prentice Hall, 3rd Edition, 2008.

   Buku ini adalah referensi klasik dalam pengolahan citra digital, mencakup dasar-dasar dan teknik-teknik transformasi geometris dalam citra.

2. David A. Forsyth, Jean Ponce. "Computer Vision: A Modern Approach". Prentice Hall, 2nd Edition, 2011.

   Buku ini memberikan pembahasan komprehensif mengenai visi komputer, termasuk pengolahan geometris citra dan teknik-teknik terkait.
