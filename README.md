# ========================
# Clash-Fallback 优化配置
# ========================

# 机场节点订阅

proxy-providers:

  红杏云cloud:
    url: "https://api-hy.9527app.site/adf0b1976c43e82dab91f7c6e3b4d258?token=4146b6edfffcfb625043c8b2875d06bc"
    type: http
    interval: 86400
    override:
      additional-prefix: '[红杏云cloud]'
      skip-cert-verify: true
      udp: true
    health-check:
      enable: true
      url: https://www.gstatic.com/generate_204
      interval: 180  
    proxy: 直连 
    
  xiaoli07722:
    url: "https://cf077200.xiaoli07722.workers.dev/sub/c641df52-5daf-4b9c-9098-10069d101817"
    type: http
    interval: 86400
    override:
      additional-prefix: '[xiaoli07722]'
      skip-cert-verify: true
      udp: true
    health-check:
      enable: true
      url: https://www.gstatic.com/generate_204
      interval: 180
    proxy: 所有-自动    

  BPB面板:
    url: "https://pan0772200.xiaoli07722.workers.dev/sub/full-normal/52de2790-a903-4fcc-ba1f-c1310b214143?app=clash#%F0%9F%92%A6%20BPB%20Full%20Normal"
    type: http
    interval: 86400
    override:
      additional-prefix: '[BPB面板]'
      skip-cert-verify: true
      udp: true
    health-check:
      enable: true
      url: https://www.gstatic.com/generate_204
      interval: 180
    proxy: 直连    

  缥缈墟:
    url: "粘贴机场订阅地址"
    type: http
    interval: 86400
    override:
      additional-prefix: '[缥缈墟]'
      skip-cert-verify: true
      udp: true
    health-check:
      enable: true
      url: https://www.gstatic.com/generate_204
      interval: 180
    proxy: 直连        
  

proxies:
  - {name: 直连, type: direct}
  - {name: 拒绝, type: reject}

# ========================
# 主要端口设置
# ========================
port: 7890
socks-port: 7891
redir-port: 7892
mixed-port: 7893
tproxy-port: 7895

allow-lan: true
mode: rule
log-level: info

external-controller: 0.0.0.0:9090
external-ui: ui
external-ui-name: zashboard
external-ui-url: https://gh-proxy.com/github.com/Zephyruso/zashboard/archive/refs/heads/gh-pages.zip
secret: "123456"

# ========================
# DNS 设置
# ========================
dns:
  enable: true
  listen: 0.0.0.0:7874
  ipv6: true
  enhanced-mode: fake-ip
  fake-ip-range: 198.20.0.1/16
  nameserver:
    - 223.5.5.5
  fake-ip-filter:
    - +.lan
    - +.local
    - geosite:cn
    - +.ifaner.dd94wan.com

ipv6: true

# ========================
# TUN 模块
# ========================
tun:
  enable: true
  stack: gvisor
  device: utun
  endpoint-independent-nat: true
  auto-route: false
  auto-detect-interface: false
  auto-redirect: false
  strict-route: false

profile:
  store-selected: true
  store-fake-ip: true

# ========================
# 策略组定义
# ========================
default: &default
  type: select
  proxies:
    - 直连
    - 所有-手动
    - 所有-自动
    - 香港-故转
    - 台湾-故转
    - 日本-故转
    - 新加坡-故转
    - 韩国-故转
    - 美国-故转
    - 英国-故转
    - 其他地区-故转
    - 拒绝

