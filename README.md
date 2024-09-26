650710983 ณัฐพล สุพรรณมี
#### I. ***การเขียนโปรแกรมเปรียบเทียบในภาษา Java, C++, Python***
#### โค้ด Java
```java
class Animal {
    Animal() {
        System.out.println("create animal");
    }

    void sound() {
        System.out.println("animal makes a sound");
    }

    protected void finalize() {
        System.out.println("delete animal");
    }
}

class Dog extends Animal {
    Dog() {
        System.out.println("dog");
    }

    @Override
    void sound() {
        System.out.println("dog barks");
    }

    protected void finalize() {
        System.out.println("delete dog");
    }
}

class Cat extends Animal {
    Cat() {
        System.out.println("cat");
    }

    @Override
    void sound() {
        System.out.println("cat meows");
    }

    protected void finalize() {
        System.out.println("delete cat");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Animal();
        Dog d = new Dog();
        Cat c = new Cat();
        
        a.sound();
        d.sound();
        c.sound();
    }
}

```
#### โค้ด C++
```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    Animal() {
        cout << "create animal" << endl;
    }

    virtual void sound() {
        cout << "animal makes a sound" << endl;
    }

    virtual ~Animal() {
        cout << "delete animal" << endl;
    }
};

class Dog : public Animal {
public:
    Dog() {
        cout << "dog" << endl;
    }

    void sound() override {
        cout << "dog barks" << endl;
    }

    ~Dog() {
        cout << "delete dog" << endl;
    }
};

class Cat : public Animal {
public:
    Cat() {
        cout << "cat" << endl;
    }

    void sound() override {
        cout << "cat meows" << endl;
    }

    ~Cat() {
        cout << "delete cat" << endl;
    }
};

int main() {
    Animal *a = new Animal();
    Animal *d = new Dog();
    Animal *c = new Cat();
    
    a->sound();
    d->sound();
    c->sound();
    
    delete a;
    delete d;
    delete c;
    
    return 0;
}

```
#### โค้ด Python
```python
class Animal:
    def __init__(self):
        print("create animal")
    
    def sound(self):
        print("animal makes a sound")
    
    def __del__(self):
        print("delete animal")

class Dog(Animal):
    def __init__(self):
        print("dog")
    
    def sound(self):
        print("dog barks")
    
    def __del__(self):
        print("delete dog")

class Cat(Animal):
    def __init__(self):
        print("cat")
    
    def sound(self):
        print("cat meows")
    
    def __del__(self):
        print("delete cat")

a = Animal()
d = Dog()
c = Cat()

a.sound()
d.sound()
c.sound()

```
#### ผลรันโค้ดของ Java,C++,Python
#### Java
```java
create animal
dog
cat
animal makes a sound
dog barks
cat meows
```
#### C++
```cpp
create animal
dog
cat
animal makes a sound
dog barks
cat meows
delete animal
delete dog
delete cat
```
#### Python
```python
create animal
dog
cat
animal makes a sound
dog barks
cat meows
delete animal
delete dog
delete cat
```

#### II. ***อธิบายแนวคิด OOP***
### คลาส (Class) 
  คลาสคือแม่แบบสำหรับสร้างออบเจ็กต์ ในตัวอย่างนี้ Animal, Dog, และ Cat เป็นคลาสซึ่งรวมข้อมูลและเมธอดต่าง ๆ ไว้
### ออบเจ็กต์ (Object) หรืออินสแตนซ์ (Instance)
  เป็นออบเจ็กต์ที่ถูกสร้างขึ้นจากคลาส เช่น a, d, และ c เป็นออบเจ็กต์ที่สร้างจากคลาส Animal, Dog, และ Cat
### คลาสย่อย (Subclass) หรือ Derived Class
  เป็นคลาสที่สืบทอดคุณสมบัติจากคลาสอื่น เช่น Dog และ Cat สืบทอดมาจาก Animal
### ข้อความ (Message)
  การสื่อสารกับออบเจ็กต์ผ่านการเรียกเมธอด เช่นการเรียก a.sound(), d.sound(), และ c.sound() คือการส่งข้อความไปยังออบเจ็กต์
### การสืบทอด (Inheritance)
  ความสามารถในการสืบทอดคุณสมบัติจากคลาสแม่ เช่น Dog และ Cat สืบทอดเมธอด sound จาก Animal
### พอลิมอร์ฟิซึม (Polymorphism)
  ความสามารถในการเรียกเมธอดเดียวกันในออบเจ็กต์ต่าง ๆ แต่ให้ผลลัพธ์ที่แตกต่างกัน เช่นการเรียก sound() ใน Animal, Dog, และ Cat ทำให้ได้ผลลัพธ์ต่างกันเพราะการ override เมธอด

#### III. ***Abstract Class คืออะไร***
#### Abstract class
  คือคลาสที่ไม่สามารถสร้างอินสแตนซ์ได้โดยตรงและอาจมีเมธอดที่เป็นนามธรรม (abstract method) ซึ่งต้องถูกนำไปใช้งานในคลาสย่อย ในตัวอย่างนี้ไม่มีคลาสใดที่เป็น abstract class แต่หากต้องการให้คลาส Animal เป็น abstract class ใน Java สามารถทำได้ดังนี้:

ตัวอย่าง Abstract Class ใน Java
```java
abstract class Animal {
    Animal() {
        System.out.println("create animal");
    }

    abstract void sound();  // เมธอดนามธรรม

    protected void finalize() {
        System.out.println("delete animal");
    }
}

```
โค้ดด้านบนเป็นการสร้าง abstract class Animal โดยเมธอด sound() เป็นเมธอดนามธรรม ซึ่งหมายความว่าคลาสที่สืบทอดจาก Animal ต้อง override เมธอดนี้ เช่น Dog และ Cat
