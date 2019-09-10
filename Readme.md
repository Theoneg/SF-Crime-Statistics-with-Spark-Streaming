

## SF Crime Statistics with Spark Streaming

Hi Reviewer,

Here are a few points to keep in mind as to the implementation of this project.

To begin, an incorrect dataset,`AB_NYC_2019.csv`, was given alongside the starter code.  I had to search for the SF Crime data `police-department-calls-for-service`, and managed to find it [Here](https://www.kaggle.com/san-francisco/sf-police-calls-for-service-and-incidents/downloads/sf-police-calls-for-service-and-incidents.zip/52#police-department-calls-for-service.csv). The data I got was `csv`,  so I converted it to `.json` format. After the conversion, the file I obtained was about `1.22GB` so I had to reduce some of the data that was in the file in other not to have a very heavy project file for submission.

Also, the dataset I downloaded has `key` fields which had values like `Crime Id`, so I had to convert it to something like `crime_id` as is used in the starter code.

After this setup of the working base, I completed `producer_server.py`. After running `python3 producer_server.py`, my producer_server was started and I was able to see the produced data from kafka consumer after running `bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic <your-topic-name> --from-beginning`. Below was my result:

![Consumer](images/kafka_consumer.png)

I also wrote a `data_consumer.py` script to consume data produced from the kafka producer. Below was the result:
![data_consumer](images/data_consumer.png)

Upon completion of the `data_stream.py`, I ran `spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.0 --master local[4] data_stream.py` and had several batch results on the console. Below is one of them:
![batch1](images/batch1.png)
