---
description: Start making your own resources with wosa today!
---

# Create your own resource!

## Scripting Introduction

{% hint style="danger" %}
The documantation provided is only for creating your own resources outside the framework. Never attempt to use these features inside the framework core.
{% endhint %}

![World Of San Andreas - Create your first script today!](.gitbook/assets/102146167-vector-line-web-concept-for-programming-linear-web-banner-for-coding-1.jpg)

> World Of San Andreas features a wide variety of development tools for out of resource usage. This documantation is originally created for developers that want to create scripts for the framework. These functions and events are not required for any resources unless you want to use data from the framework core.
>
> The documantation provided does not cover all features by any means, But covers a great section of the tools available. Functions & events may change and new features may get added to this page if requested by the community.
>
> Unlisted events and functions that are found by the community may be added or not due to various factors such as...
>
> 1. [ ] Is the feature safe to give out to other resources?
> 2. [ ] Does the feature work as expected and do we even know how it works?
> 3. [ ] Can the feature collide with other things?

{% hint style="info" %}
#### Check this out, These awesome pages have everything you need for creating resources!

Natives: [https://runtime.fivem.net/doc/natives/](https://runtime.fivem.net/doc/natives/)

Notifications: [https://wiki.gt-mp.net/index.php/Notification\_Pictures](https://wiki.gtanet.work/index.php?title=Notification_Pictures)

Blips: [https://wiki.gtanet.work/index.php?title=Blips](https://docs.fivem.net/docs/game-references/blips/)

Banners: [https://wiki.gt-mp.net/index.php?title=MenuBannerSpriteList](https://wiki.gt-mp.net/index.php?title=MenuBannerSpriteList)

Animations: [https://alexguirre.github.io/animations-list/](https://alexguirre.github.io/animations-list/)
{% endhint %}

## Public Events

All public events that should be used from Wosa are listed here. If you have found a event that you think should be listed here, Please send a message to one of our fellow developers. It is not recommended to use non-documented events.

### Server Events

```lua
AddEventHandler('__WOSA:SERVER:USER_CONNECTING', function(playerID, playerLicense, playerRank, isPlayerNew)

end)
```

```lua
AddEventHandler('__WOSA:SERVER:USER_LEAVING', function(playerID, playerLicense, playerRank, leaveReason)

end)
```

```lua
AddEventHandler('__WOSA:SERVER:CHARACTER_CREATED', function(playerID, characterData)
    print(characterData.GET_FIRSTNAME)
    print(characterData.GET_MIDDLENAME)
    print(characterData.GET_LASTNAME)
    print(characterData.GET_DAY)
    print(characterData.GET_MONTH)
    print(characterData.GET_YEAR)
    print(characterData.GET_GENDER)
    print(characterData.GET_PHONE_NUMBER)
    print(characterData.GET_CHARACTER_TABLE)
    print(characterData.GET_INVENTORY_TABLE)
end)
```

```lua
AddEventHandler('__WOSA:SERVER:CHARACTER_LOADED', function(playerID, characterData)
    print(characterData.GET_FIRSTNAME)
    print(characterData.GET_MIDDLENAME)
    print(characterData.GET_LASTNAME)
    print(characterData.GET_DAY)
    print(characterData.GET_MONTH)
    print(characterData.GET_YEAR)
    print(characterData.GET_GENDER)
    print(characterData.GET_PHONE_NUMBER)
    print(characterData.GET_CHARACTER_TABLE)
    print(characterData.GET_INVENTORY_TABLE)
end)
```

```lua
AddEventHandler('__WOSA:SERVER:CHARACTER_REMOVED', function(playerID, characterData)
    print(characterData.GET_FIRSTNAME)
    print(characterData.GET_MIDDLENAME)
    print(characterData.GET_LASTNAME)
    print(characterData.GET_DAY)
    print(characterData.GET_MONTH)
    print(characterData.GET_YEAR)
    print(characterData.GET_GENDER)
    print(characterData.GET_PHONE_NUMBER)
    print(characterData.GET_CHARACTER_TABLE)
    print(characterData.GET_INVENTORY_TABLE)
end)
```

### Client Events

```lua
AddEventHandler('__WOSA:CLIENT:ITEM_USE', function(itemName, itemDisplayName, itemDatabaseID, itemRemovedOnUse)

end)
```

```lua
AddEventHandler('__WOSA:CLIENT:ITEM_ADD', function(itemName, itemDisplayName)

end)
```

```lua
AddEventHandler('__WOSA:CLIENT:ITEM_GIVE', function(receiverPlayerID, itemName, itemDisplayName, itemDatabaseID)

end)
```

```lua
AddEventHandler('__WOSA:CLIENT:ITEM_DROP', function(itemName, itemDisplayName, itemDatabaseID)

end)
```

```lua
AddEventHandler('__WOSA:SERVER:__WOSA:SERVER:ITEM_PICKUP', function(coordsOfItem, itemName, itemDisplayName)
    print(coordsOfItem.x, coordsOfItem.y, coordsOfItem.z)
end)
```

```lua
AddEventHandler('__WOSA:CLIENT:911_CALL', function(CallerPlayerID, coords, callInfo, serviceCalled, newCallID)
    print(coords.x, coords.y, coords.z)
end)
```

```lua
AddEventHandler('__WOSA:CLIENT:SERVICE_CALL', function(CallerPlayerID, coords, callInfo, serviceCalled, newCallID)
    print(coords.x, coords.y, coords.z)
end)
```

## Public Functions

Public functions are functions that are provided with the [API connector](https://github.com/Clatanii/Wosa_Connector). The connector is used to transmit/receive data from wosa/your resource. The latest version of the connector\(s\) can be found at [https://github.com/Clatanii/wosa\_latest\_connector\_files](https://github.com/Clatanii/Wosa_Connector). To use the connectors do the following:

1. Download the latest connector file\(s\).
2. Place them inside your resource folder.
3. Add the files to your _fx_\_manifest file.
4. Add `dependency 'wosa_core'` to your fx\_manifest file at the top.

{% hint style="warning" %}
It is important that you load wosa\_core before loading any other resource using the connector files as the connector file\(s\) will start receiving data ONLY when the wosa\_core is ready. 
{% endhint %}

What can the connector file\(s\) access in your resource?

1. [x] Get resource name.
2. [ ] Send data to resource functions/events.
3. [x] Get running connector version.
4. [ ] Receive data from resource functions/events.
5. [x] Add a global resource table called `Wosa`.
6. [x] stop/start the resource.

### Server Functions

#### User Classed

```lua
local license = Wosa.User.GetLicense(playerID)
```

```lua
Wosa.User.SetPermissionLevel(playerID, newRank)
```

```lua
local rank = Wosa.User.GetPermissionLevel(playerID)
```

```lua
local inventoryDatabaseTable = Wosa.User.GetUsingTable(playerID, 'i')

local characterDatabaseTable = Wosa.User.GetUsingTable(playerID, 'c')
```

```lua
local isUserUsingAnyCharacter = Wosa.User.UsingAnyCharacter(playerID)
```

```lua
Wosa.User.RevivePed(playerID)
```

#### Character & Inventory Classed

```lua
local characterData = Wosa.Character.GetCharacterData(playerID)

print(characterData.firstname)
print(characterData.middlename)
print(characterData.lastname)
print(characterData.day)
print(characterData.month)
print(characterData.year)
print(characterData.gender)
print(characterData.phone_number)

print(characterData.driver_license)
print(characterData.truck_license)
print(characterData.air_license)
print(characterData.boat_license)
print(characterData.firearm_license)
```

```lua
Wosa.Character.SetCanBeLooted(playerID, bool)
```

```lua
local CanCharacterBeLooted = Wosa.Character.GetCanBeLooted(playerID)
```

```lua
local myInventory = Wosa.Inventory.GetItems(playerID)
```

```lua
-- add 'RE_'(Reusable item) or 'RI_'(Remove On Use) before the item name
-- the data types such as Bool1 can be used for 'custom' data later on use for example

local itemData = {itemName = 'RI_EXAMPLE_ITEM', displayName = 'Example Item', Usable = true, Givable = true, Dropable = true, String1 = '', String2 = '', String3 = '', Bool1 = false, Bool2 = false, Bool3 = false, Int1 = 0, Int2 = 0, Int3 = 0, Float1 = 0.0, Float2 = 0.0, Float3 = 0.0 }
Wosa.Inventory.AddItem(playerID, inventoryDatabaseTable, itemData)
```

```lua
Wosa.Inventory.RemoveItem(playerID, '', itemName)

-- You can either input ItemID or ItemName

Wosa.Inventory.RemoveItem(playerID, itemID, '')
```

```lua
local doesItemExistInInventory = Wosa.Inventory.DoesItemNameExist(playerID, itemName)
```

```lua
local availablePaymentMethods = Wosa.Inventory.GetAvailablePaymentMethods(playerID)

print(tostring(availablePaymentMethods[1])) -- Business Credit Card
print(tostring(availablePaymentMethods[2])) -- Vanilla Credit Card 
print(tostring(availablePaymentMethods[3])) -- Pocket Cash 
```

#### Faction & Job Classed

```lua
Wosa.Faction.SetFaction(playerID, JobName, FactionRank, FactionSubRank)
```

```
Wosa.Faction.RemoveFaction(playerID, inventoryCharacterTable, JobName)
```

```
Wosa.Faction.UpdateFaction(playerID, inventoryCharacterTable, JobName, FactionRank, FactionSubRank)
```

### Client Functions

#### User Classed

```lua
local isUserUsingAnyCharacter = Wosa.User.GetIsAnyCharacterLoaded()
```

```lua
Wosa.User.RevivePed()
```

#### Character & Inventory Classed

```lua
local characterDatabaseTable = Wosa.Character.GetCharacterDatabase()
```

```lua
local inventoryDatabaseTable = Wosa.Inventory.GetInventoryDatabase()
```

```lua
local firstname = Wosa.Character.GetFirstname()
```

```lua
local middlename = Wosa.Character.GetMiddlename()
```

```lua
local lastname = Wosa.Character.GetLastname()
```

```lua
local day = Wosa.Character.GetDayOfBirth()
```

```lua
local month = Wosa.Character.GetMonthOfBirth()
```

```lua
local year = Wosa.Character.GetYearOfBirth()
```

```lua
local gender = Wosa.Character.GetGender()
```

```lua
local driverLicense = Wosa.Character.GetDriverLicense()
```

```lua
local truckLicense = Wosa.Character.GetTruckLicense()
```

```lua
local boatLicense = Wosa.Character.GetBoatLicense()
```

```lua
local firearmLicense = Wosa.Character.GetFirearmLicense()
```

```lua
local CanCharacterBeLooted = Wosa.Character.GetCanBeLooted()
```

#### Faction & Job Classed

```lua
Wosa.Job.SetJob(JobName, JobSalary)
```

```lua
Wosa.Job.SetOffDuty()
```

```lua
local MyCurrentJob = Wosa.Job.GetJob()
```

```lua
local MyFactionRankFromDatabase = Wosa.Job.DownloadAndGetFactionRank(JobName)
```

```lua
local MyFactionRank = Wosa.Job.GetFactionRank()
```

#### Game & Utilities Classed

```lua
local weaponTable = Wosa.Game.GetCurrentWeapons()
```

```lua
Wosa.Game.SetCurrentWeapons(weaponTable)
```

```lua
Wosa.Game.RequestCameraView(x, y, z, rx, ry, rz)
```

```lua
Wosa.Game.RequestAnimatedCameraView(x, y, z, rx, ry, rz, x2, y2, z2, rx2, ry2, rz2, animationDuration)
```

```lua
Wosa.Game.StopAnyCamera()
```

```lua
Wosa.Game.HideHUDThisTick()
```

```lua
Wosa.Game.LoadingWheel(text, duration, type)
```

```lua
Wosa.Game.DisplayHelpText(text, text, text, duration)
```

```lua
Wosa.Game.DisplayHelpTextThisTick(text)
```

```lua
Wosa.Game.DisplayMissionText(text, duration)
```

```lua
Wosa.Game.DisplayNotification(text)
```

```lua
local doesVehicleHaveAnyExtras = Wosa.Game.DoesVehicleHaveAnyExtras(vehicle)
```

```lua
local vehicleData = Wosa.Game.VehicleToData(vehicle)
```

```lua
local vehicle = Wosa.Game.CreateVehicleFromData(vehicleData, x, y, z, h, dontNetwork, specialData?)
```

```lua
local data = {godemode = true, livery = 2, fade = {set = true, delay = 0}, colors = {set = true, data = {0, 0}}, blip = {set = true, label = 'my vehicle', color = 0, id = 0}, anchor = true}
local vehicle = Wosa.Game.SpawnVehicle(vehicleName, coords, data, NetworkVehicle)
```

```lua
local data = {godemode = true, weaponInHand = 'WEAPON_MICROSMG', fade = {set = true, delay = 0}, blip = {set = true, label = 'my ped', color = 0, id = 0}, }
local ped = Wosa.Game.SpawnPed(pedName, pedType, coords, data, NetworkPed)
```

```lua
Wosa.Game.RequestModel(model)
```

```lua
Wosa.Game.RequestModelHash(modelHash)
```

```lua
local input = Wosa.Game.KeyboardInput(DescText, ExampleText, MaxStringLenght)
```

```lua
Wosa.Game.LoadMultiplayerPedToLocalFile()
```

```lua
Wosa.Game.SaveMultiplayerPedToDatabase()
```

```lua
Wosa.Game.SaveMultiplayerPed()
```

```lua
Wosa.Game.SaveMultiplayerPedToLocalFile()
```

```lua
Wosa.Game.LoadMultiplayerPedFromLocalFile()
```

```lua
Wosa.Game.RequestPed(ped)
```

```lua
Wosa.Game.RequestPedClothing(arms, arms_tex, undershirt, undershirt_tex, top, top_tex, pants, pants_tex, shoes, shoes_tex, neck, neck_tex)
```

```lua
Wosa.Game.DrawScreenText(x, y, width, height, scale, text, r, g, b, a, font, centre)
```

```lua
Wosa.Game.DrawGameTextThisTick(x, y, z, text)
```

```lua
Wosa.Game.DrawGameText(x, y, z, text, duration)
```

```lua
Wosa.Game.RequestWalkStyle(walkStyle)
```

```lua
local playersInArea = Wosa.Game.GetPlayersInArea_2(coords, maxDistance)

-- unsure if this function works like this, maybe used as a sub function for Wosa.Game.GetPlayersInArea?
```

```lua
local playersInArea = Wosa.Game.GetPlayersInArea()

-- this has a bigger chance of working than the upper one I guess?
```

```lua
Wosa.Game.RequestAnimDict(animDict)
```

```lua
local closestPlayer, closestDistance = Wosa.Game.GetClosestPlayer()
```

```lua
local players = Wosa.Game.GetPlayers()
```

## External Notes

### Item Register

You can register new items in any client file with this event. This event gets called each time you use a item from the main menu. the event format is `WOSA_HANDLE_ITEM_ON_USE:MY_ITEM_NAME` . 

{% hint style="info" %}
You are required to include the full item name with `RE_` or `RI_` before.
{% endhint %}

> The data `data` is the column directly from the database. This is how the column is structured...

| Name | Comment |
| :--- | :--- |
| created\_date | date of when data last got updated/created. |
| logged\_name | Logged player name of the player \(not character name\). |
| license\_id | License of the player. |
| item\_name | The item name. |
| display\_name | The display name of the item. |
| item\_string1 | custom data type. |
| item\_string2 | custom data type. |
| item\_string3 | custom data type. |
| item\_bool1 | custom data type. |
| item\_bool2 | custom data type. |
| item\_bool3 | custom data type. |
| item\_int1 | custom data type. |
| item\_int2 | custom data type. |
| item\_int3 | custom data type. |
| item\_float1 | custom data type. |
| item\_float2 | custom data type. |
| item\_float3 | custom data type. |
| item\_dropable | Can the item be dropped. |
| item\_givable | Can the item be given to others. |
| item\_usable | Can the item be used. |
| item\_space | The space in inventory the item takes up, default: 1. |

```lua
local itemName = 'RI_EXAMPLE_ITEM'

AddEventHandler('WOSA:HANDLE_ITEM_ON_USE:'..itemName, function(data)
	print(data[1].display_name)
end)
```

