# TomRater


class TomRater:
    def __init__(self):
        self.users = {}
        self.book = {}
        
    def create_book(self, title, isbn):
        self.title = title
        self.isbn = str(isbn)
        Book(title,isbn)
        return self.title + " " + self.isbn 
        
    def create_novel(self, title, author, isbn):
        self.title = title
        self.isbn = str(isbn)
        self.author = author
        Fiction(title, author, isbn)
        return Fiction(title, author, isbn)
        
    def create_non_fiction(self, title, subject, level, isbn):
        self.title = title
        self.subject = subject
        self.level = level
        self.isbn = str(isbn)
        return Non_fiction(title, subject, level, isbn)
        
    def add_book_to_user(self, book, email, rating = None):
        self.book = book
        self.email = email
        self.rating = rating
        
        for email, user in self.users.items():
            if user not in self.users.values():
                return "No user with email {email}!"
            else:
                
                
    def print_catalog(self):
        for keys in self.book.keys():
            return keys 
    
    

class User:
    def __init__(self, name, email):
        self.name = name
        self.email = email
        self.books = {}

    def get_email(self):
        return self.email
       

    def change_email(self):
        self.email = self.name + "@gmail.net"
        return "Your email has been updated succesfully!"
        
    
    def __repr__(self):
        return "The user " + self.name + " with email: " + self.email + "had read " + str(self.books) + " books."

    def __eq__(self, other):
        if self.name == other.name:
            if self.email == other.email:
                return True
            
    
    def read_book(self, book, rating = None):
        return self.books.update({book:rating})
    def get_average_rating(self):
        total_ratings = 0
        total_books = 0
        for values in self.books.values():
             total_ratings += values
             total_books += 1
        return total_ratings/total_books

class Book:
    def __init__(self, title, isbn):
        self.title = title
        self.isbn = int(isbn)
        self.ratings = []
        
    def get_title(self):
        return self.title
        
    def get_isbn(self):
        return self.isbn
        
    def set_isbn(self):
        self.isbn = 535367667788964
        return "Your isbn has been updated succesfully! " + str(self.isbn)
        
    def add_rating(self,rating):
        self.rating = rating
        if rating <= 0 and rating >= 4:
            return self.ratings.append(rating)
        else:
            return "Invalid Rating"
    def __eq__(self, other):
        if self.name == other.name:
            if self.isbn == other.isbn:
                return True
    def __hash__(self):
        return hash((self.title, self.isbn))            
    def get_average_rating(self):
        total_ratings = 0
        total_books = 0
        for values in self.ratings:
             total_ratings += values
             total_books += 1
        return total_ratings/total_books
        
 
class Fiction(Book):
    def __init__(self, title, isbn):
        super().__init__(self, title, isbn)
    def __init__(self, title, author, isbn):
        self.title = title
        self.author = author
        self.isbn = isbn
    def get_author(self):
        return self.author
    def __repr__(self):
        return "{} by {}".format(self.title, self.author)

class Non_fiction(Book):
    def __init__(self, title, isbn):
        super().__init__(self, title, isbn)
    def __init__(self, title, subject, level, isbn):
        self.title = title
        self.subject = subject
        self.level = level
        self.isbn = isbn
        
    def get_subject(self):
        return self.subject
        
    def get_level(self):
        return self.level
        
    def __repr__(self):
        return "{} a/an {} manual on {}".format(self.title, self.level, self.subject)

#definition of the first User
first_user = User("Paul", "paul.stein@gmail.net")
second_user = User("Paul", "paul.stein@gmail.net")
first_book = Book("The Jungle Book", 57777777777777)
second_book = Book("Peter Pan", 677777777)
fiction = Fiction("The yellow submarine", "Roger federer", 955848466334)
non_fiction = Non_fiction("Bubadu", "Geology", "advanced", 785567838393)
tommy = TomRater()

new_book = tommy.create_book("My biography", 199922233)
new_nonfiction_book = tommy.create_non_fiction("My biography", "Paul", "High", 199922233)
