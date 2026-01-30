
---

# 🧠 Multithreading & Concurrency — Process vs Thread

## 1️⃣ First Understand: **Process vs Thread** (🔥 Very Important Interview Question)

---

## 🧩 What is a **Process**?

### 📖 Definition

> **Process = Instance of a program that is being executed**

### 💡 In simple words

When you **run a program**, OS creates a **process** to execute it.

### 🧪 Java Example Flow

```bash
javac Test.java   → Compilation (creates bytecode)
java Test         → Execution
```

👉 When you run:

```bash
java Test
```

➡ **JVM creates a NEW PROCESS**

---

### 🧠 Why Process is Needed?

Execution needs resources like:

* Memory (Heap, Stack)
* CPU time
* Files
* Network access

👉 **OS allocates these resources to each process**

---

### ⚙️ Key Properties of Process

| Feature        | Explanation                                          |
| -------------- | ---------------------------------------------------- |
| Independent    | Each process runs separately                         |
| Own Memory     | One process **cannot access** another process memory |
| Resource Owner | OS gives memory, CPU etc. to process                 |
| Heavyweight    | Process creation is costly                           |

---

### 🧱 Example

```
Process 1 → Heap Memory 1
Process 2 → Heap Memory 2
```

🚫 They do NOT share memory.

---

## 🧵 What is a **Thread**?

### 📖 Definition

> Thread = **Smallest sequence of instructions executed independently by CPU**

Also called: **Lightweight Process**

---

### 🧠 Relation

```
Process → Contains Threads
```

One process can have **multiple threads**.

---

### 💡 Simple Analogy

| Concept | Real-life Example         |
| ------- | ------------------------- |
| Process | Restaurant                |
| Thread  | Waiters inside restaurant |

Restaurant (process) has many waiters (threads) working simultaneously.

---

## 🚀 When a Process Starts

👉 **Every process starts with ONE thread**
That thread is called:

# ⭐ **Main Thread**

---

## 💻 Code Example (From Lecture)

```java
public class MultithreadingLearning {

    public static void main(String args[]){
        System.out.println("Thread Name: " + Thread.currentThread().getName());
    }
}
```

### ▶ Execution Steps

```bash
javac MultithreadingLearning.java
java MultithreadingLearning
```

### 🖨 Output

```
Thread Name: main
```

### 🔍 What Happened?

| Step | What Occurred                      |
| ---- | ---------------------------------- |
| 1    | JVM created a **process**          |
| 2    | Process created a **Main Thread**  |
| 3    | `main()` method ran on that thread |
| 4    | We printed thread name → **main**  |

---

## 🧵 Threads Inside a Process

```
Process
   ├── Main Thread
   ├── Thread-1
   ├── Thread-2
   └── Thread-3
```

You can create more threads from main thread to perform tasks **concurrently**.

---

## ⚖️ Process vs Thread (Interview Table)

| Feature        | Process                                 | Thread                                    |
| -------------- | --------------------------------------- | ----------------------------------------- |
| Meaning        | Program in execution                    | Unit of execution inside process          |
| Memory         | Separate memory                         | Shared memory of process                  |
| Creation Cost  | High                                    | Low                                       |
| Communication  | Hard (IPC)                              | Easy (shared memory)                      |
| Failure Impact | One process crash doesn't affect others | One thread crash may affect whole process |
| Managed By     | OS                                      | OS + JVM                                  |

---

## 🧠 Important Concept

✔ Process handles:

* Memory allocation
* Resource management
* Program execution environment

✔ Thread handles:

* Actual execution of instructions

---

## 🧩 Summary

| Term        | Meaning                            |
| ----------- | ---------------------------------- |
| Program     | `.java` file                       |
| Process     | When program starts running        |
| Thread      | Path of execution inside process   |
| Main Thread | First thread created automatically |

---

## 🎯 Interview Golden Lines

* “A process is an execution environment, while threads are execution units.”
* “Threads share memory, processes don’t.”
* “Every Java program starts with a main thread.”

---