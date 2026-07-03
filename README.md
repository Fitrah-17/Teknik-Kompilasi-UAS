# Teknik-Kompilasi-UAS

# Laporan Tahapan Kompilasi

## Deskripsi

Pada tugas ini dibuat simulasi sederhana proses kompilasi menggunakan bahasa **Python** dengan konstruksi **perulangan `while`**. Program merepresentasikan empat tahapan utama compiler, yaitu:

- Analisis Leksikal
- Analisis Sintaksis
- Analisis Semantik
- Generasi *Three-Address Code* (TAC)

---

# 1. Konstruksi yang Dipilih

Perulangan **`while`**.

Contoh input:

```text
while ( count < 5 ) {
    x = count
}
```

---

# 2. Pattern (BNF)

```text
<while_stmt> ::= "while" "(" <condition> ")" "{" <assignment> "}"

<condition> ::= <identifier> <operator> <value>

<assignment> ::= <identifier> "=" <value>
```

---

# 3. Tahapan Kompilasi

## Analisis Leksikal

Source code dipecah menjadi token.

**Hasil Token**

```text
['while', '(', 'count', '<', '5', ')', '{', 'x', '=', 'count', '}']
```

---

## Analisis Sintaksis

Token diperiksa sesuai grammar kemudian dibentuk menjadi **Abstract Syntax Tree (AST)**.

```
WhileNode
├── Condition : count < 5
└── Body      : x = count
```

---

## Analisis Semantik

Melakukan validasi:

- Variabel harus sudah dideklarasikan.
- Tipe data harus sesuai.

Jika variabel tidak ditemukan, program akan menampilkan **Semantic Error**.

---

## Generasi Three-Address Code (TAC)

Output TAC yang dihasilkan:

```text
L1:
if count < 5 goto L2
goto L3

L2:
x = count
goto L1

L3:
```

---

# 4. Kesimpulan

Program berhasil mensimulasikan proses dasar compiler untuk konstruksi **while**, mulai dari pemecahan token, pembentukan AST, validasi semantik, hingga menghasilkan **Three-Address Code (TAC)**.
