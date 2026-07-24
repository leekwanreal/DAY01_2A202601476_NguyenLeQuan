# K3 — Ngày 1: Bài Tập & Phản Ánh
## Khám Phá LLM API | Phiếu Thực Hành

**Thời lượng:** 9h00–13h00


---

## Block 1 — API Cơ Bản (trả lời sau Checkpoint 1)

### Câu 1.1 — Độ nhạy của temperature
Gọi `call_openai` với temperature 0.0, 0.5, 1.0 và 1.5 dùng prompt
**"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**
> Temperature 0.0: Một sự thật thú vị về Việt Nam là đất nước này có một hệ thống hang động lớn nhất thế giới, đó là hang Sơn Đoòng. Hang Sơn Đoòng nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng, tỉnh Quảng Bình. Hang được phát hiện vào năm 1991 bởi một người dân địa phương tên là Hồ Khanh, nhưng mãi đến năm 2009 mới được công bố rộng rãi sau khi một đoàn thám hiểm người Anh do Howard Limbert dẫn đầu tiến hành khảo sát. Hang Sơn Đoòng có kích thước khổng lồ với chiều dài hơn 5 km, cao 200 m và rộng 150 m, đủ lớn để chứa cả một tòa nhà chọc trời 40 tầng. Bên trong hang còn có hệ sinh thái riêng với rừng cây, sông ngầm và các loài động thực vật độc đáo.

> Temperature 0.5: Một sự thật thú vị về Việt Nam là đất nước này có hệ thống hang động lớn nhất thế giới, đó là hang Sơn Đoòng. Hang này nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng, tỉnh Quảng Bình. Được phát hiện vào năm 1991 bởi một người dân địa phương và được thám hiểm lần đầu tiên vào năm 2009 bởi một nhóm thám hiểm người Anh, hang Sơn Đoòng có chiều dài hơn 5 km, chiều cao lên tới 200 mét và rộng khoảng 150 mét. Bên trong hang có cả một dòng sông ngầm và hệ sinh thái riêng biệt, tạo nên một cảnh quan thiên nhiên kỳ vĩ và độc đáo.

> Temperature 1.0: Một sự thật thú vị về Việt Nam là đất nước này là một trong những quốc gia hàng đầu thế giới về sản xuất và xuất khẩu cà phê. Cà phê Việt Nam nổi tiếng với hương vị đậm đà và đặc biệt, và phương pháp pha cà phê phin truyền thống đã trở thành một phần văn hóa độc đáo. Cà phê sữa đá và cà phê trứng là hai loại đồ uống đặc trưng mà nhiều du khách yêu thích khi đến thăm Việt Nam.

> Temperature 1.5: Một sự thật thú vị về Việt Nam là hệ thống hang động Phong Nha-Kẻ Bàng, đặc biệt là hang Sơn Đoòng, được coi là hang động lớn nhất thế giới. Sơn Đoòng nằm trong vườn quốc gia Phong Nha-Kẻ Bàng, thuộc tỉnh Quảng Bình. Hang động này có thể chứa cả một tòa nhà chọc trời cao tới 40 tầng. Với những dòng sông ngầm, rừng cây và hệ sinh thái độc đáo bên trong, Sơn Đoòng không chỉ là một kỳ quan địa chất mà còn là điểm đến hấp dẫn cho các nhà thám hiểm và du khách trên toàn thế giới.

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Temperature thấp (0.0 – 0.5): Phản hồi mang tính deterministic (xác định) và an toàn cao, tập trung chọn chủ đề phổ biến nhất (hang Sơn Đoòng) với cấu trúc và số liệu thực tế gần như trùng khớp hoàn toàn. Temperature cao (1.0 – 1.5): Phản hồi gia tăng độ ngẫu nhiên và tính đa dạng, giúp mô hình chọn chủ đề mới (văn hóa cà phê ở 1.0) hoặc thay đổi góc nhìn, văn phong diễn đạt linh hoạt và bay bổng hơn (ở 1.5).

