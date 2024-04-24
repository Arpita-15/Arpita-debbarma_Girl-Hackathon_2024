# Arpita-debbarma_Girl-Hackathon_2024

**Problem Statement**
Refer to Fig 1.0 which shows a System on a Chip (SoC) consisting of a CPU and a IO peripheral accessing System memory through an weighted arbiter. The SoC components are connected through a Network on Chip (NOC). The NOC has a bi-direction port per component and routes traffic between to and fro from System memory. Each interface has buffering to account for latency of data transfer to and from System memory. Data traffic flows are between CPU to System Memory,IO peripherals to System memory. The weighted round robin arbiter feeds traffic from both CPU and IO to system memory. 
The traffic pattern in the NOC depends on the types of workloads running on CPU and IO. Given the vast possibilities of different traffic patterns, designing a NOC that is area and power efficient and yet able to achieve desired performance in terms of latency (time to retrieve data from memory) and bandwidth (throughput or the quantity of data transferred per second) is challenging. 
An over designed NOC with bigger buffers where not all entries are occupied  is area inefficient and predetermined arbitration weights will impact both bandwidth and latency 
Our goal here is to come up with the NOC design that is best suited for target workloads running on this system.  

![Diagram](https://github.com/Arpita-15/Arpita-debbarma_Girl-Hackathon_2024/assets/113752108/48b11e47-e10b-4772-b8ba-cd3aabc67fea)



**To generate the environment needed to run the code and execute it successfully, you would require the following:**

1)Simulator Setup: Set up the simulator environment that models the System on a Chip (SoC) as described in the problem statement. This includes configuring the CPU, IO peripheral, System memory, weighted arbiter, Network on Chip (NOC), and the required APIs for controlling and monitoring the system.
2)Interface Monitor Outputs: Obtain the interface monitor outputs from the simulator, which provide timestamped data about transactions (reads and writes) occurring on the CPU and IO interfaces.
3)Function Definitions: Define the necessary functions used in the code, such as parse_monitor_output to parse the interface monitor output and get_powerlimit_threshold to check the power limit threshold status.
4)Data Initialization: Initialize variables such as total_latency, total_bytes_transferred, total_cycles, throttling_cycles, and power_limit_exceeded before processing the interface monitor outputs.
5)Main Loop Execution: Iterate through the interface monitor outputs and update the variables accordingly based on the transaction type, timestamp, and data.
6)Calculations: Calculate the average latency, bandwidth, and throttling percentage based on the collected data.


**The approach used to generate the algorithm/design**
With a special focus on the Network on Chip (NOC) component, the algorithm/design provided uses a systematic approach to analyze important performance parameters and assess the effectiveness of a System on a Chip (SoC) design. This is an explanation of the approach we used:
Problem Understanding: The algorithm/design starts with a thorough understanding of the problem statement, which calls for optimizing the NOC architecture in order to meet performance targets for bandwidth, latency, and buffer occupancy.
Requirements Analysis The algorithm/design carefully examines the requirements given in the problem description, considering the necessity to evaluate bandwidth, latency, and frequency throttling while maintaining buffer occupancy and respecting power limits.
Decomposition: It breaks the issue into smaller, simpler tasks, like initializing variables, interpreting output from monitors, and figuring out performance indicators.
Modular Design: The algorithm/design uses a modular approach, dividing up the functionality into individual components or functions. For example, a function is defined to analyze monitor output, promoting code readability and reusability.
Effective Implementation: It uses a productive method to manage the computation of performance metrics and the processing of interface monitor outputs. To reduce computational overhead, code logic and data structures must be optimized.
Scalability and Adaptability: Its design allows for flexibility in performance optimization and evaluation by making it both scalable and adaptable to various workload conditions and system configurations.
Foundation for Reinforcement Learning: The algorithm/design provides the foundation for dynamically optimizing the NOC design parameters based on gathered performance data by utilizing reinforcement learning techniques.
Overall, a systematic, structured, and effective approach was used in creating the algorithm/design in order to meet the requirements and goals stated in the problem statement. It offers a strong basis for evaluating, processing, and possibly automating the SoC's NOC design optimization.

![RLFrame](https://github.com/Arpita-15/Arpita-debbarma_Girl-Hackathon_2024/assets/113752108/e297972f-d9c5-4759-95a7-7a6fdc2868a2)


**Proof of Correctness**
Variables: 
          total_latency=0
          total_bytes_transferred=0
         total_cycles=0
         throttling_cycles=0
         power_limit_exceeded=False
We can represent the parsing function as:
      parse_monitor_output(monitor_output)=(timestamp,txn_type,data)
      where timestamp,txn_type data are extracted from the monitor output string.
Updating total cycles:
            total_cycles=timestamp
 Checking power limit threshold: 
         power_limit_exceeded={True,if get_powerlimit_threshold()=1
                        {False,otherwise
Calculating latency for read transactions:  latency=timestamp−read_start_time[txn_type]
Calculating bytes transferred for write transactions:
bytes_transferred=length of data/2
Average latency:
           average_latency=total_latency/number_of_read_transactions
           Average bandwidth:
          average_bandwidth=total_bytes_transferred/total_cycles
          Throttling percentage:
           throttling_percentage=(throttling_cycles/total_cycles)×100


**Complexity Analysis**
Initializing variables takes constant time,O(1).
Parsing monitor output strings takes linear time relative to the length of the string,O(n)
Iterating through interface monitor outputs takes linear time relative to the number of outputs,O(m).
Updating total cycles, checking power limit threshold, and calculating latency and bytes transferred within the loop all take constant time,O(1) per iteration.
Calculating average latency, average bandwidth, and throttling percentage all take constant time,
O(1)
The overall time complexity can be expressed as O(n+m), where n is the length of the monitor output string and
m is the number of monitor outputs.


