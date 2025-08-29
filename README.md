Period Tracker (离线可用)

一个单文件网页（index.html），用于记录经期/卵泡/排卵高峰/黄体，带心情与“月相”强度、肌肤文本+照片（本地保存）。支持多周期长期记录、阶段手动覆盖、摘要与预测（最近 6 次中位数）、备份导入/导出、PIN 加锁、.ics 导出、PWA 壳。

在线地址
	•	GitHub Pages：https://<你的用户名>.github.io/<你的仓库名>/

首次使用
	1.	用 Safari 打开站点 → 分享 → 添加到主屏幕（获得离线能力）。
	2.	进入设置区先设一个 PIN，再点一次 导出备份 存初始 JSON。

数据与隐私
	•	数据仅存在浏览器本地（IndexedDB + localStorage）。
	•	“导出备份”会包含图片（Base64）与所有记录；勿上传到公开仓库/云盘。

备份 / 恢复
	•	导出：设置区 → “导出备份”，得到 period-backup.json。
	•	导入：设置区 → “导入备份”，选择备份文件（会覆盖当前数据，导入前建议再导出一次以防回退）。

便捷打开导出的 JSON（只看内容，不改数据）

目标：快速预览/查看备份里的结构与关键字段，不把数据导入网页。

iPhone
	•	方式 A：在「文件」App 里直接点开 period-backup.json → 会用“快速查看（Quick Look）”显示纯文本。
	•	方式 B（更清晰，推荐做成一次性快捷指令）：
	1.	打开「快捷指令」→ 新建。
	2.	依次添加动作：获取文件（从“文件”选 JSON）→ 获取文件内容 → 从 JSON 获取字典 → 快速预览。
	3.	以后点这个快捷指令，选任意备份即可格式化查看（树状展示），不会修改网页数据。
	•	小技巧：只想临时看，用 长按文件 → 共享 → 拷贝到备忘录 也能阅读。

Android
	•	“文件”或任意文件管理器直接点开；或用 Chrome 打开本地文件（地址栏输入 file:///…），或安装任意 JSON Viewer App 预览。

桌面
	•	直接拖到 Chrome/Edge/Safari 窗口；或用 VS Code、Notepad++ 打开即可自动高亮与折叠。

备份结构说明（只读参考）：

{
  "db": {
    "profile": {"periodLength": 5, "cycleLength": 28},
    "cycles": [{"start":"YYYY-MM-DD","periodLength":5,"cycleLength":28}, ...],
    "notes": {
      "YYYY-MM-DD": {"mood":"🙂","moon":1..4,"skinText":"...","phase":"p|f|o|l","hasImg":true}
    }
  },
  "images": {"YYYY-MM-DD":"data:image/jpeg;base64,...", "...": "..."}
}



更新网页
	•	直接在 GitHub 编辑 index.html → Commit；等 ~30–60 秒生效。
	•	看不到更新：硬刷新或在地址后加 ?v=时间戳；必要时清理站点的网页数据再打开。

常见问题
	•	404：仓库必须 Public；Settings → Pages 里设置 Deploy from a branch: main / root；根目录需有 index.html。
	•	图片太大导出慢：页面已自动压缩到 ~1280px/82% JPEG；如仍大，可分阶段导出。
	•	换设备：新设备先打开站点，再“导入备份 JSON”。
