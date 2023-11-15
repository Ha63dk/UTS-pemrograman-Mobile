# Tugas Pemrograman Mobile

Nama: Hadad Firdaus  
NIM: 312310739  
Kelas: TI.22.B1  
Mata Kuliah: Pemrograman Mobile

### Deskripsi Tugas
Tugas ini bertujuan untuk membuat tombol yang setiap kali diklik, angkanya akan bertambah sesuai dengan urutan angka Fibonacci. Selain itu, aplikasi ini dilengkapi dengan fitur toast untuk memberikan informasi kepada pengguna.

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:id="@+id/numberLayout"
        android:layout_width="match_parent"
        android:layout_height="76dp"
        android:orientation="horizontal">

        <EditText
            android:id="@+id/maxNumber"
            android:layout_width="94dp"
            android:layout_height="55dp"
            android:layout_marginLeft="10dp"
            android:layout_marginTop="5dp"
            android:layout_marginRight="5dp"
            android:layout_marginBottom="5dp"
            android:ems="10"
            android:freezesText="false"
            android:inputType="numberDecimal"
            android:text="0" />

        <Button
            android:id="@+id/buttonMax"
            android:layout_width="143dp"
            android:layout_height="wrap_content"
            android:text="Set Maximum" />
    </LinearLayout>

    <LinearLayout
        android:id="@+id/linear"
        android:layout_width="match_parent"
        android:layout_height="414dp"
        android:layout_below="@id/numberLayout"
        android:background="#FFD700"
        android:clipToPadding="false"
        android:gravity="center"
        android:orientation="vertical">

        <TextView
            android:id="@+id/textNama"
            android:layout_width="wrap_content"
            android:layout_height="42dp"
            android:layout_gravity="clip_horizontal|center"
            android:layout_marginTop="40dp"
            android:layout_marginBottom="30dp"
            android:text="Hadad Firdaus 312310739"
            android:textAlignment="center"
            android:textSize="24sp" />

        <!-- Sisipkan elemen-elemen XML lainnya disini -->

    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="165dp"
        android:layout_below="@id/linear"
        android:orientation="vertical">

        <!-- Sisipkan elemen-elemen XML lainnya disini -->

    </LinearLayout>

</RelativeLayout>

Penjelasan:

Kita isi relative layout dengan 3 linear layout

1. Linear layout 1 berisi editText dan button set maximum
2. Linear layout 2 diisi dengan 3 textview dan 1 linear layout horizontal:
   - Nama + NIM
   - Jumlah klik pada tombol hitung
   - Angka fibonacci terakhir
   - Linear layout: TextView untuk menampilkan jumlah maksimal angka fibonacci

3. Linear layout 3 berisi:
   - Linear layout 1: button hitung + button reset
   - Linear layout 2: button toast
