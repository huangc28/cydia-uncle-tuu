此插件可以採集遊戲中的遊戲資訊其中包含 product uuid. product uuid 是入庫插件用來跟 apple 購買商品入到倉庫用.

# Supported games

- 天堂M
- 天堂W
- 天堂2M
- 放置英雄
- 明日方舟
- 最強蝸牛
- 天涯明月刀
- 哈利波特
- 楓之谷R
- 放置英雄
- 天地劫
- 三國志霸道
- 二之國
- 叫我大掌櫃

# Installation
## Clone IOSGameItemVenorSharedLibrary

```
git@github.com:huangc28/IOSGameItemVenorSharedLibrary.git
```

Place it in siblings with extension directory 

## Clone extension project

```
git@github.com:huangc28/inappcollect.git 
```

fetch all submodules:

```
cd inappcollect && git submodule update --recursive --remote
```

## Build and run 

Create a `.env` file with content:

```
API_HOST=https://atuuapi.darkpanda.love
```

Makesure your `THEOS_DEVICE_IP` is properly set in `.zshrc`  before building extension.

build with:

```
./build.sh
```