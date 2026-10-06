| Nama Elemen Data | Tipe Data | Panjang | Keterangan / Batasan | Penanggung Jawab |
|---|---|---|---|---|
| `id_anggota` | Varchar | 10 | Primary Key, Format: KOPMA-XXXX | Divisi HRD / Keanggotaan |
| `npm` | Varchar | 8 | Unique, Nomor Pokok Mahasiswa (misal: 25430093) | Divisi HRD / Keanggotaan |
| `nama_lengkap` | Varchar | 100 | Nama sesuai KMS/KTM | Divisi HRD / Keanggotaan |
| `kode_barang` | Varchar | 13 | Primary Key / Barcode standard | Divisi Usaha & Ritel |
| `harga_jual` | Decimal | 12,2 | Min: 0 | Divisi Usaha & Ritel |
| `stok` | Integer | 6 | Min: 0 | Divisi Gudang |
| `no_faktur_jual` | Varchar | 20 | Primary Key, Format: TRX-YYYYMMDD-XXX | Divisi Usaha & Ritel |
| `jumlah_simpanan` | Decimal | 12,2 | Nilai transaksi simpanan | Bendahara |