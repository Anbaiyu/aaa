
# 对账匹配工具 · Tauri + NSIS（仅本地静态资源）

- 使用 Tauri 将 `app/` 下的静态页面封装为 EXE（NSIS 安装器），**不需要启动 dev 服务器**。
- `tauri.conf.json` ：`distDir` 与 `devPath` 均指向 `app/`，并在 HTML 中注入 `<base href="./">`，确保全部资源相对路径可用。
- 仅启用 **NSIS** 目标，绕过 WiX/MSI。

## 三步使用
1. **上传仓库**：把全部文件推送到 GitHub（默认分支 main 或 master）。
2. **运行 Actions**：仓库页 → Actions → 选择 “Build Tauri Windows (NSIS)” 工作流 → 运行（或推送即自动触发）。
3. **下载成品**：工作流完成后，在运行详情页的 Artifacts 下载 `.exe` 安装器。

> 本地构建（可选）：在 Windows 安装 Rust（MSVC），然后在仓库根目录执行：
>
> ```powershell
> cargo install tauri-cli --locked
> tauri build
> ```
> 产物位于 `src-tauri/target/release/bundle/nsis/`。
