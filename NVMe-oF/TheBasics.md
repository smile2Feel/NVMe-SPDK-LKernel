# Concepts {#concepts}

## NVMe-oF {#NVMe-oF}

`Subsystem`: **Subsystems** contain **namespaces** and **controllers** and perform **access control**. 

- An NVM subsystem includes one or more domains, one or more controllers, zero or more namespaces, and one or more ports.(refer to 1.5.43)
- 

`Target`:  The collection of **subsystems with the associated namespaces**, plus the set of **transports** and their associated **network connections**. 



















todo:

Target:

spdk_nvmf_tgt中的subsystem_ids, subsystems(ns变化)

bit_array.c是干啥的？

thread.c spdk_io_device_register/spdk_get_io_channel/poll_group



Transport:

spdk_thread_send_msg（spdk_get_thread(),...) ->发送给自己？

nvmf_transport_use_iobuf

trid: listener还是transport?

  There is a one-to-one mapping between I/O Submission Queues and I/O Completion Queues.
NVMe over Fabrics does not support multiple I/O Submission Queues being mapped to a single
I/O Completion Queue;  



Subsystem:

RB_INSERT

serial_number, model_number

discovery_subsystems

nvmf_subsystem_state_change(有点复杂)

 A running subsystem may be paused by calling [spdk_nvmf_subsystem_pause()](https://spdk.io/doc/nvmf_8h.html#a7be3b7421b631e48f9a0178ed8db8842) and resumed by calling [spdk_nvmf_subsystem_resume()](https://spdk.io/doc/nvmf_8h.html#aac21e50a3e893cf2629955dd553e9e32).  对一个动态subsystem，如何管理这个很关键。



bdev, namespace:

ctrlr不需要主动创建？

desc的作用？

bdev_register/bdev_open





summary:

pg: subsystem_pg, transport_pg, nvmf_pg

device: target, namespace





grammer:

 nvmf_transport_opts_copy

