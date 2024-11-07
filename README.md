# Welcome to Mojo Dojo Casa House 🕺🏻💃🏻
<img src="static/image/CasaHouse.png" width="480" height="240">

## Tugas 2
<details>

### Cara _Step by Step_ Mengimplementasikan _Checklist_ 
1. Membuat repositori baru dengan nama ```Mojo Dojo Casa House```.
2. Menghubungkan repositori lokal dengan repositori di GitHub.
3. Melakukan _cloning_ repositori tersebut ke komputer lokal.
4. Membuat _virtual environment_ Python dengan perintah:
    ```bash
    python3 -m venv env
    ```
5. Mengaktifkan _virtual environment_ Python baru dengan perintah:
    ```bash
    source env/bin/activate
    ```
6. Membuat file ```requirements.txt``` dengan menambahkan beberapa _depedencies_.
    ```
    django
    gunicorn
    whitenoise
    psycopg2-binary
    requests
    urllib3
    ```
7. Menginstalasi _dependencies_ dengan pip.
    ```bash
    pip install -r requirements.txt
    ```
8. Membuat proyek Django baru dengan perintah:
    ```bash
    django-admin startproject mojo_dojo_casa_house .
    ```
9. Mengubah ```ALLOWED_HOSTS``` di ```settings.py``` untuk keperluan deployment pada direktori ```mojo_dojo_casa_house```.
    ```bash
    ...
    ALLOWED_HOSTS = ["localhost", "127.0.0.1"]
    ...
    ```
10. Membuat aplikasi baru dengan nama ```main``` dengan perintah:
    ```python
    python manage.py startapp main
    ```
11. Mendaftarkan aplikasi ```main``` ke dalam ```settings.py```
    ```
    INSTALLED_APPS = [
    ...,
    'main'
    ]
    ```
12. Mengisi berkas ```models.py``` pada direktori aplikasi ```main``` dengan kode:
    ```python
    from django.db import models

    class Product(models.Model):
        name = models.CharField(max_length=255)
        price = models.IntegerField()
        description = models.TextField()
        quantity = models.IntegerField()
    ```
13. Melakukan migrasi dengan perintah:
    ```python
    python manage.py makemigrations
    python manage.py migrate
    ```
14. Membuat direktori template dan template ```main.html```. 
    ```html
    <h1>Mojo Dojo Casa House 🕺🏻💃🏻</h1>

    <h3>Welcome to our online shop! </h3>
    <p>Username: {{ name }}</p>
    <p>Class: {{ class }}</p>
    ```
15. Menambahkan fungsi pada berkas ```views.py```:
    ```python
    from django.shortcuts import render

    def show_main(request):
        context = {
            'name' : 'Joanne',
            'class' : 'PBP C'
        }

        return render(request, "main.html", context)
    ```
16. Melakukan _routing_ URL di dalam direktori ```main``` dengan membuat berkas ```urls.py``` yang isinya:
    ```python
    from django.urls import path
    from main.views import show_main

    app_name = 'main'

    urlpatterns = [
        path('', show_main, name='show_main'),
    ]
    ```
17. Melakukan tes aplikasi pada localhost dengan perintah:
    ```python
    python3 manage.py runserver
    ```
18. Membuka ```http://localhost:8000``` untuk melihat aplikasi pada _browser_
19. Melakukan _deploy app_ ke situs Pacil Web Server (PWS)

### Bagan _Request Client_ ke _Web_ Aplikasi berbasis Django
<img src="static/image/BaganDjango.png" width="500" height="375">

_Request_ dari pengguna akan diproses terlebih dahulu sebelum diteruskan ke View yang tepat. View tersebut kemudian akan mengakses atau memodifikasi data di Model dan menggunakan Template untuk menampilkan dan mengirimkan respons kembali ke pengguna.

### Fungsi ```git``` dalam Pengembangan Perangkat Lunak
1. Mencatat semua perubahan kode, memungkinkan _developer_ melihat riwayat modifikasi dan siapa yang melakukan perubahan.
2. Memungkinkan banyak _developer_ bekerja secara bersamaan di cabang berbeda tanpa konflik, dengan kemampuan menggabungkan hasil kerja menggunakan _merge_.
3. Memfasilitasi pengelolaan versi perangkat lunak sehingga pengembang dapat beralih antar versi atau mengembalikan kode ke versi sebelumnya.
4. Menyimpan proyek dalam repositori yang dapat diakses lokal atau melalui server, seperti GitHub, untuk pembaruan atau pengunduhan kode.
5. Mendukung integrasi berkelanjutan dengan memudahkan ```pull```, ```commit```, dan ```push``` perubahan serta pengujian otomatis.

