# perpus_Association_Anis
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author
        self.is_available = True

class LibraryMember:
    def __init__(self, name):
        self.name = name
        self.borrowed_books = []

    def borrow_book(self, book):
        if book.is_available:
            book.is_available = False
            self.borrowed_books.append(book)
            print("Buku", book.title, "telah dipinjam oleh", self.name)
        else:
            print("Buku", book.title, "sedang tidak tersedia")

    def return_book(self, book):
        if book in self.borrowed_books:
            book.is_available = True
            self.borrowed_books.remove(book)
            print("Buku", book.title, "telah dikembalikan oleh", self.name)
        else:
            print("Anda tidak meminjam buku", book.title)

    def display_borrowed_books(self):
        print("Daftar Buku yang Dipinjam oleh", self.name)
        print("--------------------")
        for book in self.borrowed_books:
            print("Judul:", book.title)
            print("Penulis:", book.author)
            print("Ketersediaan:", "Tersedia" if book.is_available else "Dipinjam")
            print("--------------------")

# Membuat objek LibraryMember
member = LibraryMember("safiQa risqika arif")

# Membuat objek Book
book1 = Book("dilan", "pidi baiq")
book2 = Book("rindu", "Tere liye")
book3 = Book("tenggelamnya kapal van der wijck", "hamka")
# Meminjam buku
member.borrow_book(book1)
member.borrow_book(book2)

# Menampilkan daftar buku yang dipinjam
member.display_borrowed_books()

# Mengembalikan buku
member.return_book(book1)

# Menampilkan daftar buku yang dipinjam setelah pengembalian
member.display_borrowed_books()
