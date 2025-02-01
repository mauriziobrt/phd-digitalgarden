---
{"dg-publish":true,"permalink":"/ph-d-macro-tasks/tools-for-database-and-software-analysis-to-split-into-separate-files/tools-for-database-and-software-analysis-to-split-into-separate-files/","tags":["software","database","analysis"]}
---

  

_Software is fluid, it’s never still, it always moves._



--- start-multi-column: ExampleRegion1  
```column-settings  
number of columns: 4  
```


- Sequence Mining Techniques
    
    - Sequence Pattern Mining (SPM)
    - Prefix Span Algorithm
    - Sequential Pattern Discovery Using Sequence Database (SPADE)


--- end-column ---

- Statistical Methods
    - Time series analysis
    - Markov chain modeling
    - Event correlation analysis

--- end-column ---


- Machine Learning Approaches
    - Recurrent Neural Networks (RNNs)
    - Long Short-Term Memory (LSTM) networks
    - Temporal Convolutional Networks (TCNs)

--- end-column ---

- Trace Analysis Techniques
    - Event log parsing
    - Transition matrix creation
    - Frequency analysis of event sequences

--- end-multi-column

https://github.com/huggingface/text-clustering

Transition matrix → between

**entropy of information** - the longest the starting status the more entropy - the shorter the less

entropy 0 is the least possible event

try and explore the obvious to less obvious interactively with p5.js interface - markov

controlla ci sia la mail dei phd

---

**Scope: creating software, which will be used later in the program, to read into tracing data, turning it into datasets, and finding ways to portray several visualizations easily.**

---

- [x] Transform the data into a dataset.
- [x] Text-clustering, fixing and test
- [x] LLM for event retrieval - else use regex
- [x] Windowing of elements
- [x] Sequence analysis of data
- [ ] Study sequential modeling as done in librosa.

---

**Current Problem: I need to extract patterns from the data and see how they are connected to each other.**

Why? I want meta-objects. I need meaningful informations.

- **Strategy 1:**

- [ ] Feed the LLM with windowed sequences (maybe with overlapping) and ask it to classify symbolically.

- **Strategy 2:**

- [x] Sequence pattern mining. Give windowed sequences to the system and retrieve patterns.
    
    **Result** - The algorithm should be fine-tuned to the task, because it returns a lot of 1 event sequences, although it is visible that there is no huge pattern connection between most elements. Although syscall_slow_exit_work does have a sort of connection with certain events, as visible in the snippet below.
    

```JavaScript
syscall_slow_exit_work transitions:
  -> fpregs_assert_state_consistent: 0.84
  -> exit_to_usermode_loop: 0.07
```

I’ve also got to check other aspects like windowing with skipping elements? But I don’t know if that makes sense. Which is the connection between these single elements? Is there one? Are they somewhat related? Is a CPU thread executing multiple events at a time or single ones but really fast?