### Alasan Mengapa Framework Django Dijadikan Permulaan Pembelajaran PengembanganPperangkat Lunak
1. Tersedia banyak fitur bawaan sehingga pemula bisa langsung fokus pada pengembangan (seperti autentikasi, routing URL, dan pengelolaan database).
2. Terdapat pola arsitektur _Model View Template_ (MVT) yang memudahkan pemahaman pemisahan logika, tampilan, dan data.
3. Memiliki dokumentasi lengkap yang mudah diikuti oleh pemula.
4. Mendorong _clean code writing_ yang terstruktur, membantu membangun kebiasaan pengembangan yang baik.
5. Memiliki banyak pengguna dan komunitas sehingga dapat mendukung pemula dalam belajar dan menemukan solusi.

### Alasan Model pada Django disebut ORM
Disebut sebagai _Object-Relational Mapping_ (ORM) karena ORM memungkinkan kita untuk menghubungkan objek Python dengan tabel di database. Dengan ORM, kita dapat membuat, membaca, memperbarui, dan menghapus data di database tanpa menulis _query_ SQL secara langsung. 

Misalnya, setiap model di Django mewakili tabel dalam _database_, dan setiap atribut model mewakili kolom dalam tabel tersebut. ORM juga memudahkan pengelolaan relasi antar tabel dan perubahan skema database dengan sistem migrasi otomatis.
</details>

## Tugas 3
<details>

### Alasan Mengapa Kita Perlu Data Delivery dalam Pengimplementasian sebuah _Platform_
1. Menjamin data yang dikirim secara cepat dan akurat.
2. Memastikan data relevan dan tepat waktu untuk analisis dan pengambilan keputusan.
3. Menghubungkan berbagai bagian sistem agar berfungsi secara baik.
4. Melindungi data dengan enkripsi selama pengiriman untuk mencegah akses tidak sah.
5. Mengelola volume data yang meningkat secara dinamis untuk menjaga performa platform.

### Mana yang lebih baik antara XML dan JSON?
Menurut saya, JSON lebih baik dan populer daripada XML untuk kebanyakan penggunaan saat ini. JSON lebih mudah dibaca dan ditulis, memiliki ukuran file yang lebih kecil, dan lebih cepat dalam proses unduhan dan _parsing_. 

Namun, XML masih memiliki beberapa keunggulan, seperti dukungan untuk hal yang lebih kompleks serta kemampuan untuk menyertakan metadata dan atribut tambahan. Meskipun begitu, JSON lebih sering dipilih karena kesederhanaan dan efisiensinya dalam konteks aplikasi web dan mobile saat ini.

### Fungsi Method `is_valid()` pada ```form.py``` Django
Method ini digunakan untuk memeriksa apakah data yang diisi di formulir sudah sesuai dengan aturan dan validasi yang ditetapkan. Dengan memanggil `is_valid()`, kita bisa menghindari kesalahan dan data yang tidak konsisten, serta memberikan umpan balik kepada pengguna jika ada kesalahan dalam input mereka. Hal ini untuk menjaga agar data yang diproses tetap aman dan sesuai dengan ketentuan yang telah ditetapkan.

### Alasan Kita Membutuhkan `csrf_token` pada `forms.py` Django
`csrf_token` diperlukan untuk melindungi aplikasi dari serangan Cross-Site Request Forgery (CSRF). Token ini membantu memastikan bahwa permintaan yang dikirimkan berasal dari pengguna yang sah dan bukan dari sumber eksternal yang berbahaya. Ketika formulir dikirim, Django memverifikasi token untuk mencegah permintaan palsu dan melindungi data pengguna dari manipulasi tidak sah.

Jika `csrf_token` tidak ditambahkan, aplikasi/website akan rentan terhadap serangan CSRF. Penyerang bisa memanfaatkan kerentanan ini dengan membuat formulir berbahaya yang mengirimkan data ke server kita atas nama pengguna yang sah, berpotensi menyebabkan perubahan data atau tindakan merugikan.

