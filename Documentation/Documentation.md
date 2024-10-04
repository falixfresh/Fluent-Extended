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

```

## Creating a Tab
```lua
local Tab = Window:AddTab({
  Title = "Tab",
  Icon = ""
})
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

## Creating a Toggle
```lua
local Toggle = Tabs.Main:AddToggle("MyToggle", {
    Title = "Toggle",
    Default = false
})
```
On change
```lua
Toggle:OnChanged(function()
    print("Toggle changed:", Options.MyToggle.Value)
end)
```
Set value
```lua
Options.MyToggle:SetValue(false)
```

## Creating a Slider
```lua

