---
title: "Navigating the Future of Cloud & AI: Werner Vogels Keynote"
date: 2026-10-02
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# Bài thu hoạch “Navigating the Future of Cloud & AI in Vietnam” - Keynote từ CTO Amazon Werner Vogels

### Mục Đích Của Sự Kiện

- Giải đáp những lo ngại về việc AI tự động hóa lập trình và liệu developers có bị thay thế hay không.
- Chia sẻ những insights cốt lõi về tư duy hệ thống (systems thinking), xuất sắc trong vận hành (operational excellence) và sự tiến hóa của kỹ sư hiện đại trong kỷ nguyên AI.
- Rút ra bài học thực tế từ quá trình phát triển hạ tầng và những thách thức về quy mô của Amazon.
- Truyền cảm hứng để các developers tiến hóa thành "Renaissance Developer" (Nhà phát triển Phục hưng), tận dụng AI nhưng vẫn giữ vững các kỹ năng cốt lõi của con người.

### Danh Sách Diễn Giả

- **Dr. Werner Vogels** – Chief Technology Officer và Vice President tại Amazon / Amazon Web Services (AWS)

### Nội Dung Nổi Bật

#### Sự cố triệu đô và sự ra đời của công nghệ lõi tự xây dựng (Homegrown Core Tech)

- **Điểm bùng phát**: Một sự cố sập cụm cơ sở dữ liệu quan hệ (RAC) vào mùa mua sắm cao điểm gây ra thời gian ngừng hoạt động cả ngày và thiệt hại hàng triệu đô la.
- **Phân tích mô hình sử dụng thực tế**: Kỹ sư phát hiện 70% workload là các truy vấn Key-Value đơn giản, 20% là các bảng đơn lẻ không liên kết, chỉ 10% thực sự cần khả năng quan hệ (relational).
- **Xây dựng giải pháp nội bộ**: Amazon tự thiết kế distributed Key-Value store của riêng mình, tạo nền tảng công nghệ cho Dynamo và DynamoDB.
- **Bài học cốt lõi**: Ở quy mô cực lớn, việc phụ thuộc vào các giải pháp đóng gói sẵn (off-the-shelf) có thể trở thành rủi ro vận hành lớn; các nhà lãnh đạo cần sẵn sàng xây dựng công nghệ riêng.

#### 4 Trụ cột của Xuất sắc trong Vận hành (Operational Excellence)

- **Đo lường ở phân vị 99.9 (P99.9)**: Theo dõi độ trễ trung bình là gây hiểu lầm; kỹ sư phải đo lường và tối ưu hóa ở P99.9 để nâng cao trải nghiệm tổng thể.
- **Chấp nhận "Mọi thứ đều hỏng hóc mọi lúc"**: Kiến trúc hệ thống phải được thiết kế để chịu được sự cố đột ngột của một hoặc hai trung tâm dữ liệu mà không làm gián đoạn dịch vụ.
- **Thể chế hóa "GameDays"**: Các đội cố ý ngắt kết nối các trung tâm dữ liệu production trong các cuộc diễn tập để kiểm tra khả năng failover tự động, loại bỏ sự can thiệp thủ công.
- **Đảo ngược mô hình kinh tế IT**: AWS tiên phong mô hình pay-as-you-go, đặt gánh nặng lên nhà cung cấp cloud phải cung cấp dịch vụ xuất sắc mỗi ngày để giữ chân khách hàng.

#### Giải phẫu của "Renaissance Developer" (Nhà phát triển Phục hưng)

- **Tò mò và Học tập liên tục**: Coi việc học tập suốt đời là cam kết bắt buộc giữa sự thay đổi không ngừng của ngôn ngữ và framework.
- **Tư duy hệ thống (Systems Thinking)**: Hiểu bức tranh toàn cảnh về cách các microservices tương tác ở quy mô lớn, thay vì chỉ tập trung vào một module cô lập.
- **Tinh thần sở hữu (Ownership)**: AI có thể tạo ra code, nhưng trách nhiệm cuối cùng về lỗi production, lỗ hổng bảo mật và tính toàn vẹn kiến trúc vẫn thuộc về kỹ sư.
- **Chuyên môn hình chữ T (T-Shaped Expertise)**: Duy trì kiến thức rộng across các lĩnh vực liền kề (UI, business logic, databases) bên cạnh chuyên môn sâu.
- **Kỹ năng giao tiếp**: Khám phá các vấn đề kinh doanh thực sự đằng sau các yêu cầu công nghệ và giải thích rõ ràng các sự đánh đổi (trade-offs) kỹ thuật cho các bên liên quan.