### Cara _Step by Step_ Mengimplementasikan _Checklist_ 
1. Membuat ```forms.py``` di direktori ```main``` dengan kode:
    ```python
    from django.forms import ModelForm
    from main.models import Product

    class ProductForm(ModelForm):
        class Meta:
            model = Product
            fields = ["name", "price", "description", "quantity"]
    ```

2. Menambahkan Method ```add_page``` untuk menambah entri database pada file ```views.py``` di direktori main
    ```python
    def add_product(request):
    form = ProductForm(request.POST or None)

    if form.is_valid() and request.method == "POST":
        form.save()
        return redirect('main:show_main')
    
    context = {'form': form}
    return render(request, 'add_product.html', context)
    ```

3. Mengimplementasikan form yang telah dibuat ke dalam laman baru dengan template html yang baru ```add_product.html```.

4. Routing URL ke laman yang bersangkutan di file ```urls.py``` di direktori ```main```.
    ```python
    . . .
    urlpatterns = [
        . . .
        path('add-product', add_product, name='add_product'),
    }
    ```

5. Membuat direktori ```templates``` pada direktori utama sebagai basis direktori lain dan buat sebuah berkas bernama ```base.html```.

6. Menambahkan lokasi folder templates tersebut ke settings.py di direktori ```mojo_dojo_casa_house``` dengan kode:
    ```python
    ...
    TEMPLATES = [
        {
            'BACKEND': 'django.template.backends.django.DjangoTemplates',
            'DIRS': [BASE_DIR / 'templates'], # Tambahkan konten baris ini
            'APP_DIRS': True,
            ...
        }
    ]
    ...
    ```

7. Mengimplementasikan database ke dalam ```main.html``` dan juga menjadi perpanjangan dari ```base.html``` dengan kode:
    ```html
    {% extends 'base.html' %}
    {% block content %}
    <div class="container mt-5">
        <h1 class="text-center header">Mojo Dojo Casa House 🕺🏻💃🏻</h1>
        <h3 class="text-center header">Welcome to our online shop!</h3>

        <div class="user-info mb-4 text-center">
            <p><strong>Username:</strong> {{ name }}</p>
            <p><strong>Class:</strong> {{ class }}</p>
        </div>

        <h2 class="my-4 header">Product List</h2>
        {% if not product_entries %}
            <p class="text-muted text-center">No products available in the store.</p>
        {% else %}
            <div class="table-responsive">
                <table class="table table-striped table-hover">
                    <thead class="thead-dark">
                        <tr>
                            <th>Product Name</th>
                            <th>Price</th>
                            <th>Description</th>
                            <th>Quantity</th>
                        </tr>
                    </thead>
                    <tbody>
                        {% comment %} Display product data below this line {% endcomment %}
                        {% for product_entry in product_entries %}
                        <tr>
                            <td>{{ product_entry.name }}</td>
                            <td>${{ product_entry.price }}</td>
                            <td>{{ product_entry.description }}</td>
                            <td>{{ product_entry.quantity }}</td>
                        </tr>
                        {% endfor %}
                    </tbody>
                </table>
            </div>
        {% endif %}

        <div class="text-center" style="margin-top: 50px;"> <!-- Adjusted inline margin -->
            <a href="{% url 'main:add_product' %}" class="btn btn-primary">Add New Product</a>
        </div>
    </div>
    {% endblock %}
    ```

8. Menambahkan baris UUID keys pada berkas ```models.py``` di subdirektori ```main```.
    ```python
    import uuid
    from django.db import models

    class Product(models.Model):
        id = models.UUIDField(primary_key=True, default=uuid.uuid4, editable=False)  # tambahkan baris ini
        . . .
    ```

9. Membuat fungsi baru untuk mengembalikan data dalam bentuk XML dan JSON baik secara keseluruhan maupun per-ID _database_ pada ```views.py```
    ```python
    def show_xml(request):
        data = Product.objects.all()
        return HttpResponse(serializers.serialize("xml", data), content_type="application/xml")

    def show_json(request):
        data = Product.objects.all()
        return HttpResponse(serializers.serialize("json", data), content_type="application/json")

    def show_xml_by_id(request, id):
        data = Product.objects.filter(pk=id)
        return HttpResponse(serializers.serialize("xml", data), content_type="application/xml")

    def show_json_by_id(request, id):
        data = Product.objects.filter(pk=id)
        return HttpResponse(serializers.serialize("json", data), content_type="application/json")
    ```

