# finalproject
this is my project
public class Admin {
     static String[][] admin1 = {{"Hala", "0123456"}, {"admin", "98976"}};
     static String[][] booktitle = new String[100][4];//في المصفوفة الاولى بنخزن الكتاب في التانية بنخزن التفاصيل 
     static String[][] Del = new String[100][4];//هاي عشان نستخدمها في دالة الحدف
     static String[][] reservedBook = new String[100][5];//دالة للكتب الحجوزة
     static String[][]  CDBook = new String[100][5];//دالة عشان نحدف الكتب المحجوزة
     static int BookReserved=0;//هادا للكتب المحجوزة
     static int numberofbook;//لمعرفة عدد الكتب
     public static Boolean admin(String Name, String Password) {
        boolean A = false;
        for (int i = 0; i < admin1.length; i++) {
            if (Arrays.asList(admin1[i][0]).contains(Name)) {
                if (Arrays.asList(admin1[i][1]).contains(Password)) {
                    A = true;
                    break;
                } else {
                    A = false;
                }

            } else {
                A = false;
            }
        }
        return A;
    }
     public static void Add_Books(String Book_Tittle, int ISBN, String author) {
        booktitle[numberofbook][0] = Book_Tittle;
        booktitle[numberofbook][1] = Integer.toString(ISBN);//هان حولناه لنص عشان المصفوفة
        booktitle[numberofbook][2] = author;
        booktitle[numberofbook][3] = "Available";//هاي حالة الكتاب
        numberofbook++;
    }
     public static void Update_Book_Detail(int ISBN, String Book_Tittle, String ISBN1, String author  ,String status ) {
        for (int i = 0; i < numberofbook; i++) {
            if (Integer.toString(ISBN).equals(booktitle[i][1])) {
                booktitle[i][0] = Book_Tittle;
                booktitle[i][1] = ISBN1;//الرقم الجديد
                booktitle[i][2] = author ;
                booktitle[i][3] = status ;
                break;
            }
              }
                }
     public static void Delete_book (int ISBN){
          int Z = 0;
        int X = 0;
        int rm_index = 0;
        for (int i = 0; i < BookReserved; i++) {
            if (Integer.toString(ISBN).equals(Del[i][1])) {
                rm_index = i;
                break;
            }
        }
        for (int i = 0; i < CDBook.length; i++) {
            for (int j = 0; j < 5; j++) {
                if (X == 5) {
                    X = 0;
                }
                if (i == rm_index) {
                    Z = Z - 1;
                    break;
                }
                CDBook[Z][X] = Del[i][j];
                X++;
            }
            Z++;
        }
        BookReserved--;
    }
     public static void View_Late_Books() {
        System.out.println("The late book is:");
        for (int i = 0; i < numberofbook; i++) {
            if (booktitle[i][3].equals("late")) {
                System.out.println("Title :" + booktitle[i][0] + ", Number :" + booktitle[i][1]);
            } else {
                System.out.println("No late Book");
            }
        }
    }
     public static void View_Reserved_Books() {
        if (BookReserved == 0) {
            System.out.println("No book reserved");;
        } else {
            System.out.println("Reserved books is:");
            for (int i = 0; i < BookReserved; i++) {
                System.out.println("Title :" + reservedBook[i][0] + ", Number :" + reservedBook[i][1] + ", The stdu_id:" + reservedBook[i][4]);
            }
        }
    }
     public static void View_Student_Detail(int ISBN) {
     int f = 0;
        if (BookReserved == 0) {
            System.out.println("No books is reserved");
        } else {
            for (int i = 0; i < BookReserved; i++) {
                if (Integer.toString(ISBN).equals(reservedBook[i][4])) {
                    f++;
                }
                if (f == 0) {
                    System.out.println("No reserved book for this student");
                } else {
                    System.out.println("The number of books reserved for the student is:" + f);
                }
            }
        }
     }
     public static void View_All_Books() {
        for (int i = 0; i < numberofbook; i++) {
            System.out.println("Title :" + booktitle[i][0] + ", Number :" + booktitle[i][1] + ", auther :" + booktitle[i][2] + " ,status :" +booktitle[i][3]);
        }
    }
     public static void Search_For_Book(String input) {
        for (int i = 0; i < numberofbook; i++) {
            for (int j = 0; j < 4; j++) {
                if (booktitle[i][j].equals(input)) {
                    for (int x = 0; x < 4; x++) {
                        System.out.println(booktitle[i][x]);
                    }
                    break;
                }
            }
        }
    }
      public static void Return_book(String input) {
        String book_num = "";
        for (int i = 0; i < BookReserved; i++) {
            for (int j = 0; j < 5; j++) {
                if (reservedBook[i][j].equals(input)) {
                    for (int x = 0; x < 5; x++) {
                        book_num = reservedBook[i][1];
                        System.out.println(reservedBook[i][x]);
                    }
                }
            }
        }
        for (int i = 0; i < numberofbook; i++) {
            if (booktitle[i][1].equals(book_num)) {
                booktitle[i][3] = "Available";
                break;
            }
        }
        Delete_book(Integer.parseInt(book_num));
        NewArray(reservedBook, CDBook);
    }

public static void NewArray(String[][] x, String[][] y) {
        for (int i = 0; i < x.length; i++) {
            for (int j = 0; j < x[i].length; j++) {
                x[i][j] = y[i][j];
            }
        }
    }
public static void PrintNumTitleBook() {
        for (int i = 0; i < numberofbook; i++) {
            System.out.println("Title :" + booktitle[i][0] + ", Number :" + booktitle[i][1]);
        }
    }
}




