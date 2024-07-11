
# PROJECT UAS PENGOLAHAN CITRA 2024







## Authors

- [@angelnatassya](https://www.github.com/angelnatassya)


## Aplikasi

 Menggunakan aplikasi Jupiter Notebook pada Anaconda Navigator.

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
Penjelasan :
- image_path = 'pict.jpg': Menyimpan path ke gambar yang ingin dibaca. 
- image = cv2.imread(image_path): Membaca image dari path yang telah ditentukan. OpenCV membaca image dalam format BGR (Blue, Green, Red).
- image = cv2.cvtColor(gambar, cv2.COLOR_BGR2RGB): Mengkonversi gambar dari format BGR (default OpenCV) ke format RGB (Red, Green, Blue) yang lebih umum digunakan dalam visualisasi. 
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
Penjelasan :
- image.shape memberikan dimensi gambar dalam bentuk (height, width, channels). image.shape[:2] mengambil dua nilai pertama yaitu tinggi (h) dan lebar (w) gambar.
- center adalah titik pusat rotasi gambar. Ini dihitung sebagai setengah dari lebar dan tinggi gambar.
- cv2.getRotationMatrix2D(center, angle, scale) membuat matriks transformasi untuk rotasi.
- center: Titik pusat rotasi.
- angle: Sudut rotasi dalam derajat.
- scale: Skala gambar setelah rotasi. 1.0 berarti ukuran gambar tetap.
- cv2.warpAffine(image, M, (width, height)) menerapkan transformasi affine yang didefinisikan oleh matriks M pada gambar image.
- (w, h): Ukuran output gambar yang diputar.
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
