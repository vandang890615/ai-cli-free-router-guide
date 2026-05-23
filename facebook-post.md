# Bài Đăng Facebook

Mình vừa dùng Codex để hỗ trợ test và tạo một guide cho anh em dev muốn thử các AI coding CLI với free-tier token:

Repo: https://github.com/vandang890615/ai-cli-free-router-guide

Nội dung chính:

- Claude Code + free-claude-code để route qua NVIDIA NIM, OpenRouter hoặc local model
- FreeLLMAPI để gom Google Gemini, NVIDIA, OpenRouter, GitHub Models... vào một endpoint OpenAI-compatible
- Qwen Code, OpenCode, Aider, Crush dùng với custom base URL
- Lưu ý riêng cho Codex CLI: bản mới thường cần Responses API, không phải router nào có `/v1/chat/completions` cũng dùng trực tiếp được
- Checklist bảo mật API key: không paste key vào chat, README, issue, log hay screenshot

Lý do mình viết:

Rất nhiều tool CLI coding hiện nay rất mạnh, nhưng chi phí token và billing mới là vấn đề khi dùng hằng ngày. Cách hợp lý hơn là tách CLI ra khỏi provider, dùng router/proxy để đổi provider tùy quota, model, tốc độ và khả năng tool-calling.

Stack mình thấy đáng test nhất:

1. Claude Code + free-claude-code cho workflow Claude-style
2. FreeLLMAPI cho các CLI hỗ trợ OpenAI-compatible endpoint
3. Qwen Code + NVIDIA NIM để test trực tiếp model coding free-tier
4. OpenCode/Aider/Crush + OpenRouter hoặc FreeLLMAPI

Guide có kèm diagram, file `.env.example`, bảng so sánh, các lệnh PowerShell và phần lỗi thường gặp. Đây là kết quả test nhanh trên máy Windows thực tế, không phải benchmark chuẩn công nghiệp.

Mình muốn repo này thành tài liệu cộng đồng. Nếu anh em đã từng test các tool/provider/router mà bài viết chưa có, hoặc có kinh nghiệm hay hơn, hãy fork, mở issue hoặc gửi pull request.

Mình đặc biệt muốn nhận thêm:

- Cấu hình đã chạy thật với OpenRouter, NVIDIA NIM, Gemini, local model
- Model nào tool-calling ổn định cho coding agent
- Lỗi thường gặp khi dùng Codex CLI, Claude Code, Qwen Code, OpenCode, Aider, Crush
- Router/proxy hay hơn như 9Router, LiteLLM, CLIProxyAPI, custom adapter
- Benchmark trên repo thực tế

Quan trọng: dùng free tier thì nên đọc ToS từng provider, chỉ chạy local/private, không public proxy và không commit API key.
