# Tugas-Besar-GIFT-COFB-Kelompok-8
Tugas Besar Kelompok 8 dengan beranggotakan Taufiq Hidayat (13221044), Muhammad Fikri (13221046), Daffa Muhammad Rasyid (13221060). Proyek ini adalah implementasi algoritma kriptografi algoritma GIFT-128 dengan metode Substitution-Permutation Network (SPN) dan skema encrypt dan otentikasi Combined Feedback (COFB).

## Deskripsi
GIFT-128 merupakan sebuah algoritma block cipher yang digunakan untuk mengacak data sehingga sulit dibaca oleh orang yang tidak memilik kunci enkripsi. Fungsi dari GIFT-128 adalah untuk melakukan enkripsi pada data plain text sehingga menghasilkan chiper text yang terenkripsi.

Proyek ini menggunakan bahasa pemrograman C dan mengimplementasikan algoritma GIFT-128 dengan metode Substitution-Permutation Network (SPN) dan skema encrypt dan otentikasi Combined Feedback (COFB).

### Algoritma GIFT-128
#### Input
Input dari GIFT-128 adalah data plain text berukuran 128 bit dan kunci enkripsi berukuran 128 bit.

#### Output
Output dari GIFT-128 adalah cipher text berukuran 128 bit yang diacak dan terenkripsi. Chiper text tersebut hanya dapat dibaca dengan menggunakan kunci enkripsi yang sama yang digunakan untuk enkripsi.

#### Proses Kerja
1. Data plain text memiliki panjang 128 bit yang dipecah menjadi 4 kali 32 bit kemudian diassign sebagai S, sedangkan data key dipecah menjadi ukuran 16 bit sebanyak 8 buah (diassign sebagai W).
2. Dilakukan proses substitusi dan permutasi sebelum akhirnya data dienkripsi dengan penambahan round key dan round constant.
3. Setelah algoritma berjalan selama 40 iterasi, akan menghasilkan data cipher dengan panjang 128 bit yang telah diacak dan siap digunakan.

#### Pseudocode
Plain_text ← 128 bits 
Key ← 128 bits
Round_Constant ← A[1..40] # dimana A mengandung konstanta dalam bentuk hexadecimal
S ← S[1..4] # 4 buah 32 bit dari Plain_text
W ← W[1..3] # 8 buah 16 bit dari Key
 
for i = 1 to 40 
    S ← Substitution(S) # tahap substitusi 
    S ← PermBits(S) # tahap permutasi 
    S ← AddRoundKey(RK) # penambahan round key
    S ← AddRoundConstant(S) # penambahan konstanta Round_Constant[i]
    
Cipher ← S

### Skema Encrypt dan Otentikasi COFB
COFB (Combined Feedback) adalah skema enkripsi dan otentikasi yang didasarkan pada blok cipher. Blok cipher yang digunakan adalah GIFT-128, yang digunakan untuk mengacak data sehingga sulit dibaca oleh orang yang tidak memiliki kunci enkripsi.

Input dari blok COFB adalah plain text yang ingin dienkripsi, data terkait (associated data) yang diberikan bersamaan dengan plain text, dan nonce (number only used once) yang berfungsi sebagai inisialisasi untuk menghindari pengulangan pengacakan.

Berikut adalah langkah-langkah untuk mengimplementasikan skema COFB menggunakan GIFT-128:

#### 1. Inisialisasi
Pilih sebuah kunci enkripsi acak yang memiliki ukuran 128-bit dan inisialisasi nonce. Kemudian, lakukan inisialisasi dengan menggunakan kunci enkripsi dan nonce sebagai masukan pada blok GIFT-128.

#### 2. Pengacakan
Untuk setiap blok plain text yang ingin dienkripsi, lakukan pengacakan (encryption) dengan menggunakan blok GIFT-128. Hasil pengacakan dari blok GIFT-128 kemudian di-XOR-kan dengan plain text untuk menghasilkan ciphertext.

#### 3. Penambahan Autentikasi
Setiap blok ciphertext akan ditambahkan autentikasi dengan melakukan operasi hash pada blok ciphertext yang telah di-XOR-kan dengan associated data. Autentikasi yang dihasilkan kemudian di-XOR-kan kembali dengan blok ciphertext untuk menghasilkan ciphertext yang telah ditambahkan autentikasi.

#### 4. Kembalikan Nilai
Setelah seluruh blok plain text telah dienkripsi dan ditambahkan autentikasi, kembalikan nilai kunci enkripsi, nonce, ciphertext yang telah ditambahkan autentikasi, dan autentikasi yang dihasilkan.

Dalam implementasi program menggunakan bahasa C, kita dapat menggunakan library yang menyediakan implementasi dari GIFT-128 dan COFB. Selain itu, kita juga dapat mengimplementasikan fungsi-fungsi pengacakan, operasi XOR, dan operasi hash untuk mengeksekusi langkah-langkah di atas.
