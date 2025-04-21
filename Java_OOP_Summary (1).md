📘 **جزوه شی‌گرایی در جاوا**

---

### 🔹 کلاس و شی (Class & Object)
کلاس‌ها در جاوا قالب‌هایی برای ساخت اشیاء هستند. آن‌ها شامل ویژگی‌ها (متغیرها) و رفتارها (متدها) می‌شوند. برای استفاده از کلاس، باید نمونه‌ای (object) از آن ایجاد کنیم. هر شیء ساخته شده از یک کلاس، حافظه مخصوص به خود برای ویژگی‌ها خواهد داشت.

```java
class Car {
    String brand = "Toyota";
    int speed = 100;

    void drive() {
        System.out.println("Driving " + brand + " at " + speed + " km/h");
    }
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car(); // ساخت شیء
        myCar.drive();         // فراخوانی متد
    }
}
```

---

### 🔹 سازنده (Constructor)
سازنده متدی است که هم‌نام کلاس می‌باشد و در هنگام ایجاد شیء، به‌صورت خودکار اجرا می‌شود. می‌توان سازنده‌های مختلفی تعریف کرد (Overloading سازنده). هدف آن مقداردهی اولیه به ویژگی‌های شیء است.

```java
class Student {
    String name;
    int age;

    // سازنده با پارامتر
    Student(String n, int a) {
        name = n;
        age = a;
    }

    void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("Ali", 20);
        s1.display();
    }
}
```

---

### 🔹 اینکپسولاسیون (Encapsulation)
در این مفهوم، اطلاعات داخلی یک کلاس پنهان می‌شود و فقط از طریق متدهای خاص (getter/setter) به آن‌ها دسترسی داریم. این باعث امنیت بیشتر، جلوگیری از دستکاری مستقیم داده‌ها و کنترل بهتر روی منطق می‌شود.

```java
class BankAccount {
    private double balance;

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public double getBalance() {
        return balance;
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount();
        account.deposit(1000);
        System.out.println("Balance: " + account.getBalance());
    }
}
```

---

### 🔹 وراثت (Inheritance)
در وراثت، یک کلاس می‌تواند ویژگی‌ها و رفتارهای کلاس دیگری را به ارث ببرد. این ویژگی باعث می‌شود کد تکراری کمتر بنویسیم و بتوانیم قابلیت‌ها را گسترش دهیم.

```java
class Animal {
    void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog is barking");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat();  // از کلاس والد
        d.bark(); // از کلاس خودش
    }
}
```

---

### 🔹 چندریختی (Polymorphism)
چندریختی یعنی توانایی استفاده از یک متد یا شیء به اشکال مختلف. در جاوا دو نوع چندریختی داریم:

#### ✅ Overriding
در کلاس فرزند، متدی با همان امضای کلاس والد را بازنویسی می‌کنیم.

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Cat extends Animal {
    void sound() {
        System.out.println("Meow");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Cat();
        a.sound(); // اجرای متد Cat به‌جای Animal
    }
}
```

#### ✅ Overloading
در یک کلاس، متدهایی با نام یکسان اما پارامترهای متفاوت تعریف می‌کنیم.

```java
class MathUtil {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

---

### 🔹 انتزاع (Abstraction)
انتزاع یعنی نمایش فقط ویژگی‌های اصلی و مخفی کردن جزئیات. در جاوا می‌توان انتزاع را با کلاس‌های abstract یا interface پیاده‌سازی کرد.

#### ✅ کلاس abstract
کلاسی که نمی‌توان از آن مستقیماً شیء ساخت و ممکن است شامل متدهای بدون پیاده‌سازی باشد.

```java
abstract class Shape {
    abstract void draw(); // متد انتزاعی
}

class Circle extends Shape {
    void draw() {
        System.out.println("Drawing Circle");
    }
}
```

#### ✅ Interface
interface نوعی قرارداد است که فقط شامل امضای متدهاست. کلاس‌هایی که آن را پیاده‌سازی می‌کنند، باید تمام متدها را پیاده‌سازی کنند.

```java
interface Drawable {
    void draw();
}

class Rectangle implements Drawable {
    public void draw() {
        System.out.println("Drawing Rectangle");
    }
}
```

---

### 💥 نمونه سوالات مفهومی و پیشرفته شی‌گرایی

**سوال ۱:** خروجی دقیق برنامه زیر را نوشته و دلیل منطقی آن را توضیح دهید. همچنین مشخص کنید کدام مفهوم شی‌گرایی استفاده شده است.
```java
class Animal {
    void sound() {
        System.out.println("Animal Sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Bark");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal obj = new Dog();
        obj.sound();
    }
}
```
**پاسخ:** از مفهوم polymorphism و dynamic method dispatch استفاده شده است. خروجی:
```
Bark
```

---

**سوال ۲:** برنامه‌ای بنویسید که از اینترفیس به‌درستی استفاده کند. کلاس‌هایی بنویسید که interface `Movable` را پیاده‌سازی کنند و از طریق یک متد مشترک `move()` در آن‌ها استفاده شود.

```java
interface Movable {
    void move();
}

class Car implements Movable {
    public void move() {
        System.out.println("Car is moving");
    }
}

class Human implements Movable {
    public void move() {
        System.out.println("Human is walking");
    }
}

public class Main {
    public static void main(String[] args) {
        Movable m1 = new Car();
        Movable m2 = new Human();
        m1.move();
        m2.move();
    }
}
```

---

**سوال ۳:** برنامه‌ای بنویسید که نشان دهد نمی‌توان متد `final` را override کرد. سپس توضیح دهید چرا چنین قابلیتی در زبان جاوا مفید است.

```java
class A {
    final void show() {
        System.out.println("Show from A");
    }
}

class B extends A {
    // void show() { System.out.println("Show from B"); } // خطا: Cannot override final method
}
```
**پاسخ:** متدهای final قابل override نیستند چون طراح کلاس خواسته رفتار آن متد در همه زیرکلاس‌ها ثابت بماند.

---

**سوال ۴:** از ترکیب مفاهیم وراثت، انتزاع و polymorphism برنامه‌ای بنویسید که کلاس abstract به نام `Employee` داشته باشد و دو کلاس `Manager` و `Clerk` آن را پیاده‌سازی کنند.

```java
abstract class Employee {
    String name;
    Employee(String name) {
        this.name = name;
    }
    abstract void work();
}

class Manager extends Employee {
    Manager(String name) {
        super(name);
    }
    void work() {
        System.out.println(name + " is managing the team");
    }
}

class Clerk extends Employee {
    Clerk(String name) {
        super(name);
    }
    void work() {
        System.out.println(name + " is doing clerical work");
    }
}

public class Test {
    public static void main(String[] args) {
        Employee e1 = new Manager("Ali");
        Employee e2 = new Clerk("Sara");
        e1.work();
        e2.work();
    }
}
```

---

**سوال ۵:** یک کلاس `Shape` طراحی کنید که شامل متدهای overloaded برای محاسبه مساحت دایره و مربع باشد. سپس با استفاده از چندریختی، آن‌ها را تست کنید.

```java
class Shape {
    double area(double radius) {
        return Math.PI * radius * radius;
    }

    double area(double length, double width) {
        return length * width;
    }
}

public class Main {
    public static void main(String[] args) {
        Shape s = new Shape();
        System.out.println("Area of circle: " + s.area(3));
        System.out.println("Area of rectangle: " + s.area(3, 4));
    }
}
```

---

