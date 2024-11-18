# Input System - User Manual

The input system is a default module that allows you to remap game controls by modifying the input system configuration

![image-21-1](./img/image-21-1.png)

# Input System - User Manual

The input system is a default module that allows you to remap game controls by modifying the input system configuration

![image-21-2](./img/image-21-2.png)

You can control the visibility of these in-game universal buttons through scripts: 

![image-21-3](./img/image-21-3.png)

{
  "type": "a",
  "id": "A5dC35^!WzQibCaFKtGx",
  "extraState": {
    "X": 528,
    "L": [
      1,
      2,
      3
    ],
    "T": "SetPlayerHubSwitch",
    "OT": null
  },
  "inputs": {
    "P1": {
      "shadow": {
        "type": "tys",
        "id": "yQYArCczLxf9yw3FNXAT",
        "extraState": "Player"
      }
    },
    "P2": {
      "shadow": {
        "type": "ipe",
        "id": "-)h5GeGgU0{HBI{KpY[.",
        "extraState": "PlayerHudSwitchType",
        "fields": {
          "I": "MovementHUD"
        }
      }
    },
    "P3": {
      "shadow": {
        "type": "ipe",
        "id": "Spr.Q/3v;moE6P^U%6x2",
        "extraState": "CommonHudSwitchValue",
        "fields": {
          "I": "Close"
        }
      }
    }
  }
}

## Custom Input System

In the input system, you can add or remove an input:

![image-21-4](./img/image-21-4.png)

For an input, you can choose the input type as keyboard, mouse, or UI file.

### Keyboard and Mouse

Keyboard and mouse inputs are currently only effective during PC Debug and will not be introduced here.

### Custom UI

For custom maps, in-game operations are primarily remapped through custom UI.

![image-21-5](./img/image-21-5.png)

In the input system, you can bind an input to a control on the custom UI, allowing you to use the custom UI controls to perform operations. This will help you create unique game modes or other scenarios where you want to change player inputs.

### How to Configure Custom Input

Taking custom UI as an example, you first need to prepare a custom UI for custom input.

![image-21-6](./img/image-21-6.png)

We create a UI with only one button under this custom UI, intending for this button to make the player move forward.

![image-21-7](./img/image-21-7.png)

Add a new input in the input system module.

![image-21-8](./img/image-21-8.png)

Select the mapping operation as forward, type as UI file, choose the previously created custom UI and button, and set the input gesture to hold.

![image-21-9](./img/image-21-9.png)

Create a custom UI for the player; this element script is created on the global module.

![image-21-10](./img/image-21-10.png)

{
  "type": "e",
  "id": "*%pI`W(dS_piURm|VMA!",
  "extraState": {
    "X": 14,
    "L": [
      1
    ],
    "T": "OnPlayerAdd",
    "OT": null
  },
  "fields": {
    "P1": {
      "name": "Player",
      "type": "Player"
    }
  },
  "next": {
    "block": {
      "type": "a",
      "id": "rk0cKIssMKf0cmAf5K1b",
      "extraState": {
        "X": 34,
        "L": [
          1,
          2,
          3
        ],
        "T": "CreateCustomHud",
        "OT": null
      },
      "fields": {
        "P1": {
          "name": "Created Entity",
          "type": "CustomHud"
        }
      },
      "inputs": {
        "P2": {
          "shadow": {
            "type": "tys",
            "id": "zCSt9:DaP7Fym?RosxoY",
            "extraState": "Player"
          },
          "block": {
            "type": "lcg",
            "id": "9f?Pdkf6=$dO1G6psZ?%",
            "extraState": "*%pI`W(dS_piURm|VMA!P1",
            "fields": {
              "VR": "Player"
            }
          }
        },
        "P3": {
          "shadow": {
            "type": "pkh",
            "id": "bjBa_(1|Qv}i=[l#w=p7",
            "fields": {
              "HD": "02xr50iei5df-m11x1qdn-kqt9qw8jx19"
            }
          }
        }
      }
    }
  }
}

Launch the game to find that this button's function is now working properly.

![image-21-11](./img/image-21-11.png)
