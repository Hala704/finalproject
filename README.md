# finalproject
this is my project
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package final_project;

import java.util.ArrayList;
import java.util.Scanner;

/**
 *
 * @author hp
 */
public class Final_project {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        
        ArrayList<Book> books = new ArrayList<Book>();
        Book b1 = new   Book (1 , "War and Peace" , "Leo Tolstoy" , "available");
        books.add(b1);
        Book b2 = new   Book (2 , "Song of Solomon" , "Toni Morrison" , "reserved");
        books.add(b2);
        Book b3 = new   Book (3 , "Ulysses" , "James Joyce" , "available");
        books.add(b3);
        Book b4 = new   Book (4 , "Shadow of the Wind" , "Carlos Ruiz Zafon" , "reserved");
        books.add(b4);
        Book b5 = new   Book (5 , " Lord of the Rings" , "CJ.R.R. Tolkien" , "late");
        books.add(b5);

        ArrayList<Student> Students = new ArrayList<Student>();
        ArrayList<Book> booksforS1 = new ArrayList<Book>();
        booksforS1.add(b2);
        Student s1 = new Student ("s1" , 12345 ,booksforS1 );
        Students.add(s1);

        ArrayList<Book> booksforS2 = new ArrayList<Book>();
        booksforS1.add(b4);
        Student s2 = new Student ("s2" , 12345 ,booksforS2 );
        Students.add(s2);

        ArrayList<Book> booksforS3 = new ArrayList<Book>();
        Student s3 = new Student ("s3" , 12345 ,booksforS3 );
        Students.add(s3);

