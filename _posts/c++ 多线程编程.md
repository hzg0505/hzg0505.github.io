# c++ 多线程编程

（8.15）

### 1. 基本概念

- 进程与线程
- 串行与并行

### 2. 基本操作

- **join() 方法**： 当您创建一个线程并调用其 `join()` 方法时，主线程会等待该线程完成执行，然后再继续执行下一步操作。这意味着主线程将阻塞，直到被 `join()` 的线程执行完毕。这通常用于等待工作线程完成并获取其结果。

```c++
cppCopy code
void threadFunction() {
    // Some thread work
}

int main() {
    std::thread t(threadFunction);
    t.join(); // 主线程等待 t 完成
    return 0;
}
```

在上面的示例中，主线程等待线程 `t` 完成，然后继续执行 `return 0;`。

- **detach() 方法**： 调用 `detach()` 方法将分离线程，意味着主线程和子线程之间的连接被切断。分离线程不再与主线程同步，主线程可以继续执行，而不需要等待分离的线程完成。分离的线程在执行完毕后，其资源会被自动回收。

```c++
cppCopy code
void threadFunction() {
    // Some thread work
}

int main() {
    std::thread t(threadFunction);
    t.detach(); // 分离线程 t
    return 0;
}
```

