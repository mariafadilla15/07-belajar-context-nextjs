# **Laporan Praktikum - #07 Context**

|  | Pemrograman Berbasis Framework 2024 |
|--|--|
| NIM |  2141720063|
| Nama |  Maria Fadilla |
| Kelas | TI - 3A |

<br>

## **Praktikum 1: Membuat Variasi Ukuran Teks Heading dengan Context**
---

### **Membuat stuktur folder dengan prinsip [atomic design](https://bradfrost.com/blog/post/atomic-web-design)**

Membuat folder baru di src/components seperti berikut ini:

![Screenshot](assets-report/00.png)

### **Membuat Komponen Atom Baru** 

Membuat file baru di `src/components/atoms/heading.tsx` berisi kode sebagai berikut:

```bash
export default function Heading({ level, children }: { level: number; children: any }) {
    switch (level) {
        case 1:
            return <h1>{children}</h1>;
        case 2:
            return <h2>{children}</h2>;
        case 3:
            return <h3>{children}</h3>;
        case 4:
            return <h4>{children}</h4>;
        case 5:
            return <h5>{children}</h5>;
        case 6:
            return <h6>{children}</h6>;
        default:
            throw Error('Unknown level: ' + level);
    }
}
```

Kemudian membuat file baru di `src\components\atoms\section.tsx` berisi kode berikut:

```bash
export default function Section({ children }: { children: any }) {
    return (
        <section className="section">
            {children}
        </section>
    );
}
```

Lalu pada bagian `MainPage` buat file baru di `src\components\templates\main_page.tsx` berisi kode sebagai berikut:

```bash
import Heading from "../atoms/heading";
import Section from "../atoms/section";

export default function MainPage() {
    return (
        <Section>
            <Heading level={1}>Title</Heading>
            <Section>
                <Heading level={2}>Heading</Heading>
                <Heading level={2}>Heading</Heading>
                <Heading level={2}>Heading</Heading>
                <Section>
                    <Heading level={3}>Sub-heading</Heading>
                    <Heading level={3}>Sub-heading</Heading>
                    <Heading level={3}>Sub-heading</Heading>
                    <Section>
                        <Heading level={4}>Sub-sub-heading</Heading>
                        <Heading level={4}>Sub-sub-heading</Heading>
                        <Heading level={4}>Sub-sub-heading</Heading>
                    </Section>
                </Section>
            </Section>
        </Section>
    );
}
```

Perhatikan komponen Heading tersebut yang menerima level untuk ukurannya.

### **Mengubah isi kode `page.tsx` dan run**

Mengubah kode di `src\app\page.tsx` seperti berikut:

```bash
import MainPage from "@/components/templates/main_page";

export default function Home() {
  return <MainPage />;
}
```

Lalu run dan lihat hasilnya di browser.

![Screenshot](assets-report/01.png)

### **Jawaban Soal 1**

Jelaskan apa yang telah Anda pelajari dan bagaimana tampilannya saat ini?

- Dalam praktikum ini, saya belajar tentang penggunaan context dalam React untuk menyediakan data ke komponen-komponen child. Saya juga mempraktikkan pembuatan struktur folder berdasarkan prinsip atomic design dan pembuatan komponen atom dengan variasi ukuran teks heading.

- Pada hasil running di atas, dapat dilihat bahwa tampilan saat ini menunjukkan hierarki heading yang berbeda-beda ukurannya, mulai dari level 1 hingga level 4, sesuai dengan data level yang diberikan ke komponen Heading.
