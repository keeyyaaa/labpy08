# Praktikum08 - Mengaplikasikan penggunaan class untuk menampilkan daftar nilai mahasiswa

Nama: Ica Rizqiah

Nim: 312410554

Kelas: TI.24.A.5

## Code program praktikum08 

```python
class Mahasiswa:
    def __init__(self):
        self.data_mahasiswa = []

    def tambah(self, nama, nilai):
        """
        Method untuk menambah data mahasiswa.
        :param nama: Nama mahasiswa (string).
        :param nilai: Nilai mahasiswa (int/float).
        """
        self.data_mahasiswa.append({'nama': nama, 'nilai': nilai})
        print(f"Data mahasiswa {nama} berhasil ditambahkan.")

    def tampilkan(self):
        """
        Method untuk menampilkan data mahasiswa.
        """
        if not self.data_mahasiswa:
            print("Tidak ada data mahasiswa.")
            return
        print("\nDaftar Nilai Mahasiswa:")
        for mhs in self.data_mahasiswa:
            print(f"Nama: {mhs['nama']}, Nilai: {mhs['nilai']}")

    def hapus(self, nama):
        """
        Method untuk menghapus data mahasiswa berdasarkan nama.
        :param nama: Nama mahasiswa yang akan dihapus (string).
        """
        self.data_mahasiswa = [mhs for mhs in self.data_mahasiswa if mhs['nama'] != nama]
        print(f"Data mahasiswa {nama} berhasil dihapus.")

    def ubah(self, nama, nilai_baru):
        """
        Method untuk mengubah nilai mahasiswa berdasarkan nama.
        :param nama: Nama mahasiswa yang akan diubah (string).
        :param nilai_baru: Nilai baru mahasiswa (int/float).
        """
        for mhs in self.data_mahasiswa:
            if mhs['nama'] == nama:
                mhs['nilai'] = nilai_baru
                print(f"Data mahasiswa {nama} berhasil diubah menjadi nilai {nilai_baru}.")
                return
        print(f"Data mahasiswa {nama} tidak ditemukan.")

# Program utama
if __name__ == "__main__":
    daftar_mahasiswa = Mahasiswa()

    while True:
        print("\nMenu:")
        print("1. Tambah Data Mahasiswa")
        print("2. Tampilkan Data Mahasiswa")
        print("3. Hapus Data Mahasiswa")
        print("4. Ubah Data Mahasiswa")
        print("5. Keluar")
        
        pilihan = input("Pilih menu (1-5): ")
        
        if pilihan == '1':
            nama = input("Masukkan nama mahasiswa: ")
            nilai = float(input("Masukkan nilai mahasiswa: "))
            daftar_mahasiswa.tambah(nama, nilai)
        elif pilihan == '2':
            daftar_mahasiswa.tampilkan()
        elif pilihan == '3':
            nama = input("Masukkan nama mahasiswa yang ingin dihapus: ")
            daftar_mahasiswa.hapus(nama)
        elif pilihan == '4':
            nama = input("Masukkan nama mahasiswa yang ingin diubah: ")
            nilai_baru = float(input("Masukkan nilai baru: "))
            daftar_mahasiswa.ubah(nama, nilai_baru)
        elif pilihan == '5':
            print("Keluar dari program.")
            break
        else:
            print("Pilihan tidak valid. Silakan coba lagi.")
```

## Penjelasan kode program

### 1. Import dan Definisi Class

```python
class Mahasiswa:
    def __init__(self):
        self.data_mahasiswa = []
```

- `class Mahasiswa`: Mendefinisikan sebuah class bernama `Mahasiswa`. Class ini akan digunakan untuk mengelola data mahasiswa.

- `def __init__(self):`: Ini adalah constructor dari class `Mahasiswa`. Constructor ini dipanggil saat kita membuat objek dari class ini.

- `self.data_mahasiswa = []`: Inisialisasi atribut `data_mahasiswa` sebagai list kosong. List ini akan digunakan untuk menyimpan data mahasiswa dalam bentuk dictionary.


### 2. Method `tambah`

