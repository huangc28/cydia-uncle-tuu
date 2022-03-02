
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

## Usage

After enter the game, go to product list and click on whatever product on the exhibition. If there is a stock available, the product will automatically exported to user account.

## How?

### Write receipt into AppStoreReceiptURL  

用戶購買完成後 app 都要 verify receipt , app 會從 `[[NSBundle mainBundle] appStoreReceiptURL]` path 中取得 receipt。所以我們把庫存中的 receipt 寫入到這個 path 裡來讓 app 取得這個 receipt 來 verify。應該要先把 receipt 寫入之後再執行 `SKPaymentObserver` 的 `paymentQueue:updatedTransactions` 方法。

### SKPaymentObserver hook method  

In the process of in app purchase, app has to add it's own `SKPaymentObserver` to `SKPaymentQueue` to observe the payment process. `StoreKit` would notify the observer for each status change via `paymentQueue:updatedTransactions` method. Our approach is to manually execute this method with our mocked `SKPaymentTransaction` which is the argument type of this method. For example:

```
Create mocked SKPaymentTransaction 
SKPaymentTransactions *transaction = [[SKPaymentTransactions alloc] init];

append mocked SKPaymentTransaction to array
NSArray *transArray = [[NSArray alloc] appendObject:transaction];

[observer paymentQueue:queue updatedTransactions:transArray]
```