### Câu 1.2 — Chọn temperature cho sản phẩm
**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Mức temperature đề xuất: 0.0 đến 0.3. Vì, chatbot hỗ trợ khách hàng cần cung cấp thông tin chính xác, nhất quán và đáng tin cậy (như chính sách đổi trả, giá sản phẩm, quy trình dịch vụ). Temperature thấp giúp giảm thiểu hiện tượng bị ảo giác (hallucination), đảm bảo thông tin quan trọng được truyền đạt đúng sự thật và cố định giữa các lần truy vấn của khách hàng.

### Câu 1.3 — Đánh đổi chi phí
Kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người gọi API 3 lần,
mỗi lần trung bình ~350 token đầu ra.

**Ước tính GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này? Nêu một
trường hợp GPT-4o xứng đáng với chi phí và một trường hợp nên dùng mini:**
> Workload output: $10.000 \text{ users} \times 3 \text{ requests} \times 350 \text{ tokens} = 10.500.000 \text{ output tokens/ngày}$.
Bảng giá Output Token (OpenAI):GPT-4o: \$10.00 / 1M GPT-4o-mini: $0.60 / 1M$Mức chênh lệch: GPT-4o đắt hơn GPT-4o-mini khoảng 16,6 lần $(\$10.00 / \$0.60)$ đối với lượng token đầu ra này. 

> Nên dùng GPT-4o (Xứng đáng chi phí): Các tác vụ xử lý logic phức tạp, lập trình/phân tích mã nguồn sâu, viết báo cáo chuyên môn cao hoặc đọc/phân tích biểu đồ kỹ thuật nhiều tầng.
Nên dùng GPT-4o-mini: Các tác vụ chăm sóc khách hàng thông thường, tóm tắt văn bản ngắn, phân loại ý định người dùng (intent classification) hoặc trích xuất thông tin cơ bản.

---

## Block 2 — System Prompt & Token (trả lời sau Checkpoint 2)

### Câu 2.1 — Sức mạnh của persona
Gọi `chat_with_system_prompt` hai lần với cùng câu hỏi
**"Giải thích blockchain là gì?"** nhưng hai system prompt khác nhau:
- "Bạn là giáo viên tiểu học, giải thích thật đơn giản cho trẻ 8 tuổi."
- "Bạn là chuyên gia tài chính, trả lời chuyên sâu bằng thuật ngữ kỹ thuật."

**Hai phản hồi khác nhau như thế nào (độ dài, từ vựng, ví dụ)? System prompt
ảnh hưởng đến hành vi model ra sao?** (3–4 câu)
> Phản hổi của system prompt 1: "Blockchain giống như một cuốn sổ lớn mà mọi người có thể nhìn thấy và đồng ý với nhau rằng thông tin trong đó là đúng. Khi có một giao dịch mới, nó sẽ được viết vào cuối sổ và không ai có thể xóa hay thay đổi các giao dịch đã được ghi. Mỗi trang trong sổ được gọi là "block", và khi các trang được nối lại với nhau thì gọi là "chain". Vì vậy, blockchain là một chuỗi các trang sổ mà ai cũng tin tưởng là chính xác và không thể thay đổi."

> Phản hồi của system prompt 2: 
"Blockchain là một cấu trúc dữ liệu phân tán và phi tập trung, hoạt động như một sổ cái kỹ thuật số để ghi lại các giao dịch trên nhiều máy tính. Điều này đảm bảo rằng dữ liệu không thể bị thay đổi mà không có sự đồng thuận từ toàn bộ mạng lưới. Blockchain bao gồm một chuỗi các khối (blocks), trong đó mỗi khối chứa một danh sách các giao dịch đã được xác thực. 
Các thành phần chính của blockchain: Khối (Block): Mỗi khối chứa một danh sách các giao dịch, một mã băm của khối hiện tại, một mã băm của khối trước đó, và một số nonce (số chỉ được sử dụng một lần). Mã băm là một chuỗi ký tự duy nhất được tạo ra từ các dữ liệu trong khối và được sử dụng để xác thực tính toàn vẹn của dữ liệu. Giao dịch (Transaction): Đây là các hoạt động được ghi lại trong blockchain. Mỗi giao dịch thường bao gồm thông tin về nguồn, đích và số lượng tài sản được chuyển. Nút mạng (Node): Mỗi nút mạng là một máy tính trong mạng"

