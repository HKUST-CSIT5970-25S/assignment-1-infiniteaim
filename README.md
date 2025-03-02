[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/IAASVEAZ)
# CSIT5970 Assignment-1: EC2 Measurement (2 questions, 4 marks)

### Deadline: 11:59PM, Feb, 28, Friday

---

### Name: YU, Chenwei
### Student Id: 21135523
### Email: cyuaz@connect.ust.hk

---

## Question 1: Measure the EC2 CPU and Memory performance

1. (1 mark) Report the name of measurement tool used in your measurements (you are free to choose *any* open source measurement software as long as it can measure CPU and memory performance). Please describe your configuration of the measurement tool, and explain why you set such a value for each parameter. Explain what the values obtained from measurement results represent (e.g., the value of your measurement result can be the execution time for a scientific computing task, a score given by the measurement tools or something else).

    > **1.** I use phoronix-test-suite run pts/compress-7zip to test CPU performace cause it is a common method to test cpu and the result is the **MIPS(Million Instructions Per Second)**.
    > **2.** Then I use phoronix-test-suite run pts/ramspeed to test memory writing/reading performance, including Add, Copy and Scale types with Interger benchmark, the result type is the W/R rate **MB/s(Mege Bytes per Seconds)**.

2. (1 mark) Run your measurement tool on general purpose `t2.micro`, `t2.medium`, and `c5d.large` Linux instances, respectively, and find the performance differences among these instances. Launch all the instances in the **US East (N. Virginia)** region. Does the performance of EC2 instances increase commensurate with the increase of the number of vCPUs and memory resource?

    In order to answer this question, you need to complete the following table by filling out blanks with the measurement results corresponding to each instance type.

    | Size        | CPU performance | Memory performance |
    | ----------- | --------------- | ------------------ |
    | `t2.micro` | 3730MIPS - 3103MIPS| 10615.62 MB/s 10797.76 MB/s  10053.99 MB/s|
    | `t2.medium`  |10140MIPS -  5911MIPS |19200.65 MB/s  19595.73 MB/s 18304.58 MB/s|
    | `c5d.large` | 7562MIPS - 4840 MIPS |13916.40 MB/s  13802.71 MB/s  13759.32 MB/s |

    > Region: US East (N. Virginia). Use `Ubuntu Server 24.04 LTS (HVM)` as AMI.

## Question 2: Measure the EC2 Network performance

1. (1 mark) The metrics of network performance include **TCP bandwidth** and **round-trip time (RTT)**. Within the same region, what network performance is experienced between instances of the same type and different types? In order to answer this question, you need to complete the following table.

    | Type                      | TCP b/w (Mbps) | RTT (ms) |
    | ------------------------- | -------------- | -------- |
    | `t3.medium` - `t3.medium` |3.72 Gbits/sec  | 593ms    |
    | `m5.large` - `m5.large`   |9.47 Gbits/sec  | 140ms    |
    | `c5n.large` - `c5n.large` |4.96 Gbits/sec  | 212ms    |
    | `t3.medium` - `c5n.large` |2.30 Gbits/sec  |  655ms   |
    | `m5.large` - `c5n.large`  |3.05 Gbits/sec  | 1118ms   |
    | `m5.large` - `t3.medium`  |1.99 Gbits/sec  |  1278ms  |

    > Region: US East (N. Virginia). Use `Ubuntu Server 24.04 LTS (HVM)` as AMI. Note: Use private IP address when using iPerf within the same region. You'll need iPerf for measuring TCP bandwidth and Ping for measuring Round-Trip time.

2. (1 mark) What about the network performance for instances deployed in different regions? In order to answer this question, you need to complete the following table.

    | Connection                | TCP b/w (Mbps) | RTT (ms) |
    | ------------------------- | -------------- | -------- |
    | N. Virginia - Oregon      |                |          |
    | N. Virginia - N. Virginia |4.96 Gbits/sec  | 212ms    |
    | Oregon - Oregon           |4.95 Gbits/sec  | 500ms    |
 
    > Region: US East (N. Virginia), US West (Oregon). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI. All instances are `c5.large`. Note: Use public IP address when using iPerf within the same region.
