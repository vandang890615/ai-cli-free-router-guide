# Bài Đăng Facebook

Mình vừa cập nhật lại guide test AI coding CLI/router sau khi tự dựng và test thêm combo local trên máy Windows:

Repo: https://github.com/vandang890615/ai-cli-free-router-guide

Nội dung mới đáng chú ý:

- Thêm Antigravity CLI: hướng đi mới thay cho Gemini CLI cá nhân/free theo thông báo chuyển đổi của Google.
- Thêm GitHub Copilot CLI mới: dùng `@github/copilot` hoặc `winget install GitHub.Copilot`, khác với `gh-copilot`/GitHub Next CLI cũ.
- Ghi rõ nên ngưng bắt đầu workflow mới bằng Gemini CLI cá nhân/free và Copilot CLI/extension cũ.
- Thêm combo local đã test: LM Studio + Qwen3-14B Q5_K_M + Open WebUI + Docker + Codex/CLI.
- Ghi rõ giới hạn thực tế: Open WebUI không tự web search realtime nếu lượt chat không bật Web Search; Qwen3 cần `/no_think` nếu muốn nhanh.
- Bổ sung bài viết dài: "Thời của crack đã chết: Kỷ nguyên của API, open source và tư duy đòn bẩy hệ thống".

Stack mình thấy đáng test nhất hiện tại:

1. Antigravity CLI cho hệ sinh thái Google/Gemini mới.
2. GitHub Copilot CLI mới nếu có Copilot subscription hoặc muốn thử BYOK/local model.
3. Codex/Claude Code cho workflow sửa code, chạy test, review diff nghiêm túc.
4. FreeLLMAPI cho các CLI hỗ trợ OpenAI-compatible `/v1/chat/completions`.
5. LM Studio + Open WebUI để học local LLM, test model, và chạy chat local.
6. Aider/OpenCode nếu muốn đường OpenAI-compatible đơn giản, dễ smoke test.

Kết quả test thực tế trên máy Windows:

- LM Studio chạy được Qwen3-14B Q5_K_M qua `http://127.0.0.1:1234/v1`.
- Open WebUI chạy Docker ở `http://127.0.0.1:3000`.
- Qwen3 tool calling cơ bản chạy được qua LM Studio API.
- Code prompt đơn giản qua local CLI phản hồi được khoảng vài giây, nhưng chưa mượt như cloud agent.
- Web search trong Open WebUI chỉ chạy khi request có `features.web_search=true`; gõ "hôm nay" không tự biến model local thành realtime search.
- FreeLLMAPI, Aider, Qwen Code, OpenCode vẫn giữ phần test/caveat cũ để ai cần router free-tier có chỗ đối chiếu.

Quan điểm chính của bài viết mới:

Thời của crack đã chết. Crack là tư duy tiết kiệm ngắn hạn nhưng rủi ro dài hạn: malware, mất source code, mất tài khoản, mất dữ liệu, đứng yên ở bản cũ. Thời mới là API, open source, local LLM, cloud agent và tư duy hybrid:

- Local core: giữ dữ liệu, script, workflow riêng, model local và router private.
- Cloud API: chỉ gọi khi cần model mạnh, context lớn, reasoning tốt hoặc integration chính thức.
- Open source: clone, test, tùy biến, đóng gói thành tài sản.
- API: lắp ghép dịch vụ để tạo workflow và sản phẩm nhanh hơn.

Điểm quan trọng không phải là dùng thật nhiều tool. Điểm quan trọng là biết biến tool thành đòn bẩy hệ thống: tự động hóa việc lặp lại, giảm giờ công, đóng gói thành SaaS nhỏ, script nội bộ, workflow chuyển đổi số hoặc sản phẩm bán được.

Repo vẫn giữ tinh thần responsible use:

- Không né billing, không vượt rate limit, không tạo nhiều tài khoản để lạm dụng free tier.
- Không public local proxy.
- Không commit API key.
- Không paste key vào chat, README, issue, log hoặc screenshot.
- Khi nhập key vào dashboard/router, chỉ dán raw key như `sk-or-v1-...`, `nvapi-...`, `AIza...`, không dán cả lệnh PowerShell.

Nếu anh em đã test Antigravity CLI, Copilot CLI mới, Codex, Claude Code, Qwen Code, OpenCode, Aider, LM Studio, Open WebUI, LiteLLM, 9Router hoặc router khác, có config chạy thật thì mở issue/PR để bổ sung.