Ah this is interesting: [https://www.bbc.co.uk/bitesize/guides/zws8d2p/revision/2](https://www.bbc.co.uk/bitesize/guides/zws8d2p/revision/2)

So it’s executing one event at a time, and, since this is something I did not know, it may also be something the layperson isn’t aware of.

Another aspect I forgot to consider for my Database is the CPU thread and the task-pid.

[https://wikileaks.org/ciav7p1/](https://wikileaks.org/ciav7p1/)

[https://www.sciencedirect.com/science/article/pii/S2666281721001293](https://www.sciencedirect.com/science/article/pii/S2666281721001293)

> [!important] ==**IMPORTANT: I must know what these data points actually mean. I need to gather an understanding of these traces.**==

### **How does a CPU work?**

> It would be cool to have a map like those of Crawford but for how the CPU works internally, like Cache and stuff. And then sonify these connections after the visualization to display the values.

It’s a microscopic process, a top-down approach to explore how do these things work.

syscall_slow_exit_work stands at the assembly level? But no, it is a kernel function in linux, and linux is built in C. Which in the graph should be Compiled/Intermediate language.

```Mermaid
flowchart LR
    id1(High-Level Programming Language) --> id5(Compiled/Intermediate Language) --> id2(Machine Code - 00101 specific to CPU architecture) --> id3(Microcode - Low Level Firmware CPU) --> id6(Transistor-Level Operations) --> id7(Quantum/Electron Level)
```

### Now back to the original problem. What are these system traces?

[https://www.kernel.org/doc/Documentation/trace/tracepoints.txt](https://www.kernel.org/doc/Documentation/trace/tracepoints.txt)

[https://blogs.oracle.com/linux/post/taming-tracepoints-in-the-linux-kernel](https://blogs.oracle.com/linux/post/taming-tracepoints-in-the-linux-kernel)

I need to find a “_chiave di lettura_” are the processes in assembly/bytecode or c?

Not exactly system calls, but a trace of system call events. This is an ftrace (function trace) log showing the detailed kernel-level function call sequence during a system call execution:

- Shows kernel internal functions like `mutex_unlock`, `__fsnotify_parent`
- Captures system call workflow
- Includes `syscall_slow_exit_work` and `sys_write`
- Represents low-level kernel execution tracking, not the system calls themselves

These function traces are primarily written in C, but interact closely with assembly:

- Kernel functions in Linux are predominantly written in C
- Critical low-level operations use inline assembly or assembly-level interfaces
- `syscall_slow_exit_work` and related functions are C implementations
- C code translates to assembly instructions for actual hardware execution
- Directly interfaces with CPU architecture at assembly level during execution

The trace shows the C-level function call sequence that ultimately gets translated to assembly and machine instructions.

These traces are a meta-representation - a logging mechanism that captures the internal function call sequence. They provide a diagnostic view of kernel operations, showing the sequence and details of what's happening "behind the scenes" during system call processing, but aren't the actual low-level operations themselves. It's like a detailed debug log of the system's internal workflow.

These traces are describing C behavior, with hooks into assembly. They represent the C-level function call sequence in the Linux kernel, which ultimately gets compiled to and executed as assembly/machine instructions. They're a human-readable representation of the kernel's internal C function calls during system call processing.

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Intel_Xeon_3060_Conroe_%28Reshoot%29_-_Flickr_-_cole8888.jpg/2560px-Intel_Xeon_3060_Conroe_%28Reshoot%29_-_Flickr_-_cole8888.jpg)](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Intel_Xeon_3060_Conroe_%28Reshoot%29_-_Flickr_-_cole8888.jpg/2560px-Intel_Xeon_3060_Conroe_%28Reshoot%29_-_Flickr_-_cole8888.jpg)

  

- **Alternative Take:**

Create a graphical representation, for the sake of simplicity the vertical space represents the event type (I have around 500 events), and the horizontal space its disposition in time.

Dall’analisi delle transizioni sembra possa essere interessante creare una mappa indicando quanto é probabile che un evento segua l’altro.

```Mermaid
flowchart LR
    id1[(Sequence from software traces)] --> id5(((One hot encoding))) --> id2(Extract Patterns and create a hierarchy) --> id3(Visualize and sonify the patterns)
```

  

## Trace to sound

  

```Mermaid
flowchart LR
    id1[(Sequence from software traces)] --> id5((Embedding in P5)) --> id2(Sonification using Webaudio)
```

  

---

**What is the main purpose of my research?**

```Mermaid
%%{init: {'theme':'dark'}}%%
mindmap
  root(PhD)
	  Aim: Communicating the intangible nature of software execution
	  Develop methods for the sonification of invisible data
		  (Mappings Strategies)
		  (Sound Design - There is currently no established and widely accepted practice for transforming stream-based data into sound for arbitrary data)
		  (Retrieval of Hidden Processes Data - employ dynamic analysis to collect software traces that serve as raw material for revealing software execution)
		  (Dataset Analysis)
			  (Sequential Analysis)
		
    

```

**Which are the obfuscated systems of software?**

```Mermaid
%%{init: {'theme':'dark'}}%%
mindmap
  root(Obfuscated Systems)
	  Cloud Architectures
	  (Machine Learning Algorithms Black-Box Nature)
	  Machine Level Computation - Assembly
	  Medium Level Computation - Programming Language
	  High Level Interface and GUI - Hides Backend, Example ATM no way of telling it runs on windows

    

```

**How can we get a sense of software’s hidden work?**

```Mermaid
%%{init: {'theme':'dark'}}%%
mindmap
  root(Seeing Through The Machine)
	  As an end-user: Error, Glitches
	  software analytics
	  XAI - Explainable AI
	  Mechanistic Interpretability
```

---

## How do I enhance the perception of these systems/architectures?

## How can I look at software, how many angles, how many POV?

I think I should decide _n_ systems/architectures and proceed with studying them.

---

### Relevant Informations:

---

![image 5.png|image 5.png](/img/user/Assets/image%205.png)

Kate Crawford is interested in materializing the system and showing its true impact. The materiality of the system, like mining, server location, construction, etc.. is not my main focus, although I can mention this as another way of looking through the system. We built systems so complicated that now we need to find new ways of communicating about them and we don’t understand them anymore. It’s like Ioana was saying that she had to look at how a computer works on a base level and that made her start from the transistor itself.

  

[https://extractivism.online/](https://extractivism.online/)

[https://calculatingempires.net/](https://calculatingempires.net/)

# Log Monitoring

Log analysis is → process of reviewing and interpreting log files to gain insights into a system’s behavior, performance, and security.

Various sources generate logs: os, apps, databases, servers, network devices.

Types of logs:

- Access Logs: They record requests made to a server
- Error Logs: Capture incidents in a system, useful for troubleshooting (Connect here, when the system fails we gather some understanding of its nature)
- Event Logs: Record of significant events (logins, startups)

Techniques:

- Correlation → looking for patterns/connections between different log sources.
- Pattern recognition → example, to detect unusual spikes in traffic or recurring error patterns
- System Performance Analysis→ CPU usage, memory utilization, etc…
- Log monitoring with AI→ Automate log analysis and automatically alert of significant events or anomalies.

Data analysis:

- Clustering
- SVM: classifier for detecting anomalies in data
- Decision Tree: classifier for detecting patterns and predicting outcomes

  

  

AI log monitoring:

Trained on real-time information streams in the form of network logs

> _“information from log data itself may not hold any long-term value”_ [https://www.splunk.com/en_us/blog/learn/log-monitoring.html](https://www.splunk.com/en_us/blog/learn/log-monitoring.html)

**What is the elastic stack, and why do I need to look into it?**

It is a stack that comprises different softwares. **Elasticsearch**, for example, deals with log analytics, which is relevant for my research, because logs are a way to look through the machine work. **Elasticsearch** indexes, analyzes, and searches the ingested data - which are logs from the machine. It can be a useful tool to learn about the possible processing of data. It’s also open source.

[https://www.elastic.co/elastic-stack](https://www.elastic.co/elastic-stack)

[https://www.splunk.com/en_us/blog/learn/log-analysis.html](https://www.splunk.com/en_us/blog/learn/log-analysis.html)

---

![Screenshot_2024-12-16_at_13.25.12.png](/img/user/Assets/Screenshot_2024-12-16_at_13.25.12.png)

![image 1 2.png|image 1 2.png](/img/user/Assets/image%201%202.png)

[https://www.youtube.com/watch?v=WvaBPSeA_JA](https://www.youtube.com/watch?v=WvaBPSeA_JA)[[settingupandunderstandingopentelemetrycollec\|settingupandunderstandingopentelemetrycollec]]

Occam’s razor

[https://www.ibm.com/think/topics/arima-model](https://www.ibm.com/think/topics/arima-model)

[https://www.splunk.com/en_us/blog/devops/observability-and-machine-learning.html](https://www.splunk.com/en_us/blog/devops/observability-and-machine-learning.html)

---

# Anomaly detection

**Why do I need to perform anomaly detection on a time series?**

I don’t know, it is one of the common data science practices of time series analysis but it’s not mine.

[https://www.youtube.com/watch?v=qy41dXGbAxY](https://www.youtube.com/watch?v=qy41dXGbAxY)

- To detect outliers and find when the system is not working correctly.

[https://scikit-learn.org/stable/modules/outlier_detection.html](https://scikit-learn.org/stable/modules/outlier_detection.html)

  

# Shadow AI

[https://www.ibm.com/think](https://www.ibm.com/think)

[https://www.splunk.com/en_us/blog/learn/shadow-ai.html](https://www.splunk.com/en_us/blog/learn/shadow-ai.html)

[https://www.ibm.com/think/topics/shadow-ai](https://www.ibm.com/think/topics/shadow-ai)

While shadow IT focuses on any unauthorized application or service, shadow AI zeros in on AI-specific tools, platforms and use cases. For instance, an employee might use a [large language model](https://www.ibm.com/topics/large-language-models) (LLM) to quickly generate a report without realizing the security risks. The key difference lies in the nature of the tools being used: Shadow AI is about the unauthorized use of artificial intelligence, which introduces unique concerns related to [data management](https://www.ibm.com/topics/data-management), model outputs and decision-making.

log stream --predicate '(process == "WindowServer")' --debug