import static finalproject3.Admin.Add_Books;
import static finalproject3.Admin.Del;
import static finalproject3.Admin.Delete_book;
import static finalproject3.Admin.NewArray;
import static finalproject3.Admin.PrintNumTitleBook;
import static finalproject3.Admin.Return_book;
import static finalproject3.Admin.Search_For_Book;
import static finalproject3.Admin.View_All_Books;
import static finalproject3.Admin.View_Late_Books;
import static finalproject3.Admin.View_Reserved_Books;
import static finalproject3.Admin.admin;
import static finalproject3.Admin.View_Student_Detail;
import static finalproject3.Admin.booktitle;
import java.util.Scanner;

/**
 *
 * @author hp
 */
public class Finalproject3 {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
         Admin X = new Admin();
        System.out.println("Welcom ");
        while (true) {
            System.out.println("please,enter your choice(Admin 11 , Student 22 , Exit 33");
            Scanner input = new Scanner(System.in);
            int yourchice = input.nextInt();
            if (yourchice == 11 || yourchice == 22|| yourchice == 33){
            if (yourchice == 11) {
            System.out.println("Please.enter your name:");
            Scanner inputx = new Scanner(System.in);
                String Name = inputx.next();
                System.out.println("Please,enter your password:");
                Scanner inputp = new Scanner(System.in);
                String password = inputp.next(); 
                boolean CheckTheAdmin = admin(Name, password);
                
                if (CheckTheAdmin) {
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
        Scanner inputv = new Scanner(System.in);
        int userchoice = inputv.nextInt();
                
        switch(userchoice){
            case 1:     
        System.out.println("Please,Enter The_Book_Tittle: ");
        Scanner input5 = new Scanner(System.in);
        String Book_Tittle = input5.next();
        System.out.println("Pleas,Enter The_ISBN: ");
        Scanner input6 = new Scanner(System.in);
        int ISBN = input6.nextInt();
        System.out.println("Please enter The author: ");
        Scanner input7 = new Scanner(System.in);
        String author = input7.next();
        Add_Books(Book_Tittle , ISBN , author);
        break;
                
            case 2:
        break;
                
            case 3:
        System.out.println("Pleas,Enter The_num:");
        Scanner input11 = new Scanner(System.in);
        int num = input11.nextInt();
        if (Integer.toString(num).equals("ISBN")){
        System.out.println("please.Enter New_Book_Tittle: ");
        Scanner input8 = new Scanner(System.in);
        String New_Book_Tittle = input8.next();
        System.out.println("please.Enter new_ISBN:");
        Scanner input9 = new Scanner(System.in);
        String New_ISBN = input9.next();
        System.out.println("please.Enter new_author:");
        Scanner input10 = new Scanner(System.in);
        String New_author = input10.next();
        }else{
        System.out.println("Invalid num:(");
        }
        break;
            case 4:
                System.out.println("Please enter the book number: ");
        PrintNumTitleBook();
        Scanner input20 = new Scanner(System.in);
        int book_num = input20.nextInt();
        Delete_book ( book_num);
        NewArray(booktitle, Del);
        PrintNumTitleBook();
        break;
            case 5:
        View_Late_Books();
        break;
            case 6:
        View_Reserved_Books();
        break;
            case 7:
        System.out.println("Please enter the student number: ");
        Scanner input12 = new Scanner(System.in);
        int stu_no = input12.nextInt();
        View_Student_Detail(stu_no);
        break;
            case 8:
        View_All_Books();
        break;
            case 9:
        System.out.println("Please enter book title or book number or author");
        Scanner input13 = new Scanner(System.in);
        String admins = input13.next();
        Search_For_Book(admins);
        break; 
        
            case 10:
        System.out.println("Please enter book number or Student id:");
        Scanner input14 = new Scanner(System.in);
        admins = input14.next();
        Return_book(admins);
        break;
         
        }
        
             
  
        }
         
                 }
        
        }
    }  
    }
    }
