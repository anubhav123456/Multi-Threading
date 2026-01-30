
---

# 🧵 Multithreading in Java — Thread Creation

## 📌 Topics Covered

1. Ways to create a thread
2. Why two ways exist
3. Runnable approach (recommended)
4. Extending Thread class
5. Flow of `start()` → `run()`

---

# ❓ Why Java Gives Two Ways to Create a Thread?

Java has a rule:

| Concept               | Java Rule                                     |
| --------------------- | --------------------------------------------- |
| **Class inheritance** | A class can extend **only one** parent class  |
| **Interfaces**        | A class can implement **multiple interfaces** |

So:

* If your class already extends another class → you **cannot** extend `Thread`
* But you can still make it multithreaded using **Runnable interface**

👉 That’s why Java provides:

1. **Implements Runnable**
2. **Extends Thread**

---

# ✅ Way 1: Creating Thread using **Runnable Interface** (Industry Preferred)

## 🔹 Step 1: Create a class that implements `Runnable`

```java
public class MultithreadingLearning implements Runnable {

    @Override
    public void run() {
        System.out.println("Code executed by thread: " + Thread.currentThread().getName());
    }
}
```

👉 This class is **NOT a thread**, just a task.

---

## 🔹 Step 2: Create Thread object and pass Runnable

```java
public class Main {
    public static void main(String args[]) {

        System.out.println("Going inside main method: " + Thread.currentThread().getName());

        MultithreadingLearning runnableObj = new MultithreadingLearning();

        Thread thread = new Thread(runnableObj); // Thread created
        thread.start(); // Thread started

        System.out.println("Finish main method: " + Thread.currentThread().getName());
    }
}
```

---

## ⚙️ What Happens Internally?

When you call:

```java
thread.start();
```

Flow is:

```
start() → JVM creates new thread → calls run()
Thread.run() checks:
    if (target != null)
        target.run();
```

👉 `target` = the `Runnable` object you passed
👉 So finally this runs:

```java
runnableObj.run();
```

---

## 🖨️ Possible Output

```
Going inside main method: main
Finish main method: main
Code executed by thread: Thread-0
```

⚠️ Order may change because threads run independently.

---

## ⭐ Why Runnable is Preferred?

| Runnable                                  | Extending Thread              |
| ----------------------------------------- | ----------------------------- |
| Class can extend another class            | Cannot extend any other class |
| Better design (task separate from thread) | Tight coupling                |
| More flexible                             | Less flexible                 |
| Industry standard                         | Rare in real projects         |

---

# ✅ Way 2: Creating Thread by **Extending Thread Class**

## 🔹 Step 1: Extend Thread

```java
public class MultithreadingLearning extends Thread {

    @Override
    public void run() {
        System.out.println("Code executed by thread: " + Thread.currentThread().getName());
    }
}
```

👉 This class **IS a thread**

---

## 🔹 Step 2: Create object and start

```java
public class Main {
    public static void main(String args[]) {

        System.out.println("Going inside main method: " + Thread.currentThread().getName());

        MultithreadingLearning myThread = new MultithreadingLearning();
        myThread.start(); // No need to create Thread object separately

        System.out.println("Finish main method: " + Thread.currentThread().getName());
    }
}
```

---

## 🖨️ Possible Output

```
Going inside main method: main
Finish main method: main
Code executed by thread: Thread-0
```

---

## ⚠️ Important Note

If you **don’t override `run()`**, Thread’s default `run()` does **nothing**.

So always override.

---

# 🔁 Key Difference Summary

| Feature                   | Runnable    | Thread |
| ------------------------- | ----------- | ------ |
| Is it a thread?           | ❌ No        | ✅ Yes  |
| Can extend another class? | ✅ Yes       | ❌ No   |
| Flexibility               | High        | Low    |
| Industry use              | ⭐ Most used | Rare   |

---

# 🔥 Interview Question

**Q: Why do we call `start()` and not `run()` directly?**

| start()                | run()                   |
| ---------------------- | ----------------------- |
| Creates new thread     | Runs like normal method |
| Multithreading happens | No multithreading       |

---

# 🧠 Final Concept Flow

```
Runnable Object → Passed to Thread → start() called
→ JVM creates new thread → run() invoked → task executes
```

---