        Scanner input = new Scanner(System.in);
        System.out.println("Welcom ");
        System.out.println("please,enter your choice(Admin 11 , Student 22 , Exit 33");
        int yourchice = input.nextInt();
        if (yourchice ==11) {
            System.out.println("Please.enter your name:");
            String Name = input.next();
            System.out.println("Please,enter your password:");
            int password = input.nextInt();

            if (Name.equalsIgnoreCase("Admin") && password == 12345 ){
                while(true){
                System.out.println("1- Add new book");
                System.out.println("2- Check book status");
                System.out.println("3- Update book detail");
                System.out.println("4- Delete book");
                System.out.println("5- View late books");
                System.out.println("6- View reserved books");
                System.out.println("7- View student detail");
                System.out.println("8- View all books");
                System.out.println("9- Search for book");
                System.out.println("10-Return book (change book status)");
                System.out.println("11- To exit");
                System.out.println("Please,Enter Your Choice :)");
                int userchoice = input.nextInt();
                switch(userchoice){
                    case 1:
                        System.out.println("Pleas,Enter The_ISBN: ");
                        int ISBN = input.nextInt();
                        System.out.println("Please,Enter The_Book_Tittle: ");
                        String Book_Tittle = input.next();
                        System.out.println("Please enter The author: ");
                        String author = input.next();
                        System.out.println("Please enter The status: ");
                        String status = input.next();
                   books.add(new Book(ISBN ,Book_Tittle ,author ,status ));
                    break;
                    case 2:
                        System.out.println("Pleas,Enter The_ISBN: ");
                        int ISBN2 = input.nextInt();
                        for (int i = 0 ; i < books.size() ;i++){
                           if (books.get(i).getISBN() ==ISBN2) {
                               System.out.println(books.get(i).getStatus());
                           }
                        }
                        break;
                    case 3:
                        System.out.println("Pleas,Enter The_ISBN: ");
                        int ISBN3 = input.nextInt();
                        for (int i = 0 ; i < books.size() ;i++){
                            if (books.get(i).getISBN() ==ISBN3) {
                                System.out.println("Enter new Title");
                                String new_title = input.next();
                                System.out.println("Enter new author");
                                String new_author = input.next();
                                System.out.println("Enter new status");
                                String new_status = input.next();
                                books.get(i).setTitle(new_title);
                                books.get(i).setAuthor(new_author);
                                books.get(i).setStatus(new_status);
                            }
                        }
                        break;
                    case 4:
                        System.out.println("Pleas,Enter The_ISBN: ");
                        int ISBN4 = input.nextInt();
                        for (int i = 0 ; i < books.size() ;i++){
                            if (books.get(i).getISBN() ==ISBN4) {
                          books.remove(i);
                            }
                        }
                        break;
                    case 5:
                        for (int i = 0 ; i < books.size() ;i++){
                      if( books.get(i).getStatus() =="late") {
                          System.out.println(books.get(i).getTitle());
                      }
                        }
                        break;
                    case 6:
                        for (int i = 0 ; i < Students.size() ;i++){
                         for (int j = 0 ; j < Students.get(i).getReservedBooks().size() ;j++){
                             System.out.println("Student id : "+ Students.get(i).getId());
                             System.out.println("book title : "+Students.get(i).getReservedBooks().get(j).getTitle());
                        } }
                        break;
                    case 7:
                        System.out.println(" Enter Student id : ");
                        String Sid = input.nextLine();
                        for (int i = 0 ; i < Students.size() ;i++){
                         if (Students.get(i).getId() == Sid){
                             System.out.println("id :" + Students.get(i).getId() + "password" + Students.get(i).getPassword()
                             +" reserved books "+ Students.get(i).getReservedBooks().size()
                             );
                         }
                        }
                        break;
                    case 8:
                        for (int i = 0 ; i < books.size() ;i++){
                        System.out.println("BOOK Title "+ books.get(i).getTitle()
                        +"BOOK ISBN" + books.get(i).getISBN() +"BOOK Author" + books.get(i).getAuthor()
                        +"BOOK Status" + books.get(i).getStatus()
                        );
                        }
                        break;
                    case 9:
                        System.out.println("To search for the book by the title press 1," +
                                " to search by the author press 2, to search by ISBN press 3 ");
                        int in = input.nextInt();
                        switch (in){
                            case 1 :
                                System.out.println(" enter title ");
                                String title = input.nextLine();
                                for (int i = 0 ; i < books.size() ;i++){
                                    if (books.get(i).getTitle() == title){
                                        System.out.println("BOOK Title "+ books.get(i).getTitle()
                                                +"BOOK ISBN" + books.get(i).getISBN() +"BOOK Author" + books.get(i).getAuthor()
                                                +"BOOK Status" + books.get(i).getStatus()
                                        );
                                    }

                                }
                                break;
                            case 2 :
                                System.out.println(" enter author ");
                                String author1 = input.nextLine();
                                for (int i = 0 ; i < books.size() ;i++){
                                    if (books.get(i).getAuthor() == author1){
                                        System.out.println("BOOK Title "+ books.get(i).getTitle()
                                                +"BOOK ISBN" + books.get(i).getISBN() +"BOOK Author" + books.get(i).getAuthor()
                                                +"BOOK Status" + books.get(i).getStatus()
                                        );
                                    }

                                }
                                break;
                            case 3 :
                                System.out.println(" enter ISBN ");
                                int ISBN1 = input.nextInt();
                                for (int i = 0 ; i < books.size() ;i++){
                                    if (books.get(i).getISBN() == ISBN1){
                                        System.out.println("BOOK Title "+ books.get(i).getTitle()
                                                +"BOOK ISBN" + books.get(i).getISBN() +"BOOK Author" + books.get(i).getAuthor()
                                                +"BOOK Status" + books.get(i).getStatus()
                                        );
                                    }

                                }
                                break;
                        }
                        break;
                    case 10:
                        System.out.println(" enter ISBN ");
                        int ISBN1 = input.nextInt();
                        System.out.println(" enter Student id : ");
                        String sid = input.nextLine();
                        for (int i = 0 ; i < books.size() ;i++){
                            if (books.get(i).getISBN() == ISBN1){
                                books.get(i).setStatus("available");
                                for (int x = 0 ; x < Students.size() ;x++){
                            if (Students.get(x).getId() == sid ){
                                Students.get(x).getReservedBooks().remove(books.get(i) );
                             Students.get(x).setReservedBooks(Students.get(x).getReservedBooks());
                                    }
                                }
                            }}


                        break;
                    case 11:
                        break;
                }
            }
            }


        } else if (yourchice ==22){
            System.out.println("Please.enter your name:");
            String Name = input.next();
            System.out.println("Please,enter your password:");
            int password = input.nextInt();
            if (Name.equalsIgnoreCase("Hala") && password == 12345 ){
                while(true){
                System.out.println("1- Search for book");
                System.out.println("2- Reserve book");
                System.out.println("3- Check book status ");
                System.out.println("4- Renew book ");
                System.out.println("Please,Enter Your Choice :)");
                int userchoice = input.nextInt();
                switch(userchoice){
                    case 1:
                        System.out.println( "To search for the book by the title press 1," +
                        " to search by the ISBN press 2 ");
                        int inp = input.nextInt();
                        if (inp ==1 ){
                            System.out.println(" enter title ");
                            String title = input.nextLine();
                            for (int i = 0 ; i < books.size() ;i++){
                                if (books.get(i).getTitle() == title){
                                    System.out.println("BOOK Title "+ books.get(i).getTitle()
                                            +"BOOK ISBN" + books.get(i).getISBN() +"BOOK Author" + books.get(i).getAuthor()
                                            +"BOOK Status" + books.get(i).getStatus()
                                    );
                                }

                            }
                        } else  if (inp ==2){
                            System.out.println(" enter ISBN ");
                            int ISBN1 = input.nextInt();
                            for (int i = 0 ; i < books.size() ;i++){
                                if (books.get(i).getISBN() == ISBN1){
                                    System.out.println("BOOK Title "+ books.get(i).getTitle()
                                            +"BOOK ISBN" + books.get(i).getISBN() +"BOOK Author" + books.get(i).getAuthor()
                                            +"BOOK Status" + books.get(i).getStatus()
                                    );
                                }

                            }
                        }
                        break;
                    case 2:
                        System.out.println(" enter title ");
                        String title = input.nextLine();
                        for (int i = 0 ; i < books.size() ;i++){
                            if (books.get(i).getTitle() == title){
                              if (books.get(i).getStatus().equalsIgnoreCase("available") ) {
                                  books.get(i).setStatus("reserve");
                                  System.out.println(" done ");
                              }
                              else {
                                  System.out.println(" sorry book reserve ");
                              }
                            }
                        }
                        break;
                    case 3:
                        System.out.println( "To search for the book by the title press 1," +
                                " to search by the author press 2 ");
                        int in = input.nextInt();
                        if (in == 1){
                            System.out.println("Pleas,Enter The title: ");
                            String title1 = input.nextLine();
                            for (int i = 0 ; i < books.size() ;i++){
                                if (books.get(i).getTitle() == title1){
                                    System.out.println("title : "+ title1 + "Status"+books.get(i).getStatus());
                                }
                            }
                        } else if (in == 2){
                            System.out.println("Pleas,Enter The author: ");
                            String author = input.nextLine();
                            for (int i = 0 ; i < books.size() ;i++){
                                if (books.get(i).getAuthor() == author){
                                    System.out.println("title : "+ books.get(i).getTitle() + "Status"+books.get(i).getStatus());
                                }
                            }
                        }
                        break;
                    case 4:
                        System.out.println(" done ");
                        break;

                }
            }
        } else {
            System.out.println("Thank you");
            System.exit(0) ;
       
    }
        }
}}