```python
def tambah(self, nama, nilai):
    """
    Method untuk menambah data mahasiswa.
    :param nama: Nama mahasiswa (string).
    :param nilai: Nilai mahasiswa (int/float).
    """
    self.data_mahasiswa.append({'nama': nama, 'nilai': nilai})
    print(f"Data mahasiswa {nama} berhasil ditambahkan.")
```

- `def tambah(self, nama, nilai):`: Mendefinisikan method `tambah` yang menerima dua parameter: `nama` dan `nilai.`
  
- `self.data_mahasiswa.append({'nama': nama, 'nilai': nilai})`: Menambahkan dictionary baru ke dalam list `data_mahasiswa`, di mana dictionary tersebut berisi nama dan nilai mahasiswa.
    
- `print(...)`: Menampilkan pesan konfirmasi bahwa data mahasiswa telah berhasil ditambahkan.

### 3. Method `tampilkan`

  ```python
  def tampilkan(self):
    """
    Method untuk menampilkan data mahasiswa.
    """
    if not self.data_mahasiswa:
        print("Tidak ada data mahasiswa.")
        return
    print("\nDaftar Nilai Mahasiswa:")
    for mhs in self.data_mahasiswa:
        print(f"Nama: {mhs['nama']}, Nilai: {mhs['nilai']}")
  ```

-`def tampilkan(self):`: Mendefinisikan method `tampilkan` yang tidak menerima parameter.

-`if not self.data_mahasiswa:`: Memeriksa apakah list `data_mahasiswa` kosong. Jika kosong, tampilkan pesan bahwa tidak ada data mahasiswa.

-`print(...)`: Menampilkan header untuk daftar nilai mahasiswa.

-`for mhs in self.data_mahasiswa:`: Melakukan iterasi pada setiap mahasiswa dalam list `data_mahasiswa.`

-`print(...)`: Menampilkan nama dan nilai setiap mahasiswa.

### 4. Method `hapus`

```python
def hapus(self, nama):
    """
    Method untuk menghapus data mahasiswa berdasarkan nama.
    :param nama: Nama mahasiswa yang akan dihapus (string).
    """
    self.data_mahasiswa = [mhs for mhs in self.data_mahasiswa if mhs['nama'] != nama]
    print(f"Data mahasiswa {nama} berhasil dihapus.")
```

-`def hapus(self, nama):`: Mendefinisikan method `hapus` yang menerima parameter `nama.`

-`self.data_mahasiswa = [...]`: Menggunakan list comprehension untuk membuat list baru yang hanya berisi mahasiswa yang namanya tidak sama dengan `nama` yang diberikan. Ini efektif menghapus mahasiswa dengan nama tersebut.

-`print(...)`: Menampilkan pesan konfirmasi bahwa data mahasiswa telah berhasil dihapus.

### 5. Method `ubah`

```python
def ubah(self, nama, nilai_baru):
    """
    Method untuk mengubah nilai mahasiswa berdasarkan nama.
    :param nama: Nama mahasiswa yang akan diubah (string).
    :param nilai_baru: Nilai baru mahasiswa (int/float).
    """
    for mhs in self.data_mahasiswa:
        if mhs['nama'] == nama:
            mhs['nilai'] = nilai_baru
            print(f"Data mahasiswa {nama} berhasil diubah menjadi nilai {nilai_baru}.")
            return
    print(f"Data mahasiswa {nama} tidak ditemukan.")
```

-`def ubah(self, nama, nilai_baru):`: Mendefinisikan method `ubah` yang menerima dua parameter: `nama` dan `nilai_baru.`

-`for mhs in self.data_mahasiswa:`: Melakukan iterasi pada setiap mahasiswa dalam list `data_mahasiswa.`

-`if mhs['nama'] == nama:`: Memeriksa apakah nama mahasiswa saat ini sama dengan nama yang diberikan.

`mhs['nilai'] = nilai_baru`: Jika ditemukan, mengubah nilai mahasiswa dengan nilai baru yang diberikan.

`print(...)`: Menampilkan pesan konfirmasi bahwa data mahasiswa telah berhasil diubah.

`print(...)`: Jika tidak ditemukan

## Flowchart 

![foto](https://github.com/keeyyaaa/labpy08/blob/2ea6ab480619ecd0e6acf7b6b7c238139b09a14a/fc.png)

## Diagram class

![foto]()

## Hasil output code program praktikum 08
