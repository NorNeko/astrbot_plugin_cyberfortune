# astrbot_cyberfortune

**基于Xbodwf大佬的astrbot每日运势插件项目改版**

一个使用方法简单但是可调内容丰富的今日运势插件，旨在为用户提供精美的二次元风格运势图片。

源仓库地址：https://github.com/Xbodwf/astrbot_plugin_fortnue

# 使用
```plaintext
/今日运势
/运势
/jrys
```
均可触发。

![示意图](_README.Assets/p02.png)
![示意图](_README.Assets/p01.png)

# 区分

相较于原版添加了更多当日运势可供抽取.

添加了vip用户，在配置文件中可以自由添加vip用户的QQ账号，
并可以为vip设置0-100的幸运值保底，使得抽取到的幸运值不会低于保底。

添加了管理员账号，可以通过指令清除指定账号当日的抽取结果以重新抽取。

修改了种子逻辑，以便可以重新抽取到新的随机值，但也保留当日幸运值在清除前不会变动。

添加插件自检测功能，方便后续自行修改时检查声明与传递量正常。

可自行在fortune_data.json文档中修改抽签运势信息。

修改内容100%由Google Gemini 3 pro提供，写错乱写请指正。

# 安装（与源项目相同）

## 插件市场 (推荐)
在 AstrBot 插件市场搜索 `astrbot_cyberfortune` 即可一键安装。（等待审核中，暂未上架）

## 源码安装
1. 进入 AstrBot 的插件目录：
   ```bash
   cd {AstrBot安装目录}/data/plugins
   ```
2. 克隆仓库：
   ```bash
   git clone https://github.com/NorNeko/astrbot_cyberfortune.git
   ```
3. 安装依赖：
   ```bash
   cd astrbot_astrbot_cyberfortune
   pip install -r requirements.txt
   ```
4. 重启 AstrBot。

# 指令说明

| 指令 | 说明 | 示例 |
| :--- | :--- | :--- |
| `/jrys` | 生成今日运势图片 | `/jrys` |
| `/jrysl source <图源名称>` | 指定图源生成运势 | `/jrysl source pixiv` |
| `/jrysl last` | 获取上一张生成的运势背景图 (原图) | `/jrysl last` |
| `/jrysn` | 随机从图源中获取一张背景图 (无运势信息) | `/jrysn` |
| `/jrysl none source <图源名称>` | 从指定图源获取背景图 | `/jrysl none source pixiv` |
| `/jrysd <账号>` | [管理员] 清除指定用户的今日运势记录。 | `/jrysd 123456` |
| `/jryscfg` | 插件自检测，方便后续修改时检查声明与传递量。 | `/jryscfg` |
# 图源配置指南（与源项目相同）

参见https://github.com/Xbodwf/astrbot_plugin_fortnue?tab=readme-ov-file#%E5%9B%BE%E6%BA%90%E9%85%8D%E7%BD%AE%E6%8C%87%E5%8D%97

# 配置项说明 (config.json)（与源项目相同）

在 AstrBot 管理面板或 `config.json` 中可以配置以下项：
- `proxy`: 网络代理地址 (如 `http://127.0.0.1:7890`)。
- `image_quality`: 输出图片的 JPEG 质量 (1-100)。

# 变更日志

### [v1.1.0] - 2026-02-14
- **安全修复**：增加了 `_is_safe_url` 拦截机制，防止 SSRF 任意 URL 访问漏洞及内网探测风险。
- 
- **安全修复**：重写了 `_safe_fetch` 异步下载引擎，增加 `MAX_DOWNLOAD_SIZE` 限制 (默认15MB) 与分块读取机制，防止超大文件导致的内存 OOM (DoS) 攻击。
- 
- **安全修复**：禁用了自动重定向，改为手动校验重定向 URL，防止重定向跳板绕过安全策略。
