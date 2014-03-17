DaiGUI
======

Provides access to creating UI components from a Lua table in WildStar.

### Example Usage
Create a window with a button

```lua
-- Get the package from Apollo's package system
local DaiGUI = Apollo.GetPackage("DaiGUI-1.0").tPackage

-- Create the window prototype object
local tWindow = DaiGUI:Create({
  Name = "MyExampleWindow",
  Template      = "CRB_TooltipSimple",
  UseTemplateBG = true,
  Picture       = true,
  Border        = true,
  AnchorCenter  = { 500, 300 },
  Children = {
    {
      WidgetType     = "PushButton",
      Base           = "CRB_UIKitSprites:btn_square_LARGE_Red",
      Text           = "Close Parent",
      TextThemeColor = "ffffffff", -- sets normal, flyby, pressed, pressedflyby, disabled to a color
      AnchorCenter   = { 150, 40 },
      Events = {
        ButtonSignal = function(self, wndHandler, wndControl)
          wndControl:GetParent():Close()
        end
      },
    },
  },
})

-- create the instance of the window.   This instance is the same type of object 
-- you would get from Apollo.LoadForm()
local wndInstance = tWindow:GetInstance()
```
