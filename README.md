# Cydia uncle-tuu extension

uncle-tuu 是一個使用 [Theos logos](https://github.com/theos/logos) 開發的遊戲物品出入庫插件. 買家可以

# Catalog

1. [Theos logos installation](#theos-logos-installation)
2. Product collect plugin
3. Product Import plugin
4. Product Export plugin
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
export THEOS_DEVICE_IP={IP to to your jailbreak phone}

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

```
./build.sh
```

extension should then be built and and uploaded to device.