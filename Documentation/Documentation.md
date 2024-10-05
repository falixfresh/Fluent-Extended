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
local Slider = Tab:AddSlider("Slider", {
    Title = "Slider",
    Description = "This is a slider",
    Default = 2,
    Min = 0,
    Max = 5,
    Rounding = 1,
    Callback = function(Value)
        print("Slider was changed:", Value)
    end
})
```
On change
```lua
Slider:OnChanged(function(Value)
    print("Slider changed:", Value)
end)
```
Set value
```lua
Slider:SetValue(3)
```

## Creating a Dropdown
```lua
local Dropdown = Tab:AddDropdown("Dropdown", {
    Title = "Dropdown",
    Values = {"one", "two", "three", "four", "five", "six", "seven", "eight", "nine", "ten", "eleven", "twelve", "thirteen", "fourteen"},
    Multi = false,
    Default = 1,
})
```
On change
```lua
Dropdown:OnChanged(function(Value)
    print("Dropdown changed:", Value)
end)
```
Set value
```lua
Dropdown:SetValue("four")
```

## Creating a Multi-Dropdown
```lua
local MultiDropdown = Tab:AddDropdown("MultiDropdown", {
    Title = "Dropdown",
    Description = "You can select multiple values.",
    Values = {"one", "two", "three", "four", "five", "six", "seven", "eight", "nine", "ten", "eleven", "twelve", "thirteen", "fourteen"},
    Multi = true,
    Default = {"seven", "twelve"},
})
```
On change
```lua
MultiDropdown:OnChanged(function(Value)
    local Values = {}
    for Value, State in next, Value do
        table.insert(Values, Value)
    end
    print("Mutlidropdown changed:", table.concat(Values, ", "))
end)
```
Set value
```lua
MultiDropdown:SetValue({
    three = true,
    five = true,
    seven = false
})
```

## Creating a Colorpicker
```lua
local Colorpicker = Tab:AddColorpicker("Colorpicker", {
    Title = "Colorpicker",
    Default = Color3.fromRGB(96, 205, 255)
})
```
On change
```lua
Colorpicker:OnChanged(function()
    print("Colorpicker changed:", Colorpicker.Value)
end)
```
Set value
```lua
Colorpicker:SetValueRGB(Color3.fromRGB(0, 255, 140))
```

## Creating a TColorpicker
```lua
local TColorpicker = Tab:AddColorpicker("TransparencyColorpicker", {
    Title = "Colorpicker",
    Description = "but you can change the transparency.",
    Transparency = 0,
    Default = Color3.fromRGB(96, 205, 255)
})
```
On change
```lua
TColorpicker:OnChanged(function()
    print(
        "TColorpicker changed:", TColorpicker.Value,
        "Transparency:", TColorpicker.Transparency
    )
end)
```

## Creating a Keybind
```lua
local Keybind = Tab:AddKeybind("Keybind", {
    Title = "KeyBind",
    Mode = "Toggle", -- Always, Toggle, Hold
    Default = "LeftControl", -- String as the name of the keybind (MB1, MB2 for mouse buttons)

        -- Occurs when the keybind is clicked, Value is `true`/`false`
    Callback = function(Value)
        print("Keybind clicked!", Value)
    end,

        -- Occurs when the keybind itself is changed, `New` is a KeyCode Enum OR a UserInputType Enum
    ChangedCallback = function(New)
        print("Keybind changed!", New)
    end
})
```
On click
```lua
Keybind:OnClick(function()
    print("Keybind clicked:", Keybind:GetState())
end)
```
On change
```lua
Keybind:OnChanged(function()
    print("Keybind changed:", Keybind.Value)
end)
```
Set value
```lua
Keybind:SetValue("MB2", "Toggle") -- Sets keybind to MB2, mode to Hold
```
on held (idk)
```lua
task.spawn(function()
    while true do
        wait(1)

        -- example for checking if a keybind is being pressed
        local state = Keybind:GetState()
        if state then
            print("Keybind is being held down")
        end

        if Fluent.Unloaded then break end
    end
end)
```

## Creating a Input
```lua
local Input = Tab:AddInput("Input", {
    Title = "Input",
    Default = "Default",
    Placeholder = "Placeholder",
    Numeric = false, -- Only allows numbers
    Finished = false, -- Only calls callback when you press enter
    Callback = function(Value)
        print("Input changed:", Value)
    end
})
```
On change
```lua
Input:OnChanged(function()
    print("Input updated:", Input.Value)
end)
```

## Save Manager & Interface Manager
```lua
SaveManager:SetLibrary(Fluent)
InterfaceManager:SetLibrary(Fluent)
SaveManager:IgnoreThemeSettings()
SaveManager:SetIgnoreIndexes({})
InterfaceManager:SetFolder("FluentScriptHub")
SaveManager:SetFolder("FluentScriptHub/specific-game")
InterfaceManager:BuildInterfaceSection(Tab) --settings tab
SaveManager:BuildConfigSection(Tab) -- settings
SaveManager:LoadAutoloadConfig() -- cfg auto load
```

## General
```lua
Window:SelectTab(1)
```
