最初产生的 mutex 对象是处于 unlocked 状态的

对于一个对象里的多个方法，要让第二方法在第一方法后执行，则构造函数里lock2.lock(),
第二方法里lock2.lock()，这样第二方法就会一直阻塞，直到第一方法执行lock2.unlock()

条件变量（condition_variable）实现多个线程间的同步操作；当条件不满足时，相关线程被一直阻塞，直到某种条件出现，这些线程才会被唤醒

（1）wait（unique_lock <mutex>＆lck）
当前线程的执行会被阻塞，直到收到 notify 为止。
（2）wait（unique_lock <mutex>＆lck，Predicate pred）
当前线程仅在pred=false时阻塞；如果pred=true时，不阻塞。
wait（）可依次拆分为三个操作：释放互斥锁、等待在条件变量上、再次获取互斥锁