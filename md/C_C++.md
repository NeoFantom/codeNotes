# C memory allocation
```C 
int *array = malloc((sizeof(int) * len));
int *array = calloc(len, sizeof(int));
```

# C user-defined type

```C
#define ElementType int
typedef int ElementType;

struct Node {
    struct Node *next;
    int value;
};

typdef struct Node {
    struct Node *next;
    int value;
} Node;
```
# Class

## constructor &destructor

```C++
class Person {
   public:
    Person() {}
    ~Person() {}
};
```

Classes without constructor will be given a **default constructor without
arguments **.

### Call a destructor

If created by `new`:
```C++
Person person = new Person();
delete person;
```
If it is an automatic variable, then destructor is called when the variable's lifetime ends.

### Call a constructor

```C++ 
Dog dog("bao");  // Direct initialization
Dog dog = Dog("bao");    // Copy initialization
Dog dog(anotherDog);     // Copy initialization

std::string s{};          // Value initialization
std::string s("hello");   // Direct initialization
std::string s = "hello";  // Copy initialization

std::string s{'a', 'b', 'c'};  // List initialization
// Can be used when a class has no user-defined constructor

char a[3] = {'a', 'b'};  // List initialization
char &c = a[0];          // Reference initialization
```

### Explicit constructor

C++ consider all constructors as converting constructor unless specified with [explicit](https://en.cppreference.com/w/cpp/language/explicit).

```C++
class A {
    A(int) {}
};
class B {
    explicit B(int) {}
};
void main() {
    A a(3);       // OK
    A aa = A(9);  // OK
    B b(4);       // OK
    // B bb = B(5); // Wrong, B() is explicit
}
```

### Member initializer List

```C++
class A {
    int x;
    int y;
    A(int x) : x(x), y(3) {}
}
```

### New and delete

```C++
int *p = new int; 
int *p = new int(25);
int *p = new int[10];
Dog *dog = new Dog("Miki");
```

## Member

### Visibility
 ```C++
class A {
   private:
    int x;

   protected:
    int y;

   public:
    int z;
 }
 ```

### Static

Used just like Java. Irrelevant to `static` in C.

```C++
class A {
    static string name = "A";
    static void printName() { cout << "hello"; }
}
```

## Inheritance and abstract class

C++ has no abstract class but only abstract functions. A base class can be an abstract class (some functions **pure virtual**) or an interface (all functions **pure virtual**).

```C++
class Animal {
    // Pure virtual function, like abstract function in Java
    virtual void getSpecies() = 0;
    // Virtual function, i.e. overidable
    virtual void speak() { cout << "Hello"; }
    // Virtual function without definition, to be declared somewhere else
    virtual void walk();
    // Virtual function with empty body
    virtual void nothing() {}
};
```

When specifying a base class, it can be `public`, `protected` or `private`. The *public* members of the base class becomes *public*, *protected* or *private* respectively. We usually only use **public**.

```C++
class dog : public Animal {
    void getSpecies() { ... }
}
```

## Generics

```C++
template <typename T>
class leafNode {
    ...
};
```