proxy-groups:

  # 业务分流组
  - {name: ChatGPT, <<: *default, icon: "https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/ChatGPT.png"}
  - {name: GitHub, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/github.png"}
  - {name: Telegram, <<: *default, icon: "https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/telegram.png"}
  - {name: Twitter(X), <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/twitter.png"}
  - {name: WhatsApp, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/whatsapp.png"}
  - {name: Facebook, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/facebook.png"}
  - {name: Steam, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/steam.png"}
  - {name: Game, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/game.png"}
  - {name: YouTube, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/youtube.png"}
  - {name: TikTok, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/tiktok.png"}
  - {name: Disney, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/disney.png"}
  - {name: Netflix, <<: *default, icon: "https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/netflix.png"}
  - {name: HBO, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/hbo.png"}
  - {name: Spotify, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/spotify.png"}
  - {name: Crypto, <<: *default, icon: "https://raw.githubusercontent.com/Koolson/Qure/master/IconSet/Color/Cryptocurrency_2.png"}
  - {name: Amazon, <<: *default, icon: "https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/amazon.png"}
  - {name: Apple, <<: *default, icon: "https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/apple-light.png"}
  - {name: Microsoft, <<: *default, icon: "https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/microsoft.png"}
  - {name: Google, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/google.png"}
  - {name: Check, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/speedtest.png"}
  - {name: 国外, <<: *default, icon: "https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/rocket-earth.png"}
  - {name: 国内, <<: *default, icon: "https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/China.png"}
  - {name: 漏网之鱼, <<: *default, icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/final.png"}

  - name: 所有-手动
    icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/all.png"
    type: select
    include-all: true
    filter: "^((?!(直连|拒绝)).)*$"

  - name: 所有-自动
    icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/all.png"
    type: url-test
    include-all: true
    tolerance: 50
    interval: 180
    filter: "^((?!(直连|拒绝)).)*$"

  # 香港组
  - name: 香港-故转
    icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/Hongkong.png"
    type: fallback
    interval: 180
    lazy: false
    proxies:
      - 香港-手动
      - 香港-自动
  
  - name: 香港-手动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/iconselect96.png
    type: select
    include-all: true
    filter: "(?=.*(广港|香港|HK|Hong Kong|🇭🇰|HongKong)).*$"
    
  - name: 香港-自动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/auto.png
    type: url-test
    include-all: true
    tolerance: 50
    interval: 180
    filter: "(?=.*(广港|香港|HK|Hong Kong|🇭🇰|HongKong)).*$"
 
  # 台湾组
  - name: 台湾-故转
    icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/Taiwan_China.png"
    type: fallback
    interval: 180
    lazy: false
    proxies:
      - 台湾-手动
      - 台湾-自动
  - name: 台湾-手动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/iconselect96.png
    type: select
    include-all: true
    filter: "(?=.*(广台|台湾|台灣|TW|Tai Wan|🇹🇼|🇨🇳|TaiWan|Taiwan)).*$"
  - name: 台湾-自动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/auto.png
    type: url-test
    include-all: true
    tolerance: 50
    interval: 180
    filter: "(?=.*(广台|台湾|台灣|TW|Tai Wan|🇹🇼|🇨🇳|TaiWan|Taiwan)).*$"

  # 日本组
  - name: 日本-故转
    icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/Japan.png"
    type: fallback
    interval: 180
    lazy: false
    proxies:
      - 日本-手动
      - 日本-自动
  - name: 日本-手动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/iconselect96.png
    type: select
    include-all: true
    filter: "(?=.*(广日|日本|JP|川日|东京|大阪|泉日|埼玉|沪日|深日|🇯🇵|Japan)).*$"
  - name: 日本-自动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/auto.png
    type: url-test
    include-all: true
    tolerance: 50
    interval: 180
    filter: "(?=.*(广日|日本|JP|川日|东京|大阪|泉日|埼玉|沪日|深日|🇯🇵|Japan)).*$"

  # 新加坡组
  - name: 新加坡-故转
    icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/Singapore.png"
    type: fallback
    interval: 180
    lazy: false
    proxies:
      - 新加坡-手动
      - 新加坡-自动
  - name: 新加坡-手动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/iconselect96.png
    type: select
    include-all: true
    filter: "(?=.*(广新|新加坡|SG|坡|狮城|🇸🇬|Singapore)).*$"
  - name: 新加坡-自动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/auto.png
    type: url-test
    include-all: true
    tolerance: 50
    interval: 180
    filter: "(?=.*(广新|新加坡|SG|坡|狮城|🇸🇬|Singapore)).*$"

  # 韩国组
  - name: 韩国-故转
    icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/Korea.png"
    type: fallback
    interval: 180
    lazy: false
    proxies:
      - 韩国-手动
      - 韩国-自动
  - name: 韩国-手动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/iconselect96.png
    type: select
    include-all: true
    filter: "(?=.*(广韩|韩国|韓國|KR|首尔|春川|🇰🇷|Korea)).*$"
  - name: 韩国-自动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/auto.png
    type: url-test
    include-all: true
    tolerance: 50
    interval: 180
    filter: "(?=.*(广韩|韩国|韓國|KR|首尔|春川|🇰🇷|Korea)).*$"

  # 美国组
  - name: 美国-故转
    icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/America.png"
    type: fallback
    interval: 180
    lazy: false
    proxies:
      - 美国-手动
      - 美国-自动
  - name: 美国-手动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/iconselect96.png
    type: select
    include-all: true
    filter: "(?=.*(广美|美|US|纽约|波特兰|达拉斯|俄勒|凤凰城|费利蒙|拉斯|洛杉|圣何塞|圣克拉|西雅|芝加|🇺🇸|United States)).*$"
  - name: 美国-自动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/auto.png
    type: url-test
    include-all: true
    tolerance: 50
    interval: 180
    filter: "(?=.*(广美|美|US|纽约|波特兰|达拉斯|俄勒|凤凰城|费利蒙|拉斯|洛杉|圣何塞|圣克拉|西雅|芝加|🇺🇸|United States)).*$"

  # 英国组
  - name: 英国-故转
    icon: "https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/uk.png"
    type: fallback
    interval: 180
    lazy: false
    proxies:
      - 英国-手动
      - 英国-自动
  - name: 英国-手动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/iconselect96.png
    type: select
    include-all: true
    filter: "(?=.*(英国|英|伦敦|UK|United Kingdom|🇬🇧|London)).*$"
  - name: 英国-自动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/auto.png
    type: url-test
    include-all: true
    tolerance: 50
    interval: 180
    filter: "(?=.*(英国|英|伦敦|UK|United Kingdom|🇬🇧|London)).*$"

  # 其他地区组
  - name: 其他地区-故转
    icon: "https://raw.githubusercontent.com/Lanlan13-14/Rules/refs/heads/main/icon/European.png"
    type: fallback
    interval: 180
    lazy: false
    proxies:
      - 其他地区-手动
      - 其他地区-自动
  - name: 其他地区-手动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/iconselect96.png
    type: select
    include-all: true
    filter: "^((?!(直连|拒绝|广港|香港|HK|Hong Kong|🇭🇰|HongKong|广台|台湾|台灣|TW|Tai Wan|🇹🇼|🇨🇳|TaiWan|Taiwan|广日|日本|JP|川日|东京|大阪|泉日|埼玉|沪日|深日|🇯🇵|Japan|广新|新加坡|SG|坡|狮城|🇸🇬|Singapore|广韩|韩国|韓國|KR|首尔|春川|🇰🇷|Korea|广美|美|US|纽约|波特兰|达拉斯|俄勒|凤凰城|费利蒙|拉斯|洛杉|圣何塞|圣克拉|西雅|芝加|🇺🇸|United States|英国|UK|United Kingdom|伦敦|英|London|🇬🇧)).)*$"
  - name: 其他地区-自动
    icon: https://raw.githubusercontent.com/ifanrBook/ClashConfig/refs/heads/main/icon/auto.png
    type: url-test
    include-all: true
    tolerance: 50
    interval: 180
    filter: "^((?!(直连|拒绝|广港|香港|HK|Hong Kong|🇭🇰|HongKong|广台|台湾|台灣|TW|Tai Wan|🇹🇼|🇨🇳|TaiWan|Taiwan|广日|日本|JP|川日|东京|大阪|泉日|埼玉|沪日|深日|🇯🇵|Japan|广新|新加坡|SG|坡|狮城|🇸🇬|Singapore|广韩|韩国|韓國|KR|首尔|春川|🇰🇷|Korea|广美|美|US|纽约|波特兰|达拉斯|俄勒|凤凰城|费利蒙|拉斯|洛杉|圣何塞|圣克拉|西雅|芝加|🇺🇸|United States|英国|UK|United Kingdom|伦敦|英|London|🇬🇧)).)*$"

# ========================
# 规则引擎（rules）
# ========================
rules:

  - RULE-SET,Check / Domain,Check  
  - RULE-SET,ChatGPT / Domain,ChatGPT
  - RULE-SET,Claude / Domain,ChatGPT
  - RULE-SET,Meta AI / Domain,ChatGPT
  - RULE-SET,Perplexity / Domain,ChatGPT
  - RULE-SET,Gemini / Domain,ChatGPT
  - RULE-SET,Copilot / Domain,ChatGPT
  - RULE-SET,AI / Domain,ChatGPT
  - RULE-SET,GitHub / Domain,GitHub
  - RULE-SET,Telegram / Domain,Telegram
  - RULE-SET,Telegram / IP,Telegram,no-resolve
  - RULE-SET,Twitter / Domain,Twitter(X)
  - RULE-SET,WhatsApp / Domain,WhatsApp
  - RULE-SET,Facebook / Domain,Facebook
  - RULE-SET,Amazon / Domain,Amazon
  - RULE-SET,Apple / Domain,Apple
  - RULE-SET,Apple-CN / Domain,Apple  
  - RULE-SET,Microsoft / Domain,Microsoft
  - RULE-SET,OKX / Domain,Crypto
  - RULE-SET,Bybit / Domain,Crypto
  - RULE-SET,Binance / Domain,Crypto
  - RULE-SET,crypto_domain,Crypto
  - RULE-SET,Youtube / Domain,YouTube
  - RULE-SET,TikTok / Domain,TikTok
  - RULE-SET,Netflix / Domain,Netflix
  - RULE-SET,Netflix / IP,Netflix,no-resolve
  - RULE-SET,Disney / Domain,Disney
  - RULE-SET,HBO / Domain,HBO
  - RULE-SET,Spotify / Domain,Spotify
  - RULE-SET,Steam / Domain,Steam
  - RULE-SET,Epic / Domain,Game
  - RULE-SET,EA / Domain,Game
  - RULE-SET,Blizzard / Domain,Game
  - RULE-SET,UBI / Domain,Game
  - RULE-SET,PlayStation / Domain,Game
  - RULE-SET,Nintend / Domain,Game
  - RULE-SET,Google / Domain,Google
  - RULE-SET,Google / IP,Google,no-resolve
  - RULE-SET,Proxy / Domain,国外
  - RULE-SET,Globe / Domain,国外  
  - RULE-SET,Direct / Domain,国内
  - RULE-SET,China / Domain,国内
  - RULE-SET,China / IP,国内,no-resolve
  - RULE-SET,Private / Domain,国内
  - MATCH,漏网之鱼

# ========================
# 规则集提供者
# ========================
rule-anchor:
  ip: &ip {type: http, interval: 86400, behavior: ipcidr, format: mrs}
  domain: &domain {type: http, interval: 86400, behavior: domain, format: mrs}
  class: &class {type: http, interval: 86400, behavior: classical, format: text}

rule-providers:
  Check / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/liandu2024/clash/refs/heads/main/list/Check.list"}
  ChatGPT / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/openai.mrs"}
  Claude / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/blackmatrix7/ios_rule_script/refs/heads/master/rule/Clash/Claude/Claude.list"}
  Meta AI / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/liandu2024/clash/refs/heads/main/list/MetaAi.list"}
  Perplexity / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/perplexity.mrs"}
  Copilot / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/liandu2024/clash/refs/heads/main/list/Copilot.list"}
  Gemini / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/liandu2024/clash/refs/heads/main/list/Gemini.list"}
  AI / Domain: {<<: *domain, url: "https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/meta/geo/geosite/category-ai-!cn.mrs"}
  GitHub / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/github.mrs"}
  Telegram / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/telegram.mrs"}  
  Telegram / IP: {<<: *ip, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geoip/telegram.mrs"}
  Twitter / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/x.mrs"}
  WhatsApp / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/blackmatrix7/ios_rule_script/refs/heads/master/rule/Clash/Whatsapp/Whatsapp.list"}
  Facebook / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/facebook.mrs"}
  Amazon / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/amazon.mrs"}
  Apple-CN / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/apple-cn.mrs"}
  Apple / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/apple.mrs"} 
  Microsoft / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/microsoft.mrs"}
  OKX / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/okx.mrs"}
  Bybit / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/bybit.mrs"}
  Binance / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/binance.mrs"}
  crypto_domain: { <<: *domain, url: "https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/meta/geo/geosite/category-cryptocurrency.mrs" }
  TikTok / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/tiktok.mrs"}
  Netflix / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/netflix.mrs"}
  Netflix / IP: {<<: *ip, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geoip/netflix.mrs"}
  Disney / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/disney.mrs"}
  HBO / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/hbo.mrs"}
  Spotify / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/spotify.mrs"}
  Steam / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/steam.mrs"}
  Epic / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Epic/Epic.list"}
  EA / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/EA/EA.list"}
  Blizzard / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Blizzard/Blizzard.list"}
  UBI / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/UBI/UBI.list"}
  PlayStation / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/blackmatrix7/ios_rule_script/refs/heads/master/rule/Clash/PlayStation/PlayStation.list"}
  Nintend / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Nintendo/Nintendo.list"}
  Proxy / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/liandu2024/clash/refs/heads/main/list/Proxy.list"}
  Globe / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/blackmatrix7/ios_rule_script/refs/heads/master/rule/Clash/Global/Global.list"} 
  Direct / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/liandu2024/clash/refs/heads/main/list/Direct.list"}
  China / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/cn.mrs"}
  China / IP: {<<: *ip, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geoip/cn.mrs"}
  Private / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/private.mrs"}
  Nvidia / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/blackmatrix7/ios_rule_script/refs/heads/master/rule/Clash/Nvidia/Nvidia.list"}
  Crunchyroll / Domain: {<<: *class, url: "https://gh-proxy.com/raw.githubusercontent.com/liandu2024/clash/refs/heads/main/list/Crunchyroll.list"}
  Reddit / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/reddit.mrs"}

  Youtube / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/youtube.mrs"}  
  Google / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/google.mrs"}  
  Google / IP: {<<: *ip, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geoip/google.mrs"}
  facebook_ip: { <<: *ip, url: "https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/meta/geo/geoip/facebook.mrs" }
  twitter_ip: { <<: *ip, url: "https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/meta/geo/geoip/twitter.mrs" }
  private_ip: { <<: *ip, url: "https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/refs/heads/meta/geo/geoip/private.mrs" }
# GateFireWall / Domain: {<<: *domain, url: "https://gh-proxy.com/github.com/metacubex/meta-rules-dat/raw/refs/heads/meta/geo/geosite/gfw.mrs"}