10. Merouting kembali URL yang bersangkutan di file ```urls.py```.
    ```python
    . . .
    urlpatterns = [
        . . .
        path('xml/', show_xml, name='show_xml'),
        path('json/', show_json, name='show_json'),
        path('xml/<str:id>/', show_xml_by_id, name='show_xml_by_id'),
        path('json/<str:id>/', show_json_by_id, name='show_json_by_id'),
    ]
    ```

11. Melakukan tes aplikasi pada localhost dengan perintah:
    ```python
    python3 manage.py runserver
    ```
12. Membuka ```http://localhost:8000``` untuk melihat aplikasi pada _browser_
13. Melakukan _deploy app_ ke situs Pacil Web Server (PWS)

### _Screenshot_ Postman
#### 1. HTML Source
![](static/image/HTMLsource.png)

#### 2. JSON
![](static/image/JSON.png)

#### 3. JSON by ID
![](static/image/JSONbyID.png)

#### 4. XML
![](static/image/XML.png)

#### 5. XML by ID
![](static/image/XMLbyID.png)
</details>

## Tugas 4
<details>

### Perbedaan antara `HttpResponseRedirect()` dan `redirect()`
Di Django, keduanya digunakan untuk mengarahkan pengguna ke URL lain, tetapi ada beberapa perbedaan dalam cara penggunaannya:

1. `HttpResponseRedirect()`

- Tipe: Kelas yang menghasilkan objek respons HTTP.
- Fungsi: Membuat respons HTTP yang mengarahkan pengguna ke URL tertentu.
- Penggunaan: Saat menggunakan `HttpResponseRedirect()`, kamu perlu secara eksplisit memberikan URL atau path sebagai argumen.
- Kelebihan: Dapat digunakan untuk mengarahkan ke URL absolut atau relatif.
- Contoh:
    ```python
    from django.http import HttpResponseRedirect

    def my_view(request):
        return HttpResponseRedirect('/some-url/')
    ```

2. `redirect()`
- Tipe: Fungsi shortcut bawaan Django yang lebih canggih.
- Fungsi: Selain mengarahkan ke URL, `redirect()` juga dapat menerima beberapa jenis argumen seperti nama URL (dengan `reverse()` di belakang layar) atau objek model, yang membuatnya lebih fleksibel.
- Kelebihan:
Dapat menerima nama URL, objek model, atau string URL langsung, sehingga lebih efisien daripada menulis URL secara manual dan secara otomatis menggunakan mekanisme Django URL resolver untuk mencari path yang benar.
- Contoh:
    ```python
    from django.shortcuts import redirect

    def my_view(request):
    return redirect('some-url-name')
    ```
    ```python
    def my_view(request):
    return redirect('main:show_item', item_id=42)
    ```

### Cara Kerja Penghubungan Model `Product` dengan `User`
- Biasanya dilakukan menggunakan relasi _ForeignKey_ atau _ManyToManyField_, tergantung kebutuhan. 
- Dengan _ForeignKey_, satu produk terkait dengan satu pengguna, sementara *ManyToManyField* memungkinkan banyak produk dimiliki oleh banyak pengguna. 
- Relasi ini memungkinkan kita untuk mengakses data pengguna dari objek produk dan sebaliknya, melalui atribut otomatis yang dibuat oleh Django ORM.

### Autentikasi vs Otorisasi
Autentikasi merupakan proses untuk memverifikasi identitas pengguna. Dalam Django, ini berarti memastikan bahwa pengguna yang mengakses aplikasi benar-benar pengguna yang terdaftar. Sebaliknya, otorisasi adalah proses yang menentukan tindakan apa yang dapat atau tidak dapat dilakukan oleh pengguna setelah mereka berhasil diautentikasi, termasuk pengaturan hak akses dan izin pengguna.

### Penggunaan Cookies dan Keamanannya
Cookies adalah data kecil yang disimpan di perangkat pengguna oleh server web, digunakan untuk menyimpan informasi sesi atau preferensi pengguna antara kunjungan ke situs. Django menggunakan cookies untuk mengelola sesi, seperti menyimpan ID sesi pengguna.

Karena data dalam cookies bisa diakses dan dimanipulasi, mereka rentan terhadap peretasan jika tidak diamankan. Untuk mitigasi, praktik terbaik meliputi mengenkripsi data, menggunakan atribut HttpOnly dan Secure, serta menyimpan data sesi sensitif di server, bukan di cookies.

