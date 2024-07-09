# Viana Salsabila Fairuz Syahla
# 202231027

# Geometrix Citra

## Deskripsi Proyek

Proyek ini, Geometrix Citra, mengeksplorasi berbagai teknik transformasi gambar menggunakan pustaka OpenCV dalam Python. Kode ini menunjukkan fungsionalitas rotasi gambar, pengubahan ukuran, pemotongan, pembalikan, dan penerjemahan.

## Teori

Transformasi Gambar: Dalam pemrosesan gambar digital, transformasi gambar mengacu pada manipulasi gambar untuk mendapatkan gambar baru dengan properti tertentu. Ini dapat melibatkan transformasi geometris (rotasi, penskalaan, penerjemahan), konversi skala abu-abu, konversi ruang warna, dan banyak lagi. OpenCV menyediakan berbagai fungsi untuk melakukan transformasi ini.

## Penjelasan Kode

### Import Pustaka:
- `cv2`: Pustaka OpenCV untuk tugas pemrosesan gambar.
- `numpy`: Pustaka NumPy untuk operasi numerik.
- `matplotlib.pyplot`: Pustaka Matplotlib untuk fungsionalitas plotting.
- `%matplotlib inline`: Plotting inline dalam lingkungan notebook Jupyter.

### Memuat Gambar:
```python
img = cv2.imread('viana.jpg')
```

### Properti Gambar:
```python
img.shape
```
Mencetak bentuk gambar sebagai tupel yang mewakili tinggi, lebar, dan jumlah saluran (biasanya BGR untuk gambar berwarna).

