Question 1 answer :

By default, Django signals operate synchronously. When a signal is triggered, all linked receiver functions execute sequentially in the order they were registered. The sender halts execution until all receivers have finished processing.

The output confirms that the receivers execute one after the other rather than simultaneously.
The message "After sending signal" appears only after both receivers have finished executing.
The total runtime is approximately 3 seconds (2 + 1), indicating that the functions were not executed in parallel.
Receiver 1 must complete before Receiver 2 begins, demonstrating sequential execution.

This behavior highlights synchronous execution because:

The sender remains blocked while the receivers are running.
The receivers execute in a predictable, ordered manner.
There is no parallelism or asynchronous execution involved.

Question 2 answer :

Yes, by default, Django signals execute within the same thread as the caller. The receiver functions run synchronously in the calling thread's context rather than a separate thread.

Thread Identification:
The code displays the current thread's name at each stage to confirm execution behavior.
Main Thread Execution:
The caller function runs in MainThread.
Both receiver functions also execute in MainThread.
Secondary Thread Execution:
The caller function runs in Thread-1.
Both receivers execute within Thread-1 as well.
Blocking Behavior:
The time.sleep() calls delay the execution of the calling thread, confirming that signals do not run in parallel.

Question 3 answer :

By default, Django signals are not tied to the same database transaction as the caller. They trigger instantly upon execution, even if the transaction is later rolled back. As a result, if a transaction fails and is rolled back, the signal may have already executed, which can lead to inconsistencies.

A TestModel instance is created within a transaction.
The post_save signal fires immediately after calling obj.save(), displaying Signal executed: Rollback Test.
An exception is raised, causing the transaction to be rolled back.
However, since the signal was triggered before the rollback occurred, it still executed, confirming that signals do not inherently follow transaction boundaries.

Custom classes in python question answer :

This approach defines a separate RectangleIterator class to handle iteration. It stores the length and width in a list and uses an index to track the current position. The __next__() method returns each value sequentially and raises StopIteration when all elements have been accessed. The Rectangle class implements __iter__() to return an instance of RectangleIterator, allowing objects of Rectangle to be iterated over in a structured manner.
