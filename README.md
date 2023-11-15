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
            android:text="HADAD FIRDAUS 312310739"
            android:textAlignment="center"
            android:textSize="24sp" />


    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="165dp"
        android:layout_below="@id/linear"
        android:orientation="vertical">

        

    </LinearLayout>

</RelativeLayout>
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="purple_200">#FFBB86FC</color>
    <color name="purple_500">#FF6200EE</color>
    <color name="purple_700">#FF3700B3</color>
    <color name="teal_200">#FF03DAC5</color>
    <color name="teal_700">#FF018786</color>
    <color name="yellow">#F2EF1C</color>
    <color name="green">#1CF234</color>
    <color name="red">#F50A0A</color>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <integer-array name="warna_background_fibo">
        <item>@color/red</item>
        <item>@color/yellow</item>
        <item>@color/green</item>
    </integer-array>
</resources>

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

- Nama + NIM



Penjelasan:


1. <?xml version="1.0" encoding="utf-8"?>: Menunjukkan bahwa ini adalah dokumen XML versi 1.0 dengan pengkodean UTF-8.
2. <resources>: Menandakan awal dari sumber daya yang didefinisikan di dalam file XML.
3. <integer-array>: Mendefinisikan array integer yang berisi referensi ke warna-warna tertentu. Dalam hal ini, warna merah, kuning, dan hijau diambil dari warna yang sudah didefinisikan sebelumnya.
