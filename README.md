# sing-box Remote Ruleset with Auto-update
> Based on [Toperlock' sing-box-geosite](https://github.com/Toperlock/sing-box-geosite), here's its [original README.md](#sing-box-geosite)
感谢[@Toperlock](https://github.com/Toperlock)搜集整理

利用Github Actions，定期自动生成 sing-box ruleset 规则集，从而实现远端自定义sing-box规则集(remote ruleset)的自动更新

# Usage
- Fork this repository, and enable the workflows at `Actions` -> `Workflows`
<blockquote>
For the 1st setup, you must manually trigger the workflow, after which it will run by schedule
<details>
<summary>About workflow setup file</summary>

Workflow is setup in [.github/workflows/sync.yml](.github/workflows/sync.yml), with at least 3 major steps:  
- Setup Python Runtime
- Run [main.py](main.py) script  
It integrates rule source specified at [links.txt](links.txt) and converted into JSON files that serves as sing-box remote ruleset sources
- Commit and push  
Commit change into this repository's code, so that all the generated ruleset can be served as raw files at **raw.githubusercontent.com**
</details>
</blockquote>

- Pick the rule under [rule/](rule/), and set it as a remote ruleset at your sing-box `config.json` as follows:
```json
{
  "tag": "geosite-wechat",
  "type": "remote",
  "format": "source",
  "url": "https://raw.githubusercontent.com/SmokedSalmon/sing-box-geosite/main/rule/WeChat.json",
  "download_detour": "auto"
}
```
or
```json
{
  "tag": "geosite-wechat",
  "type": "remote",
  "format": "source",
  "url": "https://raw.githubusercontent.com/SmokedSalmon/sing-box-geosite/main/rule/WeChat.json",
  "download_detour": "direct"
}
```
for China user
> the raw content are mirrored at [https://mirror.ghproxy.com](https://mirror.ghproxy.com), as shown above:  
https://raw.githubusercontent.com/SmokedSalmon/sing-box-geosite/main/rule/WeChat.json  
->  
https://mirror.ghproxy.com/https://raw.githubusercontent.com/SmokedSalmon/sing-box-geosite/main/rule/WeChat.json

## TODO
- Read and Integrate
[sing-box 1.8.0+版本迁移指南，Rule Set配置使用, 替代GeoIP/GeoSite](https://idev.dev/proxy/sing-box-rule-set.html)
- Read and extend usage of [Github Actions | Using Workflows](https://docs.github.com/en/actions/using-workflows)
- Figure out why Token or `{{ secret.GITHUB_TOKEN }}` is NOT needed for `github/action` bot to commit changes in workflow
<br />
<br />

↓ Original `README.md` ↓

---
# sing-box-geosite

在links.txt添加规则集，自动生成 sing-box Source Format。fork后自己添加想要转换的规则集，请生成token填写到仓库设置里让GitHub Actions有权限修改你的仓库

规则集源文件写法eg:

```json
{
  "tag": "geosite-wechat",
  "type": "remote",
  "format": "source",
  "url": "https://raw.githubusercontent.com/Toperlock/sing-box-geosite/main/wechat.json",
  "download_detour": "auto"
}
```

# 致谢（排名不分先后）

[@izumiChan16](https://github.com/izumiChan16)

[@ifaintad](https://github.com/ifaintad)

[@NobyDa](https://github.com/NobyDa)

[@blackmatrix7](https://github.com/blackmatrix7)

[@DivineEngine](https://github.com/DivineEngine)
