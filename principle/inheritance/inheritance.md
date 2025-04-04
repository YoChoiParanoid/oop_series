# Kế thừa (Inheritance)
- Là một tính năng quan trọng trong Lập trình Hướng đối tượng (OOP).

- Nó cho phép một lớp con (`subclass`) kế thừa thuộc tính và phương thức từ lớp cha (`superclass`).

- Điều này giúp tái sử dụng mã nguồn, giảm dư thừa, và tăng tính mở rộng cho chương trình.

- Từ khóa `extends` được sử dụng để thực hiện kế thừa trong Java.

# Lợi ích của kế thừa
- Tái sử dụng mã nguồn (Code Reusability): Lớp con có thể dùng lại phương thức và thuộc tính của lớp cha mà không cần viết lại.

- Hỗ trợ ghi đè phương thức (Method Overriding): Giúp đạt được tính đa hình (polymorphism) khi lớp con có thể thay đổi cách thực thi của phương thức lớp cha.

- Tổ chức mã nguồn khoa học: Giúp tổ chức các lớp theo cấu trúc rõ ràng, dễ đọc và bảo trì.

# Các thuật ngữ quan trọng
-  `Superclass` (Lớp cha): Lớp có thể được kế thừa.

-  `Subclass` (Lớp con): Lớp kế thừa từ lớp cha, có thể mở rộng hoặc ghi đè các phương thức của lớp cha.

-  `extends` keyword: Dùng để khai báo kế thừa giữa hai lớp.

-  Method `Overriding`: Lớp con có thể cung cấp cách triển khai mới cho phương thức đã có trong lớp cha.

# Cách sử dụng kế thừa trong Java
### Kế thừa cơ bản
```java
// Lớp cha
class Employee {
    int salary = 60000;
}

// Lớp con kế thừa từ Employee
class Engineer extends Employee {
    int benefits = 10000;
}

// Lớp chạy chương trình
public class Main {
    public static void main(String args[]) {
        Engineer E1 = new Engineer();
        System.out.println("Lương: " + E1.salary);
        System.out.println("Phúc lợi: " + E1.benefits);
    }
}
```

### Ghi đè phương thức
```java
// Lớp cha
class Parent {
    void showMessage() {
        System.out.println("Đây là phương thức của lớp cha");
    }
}

// Lớp con ghi đè phương thức của lớp cha
class Child extends Parent {
    @Override
    void showMessage() {
        System.out.println("Đây là phương thức của lớp con");
    }
}

// Lớp chạy chương trình
public class Main {
    public static void main(String[] args) {
        Parent obj1 = new Parent();
        obj1.showMessage();  // Gọi phương thức lớp cha

        Child obj2 = new Child();
        obj2.showMessage();  // Gọi phương thức lớp con (ghi đè)
    }
}
```

### Kế thừa với `super` keyword
```java
// Lớp cha
class Animal {
    String name = "Động vật";

    void makeSound() {
        System.out.println("Âm thanh của động vật");
    }
}

// Lớp con kế thừa Animal
class Dog extends Animal {
    String name = "Chó";

    void displayNames() {
        System.out.println("Tên lớp con: " + name);  // Chó
        System.out.println("Tên lớp cha: " + super.name);  // Động vật
    }

    @Override
    void makeSound() {
        super.makeSound();  // Gọi phương thức lớp cha
        System.out.println("Gâu gâu!");
    }
}

// Lớp chạy chương trình
public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.displayNames();
        myDog.makeSound();
    }
}
```

- super.name → Lấy giá trị từ lớp cha.

- super.makeSound() → Gọi phương thức của lớp cha trước khi thực thi phương thức lớp con.

# Các loại kế thừa được hỗ trợ trong Java
## Kế thừa đơn (Single Inheritance)
- Trong kế thừa đơn, một lớp con (subclass) chỉ kế thừa từ một lớp cha (superclass) duy nhất.

- Lớp con sẽ thừa hưởng các thuộc tính và phương thức của lớp cha, có thể mở rộng hoặc thay đổi chúng nếu cần.

