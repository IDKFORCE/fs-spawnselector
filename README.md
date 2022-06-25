# fs-spawnselector

Dont Not Replace qb-spawn with this ⚠⚠⚠⚠⚠

*
![showcase](https://cdn.discordapp.com/attachments/784243374269661195/990042002550829097/unknown.png)

*
# Manual Installation
This Is How It Works. 

Ok Go To [qb-apartments/client/main.lua] Then Go To The Event `apartments:client:setupSpawnUI` And Replace It With This 

```
RegisterNetEvent('apartments:client:setupSpawnUI', function(cData)
    QBCore.Functions.TriggerCallback('apartments:GetOwnedApartment', function(result)
        if result then
            TriggerEvent('qb-spawn:client:setupSpawns', cData, false, nil)
            TriggerEvent("apartments:client:SetHomeBlip", result.type)
        else
            if Apartments.Starting then
                TriggerEvent('qb-spawn:client:setupSpawns', cData, true, Apartments.Locations)
                TriggerEvent('qb-spawn:client:openUI', true)
            else
                TriggerEvent('qb-spawn:client:setupSpawns', cData, false, nil)
                TriggerEvent('qb-spawn:client:openUI', true)
            end
        end
    end, cData.citizenid)
end)
```

*

Then Go To [qb-spawn/client.lua] Then Go To The Event `qb-spawn:client:setupSpawns` And Replace It With This

```
RegisterNetEvent('qb-spawn:client:setupSpawns', function(cData, new, apps)
    if not new then
         TriggerEvent('fs-spawnselector:set')
    elseif new then
        SendNUIMessage({
            action = "setupAppartements",
            locations = apps,
        })
    end
end)
```

*
This Is The Original
[link](https://github.com/arabcodingteam/qb-spawnselector)