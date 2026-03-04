# Flutter UI Components Demo

Repository ini berisi contoh implementasi beberapa komponen antarmuka (UI) dasar pada Flutter, yaitu:

* Dropdown
* PageView
* Gradient

Project ini dibuat untuk mempelajari penggunaan beberapa widget Flutter yang sering digunakan dalam pengembangan aplikasi mobile.

---

# Daftar Isi

* [Tentang Project](#tentang-project)
* [Teknologi yang Digunakan](#teknologi-yang-digunakan)
* [Struktur Project](#struktur-project)
* [Penjelasan Komponen](#penjelasan-komponen)

  * [Dropdown](#1-dropdown)
  * [PageView](#2-pageview)
  * [Gradient](#3-gradient)
* [Cara Menjalankan Project](#cara-menjalankan-project)
* [Kesimpulan](#kesimpulan)
* [Author](#author)

---

# Tentang Project

Project ini merupakan contoh sederhana penggunaan beberapa widget UI pada Flutter yang sering digunakan dalam pembuatan aplikasi mobile.

Fitur yang ditampilkan dalam project ini meliputi:

* Pemilihan data menggunakan **Dropdown**
* Navigasi antar halaman menggunakan **PageView**
* Desain tampilan menggunakan **Gradient Background**

Dengan mempelajari implementasi widget tersebut, developer dapat memahami bagaimana Flutter membangun antarmuka yang interaktif dan menarik.

---

# Teknologi yang Digunakan

Project ini menggunakan beberapa teknologi berikut:

* **Flutter**
* **Dart**
* **Material Design Widgets**

Flutter merupakan framework open-source dari Google yang memungkinkan developer membuat aplikasi mobile secara cepat dengan performa tinggi.

---

# Struktur Project

Struktur folder pada project ini secara umum adalah sebagai berikut:

```
lib
│
├── main.dart
├── homepage.dart
│
├── pages
│   ├── page1.dart
│   ├── page2.dart
│   └── page3.dart
│
├── dropdown_example.dart
└── gradient_example.dart
```

Penjelasan struktur:

| File / Folder         | Deskripsi                                                   |
| --------------------- | ----------------------------------------------------------- |
| main.dart             | File utama untuk menjalankan aplikasi Flutter               |
| homepage.dart         | Halaman utama yang berisi PageView                          |
| pages/                | Folder berisi halaman-halaman yang digunakan dalam PageView |
| dropdown_example.dart | Contoh implementasi widget Dropdown                         |
| gradient_example.dart | Contoh penggunaan Gradient                                  |

---

# Penjelasan Komponen

# 1. Dropdown

## Pengertian

Dropdown adalah komponen UI yang memungkinkan pengguna memilih satu nilai dari beberapa pilihan yang tersedia.

Dropdown sering digunakan ketika terdapat banyak pilihan namun ingin menghemat ruang tampilan pada layar.

Flutter menyediakan widget:

```
DropdownButton
```

untuk membuat komponen dropdown.

---

## Contoh Data Dropdown

```dart
final List<String> data = [
  "Aqshal",
  "Nur",
  "Ikhsan",
];
```

---

## Implementasi Dropdown

```dart
DropdownButton(
  onChanged: (value) {
    print(value);
  },
  items: data
      .map(
        (e) => DropdownMenuItem(
          value: e,
          child: Text(e),
        ),
      )
      .toList(),
)
```

Penjelasan:

* `items` berisi daftar pilihan yang ditampilkan
* `onChanged` akan dipanggil ketika pengguna memilih item
* `DropdownMenuItem` digunakan untuk membuat item dropdown

---

## Dropdown dengan StatefulWidget

Untuk menyimpan nilai yang dipilih oleh pengguna, dropdown dapat dibuat menggunakan **StatefulWidget**.

```dart
var selected;

DropdownButton(
  value: selected,
  hint: Text("pilih nama..."),
  onChanged: (value) {
    setState(() {
      selected = value;
    });
  },
)
```

Penjelasan:

| Properti   | Fungsi                                    |
| ---------- | ----------------------------------------- |
| value      | nilai yang dipilih                        |
| hint       | teks yang muncul sebelum pilihan dipilih  |
| setState() | memperbarui tampilan ketika nilai berubah |

Dengan menggunakan StatefulWidget, dropdown dapat menyimpan dan menampilkan pilihan pengguna.

---

# 2. PageView

## Pengertian

PageView adalah widget Flutter yang digunakan untuk membuat navigasi antar halaman menggunakan gesture swipe.

PageView biasanya digunakan untuk:

* onboarding screen
* slide konten
* navigasi berbasis gesture

Flutter menyediakan dua komponen utama:

```
PageView
```

dan

```
PageController
```

---

## Contoh Halaman

Berikut contoh implementasi halaman:

```dart
class Page1 extends StatelessWidget {

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.black,
    );
  }
}
```

Setiap halaman memiliki warna latar belakang berbeda untuk membedakan tampilan halaman.

---

## Implementasi PageView

```dart
final _controller = PageController();

PageView(
  controller: _controller,
  scrollDirection: Axis.vertical,
  children: [
    Page1(),
    Page2(),
    Page3(),
  ],
)
```

Penjelasan:

| Properti        | Fungsi                          |
| --------------- | ------------------------------- |
| controller      | mengontrol perpindahan halaman  |
| scrollDirection | menentukan arah swipe           |
| children        | daftar halaman yang ditampilkan |

Jika `scrollDirection` diubah menjadi:

```
Axis.horizontal
```

maka halaman akan berpindah dengan swipe kiri dan kanan.

---

# 3. Gradient

## Pengertian

Gradient adalah teknik desain UI yang menggabungkan dua atau lebih warna sehingga menghasilkan efek transisi warna secara bertahap.

Flutter menyediakan beberapa jenis gradient:

* LinearGradient
* RadialGradient
* SweepGradient

Gradient sering digunakan untuk membuat tampilan aplikasi menjadi lebih menarik secara visual.

---

## Implementasi Gradient

Gradient biasanya digunakan pada widget `Container` dengan `BoxDecoration`.

```dart
Container(
  decoration: BoxDecoration(
    gradient: SweepGradient(
      colors: [
        Color.fromARGB(255, 61, 212, 23),
        Color.fromARGB(255, 53, 138, 14),
        Color.fromARGB(255, 87, 18, 18),
      ],
    ),
  ),
)
```

Penjelasan:

| Properti      | Fungsi                                      |
| ------------- | ------------------------------------------- |
| SweepGradient | membuat gradient berputar dari titik tengah |
| colors        | menentukan kombinasi warna                  |
| BoxDecoration | mengatur dekorasi tampilan container        |

Gradient membantu membuat tampilan aplikasi menjadi lebih modern dan menarik.

---

# Cara Menjalankan Project

Ikuti langkah berikut untuk menjalankan project Flutter ini.

## 1. Clone repository

```
git clone https://github.com/username/nama-repository.git
```

## 2. Masuk ke folder project

```
cd nama-repository
```

## 3. Install dependencies

```
flutter pub get
```

## 4. Jalankan aplikasi

```
flutter run
```

Pastikan Flutter SDK sudah terinstall di komputer.

---

# Kesimpulan

Flutter menyediakan banyak widget yang memudahkan developer dalam membangun aplikasi mobile.

Pada project ini dipelajari tiga komponen utama:

**Dropdown**

Digunakan untuk memilih satu opsi dari beberapa pilihan.

**PageView**

Digunakan untuk membuat navigasi antar halaman menggunakan gesture swipe.

**Gradient**

Digunakan untuk membuat tampilan warna yang lebih menarik pada aplikasi.

Dengan memahami komponen-komponen ini, developer dapat membuat aplikasi Flutter yang lebih interaktif, responsif, dan memiliki desain UI modern.

---
