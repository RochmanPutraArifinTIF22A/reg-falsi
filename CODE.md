# reg-falsi

def func(x):
    return x**2 - 6*x + 5

def regula_falsi(func, a, b, tol=1e-3, max_iter=100):
    if func(a) * func(b) >= 0:
        raise ValueError("Nilai fungsi pada kedua ujung interval harus memiliki tanda yang berbeda.")

    for i in range(max_iter):
        c = (a * func(b) - b * func(a)) / (func(b) - func(a))
        
        if abs(func(c)) < tol:
            return c  # Akar telah ditemukan dalam toleransi yang ditentukan.

        if func(a) * func(c) < 0:
            b = c
        else:
            a = c

    raise Exception("Metode Regula Falsi tidak konvergen dalam jumlah maksimum iterasi yang diberikan.")

# Penggunaan contoh:
a = 3
b = 6
tolerance = 0.001
max_iter = 7
root = regula_falsi(func, a, b, tolerance)

print(f"Akar perkiraan: {root}")
