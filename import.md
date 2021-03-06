此插件提供倉庫的介面. 包含以下功能:

- Purchase in game item and import receipt to DB without notifying game about item purchased.
- List of items failed to import to DB but has purchased successfully
- Purchase history of current account.
# Supported games

- 天堂M
- 天堂W
- 天堂2M
- 明日方舟
- 最強蝸牛
- 天涯明月刀
- 哈利波特
- 楓之谷R
- 放置英雄

# Installation

## Clone IOSGameItemVenorSharedLibrary

```
git@github.com:huangc28/IOSGameItemVenorSharedLibrary.git
```

Place it in siblings with extension directory 

## Clone extension project

```
git@github.com:huangc28/import.git 
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

## Usage 

安裝 extension 後，只要打開有支援的遊戲，就會跳出入庫介面。登入阿土伯帳號後即可開始入庫。