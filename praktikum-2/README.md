<div align=center>

|    NRP     |           Nama             |
| :--------: |       :------------:       |
| 5025251032 | Nagita Aliya Sanopa          |
| 5025251064 | Mas Ayu Lana Afiah    |
| 5025251062 | Aisyah Putri Diza                 |
</div>

### 1. Import Library
```
import math
```
Library math digunakan untuk memasukkan fungsi matematika.

### 2. Evaluasi Nilai Fungsi
```
def f(x, rumus):
    try:
        return eval(rumus, {"math": math, "x": x})
    except:
        return 0
```
Fungsi tersebut digunakan untuk mengevaluasi nilai fungsi pada suatu titik x. Perintah `eval()` digunakan untuk mengubah string menjadi ekspresi matematika yang dapat dihitung. Apabila terdapat kesalahan pada rumus, maka fungsi akan mengembalikan nilai 0.

### 3. Menghitung Integral
```
def hitung_trap(a, b, n, rumus):
    h = (b - a) / n
    hasil = 0.5 * (f(a, rumus) + f(b, rumus))
    for i in range(1, n):
        hasil += f(a + i * h, rumus)
    return hasil * h
```
Fungsi `hitung_trap` akan menghitung integral menggunakan metode Trapezoidal.
a = batas bawah
b = batas atas
n = segmen
h = lebar interval
hasil = setengah dari nilai ujung kiri + ujung kanan
Setelah mendapatkan nilai awal, jumlahkan seluruh titik tengah dengan looping for sebanyak n kali yang berisi `hasil += f(a + i * h, rumus)`. Setelah itu kalikan dengan lebar interval sesuai dengan rumus trapezoida.

### 4. Fungsi main()
```
def main():
    print("Perbandingan Metode Trapezoidal vs Romberg\n")

    rumus = input("Masukkan fungsi f(x): ")
    a = float(input("Batas bawah: "))
    b = float(input("Batas atas: "))

    trap_2 = hitung_trap(a, b, 2, rumus)
    trap_4 = hitung_trap(a, b, 4, rumus)

    romberg = trap_4 + (trap_4 - trap_2) / 3

    trap_50 = hitung_trap(a, b, 50, rumus)

    print("\nHasil Perhitungan:")
    print(f"Trapezoidal (n = 2)  : {trap_2:.8f}")
    print(f"Trapezoidal (n = 4)  : {trap_4:.8f}")
    print(f"Hasil Romberg        : {romberg:.8f}")
    print(f"Trapezoidal (n = 50) : {trap_50:.8f}")

if __name__ == "__main__":
    main()
```
Fungsi main berfungsi untuk membandingkan metode trapezoidal dan romberg. Rumus, batas bawah, dan batas atas yang digunakan berdasarkan input yang dimasukkan oleh user. 
trap_2 menggunakan 2 bagian interval.
trap_4 menggunakan 4 bagian interval sehingga setiap subinterval semakin kecil.
trap_50 terbagi menjadi 50 bagian, nilai ini hanya sebagai pembanding yang cukup akurat.
romberg menggunakan hasil trapezoidal yang sudah ada dan menghilangkan sebagian besar errornya dengan cara `trap_4 + (trap_4 - trap_2) / 3`.