```java
// Lớp cha (Superclass)
class One {
    public void print_geek() {
        System.out.println("Geeks");
    }
}

// Lớp con (Subclass) kế thừa từ lớp cha
class Two extends One {
    public void print_for() {
        System.out.println("for");
    }
}

// Lớp chạy chương trình
public class Main {
    public static void main(String[] args) {
        Two g = new Two();
        g.print_geek(); // Kế thừa từ lớp One
        g.print_for();  // Phương thức riêng của lớp Two
        g.print_geek();
    }
}
```

## Kế thừa đa cấp (Multilevel Inheritance)
- Trong kế thừa đa cấp, một lớp con có thể kế thừa từ một lớp khác, và lớp đó lại kế thừa từ một lớp khác nữa.

- Như vậy, lớp con cuối cùng sẽ kế thừa tất cả các phương thức và thuộc tính của các lớp cha trước đó.

```java
// Lớp cha gốc
class One {
    public void print_geek() {
        System.out.println("Geeks");
    }
}

// Lớp trung gian kế thừa từ One
class Two extends One {
    public void print_for() {
        System.out.println("for");
    }
}

// Lớp con cuối cùng kế thừa từ Two
class Three extends Two {
    public void print_lastgeek() {
        System.out.println("Geeks");
    }
}

// Lớp chạy chương trình
public class Main {
    public static void main(String[] args) {
        Three g = new Three();
        g.print_geek();     // Kế thừa từ One
        g.print_for();      // Kế thừa từ Two
        g.print_lastgeek(); // Phương thức riêng của Three
    }
}
```

## Kế thừa phân cấp (Hierarchical Inheritance)
- Trong kế thừa phân cấp, một lớp cha có nhiều lớp con kế thừa từ nó.

- Các lớp con có thể sử dụng chung các phương thức từ lớp cha nhưng không liên quan trực tiếp đến nhau.

```java
class A {
    public void print_A() {
        System.out.println("Class A");
    }
}

// Các lớp con kế thừa từ A
class B extends A {
    public void print_B() {
        System.out.println("Class B");
    }
}

class C extends A {
    public void print_C() {
        System.out.println("Class C");
    }
}

class D extends A {
    public void print_D() {
        System.out.println("Class D");
    }
}

// Lớp chạy chương trình
public class Test {
    public static void main(String[] args) {
        B obj_B = new B();
        obj_B.print_A();
        obj_B.print_B();

        C obj_C = new C();
        obj_C.print_A();
        obj_C.print_C();

        D obj_D = new D();
        obj_D.print_A();
        obj_D.print_D();
    }
}
```

## Đa kế thừa (Multiple Inheritance - Qua Interface)
- Java không hỗ trợ kế thừa đa với class nhưng có thể thực hiện được thông qua interface.

- Một class có thể implements nhiều interface cùng lúc để kế thừa nhiều tính năng.

```java
interface One {
    void print_geek();
}

interface Two {
    void print_for();
}

// Interface kế thừa từ hai interface trên
interface Three extends One, Two {
    void print_geek();
}

// Lớp triển khai (implements) cả hai interface
class Child implements Three {
    public void print_geek() {
        System.out.println("Geeks");
    }

    public void print_for() {
        System.out.println("for");
    }
}

// Lớp chạy chương trình
public class Main {
    public static void main(String[] args) {
        Child c = new Child();
        c.print_geek();
        c.print_for();
        c.print_geek();
    }
}
```

## Kế thừa lai (Hybid Inheritance - Qua interface)
- Kế thừa lai là sự kết hợp của hai hoặc nhiều kiểu kế thừa đã nói trên.

- Vì Java không hỗ trợ đa kế thừa bằng class, nên hybrid inheritance chủ yếu được thực hiện bằng cách kết hợp interface.

## Quan hệ is - a trong Java
- `IS-A` là cách mô tả một đối tượng thuộc về một loại đối tượng khác.

- Nó được thực hiện thông qua từ khóa `extends` và `implements`.

```java
class SolarSystem {}

class Earth extends SolarSystem {}

class Mars extends SolarSystem {}

public class Moon extends Earth {
    public static void main(String args[]) {
        SolarSystem s = new SolarSystem();
        Earth e = new Earth();
        Mars m = new Mars();

        System.out.println(s instanceof SolarSystem); // true
        System.out.println(e instanceof Earth);       // true
        System.out.println(m instanceof SolarSystem); // true
    }
}
```