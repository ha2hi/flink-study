### 개요
Apache Flink를 사용하여 실시간 데이터를 처리할 때 시간(Window)을 기준으로 집계하여 데이터를 처리합니다.  
이 때 시간의 종류에는 어떤 것이 있는지와 의미를 알아보도록 하겠습니다.  
  
### Prosessing Time and Event Time
- Processing Time(처리 시간) : Apache Flink가 Data를 처리하는 시간 입니다.
- Event Time(이벤트 시간) : 이벤트 데이터에 존재하는 시간입니다.
![Event_Processing_Time](./img/event_processing_time.svg)
Event Time은 원천 시스템(ex. 센서, 웹로그 등등)에서 생성된 시간입니다. 데이터에 이벤트 발생 시간을 표시하는 creation_date와 같은 컬림을  기준으로 처리하는 것을 의미합니다.  
  
Processing Time은 원천 시스템에서 발생한 데이터를 큐에 저장한 데이터를 읽고 Flink 처리하는 시스템의 시간입니다.  
```
env.set_stream_time_characteristic(TimeCharacteristic.ProcessingTime)
env.set_stream_time_characteristic(TimeCharacteristic.EventTime)
```  
  

