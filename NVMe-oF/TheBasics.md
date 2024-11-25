# Concepts {#concepts}

## NVMe-oF {#NVMe-oF}

`Subsystem`: **Subsystems** contain **namespaces** and **controllers** and perform **access control**. 

- An NVM subsystem includes one or more domains, one or more controllers, zero or more namespaces, and one or more ports.(refer to 1.5.43)
- 

`Target`:  The collection of **subsystems with the associated namespaces**, plus the set of **transports** and their associated **network connections**. 





















spdk_nvmf_tgt中的subsystem_ids, subsystems。

bit_array.c是干啥的？

thread.c spdk_io_device_register

