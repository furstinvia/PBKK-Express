POKONYA CLONE BRANCH DAN CD KE PBKK-Express

### 3. **Install Dependencies**
   Sebelum menjalankan server, mereka perlu menginstall dependencies di dua bagian proyek: di folder utama dan di folder `admin-dashboard` (folder Vue.js).

   - **Install dependencies di PBKK-Express**:
     ```bash
     npm install
     ```

   - **Install dependencies di folder `admin-dashboard`**:
     ```bash
     cd admin-dashboard
     npm install
     cd ..
     ```

### 4. **Buat Database MySQL dan Konfigurasi**
   Teman Anda perlu membuat database di MySQL mereka dan mengkonfigurasinya agar terhubung dengan proyek.

   #### Langkah-langkah:
   - **Masuk ke MySQL dan buat database**:
     ```sql
     CREATE DATABASE film;
     ```
   - **Buat tabel `users` jika diperlukan**:
     ```sql
     USE film;
     CREATE TABLE users (
         id INT AUTO_INCREMENT PRIMARY KEY,
         username VARCHAR(255) NOT NULL,
         password VARCHAR(255) NOT NULL
     );
     ```
### 5. **Menjalankan Aplikasi**
   
   Setelah semua konfigurasi selesai, teman Anda bisa menjalankan aplikasi dengan cara berikut:

   - **Jalankan server utama PBKK-Express**:
     Di root proyek (folder utama):
     ```bash
     node index.js
     ```

  ATAU NPM START
   
   - **Jalankan frontend Vue.js cd admin-dashboard **:
     Di dalam folder `admin-dashboard`:
     ```bash
     npm run serve
     ```
     Ini akan menjalankan aplikasi Vue.js di mode pengembangan. Jika teman Anda ingin build untuk produksi:
     ```bash
     npm run build
     ```

### 6. **Ganti PORT (Mac)**

```js
const db = mysql.createConnection({
  host: 'localhost',
  user: 'root',        
  password: '',        
  database: 'film',    
  port: 3308          
});
```
