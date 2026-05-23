# Bài Đăng Facebook

Mình vừa dùng Codex để hỗ trợ test và tạo một guide cho anh em dev muốn thử các AI coding CLI với free-tier token:

Repo: https://github.com/vandang890615/ai-cli-free-router-guide

Nội dung chính:

- Claude Code + free-claude-code để route qua NVIDIA NIM, OpenRouter hoặc local model
- FreeLLMAPI để gom Google Gemini, NVIDIA, OpenRouter, GitHub Models... vào một endpoint OpenAI-compatible
- Aider và OpenCode đã test được qua FreeLLMAPI khi cấu hình đúng model/provider
- Qwen Code test ổn nhất khi đi thẳng NVIDIA NIM; đường Qwen Code qua FreeLLMAPI còn vướng schema request
- Crush hiện cần provider/adapter có Responses API nếu muốn dùng kiểu OpenAI-compatible mới
- Lưu ý riêng cho Codex CLI: bản mới thường cần Responses API, không phải router nào có `/v1/chat/completions` cũng dùng trực tiếp được
- Checklist bảo mật API key: không paste key vào chat, README, issue, log hay screenshot

Lý do mình viết:

Rất nhiều tool CLI coding hiện nay rất mạnh, nhưng khi test nhiều model/provider thì cần hiểu rõ billing, quota và giới hạn sử dụng. Cách hợp lý hơn cho mục đích học tập và thử nghiệm cá nhân là tách CLI ra khỏi provider, dùng router/proxy local để đổi provider tùy quota, model, tốc độ và khả năng tool-calling.

Stack mình thấy đáng test nhất:

1. Claude Code + free-claude-code cho workflow Claude-style
2. FreeLLMAPI cho các CLI hỗ trợ OpenAI-compatible endpoint
3. Qwen Code + NVIDIA NIM để test trực tiếp model coding free-tier
4. Aider + FreeLLMAPI cho smoke test OpenAI-compatible đơn giản
5. OpenCode + FreeLLMAPI nếu khai báo provider/model trong `opencode.json`

Guide có kèm diagram, file `.env.example`, bảng so sánh, các lệnh PowerShell và phần lỗi thường gặp. Đây là kết quả test nhanh trên máy Windows thực tế, không phải benchmark chuẩn công nghiệp. Một số đường đã pass thật, một số đường được ghi rõ là chưa tương thích hoặc bị rate limit.

Kết quả test đáng chú ý:

- FreeLLMAPI chạy được với key Google/OpenRouter/NVIDIA healthy.
- Aider `0.86.2` qua FreeLLMAPI trả được `OK`.
- Qwen Code `0.16.0` đi thẳng NVIDIA NIM trả được `OK`.
- OpenCode `1.15.10` chạy được qua FreeLLMAPI sau khi thêm provider `freellmapi/gemini-2.5-flash`.
- OpenRouter free model có thể bị `429 rate-limited`, nên không nên lấy một model free làm chuẩn duy nhất.
- Qwen Code qua FreeLLMAPI hiện fail vì gửi `messages[].content` dạng content-parts array, trong khi router đang nhận string content.
- Crush trỏ vào FreeLLMAPI chưa chạy vì nó gọi `/v1/responses`, còn FreeLLMAPI expose `/v1/chat/completions`.

Mình muốn repo này thành tài liệu cộng đồng. Nếu anh em đã từng test các tool/provider/router mà bài viết chưa có, hoặc có kinh nghiệm hay hơn, hãy fork, mở issue hoặc gửi pull request.

Mình đặc biệt muốn nhận thêm:

- Cấu hình đã chạy thật với OpenRouter, NVIDIA NIM, Gemini, local model
- Model nào tool-calling ổn định cho coding agent
- Lỗi thường gặp khi dùng Codex CLI, Claude Code, Qwen Code, OpenCode, Aider, Crush
- Router/proxy hay hơn như 9Router, LiteLLM, CLIProxyAPI, custom adapter
- Benchmark trên repo thực tế

Quan trọng: bài này không khuyến khích né billing, vượt rate limit, tạo nhiều tài khoản để lạm dụng free tier, share key hay public proxy. Dùng free tier thì nên đọc ToS từng provider, chỉ chạy local/private, không dùng như production backend và không commit API key. Khi nhập key vào router/dashboard, chỉ dán raw key như `sk-or-v1-...`, `nvapi-...`, `AIza...`, không dán cả lệnh PowerShell kiểu `$env:OPENROUTER_API_KEY="..."`.
