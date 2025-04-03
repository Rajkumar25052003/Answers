Question 1 answer explanation :

The output confirms that the receivers execute one after the other rather than simultaneously.
The message "After sending signal" appears only after both receivers have finished executing.
The total runtime is approximately 3 seconds (2 + 1), indicating that the functions were not executed in parallel.
Receiver 1 must complete before Receiver 2 begins, demonstrating sequential execution.

This behavior highlights synchronous execution because:
The sender remains blocked while the receivers are running.
The receivers execute in a predictable, ordered manner.
There is no parallelism or asynchronous execution involved.

