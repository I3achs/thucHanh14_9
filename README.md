# thucHanh14_9
### 1. Kế thừa (Inheritance)

**Khái niệm Kế thừa trong C#:**

Kế thừa là một cơ chế trong lập trình hướng đối tượng cho phép một lớp (class) kế thừa các thuộc tính và phương thức từ một lớp khác. Lớp được kế thừa gọi là lớp cơ sở (base class) và lớp kế thừa gọi là lớp con (derived class). Kế thừa giúp chúng ta tái sử dụng mã nguồn và tổ chức mã nguồn theo cấu trúc phân cấp, giảm thiểu sự lặp lại mã.

**Lợi ích của Kế thừa:**

- **Tái sử dụng mã nguồn:** Các thuộc tính và phương thức của lớp cơ sở có thể được sử dụng lại mà không cần viết lại mã.
- **Giảm thiểu trùng lặp:** Thay vì tạo lại cùng một mã ở nhiều nơi, ta có thể viết mã một lần trong lớp cơ sở và kế thừa chúng ở lớp con.
- **Dễ bảo trì và mở rộng:** Thay đổi trong lớp cơ sở sẽ được phản ánh trong tất cả các lớp kế thừa, giúp dễ dàng bảo trì và mở rộng hệ thống.

**Ví dụ minh họa:**

```csharp
// Lớp cơ sở (Base class)
public class Animal
{
    public string Name { get; set; }
    
    public void Eat()
    {
        Console.WriteLine(Name + " is eating.");
    }
}

// Lớp kế thừa (Derived class)
public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine(Name + " is barking.");
    }
}

// Sử dụng lớp
public class Program
{
    public static void Main()
    {
        Dog myDog = new Dog();
        myDog.Name = "Rex";
        myDog.Eat();  // Kế thừa từ lớp Animal
        myDog.Bark(); // Phương thức riêng của lớp Dog
    }
}
```

Trong ví dụ trên, lớp `Dog` kế thừa thuộc tính `Name` và phương thức `Eat` từ lớp `Animal`. Lớp `Dog` cũng có phương thức riêng `Bark`.

### 2. Đa hình (Polymorphism)

**Khái niệm Đa hình trong C#:**

Đa hình là khả năng của một đối tượng để có nhiều dạng. Trong lập trình hướng đối tượng, đa hình cho phép một phương thức hoặc một thuộc tính có nhiều hình thức hoặc cách thức hoạt động khác nhau. Đa hình giúp cải thiện tính linh hoạt và khả năng mở rộng của mã nguồn.

**Phân biệt giữa Đa hình tĩnh và Đa hình động:**

- **Đa hình tĩnh (Compile-time Polymorphism):** Xảy ra khi quyết định về việc phương thức nào sẽ được gọi được thực hiện tại thời điểm biên dịch. Cách phổ biến để đạt được đa hình tĩnh là thông qua nạp chồng phương thức (Method Overloading).

- **Đa hình động (Run-time Polymorphism):** Xảy ra khi quyết định về việc phương thức nào sẽ được gọi được thực hiện tại thời điểm chạy. Cách phổ biến để đạt được đa hình động là thông qua phương thức ghi đè (Method Overriding).

**Ví dụ minh họa về Đa hình:**

- **Phương thức nạp chồng (Method Overloading):**

```csharp
public class Printer
{
    public void Print(string message)
    {
        Console.WriteLine("Printing string: " + message);
    }

    public void Print(int number)
    {
        Console.WriteLine("Printing integer: " + number);
    }
}

// Sử dụng lớp
public class Program
{
    public static void Main()
    {
        Printer printer = new Printer();
        printer.Print("Hello, World!"); // Gọi Print(string)
        printer.Print(123);             // Gọi Print(int)
    }
}
```

- **Phương thức ghi đè (Method Overriding):**

```csharp
// Lớp cơ sở
public class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Animal makes a sound.");
    }
}

// Lớp kế thừa
public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Dog barks.");
    }
}

// Sử dụng lớp
public class Program
{
    public static void Main()
    {
        Animal myAnimal = new Dog(); // Đa hình động
        myAnimal.MakeSound();       // Gọi phương thức ghi đè
    }
}
```

Trong ví dụ về đa hình động, mặc dù `myAnimal` có kiểu là `Animal`, phương thức `MakeSound` thực tế gọi là của lớp `Dog` nhờ vào từ khóa `override`.

### 3. So sánh và Ứng dụng

**So sánh Kế thừa và Đa hình:**

- **Giống nhau:**
  - Cả hai đều là các khái niệm cơ bản trong lập trình hướng đối tượng và giúp tổ chức mã nguồn theo cấu trúc phân cấp.
  - Cả hai đều hỗ trợ tái sử dụng mã nguồn và giảm thiểu trùng lặp mã.

- **Khác nhau:**
  - **Kế thừa** chủ yếu tập trung vào việc chia sẻ thuộc tính và phương thức giữa các lớp. Lớp con kế thừa thuộc tính và phương thức từ lớp cha.
  - **Đa hình** tập trung vào việc cho phép các đối tượng khác nhau đáp ứng với cùng một phương thức theo cách khác nhau, tùy thuộc vào kiểu đối tượng thực tế.

**Ứng dụng thực tế:**

- **Kế thừa:**
  - **Lập trình hướng đối tượng:** Giúp tổ chức các lớp theo cấu trúc phân cấp, ví dụ như trong thiết kế các loại hình động vật, xe cộ, nhân viên trong công ty.
  - **Mở rộng và bảo trì hệ thống:** Dễ dàng thêm các lớp con mới mà không thay đổi mã của lớp cha.

- **Đa hình:**
  - **Giao diện người dùng:** Cho phép các thành phần giao diện như nút, hộp thoại thực hiện các hành động khác nhau mặc dù đều sử dụng cùng một giao diện.
  - **Hệ thống plugin:** Các plugin có thể cung cấp các triển khai khác nhau của cùng một phương thức, tạo sự linh hoạt trong cách hệ thống hoạt động.

**Code ví dụ tổng hợp:**

```csharp
// Lớp cơ sở
public class Shape
{
    public virtual void Draw()
    {
        Console.WriteLine("Drawing a shape.");
    }
}

// Lớp kế thừa
public class Circle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a circle.");
    }
}

// Lớp kế thừa
public class Rectangle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a rectangle.");
    }
}

// Sử dụng đa hình
public class Program
{
    public static void Main()
    {
        Shape shape1 = new Circle();    // Đa hình động
        Shape shape2 = new Rectangle(); // Đa hình động

        shape1.Draw(); // In ra "Drawing a circle."
        shape2.Draw(); // In ra "Drawing a rectangle."
    }
}
```

Trong ví dụ trên, lớp `Shape` cung cấp phương thức `Draw`, và các lớp `Circle` và `Rectangle` ghi đè phương thức này để cung cấp triển khai cụ thể. Khi phương thức `Draw` được gọi, hệ thống sẽ sử dụng triển khai của lớp thực tế của đối tượng.
