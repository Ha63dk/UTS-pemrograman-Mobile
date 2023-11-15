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

- Color.xml

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

1. <?xml version="1.0" encoding="utf-8"?>: Menunjukkan bahwa ini adalah dokumen XML versi 1.0 dengan pengkodean UTF-8.
2. <resources>: Menandakan awal dari sumber daya yang didefinisikan di dalam file XML.
3. <integer-array>: Mendefinisikan array integer yang berisi referensi ke warna-warna tertentu. Dalam hal ini, warna merah, kuning, dan hijau diambil dari 
    warna yang sudah didefinisikan sebelumnya.
   
- Main Activity Java
'''
import android.graphics.Color;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.text.Layout;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.LinearLayout;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    public int count = 0 ;
    public int countFibo = 0 ;
    public int maxFibo = 0;
    public TextView showCount;
    public TextView showCountFibo;
    public TextView showMaxFibo;
    public EditText maxNumber;
    public Button buttonToast;
    public Button buttonCount;
    public Button buttonMax;
    public Button buttonReset;
    public Toast toastA;
    public int[] warna;
    public LinearLayout linear;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        buttonToast=(Button)findViewById(R.id.buttonToast);
        buttonCount=(Button)findViewById(R.id.buttonCount);
        buttonReset=(Button)findViewById(R.id.buttonReset);
        buttonMax=(Button)findViewById(R.id.buttonMax);
        showCount=(TextView)findViewById(R.id.textCount);
        showCountFibo=(TextView)findViewById(R.id.textCountFibo);
        showMaxFibo=(TextView)findViewById(R.id.textMaxFibo);
        maxNumber=(EditText)findViewById(R.id.maxNumber);
        warna = getResources().getIntArray(R.array.warna_background_fibo);
        linear =(LinearLayout) findViewById(R.id.linear);

        buttonToast.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if(toastA != null) { toastA.cancel(); }
                    toastA = Toast.makeText(getApplicationContext(), "Angka Fibonacci : " + countFibo, Toast.LENGTH_SHORT);
                    toastA.show();
            }
        });

        buttonCount.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) { calculate(view); }
        });

        buttonReset.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) { reset(view); }
        });

        buttonMax.setOnClickListener(new View.OnClickListener(){
            @Override
            public void onClick(View view){
                String getNumber = maxNumber.getText().toString();
                maxFibo = Integer.parseInt(getNumber);
                showMaxFibo.setText(getNumber);
                if(toastA != null) { toastA.cancel(); }
                toastA = Toast.makeText(getApplicationContext(), "Angka Maksimum fibonacci diubah menjadi " + getNumber, Toast.LENGTH_SHORT);
                toastA.show();
            };
        });

    }
    protected void calculate(View view){
        if(calculateFibo(count + 1) >= maxFibo){
            if(toastA != null) toastA.cancel();
            toastA = Toast.makeText(getApplicationContext(),"Sudah Mencapai Maksimum !!", Toast.LENGTH_SHORT);
            toastA.show();
        }else{
            count++;
            linear.setBackgroundColor(warna[count % 3]);
            countFibo = calculateFibo(count);
            showCount.setText("Tombol Hitung diklik sebanyak : " + Integer.toString(count));
            showCountFibo.setText(Integer.toString(countFibo));
            if(count % 5 == 0){
                if(toastA != null) toastA.cancel();
                toastA = Toast.makeText(getApplicationContext(),"Tombol hitung diklik : "+ count + " Kali", Toast.LENGTH_SHORT);
                toastA.show();
            }
        }
    }

    protected int calculateFibo(int n){
        if(n <= 1) {
            linear.setBackgroundColor(warna[2]);
            return n;
        }
        int prev,current,next;
        prev = 0;
        current = 1;
        for (int i = 2; i <= n; i++) {
            next = prev + current;
            prev = current;
            current = next;
        }
        return current;
    }

    protected void reset(View view){
        count = 0;
        countFibo = 0;
        showCount.setText("Tombol Hitung diklik sebanyak : " + Integer.toString(count));
        showCountFibo.setText(Integer.toString(countFibo));
        linear.setBackgroundColor(Color.WHITE);
    }
}
Kode yang diberikan adalah implementasi sederhana dari aplikasi Android yang memiliki fungsi untuk menghitung angka Fibonacci setiap kali tombol hitung diklik. Berikut adalah penjelasan singkat untuk setiap bagian dari kode tersebut:

1. **Deklarasi Variabel:**
   - `count`, `countFibo`, `maxFibo`: Variabel untuk menghitung jumlah klik tombol, nilai Fibonacci, dan nilai maksimum Fibonacci.
   - `showCount`, `showCountFibo`, `showMaxFibo`: TextView untuk menampilkan jumlah klik tombol, nilai Fibonacci, dan nilai maksimum Fibonacci.
   - `maxNumber`: EditText untuk memasukkan nilai maksimum Fibonacci.
   - `buttonToast`, `buttonCount`, `buttonReset`, `buttonMax`: Button untuk melakukan aksi toast, menghitung Fibonacci, mereset, dan mengatur nilai maksimum Fibonacci.
   - `toastA`: Objek Toast untuk menampilkan informasi.

2. **Inisialisasi Warna:**
   - `warna`: Array integer yang berisi referensi ke warna latar belakang sesuai dengan array yang didefinisikan di `colors.xml`.

3. **Event Listener dan Aksi:**
   - `buttonToast`: Menampilkan angka Fibonacci saat tombol toast diklik.
   - `buttonCount`: Menghitung dan menampilkan angka Fibonacci setiap kali tombol hitung diklik.
   - `buttonReset`: Mereset jumlah klik tombol dan nilai Fibonacci.
   - `buttonMax`: Mengubah nilai maksimum Fibonacci berdasarkan input dari pengguna.

4. **Metode `calculateFibo`:**
   - Menghitung nilai Fibonacci untuk suatu angka tertentu.
   - Mengubah warna latar belakang sesuai dengan pola warna yang telah didefinisikan.

5. **Metode `calculate`:**
   - Memeriksa apakah nilai maksimum Fibonacci telah tercapai.
   - Jika belum, menghitung nilai Fibonacci, menampilkan informasi, dan mengubah warna latar belakang.

6. **Metode `reset`:**
   - Mengatur ulang jumlah klik tombol, nilai Fibonacci, dan mengubah warna latar belakang menjadi putih.

Dengan demikian, aplikasi ini memberikan interaktifitas sederhana dengan menggabungkan konsep angka Fibonacci dan tampilan warna yang menarik pada antarmuka pengguna.
