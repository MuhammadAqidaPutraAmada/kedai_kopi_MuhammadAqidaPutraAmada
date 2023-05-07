# APLIKASI KEDAI KOPI - part 2
Aplikasi Kedai Kopi ini adalah tugas dari mata kuliah OOP, penulisan kode program berbeda dengan program kedai kopi sebelumnya. Pada program kali ini terdapat tambahan class Diskon dengan 5 tingkatan diskon.
## Penjelasan Program
#### Pembuatan Class Pesanan :
kelas Pesanan memiliki beberapa private object/ variable yang tidak boleh dipanggil selain di dalam kelas Pesanan. Apabila object ingin dipanggil selain di dalam kelas Pesanan, maka harus menggunakan fungsi yang dibuat untuk kebutuhan tersebut.
```sh
class Pesanan:

    def __init__(self, menu, jumlahPesanan):
        self.__menu          = menu
        self.__jumlahPesanan = jumlahPesanan
        self.__harga         = menu
        self.__ppn           = menu
```
Fungsi untuk menampilkan nama menu sesuai kode huruf yang diinputkan user.
Fungsi ini dibuat untuk menampilkan objek "menu" apabila ingin dipanggil di luar kelas Pesanan.
```sh
def getMenu (self) :

        if self.__menu == "A" :
            self.__menu = "ES Kopi Susu"

        elif self.__menu == "B" :
            self.__menu = "ES Kopi Coklat"
        
        elif self.__menu == "C" :
            self.__menu = "ES Kopi Hitam"
        
        elif self.__menu == "D" :
            self.__menu = "Ice Americano"

        return self.__menu
```
Fungsi untuk menampilkan jumlah pesanan sesuai dengan angka yang diinputkan user.
Fungsi ini dibuat untuk menampilkan objek "jumlah pesanan" apabila ingin dipanggil di luar kelas Pesanan.
```sh
def getJumlahPesanan (self) :

        return self.__jumlahPesanan
```
Fungsi untuk menghitung harga sesuai dengan menu yang dipilih user.
Fungsi ini dibuat untuk menampilkan objek "harga" apabila ingin dipanggil di luar kelas Pesanan.
```sh
def getHarga (self) :

        if self.__harga == "A" :
            self.__harga = 11000 * self.__jumlahPesanan
        
        elif self.__harga == "B" :
            self.__harga = 12000 * self.__jumlahPesanan
        
        elif self.__harga == "C" :
            self.__harga = 11000 * self.__jumlahPesanan
        
        elif self.__harga == "D" :
            self.__harga = 14000 * self.__jumlahPesanan
      
        return self.__harga
```
Fungsi untuk menghitung PPN sesuai dengan menu yang dipilih user.
Fungsi ini dibuat untuk menampilkan objek "PPN" apabila ingin dipanggil di luar kelas Pesanan.
```sh
def getPPN (self) :

        if self.__ppn == "A" :
            self.__ppn = int((11000 * self.__jumlahPesanan) * 0.1)

        elif self.__ppn == "B" :
            self.__ppn = int((12000 * self.__jumlahPesanan) * 0.1)

        elif self.__ppn == "C" :
            self.__ppn = int((11000 * self.__jumlahPesanan) * 0.1)

        elif self.__ppn == "D" :
            self.__ppn = int((14000 * self.__jumlahPesanan) * 0.1)

        return self.__ppn
```

### Pembuatan Class Diskon
kelas diskon adalah turunan dari kelas Pelanggan, isi dari kelas diskon adalah perhitungan diskon. Diskon dibagi dalam 5 tingkatan, kode lengkap bisa dilihat di file.
```sh
class Diskon (Pesanan) :
    def __init__(self, menu, jumlahPesanan):
        super().__init__(menu, jumlahPesanan)

        self.__diskon        = menu
        self.__jumlahPesanan = jumlahPesanan

    def getDiskon (self) :
        
    # diskon tingkat 1
        if self.__jumlahPesanan >= 3 and self.__jumlahPesanan < 5 :

            if self.__diskon == "A":
                self.__diskon = int((11000*self.__jumlahPesanan) * 0.1)

            elif self.__diskon == "B":
                self.__diskon = int((12000*self.__jumlahPesanan) * 0.1)

            elif self.__diskon == "C":
                self.__diskon = int((11000*self.__jumlahPesanan) * 0)

            elif self.__diskon == "D":
                self.__diskon = int((14000*self.__jumlahPesanan) * 0)
        
        return self.__diskon

```

#### Pembuatan Class Laporan :
kelas Laporan mengelola penambahan data kedalam kelas Pesanan, penghapusan data dari kelas Pesanan, menampilkan menu, dan menampilkan transaksi pemesanan.
Disediakan sebuah list untuk menampung data pesanan yang diinputkan oleh user.
```sh
class Laporan:
    def __init__(self):
        self.__dataPesanan = []
```
Fungsi untuk menambahkan data kedalam list :
```sh
def addPesanan (self, data) :
        self.__dataPesanan.append(data)
```
Fungsi untuk menghapus data yang ada di dalam list :
```sh
def hapusPesanan (self, data) :
        self.__dataPesanan.remove(data)
```
Fungsi untuk menampilkan menu :
```sh
def tampilkanMenu (self) :
        print("""
    ==============================

    Ananda Coffe
    List Menu Minuman Kopi
 
    ==============================
    A. ES Kopi Susu : Rp 11.000
    B. ES Kopi Coklat : Rp 12.000
    C. ES Kopi Hitam : Rp 11.000
    D. Ice Americano : Rp 14.000
    ==============================
    \n
    """)
```
Fungsi untuk menampilkan transaksi pemesanan :
```sh
def tampilkanPesanan (self) :

        for data in self.__dataPesanan:

            print("--------------------------")
            print("Ananda Coffe")
            print("--------------------------")

            menu   = print (f"Menu         : {data.getMenu()}")
            jumlah = print (f"Jumlah Pesan : {data.getJumlahPesanan()} cup")
            harga  = print (f"Harga        : {data.getHarga()} K")
            ppn    = print (f"PPN          : {data.getPPN()} K")
            diskon = print (f"Diskon       : {data.getDiskon()} K")

            print("--------------------------")
            ttl    = print (f"Jumlah Bayar : {(data.getHarga()-data.getDiskon()+data.getPPN())}K")
            print("--------------------------")

        return menu, jumlah, harga, ppn, diskon ,ttl
```

While Loop untuk melakukan proses input
```sh
lup = "Y"
while lup == "Y" :
    a = Laporan ()
    a.tampilkanMenu ()

    inputMenu = input ("Masukan Menu: ")
    while inputMenu != "A" and inputMenu != "B" and inputMenu != "C" and inputMenu != "D" :
        print ("Menu tidak terdaftar")
        inputMenu = input ("Masukan Menu: ")
    
    inputJumlah = int(input ("Masukan jumlah: "))
    
    Memesan = Diskon(inputMenu,inputJumlah)
    a.addPesanan(Memesan)
    a.tampilkanPesanan()
    
    lup = input ("Apakah ingin melakukan pemesanan lainnya? (Y/T)")
```