> Sự khác biệt về phản hồi: System Prompt 1 tạo ra câu trả lời ngắn gọn, từ vựng đơn giản và sử dụng hình ảnh so sánh gần gũi ("cuốn sổ lớn", "trang sổ") phù hợp với trẻ 8 tuổi; trong khi System Prompt 2 tạo ra câu trả lời dài hơn, tính thuật ngữ chuyên sâu ("cấu trúc dữ liệu phân tán", "mã băm", "số nonce", "nút mạng") đi kèm phân tích cấu trúc kĩ thuật.
Tác động của System Prompt: System Prompt đóng vai trò định hình persona (vị thế), giọng văn (tone of voice), cấp độ từ vựng và độ sâu kiến thức của mô hình trước khi xử lý câu hỏi của người dùng. Nó giúp điều chỉnh hành vi của AI để tùy biến thông tin phù hợp nhất với từng đối tượng độc giả cụ thể mà không làm thay đổi bản chất cốt lõi của nội dung.


### Câu 2.2 — tiktoken vs đếm từ
Chọn một đoạn văn tiếng Việt ~100 từ. So sánh số token theo `count_tokens`
(tiktoken) với ước lượng `số từ / 0.75` mà Part 1 đã dùng.

**Hai con số chênh nhau bao nhiêu phần trăm? Vì sao tiếng Việt thường tốn
nhiều token hơn tiếng Anh cùng độ dài?**
> Đoạn văn 100 từ: "Hành trình chinh phục mục tiêu chưa bao giờ là một con đường bằng phẳng. Trên con đường đó, thử thách và thất bại là những điều không thể tránh khỏi. Tuy nhiên, điểm khác biệt giữa thành công và thất bại nằm ở lòng kiên trì. Khi đối mặt với khó khăn, thay vì bỏ cuộc, người kiên trì chọn cách đứng dậy, rút ra bài học và tiếp tục bước tiếp. Mỗi bước đi nhỏ, dù chậm chạp, đều đưa ta tiến gần hơn đến ước mơ. Hãy tin tưởng vào hành trình của bản thân, kiên định với mục tiêu đã đề ra, bởi vì quả ngọt chỉ dành cho những ai không bỏ cuộc."

> Số tokens sau khi dùng tiktoken là 152 > ước lượng 100 / 0.75 = 133. Từ điển ưu tiên tiếng Anh: Thuật toán (BPE) mã hóa cả từ tiếng Anh dài thành 1 token, trong khi tiếng Việt bị cắt thành nhiều mảnh sub-words. Ký tự có dấu (UTF-8): Các dấu thanh và chữ cái tiếng Việt (â, đ, á...) tốn 2–3 bytes mã hóa, buộc tokenizer phải tách nhỏ một từ thành 2–3 token.

---

## Block 3 — Streaming & Độ Bền (trả lời sau Checkpoint 3)

### Câu 3.1 — Trải nghiệm người dùng với streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì
non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất đối với các ứng dụng tương tác trực tiếp với người dùng (như Chatbot UI, trợ lý ảo), nơi phản hồi dài tốn nhiều thời gian sinh ra; việc hiển thị từng từ giúp giảm TTFT (Time-To-First-Token), tạo cảm giác phản hồi tức thì và cải thiện trải nghiệm người dùng. Ngược lại, non-streaming phù hợp hơn cho các tác vụ xử lý ngầm (background jobs), gọi API từ backend-to-backend, trích xuất dữ liệu cấu trúc (JSON/Structured Outputs), hoặc các tác vụ cần nhận trọn vẹn toàn bộ câu trả lời trước khi thực hiện bước tiếp theo.

