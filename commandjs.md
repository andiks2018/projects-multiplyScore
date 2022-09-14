import './style.css';
console.info('tes connected..');
//kita akan buat perhitungan perkalian yang menangkap 2 num

const num1 = Math.ceil(Math.random() * 10);
const num2 = Math.ceil(Math.random() * 10);
const questionEl = document.getElementById('question');

//11 kita declare nilai score 0
//17 kita ganti nilai nol menjadi local storage agar update nilai scorenya, sampai disini kita sudah mendapatkan nnilai score yang terus update kalau jawabannya sudah bener atau salah

//let score = 0;
let score = JSON.parse(localStorage.getItem("score"));

//18 jadi kita tetapkan unutk penjumlahan angka, jika tidak mulai maka angka dasar itu 0 menggunakan if
if (!score){
  score=0;
}

// 20 kita tampilkan ke html dan selesai 
scoreEl.innerText = `score : ${score}`
questionEl.innerText = `Berapakah hasil perkalian ${num1} dengan ${num2}?`;

//berasil menuliskan soalnya ? selanjutnya kita akan menyelesaikan inputan dan form
//=============================================

// 5 tangkap elemen input
const inputEl = document.getElementById('input');

// 3 kita buat variable form
const formEl = document.getElementById('form');

//19 kita mulai buat score element untuk kita terapkan nilainya kedalam html 
const scoreEl = document.getElementById('score');

// 1 selanjutnya kita butuh jawaban yang benar
const correctAns = num1 * num2;

// 2 jawabnnya itu dari form

// 4 selanjutnya kita akan buat function addeventlistener yang akan menghandle submit diaman setiap kali user meneken submit maka kit akan menjalankan function callback, dan mendapatkan informasi yang disampaikan
formEl.addEventListener('submit', () => {

  //6 tangkap jawaban user disini inputEl //9 tambahkan + dedepan inputEl
  const userAns = +inputEl.value; // 7 inputan user akan berupa string

  // 8 kita buktikan dengan console log typedatanya string, tinggal tambahkamn + di depan inputan sehingga merubah menjadi integer/number
  console.log(userAns, typeof userAns);

  // 10 selanjutnya kita akan mengcompare jawabn user dengan jawaban yang bener. kita gunakan function if dan else, kita bener maka dia bertambah satu, kalau dia salah maka dia akan berkurang.
  if (userAns === correctAns) {
    score++;

    // 11 kita akan lihat hasilnya di console log

    // 15 kita ganti console score dengan localstorage
    mylocalStorage();
  } else {
    score--;
    mylocalStorage(); // 12 sama ya kita lihat hasilnya juga kalau salah apah minus hasilnya

    // 16 disini juga kita letakkan local storage
  }
});

//13 kita akan menambahkan localstorage agar nilai kita selalu bertambah, sehinngga nilai score tidak mulai dari 0 lagi , balik 0 lagi. jadi bisa bertambah terus
function mylocalStorage() {
  localStorage.setItem('score', JSON.stringify(score)); // 14 kita harus convert ke string kembali dengan menambahkan stringfy JSON dengan variable score //15 cara melihat bertambah dan berkuran g1 dilocalstorage coba buka console kemudian application /localstorage disana.
}
