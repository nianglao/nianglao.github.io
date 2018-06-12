---
layout: post
title:  "Python Multiprocessing Queue Deadlock Issue"
date:   2018-06-12 17:21:01 +0800
categories: bug
---
There are two ways to declare queue:

Option 1:
```python
from multiprocessing import Queue
q = Queue()
```

Option 2:
```python
from multiprocessing import Manager
q = Manager().Queue()
```

Option 1 may trigger deadlock issue described as in [warning](https://docs.python.org/2/library/multiprocessing.html).

*If a child process has put items on a queue created with Option 1, then that process will not terminate until all buffered items have been flushed to the pipe.*

*This means that if you try joining that process you may get a deadlock unless you are sure that all items which have been put on the queue have been consumed. Similarly, if the child process is non-daemonic then the parent process may hang on exit when it tries to join all its non-daemonic children.*

Use Option 2 can avoid this issues.

**Note:** I met this issue on PRD in validation codes.
