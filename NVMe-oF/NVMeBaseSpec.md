## Architecture
### Controller Architecture

### NVM Queue Models
### Message-based Transport Queue Model
#### **QUES**:
1. Submission Queue Flow Control
    - Head entry pointer如何实现的？只是一个数值吗？
    - The host may use this value to size I/O Submission Queues and optimize the number of commands
submitted at one time per queue to achieve the best performance.(3.3.2.5)
        > 队列的大小对性能有哪些影响？不是越大越好吗？
    - 如果controller队列满时受到capsule，是直接返回失败吗？
        > If the controller detects that the host has submitted a command capsule to a full Submission Queue, then the controller shall:   
        a) stop processing commands and set the Controller Fatal Status (CSTS.CFS) bit to ‘1’ (refer to section 9.5); and  
        b) terminate the NVMe Transport connection and end the association between the host and the controller.

        > When this condition occurs, host software should
attempt to reset and then re-initialize the controller.

        > If the Controller Fatal Status (CSTS.CFS) bit is set to ‘1’ on any controller in the NVM subsystem, the host
        should issue a Controller Reset to that controller.

2. Completion Queue Considerations
    - The host should size each Completion Queue to support the maximum number of commands that the host
could have outstanding at one time for a particular Submission Queue. The Completion Queue size may
be larger than the size of the corresponding Submission Queue to accommodate responses for commands
that are being processed by the controller in addition to responses for commands that are still in the
Submission Queue.(3.3.2.6)
        > 如何理解outstanding, IO不在submission就在completion Queue吗？
3. Completion/Submission Queue在memory-based/message-based中的实体？是在controller实现吗？