#### AI là Chất xúc tác, Con người là Cốt lõi Bất biến

- **Vai trò của AI**: Hoạt động như một trình biên dịch ngôn ngữ tự nhiên không hoàn hảo; xuất sắc trong việc tự động hóa các tác vụ lặp đi lặp lại và rút ngắn chu kỳ prototyping từ vài tuần xuống vài giờ.
- **Sự không thể thay thế của con người**: Khả năng phán đoán, sáng tạo, đồng cảm và niềm tự hào nghề nghiệp vẫn rất cần thiết để đánh giá rủi ro bảo mật, các trường hợp biên (edge cases) và hiệu quả code.
- **Cảnh báo về sự tự mãn**: Trích dẫn Đô đốc Grace Hopper: *"Cụm từ nguy hiểm nhất trong ngôn ngữ là, 'Chúng ta vẫn luôn làm theo cách này.'"*

### Những Gì Học Được

#### Tư Duy Thiết Kế

- **Hệ thống hơn là các silo**: Luôn nhìn vào bức tranh toàn cảnh và hiểu cách các thành phần tương tác ở quy mô lớn.
- **Tư duy làm chủ (Ownership)**: AI có thể tạo code, nhưng con người chịu trách nhiệm về kết quả, bảo mật và tính toàn vẹn kiến trúc.
- **Thách thức hiện trạng**: Tránh cái bẫy "Chúng ta vẫn luôn làm theo cách này" và liên tục tìm kiếm các giải pháp có khả năng mở rộng tốt hơn.

#### Kiến Trúc Kỹ Thuật

- **Đo lường những gì quan trọng**: Tối ưu hóa độ trễ P99.9, không chỉ hiệu suất trung bình, để đảm bảo trải nghiệm người dùng nhất quán.
- **Thiết kế cho sự thất bại**: Giả định mọi thứ sẽ hỏng và xây dựng các cơ chế failover và phục hồi tự động (ví dụ: GameDays).
- **Đúng công cụ cho đúng việc**: Đừng ép cơ sở dữ liệu quan hệ doanh nghiệp xử lý các workload Key-Value đơn giản; hãy chọn hoặc xây dựng các giải pháp chuyên biệt.

#### Chiến Lược Hiện Đại Hóa

- **Tiến hóa, đừng chỉ tự động hóa**: Sử dụng AI để rút ngắn thời gian prototyping và xử lý tác vụ lặp lại, nhưng dựa vào phán đoán của con người để đánh giá quan trọng.
- **Trau dồi kỹ năng hình chữ T**: Mở rộng kiến thức trên nhiều lĩnh vực để tối ưu hóa luồng dữ liệu end-to-end và kết quả kinh doanh.
- **Căn chỉnh kinh tế**: Tận dụng các mô hình cloud phù hợp chi phí với giá trị (pay-as-you-go) để thúc đẩy xuất sắc trong vận hành liên tục.

### Ứng Dụng Vào Công Việc

- **Áp dụng thực hành "GameDay"**: Đề xuất các cuộc diễn tập mô phỏng sự cố có kiểm soát trong môi trường staging để kiểm tra cơ chế cảnh báo và tự động phục hồi.
- **Tinh chỉnh chỉ số giám sát**: Chuyển trọng tâm từ độ trễ trung bình sang theo dõi độ trễ P99 hoặc P99.9 để xác định và giải quyết trải nghiệm người dùng tồi tệ nhất.
- **Đánh giá lại mô hình sử dụng database**: Phân tích các pattern truy cập dữ liệu hiện tại để đảm bảo công nghệ phù hợp đang được sử dụng (ví dụ: chuyển các tra cứu đơn giản sang Key-Value stores).
- **Thúc đẩy các đặc điểm của Renaissance Developer**: Khuyến khích học tập liên tục, chia sẻ kiến thức liên ngành và giao tiếp mạnh mẽ giữa các team engineering và business.
- **Tích hợp AI một cách có trách nhiệm**: Sử dụng công cụ AI cho prototyping và tác vụ lặp lại, nhưng duy trì quy trình review code nghiêm ngặt của con người về bảo mật, edge cases và hiệu quả.

