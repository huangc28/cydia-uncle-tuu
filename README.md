# Cydia uncle-tuu extension

uncle-tuu 是一個使用 [Theos logos](https://github.com/theos/logos) 開發的遊戲物品出入庫插件. 買家可以

# Catalog

1. [Theos logos installation](#theos-logos-installation)
2. [Product collect plugin](https://github.com/huangc28/cydia-uncle-tuu/blob/master/product_collect.md)
3. [Product import plugin](https://github.com/huangc28/cydia-uncle-tuu/blob/master/import.md)
4. [Product export plugin](https://github.com/huangc28/cydia-uncle-tuu/blob/master/export.md)
5. Backend

# Theos Logos Installation

我是參考 [這篇 reddit thread](https://www.reddit.com/r/jailbreak/comments/839bnv/tutorial_how_to_get_into_tweak_development_for/) 在 mac 上 安裝 theos logos.  

1. Install prerequisites

`brew install ldid dpkg xz`

2. Installing Theos

Setup env variable for theos:

**.zshrc**

```
# Installation path doesn't have to be `/opt/theos`
export THEOS=/opt/theos

// Expose theos path to global $PATH
export PATH=$THEOS/bin:$PATH 

// inet IP of your jailbreak iphone 
export THEOS_DEVICE_IP={IP to your jailbreak phone}

// SSH port to iphone
export THEOS_DEVICE_PORT=22
```

once done, reload `.zshrc` by `source ~/.zshrc`

3.  

As the Substrate library does not come installed on these platforms nor bundled with Theos, copy /Library/Frameworks/CydiaSubstrate.framework/CydiaSubstrate from the device to your local $THEOS/lib folder and rename it to libsubstrate.dylib. (If you don't do this step, or if you use an old version of Substrate, or if something else goes wrong, you may get one of these error messages). Similarly, copy /Library/Frameworks/CydiaSubstrate.framework/Headers/CydiaSubstrate.h to your local $THEOS/include folder and rename it to substrate.h.

4. 

Your environment should be all set to run the extensions.

## Clone IOSGameItemVenorSharedLibrary

IOSGameItemVenorSharedLibrary 是一些 **import**, **export** 與 **inappcollect** 都會使用到的 library. 


```
git@github.com:huangc28/IOSGameItemVenorSharedLibrary.git
```

請將這個 library 跟其他 extension 放在同一層.

## Build and run extension 

在所有的 extension directory 裡面放一個 `.env` file with content:

```
API_HOST=https://atuuapi.darkpanda.love
```

Makesure your `THEOS_DEVICE_IP` is properly set in `.zshrc`  before building extension.

build cydia by executing `build.sh`: 

```sh
# build.sh reads and compiles API_HOST from .env to final bundle.
./build.sh
```

extension should then be built and and uploaded to device.

## 遊戲破解 

### 剝殼 (crack shell)

Before injecting our own hook logic to class method in game, we need to decipher game binary encrypted by apple. Based on the decrypted binary, we can then dump out class header files used by the game. We can then inject our own hook logic into the class method that we want by browsing through the header.
#### Cracker XI

This is by far the simplest way to crack game binary. Install crackerXI app from cydia then you can start cracking some shell from there.

### frida-ios-dump (python tool)

這個文章有介紹如何用 frida 雜殼:
[frida-ios-dump](https://medium.com/zrealm-ios-dev/ios-%E9%80%86%E5%90%91%E5%B7%A5%E7%A8%8B%E5%88%9D%E9%AB%94%E9%A9%97-7498e1ff93ce)

### Inject Hooks