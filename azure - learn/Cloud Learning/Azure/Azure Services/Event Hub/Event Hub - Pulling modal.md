
Azure Event hub is a big data driven method of storing and processing data in real time. 

it is an alternative to [[Event Grid - Pushing Modal]]

Its considered an [[Event Ingestor Paas]] that sits between event publishers and consumers to decouple event streams from both sides. 


Event hub Name space.


what exams want us to know about various components of event hubs

1. its a streaming solution for real time or close event tracking
2. save no more then 7 days 
3. similar to apachi kakfa but not
4. but easily integrate with [[Apachi kafka]]
5. more then save into [[Azure data lake]] or [[Azure Blob Storage]] Gen1/2 by using [[Event Hubs Capture]]


NOTE: Event Resources has Event Instances has partitions min 1 and max 32

Offset : data position.
Checkpoint : to save the offset address.

![[Pasted image 20230812175204.png]]