
安裝此插件並登入後，使用者可以從倉庫出貨遊戲物品到支援的遊戲帳號中.
# Supported games

- 天堂M
- 天堂W
- 天堂2M
- 明日方舟
- 天涯明月刀
- 哈利波特
- 楓之谷R
- 放置英雄
- 天諭

# Installation

## Clone IOSGameItemVenorSharedLibrary

```
git@github.com:huangc28/IOSGameItemVenorSharedLibrary.git
```

Place it in siblings with extension directory 

## Clone extension project

```
git@github.com:huangc28/export.git 
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