### Cara _Step by Step_ Mengimplementasikan _Checklist_ 
1. Pada file `views.py` menambahkan fungsi `register`, `login_user`, dan `logout_user`.
2. Membuat file baru pada `main/templates` bernama login serta laman-laman yang dimilikinya seperti `login.html` dan `register.html`.
3. Melakukan _routing urls_ dari fungsi yang ada sehingga pengguna dapat mengakses halaman registrasi melalui URL tersebut.
4. Mengimplementasikan cookie sehingga user masih berstatus login ketika menjelajahi laman utama pada file `views.py` dengan kode:
    ```python
    if form.is_valid():
        user = form.get_user()
        login(request, user)
        response = HttpResponseRedirect(reverse("main:show_main"))
        response.set_cookie('last_login', str(datetime.datetime.now()))
        return response
    ```
    Tambahkan juga `last_login` ke dalam _context_ `show_main`
    ```python
    context = {
        'name': request.user.username,
        'class' : 'PBP C',
        'product_entries': product_entries,
        'last_login': request.COOKIES['last_login'],
    }
    ```
5. Menambahkan ForeignKey untuk fungsi Product pada `models.py` dengan kode:
    ```python
    class Product(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    ```
6. Melakukan migrasi database untuk mensinkronkan database pada keseluruhan proyek.
</details>

## Tugas 5
<details>

### Urutan Prioritas CSS Selector
1. Inline Styles: Gaya yang ditetapkan langsung di dalam elemen HTML menggunakan atribut `style`. Contoh: 
    ```html
    <div style="color: red;"></div>
    ```
2. IDs: Selector dengan ID (ditulis dengan `#`). Contoh: 
    ```css
    #myId { color: blue; }
    ```
3. Classes, Attributes, and Pseudo-classes: Selector yang menggunakan class `(.classname)`, atribut `([attribute=value])`, atau pseudo-class `(:hover, :focus)`. Contoh: 
    ```css
    .myClass { color: green; }
    ```
4. Elements and Pseudo-elements: Selector yang menggunakan tag HTML (seperti `div`, `p`, dll.) atau pseudo-element (`::before`, `::after`). Contoh: 
    ```css
    div { color: black; }
    ```
5. Universal Selector: Selector universal (`*`), yang berlaku untuk semua elemen, memiliki prioritas terendah. Contoh: 
    ```css
    * { margin: 0; }
    ```
### _Responsive Design_ itu Penting
Responsive design sangat penting dalam pengembangan aplikasi web karena memungkinkan tampilan situs web disesuaikan dengan ukuran layar perangkat yang digunakan, seperti desktop, tablet, atau smartphone. Hal ini memastikan semua pengguna mendapatkan pengalaman yang konsisten dan optimal tanpa perlu memperbesar atau menggeser layar. Selain itu, mengembangkan satu situs responsif lebih efisien secara biaya dan waktu dibandingkan menciptakan versi terpisah untuk setiap perangkat.

Contoh aplikasi yang sudah menerapkan _responsive design_:
1. Facebook
2. Amazon
3. [scele.cs.ui.ac.id](scele.cs.ui.ac.id)

