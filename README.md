Hey devs! 👋 If you’ve ever dipped your toes into TypeScript, you’ve probably come across things like `interface`, `type`, and mysterious keywords like `keyof`. And if you’re preparing for a dev job interview, these topics almost *always* pop up.

Today, I’ll break down two important concepts in a simple, human-friendly way:

1. The real differences between `interface` and `type`
2. What on earth does `keyof` do — and why should you care?

Let’s get started! 🚀

---

## 🥊 Interface vs Type — What’s the Difference?

You’ve likely seen both `interface` and `type` used to describe the shape of an object. They can seem identical at first glance, but they do have key differences — like cousins with different talents.

### 😎 What They Both Can Do:
- Describe object shapes
- Support extension/inheritance
- Help with code readability and safety

### ⚠️ But Here’s How They Differ:

| Feature | `interface` | `type` |
|--------|-------------|--------|
| **Extending** | Can extend other interfaces (or multiple) | Can extend using `&` (intersection) |
| **Merging** | ✅ Yes, interfaces with the same name merge | ❌ Nope |
| **Unions & Intersections** | ❌ Not directly | ✅ Yes |
| **Tuples, primitives, etc.** | ❌ Not allowed | ✅ Supported |

### 🧪 Real-Life Example:

```ts
interface User {
  name: string;
  age: number;
}

// You can merge!
interface User {
  email: string;
}

type Admin = {
  name: string;
  role: string;
};

// You can combine types like a recipe!
type UserOrAdmin = User | Admin;
````

📝 **Quick Tip:** Use `interface` for defining objects, especially in OOP-style code. Use `type` when you need flexibility, like unions or working with primitives.

---

## 🔑 `keyof` in TypeScript — Tiny Keyword, Big Power

Have you ever wanted to get the **keys of an object type** as a union? `keyof` is your friend!

Imagine you have a `Person` type, and you want to restrict access to only its existing keys. Here’s how:

### 🎯 Simple Example:

```ts
type Person = {
  name: string;
  age: number;
  isStudent: boolean;
};

type PersonKeys = keyof Person;
// 'name' | 'age' | 'isStudent'
```

Cool, right? But it gets better when used in functions.

### 🔧 Practical Use Case:

```ts
function getValue<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const person = { name: "Ruhit", age: 22, isStudent: true };

const name = getValue(person, "name"); // ✅ type is string
const age = getValue(person, "age");   // ✅ type is number
```

### ✅ Why It’s Useful:

* You avoid hardcoding property names
* Your code stays **type-safe**
* It's a must-know trick for building generic utilities or reusable components

---

## 🧠 Final Thoughts

TypeScript can feel intimidating, but once you break it down, it’s actually empowering. Whether it’s choosing between `type` and `interface`, or mastering keywords like `keyof`, these tools help you write smarter, safer code.

If this helped you, feel free to ⭐ my [Github](https://github.com/IftekarRahmanRuhit) or say hi on [LinkedIn](https://www.linkedin.com/in/iftekar-rahman-ruhit/)!

Happy coding! 💻✨

---

**Written by Iftekar Rahman Ruhit – MERN Stack Developer & TypeScript Enthusiast**