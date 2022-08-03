# Gopi Krishna Madabhushi
## Software Engineer, yellow.ai
gopikrishnam@gmail.com

[LinkedIn](https://www.linkedin.com/in/gopik-/)

---

## Skills
Distributed Systems, Speech Recognition, Machine Learning

---
## Technologies
* Programming - golang/rust/nodejs/java/R/python
* Distributed Systems - kubernetes/docker/prometheus
* Machine Learning - Tensorflow
* Speech Recognition - Kaldi-asr

---
## Work Experience
|    |    |
|----|----|
|`Apr 2020 - Present`| Software engineer at yellow.ai|
|`Oct 2010 - Apr 2020`| Software engineer at google.com|
|`Jan 2003 - Oct 2010`| Software engineer at microsoft.com|
|`Jan 2002 - Jan 2003`| Research Associate, Media Labs Asia|

## Education
|      |      |      |
|------|------|------|
|`Jan 2002`| Master of Engg (Computer Science) | Indian Institute of Science, Bangalore | 
|`Jun 2000`| B.Tech (Computer Science)| National Institute of Technology, Warangal |
|      |      |      |

## Articles
* [API Flow control](https://github.com/gopik/storage-reading-list/blob/main/ApiFlowControl.md)
* [Building a logs search system](https://github.com/gopik/storage-reading-list/blob/main/LogsSearch.md)
* [Real time analytics system](https://github.com/gopik/storage-reading-list/blob/main/RealtimeAnalytics.md)

# Projects
## yellow.ai
* Flink pipeline to support upserts in delta lake tables (open source)
The objective of this project is detailed in [Real time analytics system](https://github.com/gopik/storage-reading-list/blob/main/RealtimeAnalytics.md).
There's an existing flink connector for delta lake that supports appends to delta lake. I'm working on enhancing this to be able to support
updates to existing rows (updates will be implemented by rewriting affected parquet files).

Challenges (Not done yet):
1. Reduce the amount of IO (write amplication). T
2. The files can become "fragmented" like few files becoming too big (or small) etc, so another challenge is to maintain the storage by keeping files at reasonable size.
3. This requires the files be sorted by the primary key of the data source, but this might slow down many queries which don't filter by primary keys. How do we handle this scenario.

* Disaster recovery design - Prototype different solutions with < 1hr RTO/RPO (strimzi kafka mirroring vs native db replication).
Challenges:
1. Many data stores for which need to handle disaster recovery.
2. Native replication has overhead of maintaining different procedures for replication and failover.

Proposed a POC where we would streamline replication and failover by using a message queue to capture CDC and apply the CDC to the DR site. This simplifies failover/replication at the cost of building and maintaining a new system. The challenges were, replicating the data base that have relational constraints.
The POC was abandoned since building and maintaining cost was considered too high as well as potential unknowns in dealing with a new system in a critical area like diaster recovery.

* Resilience and Scalability of engagement backend [Tech lead] - Improving observability and identifying bottlenecks in the design and fix the design to improve scalability
Challenges:
1. Control system issues where we need to regulate micro tasks to achieve maximum throughput without overwhelming other systems. This was originally managed by heuristics which lead to either overwhelming other systems or underutilizing them. Explored this area in detail (see * [API Flow control](https://github.com/gopik/storage-reading-list/blob/main/ApiFlowControl.md) for findings). Eventually this was solved by a much simpler solution by observing the queue size of the target system directly instead of estimating it based on signals.

* Multi region deployment of cloud platform [Tech lead and project management] - Enable the existing system to be deployed in multiple cloud regions to enable data localization
Challenges:
1. Achieve this without major changes to the services and any business logic.

* Log collection to blob store [Tech lead]
Challenges:
1. Low cost, setting up ELK is expensive.
2. Find a good tradeoff between eng time spent during debugging and the cost of setting up the best system.

* Log monitoring [IC] - Design a system to monitor logs in the logs storage backend to capture metrics
* Indian english and hindi speech recognizers [IC] - Build a speech recognizer using kaldi toolkit to transcribe english and hindi audio to text
Challenges:
1. Can we build a custom ASR model that is optimized for the data for our company and has better performance on our use cases compared to using cloud models?
2. Cost to build, maintain and optimize for many languages. Again a tradeoff between potential performance gain and cost.

* Cloud ASR analysis and custom model management [IC] - Build a frontend and backend for the developers of voice bots. This was used by the developers to go through transcripts of a bot/user conversation to identify ASR issues as well as manage custom models on azure
Challenges:
1. Given we use multiple custom models, how to manage access to cloud resources that are needed to maintain custom model. Wanted to avoid giving access to many users and instead hid this access control behind an internal service which was authenticating using internal auth.

* ASR latency improvement in telephony service [IC/Tech lead] - Improve the latency of speech recognition by implementing a streaming speech recognition client
Challenges:
1. Existing speech recognition was done after we had recorded user speech and it introduced latency in the bot response to this speech. This was fixed implementing a streaming speech recognition which enables processing most of the audio by the time user speech recording ends.

## google.com
* Google pay (ML) - Payments optimization [Tech lead/IC] - Optimize the payments processing routing based on recent performance of the processors involved.
Challenges:
1. This is a combinatorial structured optimization problem. In simple words, assume a structure with many fields and each field can take n different values. We need to identify an optimal combination given an input (features in ML). Overall the number of possible values for a structure is k^n. These k fields are not independent, hence we can't predict k values independently. 

* Google pay UPI (ML) [Tech lead/IC] - Optimize the payments in UPI to reduce the chances of stuck
payments in UPI.
Challenges:
1. We want to prevent stuck payments by failing them fast. But the cost of false positive is rejection of genuine payments. Cost function is 
* Google pay (vendor gateway) [IC} - API integration for tokenized payments
* Google pay (app) - Proximity based payments (explore signal processing algorithms to send data using sound as physical layer)
* Android One - P2P filesharing implementation not going throug internet
* Google maps - Tools for Ground truth development. Tools used by ops to draw maps using satellite imagery, review and moderate the edits etc.
* Google maps - Google maps search improvement for indian addresses (for google my business)
* Google calendar/exchange integration

## microsoft.com
* Developer tools (visual studio integration) for biztalk server
* JScript enhancements for internet explorer
* Internet explorer document object model improvements (garbage collection and js prototypes for dom objects)
* J# libraries maintenance (Java based on .NET)






