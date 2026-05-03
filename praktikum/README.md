<div align=center>

|    NRP     |           Nama             |
| :--------: |       :------------:       |
| 5025251032 | Nagita Aliya Sanopa          |
| 5025251064 | Mas Ayu Lana Afiah    |
| 5025251062 | Aisyah Putri Diza                 |
</div>
```python
import numpy as np
import matplotlib.pyplot as plt
```
1. import library yang akan digunakan seperti numpy untuk operasi matematika dan matplotlib untuk membuat grafik.

```
def f(x):
    return np.exp(-x) - x
```
2. Fungsi f(x) yang akan dicari akarnya.
   
```
def regula_falsi(x1, x2, toleransi=1e-6, max_iter=50):
    if f(x1) * f(x2) >= 0:
        print("Interval tidak valid (tidak ada perubahan tanda).")
        return None

    print("Iterasi |    x1    |    x2    |    x3    |   f(x3)   | Er (%)")
    print("------------------------------------------------------------------")

    x3_old = x1
    iter_data = []

    for i in range(1, max_iter + 1):
    
        x3 = x2 - (f(x2) * (x1 - x2)) / (f(x1) - f(x2))
        er = abs((x3 - x3_old) / x3) * 100 if i > 1 else 0

        print(f"{i:^7} | {x1:^8.5f} | {x2:^8.5f} | {x3:^8.5f} | {f(x3):^10.5f} | {er:^9.5f}")

        iter_data.append(x3)

        if abs(f(x3)) < toleransi:
            print("\nAkar ditemukan:", x3)
            return x3, iter_data

        if f(x1) * f(x3) < 0:
            x2 = x3
        else:
            x1 = x3

        x3_old = x3

    print("\nMaksimum iterasi tercapai.")
    return x3, iter_data
```
3. Fungsi regula falsi yang akan digunakan.

```
akar, data_iter = regula_falsi(0, 1)
```
4. Fungsi dipanggil untuk mencari akar di interval [0,1].
   
```
x = np.linspace(-1, 2, 400)
y = f(x)

plt.figure()
plt.axhline(0)  
plt.plot(x, y, label="f(x) = e^(-x) - x")


for xi in data_iter:
    plt.plot(xi, f(xi), 'ro')

plt.title("Grafik Metode Regula Falsi")
plt.xlabel("x")
plt.ylabel("f(x)")
plt.legend()
plt.grid()

plt.show()
```
5. Membuat grafik dengan menggunakan matplotlib
