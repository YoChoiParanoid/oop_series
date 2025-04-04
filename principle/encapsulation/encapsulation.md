# Tính đóng gói (Encapsulation)
### Khái niệm
- Đóng gói là một nguyên tắc quan trọng của lập trình hướng đối tượng (OOP)

- Được định nghĩa là việc gói dữ liệu dưới một đơn vị (kết hợp dữ liệu (biến) và phương thức (hàm) trong một lớp)

- Ẩn đi các chi tiết triển khai nội bộ, là một lá chắn bảo vệ dữ liệu, ngăn dữ liệu bị truy cập bởi mã bên ngoài.

- Chỉ cung cấp giao diện công khai để tương tác, có nghĩa là chỉ có thể truy cập thông qua các phương thức thành viên public của chính lớp đó.

### Ví dụ:

```java
// Java program demonstrating Encapsulation
class Programmer {
    private String name;

    // Getter and Setter for name
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
}

public class Geeks {
    public static void main(String[] args) {
        Programmer p = new Programmer();
        p.setName("Geek"); 
        System.out.println("Name=> " + p.getName());
    }
}
```

- Lớp Programmer ẩn thuộc tính name bằng cách khai báo nó là private.

- Việc truy cập và thay đổi name chỉ có thể thực hiện thông qua các phương thức getName() và setName().

- Điều này giúp bảo vệ dữ liệu và kiểm soát cách thức thay đổi giá trị của thuộc tính name.

# Triển khai đóng gói trong Java
### Tổng quan
- Khai báo các biến thành `private` để hạn chế truy cập trực tiếp từ bên ngoài.

- Cung cấp các phương thức getter/setter để lấy/thay đổi giá trị biến.

- Cơ chế này giúp bảo vệ dữ liệu, đảm bảo tính toàn vẹn và dễ kiểm soát dữ liệu hơn.

### Ví dụ
#### Đóng gói thông tin cá nhân

```java
class Person {
    // Encapsulating the name and age
    // only approachable and used using
    // methods defined
    private String name;
    private int age;

    public String getName() { return name; }

    public void setName(String name) { this.name = name; }

    public int getAge() { return age; }

    public void setAge(int age) { this.age = age; }
}

// Driver Class
public class Geeks {
    // main function
    public static void main(String[] args)
    {
        // person object created
        Person p = new Person();
        p.setName("John");
        p.setAge(30);
        // Using methods to get the values from the
        // variables
        System.out.println("Name: " + p.getName());
        System.out.println("Age: " + p.getAge());
    }
}
```

- `name` và `age` được khai báo `private` để không thể truy cập trực tiếp từ bên ngoài.

- Các phương thức `getName()`, `setName()`, `getAge()`, `setAge()` được sử dụng để truy xuất và thay đổi giá trị.

#### Ẩn thông tin bên trong lớp

```java
class Area {
    private int length;
    private int breadth;

    Area(int length, int breadth) {
        this.length = length;
        this.breadth = breadth;
    }

    public void getArea() {
        int area = length * breadth;
        System.out.println("Area: " + area);
    }
}

public class Geeks {
    public static void main(String[] args) {
        Area rect = new Area(2, 16);
        rect.getArea();
    }
}
```

- Các thuộc tính `length` và `breadth` được đóng gói bên trong lớp Area.

- Chỉ có thể truy cập thông qua phương thức `getArea()`.

#### Quản lý thông tin sinh viên
```java
class Encapsulate {
    private String geekName;
    private int geekRoll;
    private int geekAge;

    public int getAge() { return geekAge; }
    public String getName() { return geekName; }
    public int getRoll() { return geekRoll; }

    public void setAge(int newAge) { geekAge = newAge; }
    public void setName(String newName) { geekName = newName; }
    public void setRoll(int newRoll) { geekRoll = newRoll; }
}

public class TestEncapsulation {
    public static void main(String[] args) {
        Encapsulate o = new Encapsulate();

        o.setName("Harsh");
        o.setAge(19);
        o.setRoll(51);

        System.out.println("Geek's name: " + o.getName());
        System.out.println("Geek's age: " + o.getAge());
        System.out.println("Geek's roll: " + o.getRoll());
    }
}
```

- Các thuộc tính `geekName`, `geekAge`, `geekRoll` được đóng gói bằng `private`.

- Người dùng chỉ có thể truy cập thông qua các phương thức `getter` và `setter`.

# Ưu điểm
- Bảo vệ dữ liệu: Người dùng không thể truy cập trực tiếp các thuộc tính của lớp, giúp bảo vệ dữ liệu khỏi bị thay đổi ngoài ý muốn.

- Toàn vẹn dữ liệu: Các setter có thể kiểm soát dữ liệu đầu vào để tránh lỗi hoặc giá trị không hợp lệ.

- Tái sử dụng mã nguồn: Dễ dàng bảo trì và tái sử dụng vì không bị ràng buộc với chi tiết triển khai cụ thể.

- Kiểm thử dễ dàng: Đóng gói giúp viết các bài kiểm thử đơn vị một cách hiệu quả.

# Nhược điểm
- Tăng độ phức tạp: Cần viết nhiều phương thức getter và setter cho mỗi biến, làm tăng số lượng dòng mã.

- Giảm tính linh hoạt: Không thể thay đổi trực tiếp giá trị biến từ bên ngoài.