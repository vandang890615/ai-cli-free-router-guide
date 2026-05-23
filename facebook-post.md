# Facebook Post

Minh vua dung Codex de ho tro test va tao mot guide cho anh em dev muon test cac AI coding CLI voi free-tier token:

Repo: https://github.com/vandang890615/ai-cli-free-router-guide

Noi dung chinh:

- Claude Code + free-claude-code de route qua NVIDIA NIM, OpenRouter hoac local model
- FreeLLMAPI de gom Google Gemini, NVIDIA, OpenRouter, GitHub Models... vao mot endpoint OpenAI-compatible
- Qwen Code, OpenCode, Aider, Crush dung voi custom base URL
- Luu y rieng cho Codex CLI: ban moi thuong can Responses API, khong phai router nao co `/v1/chat/completions` cung dung truc tiep duoc
- Checklist bao mat API key: khong paste key vao chat, README, issue, log hay screenshot

Ly do minh viet:

Rat nhieu tool CLI coding hien nay rat manh, nhung chi phi token va billing moi la van de khi dung hang ngay. Cach hop ly hon la tach CLI ra khoi provider, dung router/proxy de chuyen provider tuy quota, model, toc do va kha nang tool-calling.

Stack minh thay dang test nhat:

1. Claude Code + free-claude-code cho workflow Claude-style
2. FreeLLMAPI cho cac CLI ho tro OpenAI-compatible endpoint
3. Qwen Code + NVIDIA NIM de test truc tiep model coding free-tier
4. OpenCode/Aider/Crush + OpenRouter hoac FreeLLMAPI

Guide co kem diagram, file `.env.example`, bang so sanh, cac lenh PowerShell va phan loi thuong gap. Day la ket qua test nhanh tren may Windows thuc te, khong phai benchmark chuan cong nghiep.

Minh muon repo nay thanh tai lieu cong dong. Neu anh em da tung test cac tool/provider/router ma bai viet chua co, hoac co kinh nghiem hay hon, hay fork, mo issue hoac gui pull request.

Minh dac biet muon nhan them:

- Cau hinh da chay that voi OpenRouter, NVIDIA NIM, Gemini, local model
- Model nao tool-calling on dinh cho coding agent
- Loi thuong gap khi dung Codex CLI, Claude Code, Qwen Code, OpenCode, Aider, Crush
- Router/proxy hay hon nhu 9Router, LiteLLM, CLIProxyAPI, custom adapter
- Benchmark tren repo thuc te

Quan trong: dung free tier thi nen doc ToS tung provider, chi chay local/private, khong public proxy va khong commit API key.
