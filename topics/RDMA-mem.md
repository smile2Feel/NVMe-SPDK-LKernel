# RDMA-related

## Topics
1. `numa-balancing`, `get_user_pages`, `VA->PA`
2. `HCA event`, `HCA bond`
3. ... 

## Docs
* LDD3
  - Performing Direct I/O (p455)
  - Direct Memory Access(p460)
* APUE
  - Shared Memory(15.9)

## Ques
1. 先`malloc`再`ibv_reg_mr`， 是如何pin住内存的？VA->PA保存到哪里去了？
2. 先`shmget`再`ibv_reg_mr`，是如何pin住内存的？VA->PA保存到哪里去了？为何能提高iops？

1. `iser_cm_connect_request` `struct iser_device.ibv_ctxt`是从`rdma_cm_event.id`里面拿出来的？cm_id是连接后不变的吗？
2. `rdma_cm_event`中有哪些信息需要用到？
3. `struct iser_conn`里面的list。
4. UD QP有ibv_ctxt吗？UD建连也会建立QP吗？
