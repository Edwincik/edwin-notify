# **Created by Edwincik**

### [DISCORD SUPPORT SERVER](https://discord.gg/azuredev)

## SETUP INSTRUCTIONS 
Please Make a backup file for **qb-core/client/functions** file that you change. I am not responsible for any damage you do to your files/server. 

---

**CORE CHANGE INSTRUCTIONS**
- Go to the qb-core -> Client Side Folder -> functions.lua -> line 88

- Replace this Event
```lua
function QBCore.Functions.Notify(text, texttype, length)
    if type(text) == "table" then
        local ttext = text.text or 'Placeholder'
        local caption = text.caption or 'Placeholder'
        texttype = texttype or 'primary'
        length = length or 5000
        SendNUIMessage({
            action = 'notify',
            type = texttype,
            length = length,
            text = ttext,
            caption = caption
        })
    else
        texttype = texttype or 'primary'
        length = length or 5000
        SendNUIMessage({
            action = 'notify',
            type = texttype,
            length = length,
            text = text
        })
    end
end
```

- With 
```lua
QBCore.Functions.Notify = function(text, textype, length, pro)
    local textype = textype ~= nil and textype
    textype = textype or 'info'
    local length = length ~= nil and length or 5000
    if length == nil then 
        exports['Notify']:Alert(textype, text, 5000, textype)
    else
        exports['Notify']:Alert(textype, text, length, textype)
    end
end
```

---