### Câu 3.2 — Vì sao backoff theo cấp số nhân?
**So với delay cố định (ví dụ luôn chờ 1 giây), exponential backoff có lợi
thế gì khi API bị quá tải? Điều gì xảy ra nếu hàng nghìn client cùng retry
với delay cố định giống nhau?**
> Lợi thế của Exponential Backoff: Giúp hệ thống tự động giãn khoảng cách thời gian giữa các lần thử lại ($1s \rightarrow 2s \rightarrow 4s \dots$), tạo thời gian nghỉ tăng dần để máy chủ (server) đang quá tải có đủ không gian phục hồi và xử lý hết hàng đợi tắc nghẽn.Hiện tượng xảy ra nếu dùng delay cố định: Nếu hàng nghìn client cùng thử lại sau một khoảng thời gian cố định (ví dụ đúng 1 giây), tất cả sẽ đồng loạt gửi lại request tại cùng một thời điểm. Điều này gây ra hiện tượng Thundering Herd Problem (hoặc Retry Storm), tạo ra các đỉnh lưu lượng (traffic spikes) liên tục dội vào máy chủ, khiến hệ thống tiếp tục sập và không thể khôi phục.

---

## Block 4 — Mini-Project (trả lời sau Checkpoint 4)

### Câu 4.1 — Thiết kế persona
**Bạn chọn persona gì cho trợ lý của mình? Viết lại system prompt đó và giải
thích 1–2 lựa chọn từ ngữ quan trọng trong prompt (ví dụ: vì sao yêu cầu
"trả lời ngắn gọn", vì sao chỉ định ngôn ngữ...):**
> Tôi chọn persona Trợ lý lập trình Senior với System Prompt: "Bạn là một lập trình viên senior; hãy luôn trả lời đi thẳng vào vấn đề bằng tiếng Việt, cung cấp ví dụ mã nguồn súc tích và giữ giọng văn khách quan, chuyên nghiệp." Việc yêu cầu "đi thẳng vào vấn đề" giúp cắt bỏ phần chào hỏi rườm rà nhằm tiết kiệm chi phí output token và giúp lập trình viên tìm thấy giải pháp ngay lập tức, trong khi việc chỉ định "bằng tiếng Việt" giúp cố định ngôn ngữ phản hồi nhất quán dù trong prompt có chứa nhiều thuật ngữ kỹ thuật tiếng Anh.

### Câu 4.2 — Hạn chế & cải thiện
**Trợ lý của bạn hiện có hạn chế lớn nhất là gì (ví dụ: history chỉ 3 lượt,
không có bộ nhớ dài hạn, không kiểm duyệt nội dung...)? Đề xuất một cải
thiện cụ thể và mô tả ngắn cách triển khai:**
> Hạn chế lớn nhất của trợ lý hiện tại là chưa biết quản lý cửa sổ ngữ cảnh (Context Window), khiến chi phí tăng vọt và dễ vượt giới hạn token khi hội thoại kéo dài. Để cải thiện, tôi đề xuất triển khai cơ chế Sliding Window kết hợp Tóm tắt (Summarization): hệ thống sẽ chỉ giữ lại 6 lượt thoại mới nhất trong mảng messages, đồng thời dùng một prompt ngầm để nén các lượt thoại cũ hơn thành một đoạn tóm tắt ngắn rồi đính kèm ngay sau System Prompt để giữ bối cảnh dài hạn.

---

## Danh Sách Kiểm Tra Nộp Bài

- [ ] `python grade.py` — xem điểm tự động, mục tiêu ≥ 75/100
- [ ] Cả 4 checkpoint pytest đều pass
- [ ] Tất cả 9 câu trong file này đã được trả lời
- [ ] Đã copy bài làm vào folder `solution/` và zip theo hướng dẫn README
