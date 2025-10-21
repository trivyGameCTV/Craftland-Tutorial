# Shop Config

Open *Module* -> *Economy* -> *CustomShop* -> *Edit*

Creator can adjust the shop by adding new guns or remove existing ones.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/shop.png">

# Developing Tutorial

## Create Shop UI
Create *PlayerShop.eca*

Init the Shop UI by using Built In UI. Bind the shop you have created in Module -> Economy.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/init-shop.png">

## Create Shop Icon UI
We need an Icon to open the shop.

Create *ShopIcon.ui*

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/shopIcon.png">

Create *ShopIconHUD.eca* and attach to *ShopIcon.ui*

Create a callback function, execute open shop UI whenever player click it. Bind it to the button

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/ShopIconHUD.png">

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/shop-icon-btn.png">
