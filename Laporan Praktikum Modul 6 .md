# <h1 align="center">Laporan Praktikum Modul Single and Doubel Linked List</h1>
<p align="center">Yoka Romadani</p>
<p align="center">2311110060</p>>
<p align="center">SD04-B</p>

## Dasar Teori
Linked list merupakan salah satu struktur data yang digunakan untuk menyimpan kumpulan data secara berurutan. Dalam linked list, setiap elemen data disebut node, dan setiap node memiliki dua bagian utama: data itu sendiri, dan sebuah pointer yang menunjukkan ke node berikutnya dalam urutan. Konsep dasar linked list adalah bahwa setiap node terhubung satu sama lain dalam urutan tertentu, sehingga membentuk sebuah rantai.

Dalam single linked list, setiap node hanya memiliki satu pointer yang menunjuk ke node berikutnya dalam urutan. Ini berarti kita hanya dapat mengakses data secara sekuensial, dimulai dari node pertama (head) dan berlanjut ke node berikutnya hingga mencapai node terakhir (tail). Pada single linked list, akses mundur tidak langsung didukung, sehingga untuk mencapai node sebelumnya, kita harus mengunjungi setiap node dari awal.

Di sisi lain, double linked list memiliki dua pointer dalam setiap node, yang masing-masing menunjuk ke node sebelumnya dan node berikutnya dalam urutan. Hal ini memungkinkan kita untuk melakukan traversal baik dari depan ke belakang maupun sebaliknya, sehingga memberikan fleksibilitas lebih dalam manipulasi data. Dengan adanya pointer yang menunjuk ke node sebelumnya, penghapusan dan penambahan elemen di tengah linked list dapat dilakukan dengan lebih efisien, karena tidak perlu melakukan pencarian dari awal.

