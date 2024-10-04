# Fluent Interface Suite
This documentation is for the latest release of Fluent.

## Booting the Library
```lua
local Fluent = loadstring(game:HttpGet("https://raw.githubusercontent.com/falixfresh/Fluent-Extended/master/latest.lua"))()
```

## Creating a Window
```lua
local Window = Fluent:CreateWindow({
    Title = "Fluent " .. Fluent.Version,
    SubTitle = "by dawid",
    TabWidth = 160,
    Size = UDim2.fromOffset(580, 460),
    Acrylic = true, -- The blur may be detectable, setting this to false disables blur entirely
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl -- Used when theres no MinimizeKeybind
})

--[[
Title = <string> - The title of the UI.
SubTitle = <string> - The subtitle of the UI.
TabWidth = <num>, - The number of Tab Width of the UI.
]]
```

## Creating a Tab
```lua
local Tab = Window:AddTab({
  Title = "Tab",
  Icon = ""
}),
```
You can set Icon, icons are https://lucide.dev/

## Fluent Options
```lua
local Options = Fluent.Options
```

## Notifying the user
```lua
Fluent:Notify({
  Title = "Notification",
  Content = "This is a notification",
  SubContent = "SubContent", -- Optional
  Duration = 5 -- Set to nil to make the notification not disappear
})
```

## Creating a Paragraph
```lua
    local Paragraph = Tab:AddParagraph({
        Title = "Paragraph",
        Content = "This is a paragraph.\nSecond line!"
    })
```

## Creating a Button
```lua
    local Button = Tab:AddButton({
        Title = "Button",
        Description = "Very important button",
        Callback = function()
            print('Pressed button')
        end
    })
```
