# XHS-Easy-Crawler

一个基于 Chrome 扩展的小红书数据采集工具，采用模拟点击方式获取数据，无需担心反爬限制。

## 特点

- 🚀 基于 Chrome 扩展，使用简单
- 🛡️ 模拟真实用户行为，不会触发反爬措施
- 📦 自动化数据采集和处理
- 🔍 支持关键词搜索采集
- 💾 支持 HAR 文件导出和解析数据

## 工作原理

该工具通过模拟用户在小红书网页版的浏览行为来采集数据。使用 Chrome 扩展监控和记录网络请求，最后通过 Python 脚本处理导出的数据。

## 使用说明

### 前置要求

- Google Chrome 浏览器
- Python 3.6+
- 小红书账号

### 安装步骤

1. 克隆仓库

```bash
git clone https://github.com/leafiy/xhs_web_crawler
cd xhs-easy-crawler
```

2. 在 Chrome 中安装扩展
   - 打开 Chrome 扩展管理页面 (chrome://extensions/)
   - 启用开发者模式
   - 点击"加载已解压的扩展程序"
   - 选择项目中的 `chrome_extension` 文件夹
   - ![image](https://github.com/user-attachments/assets/30d2a0f4-90c0-4aac-be1f-3d4a963ed14a)


### 使用流程

1. **准备工作**

   - 打开小红书网页版 (https://www.xiaohongshu.com)
   - 登录您的账号
   - 打开 Chrome 开发者工具（F12）

2. **数据采集**

   - 在搜索框输入目标关键词
   - 点击扩展图标，打开控制面板
   - 点击"开始采集"按钮
   - 等待自动采集完成

3. **数据导出**

   - 在 Chrome 开发者工具的 Network 面板中
   - 右键点击并选择"Save all as HAR with content"
   - 保存生成的 .har 文件

4. **数据处理**

```bash
python extract-content.py
```

按提示输入 HAR 文件路径，程序将自动提取笔记数据并保存为 JSON 格式。

## 输出格式

提取的数据将保存为 JSON 文件，包含以下字段：

```json
[
  {
    "time": 1708778459000,
    "share_info": {
      "un_share": false
    },
    "type": "normal",
    "title": "9999",
    "user": {
      "user_id": "999",
      "nickname": "DOME",
      "avatar": "999",
      "xsec_token": "999="
    },
    "tag_list": [
      {
        "type": "topic",
        "id": "123",
        "name": "论文学习"
      }
    ],
    "at_user_list": [],
    "last_update_time": 1709233626000,
    "note_id": "7890",
    "desc": "78907890",
    "interact_info": {
      "collected": false,
      "collected_count": "123",
      "comment_count": "0",
      "share_count": "31",
      "followed": false,
      "relation": "none",
      "liked": false,
      "liked_count": "127"
    },
    "image_list": [
      {
        "width": 1179,
        "trace_id": "",
        "live_photo": false,
        "file_id": "",
        "height": 2007,
        "url": "",
        "info_list": [
          {
            "image_scene": "WB_PRV",
            "url": "123"
          },
          {
            "image_scene": "WB_DFT",
            "url": "123"
          }
        ],
        "url_pre": "123",
        "url_default": "123",
        "stream": {}
      }
    ]
  }
]
```

## 注意事项

- 请遵守小红书的使用条款和服务协议
- 建议控制爬取频率，避免对服务器造成压力
- 请合理使用采集到的数据，遵守相关法律法规
- 建议在使用前先进行小规模测试

## 常见问题

**Q: 为什么数据采集会暂停？**  
A: 可能是网络问题或页面加载延迟，请增加采集延迟

**Q: 如何设置采集的页数？**  
A: 不需要设置，会自动滚动页面

**Q: 数据解析出错怎么办？**  
A: 确保 HAR 文件完整且格式正确，如果问题持续，请提交 Issue。

## 许可证

[MIT License](LICENSE)

## 免责声明

本工具仅供学习和研究使用，请勿用于商业用途。对于使用本工具所产生的任何问题，作者不承担任何责任。