### Konversi Warna:
```python
imgbaru = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
Mengubah gambar dari format BGR ke format RGB untuk plotting dengan Matplotlib.

### Tampilkan Gambar Asli:
```python
fig, ax = plt.subplots(1, 1, figsize=(2, 3))
ax.imshow(imgbaru)
ax.set_title("Gambar Asli")
plt.show()
```

### Rotasi Gambar:
```python
(h, w) = imgbaru.shape[:2]
center = (w // 2, h // 2)
M = cv2.getRotationMatrix2D(center, 45, 1.0)
img_rotated = cv2.warpAffine(imgbaru, M, (w, h))
plt.subplot(2, 3, 2)
plt.imshow(img_rotated)
plt.title('Rotated Image')
plt.axis('off')
```
Kodingan ini adalah untuk melakukan rotasi gambar menggunakan OpenCV dan Matplotlib. Mari kita bahas baris per baris:

1. `(h, w) = imgbaru.shape[:2]`
   - `imgbaru.shape[:2]` mengembalikan tuple yang berisi tinggi (h) dan lebar (w) dari gambar `imgbaru`.
   - `h` adalah tinggi gambar, dan `w` adalah lebar gambar.

2. `center = (w // 2, h // 2)`
   - `center` adalah titik pusat rotasi. Kami menghitungnya dengan mengambil setengah dari lebar (`w // 2`) dan setengah dari tinggi (`h // 2`) gambar.
   - Titik ini akan menjadi pusat di sekitar mana gambar akan diputar.

3. `M = cv2.getRotationMatrix2D(center, 45, 1.0)`
   - `cv2.getRotationMatrix2D(center, angle, scale)` mengembalikan matriks rotasi `M`.
   - `center` adalah titik pusat rotasi yang sudah dihitung sebelumnya.
   - `45` adalah sudut rotasi dalam derajat. Dalam kasus ini, gambar akan diputar sebesar 45 derajat searah jarum jam.
   - `1.0` adalah faktor skala. Di sini, nilai 1.0 berarti ukuran gambar tetap tidak berubah setelah rotasi.

4. `img_rotated = cv2.warpAffine(imgbaru, M, (w, h))`
   - `cv2.warpAffine(img, M, (width, height))` mengembalikan gambar yang diputar berdasarkan matriks transformasi `M`.
   - `imgbaru` adalah gambar asli yang ingin kita putar.
   - `M` adalah matriks rotasi yang sudah kita dapatkan.
   - `(w, h)` adalah ukuran gambar hasil yang diharapkan setelah rotasi.

5. `plt.subplot(2, 3, 2)`
   - `plt.subplot(2, 3, 2)` membuat subplot dalam grid 2x3 dan memilih subplot nomor 2 (urutan kiri ke kanan, atas ke bawah).
   - Ini menyiapkan tempat untuk menampilkan gambar yang diputar di dalamnya.

6. `plt.imshow(img_rotated)`
   - `plt.imshow(img_rotated)` menampilkan gambar yang sudah diputar (`img_rotated`) di subplot yang sudah disiapkan sebelumnya.

7. `plt.title('Rotated Image')`
   - `plt.title('Rotated Image')` menambahkan judul "Rotated Image" di atas gambar yang ditampilkan.

8. `plt.axis('off')`
   - `plt.axis('off')` mematikan sumbu pada plot tersebut, sehingga hanya gambar yang ditampilkan tanpa garis-garis sumbu.

Dengan demikian, kodingan ini secara keseluruhan mengambil gambar `imgbaru`, memutarnya sebesar 45 derajat searah jarum jam berdasarkan pusat yang dihitung, dan menampilkan gambar yang diputar di subplot nomor 2 dari grid 2x3 dengan judul "Rotated Image".
### Pengubahan Ukuran Gambar:
```python
height, width = imgbaru.shape[:2]
img_resized = cv2.resize(imgbaru, (width // 3, height // 2), interpolation=cv2.INTER_CUBIC)
plt.subplot(2, 3, 3)
plt.imshow(img_resized)
plt.title('Resized Image')
plt.axis('off')
```
Kodingan ini bertujuan untuk mengubah ukuran gambar menggunakan OpenCV dan menampilkannya menggunakan Matplotlib. Mari kita bahas setiap barisnya:

1. `height, width = imgbaru.shape[:2]`
   - `imgbaru.shape[:2]` mengembalikan tuple yang berisi tinggi (height) dan lebar (width) dari gambar `imgbaru`.
   - `height` adalah tinggi gambar.
   - `width` adalah lebar gambar.

2. `img_resized = cv2.resize(imgbaru, (width // 3, height // 2), interpolation=cv2.INTER_CUBIC)`
   - `cv2.resize(img, (width, height), interpolation)` mengubah ukuran gambar `imgbaru`.
   - `(width // 3, height // 2)` adalah tuple yang menyatakan ukuran baru gambar. Di sini, gambar akan diubah menjadi sepertiga lebar dan setengah tinggi dari ukuran aslinya.
   - `interpolation=cv2.INTER_CUBIC` adalah metode interpolasi yang digunakan untuk mengubah ukuran gambar. `cv2.INTER_CUBIC` adalah salah satu metode yang memberikan hasil yang lebih halus.

3. `plt.subplot(2, 3, 3)`
   - `plt.subplot(2, 3, 3)` membuat subplot dalam grid 2x3 dan memilih subplot nomor 3 (urutan kiri ke kanan, atas ke bawah).
   - Ini menyiapkan tempat untuk menampilkan gambar yang diubah ukurannya di dalamnya.

4. `plt.imshow(img_resized)`
   - `plt.imshow(img_resized)` menampilkan gambar yang sudah diubah ukurannya (`img_resized`) di subplot yang sudah disiapkan sebelumnya.

5. `plt.title('Resized Image')`
   - `plt.title('Resized Image')` menambahkan judul "Resized Image" di atas gambar yang ditampilkan.

6. `plt.axis('off')`
   - `plt.axis('off')` mematikan sumbu pada plot tersebut, sehingga hanya gambar yang ditampilkan tanpa garis-garis sumbu.

Dengan demikian, kodingan ini secara keseluruhan mengambil gambar `imgbaru`, mengubah ukurannya menjadi sepertiga lebar dan setengah tinggi dari ukuran aslinya menggunakan OpenCV, dan menampilkan gambar yang diubah ukurannya di subplot nomor 3 dari grid 2x3 dengan judul "Resized Image".
### Pemotongan Gambar:
```python
height, width = imgbaru.shape[:2]
img_cropped = imgbaru[height//4:3*height//4, width//4:3*width//4]
plt.subplot(2, 3, 4)
plt.imshow(img_cropped)
plt.title('Cropped Image')
plt.axis('off')
```
Kodingan ini digunakan untuk memotong bagian tertentu dari gambar menggunakan operasi slicing array NumPy dan menampilkannya menggunakan Matplotlib. Mari kita bahas setiap barisnya:

1. `height, width = imgbaru.shape[:2]`
   - `imgbaru.shape[:2]` mengembalikan tuple yang berisi tinggi (height) dan lebar (width) dari gambar `imgbaru`.
   - `height` adalah tinggi gambar.
   - `width` adalah lebar gambar.

2. `img_cropped = imgbaru[height//4:3*height//4, width//4:3*width//4]`
   - `imgbaru[height//4:3*height//4, width//4:3*width//4]` adalah operasi slicing yang digunakan untuk memilih bagian tertentu dari gambar `imgbaru`.
   - `height//4:3*height//4` adalah rentang baris yang dipilih, yaitu dari seperempat atas hingga tiga perempat bawah gambar.
   - `width//4:3*width//4` adalah rentang kolom yang dipilih, yaitu dari seperempat kiri hingga tiga perempat kanan gambar.
   - Ini menghasilkan `img_cropped`, yang merupakan gambar yang telah dipotong sesuai dengan rentang yang ditentukan.

3. `plt.subplot(2, 3, 4)`
   - `plt.subplot(2, 3, 4)` membuat subplot dalam grid 2x3 dan memilih subplot nomor 4 (urutan kiri ke kanan, atas ke bawah).
   - Ini menyiapkan tempat untuk menampilkan gambar yang dipotong di dalamnya.

4. `plt.imshow(img_cropped)`
   - `plt.imshow(img_cropped)` menampilkan gambar yang sudah dipotong (`img_cropped`) di subplot yang sudah disiapkan sebelumnya.

5. `plt.title('Cropped Image')`
   - `plt.title('Cropped Image')` menambahkan judul "Cropped Image" di atas gambar yang ditampilkan.

6. `plt.axis('off')`
   - `plt.axis('off')` mematikan sumbu pada plot tersebut, sehingga hanya gambar yang ditampilkan tanpa garis-garis sumbu.

Dengan demikian, kodingan ini secara keseluruhan mengambil gambar `imgbaru`, memotong bagian dari seperempat atas dan kiri hingga tiga perempat bawah dan kanan gambar menggunakan slicing NumPy, dan menampilkan gambar yang dipotong di subplot nomor 4 dari grid 2x3 dengan judul "Cropped Image".
### Pembalikan Gambar:
```python
img_flipped = cv2.flip(imgbaru, 1)
plt.subplot(2, 3, 5)
plt.imshow(img_flipped)
plt.title('Flipped Image')
plt.axis('off')
```
Kodingan ini digunakan untuk membalik gambar secara horizontal menggunakan OpenCV dan menampilkannya menggunakan Matplotlib. Mari kita bahas setiap barisnya:

1. `img_flipped = cv2.flip(imgbaru, 1)`
   - `cv2.flip(imgbaru, 1)` adalah fungsi OpenCV yang digunakan untuk membalik gambar `imgbaru`.
   - Argumen kedua (`1`) menentukan sumbu di mana gambar akan dibalik. Di sini, `1` berarti gambar akan dibalik secara horizontal (sekitar sumbu y).

2. `plt.subplot(2, 3, 5)`
   - `plt.subplot(2, 3, 5)` membuat subplot dalam grid 2x3 dan memilih subplot nomor 5 (urutan kiri ke kanan, atas ke bawah).
   - Ini menyiapkan tempat untuk menampilkan gambar yang sudah dibalik di dalamnya.

3. `plt.imshow(img_flipped)`
   - `plt.imshow(img_flipped)` menampilkan gambar yang sudah dibalik (`img_flipped`) di subplot yang sudah disiapkan sebelumnya.

4. `plt.title('Flipped Image')`
   - `plt.title('Flipped Image')` menambahkan judul "Flipped Image" di atas gambar yang ditampilkan.

5. `plt.axis('off')`
   - `plt.axis('off')` mematikan sumbu pada plot tersebut, sehingga hanya gambar yang ditampilkan tanpa garis-garis sumbu.

Dengan demikian, kodingan ini secara keseluruhan mengambil gambar `imgbaru`, membaliknya secara horizontal menggunakan OpenCV, dan menampilkan gambar yang sudah dibalik di subplot nomor 5 dari grid 2x3 dengan judul "Flipped Image".
### Penerjemahan Gambar:
```python
rows, cols = imgbaru.shape[:2]
M_translate = np.float32([[1, 0, 250], [0, 1, 180]])
img_translated = cv2.warpAffine(imgbaru, M_translate, (cols, rows))
plt.subplot(2, 3, 6)
plt.imshow(img_translated)
plt.title('Translated Image')
plt.axis('off')
```
Kodingan ini bertujuan untuk menerjemahkan (translasi) gambar menggunakan OpenCV dan menampilkannya menggunakan Matplotlib. Mari kita bahas setiap barisnya:

1. `rows, cols = imgbaru.shape[:2]`
   - `imgbaru.shape[:2]` mengembalikan tuple yang berisi tinggi (rows) dan lebar (cols) dari gambar `imgbaru`.
   - `rows` adalah jumlah baris (tinggi) gambar.
   - `cols` adalah jumlah kolom (lebar) gambar.

2. `M_translate = np.float32([[1, 0, 250], [0, 1, 180]])`
   - `np.float32([[1, 0, 250], [0, 1, 180]])` adalah matriks translasi `M_translate`.
   - Matriks ini menentukan pergeseran horizontal dan vertikal yang akan diterapkan pada gambar.
   - `[1, 0, 250]` menunjukkan pergeseran sebesar 250 piksel ke kanan (sumbu x).
   - `[0, 1, 180]` menunjukkan pergeseran sebesar 180 piksel ke bawah (sumbu y).

3. `img_translated = cv2.warpAffine(imgbaru, M_translate, (cols, rows))`
   - `cv2.warpAffine(img, M, (cols, rows))` mengembalikan gambar yang telah diterjemahkan berdasarkan matriks transformasi `M_translate`.
   - `imgbaru` adalah gambar asli yang ingin kita terjemahkan.
   - `M_translate` adalah matriks translasi yang sudah kita tentukan sebelumnya.
   - `(cols, rows)` adalah ukuran gambar hasil yang diharapkan setelah translasi.

4. `plt.subplot(2, 3, 6)`
   - `plt.subplot(2, 3, 6)` membuat subplot dalam grid 2x3 dan memilih subplot nomor 6 (urutan kiri ke kanan, atas ke bawah).
   - Ini menyiapkan tempat untuk menampilkan gambar yang sudah diterjemahkan di dalamnya.

5. `plt.imshow(img_translated)`
   - `plt.imshow(img_translated)` menampilkan gambar yang sudah diterjemahkan (`img_translated`) di subplot yang sudah disiapkan sebelumnya.

6. `plt.title('Translated Image')`
   - `plt.title('Translated Image')` menambahkan judul "Translated Image" di atas gambar yang ditampilkan.

7. `plt.axis('off')`
   - `plt.axis('off')` mematikan sumbu pada plot tersebut, sehingga hanya gambar yang ditampilkan tanpa garis-garis sumbu.

Dengan demikian, kodingan ini secara keseluruhan mengambil gambar `imgbaru`, menerjemahkannya dengan menggunakan matriks translasi `M_translate`, dan menampilkan gambar yang sudah diterjemahkan di subplot nomor 6 dari grid 2x3 dengan judul "Translated Image".
## Visualisasi Hasil Transformasi
```python
fig, axs = plt.subplots(2, 3, figsize=(15, 10))
axs = axs.ravel()

axs[0].imshow(imgbaru)
axs[0].set_title("Gambar Asli")
axs[1].imshow(img_rotated)
axs[1].set_title("After Rotate")
axs[2].imshow(img_resized)
axs[2].set_title("After Resize")
axs[3].imshow(img_cropped)
axs[3].set_title("After Cropped")
axs[4].imshow(img_flipped)
axs[4].set_title("After Flipped")
axs[5].imshow(img_translated)
axs[5].set_title("After Translated")
```
Kodingan ini digunakan untuk membuat subplot grid 2x3 dan menampilkan beberapa versi transformasi gambar (`imgbaru`, `img_rotated`, `img_resized`, `img_cropped`, `img_flipped`, `img_translated`) dalam setiap subplotnya. Mari kita bahas setiap barisnya:

1. `fig, axs = plt.subplots(2, 3, figsize=(15, 10))`
   - `plt.subplots(2, 3, figsize=(15, 10))` membuat sebuah gambar dengan grid subplot 2x3 (2 baris, 3 kolom) dengan ukuran total 15x10 inch.
   - `fig` adalah objek gambar.
   - `axs` adalah array dari objek subplot yang terbentuk dari grid tersebut.

2. `axs = axs.ravel()`
   - `axs.ravel()` mengubah matriks `axs` menjadi array 1 dimensi. Ini memudahkan pengaksesan setiap subplot secara berurutan.

3. `axs[0].imshow(imgbaru)`
   - `axs[0].imshow(imgbaru)` menampilkan gambar asli (`imgbaru`) di subplot pertama (`axs[0]`).
   - `axs[0].set_title("Gambar Asli")` menambahkan judul "Gambar Asli" di atas subplot pertama.

4. `axs[1].imshow(img_rotated)`
   - `axs[1].imshow(img_rotated)` menampilkan gambar yang sudah diputar (`img_rotated`) di subplot kedua (`axs[1]`).
   - `axs[1].set_title("After Rotate")` menambahkan judul "After Rotate" di atas subplot kedua.

5. `axs[2].imshow(img_resized)`
   - `axs[2].imshow(img_resized)` menampilkan gambar yang sudah diubah ukurannya (`img_resized`) di subplot ketiga (`axs[2]`).
   - `axs[2].set_title("After Resize")` menambahkan judul "After Resize" di atas subplot ketiga.

6. `axs[3].imshow(img_cropped)`
   - `axs[3].imshow(img_cropped)` menampilkan gambar yang sudah dipotong (`img_cropped`) di subplot keempat (`axs[3]`).
   - `axs[3].set_title("After Cropped")` menambahkan judul "After Cropped" di atas subplot keempat.

7. `axs[4].imshow(img_flipped)`
   - `axs[4].imshow(img_flipped)` menampilkan gambar yang sudah dibalik (`img_flipped`) di subplot kelima (`axs[4]`).
   - `axs[4].set_title("After Flipped")` menambahkan judul "After Flipped" di atas subplot kelima.

8. `axs[5].imshow(img_translated)`
   - `axs[5].imshow(img_translated)` menampilkan gambar yang sudah diterjemahkan (`img_translated`) di subplot keenam (`axs[5]`).
   - `axs[5].set_title("After Translated")` menambahkan judul "After Translated" di atas subplot keenam.

Dengan demikian, kodingan ini secara keseluruhan membuat gambar dengan grid subplot 2x3 dan menampilkan berbagai transformasi gambar dalam setiap subplotnya, disertai dengan judul yang sesuai untuk setiap transformasi tersebut.

## Referensi
- [Digital Image Processing](https://en.wikipedia.org/wiki/Digital_image_processing)
- [OpenCV Documentation](https://docs.opencv.org/4.x/)
- [Matplotlib Documentation](https://matplotlib.org/stable/index.html)
- https://repository.ub.ac.id/id/eprint/176921/
- https://grdjournals.com/uploads/article/GRDJE/V02/I11/0020/GRDJEV02I110020.pdf
- https://repository.unsri.ac.id/10040/1/RAMA_55201_09021181520021_0222058001_0028068806_01_front_ref.pdf