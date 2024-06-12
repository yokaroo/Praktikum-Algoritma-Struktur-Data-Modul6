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
## 1. Latihan Single Linked list
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
![Screenshot 2024-06-12 234852](https://github.com/yokaroo/Praktikum-Algoritma-Struktur-Data-Modul6/blob/main/Screenshot%202024-06-12%20234852.png)
## Iterpretasi
Program di atas merupakan implementasi dari single linked list non-circular dalam bahasa C++. Single linked list merupakan struktur data linear yang terdiri dari serangkaian node, dimana setiap node memiliki data dan pointer yang menunjuk ke node berikutnya. Pada program ini, terdapat beberapa fungsi yang dapat dilakukan terhadap linked list seperti penambahan elemen di depan, di belakang, dan di tengah, penghapusan elemen di depan, di belakang, dan di tengah, serta pengubahan nilai elemen di depan, di belakang, dan di tengah.

Pertama, program memuat definisi struktur `Node` yang berisi data dan pointer `next`. Kemudian, terdapat fungsi `init()` untuk menginisialisasi `head` dan `tail` sebagai NULL. Fungsi `isEmpty()` digunakan untuk mengecek apakah linked list kosong atau tidak. Terdapat pula fungsi-fungsi untuk menambahkan elemen di depan (`insertDepan()`), di belakang (`insertBelakang()`), dan di tengah (`insertTengah()`), serta fungsi-fungsi untuk menghapus elemen di depan (`hapusDepan()`), di belakang (`hapusBelakang()`), dan di tengah (`hapusTengah()`).

Selain itu, terdapat fungsi-fungsi untuk mengubah nilai elemen di depan (`ubahDepan()`), di belakang (`ubahBelakang()`), dan di tengah (`ubahTengah()`). Fungsi `clearList()` digunakan untuk menghapus seluruh elemen dalam linked list. Terakhir, fungsi `tampil()` digunakan untuk menampilkan seluruh elemen dalam linked list. Dalam fungsi `main()`, berbagai operasi seperti penambahan, penghapusan, dan pengubahan elemen dilakukan untuk menguji fungsi-fungsi yang telah didefinisikan sebelumnya.
## 2. Latihan Double Linked List
```C++
#include <iostream>
using namespace std;

class Node {
    public:int data;
    Node* prev;
    Node* next;
};
class DoublyLinkedList {
        public:
        Node* head;
        Node* tail;
        DoublyLinkedList() {
            head = nullptr;
            tail = nullptr;
    }
    void push(int data) {
        Node* newNode = new Node;
        newNode->data = data;
        newNode->prev = nullptr;
        newNode->next = head;
        if (head != nullptr) {
            head->prev = newNode;
        }
        else {
            tail = newNode;
        }
        head = newNode;
    }
    void pop() {
        if (head == nullptr) {
            return;
        }
        Node* temp = head;
        head = head->next;
        if (head != nullptr) {
            head->prev = nullptr;
        }
        else {
            tail = nullptr;
        }
        delete temp;
    }
    bool update(int oldData, int newData) {
        Node* current = head;while (current != nullptr) {
            if (current->data == oldData) {
                current->data = newData;
                return true;
            }
            current = current->next;
        }
        return false;
    }
    void deleteAll() {
        Node* current = head;
        while (current != nullptr) {
            Node* temp = current;
            current = current->next;
            delete temp;
        }
        head = nullptr;
        tail = nullptr;
    }
    void display() {
        Node* current = head;
        while (current != nullptr) {
            cout << current->data << " ";
            current = current->next;
        }
        cout << endl;
    }
};

int main() {
    DoublyLinkedList list;
    while (true) {
        cout << "1. Add data" << endl;
        cout << "2. Delete data" << endl;
        cout << "3. Update data" << endl;
        cout << "4. Clear data" << endl;
        cout << "5. Display data" << endl;
        cout << "6. Exit" << endl;int choice;
        cout << "Enter your choice: ";
        cin >> choice;
        switch (choice) {
            case 1: {
                int data;
                cout << "Enter data to add: ";
                cin >> data;
                list.push(data);
                break;
            }
            case 2: {
                list.pop();
                break;
            }
            case 3: {
                int oldData, newData;
                cout << "Enter old data: ";
                cin >> oldData;
                cout << "Enter new data: ";
                cin >> newData;
                bool updated = list.update(oldData, newData);
                if (!updated) {
                    cout << "Data not found" << endl;
                }
                break;
            }
            case 4: {
                list.deleteAll();
                break;
            }
            case 5: {
                list.display();
                break;
            }
            case 6: {
                return 0;
            }
            default: {
                cout << "Invalid choice" << endl;
                break;
            }
        }
    }
    return 0;
}


```
## Output
![Screenshot 2024-06-12 235856](https://github.com/yokaroo/Praktikum-Algoritma-Struktur-Data-Modul6/blob/main/Screenshot%202024-06-12%20235856.png)
## Interpretasi Code
Kode di atas adalah implementasi dari Doubly Linked List menggunakan C++. Doubly Linked List adalah struktur data linear di mana setiap elemen, yang disebut node, memiliki dua pointer, yaitu pointer ke node sebelumnya (prev) dan pointer ke node berikutnya (next). 

Pertama, program mendefinisikan dua kelas: `Node` dan `DoublyLinkedList`. Kelas `Node` merepresentasikan setiap elemen dalam Doubly Linked List dengan tiga anggota data: `data` (untuk menyimpan nilai), `prev` (untuk menyimpan alamat node sebelumnya), dan `next` (untuk menyimpan alamat node berikutnya). Kelas `DoublyLinkedList` menyediakan berbagai metode untuk memanipulasi Doubly Linked List, seperti menambah, menghapus, memperbarui, dan menampilkan elemen-elemen dalam list.

Di dalam fungsi `main`, program memberikan opsi kepada pengguna untuk memilih aksi yang ingin dilakukan pada Doubly Linked List. Opsi termasuk menambah data baru, menghapus data, memperbarui data, membersihkan seluruh data, menampilkan data, dan keluar dari program. Setiap opsi diproses melalui `switch-case`, di mana aksi yang dipilih oleh pengguna akan memanggil metode yang sesuai dari objek `DoublyLinkedList`. Selama program berjalan, pengguna akan terus diberi opsi untuk melakukan aksi pada Doubly Linked List hingga mereka memilih untuk keluar dari program.

### UnGuided
## 1. Buatlah program menu Single Linked List Non-Circular untuk menyimpan Nama dan usia mahasiswa, dengan menggunakan inputan dari user. Lakukan operasi berikut:
![Screenshot 2024-06-13 001132](https://github.com/yokaroo/Praktikum-Algoritma-Struktur-Data-Modul6/blob/main/Screenshot%202024-06-13%20001132.png)
```C++
// Yoka Romadani
// 2311110060

#include <iostream>
using namespace std;

// deklarasi struct node
struct Node {
    string nama;
    int usia;
    Node* next;
};

// deklarasi head node
Node* head = NULL;

// fungsi untuk menambahkan node di awal
void tambahDiAwal(string nama, int usia) {
    Node* newNode = new Node;
    newNode->nama = nama;
    newNode->usia = usia;
    newNode->next = head;
    head = newNode;
}

// fungsi untuk menambahkan node di akhir
void tambahDiAkhir(string nama, int usia) {
    Node* newNode = new Node;
    newNode->nama = nama;
    newNode->usia = usia;
    newNode->next = NULL;

    if (head == NULL) {
        head = newNode;
        return;
    }

    Node* curr = head;
    while (curr->next != NULL) {
        curr = curr->next;
    }
    curr->next = newNode;
}

// fungsi untuk menambahkan node di tengah
void tambahDiTengah(string nama, int usia, int pos) {
    Node* newNode = new Node;
    newNode->nama = nama;
    newNode->usia = usia;
    newNode->next = NULL;

    if (head == NULL) {
        head = newNode;
        return;
    }

    Node* curr = head;
    int i = 1;
    while (i < pos-1 && curr->next != NULL) {
        curr = curr->next;
        i++;
    }
    newNode->next = curr->next;
    curr->next = newNode;
}

// fungsi untuk menghapus node dengan nama tertentu
void hapus(string nama) {
    Node* curr = head;
    Node* prev = NULL;

    while (curr != NULL && curr->nama != nama) {
        prev = curr;
        curr = curr->next;
    }

    if (curr == NULL) {
        cout << "Data tidak ditemukan" << endl;
        return;
    }

    if (prev == NULL) {
        head = curr->next;
    } else {
        prev->next = curr->next;
    }

    delete curr;
}

// fungsi untuk mengubah data node dengan nama tertentu
void ubah(string nama, string newNama, int newUsia) {
    Node* curr = head;

    while (curr != NULL && curr->nama != nama) {
        curr = curr->next;
    }

    if (curr == NULL) {
        cout << "Data tidak ditemukan" << endl;
        return;
    }

    curr->nama = newNama;
    curr->usia = newUsia;
}

// fungsi untuk menampilkan semua data
void tampilkan() {
    if (head == NULL) {
        cout << "List kosong" << endl;
        return;
    }

    Node* curr = head;

    while (curr != NULL) {
        cout << curr->nama << " " << curr->usia << endl;
        curr = curr->next;
    }
}

int main() {
    // memasukkan data pertama (nama dan usia anda)
    string namaAnda;
    int usiaAnda;
    cout << "Masukkan nama anda: ";
    cin >> namaAnda;
    cout << "Masukkan usia anda: ";
    cin >> usiaAnda;
    tambahDiAwal(namaAnda, usiaAnda);
    // memasukkan data lainnya
tambahDiAkhir("John", 19);
tambahDiAkhir("Jane", 20);
tambahDiAkhir("Michael", 18);
tambahDiAkhir("Yusuke", 19);
tambahDiAkhir("Akechi", 20);
tambahDiAkhir("Hoshino", 18);
tambahDiAkhir("Karin", 18);

// menampilkan semua data
cout << "Data awal:" << endl;
tampilkan();

// menghapus data Akechi
hapus("Akechi");
cout << endl << "Setelah menghapus Akechi: " << endl;
tampilkan();

// menambahkan data Futaba di antara Carol dan Ann
tambahDiTengah("Futaba", 18, 3);
cout << endl << "Setelah menambahkan Futaba di antara John dan Jane: " << endl;
tampilkan();

// menambahkan data Igor di awal
tambahDiAwal("Igor", 20);
cout << endl << "Setelah menambahkan Igor di awal: " << endl;
tampilkan();

// mengubah data Carol menjadi Reyn
ubah("Michael", "Reyn", 18);
cout << endl << "Setelah mengubah Michael menjadi Reyn: " << endl;
tampilkan();

// menampilkan semua data setelah perubahan
cout << endl << "Data setelah perubahan:" << endl;
tampilkan();

return 0;
}
```
### Output
![Screenshot 2024-06-13 000658](https://github.com/yokaroo/Praktikum-Algoritma-Struktur-Data-Modul6/blob/main/Screenshot%202024-06-13%20000658.png)
![Screenshot 2024-06-13 000713](https://github.com/yokaroo/Praktikum-Algoritma-Struktur-Data-Modul6/blob/main/Screenshot%202024-06-13%20000713.png)

## 2. Modifikasi Guided Double Linked List dilakukan dengan penambahan operasi untuk menambah data, menghapus, dan update di tengah / di urutan tertentu yang diminta. Selain itu, buatlah agar tampilannya menampilkan Nama produk dan harga
![Screenshot 2024-06-13 001308](https://github.com/yokaroo/Praktikum-Algoritma-Struktur-Data-Modul6/blob/main/Screenshot%202024-06-13%20001308.png)
```C++

#include <iostream>
#include <iomanip>

using namespace std;

struct Node {
    string nama_produk;
    int harga;
    Node* prev;
    Node* next;
};

class LinkedList {
private:
    Node* head;
    Node* tail;
public:
    LinkedList() {
        head = NULL;
        tail = NULL;
    }
    void tambahData(string nama_produk, int harga) {
        Node* newNode = new Node;
        newNode->nama_produk = nama_produk;
        newNode->harga = harga;
        newNode->prev = NULL;
        newNode->next = NULL;
        if (head == NULL) {
            head = newNode;
            tail = newNode;
        }
        else {
            tail->next = newNode;
            newNode->prev = tail;
            tail = newNode;
        }
    }
    void hapusData(string nama_produk) {
        Node* currentNode = head;
        while (currentNode != NULL) {
            if (currentNode->nama_produk == nama_produk) {
                if (currentNode == head) {
                    head = head->next;
                    head->prev = NULL;
                }
                else if (currentNode == tail) {
                    tail = tail->prev;
                    tail->next = NULL;
                }
                else {
                    currentNode->prev->next = currentNode->next;
                    currentNode->next->prev = currentNode->prev;
                }
                delete currentNode;
                break;
            }
            currentNode = currentNode->next;
        }
    }
    void updateData(string nama_produk, string new_nama_produk, int new_harga) {
        Node* currentNode = head;
        while (currentNode != NULL) {
            if (currentNode->nama_produk == nama_produk) {
                currentNode->nama_produk = new_nama_produk;
                currentNode->harga = new_harga;
                break;
            }
            currentNode = currentNode->next;
        }
    }
    void tambahDataUrutan(string nama_produk, int harga, int urutan) {
        Node* newNode = new Node;
        newNode->nama_produk = nama_produk;
        newNode->harga = harga;
        newNode->prev = NULL;
        newNode->next = NULL;
        if (urutan == 1) {
            newNode->next = head;
            head->prev = newNode;
            head = newNode;
        }
        else {
            Node* currentNode = head;
            int i = 1;
            while (i < urutan - 1) {
                currentNode = currentNode->next;
                i++;
            }
            newNode->prev = currentNode;
            newNode->next = currentNode->next;
            currentNode->next->prev = newNode;
            currentNode->next = newNode;
        }
    }
    void hapusDataUrutan(int urutan) {
        if (urutan == 1) {
            head = head->next;
            head->prev = NULL;
        }
        else {
            Node* currentNode = head;
            int i = 1;
            while (i < urutan) {
                currentNode = currentNode->next;
                i++;
            }
            if (currentNode == tail) {
                tail = tail->prev;
                tail->next = NULL;
            }
            else {
                currentNode->prev->next = currentNode->next;
                currentNode->next->prev = currentNode->prev;
            }
        }
    }
    void hapusSeluruhData() {
        while (head != NULL) {
            Node* currentNode = head;
            head = head->next;
            delete currentNode;
        }
        tail = NULL;
    } // <-- add closing bracket here


    void tampilkanData() {
        Node* currentNode = head;
        cout << setw(15) <<left<< "Nama Produk" << setw(10)<<"Harga"<< endl;
        while (currentNode != NULL) {
            cout <<  setw(15) << left <<  currentNode->nama_produk << setw(10) << currentNode->harga << endl;
            currentNode = currentNode->next;
        }
    }
    void tampilkanMenu() {
        int pilihan, harga, urutan;
        string nama_produk, new_nama_produk;
        cout << "Toko Lego Cilacap" << endl;
        cout << "1. Tambah Data" << endl;
        cout << "2. Hapus Data" << endl;
        cout << "3. Update Data" << endl;
        cout << "4. Tambah Data Urutan Tertentu" << endl;
        cout << "5. Hapus Data Urutan Tertentu" << endl;
        cout << "6. Hapus Seluruh Data" << endl;
        cout << "7. Tampilkan Data" << endl;
        cout << "8. Exit" << endl;
        do {
            cout << "Pilih menu: ";
            cin >> pilihan;
            switch (pilihan) {
            case 1:
                cout << "Masukkan Nama Produk: ";
                cin >> nama_produk;
                cout << "Masukkan Harga: ";
                cin >> harga;
                tambahData(nama_produk, harga);
                break;
            case 2:
                cout << "Masukkan Nama Produk yang akan dihapus: ";
                cin >> nama_produk;
                hapusData(nama_produk);
                break;
            case 3:
                cout << "Masukkan Nama Produk yang akan diupdate: ";
                cin >> nama_produk;
                cout << "Masukkan Nama Produk baru: ";
                cin >> new_nama_produk;
                cout << "Masukkan Harga baru: ";
                cin >> harga;
                updateData(nama_produk, new_nama_produk, harga);
                break;
            case 4:
                cout << "Masukkan Nama Produk: ";
                cin >> nama_produk;
                cout << "Masukkan Harga: ";
                cin >> harga;
                cout << "Masukkan Urutan: ";
                cin >> urutan;
                tambahDataUrutan(nama_produk, harga, urutan);
                break;
            case 5:
                cout << "Masukkan Urutan: ";
                cin >> urutan;
                hapusDataUrutan(urutan);
                break;
            case 6:
                hapusSeluruhData();
                break;
            case 7:
                tampilkanData();
                break;
            case 8:
                cout << "Terima kasih." << endl;
                break;
            default:
                cout << "Pilihan tidak tersedia." << endl;
            }
        } while (pilihan != 8);
    }
};

int main() {
    LinkedList list;
    list.tambahData ("Batman",60000);
    list.tambahData ("Superman",150000);
    list.tambahData ("HULK",100000);
    list.tambahData ("FLASH"   ,50000);
    list.tambahData ("Joker"  ,30000);
    list.tampilkanMenu();
    return 0;
}
```

## Output
![Screenshot 2024-06-13 002841](https://github.com/yokaroo/Praktikum-Algoritma-Struktur-Data-Modul6/blob/main/Screenshot%202024-06-13%20002841.png)
![Screenshot 2024-06-13 002852](https://github.com/yokaroo/Praktikum-Algoritma-Struktur-Data-Modul6/blob/main/Screenshot%202024-06-13%20002852.png)

## Kesimpulan
Linked List adalah struktur data yang terdiri dari sejumlah elemen data yang terhubung satu sama lain melalui tautan atau pointer. Dalam Single Linked List, setiap elemen atau node memiliki satu tautan yang mengarah ke node berikutnya dalam urutan linear. Di sisi lain, Double Linked List memiliki dua tautan untuk setiap node: satu mengarah ke node sebelumnya dan satu lagi mengarah ke node berikutnya. Keuntungan utama dari Double Linked List adalah kemampuannya untuk melakukan traversal maju dan mundur dengan mudah, sementara kekurangannya adalah penggunaan memori yang lebih besar karena setiap node membutuhkan penyimpanan tambahan untuk menunjuk ke node sebelumnya. Sementara itu, Single Linked List lebih efisien dalam penggunaan memori karena hanya memiliki satu tautan untuk setiap node, namun sulit untuk melakukan traversal mundur. Baik Single maupun Double Linked List cocok digunakan untuk implementasi struktur data yang memerlukan penambahan atau penghapusan elemen secara dinamis tanpa memerlukan alokasi memori statis seperti pada array.