Contoh aplikasi yang belum menerapkan _responsive design_:
1. [dequeuniversity.com](https://dequeuniversity.com/library/responsive/1-non-responsive#)
2. [siak.ng](academic.ui.ac.id)
2. Beserta contoh lainnya yang kebanyakan merupakan laman (_website_) lama/jadul.

### Margin, Border, dan Padding
1. Margin: Ruang di luar batas elemen. Ini mengatur jarak antara elemen satu dengan yang lainnya.
    ```css
    .box {
    margin: 20px; /* memberi jarak 20px di semua sisi */
    }
    ```
2. Border: Garis yang mengelilingi elemen. Anda bisa mengatur ketebalan, jenis garis, dan warnanya.
    ```css
    .box {
    border: 2px solid black; /* garis tebal 2px, solid, berwarna hitam */
    }
    ```
3. Padding: Ruang di dalam batas elemen, antara konten dan border. Ini mengatur jarak antara konten dan tepi elemen.
    ```css
    .box {
    padding: 10px; /* memberi jarak 10px di semua sisi konten */
    }
    ```
Secara sederhana, urutan dari dalam ke luar adalah: konten > padding > border > margin.

### Flexbox dan Grid Layout
1. Flexbox: 
- Dirancang untuk mengatur elemen dalam satu dimensi, baik horizontal maupun vertikal, dengan cara mengatur ruang di antara elemen dan mendistribusikan ruang kosong. Hal inini memudahkan penataan elemen seperti menu navigasi atau card.
- Flexbox sangat berguna untuk meratakan elemen di tengah atau membuat tata letak responsif yang menyesuaikan dengan ukuran layar.

2. Grid Layout:
- Memungkinkan pembuatan tata letak dua dimensi, mengatur elemen dalam baris dan kolom. Dapat menciptakan desain yang lebih terstruktur dan kompleks, seperti halaman yang memiliki beberapa bagian (_header_, _sidebar_, _konten utama_, dan _footer_). 
- Misalnya, jika kita ingin membuat halaman blog, kita bisa menggunakan Grid untuk menempatkan gambar, teks, dan sidebar dengan cara yang teratur dan mudah dibaca.

### Cara _Step by Step_ Mengimplementasikan _Checklist_ 
1. Membuat fungsi `edit_product` dan `delete_product` pada `views.py`.
2. Melakukan _routing_ untuk urls untuk kedua fungsi baru tersebut.
3. Menambahkan Tailwind ke dalam aplikasi dalam `base.html`
4. Membuat direktori `main/static/css` dengan _file_ `global.css` sebagai membantu meminimalkan penggunaan kode serta agar _styling_ tetap konsisten.
5. Mengkustomisasi halaman _login_, _register_, dan _add product_ dengan _styling_ pada `main/templates` dengan CSS dan Tailwind.
6. Pada direktori `main/templates`, membuat file `navbar.html` serta tidak lupa untuk menambahkan `{% include 'navbar.html' %}` pada tiap _page_ yang membutuhkan _navigation bar_
7. Menambahkan informasi jika belum ada produk yang ditambahkan dan gambarnya pada `main.html`. 
8. Menginisialisasi _file_ baru dengan nama `card_product.html` untuk menampilkan detail produk yang sudah ditambahkan dalam bentuk _card_.
</details>

## Tugas 6
<details>

### Manfaat Penggunaan JavaScript dalam Pengembangan Aplikasi Web
JavaScript memungkinkan interaktivitas di halaman web, seperti validasi form secara real-time, manipulasi DOM, animasi, dan AJAX untuk pengambilan data tanpa me-refresh halaman. Ini meningkatkan user experience dan membuat aplikasi web lebih dinamis.

### Fungsi `await` pada `fetch()`:
`await` digunakan untuk menunggu hingga `fetch()` selesai dan mengembalikan respons sebelum kode berikutnya dieksekusi. Jika kita tidak menggunakan await, kode selanjutnya akan dijalankan sebelum hasil dari `fetch()` siap, yang dapat menyebabkan bug atau error.

### Mengapa Menggunakan `csrf_exempt` pada AJAX POST
`csrf_exempt` digunakan untuk menonaktifkan validasi CSRF pada view yang menerima request AJAX. Hal ini diperlukan karena request AJAX default-nya tidak menyertakan token CSRF, yang dapat menyebabkan request ditolak oleh server tanpa decorator ini.

### Mengapa Data Input Juga Dibersihkan di Backend
Pembersihan data di _backend_ penting untuk keamanan. _Frontend_ bisa dimanipulasi oleh pengguna, jadi _backend_ bertindak sebagai pertahanan terakhir untuk mencegah serangan seperti XSS atau SQL Injection.

### Cara _Step by Step_ Mengimplementasikan _Checklist_ 
1. Menambahkan _message error_ pada _function_ `views.py` yaitu `login_user`.
2. Membuat fungsi untuk menambahkan _product_ dengan AJAX dengan cara mengimpor dan menambahkan `add_product_ajax(request)` pada `views.py` 
3. _Routing_ pada `urls.py` untuk fungsi diatas.
4. Menampilkan data _product_ dengan `fetch()` API dengan menghapus `product_entry` dalam `views.py`
5. Lalu tambahkan pada fungsi `show_json` serta `show_xml` di berkas `views.py`
    ```python
    data = Product.objects.filter(user=request.user)
    ```
6. Pada berkas `main.html` menambahkan block `<script>` dengan inisialisasi fungsi 
    - `addProductEntry()`
    - `showError(field, message)`
    - `clearError(field)`
    - `handleBackendErrors(errorMessage)`
    - `getAddProduct()`
    - `refreshAddProduct()`
    - `show_modal()`
    - `hide_modal()`
</details>