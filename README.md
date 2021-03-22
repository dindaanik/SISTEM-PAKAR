# SISTEM-PAKAR
#include <conio.h>
peryataan conio.h. adalah library pada C yang digunakan untuk mengkoneksikan pernyataan clrscr() dengan program yang kita buat. Tanpa menggunakan library ini, kita tidak bisa menggunakan fungsi prototype seperti: gotoxy(), clrscr(), clreol().

#include <stdio.h>
Pernyataan di atas digunakan sebagai standard library yang berfungsi untuk I/O  package maksudnya digunakan jika kita ingin pada program kita menggunakan fungsi standard input atau output bisa dikatakan seperti portable input/output package. Tanpa menggunakan library ini, kita tidak bisa menggunakan perintah-perintah input/output pada program kita.

void add(int item); 
void bfs(int s, int n);
void dfs(int s, int n); 
void push(int item);
Pernyataan di atas digunakan untuk mendefinisikan procedure untuk, antrian penuh (void add), perhitungan bfs (void bfs), perhitungan dfs (void dfs) dan jika terjadi kelebihan data (void push).

main() {
Pernyataan di atas adalah main procedure (prosedur utama dalam program ini). Fungsinya sama seperti public.static.void.main(String args[]) { pada bahasa pemrograman java.

clrscr();
Pernyataan di atas digunakan untuk membersihkan layar ketika program dieksekusi.

int n,i,s,ch,j;
Pernyataan diatas digunakan untuk mendeklarasikan variable n, i, s, ch dan j yang bertipe data integer (bilangan bulat).

printf("matriks adjasensi\n ");
Pernyataan printf di atas digunakan untuk mencetak tulisan yang ada diantara tanda kutip “ ”, yaitu Algoritma Brute Force. Pernyataan \n digunakan agar tulisan utama yang dicetak ada jedanya (enter) pada saat program dieksekusi.

scanf("%d",&n);
Pernyataan scanf digunakan untuk menyimpan angka yang kita input ketika program dieksekusi. Disini terdapat %d yang mengartikan data inputan akan ditampilkan dalam bentuk decimal, dan &x mengartikan data inputan akan disimpan sementara pada variable n.

a :
Pernyataan di atas digunakan sebagai identitas blok pernyataan yang nantinya akan dipanggil oleh program ketika program dieksekusi. 

switch(ch){
Pernyataan di atas digunakan sebagai kondisi percabangan dalam program ini, dimana pilihannya terdapat pada case-case yang dideklarasikan setelah pernyataan ini.

case 1:bfs(s,n);
Pernyataan di atas digunakan sebagai pilihan pertama dari percabangan dalam program ini, dimana program akan mengeksekusi blok procedure bfs.

case 2:dfs(s,n);
Pernyataan di atas digunakan sebagai pilihan kedua dari percabangan dalam program ini, dimana program akan mengeksekusi blok procedure dfs.

goto a;
Pernyataan di atas digunakan untuk mengarahkan program agar melanjutkan eksekusi ke blok program a:

case 3: break; }
Pernyataan di atas digunakan sebagai pilihan ketiga jika angka yang kita masukkan bukan 1 atau 2, maka program akan berhenti mengeksekusi (break).

return(0); }
Pernyataan di atas digunakan untuk mengambil data masukkan untuk melanjutkan eksekusi ke baris program berikutnya.

for(i=1;i<=n;i++) {
Pernyataan for di atas digunakan sebagai kondisi perulangan dengan ketentuan program akan mengeksekusi dimulai dari bilangan 1, program akan berhenti mengeksekusi jika variable i telah lebih besar daripada variable n, dan variable i akan bertambah satu setiap terjadi perulangan.

if(p!=0)
Pernyataan if di atas digunakan sebagai kondisi percabangan jika hasil bagi variable p tidak sama dengan 0.

getch();
berguna unutk membaca sebuah karakter, bisa juga membaca tombol, getch() tidak akan menampilkan karakter dari tombol yang ditekan. Sebuah getch() bisa pula digunakan untuk menunggu sembarang tombol ditekan. Pada keadaan seperti ini, hasil dari fungsi ini tidak perlu diletakkan ke variable, atau dipascal dapat diartikan sebagai readln