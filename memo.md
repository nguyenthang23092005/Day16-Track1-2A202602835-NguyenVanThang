# Memo Teardown — Cursor

**Họ tên:** Nguyễn Văn Thăng

**Vì sao chọn sản phẩm này:** Cursor đưa AI vào nơi lập trình viên viết, hiểu và sửa code, rồi mở rộng sang giao việc cho agent. Lịch sử cập nhật công khai giúp phân tích sự chuyển đổi từ trợ lý trong editor sang hệ thống thực thi và kiểm tra công việc.

**Ngày chốt dữ liệu:** 03/10/2026. Dữ kiện có link gốc; nguyên lý, JTBD và dự đoán là phân tích do AI soạn, được người học xác nhận đã kiểm chứng. Bản nghiên cứu được lưu trong [research-notes-cp0-cp3.md](research-notes-cp0-cp3.md).

**Bản in:** [memo-print.html](memo-print.html), dàn 5 trang A4; in ở tỷ lệ 100%, tắt header/footer của trình duyệt. Số trang của preview Markdown phụ thuộc công cụ hiển thị.

**§1. Timeline các cập nhật lớn**

Ngày dưới đây là ngày đăng cập nhật, không bảo đảm mọi tài khoản nhận rollout cùng lúc. Mã C giữ từ bản nghiên cứu để nối các phần; “x10” và “moat” chỉ hướng tạo giá trị/lợi thế, chưa phải kết quả đã đo.

