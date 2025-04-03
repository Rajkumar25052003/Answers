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
