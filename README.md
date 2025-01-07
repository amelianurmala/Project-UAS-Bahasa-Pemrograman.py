# Project-UAS-Bahasa-Pemrograman.py

## Nama   : Amelia Nurmala Dewi
## Kelas  : TI.24.A2
## NIM    : 312410199

Berikut adalah program sederhana sesuai dengan persyaratan yang ditunjukkan pada soal. Persyaratan tersebut menentukan pembuatan program dengan konsep modular dan OOP, dengan validasi input dan tampilan output. 

*1. Class StudentData:*

    class StudentData:
        def __init__(self):
            self.students = []

"membuat class StudentData yang berfungsi untuk menyimpan data. Constructor _init_ membuat list kosong yang akan menampung data mahasiswa."

  
    def add_student(self, nim, name, grade):
        student = {
            'nim': nim,
            'name': name,
            'grade': grade
        }
        self.students.append(student)

"Method add_student berguna untuk menambah data mahasiswa baru. Data disimpan dalam bentuk dictionary dengan key 'nim', 'name', dan 'grade', lalu ditambahkan ke dalam list students."


    def get_all_students(self):
        return self.students

"Method get_all_students sederhana saja, hanya mengembalikan semua data mahasiswa yang tersimpan."

*2. Class InputProcessor:*

    class InputProcessor:
        @staticmethod
        def validate_nim(nim):
            if not nim.isdigit() or len(nim) != 8:
                raise ValueError("NIM harus berupa 8 digit angka")
            return nim

"Class InputProcessor menangani validasi input. Method validate_nim memastikan NIM berupa 8 digit angka. Jika tidak sesuai, akan memunculkan error."


    @staticmethod
    def validate_name(name):
        if len(name.strip()) < 3:
            raise ValueError("Nama harus minimal 3 karakter")
        return name.strip()

"validate_name memeriksa panjang nama, minimal harus 3 karakter. strip() menghapus spasi di awal dan akhir nama."


    @staticmethod
    def validate_grade(grade):
        try:
            grade = float(grade)
            if grade < 0 or grade > 100:
                raise ValueError
            return grade
        except ValueError:
            raise ValueError("Nilai harus berupa angka antara 0-100")

"validate_grade memastikan nilai berupa angka antara 0-100. Menggunakan try-except untuk menangani error jika input bukan angka."

*3. Class StudentView:*

    class StudentView:
        @staticmethod
        def display_header():
            print("\n" + "="*50)
            print(f"{'NIM':<12}{'NAMA':<20}{'NILAI':<10}{'GRADE':<8}")
            print("="*50)

"StudentView menangani tampilan output. display_header membuat header tabel dengan format yang rapi."


    @staticmethod
    def get_letter_grade(score):
        if score >= 85: return 'A'
        elif score >= 75: return 'B'
        elif score >= 60: return 'C'
        elif score >= 45: return 'D'
        else: return 'E'

"get_letter_grade mengkonversi nilai angka menjadi huruf. Misalnya nilai 85 ke atas dapat A, 75-84 dapat B, dan seterusnya."


    def display_students(self, students):
        self.display_header()
        for student in students:
            grade = self.get_letter_grade(student['grade'])
            print(f"{student['nim']:<12}{student['name']:<20}{student['grade']:<10.1f}{grade:<8}")
        print("="*50)

"display_students menampilkan data dalam bentuk tabel. Menggunakan format string untuk mengatur lebar kolom agar rapi."

*4. Main Program:*

    def main():
        data = StudentData()
        processor = InputProcessor()
        view = StudentView()

"Di fungsi main, kita membuat objek dari ketiga class yang sudah dibuat."


    while True:
        print("\nProgram Manajemen Data Mahasiswa")
        print("1. Tambah Data Mahasiswa")
        print("2. Lihat Data Mahasiswa")
        print("3. Keluar")
        
        choice = input("\nPilih menu (1-3): ")

"Program menampilkan menu dan meminta input pilihan dari user."


        if choice == '1':
            try:
                nim, name, grade = processor.get_student_input()
                data.add_student(nim, name, grade)
                print("\nData berhasil ditambahkan!")
            except ValueError as e:
                print(f"\nError: {str(e)}")

"Jika pilihan 1, program akan meminta input data mahasiswa. Try-except menangani error jika input tidak valid."

*Demo Program:*
"Mari kita coba jalankan programnya:
1. Masukkan NIM: 31241019
2. Masukkan Nama: Amelia Nurmala Dewi
3. Masukkan Nilai: 85
Program akan menyimpan data dan bisa ditampilkan dalam bentuk tabel."