| Thời điểm | Cập nhật | Context lúc đó | Nguyên lý |
|---|---|---|---|
| **C02 · 22/08/2024** | Composer bật mặc định cho Pro/Business; Composer Projects beta chia sẻ chỉ dẫn giữa các phiên. [0.40](https://cursor.com/changelog/0-40-x). | Claude 3.5 Sonnet và Artifacts đã ra tháng 06/2024. Cursor đưa AI ngay vào editor. [Anthropic](https://www.anthropic.com/news/claude-3-5-sonnet). | **Vertical AI:** chuyên biệt hóa AI cho lập trình, giảm chuyển đổi giữa hội thoại và code. |
| **C04 · 24/11/2024** | Agent phiên bản sớm trong Composer tự chọn context và dùng terminal. [0.43](https://cursor.com/changelog/0-43-x). | Claude computer use beta ra 22/10/2024; Supermaven gia nhập Cursor ngày 12/11. [Anthropic](https://www.anthropic.com/news/3-5-models-and-computer-use), [Cursor](https://cursor.com/blog/supermaven). | **x10:** giao chuỗi tìm context → sửa → chạy lệnh; đơn vị giá trị chuyển từ gợi ý sang tác vụ, chưa chứng minh nhanh gấp 10 lần. |
| **C08 · 15/05/2025** | Background Agent early preview chạy remote, nhiều agent làm song song. [0.50](https://cursor.com/changelog/0-50). | Claude Code đã có research preview từ 24/02/2025; Cursor chuyển MAX sang giá token/API. [Claude Code](https://www.anthropic.com/news/claude-3-7-sonnet), [pricing](https://cursor.com/blog/better-pricing). | **x10:** giao việc bất đồng bộ để developer tiếp tục việc khác; hiệu quả cần tính cả công sửa và review. |
| **C09 · 04/06/2025** | Bugbot review GitHub PR và đưa context về editor qua “Fix in Cursor”. [1.0](https://cursor.com/changelog/1-0). | Background Agent vừa ra vài tuần trước; 1.0 mở rộng truy cập nhưng lúc đó còn điều kiện Privacy Mode. [1.0](https://cursor.com/changelog/1-0). | **Vertical AI:** đi sâu vào workflow viết → PR → review → sửa, nối phát hiện vấn đề với hành động. |
| **C16 · 29/10/2025** | Composer, model coding agentic đầu tiên của hãng; giao diện quản lý tối đa 8 agent song song và team commands/rules. [2.0](https://cursor.com/changelog/2-0). | Cursor đã đầu tư model chuyên dụng qua Supermaven; 2.0 vẫn cải thiện cơ chế thực thi cho model ngoài. [Supermaven](https://cursor.com/blog/supermaven), [2.0](https://cursor.com/changelog/2-0). | **Wrapper/moat:** tối ưu cùng model, thực thi và điều phối để tạo lợi thế ngoài quyền truy cập model phổ biến; model riêng chưa bảo đảm moat bền vững. |
| **C22 · 24/02/2026** | Cloud agents có VM riêng, tương tác với phần mềm đã sửa và trả video, ảnh, logs để review. [Computer use](https://cursor.com/blog/agent-computer-use). | Theo nhóm sản phẩm, thiếu khả năng dùng phần mềm gây trần năng lực; agent local còn tranh tài nguyên. [Nguồn](https://cursor.com/blog/agent-computer-use). | **Định nghĩa “tốt”:** thay đổi phải chạy được và có bằng chứng nghiệm thu; lượng code sinh ra không đủ để đánh giá. |
| **C31 · 17/08/2026** | Origin early beta: host repo, PR và đồng bộ GitHub. Repo tạo trên Origin dùng Origin làm nguồn chuẩn; repo đồng bộ vẫn dùng GitHub. [Origin](https://cursor.com/changelog/origin-code-hosting). | Agents Window 3.0 từ 02/04/2026 đã điều phối qua nhiều repo/môi trường; Origin đưa code, PR và agent về cùng nơi. [3.0](https://cursor.com/changelog/3-0). | **Wrapper/moat:** sở hữu thêm lưu trữ/cộng tác có thể tăng mức gắn vào vận hành; beta chưa chứng minh adoption hoặc chi phí chuyển thực tế. |
| **C35 · 10/09/2026** | Projects beta có coordinator lập kế hoạch, giao việc, giữ context dài hạn và chạy công việc định kỳ/theo sự kiện. [Projects](https://cursor.com/changelog/projects). | Đã có agent và cloud; vấn đề tiếp theo là phải hướng dẫn lại mỗi task. Projects chia sẻ kiến thức giữa các lần chạy. [Nguồn](https://cursor.com/changelog/projects). | **Vòng lặp học:** làm việc → lưu hiểu biết/artifacts → agent sau sử dụng lại. Đây là tích lũy context, chưa chứng minh huấn luyện lại model hay network effect. |

**Vì sao chọn những mốc này:** Tám mốc thay đổi đơn vị công việc, mức tự chủ hoặc phạm vi workflow, tạo chuỗi editor → tác vụ → review → dự án. Bản cuối loại **C19 — 2.3** vì trọng tâm sửa lỗi/ổn định, và loại **C01 — launch Product Hunt** vì ngày launch trên kênh phân phối không tự chứng minh quyết định sản phẩm mới hay ngày Cursor ra đời ([2.3](https://cursor.com/changelog/2-3), [PH](https://www.producthunt.com/products/cursor/launches/cursor-2)). Pricing và 3.0 được giữ làm context để giới hạn ở 8 hàng; lựa chọn do AI đề xuất, người học xác nhận đã kiểm chứng.

**§2. Tệp user & JTBD**

“Early adopters” là lát cắt cộng đồng 2023–2024; “tệp hiện tại” là nhóm có bằng chứng sử dụng năm 2026, chưa chứng minh là nhóm đông nhất. JTBD là diễn giải từ tình huống, không phải trích nguyên văn.

| | Early adopters | Tệp hiện tại |
|---|---|---|
| **Đặc điểm** | Người viết code tự chọn editor AI, muốn giải quyết vấn đề nhanh và kiểm soát chi phí. **Luis Moreno**, tài khoản mandelbrojt, kể chuyển từ VS Code sang Cursor ngày 15/12/2023. [Lời kể](https://forum.scrimba.com/t/best-ai-tools-for-developer/104/11). | Kỹ sư frontend trong team doanh nghiệp, làm trên repo production với chuẩn chung. **Mick Ryan, staff engineer tại Box**, xây toolkit bằng Cursor rules. [Box, 13/02/2026](https://cursor.com/blog/box). |
| **JTBD chính** | Khi bị kẹt với code/thư viện chưa quen, tôi muốn tìm cách sửa ngay trong dự án để hoàn thành chức năng và giảm tra cứu, thử sai. | Khi phải migration hoặc sửa frontend production, tôi muốn thay đổi đúng chuẩn repo, kiểm tra được kết quả và giảm công review cho team. |
| **Trước đó họ làm bằng cách nào** | Luis xác nhận dùng VS Code. Đọc docs, tìm file, sửa/test thủ công là cách cũ AI suy ra; nguồn chưa kể đủ từng bước. [Luis](https://forum.scrimba.com/t/best-ai-tools-for-developer/104/11). | Box nêu quy ước trong tài liệu/trao đổi nội bộ và React migration từng đình trệ. Chia việc sửa từng phần là suy luận; nguồn không nêu IDE cũ của Mick. [Box](https://cursor.com/blog/box). |

**Dịch chuyển tệp:** C04 cho agent thực thi, C09 nối sang review PR và C16 thêm cấu hình chung/điều phối, giúp phục vụ tổ chức cần thay đổi nhất quán. Đây là cơ chế có thể hỗ trợ dịch chuyển từ năng suất cá nhân sang giao việc trong team; không chứng minh từng release gây ra quyết định mua của Box. Case Box có trước C22/C31/C35, nên không dùng các mốc ra sau để giải thích adoption đã xảy ra.

**Tệp mở rộng:** Clement Gougeon, Head of Design Tech tại Grab, dùng Cursor tạo bản sửa UI để Engineering kiểm tra thay vì chỉ gửi bug/design file. Case ngày 15/09/2026 cho thấy designer tham gia trực tiếp vào chất lượng sản phẩm, nhưng vẫn cần học Git và review; chưa chứng minh đây là tệp chủ đạo. [Grab](https://cursor.com/blog/grab).

**Switching cost (map 4 forces):** lấy chiều **cách cũ → Cursor**; Push/Pull thúc đẩy đổi, Anxiety/Habit cản đổi.

| Lực | Bằng chứng và ý nghĩa |
|---|---|
| **Push — bất mãn với cách cũ** | Designer Grab muốn xử lý UI mà không chờ bàn giao. Nếu Cursor vẫn làm user chờ hoặc sửa lại nhiều, bất mãn đó có thể đẩy họ sang công cụ khác. [Grab](https://cursor.com/blog/grab). |
| **Pull — sức hút của kết quả mới** | Luis kể giải quyết vấn đề nhanh hơn. Carle phản đối UI review mới ngày 30/07/2025: lợi ích giữ user gồm cả kiểm soát thay đổi. [Luis](https://forum.scrimba.com/t/best-ai-tools-for-developer/104/11), [Carle](https://forum.cursor.com/t/cursor-1-3-removed-an-important-feature/124244). |
| **Anxiety — lo ngại giải pháp mới** | Lo chất lượng, dữ liệu và chi phí; HuntsDesk kể hủy gói vì muốn pricing dễ đoán hơn. Đây là phản hồi cá nhân trong thread cũ, không mô tả giá hiện tại. Khi rời Cursor, team cũng phải đánh giá lại công cụ thay thế. [Phản hồi](https://www.reddit.com/r/cursor/comments/1lu3yll/my_honest_experience_why_im_moving_from_cursor_to/). |
| **Habit — quán tính cách đang làm** | Ban đầu thói quen editor cũ cản chuyển; sau adoption, rules, review và đào tạo nội bộ có thể giữ team ở Cursor. Box có chương trình mentor; đổi công cụ đòi hỏi học và chuẩn hóa lại. [Box](https://cursor.com/blog/box). |

**Lực giữ mạnh nhất — giả thuyết:** Pull, tức lợi ích ròng khi hoàn tất thay đổi và review trong cùng workflow; Habit tăng sức giữ ở team. Nếu công cụ khác cho kết quả tương đương với ít công sửa/review hoặc chi phí thấp hơn, user có thể chuyển hoặc dùng song song. Với repo Git bên ngoài, chưa có bằng chứng source code bị khóa; Origin/Projects có thể tăng chi phí chuyển repo/context nếu team thực sự dùng chúng.

**Giới hạn:** case Box/Grab do nhà cung cấp chọn đăng, cộng đồng là mẫu tự chọn; chưa đủ xác định tỷ trọng phân khúc hoặc xếp hạng lực giữ chắc chắn. Xác nhận đã kiểm chứng nguồn không thay thế dữ liệu phỏng vấn hay thử nghiệm sản phẩm.

**§3. Ba dự đoán hướng đi (6–12 tháng tới)**

Chốt ngày **03/10/2026**, kiểm tra trong **03/04–03/10/2027**. AI đề xuất, người học xác nhận đã kiểm chứng; link hỗ trợ tiền đề, không xác nhận roadmap tương lai.

**Dự đoán 1** *(loại: mở rộng tính năng)*

- **Dự đoán:** Cursor đưa Projects ra khỏi beta, thêm tiêu chí nghiệm thu cấp dự án và báo cáo test tập trung cho migration kéo dài nhiều tuần.
- **Lập luận:** §1 C22 bổ sung bằng chứng chạy thử, C35 chuyển sang điều phối dự án; §2 có nhu cầu migration theo chuẩn chung tại Box. Chỉ tính đạt khi có cả phát hành rộng và chức năng nghiệm thu/test tập trung. [Projects](https://cursor.com/changelog/projects), [Box](https://cursor.com/blog/box).

**Dự đoán 2** *(loại: mở rộng segment)*

- **Dự đoán:** Cursor bổ sung onboarding và bộ mẫu sửa UI → preview → PR dành riêng cho product/UI designer trong team có repo sẵn.
- **Lập luận:** §2 có Clement tại Grab nhưng vẫn cần học Git; §1 C22 đã có bằng chứng UI để review. Đóng gói quy trình có thể giảm rào cản cho designer khác. Chỉ tính đạt khi có workflow/onboarding cụ thể, không chỉ bài marketing. [Grab](https://cursor.com/blog/grab), [Computer use](https://cursor.com/blog/agent-computer-use).

**Dự đoán 3** *(loại: mô hình kiếm tiền)*

- **Dự đoán:** Cursor bán gói credit trả trước riêng cho Projects, để tổ chức mua và phân bổ ngân sách agent theo dự án, bên cạnh phí seat.
- **Lập luận:** Context C08 có MAX chuyển sang usage; C35 mở rộng công việc liên tục, còn §2 có phản hồi muốn chi phí dễ đoán. Enterprise hiện đã có pooled usage: phần mới dự đoán là **credit riêng cho Projects**, không phải pooling. Chỉ tính đạt khi có gói thương mại đúng cơ chế đó. [Pricing 2025](https://cursor.com/blog/better-pricing), [giá hiện tại](https://cursor.com/pricing).

**Phản biện:** AI đánh giá cơ sở tương đối **1 > 2 > 3**. Giả định quyết định của dự đoán 1: context dài hạn giúp giảm tổng công sửa và review; nếu context sai/lỗi thời làm team phải kiểm tra lại quá nhiều, lợi ích mất đi. Beta kéo dài hoặc thay đổi ưu tiên kinh doanh cũng có thể khiến dự đoán không đạt trong kỳ kiểm tra.

**§4. AI Log**

AI là ChatGPT/Codex trong các bước soạn memo. **Nguyễn Văn Thăng xác nhận “tất cả đã kiểm chứng”** trong CP4; chưa cung cấp ghi chú từng link hay quyết định sửa/bác. Bảng tách đối chiếu do AI thực hiện và phần người học xác nhận, không tự thêm thao tác cá nhân chưa được kể.

| Việc | AI làm hay bạn làm? | Bạn kiểm chứng/phán đoán lại thế nào? |
|---|---|---|
| Chọn Cursor, tìm nguồn, gom 36 mốc CP0 | AI đề xuất và tổng hợp theo bản nháp | Bạn xác nhận đã kiểm chứng toàn bộ. Bản nháp ghi AI đã mở nguồn; CP4 chỉ mở lại nguồn dùng trong bản cuối, không tái kiểm tra đủ 36 mốc. |
| Chọn 8 mốc, viết context/nguyên lý §1 | AI chọn và lập luận | Bạn xác nhận đã kiểm chứng. AI mở lại 8 nguồn chính, đối chiếu ngày/tính năng; tách preview/beta khỏi GA, Composer trong editor khỏi model Composer; không coi x10/moat là kết quả đo. |
| User, JTBD và dịch chuyển tệp §2 | AI tìm lời kể và diễn giải | Bạn xác nhận đã kiểm chứng. AI mở lại Luis, Box, Grab; tách dữ kiện khỏi cách cũ/JTBD suy ra; không dùng release ra sau để giải thích adoption trước đó. |
| Map 4 forces, lực giữ mạnh nhất | AI phân tích định tính | Bạn xác nhận đã kiểm chứng. AI đọc Carle và HuntsDesk; giữ phản hồi ở mức cá nhân, đánh dấu lực giữ là giả thuyết, không suy ra tỷ lệ churn hay network effect. |
| Ba dự đoán và phản biện §3 | AI đề xuất; bạn xác nhận đã kiểm chứng | AI đối chiếu Projects beta, Box/Grab và trang giá; tách pooled usage đã có khỏi credit Projects dự đoán. Có kỳ kiểm tra, tiêu chí đạt và giả định làm gãy; chưa có ghi chú riêng của bạn về dự đoán đồng ý/bác. |
| Ghép CP4, rút gọn, sửa cách ghi vai trò | AI biên tập | Lưu bản CP0–CP3 riêng; bỏ câu “tôi chọn” gán lựa chọn AI cho người học. Kiểm tra 4 phần, 8 mốc có link, 3 dự đoán, AI log đủ 3 cột; đo layout bằng Chrome và xem ảnh bản in 5 trang, không tràn. |
| Xác nhận họ tên và tình trạng kiểm chứng | Bạn trả lời trực tiếp | Dùng đúng tên Nguyễn Văn Thăng và xác nhận trong phiên này; không tự nhận bạn đã phỏng vấn, thử sản phẩm hoặc giải thích bài độc lập. |

**Phản biện CP4 — AI làm thay nhiều nhất ở đâu?** Phán đoán sản phẩm ở §2–§3: diễn giải JTBD, xác định lực giữ và nối bằng chứng thành dự đoán. AI cũng chọn mốc/viết nguyên lý §1, nên vai trò AI bao phủ phần lớn bài.

**Nếu bỏ phần đó, còn tự giải thích được không?** Bạn đã xác nhận kiểm chứng toàn bộ, nhưng phiên này chưa ghi nhận phần giải thích độc lập. Chuỗi để tự bảo vệ là **tác vụ trong editor → giao việc cho agent → cần review/bằng chứng → điều phối dự án**; mỗi dự đoán phải chỉ ra mốc, nhu cầu user và điều kiện khiến nó sai. Đây là gợi ý AI soạn, không phải lời tự đánh giá của người học.
