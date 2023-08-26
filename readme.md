# 介紹目錄結構，此目錄結構並未完整整理，僅供教學使用。

## 目錄結構皆是素材包和unity自動生成。
```
├─Assets
│  ├─Scenes
│  └─SunnyLand Artwork
│      ├─Environment
│      │  ├─props
│      │  └─Tileset
│      ├─Music tracks
│      ├─Scenes
│      └─Sprites
│          ├─Enemies
│          │  ├─bat
│          │  │  ├─bat-fly
│          │  │  └─bat-hang
│          │  ├─bear
│          │  ├─Bettle
│          │  ├─bunny
│          │  ├─Dino
│          │  ├─Dino-Idle
│          │  ├─Dog
│          │  ├─Dog-idle
│          │  ├─eagle
│          │  ├─Eagle Dive Attack
│          │  ├─Eagle Hurt
│          │  ├─frog
│          │  │  ├─idle
│          │  │  └─jump
│          │  ├─opossum
│          │  ├─pig
│          │  ├─Slimer
│          │  ├─Slimer-Idle
│          │  ├─Vulture
│          │  └─Vulture-Idle
│          ├─Fx
│          │  ├─enemy-death
│          │  └─item-feedback
│          ├─Items
│          │  ├─cherry
│          │  └─gem
│          └─player
│              ├─climb
│              ├─crouch
│              ├─hurt
│              ├─idle
│              ├─jump
│              └─run
├─ other Directory....
```
# 目錄結構一:Assets
``
~/.Assets/Scenes -> 世界場景
``

``
~/.Assets/* -> 插件、素材包集合
``

# sunnyland(一般素材包)

## sunnyland/environment 建立環境

## 操作介紹: 右上角都可以把顯示先關掉，有助於我們調整素材。
``
back.png->背景 請先調整背景像素 pixels Per unit -16
``

``
tileset.png -> window->2D->Tile Palette 可以將tilset放進Tile Palette中
``

先創立一個``tileMap`` 2D->tileMap->Rectangular，將視圖切割成網格狀

至此可以開始使用 Tile Palette 的筆刷工具繪製2D地圖。

## sunnyland/sprites/player 開始創立玩家
1. ``2D->sprite`` 建立物件，並拖拽player idle到 2D物件上
2. 增加 rigidbody 2D 、box collider 2D 並調整collider 碰撞範圍
3. tileMap 設定 tile collider 2D