### Trải nghiệm trong event

Tham dự keynote của Dr. Werner Vogels tại sự kiện **“Navigating the Future of Cloud & AI in Vietnam”** là một trải nghiệm vô cùng giá trị, giúp tôi có cái nhìn toàn diện và thực tế về cách điều hướng sự tiến hóa của kỹ thuật phần mềm trong kỷ nguyên AI. Một số trải nghiệm nổi bật:

#### Học hỏi từ một nhà lãnh đạo tầm nhìn
- Dr. Vogels đã chia sẻ những **bài học thực tế, có stakes cao** từ những ngày đầu của Amazon, minh họa cách một sự cố sập hệ thống trị giá hàng triệu đô la đã thúc đẩy việc tạo ra các công nghệ nội bộ đẳng cấp thế giới như DynamoDB.
- Hiểu sâu hơn rằng **xuất sắc trong vận hành (operational excellence)** không chỉ là mục tiêu kỹ thuật, mà là một mệnh lệnh kinh doanh cốt lõi.

#### Trải nghiệm kỹ thuật thực tế (Khái niệm)
- Khái niệm **đo lường ở phân vị 99.9** đã thay đổi hoàn toàn cách tôi suy nghĩ về giám sát hiệu suất và trải nghiệm người dùng, chuyển trọng tâm từ "hoạt động tốt phần lớn" sang "hoạt động ổn định cho mọi người".
- Tìm hiểu về **GameDays** cung cấp một chiến lược hữu hình, có thể hành động để xây dựng các hệ thống tự phục hồi thực sự kiên cường, thay vì chỉ hy vọng nó chịu được áp lực.

#### Tận dụng công cụ hiện đại (Góc nhìn AI)
- Khám phá vai trò thực tế của **AI trong phát triển phần mềm**: không phải là sự thay thế cho kỹ sư, mà là một chất xúc tác mạnh mẽ đòi hỏi sự giám sát nghiêm ngặt của con người.
- Hiểu được tầm quan trọng của việc coi đầu ra của AI như một "trình biên dịch không chính xác" đòi hỏi phán đoán của con người về bảo mật và hiệu quả.

#### Kết nối và trao đổi
- Sự kiện nhấn mạnh tầm quan trọng của **kỹ năng giao tiếp** trong engineering, giúp developers khám phá các vấn đề kinh doanh thực sự và giải thích rõ ràng các sự đánh đổi kỹ thuật.
- Các ví dụ thực tế làm nổi bật giá trị của **cách tiếp cận business-first, tư duy hệ thống** thay vì bị lạc trong các chi tiết kỹ thuật bị cô lập.

#### Bài học rút ra
- Nắm bắt tư duy **"Renaissance Developer"** — tò mò, tư duy hệ thống, tinh thần sở hữu, chuyên môn hình chữ T và giao tiếp — là chìa khóa để duy trì sự phù hợp trong thế giới driven bởi AI.
- Sự phát triển sự nghiệp bền vững đến từ **học tập liên tục** và thách thức hiện trạng, không phải từ nỗi sợ hãi về tự động hóa.
- **Thiết kế cho sự thất bại** và đảo ngược các mô hình kinh tế là nền tảng để xây dựng các kiến trúc cloud có khả năng mở rộng và hướng đến khách hàng.

#### Một số hình ảnh khi tham gia sự kiện
![alt text](../../images/event2.1.png)
![alt text](../../images/event2.2.png)
![alt text](../../images/event2.3.png)

> Tổng thể, sự kiện không chỉ cung cấp kiến thức kỹ thuật và vận hành sâu sắc mà còn giúp tôi thay đổi cách tư duy về khả năng phục hồi của hệ thống, vai trò đang phát triển của kỹ sư phần mềm và giá trị không thể thay thế của phán đoán con người trong kỷ nguyên AI.