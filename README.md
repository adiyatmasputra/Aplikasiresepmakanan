# Aplikasiresepmakanan
 Adiyatma saputra - 2210010115 - UTS


### **README.md**

```markdown
# Aplikasi Resep Masakan

Aplikasi Resep Masakan adalah aplikasi berbasis GUI yang dibuat menggunakan Java dan NetBeans. Aplikasi ini dirancang untuk membantu pengguna menyimpan, mengelola, dan menyimpan resep masakan ke file teks. Aplikasi ini memanfaatkan konsep Pemrograman Berorientasi Objek (OOP) dan berbagai komponen GUI.

## Fitur Utama
1. **Menambah Resep**: Pengguna dapat menambahkan nama resep, bahan, dan langkah-langkah memasak.
2. **Mengubah Resep**: Resep yang sudah ada dapat diedit dengan mudah.
3. **Menghapus Resep**: Pengguna dapat menghapus resep yang tidak diperlukan.
4. **Menyimpan ke File**: Semua resep dapat disimpan ke file teks menggunakan fitur save.

## Teknologi yang Digunakan
- **Bahasa Pemrograman**: Java
- **IDE**: NetBeans
- **Komponen GUI**: JFrame, JList, JTextArea, JTextField, JButton

## Cara Menjalankan Aplikasi
1. Clone repository ini ke komputer Anda:
   ```bash
   git clone <repository_url>
   ```
2. Buka proyek di NetBeans IDE.
3. Klik kanan pada file `MainFrame.java` → **Run File** untuk menjalankan aplikasi.

## Struktur Kode
- **MainFrame.java**: 
  File utama yang berisi antarmuka pengguna (GUI) dan logika aplikasi.
- **Komponen GUI**:
  - `txtNamaResep`: Field untuk memasukkan nama resep.
  - `txtLangkah`: Area teks untuk memasukkan bahan dan langkah memasak.
  - `listResep`: Daftar resep yang ditampilkan.
  - `btnTambah`: Tombol untuk menambah resep.
  - `btnHapus`: Tombol untuk menghapus resep.
  - `btnUbah`: Tombol untuk mengedit resep.
  - `btnSave`: Tombol untuk menyimpan resep ke file teks.

## Penjelasan Koding
### 1. **Menambah Resep**
Kode berikut mengambil data dari `txtNamaResep` dan `txtLangkah`, lalu menambahkannya ke `DefaultListModel` yang ditampilkan di `listResep`.
```java
private void btnTambahActionPerformed(java.awt.event.ActionEvent evt) {
    String namaResep = txtNamaResep.getText();
    String bahanLangkah = txtLangkah.getText();

    if (!namaResep.isEmpty() && !bahanLangkah.isEmpty()) {
        String resep = namaResep + ":\n" + bahanLangkah;
        resepListModel.addElement(resep);

        txtNamaResep.setText("");
        txtLangkah.setText("");
        JOptionPane.showMessageDialog(this, "Resep berhasil ditambahkan!");
    } else {
        JOptionPane.showMessageDialog(this, "Semua kolom harus diisi!");
    }
}
```

### 2. **Menghapus Resep**
Kode berikut menghapus resep yang dipilih dari `listResep`.
```java
private void btnHapusActionPerformed(java.awt.event.ActionEvent evt) {
    int selectedIndex = listResep.getSelectedIndex();
    if (selectedIndex != -1) {
        resepListModel.remove(selectedIndex);
        JOptionPane.showMessageDialog(this, "Resep berhasil dihapus!");
    } else {
        JOptionPane.showMessageDialog(this, "Pilih resep yang ingin dihapus!");
    }
}
```

### 3. **Mengubah Resep**
Kode ini memungkinkan pengguna untuk mengedit resep yang sudah ada di daftar.
```java
private void btnUbahActionPerformed(java.awt.event.ActionEvent evt) {
    int selectedIndex = listResep.getSelectedIndex();
    if (selectedIndex != -1) {
        String namaResep = txtNamaResep.getText();
        String bahanLangkah = txtLangkah.getText();

        if (!namaResep.isEmpty() && !bahanLangkah.isEmpty()) {
            String resep = namaResep + ":\n" + bahanLangkah;
            resepListModel.set(selectedIndex, resep);
            JOptionPane.showMessageDialog(this, "Resep berhasil diubah!");
        } else {
            JOptionPane.showMessageDialog(this, "Semua kolom harus diisi!");
        }
    } else {
        JOptionPane.showMessageDialog(this, "Pilih resep yang ingin diubah!");
    }
}
```

### 4. **Menyimpan ke File**
Kode berikut memungkinkan pengguna menyimpan semua data dari daftar ke file teks.
```java
private void btnSaveActionPerformed(java.awt.event.ActionEvent evt) {
    try {
        javax.swing.JFileChooser fileChooser = new javax.swing.JFileChooser();
        int option = fileChooser.showSaveDialog(this);

        if (option == javax.swing.JFileChooser.APPROVE_OPTION) {
            java.io.File file = fileChooser.getSelectedFile();
            try (java.io.FileWriter writer = new java.io.FileWriter(file)) {
                for (int i = 0; i < resepListModel.getSize(); i++) {
                    writer.write(resepListModel.get(i) + "\n\n");
                }
                writer.flush();
                JOptionPane.showMessageDialog(this, "Data berhasil disimpan ke file!");
            }
        }
    } catch (Exception e) {
        JOptionPane.showMessageDialog(this, "Terjadi kesalahan: " + e.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
    }
}
```

## Pengembangan Selanjutnya
Berikut beberapa fitur tambahan yang dapat ditambahkan di masa depan:
1. **Load File**: Membaca file teks untuk mengisi daftar resep.
2. **Pencarian Resep**: Menambahkan kolom pencarian untuk mencari resep tertentu.
3. **Ekspor ke Format Lain**: Menyimpan data dalam format seperti `.csv` atau `.json`.

## Kontribusi
Kontribusi sangat diterima. Jika Anda memiliki ide pengembangan aplikasi ini, silakan ajukan *pull request*.

## Lisensi
Proyek ini menggunakan lisensi [MIT](LICENSE).
```

---

### Cara Menggunakan README.md
1. Salin teks di atas ke file baru bernama `README.md`.
2. Letakkan file tersebut di root folder proyek.
3. Tambahkan ke repository GitHub lo, supaya tampil di halaman utama repository.

Kalau lo butuh bantuan untuk fitur lain atau mau ada revisi di README ini, tinggal bilang aja! 😊
