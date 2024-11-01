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
   - **Buat semua tabel**:
     ```sql
            CREATE TABLE users (
        id INT AUTO_INCREMENT PRIMARY KEY,
        username VARCHAR(50) NOT NULL,
        password VARCHAR(255) NOT NULL
        );

        CREATE TABLE movies (
        id INT AUTO_INCREMENT PRIMARY KEY,
        title VARCHAR(255) NOT NULL,
        genre VARCHAR(100),
        release_year INT,
        rating DECIMAL(3, 1),
        description TEXT,
        image_path VARCHAR(255) -- Added image_path column here
      );

        INSERT INTO movies (title, genre, release_year, rating, description, image_path) VALUES
        ('Inception', 'Sci-Fi', 2024, 8.8, 'A thief who steals corporate secrets through the use of dream-sharing technology.', './images/inception.jpeg'),
        ('The Matrix', 'Sci-Fi', 2024, 8.7, 'A computer hacker learns about the true nature of his reality.', './images/matrix.jpg'),
        ('Interstellar', 'Sci-Fi', 2024, 8.6, 'A team of explorers travel through a wormhole in space.', './images/interstellar.jpg'),
        ('The Dark Knight', 'Action', 2024, 9.0, 'Batman raises the stakes in his war on crime.', './images/thedarkknight.jpg');

        CREATE TABLE theaters (
        id INT AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(255) NOT NULL,
        location VARCHAR(255),
        capacity INT,
        description TEXT,
        image_path VARCHAR(255)
        );

        INSERT INTO theaters (name, location, capacity, description, image_path) VALUES
        ('Grand IMAX Cinema', 'Downtown', 300, 'Experience the ultimate in movie watching with crystal-clear IMAX screens and immersive sound.', './images/c1.jpg'),
        ('Luxe VIP Cinema', 'Uptown', 200, 'Enjoy the ultimate luxury cinema experience with reclining seats, private lounges, and gourmet snacks.', './images/c2.jpg'),
        ('Outdoor Drive-In', 'Countryside', 150, 'Enjoy a nostalgic movie night under the stars at our classic outdoor drive-in theater.', './images/c3.png'),
        ('Cinema City', 'City Center', 400, 'A popular theater with a wide variety of movie selections and premium seating options.', './images/c4.jpg');

        CREATE TABLE bookings (
        id INT AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(255) NOT NULL,
        movie_id INT NOT NULL,
        theater_id INT NOT NULL,
        booking_date DATE NOT NULL,
        seats INT NOT NULL,
        FOREIGN KEY (movie_id) REFERENCES movies(id) ON DELETE CASCADE,
        FOREIGN KEY (theater_id) REFERENCES theaters(id) ON DELETE CASCADE
        );

        CREATE TABLE payments (
        id INT AUTO_INCREMENT PRIMARY KEY,
        booking_id INT NOT NULL,
        amount DECIMAL(10, 2) NOT NULL,
        payment_date DATE NOT NULL,
        status ENUM('paid', 'pending', 'failed') DEFAULT 'pending',
        FOREIGN KEY (booking_id) REFERENCES bookings(id) ON DELETE CASCADE
        );

      
     ```
### 5. **ADA 2 MODE, EDIT DAN BUILD**
   
   INI EDIT

   - **Jalankan server utama PBKK-Express**:
     Di root proyek (folder utama):
     ```bash
       node index.js
     ```
   
   - **Jalankan frontend Vue.js cd admin-dashboard **:

     Di dalam folder `admin-dashboard`:
     ```bash
       npm run dev
     ```

INI BUILD ( kalo build gabisa edit vue yaaaa & tetep jalanin node index.js nya setelah ke build)
   
   di cd admin-dashboard

 ```bash
 npm run build
 ```


### 6. **Ganti PORT kalo perlu (Mac)**

```js
const db = mysql.createConnection({
  host: 'localhost',
  user: 'root',        
  password: '',        
  database: 'film',    
  port: 3308          
});
```

NOTE : 

1. Misal mau mode edit vue, jalanin langkah atas, edit di `http://localhost:3000/admin/`

tetep jalanin backend nya di localhost:3001

  perbedaan port front end : 3000

 back end : 3001

   gunanya biar bisa barengan editnya

