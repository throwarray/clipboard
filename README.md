# clipboard
Set clipboard text so you can paste it outside of FiveM. 
It works by waiting for a keypress event on the nui.

```lua
AddEventHandler('playerSpawned', function ()
    local playerPed = PlayerPedId()
    local coords = GetEntityCoords(playerPed)

    if not exports.clipboard:SettingClipboard() then
        exports.clipboard:SetClipboard(json.encode({
            x = coords.x,
            y = coords.y,
            z = coords.z,
            model = GetEntityModel(playerPed),
            heading = GetEntityHeading(playerPed)
        }), function (err)
            print('SET CLIPBOARD SUCCESS', not err)
        end) 
    end
end)
```