/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package final_project;

/**
 *
 * @author hp
 */
public class Book {
    private int ISBN ;
    private String title ;
    private String author ;
    private String status ;

    public Book(int ISBN, String title, String author, String status) {
        this.ISBN = ISBN;
        this.title = title;
        this.author = author;
        this.status = status;
    }

    public int getISBN() {
        return ISBN;
    }

    public void setISBN(int ISBN) {
        this.ISBN = ISBN;
    }

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getAuthor() {
        return author;
    }

    public void setAuthor(String author) {
        this.author = author;
    }

    public String getStatus() {
        return status;
    }

    public void setStatus(String status) {
        this.status = status;
    }
    
    
}




/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package final_project;

import java.util.ArrayList;

/**
 *
 * @author hp
 */
public class Student {
    private String id ;
    private int password ;
   private  ArrayList<Book> reservedBooks = new ArrayList<Book>();

    public Student(String id, int password , ArrayList<Book> reservedBooks
    ) {
        this.id = id;
        this.password = password;
        this.reservedBooks = reservedBooks;
    }

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public int getPassword() {
        return password;
    }

    public void setPassword(int password) {
        this.password = password;
    }

    public ArrayList<Book> getReservedBooks() {
        return reservedBooks;
    }

    public void setReservedBooks(ArrayList<Book> reservedBooks) {
        this.reservedBooks = reservedBooks;
    }
    
}

