# mercy-labs
    This script was developed using mercy-framework, so it works on mercy-framework. 
    Follow the instructions for proper installation.

## Dependencies
- [mercy-framework](https://github.com/Mercy-Collective/mercy-framework)

## Screenshots
- Server side fuse
![Insurance](https://i.imgur.com/zCy1fy0.jpg)

- Many stages
![Many Stages](https://i.imgur.com/QIK4mbf.jpg)

## Features
- Machines that can be locked and unlocked
- Many types of drugs that can be added
- Can be configured according to your dreams

## Installation
### Manual
- Download the files and put them in the "resources\[mercy]\mercy-illegal" directory
- Add to the sh_config file inside the mercy-illegal file
```
    Config.LabsState = {
        [1] = false,
        [2] = false,
        [3] = false,
        [4] = false
    }
```
- These ids can be increased when necessary
- Required items for the lab with default settings
```
Shared.ItemList["methkey1"] = {
	['ItemName'] = "methkey1",
	['Label'] = "meth Key1",
	['Weight'] = 11.5,
	['Type'] = "Item",
	['Metal'] = false,
	['Image'] = "key.png",
	['Unique'] = true,
	['Combinable'] = false,
	['Description'] = "Sanırım bunu açacakkapıyı bulmalıyım...",
	['DecayRate'] = 0.1,
	['RemoveWhenDecayed'] = false,
	['Price'] = nil,
}
Shared.ItemList["cleaningproduct"] = {
	['ItemName'] = "cleaningproduct",
	['Label'] = "Cleaning Product",
	['Weight'] = 0.10,
	['Type'] = "Item",
	['Metal'] = false,
	['Image'] = "m_cleaningproduct.png",
	['Unique'] = false,
	['Combinable'] = nil,
	['Description'] = "Cleans n shit yo",
	['DecayRate'] = 0.01,
	['RemoveWhenDecayed'] = false,
	['Price'] = 240,
}
Shared.ItemList["xmadde"] = {
	['ItemName'] = "xmadde",
	['Label'] = "X",
	['Weight'] = 0.10,
	['Type'] = "Item",
	['Metal'] = false,
	['Image'] = "X.png",
	['Unique'] = false,
	['Combinable'] = nil,
	['Description'] = "X ?",
	['DecayRate'] = 0.01,
	['RemoveWhenDecayed'] = false,
	['Price'] = 240,
}
Shared.ItemList["mixidacid"] = {
	['ItemName'] = "mixidacid",
	['Label'] = "Mixid Acid",
	['Weight'] = 0.10,
	['Type'] = "Item",
	['Metal'] = false,
	['Image'] = "mixed_acid.png",
	['Unique'] = false,
	['Combinable'] = nil,
	['Description'] = "Doesn't look drinkable",
	['DecayRate'] = 0.01,
	['RemoveWhenDecayed'] = false,
	['Price'] = 240,
}
Shared.ItemList["methbrick"] = {
	['ItemName'] = "methbrick",
	['Label'] = "meth brick",
	['Weight'] = 1.5,
	['Type'] = "Item",
	['Metal'] = false,
	['Image'] = "c_methbrick.png",
	['Unique'] = false,
	['Combinable'] = nil,
	['Description'] = "Grow my youngling!",
	['DecayRate'] = 0.1,
	['RemoveWhenDecayed'] = false,
	['Price'] = 1,
}
Shared.ItemList["methcured"] = {
	['ItemName'] = "methcured",
	['Label'] = "meth cured",
	['Weight'] = 1.5,
	['Type'] = "Item",
	['Metal'] = false,
	['Image'] = "c_methcured.png",
	['Unique'] = false,
	['Combinable'] = nil,
	['Description'] = "Grow my youngling!",
	['DecayRate'] = 0.1,
	['RemoveWhenDecayed'] = false,
	['Price'] = 1,
}
Shared.ItemList["methbatch"] = {
	['ItemName'] = "methbatch",
	['Label'] = "meth batch",
	['Weight'] = 0.10,
	['Type'] = "Item",
	['Metal'] = false,
	['Image'] = "m_methbatch.png",
	['Unique'] = false,
	['Combinable'] = nil,
	['Description'] = "Why is this empty?",
	['DecayRate'] = 0.0,
	['RemoveWhenDecayed'] = false,
	['Price'] = 8,
}
Shared.ItemList["methbag"] = {
	['ItemName'] = "methbag",
	['Label'] = "meth bag",
	['Weight'] = 0.10,
	['Type'] = "Item",
	['Metal'] = false,
	['Image'] = "m_methbag.png",
	['Unique'] = false,
	['Combinable'] = nil,
	['Description'] = "Why is this empty?",
	['DecayRate'] = 0.0,
	['RemoveWhenDecayed'] = false,
	['Price'] = 8,
}
```

## Configuration

- You can define the items of the stages created for the beginning on your server and place them in places where you can test them by configuring the vector3 coordinates I have set.
- To produce your own special drug, you must create 6 separate stages as exemplified and define the items of these stages on your server.
- There must be a separate key item (example: methkey1) for each laboratory.
- For each lab you create, you must match an id in the config file
```
    exports['mercy-ui']:AddEyeEntry("meth_lab_open_close", {
        Type = 'Zone',
        SpriteDistance = 1.61,
        Distance = 1.6,
        ZoneData = {
            Center = vector3(1060.02, -2315.77, 19.72),
            Length = 1.0,
            Width = 0.8,
            Data = {
                debugPoly = false,
                heading = 90,
                minZ = 18.72,
                maxZ = 20.92,
            },
        },
        Options = {
            {
                Name = 'methlab_1',
                Icon = '',
                Label = 'Mathlab Insurance',
                EventType = 'Client',
                EventName = 'mercy-illegal/client/methLabs/open-close',
                EventParams = { Id = 1 }, -- id to match
                Enabled = function(Entity)
                    if exports['mercy-inventory']:HasEnoughOfItem('methkey1', 1) then
                        return true
                    else
                        return false
                    end
                end,
            }
        }
    })
```
- You should set the 6 separate stages you created as regions and determine the number of items the player will earn and spend.
```
    exports['mercy-ui']:AddEyeEntry("meth_lab_1_stage1", {
        Type = 'Zone',
        SpriteDistance = 1.61,
        Distance = 1.6,
        ZoneData = {
            Center = vector3(1059.59, -2319.35, 19.73),
            Length = 2.0,
            Width = 2.0,
            Data = {
                debugPoly = false,
                heading = 90,
                minZ = 18.72,
                maxZ = 21.33,
            },
        },
        Options = {
            {
                Name = 'methlab_1_stage1',
                Icon = '',
                Label = 'Collect X',
                EventType = 'Client',
                EventName = 'mercy-illegal/client/methLabs/cook-meth',
                EventParams = { Id = 1, Item = "xmadde", Amount = 1, RequestItem = "cleaningproduct", RequestItemAmount = 3, Animation = "base_a_m_y_vinewood_01", AnimDict = "anim@amb@casino@valet_scenario@pose_d@", ProgressText = "Collect X" },
                Enabled = function(Entity)
                    return true
                end,
            }
        }
    })
```
