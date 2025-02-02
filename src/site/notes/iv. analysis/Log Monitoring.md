---
{"dg-publish":true,"permalink":"/iv-analysis/log-monitoring/","tags":["log","software","AI"],"noteIcon":""}
---

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
