## Docs
* LDD3
  - Performing Direct I/O (p455)
  - Direct Memory Access(p460)
* APUE
  - Shared Memory(15.9)

## Ques
1. 先`malloc`再`ibv_reg_mr`， 是如何pin住内存的？VA->PA保存到哪里去了？
2. 先`shmget`再`ibv_reg_mr`，是如何pin住内存的？VA->PA保存到哪里去了？为何能提高iops？