Kedua jenis linked list ini memiliki keunggulan dan kelemahan masing-masing, tergantung pada kebutuhan aplikasi. Single linked list biasanya lebih sederhana dalam implementasinya dan membutuhkan memori yang lebih sedikit, sementara double linked list memberikan kemampuan traversing maju dan mundur yang lebih fleksibel. Dalam kedua kasus, linked list sering digunakan untuk menyimpan dan mengelola data dinamis, di mana jumlah dan urutan datanya dapat berubah selama program berjalan.
## Guided
## 1. Program Array Tiga dimensi
```C++
#include <iostream>
using namespace std;

///PROGRAM SINGLE LINKED LIST NON-CIRCULAR
//Deklarasi Struct Node
struct Node{
    //komponen/member
    int data;
    Node *next;
};
    Node *head;
    Node *tail;
//Inisialisasi Node
void init(){
    head = NULL;
    tail = NULL;
}
// Pengecekan
bool isEmpty(){
    if (head == NULL)
    return true;
    else
    return false;
}
//Tambah Depan
void insertDepan(int nilai){
    //Buat Node baru
    Node *baru = new Node;
    baru->data = nilai;
    baru->next = NULL;
    if (isEmpty() == true){
        head = tail = baru;
        tail->next = NULL;
    }
    else{
        baru->next = head;
        head = baru;
    }
}
//Tambah Belakang
void insertBelakang(int nilai){
    //Buat Node baru
    Node *baru = new Node;
    baru->data = nilai;
    baru->next = NULL;
    if (isEmpty() == true){
        head = tail = baru;
        tail->next = NULL;
    }
    else{
    tail->next = baru;
    tail = baru;
    }
}
//Hitung Jumlah List
int hitungList(){
    Node *hitung;
    hitung = head;
    int jumlah = 0;
    while( hitung != NULL ){
        jumlah++;
        hitung = hitung->next;
    }
    return jumlah;
}
//Tambah Tengah
void insertTengah(int data, int posisi){
    if( posisi < 1 || posisi > hitungList() ){
        cout << "Posisi diluar jangkauan" << endl;
    }
    else if( posisi == 1){
        cout << "Posisi bukan posisi tengah" << endl;
    }
    else{
        Node *baru, *bantu;
        baru = new Node();
        baru->data = data;
        // tranversing
            bantu = head;
            int nomor = 1;
        while( nomor < posisi - 1 ){
            bantu = bantu->next;
            nomor++;
        }
        baru->next = bantu->next;
        bantu->next = baru;
    }
}
//Hapus Depan
void hapusDepan() {
    Node *hapus;
    if (isEmpty() == false){
        if (head->next != NULL){
            hapus = head;
            head = head->next;
            delete hapus;
        }
        else{
            head = tail = NULL;
        }
    }
    else{
        cout << "List kosong!" << endl;
    }
}
//Hapus Belakang
void hapusBelakang() {
    Node *hapus;
    Node *bantu;
    if (isEmpty() == false){
        if (head != tail){
            hapus = tail;
            bantu = head;
            while (bantu->next != tail){
                bantu = bantu->next;
            }
            tail = bantu;
            tail->next = NULL;
        delete hapus;
        }
        else{
            head = tail = NULL;
        }
    }
    else{
        cout << "List kosong!" << endl;
    }
}
//Hapus Tengah
void hapusTengah(int posisi){
    Node *hapus, *bantu, *bantu2;
    if( posisi < 1 || posisi > hitungList() ){
        cout << "Posisi di luar jangkauan" << endl;
    }
    else if( posisi == 1){
        cout << "Posisi bukan posisi tengah" << endl;
    }
    else{
        int nomor = 1;
        bantu = head;
        while( nomor <= posisi ){
            if( nomor == posisi-1 ){
                bantu2 = bantu;
            }
            if( nomor == posisi ){
                hapus = bantu;
            }
            bantu = bantu->next;
            nomor++;
        }
        bantu2->next = bantu;
    delete hapus;
    }
}
//Ubah Depan
void ubahDepan(int data){
    if (isEmpty() == false){
        head->data = data;
    }
    else{
        cout << "List masih kosong!" << endl;
    }
}
//Ubah Tengah
void ubahTengah(int data, int posisi){
    Node *bantu;
    if (isEmpty() == false){
        if( posisi < 1 || posisi > hitungList() ){
            cout << "Posisi di luar jangkauan" << endl;
        }
        else if( posisi == 1){
            cout << "Posisi bukan posisi tengah" << endl;
        }
        else{
            bantu = head;
            int nomor = 1;
            while (nomor < posisi){
                bantu = bantu->next;nomor++;
            }
            bantu->data = data;
        }
    }
    else{
        cout << "List masih kosong!" << endl;
    }
}
//Ubah Belakang
void ubahBelakang(int data){
    if (isEmpty() == false){
        tail->data = data;
    }
    else{
        cout << "List masih kosong!" << endl;
    }
}
//Hapus List
void clearList(){
    Node *bantu, *hapus;
    bantu = head;
    while (bantu != NULL){
        hapus = bantu;
        bantu = bantu->next;
        delete hapus;
    }
    head = tail = NULL;
    cout << "List berhasil terhapus!" << endl;
}
//Tampilkan List
void tampil(){
    Node *bantu;
    bantu = head;
    if (isEmpty() == false){
        while (bantu != NULL){
            cout << bantu->data << ends;
            bantu = bantu->next;
        }
        cout << endl;
    }
    else{
        cout << "List masih kosong!" << endl;
    }
}
int main(){
    init();
    insertDepan(3);tampil();
    insertBelakang(5);
    tampil();
    insertDepan(2);
    tampil();
    insertDepan(1);
    tampil();
    hapusDepan();
    tampil();
    hapusBelakang();
    tampil();
    insertTengah(7,2);
    tampil();
    hapusTengah(2);
    tampil();
    ubahDepan(1);
    tampil();
    ubahBelakang(8);
    tampil();
    ubahTengah(11, 2);
    tampil();
    return 0;
}

```
### Output
![Screenshot 2024-06-12 082214](https://github.com/yokaroo/Praktikum-Struktur-Data-Asignment-Modul2/blob/main/Screenshot%202024-06-12%20082214.png)
## Iterpretasi
Kode program ini mendeklarasikan sebuah array 3 dimensi berukuran 2x3x3 dan meminta pengguna untuk mengisi setiap elemen array melalui input. Program menggunakan tiga loop bersarang untuk mengakses setiap elemen array dan mengisi nilainya. Setelah semua nilai diinput, program menampilkan nilai-nilai tersebut dalam dua format: pertama, dengan menunjukkan indeks setiap elemen dan nilainya, dan kedua, dengan menampilkan elemen-elemen array dalam bentuk baris dan kolom yang lebih mudah dibaca. Program kemudian mengakhiri dengan return 0, menandakan bahwa program selesai dijalankan dengan sukses.

## 2. Program Mencari Nilai Maksimal Pada Aray
```C++
#include <iostream>
using namespace std;

int main() {
    int maks, a, lokasi;
    cout << "Masukkan panjang array: ";
    cin >> a;
    int array[a];

    cout << "Masukkan " << a << " angka\n";
    for (int i = 0; i < a; i++) {
        cout << "Array ke-" << i << ": ";
        cin >> array[i];
    }

    maks = array[0];
    lokasi = 0;  // Inisialisasi lokasi dengan indeks pertama

    for (int i = 1; i < a; i++) {  // Mulai dari indeks ke-1 karena maks sudah diinisialisasi dengan array[0]
        if (array[i] > maks) {
            maks = array[i];
            lokasi = i;
        }
    }

    cout << "Nilai maksimum adalah " << maks << " berada di Array ke-" << lokasi << endl;

    return 0;
}
```
## Output
![Screenshot 2024-06-12 083334](https://github.com/yokaroo/Praktikum-Struktur-Data-Asignment-Modul2/blob/main/Screenshot%202024-06-12%20083334.png)
## Interpretasi Code
Kode tersebut adalah sebuah program C++ yang mencari nilai maksimum dalam sebuah array yang dimasukkan oleh pengguna. Program ini meminta pengguna untuk memasukkan panjang array dan kemudian mengisi array dengan angka-angka yang diinput oleh pengguna. Setelah array terisi, program mencari nilai maksimum dalam array tersebut dengan memulai perbandingan dari elemen kedua (indeks 1) hingga elemen terakhir. Jika ditemukan nilai yang lebih besar daripada nilai maksimum saat ini, nilai tersebut akan menjadi nilai maksimum yang baru, dan lokasinya (indeks) akan diperbarui. Akhirnya, program menampilkan nilai maksimum dan indeksnya kepada pengguna.

### UnGuided
## 1. Buatlah program untuk menampilkan output seperti berikut dengan data yang ditampilkan user
```C++
//Menggunakan library input/output dan struktur data
#include <iostream>
#include <sstream>
#include <vector>
using namespace std;

//Membuat kode inti atau main code
int main() {
    string name; // membuat variabel
    //membuat vektor bertipe integer
    vector<int> numbers;
    vector<int> evenNumbers;
    vector<int> oddNumbers;
    
    //meminta inputan
    cout << "Masukkan nama Anda:" << endl;
    getline(cin, name);
    cout<<endl;
    //Menyapa pengguna dan meminta inputan angka
    cout<<"Halo, "<< name << ". Selamat datang di Program pemilihan angka genap dan ganjil." << endl<<endl;
    cout << "Masukkan angka anda, pisahkan dengan spasi!" << endl;
    cout << "Klik enter untuk menampilkan hasil !" << endl;
    string input;
    getline(cin, input);
    
    // Membaca angka-angka dari baris input
    stringstream ss(input);
    int num;
    while (ss >> num) {
        numbers.push_back(num);
    }
    
    // Memisahkan angka genap dan ganjil dari inputan pengguna
    for (int num : numbers) {
        if (num % 2 == 0) { //menggunakan modulus
            evenNumbers.push_back(num);  //jika habis di bagi 2 masuk ke sini
        } else {
            oddNumbers.push_back(num); //jika tidak habis masuk kesini
        }
    }
    
    // Menampilkan angka-angka genap
    cout << "Angka genap: ";
    for (int num : evenNumbers) {
        cout << num << " ";
    }
    cout << endl;
    
    // Menampilkan angka-angka ganjil
    cout << "Angka ganjil: ";
    for (int num : oddNumbers) {
        cout << num << " ";
    }
    cout << endl<<endl;
    
    return 0;
}
```
### Output
![Screenshot 2024-06-12 094446](https://github.com/yokaroo/Praktikum-Struktur-Data-Asignment-Modul2/blob/main/Screenshot%202024-06-12%20094446.png)

## 2. Buatlah program Input array tiga dimensi (seperti pada guided) tetapi jumlah atau ukuran elemennya diinputkan oleh user!
```C++
#include <iostream>
using namespace std;

int main() {
    int x, y, z;

    // Meminta pengguna untuk memasukkan ukuran array
    cout << "Masukkan jumlah baris: ";
    cin >> x;
    cout << "Masukkan jumlah kolom: ";
    cin >> y;
    cout << "Masukkan jumlah depth: ";
    cin >> z;

    // Deklarasi array tiga dimensi
    int arr[x][y][z];

    // Input elemen array
    cout << "Masukkan elemen-elemen array:\n";
    for (int i = 0; i < x; ++i) {
        for (int j = 0; j < y; ++j) {
            for (int k = 0; k < z; ++k) {
                cout << "Array[" << i << "][" << j << "][" << k << "]: ";
                cin >> arr[i][j][k];
            }
        }
    }

    // Output elemen array
    cout << "\nElemen-elemen array yang dimasukkan:\n";
    for (int i = 0; i < x; ++i) {
        for (int j = 0; j < y; ++j) {
            for (int k = 0; k < z; ++k) {
                cout << "Array[" << i << "][" << j << "][" << k << "]: " << arr[i][j][k] << endl;
            }
        }
    }

    return 0;
}

```

## Output
![Screenshot 2024-06-12 094933.png](https://github.com/yokaroo/Praktikum-Struktur-Data-Asignment-Modul2/blob/main/Screenshot%202024-06-12%20094933.png)

### 3.  Buatlah program menu untuk mencari nilai Maksimum, Minimum dan Nilai rata– rata dari suatu array dengan input yang dimasukan oleh user
```C++
#include <iostream>
#include <climits> // Untuk menggunakan konstanta INT_MIN dan INT_MAX
using namespace std;

int main() {
    int n;

    // Meminta pengguna untuk memasukkan jumlah elemen array
    cout << "Masukkan jumlah elemen array: ";
    cin >> n;

    // Membuat array untuk menyimpan elemen-elemen yang dimasukkan oleh pengguna
    int arr[n];

    // Meminta pengguna untuk memasukkan elemen-elemen array
    cout << "Masukkan elemen-elemen array:\n";
    for (int i = 0; i < n; ++i) {
        cout << "Elemen " << i + 1 << ": ";
        cin >> arr[i];
    }

    // Mencari nilai maksimum, minimum, dan rata-rata
    int maksimum = INT_MIN;
    int minimum = INT_MAX;
    int total = 0;

    for (int i = 0; i < n; ++i) {
        if (arr[i] > maksimum) {
            maksimum = arr[i];
        }
        if (arr[i] < minimum) {
            minimum = arr[i];
        }
        total += arr[i];
    }

    double rata_rata = static_cast<double>(total) / n;

    // Menampilkan hasil
    cout << "\nNilai Maksimum: " << maksimum << endl;
    cout << "Nilai Minimum: " << minimum << endl;
    cout << "Nilai Rata-rata: " << rata_rata << endl;

    return 0;
}
```
## output
![Screenshot 2024-06-12 095423](https://github.com/yokaroo/Praktikum-Struktur-Data-Asignment-Modul2/blob/main/Screenshot%202024-06-12%20095423.png)

### Kesimpulan 
Dengan pemahaman tentang berbagai jenis array ini, kita dapat lebih efektif menggunakan dan memahami struktur data yang kompleks dan penggunaannya dalam pemrograman. Array merupakan fondasi yang penting dalam mempelajari struktur data lainnya dan memiliki peran yang krusial dalam pengembangan perangkat lunak.
