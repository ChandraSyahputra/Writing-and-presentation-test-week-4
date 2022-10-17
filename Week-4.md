# Writing Test Week-4

## JavaScript Intermediate - Asynchronous - Fetch
- Dalam JavaScript kita bisa mengirimkan **network request** dan juga bisa mengambil informasi data terbaru dari server jika dibutuhkan.
- Contoh **network request** yang biasa kita lakukan:
    - Mengirimkan data dari sebuah form.
    - Mengambil data untuk ditampilkan dalam list/table.
    - Mendapatkan notifikasi.
- Dalam melakukan **network request**, JavaScript memiliki metode bernama *fetch()*.
- *fetch()* adalah salah satu proses asynchronous di JavaScript sehingga kita perlu menggunakan salah satu diantara *promise* atau *async/await*.

**Fetch dengan Promise**
- Berikut ini contoh request data dengan fetch() menggunakan promise:

```JS
fetch("https://jsonplaceholder.typicode.com/posts")
  .then(function (response) {
    return response.json();
  })
  .then(function (post) {
    console.log(post);
  });
```

**Fetch dengan async/await**
- Berikut contoh request data dengan fetch() menggunakan async/await:

```JS
const tesFetchAsync = async () => {
  let response = await fetch("https://jsonplaceholder.typicode.com/posts");
  response = await response.json();
  console.log(response);
};
tesFetchAsync();
```

- Kita masih mengambil data dari sumber end-point yang sama dengan fetch() sebelumnya yang menggunakan promise sehingga hasilnya pun masih sama persis seperti sebelumnya.

- Ketika menggunakan async/await, kode kita terlihat lebih clean dan mudah dibaca.

## JavaScript Intermediate - Asynchronous - Async Await
- Kita bisa menggunakan **async/await** untuk menggunakan asynchronous pada JavaScript. **Async/await** baru ada ketika update JavaScript ES8 dan dibangun menggunakan promise. Jadi sebenarnya **async/await** dan promise itu sama saja, namun hanya berbeda dari syntax dan cara penggunaannya.

- Ada 2 kata kunci yang memiliki pengertian sebagai berikut:
    - **Async**, mengubah function synchronous menjadi asynchronous.
    - **Await**, menunda eksekusi hingga proses asynchronous selesai.

- Sebuah **async** function bisa tidak berisi await sama sekali atau lebih dari satu await. Keyword await hanya bisa digunakan didalam **async** function, jika digunakan di luar **async** function maka akan terjadi error.

**Async**
- Berikut ini contoh penggunaan dari **async** :

```JS
// async menggunakan keyword function 
async function tesAsyncAwait() {
  return "Fulfilled";
}

console.log(tesAsyncAwait());

// async menggunakan arrow function
const tesAsyncAwait = async () => {
  return "Fulfilled";
};

console.log(tesAsyncAwait());
```

**Await**
- **Await** hanya bisa digunakan dalam async function dan **await** adalah keyword dalam **async** yang digunakan untuk menunda hingga proses asynchronous selesai.

- Berikut ini contoh penggunaan dari **async/await** :

```JS
async function tesAsyncAwait() {
   await 'Fulfilled';
}
```

Kita juga bisa memberikan error handling pada async/await. Contoh lengkap penggunaan async/await:

```JS
// Definisikan dahulu promise yang ingin digunakan
let condition = true;
let tesAsyncAwait = async (condition) => {
  if (condition) {
    return "Condition is fulfilled!";
  } else {
    throw "Condition is rejected!";
  }
};

// Membuat fungsi run menjadi asynchronous menggunakan async/await
const run = async (condition) => {
  try {
    const message = await tesAsyncAwait(condition);
    console.log(message);  // Output: Condition is fulfilled!
    console.log("After condition is fulfilled"); // Output: After condition is fulfilled
  } catch (error) {
    console.log(error);
  }
};

run(true);
```
Dari kode di atas, kita dapat melihat bahwa run adalah sebuah fungsi async dan await dipanggil bersamaan dengan fungsi tesAsyncAwait(condition). await pada fungsi ini artinya, console.log pada message dan After condition is fulfilled tidak akan dijalankan (ditunda) hingga proses tesAsyncAwait(condition) selesai dijalankan.

## Git & GitHub Lanjutan
**Membuat Organizations untuk kolaborasi**
- Kita dapat berkolaborasi dalam satu project dengan menggunakan GitHub.
Caranya:
1. Masuk ke akun github anda.
2. Klik `setting` -> `organization` -> `new organizations`
3. Pick a plant yang diinginkan atau free.
4. Set up your organization.

## Responsive Web Design
- Responsive Web Design adalah bertujuan membuat desain website kita dapat diakses dalam device apapun.

**Setting Chrome Dev Tools**
- Developer website wajib menggunakan tools bawaan dari setiap browser. Ini akan memudahkan proses development website.
- Pada browser chrome biasa disebut Chrome Dev Tools.
- Kita dapat mengaksesnya menggunakan `ctrl` + `shift` + `J`
- Kita dapat mengakses tools responsive web menggunakan `ctrl` + `shift` + `M`

**Menambahkan Viewport di HTML**
- Untuk menambahkan viewport kita dapat memasukkan kode di bawah ke dalam head.
```HTML
<meta name="viewport" content="width=device-width, initial-scale=l.0" />
```
- Menjadi seperti ini
```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initiat-scate=l.O" />
    <title>Responsive Web Design</title>
  </head>
  <body></body>
</html>
```

**Menggunakan max-width element**
- Ketika tidak menggunakan max-width, element image akan menggunakan overflow ketika ditampilkan pada halaman yang lebih kecil dari image.

```HTML
<img style="max-width: 100%;" src=”images/nature.jpg" att="image"/>
```
Dengan demikian gambar akan menyesuaikan ukuran layar device.

**Media Query**
- Media query untuk responsive web design umumnya menggunakan 2 jenis media query yaitu `min-width` dan `max-width`
- Media query ini digunakan untuk membuat beberapa styles yang tergantung pada jenis device.

**Setting Media Query**
```CSS
@media screen and (min-width: your pixel) {
  /* your tag element html and your css */
}
@media screen and (max-width: your pixel) {
  /* your tag element html and your css */
}
```

**Terdapat 2 cara dalam menggunakan media query**
- Membuat file css yang berbeda untuk masing-masing device.
```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Responsive Web Design</title>
    <!-- main.css untuk device laptop -->
    <link rel="stylesheet" href="styles/main.css" />
    <!-- main.mobile.css untuk device mobile -->
    <link
      rel="stylesheet"
      media="screen and (max-width: SOOpx)"
      href="styles/main.mobile.css"
    />
  </head>
  <body>
    <h2>Responsive Web Design (RWD)</h2>
  </body>
</html>
```
```CSS
/* file main.css */
body {
  background-color: black;
}
/* file main.mobile.css */
body {
  background-color: red;
}
```
-

## Bootstrap 5