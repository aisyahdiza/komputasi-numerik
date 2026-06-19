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

### 4.
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
