# TypeScript-এ OOP-এর ৪টি পিলার: বড় প্রজেক্টের জটিলতা দূর করার সমাধান

বড় মাপের বা এন্টারপ্রাইজ লেভেলের প্রজেক্টগুলোতে যখন কোডের পরিধি বাড়তে থাকে, তখন লজিকগুলো জট পাকিয়ে যাওয়ার সম্ভাবনা তৈরি হয়। এই জটিলতা দূর করে কোডকে সুশৃঙ্খল ও মেইনটেইনেবল রাখতে সাহায্য করে **Object-Oriented Programming (OOP)**। টাইপস্ক্রিপ্টে OOP-এর ৪টি পিলার কীভাবে কাজ করে, তা বাস্তব উদাহরণসহ দেখে নেওয়া যাক।

---

## ১. Inheritance (উত্তরাধিকার)

ইনহেরিটেন্সের মাধ্যমে একটি নতুন ক্লাস অন্য একটি বিদ্যমান ক্লাসের সমস্ত প্রপার্টি ও মেথড নিজের মধ্যে নিয়ে নিতে পারে। এতে কোড রিইউজেবিলিটি বহুগুণ বেড়ে যায়।

### বাস্তব উদাহরণ:

```typescript
class Employee {
  constructor(public name: string, public salary: number) {}
}

class Developer extends Employee {
  constructor(name: string, salary: number, public language: string) {
    super(name, salary); 
  }
}
```
এখানে `Developer` ক্লাসটি অত্যন্ত সহজে `Employee` ক্লাসের বৈশিষ্ট্যগুলো নিজের মধ্যে নিয়ে নিয়েছে।

## ২. Polymorphism

Polymorphism শব্দের অর্থ "বহুরূপ"। এর মাধ্যমে ভিন্ন ভিন্ন ক্লাস একই নামের মেথড ব্যবহার করে ভিন্ন ভিন্ন আচরণ করতে পারে।

### উদাহরণ:

```typescript
class Animal {
  makeSound(): void {
    console.log("Some sound...");
  }
}

class Dog extends Animal {
  makeSound(): void {
    console.log("Gheu Gheu!"); 
  }
}

class Cat extends Animal {
  makeSound(): void {
    console.log("Meow Meow!"); 
  }
}
```

## ৩. Abstraction

অ্যাবস্ট্রাকশন হলো অপ্রয়োজনীয় বা পেছনের জটিল লজিক লুকিয়ে রেখে শুধুমাত্র প্রয়োজনীয় অংশ ব্যবহারকারীর সামনে উপস্থাপন করা। টাইপস্ক্রিপ্টে `abstract` ক্লাস বা `interface` ব্যবহার করে এটি করা হয়।

### উদাহরণ:

```typescript
abstract class PaymentGateway {
  abstract processPayment(amount: number): void; 
}

class BkashPayment extends PaymentGateway {
  processPayment(amount: number): void {
    console.log(`Processing ${amount} BDT via bKash.`);
  }
}
```

এখানে ইউজার বা ডেভেলপার শুধু জানবেন যে `processPayment` মেথডটি কল করতে হবে, পেছনের জটিল এপিআই ইন্টিগ্রেশন এখানে হাইড করা থাকে।

## ৪. Encapsulation

ক্লাসের প্রপার্টি এবং মেথডগুলোকে বাইরের সরাসরি অ্যাক্সেস থেকে সুরক্ষিত রাখাই হলো Encapsulation। টাইপস্ক্রিপ্টে `private, protected,` এবং `public` অ্যাক্সেস মডিফায়ার দিয়ে এটি নিয়ন্ত্রণ করা হয়।

### উদাহরণ:

```typescript
class BankAccount {
  private _balance: number = 0; 

  deposit(amount: number): void {
    if (amount > 0) this._balance += amount;
  }

  getBalance(): number {
    return this._balance; 
  }
}
```

### উপসংহার

টাইপস্ক্রিপ্টের শক্তিশালী টাইপ সিস্টেম এবং `OOP`-এর এই ৪টি পিলার একসাথে মিলে কোডকে করে তোলে অত্যন্ত সিকিউর, রিইউজেবল এবং সহজে বর্ধনশীল **(Scalable)**। বড় প্রজেক্টে ভালো আর্কিটেকচার গড়ে তোলার জন্য এই ৪টি নিয়মের কোনো বিকল্প নেই।