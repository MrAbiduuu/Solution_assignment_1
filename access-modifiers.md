# Access Modifiers in TypeScript OOP

## Introduction

Object-Oriented Programming (OOP) is an important concept in TypeScript. It allows us to organize code using classes and objects. While working with classes, sometimes we need to control which properties and methods can be accessed from outside or inside a class. This is where Access Modifiers become useful.

TypeScript provides four commonly used modifiers: `public`, `private`, `protected`, and `readonly`. Each of them has a different purpose.

## 1. Understanding Public

The `public` modifier allows properties and methods to be accessed from anywhere in the program. It can be accessed inside the class, outside the class, and even from child classes.

It is also the default access modifier in TypeScript, so we don't always need to write it.

```typescript
class Student {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }
}

const student = new Student("Abid");
console.log(student.name);
```

Here, we can access the `name` property directly using the object.

## 2. Understanding Private

The `private` modifier is used when we want to restrict access to a particular property or method. It can only be accessed inside the class where it is declared.

For example, salary information should not always be directly accessible from outside a class.

```typescript
class Employee {
  private salary: number;

  constructor(salary: number) {
    this.salary = salary;
  }

  getSalary(): number {
    return this.salary;
  }
}
```

In this example, we cannot access `salary` directly from an Employee object. However, we can get its value through the public `getSalary()` method.

## 3. Understanding Protected

The `protected` modifier is quite similar to `private`, but it has one important difference. A protected property can also be accessed inside child classes through inheritance.

```typescript
class Employee {
  protected department: string;

  constructor(department: string) {
    this.department = department;
  }
}

class Manager extends Employee {
  showDepartment(): string {
    return this.department;
  }
}
```

Here, `Manager` extends `Employee`, so it can access the protected `department` property. However, we cannot access that property directly from outside the class.

## 4. Understanding Readonly

The `readonly` modifier is used when we want a property to be assigned only once during initialization or inside the constructor.

After that, we cannot assign a new value to it. It is useful for information that should remain unchanged, such as an employee ID.

```typescript
class User {
  readonly userId: number;

  constructor(userId: number) {
    this.userId = userId;
  }
}
```

Here, the `userId` can be initialized in the constructor, but trying to change it later will produce a TypeScript error.

## 5. Combining Access Modifiers in One Class

We can also use different access modifiers together in a single class. This helps us control access to different types of information according to their purpose.

```typescript
class Employee {
  public name: string;
  private salary: number;
  protected department: string;
  readonly employeeId: number;

  constructor(
    name: string,
    salary: number,
    department: string,
    employeeId: number
  ) {
    this.name = name;
    this.salary = salary;
    this.department = department;
    this.employeeId = employeeId;
  }

  public getSalary(): number {
    return this.salary;
  }
}

class Manager extends Employee {
  showDepartment(): string {
    return this.department;
  }
}
```

In this example, each modifier controls access in a different way. The `name` property is public, `salary` is private, `department` is protected, and `employeeId` is readonly.

## 6. Why Are Access Modifiers Important?

Access modifiers help us write more organized and maintainable code. They prevent unnecessary access to internal class data and make it easier to manage larger applications.

For example, in a banking application, we should not allow users to directly change their account balance. Instead, we can provide specific methods for depositing or withdrawing money.

This approach helps maintain better control over how data is modified.

## Conclusion

Access Modifiers are an important part of TypeScript OOP because they provide control over class properties and methods. Each modifier has its own purpose depending on the situation. By using `public`, `private`, `protected`, and `readonly` correctly, we can create better structured, reusable, and maintainable applications. Learning these concepts also makes it easier to understand inheritance and encapsulation in Object-Oriented Programming.