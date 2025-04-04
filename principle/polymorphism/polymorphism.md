# Đa hình (Polymorphism)
### Khái niệm
- Là khả năng một phương thức hoặc hành động có thể thể hiện theo nhiều cách khác nhau, tùy thuộc vào loại đối tượng thực tế.

- Đây là một đặc điểm quan trọng của lập trình hướng đối tượng (OOP), giúp các đối tượng có thể có hành vi khác nhau dựa trên lớp mà chúng thuộc về.

### Ví dụ
- Một người có thể có nhiều vai trò khác nhau cùng một lúc.
    - Một người đàn ông có thể vừa là một người cha, vừa là một người chồng, và cũng có thể là một nhân viên.

- Mỗi vai trò có những hành vi riêng biệt trong từng tình huống khác nhau.

- Đây chính là nguyên lý của đa hình.

```java
// Lớp cha Person
class Person {
  
    // Phương thức hiển thị vai trò của một người
    void role() {
        System.out.println("I am a person.");
    }
}

// Lớp con Father kế thừa từ Person và ghi đè phương thức role()
class Father extends Person {
  
    // Ghi đè phương thức để thể hiện vai trò của người cha
    @Override
    void role() {
        System.out.println("I am a father.");
    }
}

public class Main {
    public static void main(String[] args) {
      
        // Tạo một tham chiếu kiểu Person nhưng khởi tạo bằng đối tượng Father
        Person p = new Father();
        
        // Gọi phương thức role(), phương thức bị ghi đè trong lớp Father sẽ được gọi
        p.role();  
    }
}
```

- Lớp `Person` có một phương thức `role()` in ra một thông báo chung.

- Lớp `Father` kế thừa từ `Person` và ghi đè (`override`) phương thức `role()` để in ra một thông báo riêng.

- Trong `main()`, một biến tham chiếu kiểu `Person` được gán một đối tượng của `Father`.

- Khi gọi `p.role()`, do tính chất đa hình tại thời gian chạy (`runtime polymorphism`), phương thức `role()` của `Father` sẽ được thực thi thay vì của `Person`.

# Các loại đa hình
- Trong Java, đa hình được chia thành hai loại chính:

    - Đa hình lúc biên dịch (Compile-Time Polymorphism)

    - Đa hình lúc chạy (Runtime Polymorphism)

### Đa hình lúc biên dịch
- Còn được gọi là đa hình tĩnh (static polymorphism).

- Được thực hiện thông qua `nạp chồng phương thức` (`Method Overloading`).

- Lưu ý:
    - Java không hỗ trợ nạp chồng toán tử (Operator Overloading) như C++.

- Nạp chồng phương thức trong Java xảy ra khi có nhiều phương thức cùng tên nhưng khác nhau về số lượng hoặc kiểu tham số.

```java
class Helper {

    // Phương thức nhân hai số nguyên
    static int Multiply(int a, int b) {
        return a * b;
    }

    // Phương thức nhân hai số thực
    static double Multiply(double a, double b) {
        return a * b;
    }
}

class Geeks {
    public static void main(String[] args) {
        System.out.println(Helper.Multiply(2, 4));     // Gọi phương thức Multiply(int, int)
        System.out.println(Helper.Multiply(5.5, 6.3)); // Gọi phương thức Multiply(double, double)
    }
}
```

- Khi gọi `Multiply(2, 4)`, chương trình sẽ gọi phương thức có tham số kiểu `int`.

- Khi gọi `Multiply(5.5, 6.3)`, chương trình sẽ gọi phương thức có tham số kiểu `double`.

- Trình biên dịch quyết định phương thức nào sẽ được gọi dựa vào kiểu dữ liệu của tham số → đây là đa hình lúc biên dịch.

### Đa hình lúc chạy
- Còn được gọi là gửi phương thức động (Dynamic Method Dispatch).

- Trong Java, đa hình lúc chạy đạt được thông qua `ghi đè phương thức` (`Method Overriding`).

- `Ghi đè phương thức` xảy ra khi một lớp con định nghĩa là một phương thức của lớp cha

```java
class Parent {
    void Print() {
        System.out.println("parent class");
    }
}

class subclass1 extends Parent {
    void Print() { 
        System.out.println("subclass1"); 
    }
}

class subclass2 extends Parent {
    void Print() {
        System.out.println("subclass2");
    }
}

class Geeks {
    public static void main(String[] args) {
        Parent a; // Tham chiếu kiểu Parent

        a = new subclass1(); // Đối tượng subclass1
        a.Print();  // Gọi phương thức Print() của subclass1

        a = new subclass2(); // Đối tượng subclass2
        a.Print();  // Gọi phương thức Print() của subclass2
    }
}
```

- Biến tham chiếu `a` có kiểu `Parent`, nhưng nó trỏ đến các đối tượng của `subclass1` và `subclass2`.

- Khi gọi `a.Print()`, chương trình sẽ ưu tiên phương thức được ghi đè trong lớp con, thay vì phương thức của lớp cha.

- Quyết định phương thức nào được gọi chỉ xảy ra trong lúc chạy chương trình → đây là đa hình lúc chạy.

# Ưu điểm
- Tăng khả năng tái sử dụng mã nguồn: Cho phép các đối tượng của nhiều lớp khác nhau được xử lý như đối tượng của một lớp chung, giúp tiết kiệm công sức lập trình.

- Cải thiện tính dễ đọc và bảo trì mã nguồn: Giảm số lượng mã cần viết và duy trì, làm cho chương trình dễ hiểu hơn.

- Hỗ trợ liên kết động (Dynamic Binding): Giúp chọn đúng phương thức để gọi tại thời gian chạy, dựa vào kiểu thực tế của đối tượng.

- Cho phép xử lý đối tượng như một kiểu duy nhất: Giúp viết mã chung (generic code) để xử lý nhiều loại đối tượng mà không cần quan tâm đến lớp cụ thể của chúng.

# Nhược điểm
- Có thể gây khó hiểu: Nếu chương trình quá phức tạp, có nhiều lớp và phương thức được ghi đè, việc theo dõi hành vi của một đối tượng có thể trở nên khó khăn.

- Ảnh hưởng đến hiệu suất: Do Java cần xác định phương thức phù hợp tại thời gian chạy, điều này có thể yêu cầu thêm tính toán, làm giảm hiệu suất so với việc gọi phương thức tĩnh.