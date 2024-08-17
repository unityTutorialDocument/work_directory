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

# 移動
Input 控制項 -> `` Edit->Project Setting->Input ``
將玩家的鋼體物件的位置 調整到新的vector 上即可完成移動。
```
void Movement()
    {
        float horizontalmove;
        horizontalmove=Input.GetAxis("Horizontal");

        if(horizontalmove !=0 )
        {
           Debug.Log(horizontalmove);
            rb.velocity=new Vector2(horizontalmove*speed,rb.velocity.y); // rb new position is on 
        }
       // Debug.Log(rb.velocity);
    }
```
# 開發:移動(自行優化)
這段代碼感覺可以優化成設置一份InputController
可以導入InputController
並且將玩家的鋼體傳入，並且以傳址的方式重新賦予玩家鋼體位置。

創立 InputController namespace 
代碼如下
```
using System.Collections; 
using System.Collections.Generic;
using UnityEngine;
/*
以上為了拿取 unity引擎的類型推斷(Rigidbody2D)
*/
namespace InputController{
	
	public class TheX{
		public static void Movement(Rigidbody2D rb,float speed)
		{
             float horizontalmove=Input.GetAxis("Horizontal");
			 if(horizontalmove!=0)
			 {
				 rb.velocity=new Vector2(horizontalmove*speed,rb.velocity.y);
			 }
		}

	} // end class
} // end namespace
```

玩家代碼重構:
```
using InputController;
 void Update()
{
    InputController.TheX.Movement(rb,speed);
}
```
現在只要 把自己的鋼體傳入，便可以在遊戲中進行互動。