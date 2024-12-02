Apache Kafka và Các Khái Niệm Cơ Bản trong Spring Kafka
Apache Kafka là một nền tảng phân tán dùng để xử lý, lưu trữ, và truyền tải luồng dữ liệu theo thời gian thực. Khi tích hợp với Spring Boot (thông qua Spring Kafka), bạn có thể xây dựng các ứng dụng mạnh mẽ để gửi, nhận, và xử lý thông điệp.

1. Các Khái Niệm Cơ Bản trong Kafka
   Topic
   Topic là nơi lưu trữ các thông điệp trong Kafka.
   Mỗi topic được chia thành các partition.
   Các producer gửi thông điệp tới một topic, và các consumer nhận thông điệp từ topic đó.
   Partition
   Partition là một đơn vị lưu trữ của topic, giúp phân tán dữ liệu trên nhiều máy trong một cụm Kafka.
   Một topic có thể có nhiều partition, và mỗi thông điệp trong partition được xác định bởi một offset (vị trí duy nhất).
   Producer
   Producer là thành phần chịu trách nhiệm gửi thông điệp vào Kafka.
   Một producer có thể gửi thông điệp tới một hoặc nhiều topic.
   Consumer
   Consumer là thành phần đọc dữ liệu từ Kafka.
   Các consumer thuộc một consumer group. Kafka đảm bảo rằng mỗi thông điệp trong một partition được xử lý bởi một consumer trong group đó.
   Broker
   Broker là một node (máy chủ) trong cụm Kafka. Mỗi broker chịu trách nhiệm lưu trữ và quản lý các partition của topic.
   Zookeeper
   Zookeeper là hệ thống quản lý cụm Kafka, chịu trách nhiệm theo dõi trạng thái của broker và duy trì thông tin về metadata.
   Offset
   Offset là một chỉ số duy nhất xác định vị trí của một thông điệp trong partition.
   Consumer có thể quản lý offset để đảm bảo việc đọc thông điệp đúng thứ tự.
2. Spring Kafka
   Spring Kafka là một thư viện giúp dễ dàng tích hợp Apache Kafka vào các ứng dụng Spring Boot. Nó cung cấp các API và công cụ để quản lý producer, consumer, và các cấu hình liên quan.

Producer trong Spring Kafka
Producer dùng để gửi dữ liệu (thông điệp) tới topic trong Kafka.
Trong Spring Kafka, KafkaTemplate được sử dụng để gửi thông điệp.
Consumer trong Spring Kafka
Consumer dùng để nhận và xử lý thông điệp từ Kafka.
Trong Spring Kafka, @KafkaListener giúp đơn giản hóa việc lắng nghe và xử lý thông điệp từ topic.
Message Listener Container
Một cơ chế giúp quản lý consumer trong Spring Kafka.
Dựa trên ConcurrentMessageListenerContainer, Spring Kafka có thể xử lý đồng thời nhiều consumer.
3. Các Thành Phần Chính trong Spring Kafka
   KafkaTemplate
   Là một lớp hỗ trợ trong Spring Kafka để gửi thông điệp.
   Tích hợp các tính năng như retries (thử lại) và transactions (giao dịch).
   @KafkaListener
   Annotation được sử dụng để định nghĩa một consumer lắng nghe thông điệp từ topic.
   Hỗ trợ nhiều tính năng như xử lý đồng thời và ghi log thông điệp.
   ProducerFactory & ConsumerFactory
   Cấu hình các producer và consumer.
   Quản lý cách producer và consumer tương tác với Kafka.
   Message Conversion
   Spring Kafka hỗ trợ tự động chuyển đổi dữ liệu, ví dụ từ JSON sang Object và ngược lại, thông qua các MessageConverter.
4. Luồng Hoạt Động Cơ Bản
   Producer gửi thông điệp: Producer gửi thông điệp tới một Kafka topic (thông qua KafkaTemplate).

Broker lưu trữ thông điệp: Kafka broker lưu trữ thông điệp trong topic, chia nhỏ chúng thành các partition.

Consumer đọc thông điệp: Consumer lắng nghe topic (sử dụng @KafkaListener) và xử lý các thông điệp.

Offset được quản lý: Kafka tự động quản lý hoặc consumer có thể tùy chỉnh cách theo dõi offset.

5. Ứng dụng Thực Tế của Kafka
   Log Aggregation: Thu thập và xử lý log từ nhiều nguồn.
   Real-Time Streaming: Xử lý dữ liệu theo thời gian thực, ví dụ trong ngành tài chính hoặc IoT.
   Event Sourcing: Xử lý các sự kiện trong hệ thống phân tán.
   Data Integration: Làm pipeline dữ liệu giữa các hệ thống.
6. Ưu Điểm của Kafka
   Hiệu suất cao: Kafka có khả năng xử lý hàng triệu thông điệp mỗi giây.
   Phân tán: Dữ liệu được lưu trữ và xử lý trên nhiều broker.
   Khả năng mở rộng: Dễ dàng mở rộng hệ thống khi cần.
   Độ tin cậy cao: Đảm bảo thứ tự và độ bền của thông điệp.


What is event-driven architecture?
Event-driven architecture (EDA) is a software design pattern
Different applications can asynchronously produce and consume events/messages via an event broker/message broker.
Applications communicate with each other by sending and/or receiving events or messages "asynchronous“ 