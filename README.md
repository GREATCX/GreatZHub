local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("GreatZ HUB ", "BloodTheme")

local Tab = Window:NewTab("Main")
local Section = Tab:NewSection("Basic")

Section:NewButton("Fly[E]", "GreatZ So Gay", function()
	local flygui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local fly = Instance.new("TextButton")

	flygui.Name = "flygui"
flygui.Parent = game.CoreGui
flygui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
 
Frame.Parent = flygui
Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Frame.Position = UDim2.new(0.582615495, 0, 0.336609334, 0)
Frame.Size = UDim2.new(0, 100, 0, 100)
Frame.Draggable = true
Frame.Active = true
 
fly.Name = "fly"
fly.Parent = Frame
fly.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
fly.Position = UDim2.new(0.189999998, 0, 0.140000001, 0)
fly.Size = UDim2.new(0, 66, 0, 67)
fly.Font = Enum.Font.SourceSans
fly.Text = "fly"
fly.TextColor3 = Color3.fromRGB(0, 0, 0)
fly.TextSize = 14.000

local function ZMDYKO_fake_script() -- fly.LocalScript 
	local script = Instance.new('LocalScript', fly)
 
	script.Parent.MouseButton1Click:Connect(function()
		print("re execute if you die")
		wait(.1)
		repeat wait() 
		until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Head") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid") 
		local mouse = game.Players.LocalPlayer:GetMouse() 
		repeat wait() until mouse
		local plr = game.Players.LocalPlayer 
		local torso = plr.Character.Head 
		local flying = false
		local deb = true 
		local ctrl = {f = 0, b = 0, l = 0, r = 0} 
		local lastctrl = {f = 0, b = 0, l = 0, r = 0} 
		local maxspeed = 50 
		local speed = 0 
 
		function Fly() 
			local bg = Instance.new("BodyGyro", torso) 
			bg.P = 9e4 
			bg.maxTorque = Vector3.new(9e9, 9e9, 9e9) 
			bg.cframe = torso.CFrame 
			local bv = Instance.new("BodyVelocity", torso) 
			bv.velocity = Vector3.new(0,0.1,0) 
			bv.maxForce = Vector3.new(9e9, 9e9, 9e9) 
			repeat wait() 
				plr.Character.Humanoid.PlatformStand = true 
				if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then 
					speed = speed+.5+(speed/maxspeed) 
					if speed > maxspeed then 
						speed = maxspeed 
					end 
				elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then 
					speed = speed-1 
					if speed < 0 then 
						speed = 0 
					end 
				end 
				if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then 
					bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
					lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r} 
				elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then 
					bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed 
				else 
					bv.velocity = Vector3.new(0,0.1,0) 
				end 
				bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0) 
			until not flying 
			ctrl = {f = 0, b = 0, l = 0, r = 0} 
			lastctrl = {f = 0, b = 0, l = 0, r = 0} 
			speed = 0 
			bg:Destroy() 
			bv:Destroy() 
			plr.Character.Humanoid.PlatformStand = false 
		end 
		mouse.KeyDown:connect(function(key) 
			if key:lower() == "e" then 
				if flying then flying = false 
				else 
					flying = true 
					Fly() 
				end 
			elseif key:lower() == "w" then 
				ctrl.f = 1 
			elseif key:lower() == "s" then 
				ctrl.b = -1 
			elseif key:lower() == "a" then 
				ctrl.l = -1 
			elseif key:lower() == "d" then 
				ctrl.r = 1 
			end 
		end) 
		mouse.KeyUp:connect(function(key) 
			if key:lower() == "w" then 
				ctrl.f = 0 
			elseif key:lower() == "s" then 
				ctrl.b = 0 
			elseif key:lower() == "a" then 
				ctrl.l = 0 
			elseif key:lower() == "d" then 
				ctrl.r = 0 
			end 
		end)
		Fly()
	end)
end
coroutine.wrap(ZMDYKO_fake_script)()
end)

Section:NewButton ("Noclip", "GreatZ So Gay", function()
	local Workspace = game:GetService("Workspace")
	local CoreGui = game:GetService("CoreGui")
	local Players = game:GetService("Players")
	local Noclip = Instance.new("ScreenGui")
	local BG = Instance.new("Frame")
	local Title = Instance.new("TextLabel")
	local Toggle = Instance.new("TextButton")
	local StatusPF = Instance.new("TextLabel")
	local Status = Instance.new("TextLabel")
	local Credit = Instance.new("TextLabel")
	local Plr = Players.LocalPlayer
	local Clipon = false
	 
	Noclip.Name = "Noclip"
	Noclip.Parent = game.CoreGui
	 
	BG.Name = "BG"
	BG.Parent = Noclip
	BG.BackgroundColor3 = Color3.new(0.0980392, 0.0980392, 0.0980392)
	BG.BorderColor3 = Color3.new(0.0588235, 0.0588235, 0.0588235)
	BG.BorderSizePixel = 2
	BG.Position = UDim2.new(0.149479166, 0, 0.82087779, 0)
	BG.Size = UDim2.new(0, 210, 0, 127)
	BG.Active = true
	BG.Draggable = true
	 
	Title.Name = "Title"
	Title.Parent = BG
	Title.BackgroundColor3 = Color3.new(0.266667, 0.00392157, 0.627451)
	Title.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
	Title.BorderSizePixel = 2
	Title.Size = UDim2.new(0, 210, 0, 33)
	Title.Font = Enum.Font.Highway
	Title.Text = "Noclip"
	Title.TextColor3 = Color3.new(1, 1, 1)
	Title.FontSize = Enum.FontSize.Size32
	Title.TextSize = 30
	Title.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
	Title.TextStrokeTransparency = 0
	 
	Toggle.Parent = BG
	Toggle.BackgroundColor3 = Color3.new(0.266667, 0.00392157, 0.627451)
	Toggle.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
	Toggle.BorderSizePixel = 2
	Toggle.Position = UDim2.new(0.152380958, 0, 0.374192119, 0)
	Toggle.Size = UDim2.new(0, 146, 0, 36)
	Toggle.Font = Enum.Font.Highway
	Toggle.FontSize = Enum.FontSize.Size28
	Toggle.Text = "Toggle"
	Toggle.TextColor3 = Color3.new(1, 1, 1)
	Toggle.TextSize = 25
	Toggle.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
	Toggle.TextStrokeTransparency = 0
	 
	StatusPF.Name = "StatusPF"
	StatusPF.Parent = BG
	StatusPF.BackgroundColor3 = Color3.new(1, 1, 1)
	StatusPF.BackgroundTransparency = 1
	StatusPF.Position = UDim2.new(0.314285725, 0, 0.708661377, 0)
	StatusPF.Size = UDim2.new(0, 56, 0, 20)
	StatusPF.Font = Enum.Font.Highway
	StatusPF.FontSize = Enum.FontSize.Size24
	StatusPF.Text = "Status:"
	StatusPF.TextColor3 = Color3.new(1, 1, 1)
	StatusPF.TextSize = 20
	StatusPF.TextStrokeColor3 = Color3.new(0.333333, 0.333333, 0.333333)
	StatusPF.TextStrokeTransparency = 0
	StatusPF.TextWrapped = true
	 
	Status.Name = "Status"
	Status.Parent = BG
	Status.BackgroundColor3 = Color3.new(1, 1, 1)
	Status.BackgroundTransparency = 1
	Status.Position = UDim2.new(0.580952346, 0, 0.708661377, 0)
	Status.Size = UDim2.new(0, 56, 0, 20)
	Status.Font = Enum.Font.Highway
	Status.FontSize = Enum.FontSize.Size14
	Status.Text = "off"
	Status.TextColor3 = Color3.new(0.666667, 0, 0)
	Status.TextScaled = true
	Status.TextSize = 14
	Status.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
	Status.TextWrapped = true
	Status.TextXAlignment = Enum.TextXAlignment.Left
	 
	Credit.Name = "Credit"
	Credit.Parent = BG
	Credit.BackgroundColor3 = Color3.new(1, 1, 1)
	Credit.BackgroundTransparency = 1
	Credit.Position = UDim2.new(0.195238099, 0, 0.866141737, 0)
	Credit.Size = UDim2.new(0, 128, 0, 17)
	Credit.Font = Enum.Font.SourceSans
	Credit.FontSize = Enum.FontSize.Size18
	Credit.Text = "Created by GreatZ"
	Credit.TextColor3 = Color3.new(1, 1, 1)
	Credit.TextSize = 16
	Credit.TextStrokeColor3 = Color3.new(0.196078, 0.196078, 0.196078)
	Credit.TextStrokeTransparency = 0
	Credit.TextWrapped = true
	 
	Toggle.MouseButton1Click:connect(function()
		if Status.Text == "off" then
			Clipon = true
			Status.Text = "on"
			Status.TextColor3 = Color3.new(0,185,0)
			Stepped = game:GetService("RunService").Stepped:Connect(function()
				if not Clipon == false then
					for a, b in pairs(Workspace:GetChildren()) do
					if b.Name == Plr.Name then
					for i, v in pairs(Workspace[Plr.Name]:GetChildren()) do
					if v:IsA("BasePart") then
					v.CanCollide = false
					end end end end
				else
					Stepped:Disconnect()
				end
			end)
		elseif Status.Text == "on" then
			Clipon = false
			Status.Text = "off"
			Status.TextColor3 = Color3.new(170,0,0)
		end
	end)
end)

Section:NewButton("Esp Player", "GreatZ So Gay", function()
    while wait() do
		pcall(function()
		  for i,v in pairs(game.Players:GetChildren()) do
			   if not v.Character.Head:FindFirstChild("ESP") then
				   local BillboardGui = Instance.new("BillboardGui")
				   local TextLabel = Instance.new("TextLabel")
				   BillboardGui.Parent = v.Character.Head
				   BillboardGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
				   BillboardGui.Active = true
				   BillboardGui.Name = "ESP"
				   BillboardGui.AlwaysOnTop = true
				   BillboardGui.LightInfluence = 1.000
				   BillboardGui.Size = UDim2.new(0, 200, 0, 50)
				   BillboardGui.StudsOffset = Vector3.new(0, 2.5, 0)
				   TextLabel.Parent = BillboardGui
				   TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				   TextLabel.BackgroundTransparency = 1.000
				   TextLabel.Size = UDim2.new(0, 200, 0, 50)
				   TextLabel.Font = Enum.Font.GothamBold
				   TextLabel.Text = v.Name
				   TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
				   TextLabel.TextScaled = true
				   TextLabel.TextSize = 14.000
				   TextLabel.TextStrokeTransparency = 0.000
				   TextLabel.TextWrapped = true
			   end
		   end
	   end) 
   end
end)

Section:NewButton("anti kick", "GreatZ So Gay", function()

local Players = game:GetService("Players")
local OldNameCall = nil

getgenv().SendNotifications = true -- Set to true if you want to get notified regularly.

OldNameCall = hookmetamethod(game, "__namecall", function(Self, ...)
    local NameCallMethod = getnamecallmethod()

    if tostring(string.lower(NameCallMethod)) == "kick" then
        if getgenv().SendNotifications == true then
            game:GetService("StarterGui"):SetCore("SendNotification", {
                Title = "Exunys Developer",
                Text = "You almost got kicked! Successfully prevented.",
                Icon = "rbxassetid://6238540373",
                Duration = 3,
            })
        end
        
        return nil
    end
    
    return OldNameCall(Self, ...)
end)

if getgenv().SendNotifications == true then
    game:GetService("StarterGui"):SetCore("SendNotification", {
        Title = "Exunys Developer",
        Text = "Anti-Kick script loaded",
        Icon = "rbxassetid://6238537240",
        Duration = 5,
    })
end
end)

Section:NewButton("anti afk", "GreatZ So Gay", function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/KazeOnTop/Rice-Anti-Afk/main/Wind", true))()
end)

local Tab = Window:NewTab("Misc")
local Section = Tab:NewSection("Hot Scipts")

Section:NewButton("Dex V4", "GreatZ So Gay", function()
	loadstring(game:HttpGetAsync("https://pastebin.com/raw/fPP8bZ8Z"))()
end)

Section:NewButton("Remote Spy", "GreatZ So Gay", function()
	local RemoteSpy = Instance.new("ScreenGui")
local BG = Instance.new("Frame")
local Ribbon = Instance.new("ImageLabel")
local Hide = Instance.new("TextButton")
local Title = Instance.new("TextLabel")
local Remotes = Instance.new("ScrollingFrame")
local Source = Instance.new("ScrollingFrame")
local ButtonsFrame = Instance.new("ScrollingFrame")
local ToClipboard = Instance.new("TextButton")
local Decompile = Instance.new("TextButton")
local GetReturn = Instance.new("TextButton")
local ClearList = Instance.new("TextButton")
local CryptStrings = Instance.new("TextButton")
local EnableSpy = Instance.new("TextButton")
local Total = Instance.new("TextLabel")
local Settings = Instance.new("TextButton")
local SetRemotes = Instance.new("ScrollingFrame")
local Storage = Instance.new("Frame")
local RBTN = Instance.new("TextButton")
local Icon = Instance.new("ImageLabel")
local RemoteName = Instance.new("TextLabel")
local ID = Instance.new("TextLabel")
local SBTN = Instance.new("TextButton")
local Icon_2 = Instance.new("ImageLabel")
local RemoteName_2 = Instance.new("TextLabel")
local ScriptLine = Instance.new("Frame")
local Line = Instance.new("TextLabel")
local SourceText = Instance.new("TextLabel")
local Tokens = Instance.new("TextLabel")
local Strings = Instance.new("TextLabel")
local Comments = Instance.new("TextLabel")
local Keywords = Instance.new("TextLabel")
local Globals = Instance.new("TextLabel")
local RemoteHighlight = Instance.new("TextLabel")
local Enabled = Instance.new("TextLabel")
local FullScreen = Instance.new("TextButton")
--local Exit = Instance.new("TextButton")
local SetRemotesTab = Instance.new("Frame")
local FilterF = Instance.new("TextButton")
local FilterE = Instance.new("TextButton")
local Search = Instance.new("TextBox")
local lvl6Frame = Instance.new("Frame")
local lvl6Output = Instance.new("ScrollingFrame")
local lvl6Source = Instance.new("ScrollingFrame")
local Source_ = Instance.new("TextBox")
local Comments_ = Instance.new("TextLabel")
local Globals_ = Instance.new("TextLabel")
local Keywords_ = Instance.new("TextLabel")
local RemoteHighlight_ = Instance.new("TextLabel")
local SourceText_ = Instance.new("TextLabel")
local Strings_ = Instance.new("TextLabel")
local Tokens_ = Instance.new("TextLabel")
local ClearScript = Instance.new("TextButton")
local ExecuteScript = Instance.new("TextButton")
local Resize = Instance.new("TextButton")
local lvl6 = Instance.new("TextButton")
local ClearOutput = Instance.new("TextButton")
local Label = Instance.new("TextLabel")
local Lines = Instance.new("TextLabel")
local Mute = Instance.new("TextButton")
local Icon_3 = Instance.new("ImageLabel")
local RemoteButtons = Instance.new("ScrollingFrame")
local FireRemote = Instance.new("TextButton")
local FireDelay = Instance.new("TextBox")
local LoopFire = Instance.new("TextButton")
local FireAmount = Instance.new("TextBox")
local Break = Instance.new("TextButton")
local WhileLoopFire = Instance.new("TextButton")
local remotes_fired = 0
local last_bg_pos
local LoadSource = Instance.new("TextButton")
local Refresh = Instance.new("TextButton")
local encrypt_string = false
local spy_enabled = true
 
local lua_keywords = {"and", "break", "do", "else", "elseif", "end", "false", "for", "function", "goto", "if", "in", "local", "nil", "not", "or", "repeat", "return", "then", "true", "until", "while"}
local global_env = {"getrawmetatable", "game", "workspace", "script", "math", "string", "table", "print", "wait", "BrickColor", "Color3", "next", "pairs", "ipairs", "select", "unpack", "Instance", "Vector2", "Vector3", "CFrame", "Ray", "UDim2", "Enum", "assert", "error", "warn", "tick", "loadstring", "_G", "shared", "getfenv", "setfenv", "newproxy", "setmetatable", "getmetatable", "os", "debug", "pcall", "ypcall", "xpcall", "rawequal", "rawset", "rawget", "tonumber", "tostring", "type", "typeof", "_VERSION", "coroutine", "delay", "require", "spawn", "LoadLibrary", "settings", "stats", "time", "UserSettings", "version", "Axes", "ColorSequence", "Faces", "ColorSequenceKeypoint", "NumberRange", "NumberSequence", "NumberSequenceKeypoint", "gcinfo", "elapsedTime", "collectgarbage", "PhysicalProperties", "Rect", "Region3", "Region3int16", "UDim", "Vector2int16", "Vector3int16"}
 
-- Sounds
 
local logSound = Instance.new("Sound")
local topPress = Instance.new("Sound")
local errorSound = Instance.new("Sound")
local openSound = Instance.new("Sound")
local disableSound = Instance.new("Sound")
 
local sounds = {logSound, topPress, errorSound, openSound, disableSound}
 
-- Properties
 
RemoteSpy.Name = "RemoteSpy"
RemoteSpy.Parent = game.CoreGui
 
logSound.SoundId = "rbxassetid://917942453"
 
errorSound.SoundId = "rbxassetid://582374365"
 
topPress.SoundId = "rbxassetid://558993260"
 
openSound.SoundId = "rbxassetid://472556995"
 
disableSound.SoundId = "rbxassetid://550209561"
 
BG.Name = "BG"
BG.Parent = RemoteSpy
--BG.Active = true
BG.BackgroundColor3 = Color3.new(0.141176, 0.141176, 0.141176)
BG.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
--BG.Draggable = true
BG.Position = UDim2.new(0.5, -700, 0.5, -400)
BG.Size = UDim2.new(1, -300, 1, -200)
BG.ClipsDescendants = true
 
Ribbon.Name = "Ribbon"
Ribbon.Parent = BG
Ribbon.BackgroundColor3 = Color3.new(0.760784, 0.0117647, 0.317647)
Ribbon.BorderSizePixel = 0
Ribbon.Size = UDim2.new(1, 0, 0, 20)
Ribbon.ZIndex = 2
 
Hide.Name = "Hide"
Hide.Parent = Ribbon
Hide.BackgroundColor3 = Color3.new(1, 0, 0)
Hide.BorderSizePixel = 0
Hide.Position = UDim2.new(1, -40, 0, 0)
Hide.Size = UDim2.new(0, 40, 0, 20)
Hide.ZIndex = 3
Hide.Font = Enum.Font.SourceSansBold
Hide.FontSize = Enum.FontSize.Size14
Hide.Text = "_"
Hide.TextColor3 = Color3.new(1, 1, 1)
Hide.TextSize = 14
 
Title.Name = "Title"
Title.Parent = Ribbon
Title.BackgroundColor3 = Color3.new(1, 0.0117647, 0.423529)
Title.BorderSizePixel = 0
Title.Position = UDim2.new(0.5, -100, 0, 0)
Title.Size = UDim2.new(0, 200, 0, 20)
Title.ZIndex = 3
Title.Font = Enum.Font.SourceSansBold
Title.FontSize = Enum.FontSize.Size14
Title.Text = "Remote2Script v2 R3.4"
Title.TextColor3 = Color3.new(1, 1, 1)
Title.TextSize = 14
 
Remotes.Name = "Remotes"
Remotes.Parent = BG
Remotes.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
Remotes.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
Remotes.Position = UDim2.new(0, 10, 0, 80)
Remotes.CanvasSize = UDim2.new(0, 0, 40, 0)
Remotes.Size = UDim2.new(0, 250, 1, -90)
Remotes.ZIndex = 2
Remotes.BottomImage = "rbxassetid://148970562"
Remotes.MidImage = "rbxassetid://148970562"
Remotes.ScrollBarThickness = 5
Remotes.TopImage = "rbxassetid://148970562"
 
Source.Name = "Source"
Source.Parent = BG
Source.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
Source.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
Source.Position = UDim2.new(0, 270, 0, 80)
Source.Size = UDim2.new(1, -280, 1, -140)
Source.ZIndex = 2
Source.BottomImage = "rbxassetid://148970562"
Source.CanvasSize = UDim2.new(3, 0, 160, 0)
Source.MidImage = "rbxassetid://148970562"
Source.ScrollBarThickness = 5
Source.TopImage = "rbxassetid://148970562"
 
ButtonsFrame.Name = "ButtonsFrame"
ButtonsFrame.Parent = BG
ButtonsFrame.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
ButtonsFrame.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
ButtonsFrame.Position = UDim2.new(0, 10, 0, 30)
ButtonsFrame.Size = UDim2.new(1, -20, 0, 40)
ButtonsFrame.ZIndex = 2
ButtonsFrame.ClipsDescendants = true
ButtonsFrame.CanvasSize = UDim2.new(2, 0, 0, 0)
ButtonsFrame.ScrollBarThickness = 5
ButtonsFrame.BottomImage = "rbxassetid://148970562"
ButtonsFrame.TopImage = "rbxassetid://148970562"
ButtonsFrame.MidImage = "rbxassetid://148970562"
 
ToClipboard.Name = "ToClipboard"
ToClipboard.Parent = ButtonsFrame
ToClipboard.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
ToClipboard.BorderColor3 = Color3.new(0.117647, 0.392157, 0.117647)
ToClipboard.Position = UDim2.new(0, 10, 0.5, -10)
ToClipboard.Size = UDim2.new(0, 100, 0, 20)
ToClipboard.ZIndex = 3
ToClipboard.Font = Enum.Font.SourceSansBold
ToClipboard.FontSize = Enum.FontSize.Size14
ToClipboard.Text = "COPY"
ToClipboard.TextColor3 = Color3.new(0.235294, 0.784314, 0.235294)
ToClipboard.TextSize = 14
 
Decompile.Name = "Decompile"
Decompile.Parent = ButtonsFrame
Decompile.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
Decompile.BorderColor3 = Color3.new(0.384314, 0.384314, 0.384314)
Decompile.Position = UDim2.new(0, 120, 0.5, -10)
Decompile.Size = UDim2.new(0, 100, 0, 20)
Decompile.ZIndex = 3
Decompile.Font = Enum.Font.SourceSansBold
Decompile.FontSize = Enum.FontSize.Size14
Decompile.Text = "DECOMPILE"
Decompile.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
Decompile.TextSize = 14
 
GetReturn.Name = "GetReturn"
GetReturn.Parent = ButtonsFrame
GetReturn.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
GetReturn.BorderColor3 = Color3.new(0.384314, 0.384314, 0.384314)
GetReturn.Position = UDim2.new(0, 230, 0.5, -10)
GetReturn.Size = UDim2.new(0, 100, 0, 20)
GetReturn.ZIndex = 3
GetReturn.Font = Enum.Font.SourceSansBold
GetReturn.FontSize = Enum.FontSize.Size14
GetReturn.Text = "GET RETURN"
GetReturn.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
GetReturn.TextSize = 14
 
ClearList.Name = "ClearList"
ClearList.Parent = ButtonsFrame
ClearList.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
ClearList.BorderColor3 = Color3.new(0.384314, 0.384314, 0.384314)
ClearList.Position = UDim2.new(0, 340, 0.5, -10)
ClearList.Size = UDim2.new(0, 100, 0, 20)
ClearList.ZIndex = 3
ClearList.Font = Enum.Font.SourceSansBold
ClearList.FontSize = Enum.FontSize.Size14
ClearList.Text = "CLEAR LOGS"
ClearList.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
ClearList.TextSize = 14
 
CryptStrings.Name = "CryptStrings"
CryptStrings.Parent = ButtonsFrame
CryptStrings.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
CryptStrings.BorderColor3 = Color3.new(0.392157, 0.117647, 0.117647)
CryptStrings.Position = UDim2.new(0, 450, 0.5, -10)
CryptStrings.Size = UDim2.new(0, 100, 0, 20)
CryptStrings.ZIndex = 3
CryptStrings.Font = Enum.Font.SourceSansBold
CryptStrings.FontSize = Enum.FontSize.Size14
CryptStrings.Text = "CRYPT STRINGS"
CryptStrings.TextColor3 = Color3.new(0.784314, 0.235294, 0.235294)
CryptStrings.TextSize = 14
 
EnableSpy.Name = "EnableSpy"
EnableSpy.Parent = ButtonsFrame
EnableSpy.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
EnableSpy.BorderColor3 = Color3.fromRGB(30, 100, 30)
EnableSpy.Position = UDim2.new(0, 560, 0.5, -10)
EnableSpy.Size = UDim2.new(0, 100, 0, 20)
EnableSpy.ZIndex = 3
EnableSpy.Font = Enum.Font.SourceSansBold
EnableSpy.FontSize = Enum.FontSize.Size14
EnableSpy.Text = "REMOTESPY"
EnableSpy.TextColor3 = Color3.fromRGB(60, 200, 60)
EnableSpy.TextSize = 14
 
Total.Name = "Total"
Total.Parent = ButtonsFrame
Total.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
Total.BorderColor3 = Color3.new(0.384314, 0.384314, 0.384314)
Total.Position = UDim2.new(0, 780, 0.5, -10)
Total.Size = UDim2.new(0, 50, 0, 20)
Total.ZIndex = 3
Total.Font = Enum.Font.SourceSansBold
Total.FontSize = Enum.FontSize.Size14
Total.Text = "0"
Total.TextColor3 = Color3.new(1, 1, 1)
Total.TextSize = 14
Total.TextWrapped = true
 
Settings.Name = "Settings"
Settings.Parent = ButtonsFrame
Settings.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
Settings.BorderColor3 = Color3.new(0.117647, 0.392157, 0.392157)
Settings.Position = UDim2.new(0, 670, 0.5, -10)
Settings.Size = UDim2.new(0, 100, 0, 20)
Settings.ZIndex = 3
Settings.Font = Enum.Font.SourceSansBold
Settings.FontSize = Enum.FontSize.Size14
Settings.Text = "REMOTES"
Settings.TextColor3 = Color3.new(0.235294, 0.784314, 0.784314)
Settings.TextSize = 14
 
SetRemotes.Name = "SetRemotes"
SetRemotes.Parent = BG
SetRemotes.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
SetRemotes.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
SetRemotes.Position = UDim2.new(0, 270, 0, 80)
SetRemotes.Size = UDim2.new(1, -280, 1, -140)
SetRemotes.Visible = false
SetRemotes.ZIndex = 2
SetRemotes.BottomImage = "rbxassetid://148970562"
SetRemotes.CanvasSize = UDim2.new(0, 0, 25, 0)
SetRemotes.MidImage = "rbxassetid://148970562"
SetRemotes.ScrollBarThickness = 5
SetRemotes.TopImage = "rbxassetid://148970562"
 
Storage.Name = "Storage"
Storage.Parent = RemoteSpy
Storage.BackgroundColor3 = Color3.new(1, 1, 1)
Storage.Size = UDim2.new(0, 100, 0, 100)
Storage.Visible = false
 
RBTN.Name = "RBTN"
RBTN.Parent = Storage
RBTN.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
RBTN.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
RBTN.Position = UDim2.new(0, 10, 0, 10)
RBTN.Size = UDim2.new(1, -20, 0, 20)
RBTN.ZIndex = 3
RBTN.Font = Enum.Font.SourceSansBold
RBTN.FontSize = Enum.FontSize.Size14
RBTN.Text = ""
RBTN.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
RBTN.TextSize = 14
RBTN.TextXAlignment = Enum.TextXAlignment.Left
 
Icon.Name = "Icon"
Icon.Parent = RBTN
Icon.BackgroundColor3 = Color3.new(1, 1, 1)
Icon.BackgroundTransparency = 1
Icon.Size = UDim2.new(0, 20, 0, 20)
Icon.ZIndex = 4
Icon.Image = "rbxassetid://413369506"
 
print(Icon:GetFullName())
 
RemoteName.Name = "RemoteName"
RemoteName.Parent = RBTN
RemoteName.BackgroundColor3 = Color3.new(0.713726, 0.00392157, 0.298039)
RemoteName.BorderSizePixel = 0
RemoteName.Position = UDim2.new(0, 30, 0, 0)
RemoteName.Size = UDim2.new(0, 140, 0, 20)
RemoteName.ZIndex = 4
RemoteName.Font = Enum.Font.SourceSansBold
RemoteName.FontSize = Enum.FontSize.Size14
RemoteName.Text = "10"
RemoteName.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
RemoteName.TextSize = 14
 
ID.Name = "ID"
ID.Parent = RBTN
ID.BackgroundColor3 = Color3.new(0.458824, 0.00392157, 0.192157)
ID.BorderSizePixel = 0
ID.Position = UDim2.new(1, -50, 0, 0)
ID.Size = UDim2.new(0, 50, 0, 20)
ID.ZIndex = 4
ID.Font = Enum.Font.SourceSansBold
ID.FontSize = Enum.FontSize.Size14
ID.Text = "10"
ID.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
ID.TextSize = 14
 
SBTN.Name = "SBTN"
SBTN.Parent = Storage
SBTN.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
SBTN.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
SBTN.Position = UDim2.new(0, 10, 0, 10)
SBTN.Size = UDim2.new(1, -20, 0, 20)
SBTN.ZIndex = 3
SBTN.Font = Enum.Font.SourceSansBold
SBTN.FontSize = Enum.FontSize.Size14
SBTN.Text = ""
SBTN.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
SBTN.TextSize = 11
SBTN.TextXAlignment = Enum.TextXAlignment.Left
 
Icon_2.Name = "Icon"
Icon_2.Parent = SBTN
Icon_2.BackgroundColor3 = Color3.new(1, 1, 1)
Icon_2.BackgroundTransparency = 1
Icon_2.Size = UDim2.new(0, 20, 0, 20)
Icon_2.ZIndex = 4
Icon_2.Image = "rbxassetid://413369506"
 
print(Icon_2:GetFullName())
 
RemoteName_2.Name = "RemoteName"
RemoteName_2.Parent = SBTN
RemoteName_2.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
RemoteName_2.BorderSizePixel = 1
RemoteName_2.BorderColor3 = Color3.fromRGB(62, 62, 62)
RemoteName_2.Position = UDim2.new(0, 30, 0, 0)
RemoteName_2.Size = UDim2.new(0, 140, 0, 20)
RemoteName_2.ZIndex = 4
RemoteName_2.Font = Enum.Font.SourceSansBold
RemoteName_2.FontSize = Enum.FontSize.Size14
RemoteName_2.Text = "SayMessageRequest"
RemoteName_2.TextColor3 = Color3.fromRGB(200, 200, 200)
RemoteName_2.TextSize = 11
 
 
ScriptLine.Name = "ScriptLine"
ScriptLine.Parent = Storage
ScriptLine.BackgroundColor3 = Color3.new(1, 1, 1)
ScriptLine.BackgroundTransparency = 1
ScriptLine.Size = UDim2.new(1, 0, 0, 17)
ScriptLine.ZIndex = 2
 
Line.Name = "Line"
Line.Parent = ScriptLine
Line.BackgroundColor3 = Color3.new(0.329412, 0, 0)
Line.BackgroundTransparency = 1
Line.BorderSizePixel = 0
Line.Size = UDim2.new(0, 40, 1, 0)
Line.ZIndex = 3
Line.Font = Enum.Font.SourceSansBold
Line.FontSize = Enum.FontSize.Size18
Line.Text = ""
Line.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
Line.TextSize = 17
 
SourceText.Name = "SourceText"
SourceText.Parent = ScriptLine
SourceText.BackgroundColor3 = Color3.new(1, 1, 1)
SourceText.BackgroundTransparency = 1
SourceText.Position = UDim2.new(0, 40, 0, 0)
SourceText.Size = UDim2.new(1, -40, 1, 0)
SourceText.ZIndex = 3
SourceText.Font = Enum.Font.Code
SourceText.FontSize = Enum.FontSize.Size18
SourceText.Text = ""
SourceText.TextColor3 = Color3.new(1, 1, 1)
SourceText.TextSize = 17
SourceText.TextXAlignment = Enum.TextXAlignment.Left
 
Tokens.Name = "Tokens"
Tokens.Parent = ScriptLine
Tokens.BackgroundColor3 = Color3.new(1, 1, 1)
Tokens.BackgroundTransparency = 1
Tokens.Position = UDim2.new(0, 40, 0, 0)
Tokens.Size = UDim2.new(1, -40, 1, 0)
Tokens.ZIndex = 3
Tokens.Font = Enum.Font.Code
Tokens.FontSize = Enum.FontSize.Size18
Tokens.Text = ""
Tokens.TextColor3 = Color3.new(0.392157, 0.392157, 0.392157)
Tokens.TextSize = 17
Tokens.TextXAlignment = Enum.TextXAlignment.Left
 
Strings.Name = "Strings"
Strings.Parent = ScriptLine
Strings.BackgroundColor3 = Color3.new(1, 1, 1)
Strings.BackgroundTransparency = 1
Strings.Position = UDim2.new(0, 40, 0, 0)
Strings.Size = UDim2.new(1, -40, 1, 0)
Strings.ZIndex = 5
Strings.Font = Enum.Font.Code
Strings.FontSize = Enum.FontSize.Size18
Strings.Text = ""
Strings.TextColor3 = Color3.new(1, 0.615686, 0)
Strings.TextSize = 17
Strings.TextXAlignment = Enum.TextXAlignment.Left
 
Comments.Name = "Comments"
Comments.Parent = ScriptLine
Comments.BackgroundColor3 = Color3.new(1, 1, 1)
Comments.BackgroundTransparency = 1
Comments.Position = UDim2.new(0, 40, 0, 0)
Comments.Size = UDim2.new(1, -40, 1, 0)
Comments.ZIndex = 5
Comments.Font = Enum.Font.Code
Comments.FontSize = Enum.FontSize.Size18
Comments.Text = ""
Comments.TextColor3 = Color3.fromRGB(60, 200, 60)
Comments.TextSize = 17
Comments.TextXAlignment = Enum.TextXAlignment.Left
 
RemoteHighlight.Name = "RemoteHighlight"
RemoteHighlight.Parent = ScriptLine
RemoteHighlight.BackgroundColor3 = Color3.new(1, 1, 1)
RemoteHighlight.BackgroundTransparency = 1
RemoteHighlight.Position = UDim2.new(0, 40, 0, 0)
RemoteHighlight.Size = UDim2.new(1, -40, 1, 0)
RemoteHighlight.ZIndex = 3
RemoteHighlight.Font = Enum.Font.Code
RemoteHighlight.FontSize = Enum.FontSize.Size18
RemoteHighlight.Text = ""
RemoteHighlight.TextColor3 = Color3.fromRGB(0, 145, 255)
RemoteHighlight.TextSize = 17
RemoteHighlight.TextXAlignment = Enum.TextXAlignment.Left
 
Keywords.Name = "Keywords"
Keywords.Parent = ScriptLine
Keywords.BackgroundColor3 = Color3.new(1, 1, 1)
Keywords.BackgroundTransparency = 1
Keywords.Position = UDim2.new(0, 40, 0, 0)
Keywords.Size = UDim2.new(1, -40, 1, 0)
Keywords.ZIndex = 3
Keywords.Font = Enum.Font.Code
Keywords.FontSize = Enum.FontSize.Size18
Keywords.Text = ""
Keywords.TextColor3 = Color3.new(0.231373, 1, 0)
Keywords.TextSize = 17
Keywords.TextXAlignment = Enum.TextXAlignment.Left
 
Globals.Name = "Globals"
Globals.Parent = ScriptLine
Globals.BackgroundColor3 = Color3.new(1, 1, 1)
Globals.BackgroundTransparency = 1
Globals.Position = UDim2.new(0, 40, 0, 0)
Globals.Size = UDim2.new(1, -40, 1, 0)
Globals.ZIndex = 3
Globals.Font = Enum.Font.Code
Globals.FontSize = Enum.FontSize.Size18
Globals.Text = ""
Globals.TextColor3 = Color3.new(1, 0, 0)
Globals.TextSize = 17
Globals.TextXAlignment = Enum.TextXAlignment.Left
 
Enabled.Name = "Enabled"
Enabled.Parent = SBTN
Enabled.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
Enabled.BorderSizePixel = 1
Enabled.BorderColor3 = Color3.fromRGB(30, 100, 30)
Enabled.Position = UDim2.new(0, 210, 0, 0)
Enabled.Size = UDim2.new(1, -210, 1, 0)
Enabled.ZIndex = 4
Enabled.Font = Enum.Font.SourceSansBold
Enabled.FontSize = Enum.FontSize.Size14
Enabled.Text = "Enabled"
Enabled.TextColor3 = Color3.fromRGB(60, 200, 60)
Enabled.TextSize = 14
 
FullScreen.Name = "FullScreen"
FullScreen.Parent = Ribbon
FullScreen.BackgroundColor3 = Color3.new(1, 0, 0)
FullScreen.BorderSizePixel = 0
FullScreen.Position = UDim2.new(1, -90, 0, 0)
FullScreen.Size = UDim2.new(0, 40, 0, 20)
FullScreen.ZIndex = 3
FullScreen.Font = Enum.Font.SourceSansBold
FullScreen.FontSize = Enum.FontSize.Size14
FullScreen.Text = "[~]"
FullScreen.TextColor3 = Color3.new(1, 1, 1)
FullScreen.TextSize = 14
 
--[[Exit.Name = "Exit"
Exit.Parent = Ribbon
Exit.BackgroundColor3 = Color3.new(1, 0, 0)
Exit.BorderSizePixel = 0
Exit.Position = UDim2.new(1, -140, 0, 0)
Exit.Size = UDim2.new(0, 40, 0, 20)
Exit.ZIndex = 3
Exit.Font = Enum.Font.SourceSansBold
Exit.FontSize = Enum.FontSize.Size14
Exit.Text = "[D]"
Exit.TextColor3 = Color3.new(1, 1, 1)
Exit.TextSize = 14--]]
 
SetRemotesTab.Name = "SetRemotesTab"
SetRemotesTab.Parent = BG
SetRemotesTab.Visible = false
SetRemotesTab.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
SetRemotesTab.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
SetRemotesTab.ClipsDescendants = true
SetRemotesTab.Position = UDim2.new(0, 270, 1, -50)
SetRemotesTab.Size = UDim2.new(1, -280, 0, 40)
SetRemotesTab.ZIndex = 2
 
FilterF.Name = "FilterF"
FilterF.Parent = SetRemotesTab
FilterF.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
FilterF.BorderColor3 = Color3.new(0.392157, 0.117647, 0.117647)
FilterF.Position = UDim2.new(0, 120, 0.5, -10)
FilterF.Size = UDim2.new(0, 120, 0, 20)
FilterF.ZIndex = 3
FilterF.Font = Enum.Font.SourceSansBold
FilterF.FontSize = Enum.FontSize.Size14
FilterF.Text = "FILTER FUNCTIONS"
FilterF.TextColor3 = Color3.new(0.784314, 0.235294, 0.235294)
FilterF.TextSize = 14
 
FilterE.Name = "FilterE"
FilterE.Parent = SetRemotesTab
FilterE.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
FilterE.BorderColor3 = Color3.new(0.392157, 0.117647, 0.117647)
FilterE.Position = UDim2.new(0, 10, 0.5, -10)
FilterE.Size = UDim2.new(0, 100, 0, 20)
FilterE.ZIndex = 3
FilterE.Font = Enum.Font.SourceSansBold
FilterE.FontSize = Enum.FontSize.Size14
FilterE.Text = "FILTER EVENTS"
FilterE.TextColor3 = Color3.new(0.784314, 0.235294, 0.235294)
FilterE.TextSize = 14
 
Search.Name = "Search"
Search.Parent = SetRemotesTab
Search.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
Search.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
Search.Position = UDim2.new(0, 360, 0.5, -10)
Search.Selectable = true
Search.Size = UDim2.new(1, -370, 0, 20)
Search.ZIndex = 3
Search.Font = Enum.Font.SourceSansBold
Search.FontSize = Enum.FontSize.Size14
Search.Text = "[SEARCH]"
Search.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
Search.TextSize = 14
 
lvl6Output.Name = "lvl6Output"
lvl6Output.Parent = lvl6Frame
lvl6Output.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
lvl6Output.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
lvl6Output.Position = UDim2.new(0, 0, 1, -110)
lvl6Output.Size = UDim2.new(1, 0, 0, 110)
lvl6Output.ZIndex = 3
lvl6Output.CanvasSize = UDim2.new(3, 0, 15, 0)
lvl6Output.BottomImage = "rbxassetid://148970562"
lvl6Output.MidImage = "rbxassetid://148970562"
lvl6Output.ScrollBarThickness = 5
lvl6Output.TopImage = "rbxassetid://148970562"
 
lvl6Source.Name = "lvl6Source"
lvl6Source.Parent = lvl6Frame
lvl6Source.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
lvl6Source.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
lvl6Source.Position = UDim2.new(0, 0, 0, 30)
lvl6Source.Size = UDim2.new(1, 0, 1, -160)
lvl6Source.ZIndex = 3
lvl6Source.BottomImage = "rbxassetid://148970562"
lvl6Source.CanvasSize = UDim2.new(0, 0, 20, 0)
lvl6Source.MidImage = "rbxassetid://148970562"
lvl6Source.ScrollBarThickness = 5
lvl6Source.TopImage = "rbxassetid://148970562"
 
Source_.Name = "Source_"
Source_.Parent = lvl6Source
Source_.BackgroundColor3 = Color3.new(1, 1, 1)
Source_.BackgroundTransparency = 1
Source_.Size = UDim2.new(1, 0, 1, 0)
Source_.Position = UDim2.new(0, 30, 0, 0)
Source_.ZIndex = 4
Source_.ClearTextOnFocus = false
Source_.MultiLine = true
Source_.Font = Enum.Font.Code
Source_.FontSize = Enum.FontSize.Size18
Source_.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
Source_.TextSize = 17
Source_.Text = "print(\"Welcome to R2S script editor!\")"
Source_.TextXAlignment = Enum.TextXAlignment.Left
Source_.TextYAlignment = Enum.TextYAlignment.Top
 
Comments_.Name = "Comments_"
Comments_.Parent = Source_
Comments_.BackgroundColor3 = Color3.new(1, 1, 1)
Comments_.BackgroundTransparency = 1
Comments_.Size = UDim2.new(1, 0, 1, 0)
Comments_.ZIndex = 5
Comments_.Font = Enum.Font.Code
Comments_.FontSize = Enum.FontSize.Size18
Comments_.Text = ""
Comments_.TextColor3 = Color3.new(0.235294, 0.784314, 0.235294)
Comments_.TextSize = 17
Comments_.TextXAlignment = Enum.TextXAlignment.Left
Comments_.TextYAlignment = Enum.TextYAlignment.Top
 
Globals_.Name = "Globals_"
Globals_.Parent = Source_
Globals_.BackgroundColor3 = Color3.new(1, 1, 1)
Globals_.BackgroundTransparency = 1
Globals_.Size = UDim2.new(1, 0, 1, 0)
Globals_.ZIndex = 5
Globals_.Font = Enum.Font.Code
Globals_.FontSize = Enum.FontSize.Size18
Globals_.Text = ""
Globals_.TextColor3 = Color3.new(1, 0, 0)
Globals_.TextSize = 17
Globals_.TextXAlignment = Enum.TextXAlignment.Left
Globals_.TextYAlignment = Enum.TextYAlignment.Top
 
Keywords_.Name = "Keywords_"
Keywords_.Parent = Source_
Keywords_.BackgroundColor3 = Color3.new(1, 1, 1)
Keywords_.BackgroundTransparency = 1
Keywords_.Size = UDim2.new(1, 0, 1, 0)
Keywords_.ZIndex = 5
Keywords_.Font = Enum.Font.Code
Keywords_.FontSize = Enum.FontSize.Size18
Keywords_.Text = ""
Keywords_.TextColor3 = Color3.new(0.231373, 1, 0)
Keywords_.TextSize = 17
Keywords_.TextXAlignment = Enum.TextXAlignment.Left
Keywords_.TextYAlignment = Enum.TextYAlignment.Top
 
RemoteHighlight_.Name = "RemoteHighlight_"
RemoteHighlight_.Parent = Source_
RemoteHighlight_.BackgroundColor3 = Color3.new(1, 1, 1)
RemoteHighlight_.BackgroundTransparency = 1
RemoteHighlight_.Size = UDim2.new(1, 0, 1, 0)
RemoteHighlight_.ZIndex = 5
RemoteHighlight_.Font = Enum.Font.Code
RemoteHighlight_.FontSize = Enum.FontSize.Size18
RemoteHighlight_.Text = ""
RemoteHighlight_.TextColor3 = Color3.new(0, 0.568627, 1)
RemoteHighlight_.TextSize = 17
RemoteHighlight_.TextXAlignment = Enum.TextXAlignment.Left
RemoteHighlight_.TextYAlignment = Enum.TextYAlignment.Top
 
Strings_.Name = "Strings_"
Strings_.Parent = Source_
Strings_.BackgroundColor3 = Color3.new(1, 1, 1)
Strings_.BackgroundTransparency = 1
Strings_.Size = UDim2.new(1, 0, 1, 0)
Strings_.ZIndex = 5
Strings_.Font = Enum.Font.Code
Strings_.FontSize = Enum.FontSize.Size18
Strings_.Text = ""
Strings_.TextColor3 = Color3.new(1, 0.615686, 0)
Strings_.TextSize = 17
Strings_.TextXAlignment = Enum.TextXAlignment.Left
Strings_.TextYAlignment = Enum.TextYAlignment.Top
 
Tokens_.Name = "Tokens_"
Tokens_.Parent = Source_
Tokens_.BackgroundColor3 = Color3.new(1, 1, 1)
Tokens_.BackgroundTransparency = 1
Tokens_.Size = UDim2.new(1, 0, 1, 0)
Tokens_.ZIndex = 5
Tokens_.Font = Enum.Font.Code
Tokens_.FontSize = Enum.FontSize.Size18
Tokens_.Text = ""
Tokens_.TextColor3 = Color3.new(0.392157, 0.392157, 0.392157)
Tokens_.TextSize = 17
Tokens_.TextXAlignment = Enum.TextXAlignment.Left
Tokens_.TextYAlignment = Enum.TextYAlignment.Top
 
ExecuteScript.Name = "ExecuteScript"
ExecuteScript.Parent = lvl6Frame
ExecuteScript.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
ExecuteScript.BorderColor3 = Color3.new(0.117647, 0.392157, 0.117647)
ExecuteScript.Size = UDim2.new(1, -700, 0, 20)
ExecuteScript.ZIndex = 3
ExecuteScript.Font = Enum.Font.SourceSansBold
ExecuteScript.FontSize = Enum.FontSize.Size14
ExecuteScript.Text = "EXECUTE"
ExecuteScript.TextColor3 = Color3.new(0.235294, 0.784314, 0.235294)
ExecuteScript.TextSize = 14
 
lvl6.Name = "lvl6"
lvl6.Parent = ButtonsFrame
lvl6.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
lvl6.BorderColor3 = Color3.new(0.384314, 0.384314, 0.384314)
lvl6.Position = UDim2.new(0, 840, 0.5, -10)
lvl6.Size = UDim2.new(0, 100, 0, 20)
lvl6.ZIndex = 3
lvl6.Font = Enum.Font.SourceSansBold
lvl6.FontSize = Enum.FontSize.Size14
lvl6.Text = "LVL6 "
lvl6.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
lvl6.TextSize = 14
 
lvl6Frame.Name = "lvl6Frame"
lvl6Frame.Parent = BG
lvl6Frame.BackgroundColor3 = Color3.new(1, 1, 1)
lvl6Frame.BackgroundTransparency = 1
lvl6Frame.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
lvl6Frame.Position = UDim2.new(0, 270, 0, 80)
lvl6Frame.Size = UDim2.new(1, -280, 1, -90)
lvl6Frame.ZIndex = 2
lvl6Frame.Visible = false
 
Resize.Name = "Resize"
Resize.Parent = lvl6Frame
Resize.BackgroundColor3 = Color3.new(0.392157, 0.392157, 0.392157)
Resize.BorderSizePixel = 0
Resize.Draggable = true
Resize.Position = UDim2.new(0.5, -50, 1, -130)
Resize.Size = UDim2.new(0, 100, 0, 10)
Resize.ZIndex = 3
Resize.Font = Enum.Font.SourceSans
Resize.FontSize = Enum.FontSize.Size14
Resize.Text = ""
Resize.TextSize = 14
 
ClearScript.Name = "ClearScript"
ClearScript.Parent = lvl6Frame
ClearScript.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
ClearScript.BorderColor3 = Color3.new(0.392157, 0.117647, 0.117647)
ClearScript.Position = UDim2.new(1, -280, 0, 0)
ClearScript.Size = UDim2.new(0, 280, 0, 20)
ClearScript.ZIndex = 3
ClearScript.Font = Enum.Font.SourceSansBold
ClearScript.FontSize = Enum.FontSize.Size14
ClearScript.Text = "CLEAR"
ClearScript.TextColor3 = Color3.new(0.784314, 0.235294, 0.235294)
ClearScript.TextSize = 14
 
ClearOutput.Name = "ClearOutput"
ClearOutput.Parent = lvl6Frame
ClearOutput.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
ClearOutput.BorderColor3 = Color3.new(0.392157, 0.117647, 0.117647)
ClearOutput.Position = UDim2.new(1, -680, 0, 0)
ClearOutput.Size = UDim2.new(0, 390, 0, 20)
ClearOutput.ZIndex = 3
ClearOutput.Font = Enum.Font.SourceSansBold
ClearOutput.FontSize = Enum.FontSize.Size14
ClearOutput.Text = "CLEAR OUTPUT"
ClearOutput.TextColor3 = Color3.new(0.784314, 0.235294, 0.235294)
ClearOutput.TextSize = 14
 
Label.Name = "Label"
Label.Parent = Storage
Label.BackgroundColor3 = Color3.new(1, 1, 1)
Label.BackgroundTransparency = 1
Label.Size = UDim2.new(1, 0, 0, 17)
Label.ZIndex = 4
Label.Font = Enum.Font.Code
Label.FontSize = Enum.FontSize.Size14
Label.TextColor3 = Color3.new(1, 1, 1)
Label.TextSize = 14
Label.TextXAlignment = Enum.TextXAlignment.Left
 
Lines.Name = "Lines"
Lines.Parent = lvl6Source
Lines.BackgroundColor3 = Color3.new(1, 1, 1)
Lines.BackgroundTransparency = 1
Lines.Size = UDim2.new(0, 30, 1, 0)
Lines.ZIndex = 4
Lines.Font = Enum.Font.Code
Lines.FontSize = Enum.FontSize.Size18
Lines.Text = "1"
Lines.TextColor3 = Color3.new(1, 1, 1)
Lines.TextSize = 17
Lines.TextYAlignment = Enum.TextYAlignment.Top
 
LoadSource.Name = "LoadSource"
LoadSource.Parent = ButtonsFrame
LoadSource.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
LoadSource.BorderColor3 = Color3.new(0.384314, 0.384314, 0.384314)
LoadSource.Position = UDim2.new(0, 950, 0.5, -10)
LoadSource.Size = UDim2.new(0, 100, 0, 20)
LoadSource.ZIndex = 3
LoadSource.Font = Enum.Font.SourceSansBold
LoadSource.FontSize = Enum.FontSize.Size14
LoadSource.Text = "LOAD"
LoadSource.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
LoadSource.TextSize = 14
 
Mute.Name = "Mute"
Mute.Parent = ButtonsFrame
Mute.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
Mute.BorderColor3 = Color3.fromRGB(30, 100, 30)
Mute.Position = UDim2.new(0, 1060, 0.5, -10)
Mute.Size = UDim2.new(0, 100, 0, 20)
Mute.ZIndex = 3
Mute.Font = Enum.Font.SourceSansBold
Mute.FontSize = Enum.FontSize.Size14
Mute.Text = ""
Mute.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
Mute.TextSize = 14
 
Icon_3 .Name = "Icon"
Icon_3 .Parent = Mute
Icon_3 .BackgroundColor3 = Color3.new(1, 1, 1)
Icon_3 .BackgroundTransparency = 1
Icon_3 .Position = UDim2.new(0.5, -10, 0, 0)
Icon_3 .Size = UDim2.new(0, 20, 1, 0)
Icon_3 .ZIndex = 4
Icon_3 .Image = "rbxassetid://302250236"
Icon_3 .ImageColor3 = Color3.fromRGB(60, 200, 60)
 
Refresh.Name = "Refresh"
Refresh.Parent = SetRemotesTab
Refresh.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
Refresh.BorderColor3 = Color3.new(0.380392, 0.380392, 0.380392)
Refresh.Position = UDim2.new(0, 250, 0.5, -10)
Refresh.Size = UDim2.new(0, 100, 0, 20)
Refresh.ZIndex = 3
Refresh.Font = Enum.Font.SourceSansBold
Refresh.FontSize = Enum.FontSize.Size14
Refresh.Text = "REFRESH"
Refresh.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
Refresh.TextSize = 14
 
RemoteButtons.Name = "RemoteButtons"
RemoteButtons.Parent = BG
RemoteButtons.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
RemoteButtons.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
RemoteButtons.Position = UDim2.new(0, 270, 1, -50)
RemoteButtons.Size = UDim2.new(1, -280, 0, 40)
RemoteButtons.ZIndex = 2
RemoteButtons.BottomImage = "rbxassetid://148970562"
RemoteButtons.CanvasSize = UDim2.new(2, 0, 0, 0)
RemoteButtons.MidImage = "rbxassetid://148970562"
RemoteButtons.ScrollBarThickness = 5
RemoteButtons.TopImage = "rbxassetid://148970562"
 
FireRemote.Name = "FireRemote"
FireRemote.Parent = RemoteButtons
FireRemote.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
FireRemote.BorderColor3 = Color3.new(0.384314, 0.384314, 0.384314)
FireRemote.Position = UDim2.new(0, 10, 0.5, -10)
FireRemote.Size = UDim2.new(0, 100, 0, 20)
FireRemote.ZIndex = 3
FireRemote.Font = Enum.Font.SourceSansBold
FireRemote.FontSize = Enum.FontSize.Size14
FireRemote.Text = "FIRE REMOTE"
FireRemote.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
FireRemote.TextSize = 14
 
FireDelay.Name = "FireDelay"
FireDelay.Parent = RemoteButtons
FireDelay.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
FireDelay.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
FireDelay.Position = UDim2.new(0, 290, 0.5, -10)
FireDelay.Size = UDim2.new(0, 50, 0, 20)
FireDelay.ZIndex = 3
FireDelay.Font = Enum.Font.SourceSansBold
FireDelay.FontSize = Enum.FontSize.Size14
FireDelay.Text = "0"
FireDelay.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
FireDelay.TextSize = 14
 
LoopFire.Name = "LoopFire"
LoopFire.Parent = RemoteButtons
LoopFire.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
LoopFire.BorderColor3 = Color3.new(0.384314, 0.384314, 0.384314)
LoopFire.Position = UDim2.new(0, 120, 0.5, -10)
LoopFire.Size = UDim2.new(0, 100, 0, 20)
LoopFire.ZIndex = 3
LoopFire.Font = Enum.Font.SourceSansBold
LoopFire.FontSize = Enum.FontSize.Size14
LoopFire.Text = "FOR-LOOP FIRE"
LoopFire.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
LoopFire.TextSize = 14
 
FireAmount.Name = "FireAmount"
FireAmount.Parent = RemoteButtons
FireAmount.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
FireAmount.BorderColor3 = Color3.new(0.243137, 0.243137, 0.243137)
FireAmount.Position = UDim2.new(0, 230, 0.5, -10)
FireAmount.Size = UDim2.new(0, 50, 0, 20)
FireAmount.ZIndex = 3
FireAmount.Font = Enum.Font.SourceSansBold
FireAmount.FontSize = Enum.FontSize.Size14
FireAmount.Text = "0"
FireAmount.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
FireAmount.TextSize = 14
 
Break.Name = "Break"
Break.Parent = RemoteButtons
Break.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
Break.BorderColor3 = Color3.new(0.392157, 0.117647, 0.117647)
Break.Position = UDim2.new(0, 350, 0.5, -10)
Break.Size = UDim2.new(0, 100, 0, 20)
Break.ZIndex = 3
Break.Font = Enum.Font.SourceSansBold
Break.FontSize = Enum.FontSize.Size14
Break.Text = "BREAK"
Break.TextColor3 = Color3.new(0.784314, 0.235294, 0.235294)
Break.TextSize = 14
 
WhileLoopFire.Name = "WhileLoopFire"
WhileLoopFire.Parent = RemoteButtons
WhileLoopFire.BackgroundColor3 = Color3.new(0.0784314, 0.0784314, 0.0784314)
WhileLoopFire.BorderColor3 = Color3.new(0.384314, 0.384314, 0.384314)
WhileLoopFire.Position = UDim2.new(0, 460, 0.5, -10)
WhileLoopFire.Size = UDim2.new(0, 100, 0, 20)
WhileLoopFire.ZIndex = 3
WhileLoopFire.Font = Enum.Font.SourceSansBold
WhileLoopFire.FontSize = Enum.FontSize.Size14
WhileLoopFire.Text = "INF-LOOP FIRE"
WhileLoopFire.TextColor3 = Color3.new(0.784314, 0.784314, 0.784314)
WhileLoopFire.TextSize = 14
 
local Mouse = game.Players.LocalPlayer:GetMouse()
local UIS = game:GetService('UserInputService')
local RS = game:GetService('RunService')
local canDrag = false
 
local function MakeDraggable(panel, handle)
    handle.MouseEnter:connect(function()
        canDrag = true
    end)
    handle.MouseLeave:connect(function()
        canDrag = false
    end)
    Mouse.Button1Down:connect(function()
        if canDrag then
            panel.Position = UDim2.new(0, Mouse.X + (Mouse.X - panel.AbsolutePosition.X), 0, Mouse.Y + (Mouse.Y - panel.AbsolutePosition.Y))
            local pX = Mouse.X - panel.AbsolutePosition.X
            local pY = Mouse.Y - panel.AbsolutePosition.Y
            repeat RS.RenderStepped:wait()
                panel.Position = UDim2.new(0, Mouse.X + pX, 0, Mouse.Y + pY)
            until not UIS:IsMouseButtonPressed(Enum.UserInputType.MouseButton1)
        end
    end)
end
 
MakeDraggable(BG, BG)
 
-- FrontEnd-Backend // UI Functions
 
local playSound = function(sound, int)
    spawn(function()
        local s = sound:Clone()
        s.Parent = RemoteSpy
        s:Play()
        s.PlaybackSpeed = int
    end)
end
 
local HasSpecial = function(string)
    return (string:match("%c") or string:match("%s") or string:match("%p")) ~= nil
end
 
local GetPath = function(Instance)
    local Obj = Instance
    local string = {}
    local temp = {}
    local error = false
    
    while Obj ~= game do
        if Obj == nil then
            error = true
            break
        end
        table.insert(temp, Obj.Parent == game and Obj.ClassName or tostring(Obj))
        Obj = Obj.Parent
    end
    
    table.insert(string, "game:GetService(\"" .. temp[#temp] .. "\")")
    
    for i = #temp - 1, 1, -1 do
        table.insert(string, HasSpecial(temp[i]) and "[\"" .. temp[i] .. "\"]" or "." .. temp[i])
    end
 
    return (error and "nil -- Path contained an invalid instance" or table.concat(string, ""))
end
 
local GetType = function(Instance)
    local Types = 
    {
        EnumItem = function()
            return "Enum." .. tostring(Instance.EnumType) .. "." .. tostring(Instance.Name)
        end,
        Instance = function()
            return GetPath(Instance)
        end,
        CFrame = function()
            return "CFrame.new(" .. tostring(Instance) .. ")"
        end,
        Vector3 = function()
            return "Vector3.new(" .. tostring(Instance) .. ")"
        end,
        BrickColor = function()
            return "BrickColor.new(\"" .. tostring(Instance) .. "\")"
        end,
        Color3 = function()
            return "Color3.new(" .. tostring(Instance) .. ")"
        end,
        string = function()
            return "\"" .. tostring(Instance) .. "\""
        end,
        Ray = function()
            return "Ray.new(Vector3.new(" .. tostring(Instance.Origin) .. "), Vector3.new(" .. tostring(Instance.Direction) .. "))"
        end
    }
 
    return Types[(typeof or type)(Instance)] ~= nil and Types[(typeof or type)(Instance)]() or tostring(Instance)
end
 
local size_frame = function(frame, UDim)
    frame:TweenSize(UDim, "Out", "Quint", 0.3)
end
 
local pos_frame = function(frame, UDim)
    frame:TweenPosition(UDim, "Out", "Quint", 0.3)
end
 
local size_pos_frame = function(frame, UDim, UDim2)
    frame:TweenSizeAndPosition(UDim, UDim2, "Out", "Quint", 0.3)
end
 
local resize_onchange = function(type)
    if type == "Position" then
        Resize.Position = UDim2.new(0.5, -50, 1, Resize.Position.Y.Offset)
        lvl6Source.Size = UDim2.new(1, 0, 1, Resize.Position.Y.Offset - 30)
        lvl6Output.Position = UDim2.new(0, 0, 1, Resize.Position.Y.Offset + 20)
        lvl6Output.Size = UDim2.new(1, 0, 0, 110 + (-130 - Resize.Position.Y.Offset))
        if Resize.Position.Y.Offset <= -420 then
            Resize.Position = UDim2.new(0.5, -50, 1, -420)
        elseif Resize.Position.Y.Offset >= -40 then
            Resize.Position = UDim2.new(0.5, -50, 1, -40)
        end
    end
end
 
local clear_lvl6 = function()
    playSound(topPress, 1)
    Source_.Text = ""
end
 
local onchange_lvl6source = function(type)
    if type == "Text" then
        Source_.Comments_.Text = Comments(Source_.Text)
    end
end
 
local hide = function()
    playSound(openSound, 0.9)
    size_frame(BG, UDim2.new(0, 300, 0, 20))
    pos_frame(Title, UDim2.new(0, 0, 0, 0))
    pos_frame(Remotes, UDim2.new(0, 10, 0, 100))
    pos_frame(Source, UDim2.new(0, 270, 0, 100))
    BG.Draggable = true
    SetRemotes.Visible = false
    SetRemotesTab.Visible = false
    lvl6Frame.Visible = false
    Source.Visible = true
    
    return "[]"
end
 
local show = function()
    playSound(openSound, 1)
    size_frame(BG, UDim2.new(1, -300, 1, -200))
    pos_frame(BG, UDim2.new(0.1, 0, 0.1, 0))
    pos_frame(Title, UDim2.new(0.5, -100, 0, 0))
    pos_frame(Remotes, UDim2.new(0, 10, 0, 80))
    pos_frame(Source, UDim2.new(0, 270, 0, 80))
    BG.Draggable = false
    
    return "_"
end
 
local onclick_lvl6 = function()
    print("hi")
    playSound(topPress, 1)
    lvl6Frame.Visible = true
    RemoteButtons.Visible = false
    SetRemotes.Visible = false
    SetRemotesTab.Visible = false
    Source.Visible = false
end
 
local onclick_hide = function()
    Hide.Text = Hide.Text == "_" and hide() or show()
end
 
local onclick_settings = function()
    playSound(topPress, 1)
    Source.Visible = not Source.Visible
    SetRemotes.Visible = not Source.Visible
    SetRemotesTab.Visible = not Source.Visible
    RemoteButtons.Visible = Source.Visible
    lvl6Frame.Visible = false
end
 
local onclick_remotespy = function()
    playSound(topPress, 1)
    spy_enabled = not spy_enabled
    EnableSpy.TextColor3 = EnableSpy.TextColor3 == Color3.fromRGB(60, 200, 60) and Color3.fromRGB(200, 60, 60) or Color3.fromRGB(60, 200, 60)
    EnableSpy.BorderColor3 = EnableSpy.TextColor3 == Color3.fromRGB(200, 60, 60) and Color3.fromRGB(100, 30, 30) or Color3.fromRGB(30, 100, 30)
end
 
local onclick_mute = function()
    playSound(topPress, 1)
    Mute.BorderColor3 = Mute.BorderColor3 == Color3.fromRGB(30, 100, 30) and Color3.fromRGB(100, 30, 30) or Color3.fromRGB(30, 100, 30)
    Mute.Icon.ImageColor3 = Mute.Icon.ImageColor3 == Color3.fromRGB(60, 200, 60) and Color3.fromRGB(200, 60, 60) or Color3.fromRGB(60, 200, 60)
    for i, v in pairs(sounds) do
        v.Volume = Mute.Icon.ImageColor3 == Color3.fromRGB(60, 200, 60) and 0.5 or 0
    end
end
 
local onclick_cryptstring = function()
    playSound(topPress, 1)
    encrypt_string = not encrypt_string
    CryptStrings.TextColor3 = CryptStrings.TextColor3 == Color3.fromRGB(60, 200, 60) and Color3.fromRGB(200, 60, 60) or Color3.fromRGB(60, 200, 60)
    CryptStrings.BorderColor3 = CryptStrings.TextColor3 == Color3.fromRGB(200, 60, 60) and Color3.fromRGB(100, 30, 30) or Color3.fromRGB(30, 100, 30)
end
 
local clear_logs = function()
    playSound(topPress, 1)
    Remotes:ClearAllChildren()
    remotes_fired = 0
    Total.Text = "0"
end
 
local filter_events = function()
    local n = 0
    for i, v in pairs(SetRemotes:GetChildren()) do
        v.Visible = not (FilterE.TextColor3 == Color3.fromRGB(60, 200, 60) and v.Icon.Image == "rbxassetid://413369623")
        if v.Visible == true then
            n = n + 1
            v.Position = UDim2.new(0, 10, 0, -20 + n * 30)
        else
            v.Position = UDim2.new(0, 10, 0, -20 + i * 30)
        end
    end
end
 
local filter_functions = function()
    local n = 0
    for i, v in pairs(SetRemotes:GetChildren()) do
        v.Visible = not (FilterF.TextColor3 == Color3.fromRGB(60, 200, 60) and v.Icon.Image == "rbxassetid://413369506")
        if v.Visible == true then
            n = n + 1
            v.Position = UDim2.new(0, 10, 0, -20 + n * 30)
        else
            v.Position = UDim2.new(0, 10, 0, -20 + i * 30)
        end
    end
end
 
local onclick_fevents = function()
    playSound(topPress, 1)
    FilterE.TextColor3 = FilterE.TextColor3 == Color3.fromRGB(60, 200, 60) and Color3.fromRGB(200, 60, 60) or Color3.fromRGB(60, 200, 60)
    FilterE.BorderColor3 = FilterE.TextColor3 == Color3.fromRGB(200, 60, 60) and Color3.fromRGB(100, 30, 30) or Color3.fromRGB(30, 100, 30)
    filter_events()
end
 
local onclick_ffunctions = function()
    playSound(topPress, 1)
    FilterF.TextColor3 = FilterF.TextColor3 == Color3.fromRGB(60, 200, 60) and Color3.fromRGB(200, 60, 60) or Color3.fromRGB(60, 200, 60)
    FilterF.BorderColor3 = FilterF.TextColor3 == Color3.fromRGB(200, 60, 60) and Color3.fromRGB(100, 30, 30) or Color3.fromRGB(30, 100, 30)
    filter_functions()
end
 
local Highlight = function(string, keywords)
    local K = {}
    local S = string
    local Token =
    {
        ["="] = true,
        ["."] = true,
        [","] = true,
        ["("] = true,
        [")"] = true,
        ["["] = true,
        ["]"] = true,
        ["{"] = true,
        ["}"] = true,
        [":"] = true,
        ["*"] = true,
        ["/"] = true,
        ["+"] = true,
        ["-"] = true,
        ["%"] = true,
        [";"] = true,
        ["~"] = true
    }
    for i, v in pairs(keywords) do
        K[v] = true
    end
    S = S:gsub(".", function(c)
        if Token[c] ~= nil then
            return "\32"
        else
            return c
        end
    end)
    S = S:gsub("%S+", function(c)
        if K[c] ~= nil then
            return c
        else
            return (" "):rep(#c)
        end
    end)
  
    return S
end
 
local hTokens = function(string)
    local Token =
    {
        ["="] = true,
        ["."] = true,
        [","] = true,
        ["("] = true,
        [")"] = true,
        ["["] = true,
        ["]"] = true,
        ["{"] = true,
        ["}"] = true,
        [":"] = true,
        ["*"] = true,
        ["/"] = true,
        ["+"] = true,
        ["-"] = true,
        ["%"] = true,
        [";"] = true,
        ["~"] = true
    }
    local A = ""
    string:gsub(".", function(c)
        if Token[c] ~= nil then
            A = A .. c
        elseif c == "\n" then
            A = A .. "\n"
        elseif c == "\t" then
            A = A .. "\t"
        else
            A = A .. "\32"
        end
    end)
  
    return A
end
 
 
local strings = function(string)
    local highlight = ""
    local quote = false
    string:gsub(".", function(c)
        if quote == false and c == "\"" then
            quote = true
        elseif quote == true and c == "\"" then
            quote = false
        end
        if quote == false and c == "\"" then
            highlight = highlight .. "\""
        elseif c == "\n" then
            highlight = highlight .. "\n"
        elseif c == "\t" then
            highlight = highlight .. "\t"
        elseif quote == true then
            highlight = highlight .. c
        elseif quote == false then
            highlight = highlight .. "\32"
        end
    end)
  
    return highlight
end
 
local comments = function(string)
    local ret = ""
    string:gsub("[^\r\n]+", function(c)
        local comm = false
        local i = 0
        c:gsub(".", function(n)
            i = i + 1
            if c:sub(i, i + 1) == "--" then
                comm = true
            end
            if comm == true then
                ret = ret .. n
            else
                ret = ret .. "\32"
            end
        end)
        ret = ret
    end)
    
    return ret
end
 
local copy_source = function()
    playSound(topPress, 1)
    local script = ""
    local copy
    for i, v in pairs(Source:GetChildren()) do
        script = script .. v.SourceText.Text .. "\n"
    end
    if Clipboard ~= nil then
        copy = Clipboard.set
    elseif Synapse ~= nil then
        copy = function(str)
            Synapse:Copy(str)
        end
    elseif setclipboard ~= nil then 
        copy = setclipboard
    end
    copy(script)
end
 
local onclick_fullscreen = function()
    playSound(openSound, BG.Size == UDim2.new(1, 0, 1, 40) and 0.9 or 1)
    BG.Draggable = BG.Size == UDim2.new(1, 0, 1, 40)
    if (BG.Size == UDim2.new(1, -300, 1, -200)) then
        last_bg_pos = BG.Position
        size_pos_frame(BG, UDim2.new(1, 0, 1, 40), UDim2.new(0, 0, 0, -40))
    else
        BG.Draggable = true
        size_pos_frame(BG, UDim2.new(1, -300, 1, -200), last_bg_pos)
    end
end
 
local onclick_exit = function()
    game:GetService("CoreGui").RemoteSpy:Destroy()
end
 
local filter_remotes = function(type)
    local n = 0
    if type == "Text" then
        for i, v in pairs(SetRemotes:GetChildren()) do
            if v.Name:lower():match(Search.Text:lower()) and string ~= "" then
                v.Visible = true
                n = n + 1
            else
                v.Visible = false
            end
            if v.Visible == true then
                v.Position = UDim2.new(0, 10, 0, -20 + n * 30)
            else
                v.Position = UDim2.new(0, 10, 0, -20 + i * 30)
            end
        end
    end
end
 
local fix = function(string)
    if string == "/e fix" then
        show()
        wait(0.3)
        pos_frame(BG, UDim2.new(0.1, 0, 0.1, 0))
    end
end
 
local highlight_source = function(type)
    if type == "Text" then
        Source_.Text = Source_.Text:gsub("\13", "")
        Source_.Text = Source_.Text:gsub("\t", "      ")
        local s = Source_.Text
        Source_.Keywords_.Text = Highlight(s, lua_keywords)
        Source_.Globals_.Text = Highlight(s, global_env)
        Source_.RemoteHighlight_.Text = Highlight(s, {"FireServer", "fireServer", "InvokeServer", "invokeServer"})
        Source_.Strings_.Text = strings(s)
        Source_.Tokens_.Text = hTokens(s)
        local lin = 1
        s:gsub("\n", function()
            lin = lin + 1
        end)
        Lines.Text = ""
        for i = 1, lin do
            Lines.Text = Lines.Text .. i .. "\n"
        end
    end
end
 
highlight_source("Text")
 
local format_warn_time = function()
    local d = os.date("*t")
    local tick = tostring(tick())
    return d.hour .. ":" .. (d.min < 10 and "0" .. d.min or d.min) .. ":" .. (d.sec < 10 and "0" .. d.sec or d.sec) .. "." .. tick:sub(-3)
end
 
local log_output = function(string, type, color)
    local out = Label:Clone()
    out.Text = (type == true and string:gsub("\t", "      ") or format_warn_time() .. " - " .. string:gsub("\t", "      "))
    out.TextColor3 = (color == nil and Color3.new(1, 1, 1) or color)
    out.Parent = lvl6Output
    out.Position = UDim2.new(0, 0, 0, -17 + #lvl6Output:GetChildren() * 17)
end
 
local load_source = function()
    playSound(topPress, 1)
    local script = ""
    for i, v in pairs(Source:GetChildren()) do
        script = script .. v.SourceText.Text .. "\n"
    end
    Source_.Text = (script == "" and (function() playSound(errorSound, 1) log_output("You haven't logged any remotes yet...", true) return "" end)() or script)
    lvl6Frame.Visible = true
    Source.Visible = false
    RemoteButtons.Visible = false
    SetRemotes.Visible = false
    SetRemotesTab.Visible = false
end
 
local output_format = function(...)
    local string = ""
    for i, v in pairs{...} do
        string = string .. tostring(v) .. "     "
    end
    
    return string
end
 
local execute_lvl6 = function()
    playSound(topPress, 1)
    local env = 
    {
        print = function(...)
            output_format(...):gsub("[^\r\n]+", function(line)
                log_output(line, false, Color3.new(1, 1, 1))
            end)
        end,
        warn = function(...)
            output_format(...):gsub("[^\r\n]+", function(line)
                log_output(line, false, Color3.fromRGB(255, 155, 0))
            end)
        end
    }
    local func = loadstring(Source_.Text)
    assert(not (type(func) == "nil" or type(func) == "string"), "Syntax error . . . Check script!")
    spawn(setfenv(func, setmetatable(env, {__index = getfenv()})))
end
 
local clear_output = function()
    playSound(topPress, 1)
    lvl6Output:ClearAllChildren()
end
 
local context_error = function(error, trace)
    playSound(errorSound, 1)
    error:gsub("[^\r\n]+", function(line)
        log_output(line, false, Color3.new(1, 0, 0))
    end)
    trace:gsub("[^\r\n]+", function(line)
        log_output(line, false, Color3.fromRGB(0, 100, 255))
    end)
end
 
-- FrontEnd-Connections // UI Events
 
LoadSource.MouseButton1Down:Connect(load_source)
ClearOutput.MouseButton1Down:Connect(clear_output)
ExecuteScript.MouseButton1Down:Connect(execute_lvl6)
ClearScript.MouseButton1Down:Connect(clear_lvl6)
Source_.Changed:Connect(highlight_source)
Hide.MouseButton1Down:Connect(onclick_hide)
lvl6Source.Changed:Connect(onchange_lvl6source)
Resize.Changed:Connect(resize_onchange)
lvl6.MouseButton1Down:Connect(onclick_lvl6)
Settings.MouseButton1Down:Connect(onclick_settings)
ClearList.MouseButton1Down:Connect(clear_logs)
EnableSpy.MouseButton1Down:Connect(onclick_remotespy)
ToClipboard.MouseButton1Down:Connect(copy_source)
CryptStrings.MouseButton1Down:Connect(onclick_cryptstring)
FullScreen.MouseButton1Down:Connect(onclick_fullscreen)
--Exit.MouseButton1Down:Connect(onclick_exit)
FilterE.MouseButton1Down:Connect(onclick_fevents)
FilterF.MouseButton1Down:Connect(onclick_ffunctions)
Search.Changed:Connect(filter_remotes)
Mute.MouseButton1Down:Connect(onclick_mute)
game:GetService("Players").LocalPlayer.Chatted:Connect(fix)
game:GetService("ScriptContext").Error:Connect(context_error)
 
-- Recursive Remotefill // UI-Backend
 
Parse = function(T)
    local M = {}
    for i, v in pairs(T) do
        local I = "\n\t" .. (type(i) == "number" and "[" .. i .. "] = " or "[\"" .. i .. "\"] = ")
        table.insert(M, I .. (type(v) == "table" and Parse(v) or GetType(v)))
    end
    
    return " {" .. table.concat(M, ", ") .. "\n}"
end
 
function fill(base)
    for i, v in pairs(base:GetChildren()) do
        if v.ClassName:match("Remote") and v.Name ~= "CharacterSoundEvent" then
            local B = SBTN:Clone()
            
            B.Parent = SetRemotes
            B.Icon.Image = (v.ClassName == "RemoteEvent" and "rbxassetid://413369506" or "rbxassetid://413369623")
            B.RemoteName.Text = v.Name
            B.Name = v.Name
            B.Position = UDim2.new(0, 10, 0, -20 + #SetRemotes:GetChildren() * 30)
            B.MouseButton1Down:Connect(function()
                B.Enabled.Text = B.Enabled.Text == "Enabled" and "Disabled" or "Enabled"
                B.Enabled.TextColor3 = B.Enabled.Text == "Enabled" and Color3.fromRGB(60, 200, 60) or Color3.fromRGB(200, 60, 60)
                B.Enabled.BorderColor3 = B.Enabled.Text == "Enabled" and Color3.fromRGB(30, 100, 30) or Color3.fromRGB(100, 30, 30)
                playSound(disableSound, B.Enabled.Text == "Enabled" and 1 or 0.9)
                for i, v in pairs(Remotes:GetChildren()) do
                    if (v.RemoteName.Text == B.RemoteName.Text) then
                        v.Icon.ImageColor3 = B.Enabled.Text == "Disabled" and Color3.new(1, 0, 0) or Color3.new(1, 1, 1)
                    end
                end
            end)
        end
        fill(v)
    end
end
 
fill(game)
 
-- Backend // Remotespy Backend
 
local game_meta = getrawmetatable(game)
local game_namecall = game_meta.__namecall
local namecall_dump = {}
local current_rmt = nil
local g_caller = nil
local f_return = nil
local Step = game:GetService("RunService").Stepped
local breakloop = false
local looprunning = false
 
local mwr = function() end
 
if setreadonly ~= nil then
    mwr = function()
        setreadonly(game_meta, false)
    end
elseif make_writeable ~= nil then   
    mwr = function()
        make_writeable(game_meta)
    end
end
 
mwr()
 
local namecall_script = function(object, method, ...)
    local script = "-- Script generated by R2Sv2\n-- R2Sv2 fixed by ButterflyEffect, dragging function Danisty§#9161\n-- Remote Path: " .. GetPath(object) .. "\n\32\n"
    local args = {}
    
    --[[local CN    
    if object:IsA("RemoteEvent") then
        CN = "FireServer"
    elseif object:IsA("RemoteFunction") then
        CN = "InvokeServer"
    elseif object:IsA("BindableEvent") then
        CN = "Fire"
    elseif object:IsA("BindableFunction") then
        CN = "Invoke"
    end--]]
    --local members = {}    
    
    for i, v in pairs{...} do
        script = script .. "local A_" .. i .. " = " .. (type(v) == "table" and Parse(v) or GetType(v)) .. "\n"
        table.insert(args, "A_" .. i)
    end
    
    script = script .. "local Event = " .. GetPath(object) .. "\n\n"
    script = script .. "Event:" .. tostring(method) .. "(" .. table.concat(args, ", ") .. ")"
    return script
end
 
 
local dump_script = function(script)
    Source:ClearAllChildren()
    local lines = 0
    script:gsub("[^\r\n]+", function(c)
        lines = lines + 1
        local tabs = 0
        c:gsub("%\t", function() tabs = tabs + 1 end)
        local line = ScriptLine:Clone()
        line.Parent = Source
        line.SourceText.Text = c 
        line.Line.Text = lines
        line.RemoteHighlight.Text = Highlight(c, {"FireServer", "InvokeServer", "invokeServer", "fireServer"})
        line.Position = UDim2.new(0, tabs * (17 * 2), 0, -17 + #Source:GetChildren() * 17)
        line.Globals.Text = Highlight(c, global_env)
        line.Line.Position = UDim2.new(0, 0 - tabs * (17 * 2), 0, 0)
        line.Strings.Text = strings(c)
        line.Keywords.Text = Highlight(c, lua_keywords)
        line.Tokens.Text = hTokens(c)
        line.Comments.Text = comments(c)
    end)
end
 
local log_remote = function(table)
    if SetRemotes[table.object.Name].Enabled.Text == "Disabled" then return end
    playSound(logSound, 5)
    local B = RBTN:Clone()
    g_caller = table.caller
    remotes_fired = remotes_fired + 1
    Total.Text = remotes_fired
 
    B.Parent = Remotes
    B.Position = UDim2.new(0, 10, 0, -20 + #Remotes:GetChildren() * 30)
    B.Icon.Image = table.method == "FireServer" and "rbxassetid://413369506" or "rbxassetid://413369623"
    B.RemoteName.Text = table.object.Name
    B.ID.Text = tostring(remotes_fired)
    B.MouseButton1Down:Connect(function()
        current_rmt = table.object
        playSound(topPress, 1)
        lvl6Frame.Visible = false
        SetRemotes.Visible = false
        RemoteButtons.Visible = true
        SetRemotesTab.Visible = false
        Source.Visible = true
        dump_script(table.script)
        g_caller = table.caller
        f_return = table.freturn == nil and table.object.Name .. " is not RemoteFunction" or table.freturn
    end)
    B.MouseButton2Down:Connect(function()
        local bool = B.Icon.ImageColor3 == Color3.new(1, 1, 1)
        playSound(disableSound, bool and 0.9 or 1)
        for i, v in pairs(Remotes:GetChildren()) do
            if (v.RemoteName.Text == B.RemoteName.Text) then
                v.Icon.ImageColor3 = bool and Color3.new(1, 0, 0) or Color3.new(1, 1, 1)
            end
        end
        SetRemotes[B.RemoteName.Text].Enabled.Text = not bool and "Enabled" or "Disabled"
        SetRemotes[B.RemoteName.Text].Enabled.TextColor3 = not bool and Color3.fromRGB(60, 200, 60) or Color3.fromRGB(200, 60, 60)
        SetRemotes[B.RemoteName.Text].Enabled.BorderColor3 = not bool and Color3.fromRGB(30, 100, 30) or Color3.fromRGB(100, 30, 30)
    end)
end
 
local get_namecall_dump = function(script, object, ...)
    local Ret = nil
    if object.ClassName == "RemoteFunction" then
        local freturn = {pcall(object.InvokeServer, object, ...)}
        freturn = {select(2, unpack(freturn))}
        
        if #freturn == 0 then
            Ret = object.Name .. " is a void type RemoteFunction."
        else
            Ret = "local " .. object.Name .. "_return = " .. Parse(freturn)
        end
    end
    if object.ClassName == "BindableFunction" then
        local freturn = {pcall(object.Invoke, object, ...)}
        freturn = {select(2, unpack(freturn))}
        
        if #freturn == 0 then
            Ret = object.Name .. " is a void type BindableFunction."
        else
            Ret = "local " .. object.Name .. "_return = " .. Parse(freturn)
        end
    end
    namecall_dump[#namecall_dump + 1] = 
    {   
        script = namecall_script(object, (object.ClassName == "RemoteEvent" and "FireServer" or "InvokeServer") or (object.ClassName == "BindableEvent" and "Fire" or "Invoke"), ...),
        caller = script,
        object = object,
        method = (object.ClassName == "RemoteEvent" and "FireServer" or "InvokeServer") or (object.ClassName == "BindableEvent" and "Fire" or "Invoke"),
        freturn = Ret
    }
end
 
GetReturn.MouseButton1Down:Connect(function() 
    dump_script(f_return)
    if (f_return:match("is not Remote")) then playSound(errorSound, 1) end
end)
 
Decompile.MouseButton1Down:Connect(function()
    playSound(topPress, 1)
    local source = decompile(g_caller)
        
    dump_script(type(source) == "boolean" and (function() playSound(errorSound, 1) Source.Visible = false SetRemotes.Visible = false SetRemotesTab.Visible = false lvl6Frame.Visible = true log_output("Failed to decompile...", true) return "" end)() or source)
end)
 
Step:Connect(function()
    while #namecall_dump > 0 do
        log_remote(table.remove(namecall_dump, 1))
    end
end)
 
local on_namecall = function(object, ...)
    local args = {...}
    local method = isluau() and getnamecallmethod() or table.remove(args, #args)  --FIXEDLINE
    --args[#args] = nil
    if object.Name ~= "CharacterSoundEvent" and method:match("Server") and spy_enabled == true then get_namecall_dump(getfenv(2).script, object, unpack(args)) end
 
    return game_namecall(object, ...)
end
 
local onclick_refresh = function()
    playSound(topPress, 1)
    SetRemotes:ClearAllChildren()
    wait(0.2)
    fill(game)
end
 
local infloop = function()
    playSound(topPress, 1)
    local script = ""
    for i, v in pairs(Source:GetChildren()) do
        script = script .. v.SourceText.Text .. "\n"
    end
    local source = loadstring(script)
    local delay = tonumber(FireDelay.Text)
    while wait(delay) do
        source()
        if (breakloop == true) then breakloop = false break end
    end
end
 
local forloop = function()
    playSound(topPress, 1)
    local script = ""
    for i, v in pairs(Source:GetChildren()) do
        script = script .. v.SourceText.Text .. "\n"
    end
    local source = loadstring(script)
    local delay = tonumber(FireDelay.Text)
    local amount = tonumber(FireAmount.Text)
    for i = 1, amount do
        source()
        wait(delay)
        if (breakloop == true) then breakloop = false break end 
        FireAmount.Text = tostring(amount - i)
    end
end
 
local fireremote = function()
    playSound(topPress, 1)
    local script = ""
    for i, v in pairs(Source:GetChildren()) do
        script = script .. v.SourceText.Text .. "\n"
    end
    loadstring(script)()
end
 
local enable_break = function() breakloop = true end
 
-- Backend Event Connections
 
FireRemote.MouseButton1Down:Connect(fireremote)
LoopFire.MouseButton1Down:Connect(forloop)
WhileLoopFire.MouseButton1Down:Connect(infloop)
Refresh.MouseButton1Down:Connect(onclick_refresh)
Break.MouseButton1Down:Connect(enable_break)
game_meta.__namecall = on_namecall
end)

Section:NewButton("Open gui", "GreatZ So Gay", function()
    if not _G.require then
		_G.require = require
	end
	 
	--// API References
	local GUIData = (function()
		-- Variables
		_V = 1.11
		
		local screenGui = (script:FindFirstChild("ScreenGui")) or game:GetObjects("rbxassetid://2718157603")[1]:FindFirstChild("ScreenGui", true)
		  local Container = screenGui.Frame
			local Opt = Container.OptionsFrame
			local Checkbox = Opt.Checkbox
			local Color = Opt.Color
			local Frame = Opt.Frame
			local Execute = Opt.Execute
			local Mode = Opt.Mode
			local Number = Opt.Number
			local Toggle = Opt.Toggle
		  local Mods = screenGui.Mods
			local ModLabel = Mods.Example
		
		local TextService = game:GetService("TextService")
		local UserInputService = game:GetService("UserInputService")
		local HttpService = game:GetService("HttpService")
		local Player = game:GetService("Players").LocalPlayer
		  local Mouse = Player:GetMouse()
		
		pcall(function()
			screenGui.Parent = game:GetService("CoreGui")
		end)
		
		Container.Parent = nil
		Checkbox.Parent = nil
		Color.Parent = nil
		Frame.Parent = nil
		Execute.Parent = nil
		Mode.Parent = nil
		Number.Parent = nil
		Toggle.Parent = nil
		ModLabel.Parent = nil
		
		local settingsArray = {{Object = screenGui},{}}
		local saveData = {Options = {}, Hotkeys = {}}
		
		local hotkeyFunctions = {}
		local gui = {}
		
		-- Save Functions
		local writefile = writefile or function() end
		local function Save()
			local JSONData = HttpService:JSONEncode(saveData)
			writefile("OpenGui.txt", JSONData)
		end
		
		-- Color Functions
		local color = {}
		local colors = {
			TextDisabled = Color3.fromRGB(200, 200, 200),
			TextEnabled = Color3.fromRGB(255, 255, 255),
		}
		
		local Colors = {
			Color3.fromRGB(255, 73, 73),
			Color3.fromRGB(255, 161, 66),
			Color3.fromRGB(255, 233, 62),
			Color3.fromRGB(137, 255, 64),
			Color3.fromRGB(64, 255, 140),
			Color3.fromRGB(66, 252, 255),
			Color3.fromRGB(64, 147, 255),
			Color3.fromRGB(255, 93, 253),
			Color3.fromRGB(195, 110, 255),
			Color3.fromRGB(255, 90, 134),
			Color3.fromRGB(255, 255, 255),
			Color3.fromRGB(209, 209, 209),
		}
		
		local function h2rgb(m1, m2, h)
			if h<0 then h = h+1 end
			if h>1 then h = h-1 end
			if h*6<1 then
				return m1+(m2-m1)*h*6
			elseif h*2<1 then
				return m2
			elseif h*3<2 then
				return m1+(m2-m1)*(2/3-h)*6
			else
				return m1
			end
		end
		
		function color:rgbToHsv(r, g, b)
			local a = 0
			r, g, b, a = r / 255, g / 255, b / 255, a / 255
			local max, min = math.max(r, g, b), math.min(r, g, b)
			local h, s, v
			v = max
		
			local d = max - min
			if max == 0 then s = 0 else s = d / max end
		
			if max == min then
				h = 0 -- achromatic
			else
				if max == r then
				h = (g - b) / d
				if g < b then h = h + 6 end
				elseif max == g then h = (b - r) / d + 2
				elseif max == b then h = (r - g) / d + 4
				end
				h = h / 6
			end
		
			return h, s, v
		end
		
		function color:hslToRgb(h, s, L)
			h = h / 360
			local m2 = L <= .5 and L*(s+1) or L+s-L*s
			local m1 = L*2-m2
			return
				h2rgb(m1, m2, h+1/3),
				h2rgb(m1, m2, h),
				h2rgb(m1, m2, h-1/3)
		end
		
		function color:rgbToHsl(r, g, b)
			local min = math.min(r, g, b)
			local max = math.max(r, g, b)
			local delta = max - min
		
			local h, s, l = 0, 0, (min + max) / 2
		
			if l > 0 and l < 0.5 then s = delta / (max + min) end
			if l >= 0.5 and l < 1 then s = delta / (2 - max - min) end
		
			if delta > 0 then
				if max == r and max ~= g then h = h + (g-b) / delta end
				if max == g and max ~= b then h = h + 2 + (b-r) / delta end
				if max == b and max ~= r then h = h + 4 + (r-g) / delta end
				h = h / 6
			end
		
			if h < 0 then h = h + 1 end
			if h > 1 then h = h - 1 end
		
			return h * 360, s, l
		end
		
		function color:adjustLightness(color3, amount)
			local h, s, l = self:rgbToHsl(color3.r, color3.g, color3.b)
			return Color3.new(self:hslToRgb(h, s, l + amount))
		end
		
		-- UI Functions
		function gui.tween(object,style,direction,t,goal)
			local tweenservice = game:GetService("TweenService")
			local tweenInfo = TweenInfo.new(t,Enum.EasingStyle[style],Enum.EasingDirection[direction])
			local tween = tweenservice:Create(object,tweenInfo,goal)
			tween.Completed:Connect(function()
				tween:Destroy()
			end)
			tween:Play()
			return tween
		end
		
		function gui:makeDraggable(ui, callback)
			local UserInputService = game:GetService("UserInputService")
			
			local dragging
			local dragInput
			local dragStart
			local startPos
			
			local function update(input)
				local delta = input.Position - dragStart
				ui.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
				
				if callback then
					callback(ui.Position.X.Offset, ui.Position.Y.Offset)
				end
			end
			
			ui.InputBegan:Connect(function(input)
				if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
					dragging = true
					dragStart = input.Position
					startPos = ui.Position
					
					input.Changed:Connect(function()
						if input.UserInputState == Enum.UserInputState.End then
							dragging = false
						end
					end)
				end
			end)
			
			ui.InputChanged:Connect(function(input)
				if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
					dragInput = input
				end
			end)
			
			UserInputService.InputChanged:Connect(function(input)
				if input == dragInput and dragging then
					update(input)
				end
			end)
		end
		
		function gui:unpack(data, type)
			if data == nil then return end
			if type == "UDim2" then
				return data and UDim2.new(data[1], data[2], data[3], data[4])
			elseif type == "boolean" then
				return data == 1 and true or false
			elseif type == "Color3" then
				return Color3.new(data[1], data[2], data[3])
			end
			return data
		end
		
		function gui:pack(data)
			if typeof(data) == "UDim2" then
				return {data.X.Scale, data.X.Offset, data.Y.Scale, data.Y.Offset}
			elseif typeof(data) == "boolean" then
				return data and 1 or 0
			elseif typeof(data) == "Color3" then
				return {data.r, data.g, data.b}
			end
			return data
		end
		
		function gui:getn(array)
			local n = 0
			for _, v in pairs(array) do
				n = n + 1
			end
			return n
		end
		
		function gui:setText(textLabel, text)
			text = tostring(text)
			textLabel.Text = text
			if textLabel:FindFirstChild("Opaque") then
				textLabel.Opaque.Text = text
			end
			if textLabel:FindFirstChild("Shadow") then
				textLabel.Shadow.Text = text
			end
		end
		
		function gui:onDoubleTap(guiObject, callback)
			local lastTap = tick()
			guiObject.InputBegan:Connect(function(input)
				if input.UserInputType == Enum.UserInputType.MouseButton1 then
					if tick() - lastTap < 0.25 then
						callback()
					end
					lastTap = tick()
				end
			end)
		end
		
		local connections = {}
		function gui:connect(func)
			table.insert(connections, func)
		end
		
		function gui:createList(guiObject, guiData)
			local ListLayout = guiObject.OptionsFrame.UIListLayout
			local Padding = guiObject.OptionsFrame.UIPadding
			guiObject.OptionsFrame.UIListLayout.Changed:Connect(function(Property)
				if Property == "AbsoluteContentSize" then
					guiData.ySize = ListLayout.AbsoluteContentSize.Y + 2 + Padding.PaddingTop.Offset + ListLayout.Padding.Offset * 2
				end
			end)
			
			gui:connect(function()
				if guiObject:FindFirstChild("Title") then
					local yRes = Mouse.ViewSizeY
					local diff = yRes - (guiData.yPos + guiData.ySize)
					local difference = math.clamp(diff, 0, 5000)
					guiObject.OptionsFrame.CanvasSize = UDim2.new(1, 0, 1.001, guiData.ySize - 35)
					
					if guiData.Open then
						guiObject.OptionsFrame.Size = guiObject.OptionsFrame.Size:Lerp(UDim2.new(1, 0, 0, guiData.ySize + math.clamp(diff, -5000, 0)), 0.3)
					else
						guiObject.OptionsFrame.Size = guiObject.OptionsFrame.Size:Lerp(UDim2.new(1, 0, 0, 0), 0.3)
					end
					
					guiObject.Frame.Size = guiObject.OptionsFrame.Size
				else
					if guiData.Open then
						guiObject.Size = guiObject.Size:Lerp(UDim2.new(1, -8, 0, 35 + guiData.ySize), 0.3)
					else
						guiObject.Size = guiObject.Size:Lerp(UDim2.new(1, -8, 0, 35), 0.3)
					end
				end
			end)
			
			if guiObject:FindFirstChild("Dropdown") then
				guiObject.Dropdown.Visible = false
				guiObject.Dropdown.MouseButton1Down:Connect(function()
					guiData.Open = not guiData.Open
					if guiData.Open then
						guiObject.Dropdown.Image = "rbxassetid://3559638428"
					else
						guiObject.Dropdown.Image = "rbxassetid://3554238678"
					end
				end)
			else
				gui:onDoubleTap(guiObject, function()
					guiData.Open = not guiData.Open
				end)
			end
		end
		
		function gui:textColorOnHover(guiObject, guiData)
			local hover = guiData.baseColor or guiObject.TextColor3
			local default = color:adjustLightness(hover, -0.075)
			local mdown = color:adjustLightness(hover, -0.15)
			local mouseIn
			
			local function update()
				if guiData.baseColor then
					hover = guiData.baseColor or guiObject.TextColor3
					default = color:adjustLightness(hover, -0.075)
					mdown = color:adjustLightness(hover, -0.15)
				end
			end
			
			guiObject.MouseEnter:Connect(function()
				update()
				gui.tween(guiObject, "Sine", "Out", 0.25, {
					TextColor3 = hover;
				})
				mouseIn = true
			end)
			
			guiObject.MouseLeave:Connect(function()
				mouseIn = false
				update()
				gui.tween(guiObject, "Sine", "Out", 0.25, {
					TextColor3 = default;
				})
			end)
			
			guiObject.InputBegan:Connect(function(input)
				if input.UserInputType == Enum.UserInputType.MouseButton1 then
					update()
					gui.tween(guiObject, "Sine", "Out", 0.25, {
						TextColor3 = mdown;
					})
				end
			end)
			
			guiObject.InputEnded:Connect(function(input)
				if input.UserInputType == Enum.UserInputType.MouseButton1 then
					update()
					gui.tween(guiObject, "Sine", "Out", 0.25, {
						TextColor3 = mouseIn and hover or default;
					})
				end
			end)
			
			guiObject.TextColor3 = default
		end
		
		function gui:sliderXY(sliderFrame, inputObjects, callback)
			local inputDown = false
			
			local function refresh(c1, c2)
				local sliderX = sliderFrame.AbsolutePosition.X + sliderFrame.AbsoluteSize.X
				local sliderY = sliderFrame.AbsolutePosition.Y + sliderFrame.AbsoluteSize.Y
				
				local distX = sliderX - Mouse.X
				local distY = sliderY - Mouse.Y
				
				local deltaX = 1-math.clamp(distX / sliderFrame.AbsoluteSize.X, 0, 1)
				local deltaY = 1-math.clamp(distY / sliderFrame.AbsoluteSize.Y, 0, 1)
				
				if callback then
					callback(c1 or deltaX, c2 or deltaY)
				end
			end
			
			for _, obj in pairs(inputObjects) do
				obj.InputBegan:Connect(function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						inputDown = true
						refresh()
					end
				end)
				obj.InputEnded:Connect(function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						inputDown = false
						refresh()
					end
				end)
				obj.InputChanged:Connect(function(input)
					if input == nil or input.UserInputType == Enum.UserInputType.MouseMovement then
						if inputDown then
							refresh()
						end
					end
				end)
			end
			
			return refresh
		end
		
		function gui:createSlider(sliderFrame, inputObjects, callback)
			local slider = sliderFrame.Value
			local inputDown = false
			
			local absPos = sliderFrame.AbsolutePosition.X + sliderFrame.AbsoluteSize.X
			local absSize = sliderFrame.AbsoluteSize.X
			
			local function refresh(custom)
				local mouseX = Mouse.X
				local sliderX = absPos
				local dist = sliderX - mouseX
				local delta = 1 - math.clamp(dist / absSize, 0, 1)
				
				if custom then
					delta = custom
				end
				
				slider.Size = UDim2.new(delta, 0, 1, 0)
				if callback then
					callback(delta, custom)
				end
			end
			
			for _, obj in pairs(inputObjects) do
				obj.InputBegan:Connect(function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						inputDown = true
						absPos = sliderFrame.AbsolutePosition.X + sliderFrame.AbsoluteSize.X
						absSize = sliderFrame.AbsoluteSize.X
						refresh()
					end
				end)
				obj.InputEnded:Connect(function(input)
					if input.UserInputType == Enum.UserInputType.MouseButton1 then
						inputDown = false
						refresh()
					end
				end)
				obj.InputChanged:Connect(function(input)
					if input == nil or input.UserInputType == Enum.UserInputType.MouseMovement then
						if inputDown then
							refresh()
						end
					end
				end)
			end
			
			return refresh
		end
		
		function gui:textSize(txt, vSize)
			return TextService:GetTextSize(txt.Text, txt.TextSize, txt.Font, vSize)
		end
		
		local currentHint = 0
		
		function gui:addHint(guiObject, hintText)
			local hintKey = math.random()
			guiObject.MouseEnter:Connect(function()
				hintKey = math.random()
				currentHint = hintKey
				
				wait(2)
				
				if currentHint == hintKey then
					gui:setText(screenGui.Hint, " " .. hintText .. " ")
					local textSize = gui:textSize(screenGui.Hint, Vector2.new(2500, 500))
					screenGui.Hint.Position = UDim2.new(0, Mouse.X, 0, Mouse.Y + 4)
					screenGui.Hint.Size = UDim2.new(0, textSize.X, 0, textSize.Y)
					screenGui.Hint.Visible = true
				end
			end)
			
			guiObject.MouseLeave:Connect(function()
				hintKey = math.random()
			end)
			
			Mouse.Move:Connect(function()
				if currentHint == hintKey then
					screenGui.Hint.Visible = false
				end
			end)
		end
		
		-- UI Type Library
		local lib = {}
		
		function lib.Color(data, dataArray)
			local guiObject = Color:Clone()
			local color3Value = gui:unpack(saveData.Options[data.ID].Value, "Color3") or data.Default or Color3.new(1, 1, 1)
			local guiData = {}
			
			local HSV = color3Value
			local H, S, V = color:rgbToHsv(HSV.r * 255, HSV.g * 255, HSV.b * 255)
			
			local newValue = function()
				HSV = Color3.fromHSV(H, S, V)
				guiObject.SV.BackgroundColor3 = Color3.fromHSV(H, 1, 1)
				guiObject.Indicator.BackgroundColor3 = HSV
				saveData.Options[data.ID].Value = gui:pack(HSV, "Color3")
				
				guiObject.R.Text = math.floor(HSV.r * 255)
				guiObject.G.Text = math.floor(HSV.g * 255)
				guiObject.B.Text = math.floor(HSV.b * 255)
				
				if data.Callback then
					data.Callback(HSV)
				end
			end
			
			local function updateHSV()
				H, S, V = color:rgbToHsv(HSV.r * 255, HSV.g * 255, HSV.b * 255)
			end
			
			local H_set = gui:sliderXY(guiObject.H, {guiObject.H}, function(X, Y, u)
				if not u then H = 1 - Y end
				guiObject.H.Locator.Position = UDim2.new(0.5, 0, Y, 0)
				newValue()
			end)
			
			local SV_set = gui:sliderXY(guiObject.SV, {guiObject.SV}, function(X, Y, u)
				if not u then S = X; V = 1 - Y; end
				guiObject.SV.Locator.Position = UDim2.new(X, 0, Y, 0)
				newValue()
			end)
			
			guiObject.R.FocusLost:Connect(function()
				HSV = Color3.new(guiObject.R.Text / 255, HSV.g, HSV.b)
				updateHSV()
				newValue()
			end)
			guiObject.G.FocusLost:Connect(function()
				HSV = Color3.new(HSV.r, guiObject.G.Text / 255, HSV.b)
				updateHSV()
				newValue()
			end)
			guiObject.B.FocusLost:Connect(function()
				HSV = Color3.new(HSV.r, HSV.g, guiObject.B.Text / 255)
				updateHSV()
				newValue()
			end)
			
			newValue()
			SV_set(S, 1 - V)
			H_set(0, H)
			
			guiData.ySize = 0
			guiData.Open = false
			guiData.baseColor = colors.TextEnabled
			
			gui:setText(guiObject.Label, data.Name)
			gui:textColorOnHover(guiObject.Label, guiData)
			
			return guiObject
		end
		
		function lib.Number(data, dataArray)
			local guiObject = Number:Clone()
			local Value = gui:unpack(saveData.Options[data.ID].Value, "number") or data.Default or math.floor(data.Min + (data.Max - data.Min) / 2)
			local guiData = {}
			
			local dMax = data.Max - data.Min
			local dValue = (Value - data.Min) / dMax
			
			data.Round = data.Round or 1
			
			local newValue = function(delta)
				local exactValue = data.Min + (data.Max - data.Min) * delta
				Value = math.floor(exactValue / data.Round) * data.Round
				Value = math.clamp(Value, data.Min, data.Max)
				guiObject.Indicator.Value.Text = tostring(Value)
				
				if data.Callback then
					data.Callback(Value)
				end
				saveData.Options[data.ID].Value = gui:pack(Value, "number")
			end
			
			local slideSet = gui:createSlider(guiObject.ValueFrame, {guiObject.Label, guiObject.Indicator}, newValue)
			slideSet(math.clamp(dValue, 0, 1))
			
			guiObject.Indicator.MouseButton1Down:Connect(newValue)
			guiObject.Label.MouseButton1Down:Connect(newValue)
			newValue(math.clamp(dValue, 0, 1))
			
			guiData.ySize = 0
			guiData.Open = false
			guiData.baseColor = colors.TextEnabled
			
			gui:createList(guiObject, guiData)
			gui:setText(guiObject.Label, data.Name)
			gui:textColorOnHover(guiObject.Label, guiData)
			
			return guiObject
		end
		
		function lib.Execute(data, dataArray)
			local guiObject = Execute:Clone()
			local guiData = {}
			
			local newValue = function(val)
				if data.Callback then
					data.Callback()
				end
			end
			
			guiObject.MouseEnter:Connect(function()
				gui.tween(guiObject.Indicator, "Sine", "Out", .25, {Size = UDim2.new(0, 40, 0, 25)})
			end)
			
			guiObject.MouseLeave:Connect(function()
				gui.tween(guiObject.Indicator, "Sine", "Out", .25, {Size = UDim2.new(0, 0, 0, 25)})
			end)
			
			guiObject.Indicator.MouseButton1Down:Connect(newValue)
			guiObject.Label.MouseButton1Down:Connect(newValue)
			newValue(true)
			
			guiData.ySize = 0
			guiData.Open = false
			guiData.baseColor = colors.TextEnabled
			
			gui:createList(guiObject, guiData)
			gui:setText(guiObject.Label, data.Name)
			gui:textColorOnHover(guiObject.Label, guiData)
			
			return guiObject
		end
		
		function lib.Mode(data, dataArray)
			local guiObject = Mode:Clone()
			local valueIndex = gui:unpack(saveData.Options[data.ID].Value, "number") or data.Default or 1
			local guiData = {}
			
			local newValue = function(val)
				if val == true then else
					valueIndex = (valueIndex % #data.Modes) + 1
				end
				
				local Value = data.Modes[valueIndex]
				gui:setText(guiObject.Mode, Value)
				
				if data.Callback then
					data.Callback(Value)
				end
				saveData.Options[data.ID].Value = gui:pack(valueIndex)
			end
			
			guiObject.Mode.MouseButton1Down:Connect(newValue)
			guiObject.Label.MouseButton1Down:Connect(newValue)
			newValue(true)
			
			guiData.ySize = 0
			guiData.Open = false
			guiData.baseColor = colors.TextEnabled
			
			gui:createList(guiObject, guiData)
			gui:setText(guiObject.Label, data.Name)
			gui:textColorOnHover(guiObject.Label, guiData)
			
			return guiObject
		end
		
		function lib.Hotkey(data, dataArray)
			local guiObject = Mode:Clone()
			local hotkeyInput = gui:unpack(saveData.Hotkeys[data.ID], "string") or data.Hotkey or ""
			local guiData = {}
			
			local lastInput = hotkeyInput
			local mouseIn = false
			
			guiObject.Name = "Z"
			
			local newValue = function(val)
				local input
				gui:setText(guiObject.Mode, "...")
				saveData.Hotkeys[data.ID] = nil
				
				if not val then
					input = lastInput
					mouseIn = true
					
					lastInput = nil
					
					repeat wait() until mouseIn == false or lastInput
				end
				
				if not lastInput then
					lastInput = hotkeyInput
				end
				
				saveData.Hotkeys[data.ID] = tostring(lastInput)
				hotkeyFunctions[data.ID] = data.callback
				
				hotkeyInput = tostring(lastInput)
				saveData.Options[data.ID].Value = hotkeyInput
				gui:setText(guiObject.Mode, hotkeyInput:sub(14))
			end
			
			UserInputService.InputBegan:Connect(function(input)
				if input.KeyCode == Enum.KeyCode.Unknown then return end
				if input.KeyCode == Enum.KeyCode.Backspace then lastInput = "" return end
				lastInput = tostring(input.KeyCode)
			end)
			
			guiObject.Mode.MouseButton1Down:Connect(function() newValue() end)
			guiObject.Label.MouseButton1Down:Connect(function() newValue() end)
			guiObject.MouseLeave:Connect(function()
				mouseIn = false
			end)
			newValue(true)
			
			guiData.ySize = 0
			guiData.Open = false
			guiData.baseColor = colors.TextEnabled
			
			gui:createList(guiObject, guiData)
			gui:setText(guiObject.Label, "Hotkey")
			gui:textColorOnHover(guiObject.Label, guiData)
			
			guiObject.Parent = dataArray.Object.OptionsFrame
			
			return guiObject
		end
		
		function lib.Toggle(data, dataArray)
			local guiObject = Toggle:Clone()
			local Value = gui:unpack(saveData.Options[data.ID].Value, "boolean") or data.Default or false
			local guiData = {}
			
			local modFrame = ModLabel:Clone()
			modFrame.Parent = Mods
			modFrame.TextColor3 = Colors[math.random(1, #Colors)]
			modFrame.Visible = false
			gui:setText(modFrame, data.Name)
			
			guiObject.Name = data.Name
			
			local newValue = function(val, set)
				if val == true then
				else
					if set then
						Value = set
					else
						Value = not Value
					end
				end
				
				if Value then
					gui.tween(guiObject.Indicator, "Sine", "Out", .25, {BackgroundColor3 = Color3.fromRGB(60, 222, 60)})
					guiObject.Indicator.Text = "ON"
					guiData.baseColor = colors.TextEnabled
				else
					gui.tween(guiObject.Indicator, "Sine", "Out", .25, {BackgroundColor3 = Color3.fromRGB(222, 60, 60)})
					guiObject.Indicator.Text = "OFF"
					guiData.baseColor = colors.TextDisabled
				end
				
				if data.Callback then
					data.Callback(Value)
				end
				
				saveData.Options[data.ID].Value = gui:pack(Value)
				modFrame.Visible = Value
				
			end
			
			guiObject.MouseEnter:Connect(function()
				gui.tween(guiObject.Indicator, "Sine", "Out", .25, {Size = UDim2.new(0, 40, 0, 25)})
			end)
			
			guiObject.MouseLeave:Connect(function()
				gui.tween(guiObject.Indicator, "Sine", "Out", .25, {Size = UDim2.new(0, 0, 0, 25)})
			end)
			
			gui.tween(guiObject.Indicator, "Sine", "Out", .25, {Size = UDim2.new(0, 0, 0, 25)})
			guiObject.Indicator.MouseButton1Down:Connect(function() newValue() end)
			guiObject.Label.MouseButton1Down:Connect(function() newValue() end)
			newValue(true)
			
			guiData.ySize = 0
			guiData.Open = false
			guiData.baseColor = colors.TextDisabled
			
			gui:createList(guiObject, guiData)
			gui:setText(guiObject.Label, data.Name)
			gui:textColorOnHover(guiObject.Label, guiData)
			
			data.callback = newValue
			
			return guiObject
		end
		
		function lib.Checkbox(data, dataArray)
			local guiObject = Checkbox:Clone()
			local Value = gui:unpack(saveData.Options[data.ID].Value, "boolean") or data.Default or false
			local guiData = {}
			
			guiObject.Name = "0"
			
			local newValue = function(val)
				if val == true then else
					Value = not Value
				end
				if Value then
					gui.tween(guiObject.Indicator, "Sine", "Out", .35, {Size = UDim2.new(0, 35, 0, 35)})
					guiData.baseColor = colors.TextEnabled
				else
					gui.tween(guiObject.Indicator, "Sine", "Out", .35, {Size = UDim2.new(0, 0, 0, 35)})
					guiData.baseColor = colors.TextDisabled
				end
				if data.Callback then
					data.Callback(Value)
				end
				saveData.Options[data.ID].Value = gui:pack(Value)
			end
			
			guiObject.Indicator.MouseButton1Down:Connect(newValue)
			guiObject.Label.MouseButton1Down:Connect(newValue)
			newValue(true)
			
			guiData.ySize = 0
			guiData.Open = false
			guiData.baseColor = colors.TextDisabled
			
			gui:createList(guiObject, guiData)
			gui:setText(guiObject.Label, data.Name)
			gui:textColorOnHover(guiObject.Label, guiData)
			
			return guiObject
		end
		
		function lib.Frame(data, dataArray)
			local guiObject = Frame:Clone()
			
			local guiData = {}
			guiData.ySize = 0
			guiData.Open = false
			
			gui:createList(guiObject, guiData)
			gui:setText(guiObject.Label, data.Name)
			gui:textColorOnHover(guiObject.Label, guiData)
			
			return guiObject
		end
		
		function lib.Container(data, dataArray)
			local guiObject = Container:Clone()
			
			guiObject.Position = gui:unpack(saveData.Options[data.ID].Position, "UDim2") or UDim2.new(0, 3, 0, 3 + gui:getn(settingsArray[2]) * 38)
			
			local guiData = {}
			guiData.yPos = 0
			guiData.ySize = 0
			guiData.Open = false
			
			gui:textColorOnHover(guiObject.Title, guiData)
			gui:createList(guiObject, guiData)
			gui:setText(guiObject.Title, data.Name)
			gui:makeDraggable(guiObject, function(x, y)
				guiData.yPos = y
				saveData.Options[data.ID].Position = gui:pack(guiObject.Position)
			end)
			
			return guiObject
		end
		
		-- UI Creation Library
		function gui.create(self, guiType, data)
			if self == gui then
				self = settingsArray
			end
			
			data.ID = data.Name .. "_" .. (self[1].Name or "TOP")
			
			if not saveData.Options[data.ID] then
				saveData.Options[data.ID] = {}
			end
			
			if self[1].Object:FindFirstChild("Dropdown") then
				self[1].Object.Dropdown.Visible = true
			end
			
			local dataArray = {}
			local objectArray = {}
			local selfArray = {dataArray, objectArray, create = gui.create, callback = data.Callback}
			dataArray.Name = data.Name
			dataArray.Data = data
			dataArray.Object = lib[guiType](data, dataArray)
			dataArray.self = selfArray
			
			if guiType == "Toggle" then
				lib.Hotkey(data, dataArray)
			end
			if data.Hint then
				local Object = dataArray.Object
				gui:addHint(Object:FindFirstChild("Title") or Object:FindFirstChild("Label"), data.Hint)
			end
			
			self[1][data.Name] = selfArray
			self[2][data.Name] = dataArray.Object
			
			dataArray.Object.Parent = self[1].Object:FindFirstChild("OptionsFrame") or self[1].Object
			
			return dataArray
		end
		
		-- Connection Stuff
		game:GetService("RunService").RenderStepped:Connect(function()
			for _, func in pairs(connections) do
				func()
			end
		end)
		
		UserInputService.InputBegan:Connect(function(input, gameProcessed)
			if gameProcessed then return end
			for id, key in pairs(saveData.Hotkeys) do
				if key == tostring(input.KeyCode) then
					hotkeyFunctions[id]()
				end
			end
		end)
		
		Mods.Text = "OpenGui " .. _V
		
		game.Close:Connect(function()
			Save()
		end)
		
		return {gui, saveData, screenGui}
	end)()
	 
	local _ESP = (function()
		--// Variables
		local RunService = game:GetService("RunService")
		local Players = game:GetService("Players")
		  local Player = Players.LocalPlayer
		local Screen = Instance.new("ScreenGui")
		  local Viewport = Instance.new("ViewportFrame", Screen)
		
		local module = {}
		local characters = {}
		local clones = {}
		local parts = {}
		
		module.Options = {
			Enabled = false,
			Parent = script.Parent or game.CoreGui,
			Color = Color3.new(1, 1, 1),
			ShowDescendants = false,
			TeamColor = false,
			ShowSelf = false,
			ShowTeam = false,
			Mode = "Shader",
			Opacity = 1,
			Arrow = false,
			MaxDistance = 500,
		}
		
		--// Edits
		Viewport.Size = UDim2.new(1, 0, 1, 0)
		Viewport.BackgroundTransparency = 1
		Viewport.CurrentCamera = workspace.CurrentCamera
		Screen.IgnoreGuiInset = true
		
		--// Functions
		local function getParts(Model)
			local parts = {}
			local descendants = Model:GetDescendants()
			local descendantsn = #descendants
			for i = 1, descendantsn do
				local desc = descendants[i]
				if desc:IsA("BasePart") then
					table.insert(parts, desc)
				end
			end
			return parts
		end
		
		local function getPart(Model)
			return Model.PrimaryPart or Model:FindFirstChild("HumanoidRootPart") or Model:FindFirstChildWhichIsA("Part")
		end
		
		function module:Clone(Object)
			local isArchivable = Object.Archivable
			local Clone
			
			Object.Archivable = true
			Clone = Object:Clone()
			Object.Archivable = isArchivable
			
			for _, child in pairs(Clone:GetDescendants()) do
				if child:IsA("Clothing") or child:IsA("Decal") or child:IsA("Script") or child:IsA("LocalScript") or child:IsA("Sound") then
					child:Destroy()
				elseif child:IsA("BasePart") then
					child.Color = Color3.new(1, 1, 1)
					child.Material = "ForceField"
				elseif child:IsA("Humanoid") then
					child.DisplayDistanceType = "None"
				elseif child:IsA("SpecialMesh") then
					child.TextureId = "rbxassetid://55054494"
				elseif child:IsA("MeshPart") then
					child.TextureID = "rbxassetid://55054494"
				end
			end
			
			return Clone
		end
		
		function module:Enable()
			module.Options.Enabled = true
			Screen.Parent = module.Options.Parent
			
			module:ReloadCharacters()
		end
		
		function module:Disable()
			module.Options.Enabled = false
			Screen.Parent = nil
		end
		
		function module:ReloadCharacters()
			Viewport:ClearAllChildren()
			if module.Options.Mode ~= "Shader" then
				return
			end
			for player, character in pairs(characters) do
				local clone = module:Clone(character)
				clone.Name = player.Name
				clone.Parent = Viewport
				clones[player] = clone
			end
		end
		
		local function newPlayer(player)
			if player.Character then
				characters[player] = player.Character
				
				local clone = module:Clone(player.Character)
				clone.Name = player.Name
				clone.Parent = Viewport
				clones[player] = clone
			end
			player.CharacterAdded:Connect(function(char)
				if clones[player] then
					clones[player]:Destroy()
					clones[player] = nil
				end;if characters[player] then
					characters[player]:Destroy()
					characters[player] = nil
				end
				
				characters[player] = char
				
				local clone = module:Clone(char)
				clone.Name = player.Name
				clone.Parent = Viewport
				clones[player] = clone
			end)
		end
		
		Players.PlayerAdded:Connect(newPlayer)
		Players.PlayerRemoving:Connect(function(player)
			if clones[player] then
				clones[player]:Destroy()
				clones[player] = nil
			end;if characters[player] then
				characters[player]:Destroy()
				characters[player] = nil
			end
		end)
		for _, player in pairs(Players:GetPlayers()) do
			newPlayer(player)
		end
		
		RunService.RenderStepped:Connect(function()
			if module.Options.Enabled and module.Options.Mode == "Shader" then
				for player, character in pairs(characters) do
					local clone = clones[player]
					local target = getPart(clone)
					if target then
						if ((player.Team == Player.Team and module.Options.ShowTeam) or player.Team ~= Player.Team) and (target.Position - workspace.CurrentCamera.CFrame.p).Magnitude <= module.Options.MaxDistance then
							if (player == Player and module.Options.ShowSelf) or player ~= Player then
								local parts = getParts(clone)
								for i = 1, #parts do
									local obj = parts[i]
									local cor = character:FindFirstChild(obj.Name, true)
									if character:FindFirstChild(obj.Parent.Name) then
										cor = character:FindFirstChild(obj.Parent.Name):FindFirstChild(obj.Name)
									end
									
									if cor and obj then
										if module.Options.TeamColor then
											obj.Color = player.TeamColor.Color
										else
											obj.Color = Color3.new(1, 1, 1)
										end
										if module.Options.ShowDescendants then
											obj.CFrame = cor.CFrame
										elseif obj.Parent == clone then
											obj.CFrame = cor.CFrame
										else
											obj.CFrame = CFrame.new(10000, 10000, 10000)
										end
									end
								end
								if clone.Parent == nil then
									clone.Parent = Viewport
								end
							else
								clone.Parent = nil
							end
						else
							clone.Parent = nil
						end
					else
						clone.Parent = nil
					end
				end
				Viewport.ImageColor3 = module.Options.Color
				Viewport.ImageTransparency = 1 - module.Options.Opacity
			end
		end)
		
		return module
		
	end)()
	local _ESP2D = (function()
		--// Variables
		local RunService = game:GetService("RunService")
		local Players = game:GetService("Players")
		  local Player = Players.LocalPlayer
		
		local module = {}
		local characters = {}
		local esp = {}
		
		module.Options = {
			Enabled = false,
			Parent = script.Parent or game.CoreGui,
			Color = Color3.new(1, 1, 1),
			TeamColor = false,
			ShowSelf = false,
			ShowTeam = false,
			ShowDescendants = false,
			Opacity = 1,
			Mode = "Box",
			Arrow = false,
			MaxDistance = 500,
		}
		
		--// Functions
		local function getParts(Model)
			local parts = {}
			local descendants = (module.Options.ShowDescendants and Model:GetDescendants()) or Model:GetChildren()
			local descendantsn = #descendants
			for i = 1, descendantsn do
				local desc = descendants[i]
				if desc:IsA("BasePart") then
					table.insert(parts, desc)
				end
			end
			return parts
		end
		
		local function getPart(Model)
			return Model.PrimaryPart or Model:FindFirstChild("HumanoidRootPart") or Model:FindFirstChildWhichIsA("Part")
		end
		
		function module:Enable()
			module.Options.Enabled = true
			module:ReloadCharacters()
		end
		
		function module:Disable()
			module.Options.Enabled = false
		end
		
		function module:LoadCharacter(player, char)
			local boxes = {}
			if module.Options.Mode == "Default" then
				local parts = getParts(char)
				for i = 1, #parts do
					local part = parts[i]
					local adornment = Instance.new("BoxHandleAdornment", module.Options.Parent)
					adornment.Adornee = part
					adornment.AlwaysOnTop = true
					adornment.Color3 = module.Options.Color
					adornment.Size = part.Size
					adornment.ZIndex = 1
					adornment.Transparency = 1 - module.Options.Opacity
					if module.Options.TeamColor then
						adornment.Color3 = player.TeamColor.Color
					end
					
					table.insert(boxes, adornment)
				end
				
				local part = getPart(char)
				if module.Options.Arrow then
					local arrow = Instance.new("Handles", module.Options.Parent)
					arrow.Adornee = part
					arrow.Faces = Faces.new(Enum.NormalId.Front)
					arrow.Style = Enum.HandlesStyle.Movement
					arrow.Color3 = module.Options.Color
					if module.Options.TeamColor then
						arrow.Color3 = player.TeamColor.Color
					end
					table.insert(boxes, arrow)
				end
			elseif module.Options.Mode == "Box" then
				local part = getPart(char)
				local adornment = Instance.new("BoxHandleAdornment", module.Options.Parent)
				adornment.Adornee = part
				adornment.AlwaysOnTop = true
				adornment.Color3 = module.Options.Color
				adornment.Size = char:GetExtentsSize()
				adornment.ZIndex = 1
				adornment.Transparency = 1 - module.Options.Opacity
				if module.Options.TeamColor then
					adornment.Color3 = player.TeamColor.Color
				end
				
				if module.Options.Arrow then
					local arrow = Instance.new("Handles", module.Options.Parent)
					arrow.Adornee = part
					arrow.Faces = Faces.new(Enum.NormalId.Front)
					arrow.Style = Enum.HandlesStyle.Movement
					arrow.Color3 = module.Options.Color
					if module.Options.TeamColor then
						arrow.Color3 = player.TeamColor.Color
					end
					table.insert(boxes, arrow)
				end
				
				table.insert(boxes, adornment)
			elseif module.Options.Mode == "Square" then
				local part = getPart(char)
				local billboard = (function()
			local partsWithId = {}
			local awaitRef = {}
			
			local root = {
				ID = 0;
				Type = "BillboardGui";
				Properties = {
					ClipsDescendants = true;
					LightInfluence = 1;
					Name = "B";
					ZIndexBehavior = Enum.ZIndexBehavior.Sibling;
					StudsOffset = Vector3.new(0,-0.5,0);
					Active = true;
					AlwaysOnTop = true;
					Size = UDim2.new(5,0,6,0);
				};
				Children = {
					{
						ID = 1;
						Type = "Frame";
						Properties = {
							AnchorPoint = Vector2.new(0.5,0.5);
							BackgroundTransparency = 0.5;
							Position = UDim2.new(0.5,0,0.5,0);
							BorderColor3 = Color3.new(4/51,4/51,4/51);
							Size = UDim2.new(1,-4,1,-4);
							BorderSizePixel = 2;
							BackgroundColor3 = Color3.new(1,1,1);
						};
						Children = {};
					};
				};
			};
			
			local function Scan(item, parent)
				local obj = Instance.new(item.Type)
				if (item.ID) then
					local awaiting = awaitRef[item.ID]
					if (awaiting) then
						awaiting[1][awaiting[2]] = obj
						awaitRef[item.ID] = nil
					else
						partsWithId[item.ID] = obj
					end
				end
				for p,v in pairs(item.Properties) do
					if (type(v) == "string") then
						local id = tonumber(v:match("^_R:(%w+)_$"))
						if (id) then
							if (partsWithId[id]) then
								v = partsWithId[id]
							else
								awaitRef[id] = {obj, p}
								v = nil
							end
						end
					end
					obj[p] = v
				end
				for _,c in pairs(item.Children) do
					Scan(c, obj)
				end
				obj.Parent = parent
				return obj
			end
			
			return function() return Scan(root, nil) end
		end)()()
				billboard.Parent = module.Options.Parent
				billboard.Adornee = part
				billboard.Frame.BackgroundColor3 = module.Options.Color
				billboard.Frame.Transparency = 1 - module.Options.Opacity
				if module.Options.TeamColor then
					billboard.Frame.Color3 = player.TeamColor.Color
				end
				
				if module.Options.Arrow then
					local arrow = Instance.new("Handles", module.Options.Parent)
					arrow.Adornee = part
					arrow.Faces = Faces.new(Enum.NormalId.Front)
					arrow.Style = Enum.HandlesStyle.Movement
					arrow.Color3 = module.Options.Color
					if module.Options.TeamColor then
						arrow.Color3 = player.TeamColor.Color
					end
					table.insert(boxes, arrow)
				end
				
				table.insert(boxes, billboard)
			end
			esp[player] = boxes
		end
		
		function module:ReloadCharacters()
			for plr, tbl in pairs(esp) do
				for i, v in pairs(tbl) do
					v:Destroy()
				end
				esp[plr] = {}
			end
			if module.Options.Enabled then
				for player, character in pairs(characters) do
					local target = getPart(character)
					if target then
						if ((player.Team == Player.Team and module.Options.ShowTeam) or player.Team ~= Player.Team) and target and (target.Position - workspace.CurrentCamera.CFrame.p).Magnitude <= module.Options.MaxDistance then
							if (player == Player and module.Options.ShowSelf) or player ~= Player then
								module:LoadCharacter(player, character)
							end
						end
					end
				end
			end
		end
		
		local function newPlayer(player)
			if player.Character then
				characters[player] = player.Character
				module:LoadCharacter(player, player.Character)
			end
			player.CharacterAdded:Connect(function(char)
				if esp[player] then
					for i, v in pairs(esp[player]) do
						v:Destroy()
					end
					esp[player] = {}
				end
				
				characters[player] = char
				module:LoadCharacter(player, player.Character)
			end)
		end
		
		Players.PlayerAdded:Connect(newPlayer)
		Players.PlayerRemoving:Connect(function(player)
			if esp[player] then
				for i, v in pairs(esp[player]) do
					v:Destroy()
				end
				esp[player] = {}
				characters[player] = nil
			end
		end)
		for _, player in pairs(Players:GetPlayers()) do
			newPlayer(player)
		end
		
		spawn(function()
			while wait(2) do
				module:ReloadCharacters()
			end
		end)
		
		return module
		
	end)()
	local _Chams = (function()
		--// Variables
		local RunService = game:GetService("RunService")
		local Players = game:GetService("Players")
		  local Player = Players.LocalPlayer
		local Screen = Instance.new("ScreenGui")
		  local Viewport = Instance.new("ViewportFrame", Screen)
		
		local module = {}
		local characters = {}
		local clones = {}
		local parts = {}
		
		module.Options = {
			Enabled = false,
			Parent = script.Parent or game.CoreGui,
			Color = Color3.new(1, 1, 1),
			ShowDescendants = false,
			TeamColor = false,
			ShowSelf = false,
			ShowTeam = false,
			Mode = "Shader",
			Opacity = 1,
			MaxDistance = 500,
		}
		
		--// Edits
		Viewport.Size = UDim2.new(1, 0, 1, 0)
		Viewport.BackgroundTransparency = 1
		Viewport.CurrentCamera = workspace.CurrentCamera
		Screen.IgnoreGuiInset = true
		
		--// Functions
		local function getParts(Model)
			local parts = {}
			local descendants = Model:GetDescendants()
			local descendantsn = #descendants
			for i = 1, descendantsn do
				local desc = descendants[i]
				if desc:IsA("BasePart") then
					table.insert(parts, desc)
				end
			end
			return parts
		end
		
		local function getPart(Model)
			return Model.PrimaryPart or Model:FindFirstChild("HumanoidRootPart") or Model:FindFirstChildWhichIsA("Part")
		end
		
		function module:Clone(Object)
			local isArchivable = Object.Archivable
			local Clone
			
			Object.Archivable = true
			Clone = Object:Clone()
			Object.Archivable = isArchivable
			
			if module.Options.Mode == "Shader" then
				Viewport.Ambient = Color3.fromRGB(200, 200, 200)
			else
				Viewport.Ambient = Color3.fromRGB(255, 255, 255)
			end
			
			for _, child in pairs(Clone:GetDescendants()) do
				if child:IsA("Script") or child:IsA("LocalScript") or child:IsA("Sound") then
					child:Destroy()
				elseif child:IsA("Humanoid") then
					child.DisplayDistanceType = "None"
				elseif module.Options.Mode ~= "Shader" then
					if child:IsA("SpecialMesh") then
						child.TextureId = ""
					elseif child:IsA("MeshPart") then
						child.TextureID = ""
					elseif child:IsA("BasePart") then
						child.Color = Color3.new(1, 1, 1)
						child.Material = "Neon"
					elseif child:IsA("Clothing") or child:IsA("Decal") then
						child:Destroy()
					end
				end
			end
			
			return Clone
		end
		
		function module:Enable()
			module.Options.Enabled = true
			Screen.Parent = module.Options.Parent
			
			module:ReloadCharacters()
		end
		
		function module:Disable()
			module.Options.Enabled = false
			Screen.Parent = nil
		end
		
		function module:ReloadCharacters()
			Viewport:ClearAllChildren()
			for player, character in pairs(characters) do
				local clone = module:Clone(character)
				clone.Name = player.Name
				clone.Parent = Viewport
				clones[player] = clone
			end
		end
		
		local function newPlayer(player)
			if player.Character then
				characters[player] = player.Character
				
				local clone = module:Clone(player.Character)
				clone.Name = player.Name
				clone.Parent = Viewport
				clones[player] = clone
			end
			player.CharacterAdded:Connect(function(char)
				if clones[player] then
					clones[player]:Destroy()
					clones[player] = nil
				end;if characters[player] then
					characters[player]:Destroy()
					characters[player] = nil
				end
				
				characters[player] = char
				
				local clone = module:Clone(char)
				clone.Name = player.Name
				clone.Parent = Viewport
				clones[player] = clone
			end)
		end
		
		Players.PlayerAdded:Connect(newPlayer)
		Players.PlayerRemoving:Connect(function(player)
			if clones[player] then
				clones[player]:Destroy()
				clones[player] = nil
			end;if characters[player] then
				characters[player]:Destroy()
				characters[player] = nil
			end
		end)
		for _, player in pairs(Players:GetPlayers()) do
			newPlayer(player)
		end
		
		RunService.RenderStepped:Connect(function()
			if module.Options.Enabled then
				for player, character in pairs(characters) do
					local clone = clones[player]
					local target = getPart(clone)
					
					if target then
						if ((player.Team == Player.Team and module.Options.ShowTeam) or player.Team ~= Player.Team) and target and (target.Position - workspace.CurrentCamera.CFrame.p).Magnitude <= module.Options.MaxDistance then
							if (player == Player and module.Options.ShowSelf) or player ~= Player then
								local parts = getParts(clone)
								for i = 1, #parts do
									local obj = parts[i]
									local cor = character:FindFirstChild(obj.Name, true)
									if character:FindFirstChild(obj.Parent.Name) then
										cor = character:FindFirstChild(obj.Parent.Name):FindFirstChild(obj.Name)
									end
									
									if cor and obj then
										if module.Options.TeamColor then
											obj.Color = player.TeamColor.Color
										elseif module.Options.Mode ~= "Shader" then
											obj.Color = Color3.new(1, 1, 1)
										end
										if module.Options.ShowDescendants then
											obj.CFrame = cor.CFrame
										elseif obj.Parent == clone then
											obj.CFrame = cor.CFrame
										else
											obj.CFrame = CFrame.new(10000, 10000, 10000)
										end
									end
								end
								if clone.Parent == nil then
									clone.Parent = Viewport
								end
							else
								clone.Parent = nil
							end
						else
							clone.Parent = nil
						end
					else
						clone.Parent = nil
					end
				end
				Viewport.ImageColor3 = module.Options.Color
				Viewport.ImageTransparency = 1 - module.Options.Opacity
			end
		end)
		
		return module
		
	end)()
	local _Tracers = (function()
		--// Variables
		local RunService = game:GetService("RunService")
		local Players = game:GetService("Players")
		  local Player = Players.LocalPlayer
		local Screen = Instance.new("ScreenGui")
		local Camera = workspace.CurrentCamera
		
		local module = {}
		local characters = {}
		local tracers = {}
		
		module.Options = {
			Enabled = false,
			Parent = script.Parent or game.CoreGui,
			Color = Color3.new(1, 1, 1),
			TeamColor = false,
			ShowSelf = false,
			ShowTeam = false,
			Opacity = 1,
			Radius = 1,
			MaxDistance = 500,
		}
		
		Screen.Parent = module.Options.Parent
		Screen.IgnoreGuiInset = true
		
		--// Functions
		local function getParts(Model)
			local parts = {}
			local descendants = Model:GetDescendants()
			local descendantsn = #descendants
			for i = 1, descendantsn do
				local desc = descendants[i]
				if desc:IsA("BasePart") then
					table.insert(parts, desc)
				end
			end
			return parts
		end
		
		local function getPart(Model)
			return Model.PrimaryPart or Model:FindFirstChild("HumanoidRootPart") or Model:FindFirstChildWhichIsA("Part")
		end
		
		function module:Enable()
			module.Options.Enabled = true
			module:ReloadCharacters()
		end
		
		function module:Disable()
			module.Options.Enabled = false
			for plr, line in pairs(tracers) do
				if line then
					line[1]:Destroy()
				end
				tracers[plr] = nil
			end
		end
		
		function module:LoadCharacter(player, char)
			local tracer = {}
			local target = getPart(char)
			if target then
				local line = Instance.new("Part", Screen)
				line.Transparency = 1
				line.Anchored = true
				line.CanCollide = false
				
				local adornment = Instance.new("LineHandleAdornment", line)
				adornment.Name = "A"
				adornment.AlwaysOnTop = true
				adornment.ZIndex = 1
				adornment.Adornee = line
				
				tracer[1] = line
				tracer[2] = target
				tracer[3] = player
			else
				return
			end
			
			tracers[player] = tracer
		end
		
		function module:ReloadCharacters()
			for plr, line in pairs(tracers) do
				if line then
					line[1]:Destroy()
				end
				tracers[plr] = nil
			end
			if module.Options.Enabled then
				for player, character in pairs(characters) do
					if (player.Team == Player.Team and module.Options.ShowTeam) or player.Team ~= Player.Team then
						if (player == Player and module.Options.ShowSelf) or player ~= Player then
							module:LoadCharacter(player, character)
						end
					end
				end
			end
		end
		
		local function newPlayer(player)
			if player.Character then
				characters[player] = player.Character
				module:LoadCharacter(player, player.Character)
			end
			player.CharacterAdded:Connect(function(char)
				if tracers[player] then
					tracers[player][1]:Destroy()
					tracers[player] = nil
				end
				char:WaitForChild("Humanoid")
				characters[player] = char
				module:LoadCharacter(player, player.Character)
			end)
		end
		
		Players.PlayerAdded:Connect(newPlayer)
		Players.PlayerRemoving:Connect(function(player)
			if tracers[player] then
				if tracers[player] then
					tracers[player][1]:Destroy()
					tracers[player] = nil
				end
				characters[player] = nil
			end
		end)
		for _, player in pairs(Players:GetPlayers()) do
			newPlayer(player)
		end
		
		local function divideUDim(udim, factor)
			return UDim2.new(udim.X.Scale / factor, udim.X.Offset / factor, udim.Y.Scale / factor, udim.Y.Offset / factor)
		end
		
		RunService.RenderStepped:Connect(function()
			if module.Options.Enabled then
				for player, data in pairs(tracers) do
					local line, target = unpack(data)
					if (target and (player.Team == Player.Team and module.Options.ShowTeam) or player.Team ~= Player.Team) and (target.Position - Camera.CFrame.p).Magnitude <= module.Options.MaxDistance then
						if (player == Player and module.Options.ShowSelf) or player ~= Player then
							if line.Parent ~= Screen then
								line.Parent = Screen
							end
							
							local point1 = (Camera.CFrame * CFrame.new(0, 0, -0.5) - Vector3.new(0, 3, 0)).p
							local point2 = target.Position - Vector3.new(0, 3, 0)
							
							local distance = point1 - point2
							local magnitude = distance.Magnitude
							
							local c = module.Options.Color
							
							line.CFrame = CFrame.new(point1, point2)
							
							line.A.Thickness = module.Options.Radius
							line.A.Length = magnitude
							line.A.Color3 = Color3.new(c.r*5,c.g*5,c.b*5)
							line.A.Transparency = 1 - module.Options.Opacity
						else
							line.Parent = nil
						end
					else
						line.Parent = nil
					end
				end
			end
		end)
		
		spawn(function()
			while wait(2) do
				if module.Options.Enabled then
					module:ReloadCharacters()
				end
			end
		end)
		
		return module
		
	end)()
	local _Aimbot = (function()
		--// Variables
		local RunService = game:GetService("RunService")
		local UserInputService = game:GetService("UserInputService")
		local Players = game:GetService("Players")
		  local Player = Players.LocalPlayer
			local Mouse = Player:GetMouse()
		local Camera = workspace.CurrentCamera
		
		local nearestCharacters = {}
		local module = {}
		
		module.Options = {
			Easing = 2,
			Enabled = false,
			ShowTeams = false,
			MaxDistance = 500,
			Legit = false,
			AimPart = "Head",
			Onscreen = false,
			Visible = true,
			Mode = "Nearest",
			Radius = 250,
		}
		
		--// Functions
		local function findPart(Model)
			return Model:FindFirstChild(module.Options.AimPart) or Model:FindFirstChild("HumanoidRootPart") or Model.PrimaryPart or Model:FindFirstChildWhichIsA("Part", true)
		end
		
		local mousemoverel = (mousemoverel or (Input and Input.MouseMove)) or function() end
		
		local function mouseMove(x, y, depth)
			local v1, v2 = Vector2.new(x, y), Vector2.new(Mouse.X, Mouse.Y)
			local viewCenter = Vector2.new(Mouse.ViewSizeX/2, Mouse.ViewSizeY/2)
			
			if depth < 0 then
				local n = 1
				if (v1 - v2).X < 0 then
					n = -1
				end
				if math.abs(v1.X - v2.X) < Mouse.ViewSizeX * 1.5 then
					n = n / 2
				end
				v1 = v1 + Vector2.new(Mouse.ViewSizeX * n, 0)
			end
			
			local diff = (v1 - v2) / module.Options.Easing
			
			if module.Options.Legit then
				diff = diff.Unit * diff.Magnitude
			end
			
			mousemoverel(diff.X, diff.Y)
		end
		
		local function updateMouse(target)
			if not target then return end
			local posVector3 = Camera:WorldToScreenPoint(target.Position)
			local posVector2, distance = Vector2.new(posVector3.X, posVector3.Y), posVector3.Z
			mouseMove(posVector2.X, posVector2.Y, posVector3.Z)
		end
		
		local function updateNearest()
			nearestCharacters = {}
			for _, player in pairs(Players:GetPlayers()) do
				if player ~= Player then
					if (player.Team == Player.Team and module.Options.ShowTeams) or player.Team ~= Player.Team then
						if player.Character then
							local part = findPart(player.Character)
							if part then --too many ifs
								local distance = (part.Position - Camera.CFrame.p).Magnitude
								
								local a, onScreen = Camera:WorldToScreenPoint(part.Position)
								local obstructed = #Camera:GetPartsObscuringTarget({part.Position}, {player.Character, Player.Character}) > 0
								
								if distance <= module.Options.MaxDistance then
									if (module.Options.Onscreen and onScreen) or not module.Options.Onscreen then
										if (module.Options.Visible and not obstructed) or not module.Options.Visible then
											table.insert(nearestCharacters, {tostring(distance), part, a.Z})
										end
									end
								end
							end
						end
					end
				end
			end
		end
		
		local windowFocused = true
		RunService.RenderStepped:Connect(function()
			if module.Options.Enabled == false or not windowFocused then return end
			updateNearest()
			
			local dist, nearestPart = 2048
			
			table.sort(nearestCharacters, function(a, b)
				local D1, NP1 = unpack(a)
				local D2, NP2 = unpack(b)
				return tonumber(D1) < tonumber(D2)
			end)
			
			if module.Options.Mode == "Nearest" then
				if nearestCharacters[1] then
					local D, NP = unpack(nearestCharacters[1])
					nearestPart = NP
				end
			else
				for i, v in pairs(nearestCharacters) do
					local D, NP, Depth = unpack(v)
					
					local pV3 = Camera:WorldToScreenPoint(NP.Position)
					local v1, v2 = Vector2.new(pV3.X, pV3.Y), Vector2.new(Mouse.X, Mouse.Y)
					
					if (v1 - v2).Magnitude <= module.Options.Radius and Depth >= 0 then
						nearestPart = NP
						break
					end
				end
			end
			
			if nearestPart then
				updateMouse(nearestPart)
			end
		end)
		
		UserInputService.WindowFocused:Connect(function()
			windowFocused = true
		end)
		UserInputService.WindowFocusReleased:Connect(function()
			windowFocused = false
		end)
		
		return module
		
	end)()
	local _Flight = (function()
		--// Variables
		local RunService = game:GetService("RunService")
		local UserInputService = game:GetService("UserInputService")
		local Players = game:GetService("Players")
		  local Player = Players.LocalPlayer
			local character = Player.Character
		local camera = workspace.CurrentCamera
		
		local module = {}
		module.Options = {
			Speed = 5,
			Smoothness = 0.2,
		}
		
		local lib, connections = {}, {}
		lib.connect = function(name, connection)
			connections[name .. tostring(math.random(1000000, 9999999))] = connection
			return connection
		end
		lib.disconnect = function(name)
			for title, connection in pairs(connections) do
				if title:find(name) == 1 then
					connection:Disconnect()
				end
			end
		end
		
		--// Functions
		local flyPart
		
		local function flyEnd()
			lib.disconnect("fly")
			if flyPart then
				--flyPart:Destroy()
			end
			character:FindFirstChildWhichIsA("Humanoid").PlatformStand = false
			if character and character.Parent and flyPart then
				for _, part in pairs(character:GetDescendants()) do
					if part:IsA("BasePart") then
						part.Velocity = Vector3.new()
					end
				end
			end
		end
		
		module.flyStart = function(enabled)
			if not enabled then flyEnd() return end
			local dir = {w = false, a = false, s = false, d = false}
			local cf = Instance.new("CFrameValue")
			
			flyPart = flyPart or Instance.new("Part")
			flyPart.Anchored = true
			pcall(function()
				flyPart.CFrame = character.HumanoidRootPart.CFrame
			end)
			
			lib.connect("fly", RunService.Heartbeat:Connect(function()
				if not character or not character.Parent or not character:FindFirstChild("HumanoidRootPart") then return end
		
				local primaryPart = character.HumanoidRootPart
				local humanoid = character:FindFirstChildWhichIsA("Humanoid")
				local speed = module.Options.Speed
				
				local x, y, z = 0, 0, 0
				if dir.w then z = -1 * speed end
				if dir.a then x = -1 * speed end
				if dir.s then z = 1 * speed end
				if dir.d then x = 1 * speed end
				if dir.q then y = 1 * speed end
				if dir.e then y = -1 * speed end
				
				flyPart.CFrame = CFrame.new(
					flyPart.CFrame.p,
					(camera.CFrame * CFrame.new(0, 0, -2048)).p
				)
				
				for _, part in pairs(character:GetChildren()) do
					if part:IsA("BasePart") then
						part.Velocity = Vector3.new()
					end
				end
				
				local moveDir = CFrame.new(x,y,z)
				cf.Value = cf.Value:lerp(moveDir, module.Options.Smoothness)
				flyPart.CFrame = flyPart.CFrame:lerp(flyPart.CFrame * cf.Value, module.Options.Smoothness)
				primaryPart.CFrame = flyPart.CFrame
				humanoid.PlatformStand = true
			end))
			lib.connect("fly", UserInputService.InputBegan:Connect(function(input, event)
				if event then return end
				local code, codes = input.KeyCode, Enum.KeyCode
				if code == codes.W then
					dir.w = true
				elseif code == codes.A then
					dir.a = true
				elseif code == codes.S then
					dir.s = true
				elseif code == codes.D then
					dir.d = true
				elseif code == codes.Q then
					dir.q = true
				elseif code == codes.E then
					dir.e = true
				elseif code == codes.Space then
					dir.q = true
				end
			end))
			lib.connect("fly", UserInputService.InputEnded:Connect(function(input, event)
				if event then return end
				local code, codes = input.KeyCode, Enum.KeyCode
				if code == codes.W then
					dir.w = false
				elseif code == codes.A then
					dir.a = false
				elseif code == codes.S then
					dir.s = false
				elseif code == codes.D then
					dir.d = false
				elseif code == codes.Q then
					dir.q = false
				elseif code == codes.E then
					dir.e = false
				elseif code == codes.Space then
					dir.q = false
				end
			end))
		end
		
		--// Events
		Player.CharacterAdded:Connect(function(char)
			character = char
		end)
		
		return module
	end)()
	local _Freecam = (function()
		--// Variables
		local RunService = game:GetService("RunService")
		local UserInputService = game:GetService("UserInputService")
		local Players = game:GetService("Players")
		  local Player = Players.LocalPlayer
			local character = Player.Character
		local camera = workspace.CurrentCamera
		
		local module = {}
		module.Options = {
			Speed = 5,
			Smoothness = 0.2,
		}
		
		local lib, connections = {}, {}
		lib.connect = function(name, connection)
			connections[name .. tostring(math.random(1000000, 9999999))] = connection
			return connection
		end
		lib.disconnect = function(name)
			for title, connection in pairs(connections) do
				if title:find(name) == 1 then
					connection:Disconnect()
				end
			end
		end
		
		--// Functions
		local flyPart
		
		local function flyEnd()
			lib.disconnect("freecam")
			camera.CameraSubject = character
			pcall(function()
				character.PrimaryPart.Anchored = false
			end)
		end
		
		module.flyStart = function(enabled)
			if not enabled then flyEnd() return end
			local dir = {w = false, a = false, s = false, d = false}
			local cf = Instance.new("CFrameValue")
			local camPart = Instance.new("Part")
			camPart.Transparency = 1
			camPart.Anchored = true
			camPart.CFrame = camera.CFrame
			pcall(function()
				character.PrimaryPart.Anchored = true
			end)
			
			lib.connect("freecam", RunService.RenderStepped:Connect(function()
				local primaryPart = camPart
				camera.CameraSubject = primaryPart
				
				local speed = module.Options.Speed
				
				local x, y, z = 0, 0, 0
				if dir.w then z = -1 * speed end
				if dir.a then x = -1 * speed end
				if dir.s then z = 1 * speed end
				if dir.d then x = 1 * speed end
				if dir.q then y = 1 * speed end
				if dir.e then y = -1 * speed end
				
				primaryPart.CFrame = CFrame.new(
					primaryPart.CFrame.p,
					(camera.CFrame * CFrame.new(0, 0, -100)).p
				)
				
				local moveDir = CFrame.new(x,y,z)
				cf.Value = cf.Value:lerp(moveDir, module.Options.Smoothness)
				primaryPart.CFrame = primaryPart.CFrame:lerp(primaryPart.CFrame * cf.Value, module.Options.Smoothness)
			end))
			lib.connect("freecam", UserInputService.InputBegan:Connect(function(input, event)
				if event then return end
				local code, codes = input.KeyCode, Enum.KeyCode
				if code == codes.W then
					dir.w = true
				elseif code == codes.A then
					dir.a = true
				elseif code == codes.S then
					dir.s = true
				elseif code == codes.D then
					dir.d = true
				elseif code == codes.Q then
					dir.q = true
				elseif code == codes.E then
					dir.e = true
				elseif code == codes.Space then
					dir.q = true
				end
			end))
			lib.connect("freecam", UserInputService.InputEnded:Connect(function(input, event)
				if event then return end
				local code, codes = input.KeyCode, Enum.KeyCode
				if code == codes.W then
					dir.w = false
				elseif code == codes.A then
					dir.a = false
				elseif code == codes.S then
					dir.s = false
				elseif code == codes.D then
					dir.d = false
				elseif code == codes.Q then
					dir.q = false
				elseif code == codes.E then
					dir.e = false
				elseif code == codes.Space then
					dir.q = false
				end
			end))
		end
		
		--// Events
		Player.CharacterAdded:Connect(function(char)
			character = char
		end)
		
		return module
	end)()
	local _Rubberbanding = (function()
		--// Variables
		local RunService = game:GetService("RunService")
		local Players = game:GetService("Players")
		  local Player = Players.LocalPlayer
			local Character = Player.Character
		
		local module = {}
		module.Options = {
			Enabled = false,
			Threshold = 150,
			UpdateSpeed = 100,
		}
		
		local connections = {}
		
		--// Functions
		local function getPart(Model)
			return Model.PrimaryPart or Model:FindFirstChild("HumanoidRootPart") or Model:FindFirstChildWhichIsA("Part")
		end
		
		local function connectPart(Part)
			local lastPosition = CFrame.new()
			local lastVelocity = Vector3.new()
			local lastRender = tick()
			
			connections[#connections+1] = RunService.RenderStepped:Connect(function()
				if not module.Options.Enabled then return end
				
				if Part and (tick() - lastRender >= module.Options.UpdateSpeed / 1000) then
					if (lastVelocity - Part.Velocity).Magnitude > module.Options.Threshold and Part.Velocity.Magnitude > lastVelocity.Magnitude then
						Part.Velocity = lastVelocity
						Part.CFrame = lastPosition
					end
					
					lastPosition = Part.CFrame
					lastVelocity = Part.Velocity
					lastRender = tick()
				end
			end)
		end
		
		local function onCharacter(char)
			Character = char
			for i, v in pairs(connections) do
				v:Disconnect()
				connections[i] = nil
			end
			for _, part in pairs(char:GetChildren()) do
				if part.Name == "HumanoidRootPart" then
					connectPart(part)
				end
			end
			connections[#connections+1] = Character.ChildAdded:Connect(function(child)
				if child.Name == "HumanoidRootPart" then
					connectPart(child)
				end
			end)
		end
		
		
		module.Toggle = function(enabled)
			module.Options.Enabled = enabled
			for i, v in pairs(connections) do
				v:Disconnect()
				connections[i] = nil
			end
			if enabled and Character then
				onCharacter(Character)
			end
		end
		
		--// Events
		Player.CharacterAdded:Connect(function(char)
			onCharacter(char)
		end)
		
		if Character then
			onCharacter(Character)
		end
		
		return module
		
	end)()
	local _AntiTP = (function()
		--// Variables
		local RunService = game:GetService("RunService")
		local Players = game:GetService("Players")
		  local Player = Players.LocalPlayer
			local Character = Player.Character
		
		local module = {}
		module.Options = {
			Enabled = false,
			Threshold = 150,
			UpdateSpeed = 100,
		}
		
		local connections = {}
		
		--// Functions
		local function getPart(Model)
			return Model.PrimaryPart or Model:FindFirstChild("HumanoidRootPart") or Model:FindFirstChildWhichIsA("Part")
		end
		
		local function connectPart(Part)
			local lastPosition = Part.CFrame
			local lastRender = tick()
			
			connections[#connections+1] = RunService.RenderStepped:Connect(function()
				if not module.Options.Enabled then return end
				
				if Part and (tick() - lastRender >= module.Options.UpdateSpeed / 1000) then
					if (lastPosition.p - Part.Position).Magnitude > module.Options.Threshold then
						Part.CFrame = lastPosition
						Part.Velocity = Vector3.new(0, 0, 0)
					end
					
					lastPosition = Part.CFrame
					lastRender = tick()
				end
			end)
		end
		
		local function onCharacter(char)
			Character = char
			for i, v in pairs(connections) do
				v:Disconnect()
				connections[i] = nil
			end
			for _, part in pairs(char:GetChildren()) do
				if part.Name == "HumanoidRootPart" then
					connectPart(part)
				end
			end
			connections[#connections+1] = Character.ChildAdded:Connect(function(child)
				if child.Name == "HumanoidRootPart" then
					connectPart(child)
				end
			end)
		end
		
		module.Toggle = function(enabled)
			module.Options.Enabled = enabled
			for i, v in pairs(connections) do
				v:Disconnect()
				connections[i] = nil
			end
			if enabled and Character then
				onCharacter(Character)
			end
		end
		
		--// Events
		Player.CharacterAdded:Connect(function(char)
			onCharacter(char)
		end)
		
		if Character then
			onCharacter(Character)
		end
		
		return module
		
	end)()
	local _Noclip = (function()
		--// Variables
		local RunService = game:GetService("RunService")
		local Players = game:GetService("Players")
		  local Player = Players.LocalPlayer
			local Character = Player.Character
		
		local module = {}
		module.Options = {
			Enabled = false,
		}
		
		local connections = {}
		
		--// Functions
		local function getPart(Model)
			return Model.PrimaryPart or Model:FindFirstChild("HumanoidRootPart") or Model:FindFirstChildWhichIsA("Part")
		end
		
		local function connectModel(Model)
			connections[#connections+1] = RunService.Stepped:Connect(function()
				if not module.Options.Enabled then return end
				for _, part in pairs(Model:GetDescendants()) do
					if part:IsA("BasePart") then
						part.CanCollide = false
					end
				end
			end)
		end
		
		module.Toggle = function(enabled)
			module.Options.Enabled = enabled
			for i, v in pairs(connections) do
				v:Disconnect()
				connections[i] = nil
			end
			if enabled and Character then
				onCharacter(Character)
			end
		end
		
		function onCharacter(char)
			for i, v in pairs(connections) do
				v:Disconnect()
				connections[i] = nil
			end
			Character = char
			connectModel(char)
		end
		
		--// Events
		Player.CharacterAdded:Connect(function(char)
			onCharacter(char)
		end)
		
		if Character then
			onCharacter(Character)
		end
		
		return module
		
	end)()
	 
	--// Variables
	local RunService = game:GetService("RunService")
	local HttpService = game:GetService("HttpService")
	local UserInputService = game:GetService("UserInputService")
	local Players = game:GetService("Players")
	  local Player = Players.LocalPlayer
		local Mouse = Player:GetMouse()
	 
	local gui = GUIData[1]
	local saveData = GUIData[2]
	local screenGui = GUIData[3]
	 
	local screenscale = 250
	local opacity = 1
	local backcolor = Color3.new()
	 
	--// Saving
	local readfile = readfile or function() end
	pcall(function()
		local JSONData = readfile("OpenGui.txt")
		if JSONData then
			local LUAData = HttpService:JSONDecode(JSONData)
			saveData.Options = LUAData.Options
			saveData.Hotkeys = LUAData.Hotkeys
			print("Save Data found")
		else
			print("Save Data not found")
		end
	end)
	 
	 
	--// UI Creation
	 
	--// Render Frame
	local Render = gui:create("Container", {
		Name = "Render",
	})--|
		local OpenGui = Render.self:create("Toggle", {
			Name = "OpenGui",
			Default = true,
			Hotkey = tostring(Enum.KeyCode.RightControl),
			Hint = "The navigation GUI",
			Callback = function(enabled)
				for _, frame in pairs(screenGui:GetChildren()) do
					if frame:IsA("Frame") then
						frame.Visible = enabled
					end
				end
				screenGui.Modal.Visible = enabled
				screenGui.Hint.Visible = false
			end,
		})--|
			local Opacity = OpenGui.self:create("Number", {
				Name = "Opacity",
				Min = 0,
				Max = 1,
				Round = 0.01,
				Default = 0.75,
				Hint = "Transparency of the navigation GUI",
				Callback = function(alpha)
					opacity = 1 - alpha
					for _, frame in pairs(screenGui:GetChildren()) do
						if frame:IsA("Frame") then
							frame.BackgroundTransparency = 1 - alpha
							frame.OptionsFrame.BackgroundTransparency = 1 - alpha
						end
					end
				end,
			})
			local Width = OpenGui.self:create("Number", {
				Name = "Width",
				Min = 200,
				Max = 300,
				Round = 1,
				Default = 250,
				Hint = "Width of the navigation GUI",
				Callback = function(scale)
					screenscale = scale
					for _, frame in pairs(screenGui:GetChildren()) do
						if frame:IsA("Frame") then
							frame.Size = UDim2.new(0, scale, 0, frame.Size.Y.Offset)
						end
					end
				end,
			})
			local Color = OpenGui.self:create("Color", {
				Name = "Background Color",
				Default = Color3.fromRGB(40, 40, 40),
				Hint = "Background color of the navigation GUI",
				Callback = function(color)
					backcolor = color
					for _, frame in pairs(screenGui:GetChildren()) do
						if frame:IsA("Frame") then
							frame.BackgroundColor3 = color
							frame.OptionsFrame.BackgroundColor3 = color
						end
					end
				end,
			})
		local ESP = Render.self:create("Toggle", {
			Name = "ESP",
			Default = false,
			Hint = "Toggle player ESP",
			Callback = function(enabled)
				_ESP.Options.Enabled = enabled
				if enabled then
					_ESP:Enable()
					_ESP2D:Enable()
				else
					_ESP:Disable()
					_ESP2D:Disable()
				end
				_ESP2D:ReloadCharacters()
			end,
		})--|
			local ESPColor = ESP.self:create("Color", {
				Name = "ESP Color",
				Default = Color3.new(1, 1, 1),
				Hint = "Color of the player ESP",
				Callback = function(color)
					_ESP.Options.Color = color
					_ESP2D.Options.Color = color
					_ESP2D:ReloadCharacters()
				end,
			})
			local ESPShowTeam = ESP.self:create("Checkbox", {
				Name = "Show Team",
				Default = false,
				Hint = "Players on your team are highlighted",
				Callback = function(enabled)
					_ESP.Options.ShowTeam = enabled
					_ESP2D.Options.ShowTeam = enabled
					_ESP2D:ReloadCharacters()
				end,
			})
			local ESPShowSelf = ESP.self:create("Checkbox", {
				Name = "Show Self",
				Default = false,
				Hint = "Include yourself in the ESP",
				Callback = function(enabled)
					_ESP.Options.ShowSelf = enabled
					_ESP2D.Options.ShowSelf = enabled
					_ESP2D:ReloadCharacters()
				end,
			})
			local ESPTeamColor = ESP.self:create("Checkbox", {
				Name = "Team Color",
				Default = false,
				Hint = "The ESP's color corresponds to the player's team",
				Callback = function(enabled)
					_ESP.Options.TeamColor = enabled
					_ESP2D.Options.TeamColor = enabled
					_ESP2D:ReloadCharacters()
				end,
			})
			local ESPShowDescendants = ESP.self:create("Checkbox", {
				Name = "Show Descendants",
				Default = false,
				Hint = "Highlight items like accessories",
				Callback = function(enabled)
					_ESP.Options.ShowDescendants = enabled
					_ESP2D.Options.ShowDescendants = enabled
					_ESP2D:ReloadCharacters()
				end,
			})
			local ESPDirection = ESP.self:create("Checkbox", {
				Name = "Show Direction",
				Default = false,
				Hint = "Show where the player is facing",
				Callback = function(enabled)
					_ESP.Options.Arrow = enabled
					_ESP2D.Options.Arrow = enabled
					_ESP2D:ReloadCharacters()
				end,
			})
			local ESPOpacity = ESP.self:create("Number", {
				Name = "Opacity",
				Default = 0.5,
				Min = 0,
				Max = 1,
				Round = 0.01,
				Hint = "Visibility of the ESP",
				Callback = function(opacity)
					_ESP.Options.Opacity = opacity
					_ESP2D.Options.Opacity = opacity
					_ESP2D:ReloadCharacters()
				end,
			})
			local ESPMaxDistance = ESP.self:create("Number", {
				Name = "Max Distance",
				Default = 500,
				Min = 32,
				Max = 2048,
				Round = 0.5,
				Hint = "The maximum distance of the ESP",
				Callback = function(distance)
					_ESP.Options.MaxDistance = distance
					_ESP2D.Options.MaxDistance = distance
					_ESP2D:ReloadCharacters()
				end,
			})
			local ESPMode = ESP.self:create("Mode", {
				Name = "ESP Mode",
				Default = 1,
				Modes = {"Shader", "Default", "Box", "Square"},
				Hint = "The type of ESP used",
				Callback = function(mode)
					_ESP.Options.Mode = mode
					_ESP2D.Options.Mode = mode
					_ESP:ReloadCharacters()
					_ESP2D:ReloadCharacters()
				end,
			})
		local Chams = Render.self:create("Toggle", {
			Name = "Chams",
			Default = false,
			Hint = "Render players through walls",
			Callback = function(enabled)
				_Chams.Options.Enabled = enabled
				if enabled then
					_Chams:Enable()
				else
					_Chams:Disable()
				end
			end,
		})--|
			local ChamsColor = Chams.self:create("Color", {
				Name = "Chams Color",
				Default = Color3.new(1, 1, 1),
				Hint = "Color of the player chams",
				Callback = function(color)
					_Chams.Options.Color = color
				end,
			})
			local ChamsShowTeam = Chams.self:create("Checkbox", {
				Name = "Show Team",
				Default = false,
				Hint = "Include your teammates",
				Callback = function(enabled)
					_Chams.Options.ShowTeam = enabled
				end,
			})
			local ChamsShowSelf = Chams.self:create("Checkbox", {
				Name = "Show Self",
				Default = false,
				Hint = "Include yourself",
				Callback = function(enabled)
					_Chams.Options.ShowSelf = enabled
				end,
			})
			local ChamsTeamColor = Chams.self:create("Checkbox", {
				Name = "Team Color",
				Default = false,
				Hint = "The chams color corresponds to the player's team",
				Callback = function(enabled)
					_Chams.Options.TeamColor = enabled
				end,
			})
			local ChamsShowDescendants = Chams.self:create("Checkbox", {
				Name = "Show Descendants",
				Default = false,
				Hint = "Highlight items like accessories",
				Callback = function(enabled)
					_Chams.Options.ShowDescendants = enabled
				end,
			})
			local ChamsMode = Chams.self:create("Mode", {
				Name = "Chams Mode",
				Default = 1,
				Modes = {"Opaque", "Shader"},
				Hint = "The type of chams used",
				Callback = function(mode)
					_Chams.Options.Mode = mode
					_Chams:ReloadCharacters()
				end,
			})
			local ChamsOpacity = Chams.self:create("Number", {
				Name = "Opacity",
				Default = 0.5,
				Min = 0,
				Max = 1,
				Round = 0.01,
				Hint = "Visibility of the chams",
				Callback = function(opacity)
					_Chams.Options.Opacity = opacity
				end,
			})
			local ChamsMaxDistance = Chams.self:create("Number", {
				Name = "Max Distance",
				Default = 500,
				Min = 32,
				Max = 2048,
				Round = 0.5,
				Hint = "The chams' maximum distance",
				Callback = function(distance)
					_Chams.Options.MaxDistance = distance
				end,
			})
		local Tracers = Render.self:create("Toggle", {
			Name = "Tracers",
			Default = false,
			Hint = "Draw lines to other players",
			Callback = function(enabled)
				_Tracers.Options.Enabled = enabled
				if enabled then
					_Tracers:Enable()
				else
					_Tracers:Disable()
				end
			end,
		})--|
			local TracersColor = Tracers.self:create("Color", {
				Name = "Tracers Color",
				Default = Color3.new(1, 1, 1),
				Hint = "Color of the tracers",
				Callback = function(color)
					_Tracers.Options.Color = color
				end,
			})
			local TracersShowTeam = Tracers.self:create("Checkbox", {
				Name = "Show Team",
				Default = false,
				Hint = "Include your teammates",
				Callback = function(enabled)
					_Tracers.Options.ShowTeam = enabled
					_Tracers:ReloadCharacters()
				end,
			})
			local TracersShowSelf = Tracers.self:create("Checkbox", {
				Name = "Show Self",
				Default = false,
				Hint = "Include yourself",
				Callback = function(enabled)
					_Tracers.Options.ShowSelf = enabled
					_Tracers:ReloadCharacters()
				end,
			})
			local TracersTeamColor = Tracers.self:create("Checkbox", {
				Name = "Team Color",
				Default = false,
				Hint = "Tracer colors correspond to the player's team",
				Callback = function(enabled)
					_Tracers.Options.TeamColor = enabled
				end,
			})
			local TracersOpacity = Tracers.self:create("Number", {
				Name = "Opacity",
				Default = 1,
				Min = 0,
				Max = 1,
				Round = 0.01,
				Hint = "Visibility of the tracers",
				Callback = function(opacity)
					_Tracers.Options.Opacity = opacity
				end,
			})
			local TracersMaxDistance = Tracers.self:create("Number", {
				Name = "Max Distance",
				Default = 500,
				Min = 32,
				Max = 2048,
				Round = 0.5,
				Hint = "The maximum distance in which tracers are drawn",
				Callback = function(distance)
					_Tracers.Options.MaxDistance = distance
				end,
			})
			local TracersWidth = Tracers.self:create("Number", {
				Name = "Width",
				Default = 2,
				Min = 1,
				Max = 10,
				Round = 1,
				Hint = "Width of the tracers",
				Callback = function(value)
					_Tracers.Options.Radius = value
				end,
			})
		local Freecam = Render.self:create("Toggle", {
			Name = "Freecam",
			Default = false,
			Hint = "Move your camera freely",
			Callback = function(enabled)
				_Freecam.flyStart(enabled)
			end,
		})--|
			local FreecamSpeed = Freecam.self:create("Number", {
				Name = "Speed",
				Default = 5,
				Min = 0.1,
				Max = 100,
				Round = 0.1,
				Hint = "Camera speed",
				Callback = function(value)
					_Freecam.Options.Speed = value
				end,
			})
			local FreecamSpeed = Freecam.self:create("Number", {
				Name = "Smoothness",
				Default = 0.2,
				Min = 0.1,
				Max = 1,
				Round = 0.01,
				Hint = "Smoothness of the interpolation",
				Callback = function(value)
					_Freecam.Options.Smoothness = value
				end,
			})
	 
	--// Combat Frame
	local Combat = gui:create("Container", {
		Name = "Combat",
	})--|
		local Aimbot = Combat.self:create("Toggle", {
			Name = "Aimbot",
			Default = false,
			Hint = "Automatically point to other players, hotkey recommended",
			Callback = function(enabled)
				_Aimbot.Options.Enabled = enabled
			end,
		})--]
			local AimbotEasing = Aimbot.self:create("Number", {
				Name = "Easing",
				Default = 2,
				Min = 1.3,
				Max = 32,
				Round = 0.1,
				Hint = "Smoothness of the aimbot",
				Callback = function(value)
					_Aimbot.Options.Easing = value
				end,
			})
			local AimbotLegit = Aimbot.self:create("Checkbox", {
				Name = "Legit",
				Hint = "Give the aimbot a maximum speed, looks more legit",
				Callback = function(value)
					_Aimbot.Options.Legit = value
				end,
			})
			local AimbotMaxDistance = Aimbot.self:create("Number", {
				Name = "Max Distance",
				Default = 500,
				Min = 32,
				Max = 2048,
				Round = 1,
				Hint = "The aimbot's maximum distance",
				Callback = function(value)
					_Aimbot.Options.MaxDistance = value
				end,
			})
			local AimbotMode = Aimbot.self:create("Mode", {
				Name = "Aim Target",
				Modes = {
					"Head",
					"Torso",
				},
				Hint = "Where the aimbot will aim",
				Callback = function(value)
					_Aimbot.Options.AimPart = value
				end,
			})
			local AimbotShowTeam = Aimbot.self:create("Checkbox", {
				Name = "Target Team",
				Hint = "Target your teammates",
				Callback = function(value)
					_Aimbot.Options.ShowTeams = value
				end,
			})
			local AimbotOnscreen = Aimbot.self:create("Checkbox", {
				Name = "Target On-Screen",
				Hint = "Target players only in front of you",
				Default = false,
				Callback = function(value)
					_Aimbot.Options.Onscreen = value
				end,
			})
			local AimbotVisible = Aimbot.self:create("Checkbox", {
				Name = "Target Visible",
				Hint = "Ignore players obstructed from view",
				Default = false,
				Callback = function(value)
					_Aimbot.Options.Visible = value
				end,
			})
			local AimbotMode = Aimbot.self:create("Mode", {
				Name = "Aimbot Mode",
				Hint = "Change who the aimbot targets",
				Default = 1,
				Modes = {
					"Nearest",
					"Snap",
				},
				Callback = function(value)
					_Aimbot.Options.Mode = value
				end,
			})--]
				local AimbotModeRadius = AimbotMode.self:create("Number", {
					Name = "Snap Radius",
					Default = 250,
					Min = 32,
					Max = 1024,
					Round = 1,
					Hint = "The detection radius of the aimbot mode 'Snap'",
					Callback = function(value)
						_Aimbot.Options.Radius = value
					end,
				})
	 
	--// Movement
	local Movement = gui:create("Container", {
		Name = "Movement",
	})--|
		local Flight = Movement.self:create("Toggle", {
			Name = "Flight",
			Default = false,
			Hint = "Toggle player flight (uses CFrame)",
			Callback = function(enabled)
				_Flight.flyStart(enabled)
			end,
		})--|
			local FlightSpeed = Flight.self:create("Number", {
				Name = "Speed",
				Default = 5,
				Min = 0.1,
				Max = 100,
				Round = 0.1,
				Hint = "Flight speed",
				Callback = function(value)
					_Flight.Options.Speed = value
				end,
			})
			local FlightSpeed = Flight.self:create("Number", {
				Name = "Smoothness",
				Default = 0.2,
				Min = 0.1,
				Max = 1,
				Round = 0.01,
				Hint = "Smoothness of the interpolation",
				Callback = function(value)
					_Flight.Options.Smoothness = value
				end,
			})
	 
	--// Player
	local PlayerTab = gui:create("Container", {
		Name = "Player",
	})--|
		local Rubberbanding = PlayerTab.self:create("Toggle", {
			Name = "Rubberbanding",
			Default = false,
			Hint = "Get set back if your velocity changes above the threshold",
			Callback = function(enabled)
				_Rubberbanding.Toggle(enabled)
			end,
		})--|
			local RubberbandingThreshold = Rubberbanding.self:create("Number", {
				Name = "Threshold",
				Default = false,
				Min = 50,
				Max = 1000,
				Default = 150,
				Round = 1,
				Hint = "Threshold for magnitude check",
				Callback = function(value)
					_Rubberbanding.Options.Threshold = value
				end,
			})
			local RubberbandingSpeed = Rubberbanding.self:create("Number", {
				Name = "Update Speed",
				Default = false,
				Min = 1,
				Max = 500,
				Default = 100,
				Round = 1,
				Hint = "How often it checks the velocity in ms",
				Callback = function(value)
					_Rubberbanding.Options.UpdateSpeed = value
				end,
			})
		local AntiTP = PlayerTab.self:create("Toggle", {
			Name = "Anti TP",
			Default = false,
			Hint = "Prevent teleporting large distances",
			Callback = function(enabled)
				_AntiTP.Toggle(enabled)
			end,
		})--|
			local AntiTPThreshold = AntiTP.self:create("Number", {
				Name = "Threshold",
				Min = 1,
				Max = 1000,
				Default = 150,
				Round = 1,
				Hint = "Maximum distance",
				Callback = function(value)
					_AntiTP.Options.Threshold = value
				end,
			})
			local AntiTPSpeed = AntiTP.self:create("Number", {
				Name = "Update Speed",
				Min = 1,
				Max = 500,
				Default = 100,
				Round = 1,
				Hint = "How often it checks the position in ms",
				Callback = function(value)
					_AntiTP.Options.UpdateSpeed = value
				end,
			})
		local Noclip = PlayerTab.self:create("Toggle", {
			Name = "No Collision",
			Default = false,
			Hint = "Ignore object collision",
			Callback = function(enabled)
				_Noclip.Toggle(enabled)
			end,
		})
	 
	--// UI Functionality
	RunService.RenderStepped:Connect(function()
		for _, frame in pairs(screenGui:GetChildren()) do
			if frame:IsA("Frame") then
				frame.Size = UDim2.new(0, screenscale, 0, frame.Size.Y.Offset)
				
				frame.BackgroundTransparency = opacity
				frame.OptionsFrame.BackgroundTransparency = opacity
				
				frame.BackgroundColor3 = backcolor
				frame.OptionsFrame.BackgroundColor3 = backcolor
			end
		end
	end)
end)

Section:NewButton("Game Sense", "GreatZ So Gay", function()
	local UIS = game:GetService("UserInputService")
	local RS = game:GetService("RunService")
	local Players = game:GetService("Players")
	local StarterGui = game:GetService("StarterGui")
	local Player = Players.LocalPlayer
	local Studio = RS:IsStudio()
	local PlayerGui = RS:IsStudio() and Player:WaitForChild("PlayerGui") or game.CoreGui
	local Mouse = Player:GetMouse()
	local Camera = workspace.CurrentCamera
	targetpart = "Head" -- Don"t change this.
	-- It can be changed with the targetpart_change hotkey ingame.
	local target
	local target_old
	local alert = false
	local lockedon = false
	local settingkey = false
	local upvals = nil
	local val = 1
	local windows = {}
	local function hb()
		RS.Heartbeat:wait()
	end
	 
	local version = 1.25
	local Spawn = nil or game.PlaceId == 292439477 and workspace:WaitForChild("Lobby", 2):WaitForChild("Spawn1", 2)
	local spawned = false
	 
	script.Name = "GameSense!"
	Mouse.TargetFilter = Camera
	 
	-- hotkey
	toggle_aim = Enum.KeyCode.LeftShift
	toggle_aimbot = Enum.KeyCode.LeftAlt
	toggle_trigger = Enum.KeyCode.RightAlt
	toggle_esp = Enum.KeyCode.End
	toggle_gui = Enum.KeyCode.F6
	toggle_fov = Enum.KeyCode.F7
	toggle_bottompos = Enum.KeyCode.PageDown
	toggle_performance = Enum.KeyCode.F10
	toggle_bones = Enum.KeyCode.Delete
	toggle_chams = Enum.KeyCode.F3
	toggle_tracers = Enum.KeyCode.F2
	toggle_boxes = Enum.KeyCode.F4
	toggle_font = Enum.KeyCode.F1
	ffatoggle = Enum.KeyCode.Home
	targetpart_change = Enum.KeyCode.BackSlash
	priority_toggle = Enum.KeyCode.Insert
	sethotkey = Enum.KeyCode.RightControl
	-- aim fov
	fov_increase = Enum.KeyCode.KeypadPlus
	fov_decrease = Enum.KeyCode.KeypadMinus
	-- aim sens (how smooth your crosshair will move)
	sens_increase = Enum.KeyCode.RightBracket
	sens_decrease = Enum.KeyCode.LeftBracket
	tsens_increase = Enum.KeyCode.RightBracket
	tsens_decrease = Enum.KeyCode.LeftBracket
	 
	-- parts
	parts = {
		"Head";
		"Torso"
	}
	 
	fonts = {
		Enum.Font.SourceSansBold,
		Enum.Font.Cartoon,
		Enum.Font.Arcade,
		Enum.Font.SciFi,
		Enum.Font.Fantasy,
		Enum.Font.Code,
		Enum.Font.Highway,
		Enum.Font.Bodoni
	}
	 
	textSet = false
	 
	function writefileExploit()
		if writefile then
			return true
		end
	end
	 
	DefaultSettings = {
		currentfont = 1;
		ffa = false;
		hidden = false;
		fovhidden = false;
		performancemode = false;
		fov = 20;
		oldfov = 20;
		tsens = 0.5;
		sens = 0.25;
		drop = 0;
		bottompos = true;
		aim_priority = 2;
		esp_toggled = true;
		esp_bones = true;
		esp_chams = true;
		esp_tracers = false;
		bounding_box = true
	}
	 
	Defaults = game:GetService("HttpService"):JSONEncode(DefaultSettings)
	 
	local NoSaves = false
	 
	function Saves()
		if writefileExploit() then
			if pcall(function() readfile("GameSense.json") end) then
				if readfile("GameSense.json") ~= nil then
					local json = game:GetService("HttpService"):JSONDecode(readfile("GameSense.json"))
					if json.currentfont ~= nil then currentfont = json.currentfont else currentfont = 1 end
					if json.ffa ~= nil then ffa = json.ffa else ffa = false end
					if json.hidden ~= nil then hidden = json.hidden else hidden = false end
					if json.fovhidden ~= nil then fovhidden = json.fovhidden else fovhidden = false end
					if json.performancemode ~= nil then performancemode = json.performancemode else performancemode = false end
					if json.fov ~= nil then fov = json.fov oldfov = fov else fov = 20 oldfov = fov end
					if json.tsens ~= nil then tsens = json.tsens else tsens = 0.5 end
					if json.sens ~= nil then sens = json.sens else sens = 0.25 end
					if json.drop ~= nil then drop = json.drop else drop = 0 end
					if json.bottompos ~= nil then bottompos = json.bottompos else bottompos = true end
					if json.aim_priority ~= nil then aim_priority = json.aim_priority else aim_priority = 2 end
					if json.esp_toggled ~= nil then esp_toggled = json.esp_toggled else esp_toggled = true end
					if json.esp_bones ~= nil then esp_bones = json.esp_bones else esp_bones = true end
					if json.esp_chams ~= nil then esp_chams = json.esp_chams else esp_chams = true end
					if json.esp_tracers ~= nil then esp_tracers = json.esp_tracers else esp_tracers = false end
					if json.bounding_box ~= nil then bounding_box = json.bounding_box else bounding_box = true end
				else
					writefile("GameSense.json", Defaults)
					wait()
					Saves()
				end
			else
				writefile("GameSense.json", Defaults)
				wait()
				if pcall(function() readfile("GameSense.json") end) then
					Saves()
				else
					NoSaves = true
					currentfont = 1;
					ffa = false;
					hidden = false;
					fovhidden = false;
					oldfov = 20;
					performancemode = false;
					fov = 20;
					tsens = 0.5;
					sens = 0.25;
					drop = 0;
					bottompos = true;
					aim_priority = 2;
					esp_toggled = true;
					esp_bones = true;
					esp_chams = true;
					esp_tracers = false;
					bounding_box = true
				end
			end
		else
			currentfont = 1;
			ffa = false;
			hidden = false;
			fovhidden = false;
			oldfov = 20;
			performancemode = false;
			fov = 20;
			tsens = 0.5;
			sens = 0.25;
			drop = 0;
			bottompos = true;
			aim_priority = 2;
			esp_toggled = true;
			esp_bones = true;
			esp_chams = true;
			esp_tracers = false;
			bounding_box = true
		end
	end
	 
	Saves()
	 
	function UpdateSaves()
		if NoSaves == false and writefileExploit() then
			local Update = {
				currentfont = currentfont;
				ffa = ffa;
				hidden = hidden;
				fovhidden = fovhidden;
				oldfov = oldfov;
				performancemode = performancemode;
				fov = fovhidden and oldfov or fov;
				tsens = tsens;
				sens = sens;
				drop = drop;
				bottompos = bottompos;
				aim_priority = aim_priority;
				esp_toggled = esp_toggled;
				esp_bones = esp_bones;
				esp_chams = esp_chams;
				esp_tracers = esp_tracers;
				bounding_box = bounding_box
			}
			writefile("GameSense.json", game:GetService("HttpService"):JSONEncode(Update))
		end
	end
	 
	-- aim
	aim_toggled = false
	bottompos = true
	-- [2] FOV or [1] Distance
	aimingcolor = Color3.fromRGB(0, 165, 255)
	aimbot_toggled = true
	aim_line = true
	locksoundid = 538769304
	 
	-- trigger
	trigger_toggled = false
	trigger_delay = 1 / 20
	 
	-- esp
	esp_toggled = true
	esp_bones = true
	esp_chams = true
	esp_tracers = false
	-- item_esp (coming soon)
	linesize = 1
	showdists = true
	textsize = 14
	textoffset = 20
	visiblecolor = Color3.fromRGB(38, 255, 99)
	hiddencolor = Color3.fromRGB(255, 37, 40)
	headboxsize = 4
	headboxaimsize = 6
	headboxshape = "diamond"
	-- rectangle or diamond
	 
	-- box esp
	bounding_box = true
	-- box_pointsize = 0 [UNUSED]
	box_line_size = 1
	-- box_line_size_visible = 2 [UNUSED]
	 
	local GUI = Instance.new("ScreenGui", PlayerGui)
	GUI.Name = "GameSense "..version
	GUI.ResetOnSpawn = false
	 
	ESP = Instance.new("Folder", GUI)
	ESP.Name = "ESP"
	local Bottom = Instance.new("Frame", ESP)
	Bottom.Name = "Bottom"
	Bottom.BackgroundTransparency = 1
	Bottom.Size = UDim2.new(0, 1, 0, 1)
	Bottom.Position = UDim2.new(.5, 0, 1, 1)
	 
	local Status = Instance.new("TextLabel", GUI)
	Status.Name = "Status"
	Status.BackgroundTransparency = 1
	Status.Size = UDim2.new(0, 500, 0, 50)
	Status.Position = UDim2.new(.5, -250, .85, 0)
	Status.TextSize = 24
	Status.Font = Enum.Font.SourceSansBold
	Status.TextColor3 = Color3.new(1, 1, 1)
	Status.TextStrokeColor3 = Color3.new(0, 0, 0)
	Status.TextStrokeTransparency = .6
	Status.Text = "On Standby"
	Status.ZIndex = 50
	 
	local FovGui = Instance.new("ImageLabel", GUI)
	FovGui.Name = "FovGui"
	FovGui.Image = "rbxassetid://324848180"
	FovGui.Size = UDim2.new(0, (Camera.ViewportSize.X / (90 / fov)) * 2, 0, (Camera.ViewportSize.X / (90 / fov)) * 2)
	FovGui.Position = UDim2.new(0.5, -FovGui.AbsoluteSize.X / 2, 0.5, -FovGui.AbsoluteSize.Y / 2)
	FovGui.BackgroundTransparency = 1
	FovGui.ImageTransparency = .9
	FovGui.ImageColor3 = Color3.new(1, 0, 0)
	 
	local Indicator = Instance.new("TextLabel", GUI)
	Indicator.Name = "Indicator"
	Indicator.Font = Enum.Font.SourceSans
	Indicator.TextSize = 14
	Indicator.TextXAlignment = Enum.TextXAlignment.Center
	Indicator.TextYAlignment = Enum.TextYAlignment.Center
	Indicator.TextStrokeTransparency = .75
	Indicator.Text = aim_priority > 1 and "FOV: "..fov or "Distance"
	 
	local SensAdjust = Instance.new("TextBox", GUI)
	SensAdjust.Name = "SensAdjust"
	SensAdjust.Font = Enum.Font.SourceSans
	SensAdjust.BackgroundTransparency = .75
	SensAdjust.BackgroundColor3 = Color3.new(0, 0, 0)
	SensAdjust.BorderColor3 = Color3.new(1, 1, 1)
	SensAdjust.Size = UDim2.new(0, 50, 0, 20)
	SensAdjust.TextStrokeTransparency = .6
	SensAdjust.TextColor3 = Color3.new(1, 1, 1)
	SensAdjust.TextSize = 14
	SensAdjust.PlaceholderText = "Sens"
	SensAdjust.Text = tonumber(sens)
	SensAdjust.Position = UDim2.new(.5, -250, .85, -20) + UDim2.new(0, 250, 0, 65)
	 
	local SensLabel = Instance.new("TextLabel", SensAdjust)
	SensLabel.Name = "SensLabel"
	SensLabel.Font = Enum.Font.SourceSans
	SensLabel.Size = UDim2.new(1, 0, 1, 0)
	SensLabel.BackgroundTransparency = 1
	SensLabel.TextSize = 14
	SensLabel.TextColor3 = Color3.new(1, 1, 1)
	SensLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
	SensLabel.TextStrokeTransparency = .6
	SensLabel.Text = "Sens:"
	SensLabel.Position = UDim2.new(-1, 0, 0, 0)
	SensLabel.TextXAlignment = Enum.TextXAlignment.Left
	 
	local TSensAdjust = Instance.new("TextBox", GUI)
	TSensAdjust.Name = "TSensAdjust"
	TSensAdjust.Font = Enum.Font.SourceSans
	TSensAdjust.BackgroundTransparency = .75
	TSensAdjust.BackgroundColor3 = Color3.new(0, 0, 0)
	TSensAdjust.BorderColor3 = Color3.new(1, 1, 1)
	TSensAdjust.Size = UDim2.new(0, 50, 0, 20)
	TSensAdjust.TextStrokeTransparency = .6
	TSensAdjust.TextColor3 = Color3.new(1, 1, 1)
	TSensAdjust.TextSize = 14
	TSensAdjust.PlaceholderText = "Third Person Sens"
	TSensAdjust.Text = tonumber(tsens)
	TSensAdjust.Position = UDim2.new(.5, -250, .85, -20) + UDim2.new(0, 250, 0, 85)
	 
	local TSensLabel = Instance.new("TextLabel", TSensAdjust)
	TSensLabel.Name = "TSensLabel"
	TSensLabel.Font = Enum.Font.SourceSans
	TSensLabel.Size = UDim2.new(1, 0, 1, 0)
	TSensLabel.BackgroundTransparency = 1
	TSensLabel.TextSize = 14
	TSensLabel.TextColor3 = Color3.new(1, 1, 1)
	TSensLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
	TSensLabel.TextStrokeTransparency = .6
	TSensLabel.Text = "Third Person Sens:"
	TSensLabel.Position = UDim2.new(-2, 0, 0, 0)
	TSensLabel.TextXAlignment = Enum.TextXAlignment.Left
	 
	local FovAdjust = SensAdjust:Clone()
	FovAdjust.Parent = GUI
	FovAdjust.PlaceholderText = "FOV"
	FovAdjust.Name = "FovAdjust"
	FovAdjust.Text = tonumber(fov)
	FovAdjust.Position = TSensAdjust.Position + UDim2.new(0, 0, 0, 20)
	FovAdjust.SensLabel.Name = "FovLabel"
	FovAdjust.FovLabel.Text = "Fov:"
	 
	local DropAdjust = SensAdjust:Clone()
	DropAdjust.Parent = GUI
	DropAdjust.PlaceholderText = "Drop"
	DropAdjust.Name = "DropAdjust"
	DropAdjust.Text = tonumber(drop)
	DropAdjust.Position = TSensAdjust.Position + UDim2.new(0, 0, 0, 40)
	DropAdjust.SensLabel.Name = "DropLabel"
	DropAdjust.DropLabel.Text = "Drop:"
	 
	local KeysList = Instance.new("TextLabel", GUI)
	KeysList.Name = "KeysList"
	KeysList.Font = Enum.Font.SourceSans
	KeysList.TextStrokeTransparency = .6
	KeysList.TextSize = 14
	KeysList.TextColor3 = Color3.new(1, 1, 1)
	KeysList.Size = UDim2.new(0, 0, 1, 0)
	KeysList.Position = UDim2.new(0, 5, 0, -280)
	KeysList.BackgroundTransparency = 1
	KeysList.Active = false
	KeysList.TextXAlignment = Enum.TextXAlignment.Left
	KeysList.TextYAlignment = Enum.TextYAlignment.Bottom
	KeysList.Text = "AimBot Toggle: "..toggle_aimbot.Name..
	"\nAim Toggle: "..toggle_aim.Name..
	"\nAim Part Toggle: "..targetpart_change.Name..
	"\nPriority Toggle: "..priority_toggle.Name..
	"\nESP Toggle: "..toggle_esp.Name..
	"\nBones Toggle: "..toggle_bones.Name..
	"\nChams Toggle: "..toggle_chams.Name..
	"\nBoxes Toggle: "..toggle_boxes.Name..
	"\nFOV Increase: "..fov_increase.Name..
	"\nFOV Decrease: "..fov_decrease.Name..
	"\nSens Increase: "..sens_increase.Name..
	"\nSens Decrease: "..sens_decrease.Name..
	"\nThird Person Sens Increase: "..tsens_increase.Name..
	"\nThird Person Sens Decrease: "..tsens_decrease.Name..
	"\nTrigger Toggle: "..toggle_trigger.Name..
	"\nFFA Toggle: "..ffatoggle.Name..
	"\nHide UI: "..toggle_gui.Name..
	"\nUse FOV Circle: "..toggle_fov.Name..
	"\nChange ESP Origin: "..toggle_bottompos.Name..
	"\nPerformance Mode: "..toggle_performance.Name..
	"\nChange Font: "..toggle_font.Name
	 
	local n = 0
	 
	spawn(function()
		while Status do
			Indicator.TextColor3 = Color3.fromHSV(n, .5, 1)
			FovGui.ImageColor3 = Indicator.TextColor3
			if not textSet then
				if aim_toggled and target then
					Status.TextColor3 = aimingcolor
					Status.Text = ("Aiming at "..target.Name)
				else
					Status.TextColor3 = Color3.fromHSV(n, .5, 1)
					Status.Text = "On Standby"
				end
			end
			n = (n + .005) % 1
			hb()
		end
	end)
	 
	SensAdjust.InputEnded:Connect(function()
		if SensAdjust.Text ~= "" then
			sens = tonumber(SensAdjust.Text) > 0 and tonumber(SensAdjust.Text) or sens
			UpdateSaves()
		end
	end)
	TSensAdjust.InputEnded:Connect(function()
		if TSensAdjust.Text ~= "" then
			tsens = tonumber(TSensAdjust.Text) > 0 and tonumber(TSensAdjust.Text) or tsens
			UpdateSaves()
		end
	end)
	FovAdjust.InputEnded:Connect(function()
		if FovAdjust.Text ~= "" then
			fov = tonumber(FovAdjust.Text) > 0 and tonumber(FovAdjust.Text) or fov
			UpdateSaves()
			FovGui:TweenSize(UDim2.new(0, (Camera.ViewportSize.X / (90 / fov)) * 2, 0, (Camera.ViewportSize.X / (90 / fov)) * 2), Enum.EasingDirection.InOut, Enum.EasingStyle.Quad, .1, true)
		end
	end)
	DropAdjust.InputEnded:Connect(function()
		if DropAdjust.Text ~= "" then
			drop = tonumber(DropAdjust.Text) >= 0 and tonumber(DropAdjust.Text) or drop
			UpdateSaves()
		end
	end)
	 
	local function distfromspawn(x)
		if Spawn then
			return x:DistanceFromCharacter(Spawn.Position)
		else
			return 201
		end
	end
	 
	local function setText(text)
		spawn(function()
			textSet = true
			Status.Text = text
			Status.TextColor3 = Color3.new(1, 1, 1)
			wait(#text / 4)
			textSet = false
		end)
	end
	 
	local function playsound(id)
		local sound = Instance.new("Sound", Camera)
		sound.SoundId = "rbxassetid://"..id
		sound.Volume = 3
		sound:Play()
		game:GetService("Debris"):AddItem(sound, 5)
	end
	 
	playsound(1168009121)
	 
	local function Notification(...)
		playsound(140910211)
		StarterGui:SetCore("SendNotification", ...)
	end
	 
	local function DrawLine(Folder, P1, P2, Thickness, Color, LineTransparency, BorderThickness, BorderColor)
		-- Declare variables
		local Point1, Point2 = P1.Position, P2.Position
		if Point1 and Point2 then
			local X, Y = Camera.ViewportSize.X, Camera.ViewportSize.Y
			local X1, X2 = (X * Point1.X.Scale + Point1.X.Offset + P1.Size.X.Offset / 2), (X * Point2.X.Scale + Point2.X.Offset + P2.Size.X.Offset / 2)
			local Y1, Y2 = (Y * Point1.Y.Scale + Point1.Y.Offset + P1.Size.Y.Offset / 2), (Y * Point2.Y.Scale + Point2.Y.Offset + P2.Size.Y.Offset / 2)
			local MidX, MidY = (X1 + X2) / 2, (Y1 + Y2) / 2
		-- Set defaults to prevent errors
			Thickness = Thickness or 1
			Color = Color or Color3.new(1, 1, 1)
			LineTransparency =  LineTransparency or 0
			BorderThickness = BorderThickness or 0
			BorderColor = BorderColor or Color3.new(0, 0, 0)
		-- Draw the line
			local Line = Folder:FindFirstChild(P1.Name.."-"..P2.Name) or Instance.new("Frame", Folder)
			Line.Visible = false
			Line.BackgroundTransparency = LineTransparency
			Line.BorderSizePixel = BorderThickness
			Line.BorderColor3 = BorderColor
			Line.Size = UDim2.new(0, (Vector2.new(X1, Y1) - Vector2.new(X2, Y2)).magnitude - 1, 0, Thickness)
			Line.Position = UDim2.new(0, MidX - Line.AbsoluteSize.X / 2, 0, MidY - Line.AbsoluteSize.Y)
			Line.BackgroundColor3 = Color
			Line.Rotation = math.deg(math.atan2((Y2 - Y1), (X2 - X1)))
			Line.Name = P1.Name.."-"..P2.Name
			Line.Visible = true
			return Line
		else
			return nil
		end
	end
	 
	local function GetNearest(Mode)
		local lowest, nearest, gui = math.huge, nil, nil
		if Mode == 1 then
			for _, plr in next, Players:GetPlayers() do 
				if plr.Name ~= Player.Name and plr.Character ~= nil and plr.Character:FindFirstChild(targetpart) then
					local dist = Player:DistanceFromCharacter(plr.Character[targetpart].Position)
					local ray = Ray.new(Player.Character.Head.Position, (plr.Character[targetpart].Position - Player.Character.Head.Position).unit * 5000)
					local part, point = workspace:FindPartOnRayWithIgnoreList(ray, {
						Camera,
						Player.Character,
						unpack(windows)
					})
					local Z = Camera:WorldToScreenPoint(plr.Character[targetpart].Position).Z
					if part and part:IsDescendantOf(plr.Character) and Z > 0 and dist < lowest and (ffa or plr.TeamColor ~= Player.TeamColor) then
						lowest = dist
						nearest = plr.Character
					end
				end
			end
		elseif Mode == 2 then
			for _, plr in next, Players:GetPlayers() do
				if plr.Name ~= Player.Name and plr.Character ~= nil and plr.Character:FindFirstChild(targetpart) then
					local pos = Camera:WorldToScreenPoint(plr.Character[targetpart].Position)
					local ray = Ray.new(Player.Character[targetpart].Position, (plr.Character[targetpart].Position - Player.Character[targetpart].Position).unit * 2048)
					local part, point = workspace:FindPartOnRayWithIgnoreList(ray, {
						Camera,
						Player.Character,
						unpack(windows)
					})
					local dist = (Vector2.new(Mouse.X, Mouse.Y) - Vector2.new(pos.X, pos.Y)).magnitude
					if part and part:IsDescendantOf(plr.Character) and pos.Z > 0 and dist <= Camera.ViewportSize.X / (90 / fov) and dist < lowest and (ffa or plr.TeamColor ~= Player.TeamColor) then
						lowest = dist
						nearest = plr.Character
					end
				end
			end
		end
		return nearest
	end
	 
	Mouse.Move:Connect(function()
		cursor = ESP:FindFirstChild("Cursor") or Instance.new("Frame", ESP)
		cursor.Name = "Cursor"
		cursor.BackgroundTransparency = 1
		cursor.Size = UDim2.new(0, 1, 0, 1)
		cursor.Position = UDim2.new(0, Mouse.X, 0, Mouse.Y)
	end)
	 
	if fovhidden then
		FovGui.Visible = false
		fov = 120
	end
	 
	UIS.InputBegan:Connect(function(Input)
		if Input.KeyCode == toggle_aim or Input.UserInputType == toggle_aim then
			aim_toggled = true
			warn("GS: aim toggled", aim_toggled and "on" or "off")
			alert = true
			while aim_toggled and aimbot_toggled do
				target = GetNearest(aim_priority)
				if target then
					local dist = Player:DistanceFromCharacter(target[targetpart].Position)
					local headpos = Camera:WorldToScreenPoint(target[targetpart].Position + Vector3.new(0, dist / (100 / drop), 0))
					local moveto = Vector2.new((headpos.X - Mouse.X) * sens, (headpos.Y - Mouse.Y) * sens)
					if (Camera.focus.p - Camera.CFrame.p).magnitude > 0.6 and not (UIS:IsMouseButtonPressed(Enum.UserInputType.MouseButton3) or UIS:IsMouseButtonPressed(Enum.UserInputType.MouseButton2)) then
						moveto = Vector2.new((headpos.X - Mouse.X) * tsens, (headpos.Y - Mouse.Y) * tsens)
					end
					aimpos = GUI:FindFirstChild("AimPos") or Instance.new("Frame", GUI)
					if not GUI:FindFirstChild("AimPos") then
						aimpos.Name = "AimPos"
						aimpos.BorderSizePixel = 1
						aimpos.BorderColor3 = Color3.new(0, 0, 0)
						aimpos.BackgroundTransparency = 0
						aimpos.BackgroundColor3 = Color3.new(1, 1, 1)
						aimpos.Rotation = 45
						aimpos.ZIndex = 4
						aimpos.Size = UDim2.new(0, 3, 0, 3)
					end
					aimpos.Position = UDim2.new(0, headpos.X - aimpos.AbsoluteSize.X / 2, 0, headpos.Y - aimpos.AbsoluteSize.Y / 2)
					aimpos.Visible = true
					mousemoverel(moveto.X, moveto.Y)
					if alert or target ~= target_old then
						playsound(locksoundid)
						print("GS: locked onto", target.Name)
						lockedon = true
						alert = false
					end
				end
				RS.Heartbeat:wait()
				target_old = target
				if aimpos then
					aimpos.Visible = false
				end
			end
			lockedon = false
		elseif Input.KeyCode == toggle_trigger then
			trigger_toggled = not trigger_toggled
			setText("Toggled TriggerBot "..(trigger_toggled and "On" or "Off"))
			Notification({
				Title = "TriggerBot";
				Text = "TriggerBot was toggled "..(trigger_toggled and "On" or "Off");
				Duration = 2;
			})
			warn("trigger toggled", trigger_toggled and "on" or "off")
			local Box = Instance.new("SelectionBox", PlayerGui)
			Box.Color3 = Color3.new(1, 0, 0)
			Box.LineThickness = .05
			Box.Adornee = nil
			if trigger_delay > 0 then
				wait(trigger_delay)
			end
			while trigger_toggled do
				local Target = Mouse.Target
				local plr = Players:FindFirstChild(Target.Parent.Name)
				if Target and Target.Parent and plr ~= nil and plr ~= Player and ffa or plr ~= nil and plr.TeamColor ~= Player.TeamColor then
					Box.Adornee = Mouse.Target
					mouse1press()
					wait()
					mouse1release()
				end
				RS.Heartbeat:wait()
			end
			Box:Destroy()
		elseif Input.KeyCode == toggle_esp then
			esp_toggled = not esp_toggled
			UpdateSaves()
			Notification({
				Title = "ESP";
				Text = "ESP was toggled "..(esp_toggled and "On" or "Off");
				Duration = 2;
			})
			setText("Toggled ESP "..(esp_toggled and "On" or "Off"))
		elseif Input.KeyCode == toggle_aimbot then
			aimbot_toggled = not aimbot_toggled	
			Notification({
				Title = "AimBot";
				Text = "AimBot was toggled "..(aimbot_toggled and "On" or "Off");
				Duration = 2;
			})
			setText("Toggled AimBot "..(aimbot_toggled and "On" or "Off"))
		elseif Input.KeyCode == fov_increase then
			fov = fov + .5
			UpdateSaves()
			FovAdjust.Text = tonumber(fov)
			if FovGui.Visible then
				FovGui:TweenSize(UDim2.new(0, (Camera.ViewportSize.X / (90 / fov)) * 2, 0, (Camera.ViewportSize.X / (90 / fov)) * 2), Enum.EasingDirection.InOut, Enum.EasingStyle.Quad, .1, true)
			end
			setText("Aim FOV: "..fov)
		elseif Input.KeyCode == fov_decrease and fov > 0 then
			fov = fov - .5
			UpdateSaves()
			FovAdjust.Text = tonumber(fov)
			if FovGui.Visible then
				FovGui:TweenSize(UDim2.new(0, (Camera.ViewportSize.X / (90 / fov)) * 2, 0, (Camera.ViewportSize.X / (90 / fov)) * 2), Enum.EasingDirection.InOut, Enum.EasingStyle.Quad, .1, true)
			end
			setText("Aim FOV: "..fov)
		elseif Input.KeyCode == sens_increase then
			sens = sens + .05
			UpdateSaves()
			SensAdjust.Text = tonumber(sens)
			setText("Sens: "..sens)
		elseif Input.KeyCode == sens_decrease then
			sens = sens - .05
			UpdateSaves()
			SensAdjust.Text = tonumber(sens)
			setText("Sens: "..sens)
		elseif Input.KeyCode == tsens_increase then
			tsens = tsens + .05
			UpdateSaves()
			SensAdjust.Text = tonumber(tsens)
			setText("Third Person Sens: "..tsens)
		elseif Input.KeyCode == tsens_decrease then
			tsens = tsens - .05
			UpdateSaves()
			SensAdjust.Text = tonumber(tsens)
			setText("Third Person Sens: "..tsens)
		elseif Input.KeyCode == targetpart_change then
			val = val + 1
			targetpart = val <= #parts and parts[val] or parts[1]
			if parts[1] == targetpart then
				val = 1
			end
			Notification({
				Title = "Target Part";
				Text = "Target part set to "..targetpart;
				Duration = 2;
			})
			setText("Target Part: "..targetpart)
		elseif Input.KeyCode == ffatoggle then
			ffa = not ffa
			UpdateSaves()
			Notification({
				Title = "FFA Mode";
				Text = "FFA Mode is "..(ffa and "Enabled" or "Disabled");
				Duration = 2;
			})
			setText("FFA Mode: "..(ffa and "Enabled" or "Disabled"))
		elseif Input.KeyCode == priority_toggle then
			aim_priority = aim_priority + 1 > 2 and 0 or 1
			aim_priority = aim_priority + 1
			UpdateSaves()
			FovGui.Visible = aim_priority > 1
			Notification({
				Title = "Aim Priority";
				Text = "Aim Priority: "..(aim_priority == 1 and "Distance" or "FOV");
				Duration = 2;
			})
			setText("Aim Priority: "..(aim_priority == 1 and "Distance" or "FOV"))
		elseif Input.KeyCode == toggle_bones then
			esp_bones = not esp_bones
			UpdateSaves()
			if not esp_bones then
				for _, v in next, ESP:GetDescendants() do
					if v:IsA("Frame") and v.Name:match("-") then
						v:Destroy()
					end
				end
			end
			Notification({
				Title = "ESP";
				Text = "ESP Bones: "..(esp_bones and "Enabled" or "Disabled");
				Duration = 2;
			})
			setText("Toggled ESP Bones "..(esp_bones and "Enabled" or "Disabled"))
		elseif Input.KeyCode == toggle_gui then
			hidden = not hidden
			UpdateSaves()
			for _, gui in next, GUI:GetDescendants() do
				if gui:IsA("GuiObject") and not hidden and not gui.Visible and gui.Name ~= "FovGui" and gui.Name ~= "Indicator" and gui.Name ~= "AimPos" then
					gui.Visible = true
				elseif gui:IsA("GuiObject") and gui.Visible and gui.Name ~= "FovGui" and gui.Name ~= "Indicator" and gui.Name ~= "AimPos" then
					gui.Visible = false
				end
			end
		elseif Input.KeyCode == toggle_fov then
			fovhidden = not fovhidden
			UpdateSaves()
			if not fovhidden then
				FovGui.Visible = true
				fov = oldfov
			elseif fovhidden then
				FovGui.Visible = false
				fov = 120
			end
			if not fovhidden then
				oldfov = fov
			end
		elseif Input.KeyCode == toggle_bottompos then
			bottompos = not bottompos
			UpdateSaves()
			if bottompos then
				Bottom.Position = UDim2.new(.5, 0, 1, 1)
			end
		elseif Input.KeyCode == toggle_performance then
			performancemode = not performancemode
			UpdateSaves()
			setText("Performance Mode "..(performancemode and "Enabled" or "Disabled"))
		elseif Input.KeyCode == toggle_chams then
			esp_chams = not esp_chams
			UpdateSaves()
			setText("Chams "..(esp_chams and "Enabled" or "Disabled"))
			Notification({
				Title = "ESP";
				Text = "Chams: "..(esp_chams and "Enabled" or "Disabled");
				Duration = 2;
			})
		elseif Input.KeyCode == toggle_tracers then
			esp_tracers = not esp_tracers
			UpdateSaves()
			setText("Tracers "..(esp_chams and "Enabled" or "Disabled"))
			Notification({
				Title = "ESP";
				Text = "Tracers: "..(esp_tracers and "Enabled" or "Disabled");
				Duration = 2;
			})
		elseif Input.KeyCode == toggle_boxes then
			bounding_box = not bounding_box
			UpdateSaves()
			setText("Bounding Boxes "..(bounding_box and "Enabled" or "Disabled"))
			Notification({
				Title = "ESP";
				Text = "Bounding Boxes: "..(bounding_box and "Enabled" or "Disabled");
				Duration = 2;
			})
		elseif Input.KeyCode == toggle_font then
			currentfont = (currentfont + 1) > #fonts and 1 or currentfont + 1
			UpdateSaves()
			for _, v in next, GUI:GetDescendants() do
				if v.Name ~= "KeysList" then
					if v:IsA("TextLabel") or v:IsA("TextButton") then
						v.Font = fonts[currentfont]
					end
				end
			end
		end
	end)
	 
	UIS.InputEnded:Connect(function(Input)
		if Input.KeyCode == toggle_aim or Input.UserInputType == toggle_aim then
			aim_toggled = false
		end
	end)
	 
	local function checkifspawned(x)
		spawned = false
		while not spawned and game.PlaceId == 292439477 do
			spawned = distfromspawn(x) > 200 and true or false
			wait(1 / 5)
		end
		spawned = true
	end
	 
	checkifspawned(Player)
	Player.CharacterAdded:Connect(function(c)
		checkifspawned(Player)
	 
		for _, v in next, ESP:GetDescendants() do
			if v:IsA("Frame") and v.Name:match("-") then
				v:Destroy()
			end
		end
	end)
	 
	Notification({
		Title = "GameSense "..version;
		Text = "Cheat loaded successfully.";
		Icon = "rbxassetid://2572157833";
		Duration = 10;
	})
	 
	RS.RenderStepped:Connect(function()
		if cursor then
			FovGui.Position = cursor.Position - UDim2.new(0, FovGui.AbsoluteSize.X / 2, 0, FovGui.AbsoluteSize.Y / 2)
			Indicator.Position = cursor.Position + UDim2.new(0, 0, 0, 40)
		end
	end)
	 
	Mouse.Button1Down:Connect(function()
		spawn(function()
			if FovGui.Visible then
				FovGui:TweenSize(UDim2.new(0, Camera.ViewportSize.X / (90 / fov) * 2.35, 0, Camera.ViewportSize.X / (90 / fov) * 2.35), Enum.EasingDirection.InOut, Enum.EasingStyle.Quad, .1, true)
				wait(.1)
				FovGui:TweenSize(UDim2.new(0, Camera.ViewportSize.X / (90 / fov) * 2, 0, Camera.ViewportSize.X / (90 / fov) * 2), Enum.EasingDirection.InOut, Enum.EasingStyle.Quad, .1, true)
			end
		end)
	end)
	 
	while true do
		Indicator.Text = (not fovhidden and (aim_priority > 1 and "FOV: "..fov.."\n" or "Distance\n") or "")..(((Camera.focus.p - Camera.CFrame.p).magnitude > 0.6 and not (UIS:IsMouseButtonPressed(Enum.UserInputType.MouseButton3) or UIS:IsMouseButtonPressed(Enum.UserInputType.MouseButton2))) and "Third Person Sens: "..tsens or "Sens: "..sens)..(aim_toggled and "\nAiming" or "")
		if not bottompos then
			Bottom.Position = cursor.Position
		end
		if esp_toggled then
			for _, v in next, ESP:children() do
				if v ~= Bottom and not Players:FindFirstChild(v.Name) then
					v:Destroy()
				end
			end
			for _, v in next, Players:GetPlayers() do
				local Char = v.Character
				if Char and spawned and v ~= Player and Char:FindFirstChild(targetpart) and distfromspawn(v) > 100 then
					if ffa or v.TeamColor ~= Player.TeamColor then
						local X = Camera:GetPartsObscuringTarget({
							Camera.CFrame.p,
							Char[targetpart].CFrame.p
						}, {
							v.Character,
							Char,
							Camera,
							unpack(windows)
						})
						local Dist = Player:DistanceFromCharacter(Char:FindFirstChild(targetpart).Position)
						local Color = hiddencolor
						local Folder = ESP:FindFirstChild(v.Name) or Instance.new("Folder", ESP)
						Folder.Name = v.Name
				-- ESP
						local Head = Folder:FindFirstChild("Head") or Instance.new("Frame", Folder)
						if not Folder:FindFirstChild("Head") then
							Head.Name = "Head"
							Head.BorderSizePixel = 1
							Head.BorderColor3 = Color3.new(0, 0, 0)
							Head.BackgroundTransparency = 0
						end
						Head.BackgroundColor3 = #X > 0 and hiddencolor or #X == 0 and visiblecolor
						Head.Rotation = headboxshape == "diamond" and 45 or 0
						Head.ZIndex = 3
						local HP = Folder:FindFirstChild("HP") or Instance.new("TextLabel", Folder)
						if not Folder:FindFirstChild("HP") then
							HP.Name = "HP"
							HP.TextTransparency = Head.BackgroundTransparency - .4
							HP.Font = fonts[currentfont]
							HP.TextStrokeTransparency = .6
							HP.BackgroundTransparency = 1
							HP.TextSize = 14
						end
						HP.Text = showdists and Char.Name.."\n"..math.floor(Dist + .5) or Char.Name
						if aim_toggled and target == Char then
							Head.Size = UDim2.new(0, headboxaimsize, 0, headboxaimsize)
							Head.BackgroundColor3 = aimingcolor
							HP.Text = showdists and "["..Char.Name.."]".."\n"..math.floor(Dist + .5) or "["..Char.Name.."]"
							HP.TextSize = 16
						else
							Head.Size = UDim2.new(0, headboxsize, 0, headboxsize)
						end
						HP.TextColor3 = Head.BackgroundColor3
						local toScreen = Camera:WorldToScreenPoint(Char[targetpart].CFrame.p)
						if #X == 0 then
							Color = visiblecolor
						end
						Head.Position = UDim2.new(0, toScreen.X - Head.Size.X.Offset / 2, 0, toScreen.Y - Head.Size.Y.Offset / 2)
						HP.Position = Head.Position - UDim2.new(0, 0, 0, textoffset)
						if esp_tracers then
							local Line = DrawLine(Folder, ESP.Bottom, Head, linesize, Head.BackgroundColor3, .75, 1, Color3.new(0, 0, 0))
							Line.Visible = Head.Visible
						else
							local imtired = Folder:FindFirstChild(ESP.Bottom.Name.."-"..Head.Name)
							if imtired then
								imtired:Destroy()
							end
						end
						if toScreen.Z <= 0 then
							Head.Visible = false
						else
							Head.Visible = true
						end
						HP.Visible = Head.Visible
						if Char:FindFirstChild("Humanoid") and Char.Humanoid.RigType == Enum.HumanoidRigType.R6 then
							local Neck = Folder:FindFirstChild("Neck") or Instance.new("Frame", Folder)
							Neck.Name = "Neck"
							Neck.ZIndex = 2
							if Char["Torso"] ~= nil then
								local Pos = (Char.Torso.CFrame * CFrame.new(0, .8, 0)).p
								local X, Y, Z = Camera:WorldToScreenPoint(Pos).X, Camera:WorldToScreenPoint(Pos).Y, Camera:WorldToScreenPoint(Pos).Z
								Neck.Position = UDim2.new(0, X, 0, Y)
								Neck.BorderSizePixel = 0
								if Z <= 0 then
									Neck.Visible = false
								else
									Neck.Visible = true
								end
							else
								Neck.Visible = false
							end
				--
							local Pelvis = Folder:FindFirstChild("Pelvis") or Instance.new("Frame", Folder)
							Pelvis.Name = "Pelvis"
							Pelvis.ZIndex = 2
							Pelvis.BorderSizePixel = 0
							if Char["Torso"] ~= nil then
								local Pos = (Char.Torso.CFrame * CFrame.new(0, -1, 0)).p
								local X, Y, Z = Camera:WorldToScreenPoint(Pos).X, Camera:WorldToScreenPoint(Pos).Y, Camera:WorldToScreenPoint(Pos).Z
								Pelvis.Position = UDim2.new(0, X, 0, Y)
								if Z <= 0 then
									Pelvis.Visible = false
								else
									Pelvis.Visible = true
								end
							else
								Pelvis.Visible = false
							end
				--
							local RightFoot = Folder:FindFirstChild("Right Foot") or Instance.new("Frame", Folder)
							RightFoot.Name = "Right Foot"
							RightFoot.ZIndex = 2
							RightFoot.BorderSizePixel = 0
							if Char["Right Leg"] ~= nil then
								local Pos = (Char["Right Leg"].CFrame * CFrame.new(0, -1, 0)).p
								local X, Y, Z = Camera:WorldToScreenPoint(Pos).X, Camera:WorldToScreenPoint(Pos).Y, Camera:WorldToScreenPoint(Pos).Z
								RightFoot.Position = UDim2.new(0, X, 0, Y)
								if Z <= 0 then
									RightFoot.Visible = false
								else
									RightFoot.Visible = true
								end
							else
								RightFoot.Visible = false
							end
				--
							local LeftFoot = Folder:FindFirstChild("Left Foot") or Instance.new("Frame", Folder)
							LeftFoot.Name = "Left Foot"
							if Char["Left Leg"] ~= nil then
								local Pos = (Char["Left Leg"].CFrame * CFrame.new(0, -1, 0)).p
								local X, Y, Z = Camera:WorldToScreenPoint(Pos).X, Camera:WorldToScreenPoint(Pos).Y, Camera:WorldToScreenPoint(Pos).Z
								LeftFoot.Position = UDim2.new(0, X, 0, Y)
								LeftFoot.BorderSizePixel = 0
								if Z <= 0 then
									LeftFoot.Visible = false
								else
									LeftFoot.Visible = true
								end
							else
								LeftFoot.Visible = false
							end
				--
							local RightHand = Folder:FindFirstChild("Right Hand") or Instance.new("Frame", Folder)
							RightHand.Name = "Right Hand"
							RightHand.ZIndex = 2
							RightHand.BorderSizePixel = 0
							if Char["Right Arm"] ~= nil then
								local Pos = (Char["Right Arm"].CFrame * CFrame.new(0, -1, 0)).p
								local X, Y, Z = Camera:WorldToScreenPoint(Pos).X, Camera:WorldToScreenPoint(Pos).Y, Camera:WorldToScreenPoint(Pos).Z
								RightHand.Position = UDim2.new(0, X, 0, Y)
								if Z <= 0 then
									RightHand.Visible = false
								else
									RightHand.Visible = true
								end
							else
								RightHand.Visible = false
							end
				--
							local LeftHand = Folder:FindFirstChild("Left Hand") or Instance.new("Frame", Folder)
							LeftHand.Name = "Left Hand"
							LeftHand.ZIndex = 2
							LeftHand.BorderSizePixel = 0
							if Char["Left Arm"] ~= nil then
								local Pos = (Char["Left Arm"].CFrame * CFrame.new(0, -1, 0)).p
								local X, Y, Z = Camera:WorldToScreenPoint(Pos).X, Camera:WorldToScreenPoint(Pos).Y, Camera:WorldToScreenPoint(Pos).Z
								LeftHand.Position = UDim2.new(0, X, 0, Y)
								if Z <= 0 then
									LeftHand.Visible = false
								else
									LeftHand.Visible = true
								end
							else
								LeftHand.Visible = false
							end
				-- draw joints
							if esp_bones then
								if Head.Visible then
									DrawLine(Folder, Head, Neck, 1, Color3.new(1, 1, 1), Head.BackgroundTransparency)
								end
								if Neck.Visible then
									DrawLine(Folder, Neck, Pelvis, 1, Color3.new(1, 1, 1), Head.BackgroundTransparency)
								end
								if Neck.Visible then
									DrawLine(Folder, Neck, RightHand, 1, Color3.new(1, 1, 1), Head.BackgroundTransparency)
								end
								if Neck.Visible then
									DrawLine(Folder, Neck, LeftHand, 1, Color3.new(1, 1, 1), Head.BackgroundTransparency)
								end
								if Pelvis.Visible then
									DrawLine(Folder, Pelvis, RightFoot, 1, Color3.new(1, 1, 1), Head.BackgroundTransparency)
								end
								if Pelvis.Visible then
									DrawLine(Folder, Pelvis, LeftFoot, 1, Color3.new(1, 1, 1), Head.BackgroundTransparency)
								end
							end
						end
	 
						if esp_chams then
							for _, Part in next, Char:children() do
								if Part:IsA("BasePart") and Part.Name ~= "HumanoidRootPart" then
									local Adornment = Folder:FindFirstChild(Part.Name.."_Cham") or Instance.new("BoxHandleAdornment", Folder)
									if not Folder:FindFirstChild(Part.Name.."_Cham") then
										Adornment.Name = Part.Name.."_Cham"
										Adornment.Adornee = Part
										Adornment.AlwaysOnTop = true
										Adornment.Size = Part.Name == "Head" and Vector3.new(1, 1, 1) or Part.Size
										Adornment.ZIndex = 1
									end
									Adornment.Color3 = Head.BackgroundColor3
								end
							end
						else
							for _, v in next, Folder:GetDescendants() do
								if v.Name:match("Cham") then
									v:Destroy()
								end
							end
						end
	 
						if bounding_box and Char:FindFirstChild("HumanoidRootPart") then
							local Box = Char:FindFirstChild("Box") or Instance.new("BillboardGui", Char)
							if not Char:FindFirstChild("Box") then
								Box.Name = "Box"
								Box.Adornee = Char:FindFirstChild("HumanoidRootPart")
								Box.AlwaysOnTop = true
								Box.LightInfluence = 0
								Box.StudsOffset = Vector3.new(0, -Box.Adornee.Size.Y / 4, 0)
								Box.Size = UDim2.new(4, 1, 5, 1)
								local Top = Instance.new("Frame", Box)
								Top.Size = UDim2.new(1, 0, 0, box_line_size)
								Top.BorderSizePixel = 0
								local Bot = Top:Clone()
								Bot.Position = UDim2.new(0, 0, 1, -box_line_size)
								Bot.Parent = Box
								local Left = Top:Clone()
								Left.Size = UDim2.new(0, 1, 1, 0)
								Left.Parent = Box
								local Right = Left:Clone()
								Right.Position = UDim2.new(1, -box_line_size, 0, 0)
								Right.Parent = Box
							end
							for _, v in next, Box:children() do
								if v:IsA("Frame") then
									v.BackgroundColor3 = Head.BackgroundColor3
								end
							end
						else
							local Box = Char:FindFirstChild("Box")
							if Box then
								Box:Destroy()
							end
						end
	 
						if lockedon and target and aim_line and ESP:FindFirstChild(target.Name) then
							DrawLine(ESP, cursor, ESP:FindFirstChild(target.Name).Head, 1, Head.BackgroundColor3, .5)
						end
	 
					else
						if ESP:FindFirstChild(v.Name) then
							ESP:FindFirstChild(v.Name):Destroy()
						end
					end
				else
					if ESP:FindFirstChild(v.Name) then
						ESP:FindFirstChild(v.Name):Destroy()
					end
				end
			end
		else
			for _, v in next, ESP:children() do
				if v:IsA("Folder") then
					v:Destroy()
				end
			end
		end
		if performancemode then
			wait(1 / (workspace:GetRealPhysicsFPS() * .75))
		else
			RS.Stepped:wait()
		end
	end
end)

Section:NewButton("Unnamed-ESP", "GreatZ So Gay", function()
    assert(Drawing, 'exploit not supported')

if not syn and not PROTOSMASHER_LOADED then print'Unnamed ESP only officially supports Synapse and Protosmasher! If you\'re an exploit developer and have added drawing API to your exploit, try setting syn as true then checking if that works, otherwise, DM me on discord @ cppbook.org#1968 or add an issue to the Unnamed ESP Github Repository and I\'ll see it through email!' end

local UserInputService	= game:GetService'UserInputService';
local HttpService	= game:GetService'HttpService';
local GUIService	= game:GetService'GuiService';
local TweenService	= game:GetService'TweenService';
local RunService	= game:GetService'RunService';
local Players		= game:GetService'Players';
local LocalPlayer	= Players.LocalPlayer;
local Camera		= workspace.CurrentCamera;
local Mouse		= LocalPlayer:GetMouse();
local V2New		= Vector2.new;
local V3New		= Vector3.new;
local WTVP		= Camera.WorldToViewportPoint;
local WorldToViewport	= function(...) return WTVP(Camera, ...) end;
local Menu		= {};
local MouseHeld		= false;
local LastRefresh	= 0;
local OptionsFile	= 'IC3_ESP_SETTINGS.dat';
local Binding		= false;
local BindedKey		= nil;
local OIndex		= 0;
local LineBox		= {};
local UIButtons		= {};
local Sliders		= {};
local ColorPicker	= { Loading = false; LastGenerated = 0 };
local Dragging		= false;
local DraggingUI	= false;
local Rainbow		= false;
local DragOffset	= V2New();
local DraggingWhat	= nil;
local OldData		= {};
local IgnoreList	= {};
local EnemyColor	= Color3.new(1, 0, 0);
local TeamColor		= Color3.new(0, 1, 0);
local MenuLoaded	= false;
local ErrorLogging	= false;
local TracerPosition	= V2New(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y - 135);
local DragTracerPosition= false;
local SubMenu 		= {};
local IsSynapse 	= syn and not PROTOSMASHER_LOADED;
local Connections 	= { Active = {} };
local Signal 		= {}; Signal.__index = Signal;
local GetCharacter;
local CurrentColorPicker;
local Spectating;

local Executor = (identifyexecutor or (function() return '' end))()
local SupportedExploits = { 'Synapse X', 'ScriptWare', 'Krnl', 'OxygenU', 'Temple' }
local QUAD_SUPPORTED_EXPLOIT = table.find(SupportedExploits, Executor) ~= nil

-- if not PROTOSMASHER_LOADED then Drawing.UseCompatTransparency = true; end -- For Elysian

shared.MenuDrawingData	= shared.MenuDrawingData or { Instances = {} };
shared.InstanceData	= shared.InstanceData or {};
shared.RSName		= shared.RSName or ('UnnamedESP_by_ic3-' .. HttpService:GenerateGUID(false));

local GetDataName	= shared.RSName .. '-GetData';
local UpdateName	= shared.RSName .. '-Update';

local Debounce		= setmetatable({}, {
	__index = function(t, i)
		return rawget(t, i) or false
	end;
});

if shared.UESP_InputChangedCon then shared.UESP_InputChangedCon:Disconnect() end
if shared.UESP_InputBeganCon then shared.UESP_InputBeganCon:Disconnect() end
if shared.UESP_InputEndedCon then shared.UESP_InputEndedCon:Disconnect() end
if shared.CurrentColorPicker then shared.CurrentColorPicker:Dispose() end

local RealPrint, LastPrintTick = print, 0;
local LatestPrints = setmetatable({}, { __index = function(t, i) return rawget(t, i) or 0 end });

local function print(...)
	local Content = unpack{...};
	local print = RealPrint;

	if tick() - LatestPrints[Content] > 5 then
		LatestPrints[Content] = tick();
		print(Content);
	end
end

local function FromHex(HEX)
	HEX = HEX:gsub('#', '');
	
	return Color3.fromRGB(tonumber('0x' .. HEX:sub(1, 2)), tonumber('0x' .. HEX:sub(3, 4)), tonumber('0x' .. HEX:sub(5, 6)));
end

local function IsStringEmpty(String)
	if type(String) == 'string' then
		return String:match'^%s+$' ~= nil or #String == 0 or String == '' or false;
	end
	
	return false;
end

local function Set(t, i, v)
	t[i] = v;
end

local Teams = {};
local CustomTeams = { -- Games that don't use roblox's team system
	[2563455047] = {
		Initialize = function()
			Teams.Sheriffs = {}; -- prevent big error
			Teams.Bandits = {}; -- prevent big error
			local Func = game:GetService'ReplicatedStorage':WaitForChild('RogueFunc', 1);
			local Event = game:GetService'ReplicatedStorage':WaitForChild('RogueEvent', 1);
			local S, B = Func:InvokeServer'AllTeamData';

			Teams.Sheriffs = S;
			Teams.Bandits = B;

			Event.OnClientEvent:Connect(function(id, PlayerName, Team, Remove) -- stolen straight from decompiled src lul
				if id == 'UpdateTeam' then
					local TeamTable, NotTeamTable
					if Team == 'Bandits' then
						TeamTable = TDM.Bandits
						NotTeamTable = TDM.Sheriffs
					else
						TeamTable = TDM.Sheriffs
						NotTeamTable = TDM.Bandits
					end
					if Remove then
						TeamTable[PlayerName] = nil
					else
						TeamTable[PlayerName] = true
						NotTeamTable[PlayerName] = nil
					end
					if PlayerName == LocalPlayer.Name then
						TDM.Friendlys = TeamTable
						TDM.Enemies = NotTeamTable
					end
				end
			end)
		end;
		CheckTeam = function(Player)
			local LocalTeam = Teams.Sheriffs[LocalPlayer.Name] and Teams.Sheriffs or Teams.Bandits;
			
			return LocalTeam[Player.Name] and true or false;
		end;
	};
	[5208655184] = {
		CheckTeam = function(Player)
			local LocalLastName = LocalPlayer:GetAttribute'LastName' if not LocalLastName or IsStringEmpty(LocalLastName) then return true end
			local PlayerLastName = Player:GetAttribute'LastName' if not PlayerLastName then return false end

			return PlayerLastName == LocalLastName
		end
	};
	[3541987450] = {
		CheckTeam = function(Player)
			local LocalStats = LocalPlayer:FindFirstChild'leaderstats';
			local LocalLastName = LocalStats and LocalStats:FindFirstChild'LastName'; if not LocalLastName or IsStringEmpty(LocalLastName.Value) then return true; end
			local PlayerStats = Player:FindFirstChild'leaderstats';
			local PlayerLastName = PlayerStats and PlayerStats:FindFirstChild'LastName'; if not PlayerLastName then return false; end

			return PlayerLastName.Value == LocalLastName.Value;
		end;
	};
    [6032399813] = {
		CheckTeam = function(Player)
			local LocalStats = LocalPlayer:FindFirstChild'leaderstats';
			local LocalGuildName = LocalStats and LocalStats:FindFirstChild'Guild'; if not LocalGuildName or IsStringEmpty(LocalGuildName.Value) then return true; end
			local PlayerStats = Player:FindFirstChild'leaderstats';
			local PlayerGuildName = PlayerStats and PlayerStats:FindFirstChild'Guild'; if not PlayerGuildName then return false; end

			return PlayerGuildName.Value == LocalGuildName.Value;
		end;
	};
    [5735553160] = {
		CheckTeam = function(Player)
			local LocalStats = LocalPlayer:FindFirstChild'leaderstats';
			local LocalGuildName = LocalStats and LocalStats:FindFirstChild'Guild'; if not LocalGuildName or IsStringEmpty(LocalGuildName.Value) then return true; end
			local PlayerStats = Player:FindFirstChild'leaderstats';
			local PlayerGuildName = PlayerStats and PlayerStats:FindFirstChild'Guild'; if not PlayerGuildName then return false; end

			return PlayerGuildName.Value == LocalGuildName.Value;
		end;
	};
};

local RenderList = {Instances = {}};

function RenderList:AddOrUpdateInstance(Instance, Obj2Draw, Text, Color)
	RenderList.Instances[Instance] = { ParentInstance = Instance; Instance = Obj2Draw; Text = Text; Color = Color };
	return RenderList.Instances[Instance];
end

local CustomPlayerTag;
local CustomESP;
local CustomCharacter;
local GetHealth;
local GetAliveState;
local CustomRootPartName;

local Modules = {
	[292439477] = {
		CustomESP = function()
			if type(shared.PF_Replication) ~= 'table' then
				local lastScan = shared.pfReplicationScan

				if (tick() - (lastScan or 0)) > 0.01 then
					shared.pfReplicationScan = tick()

					local gc = getgc(true)
					for i = 1, #gc do
						local gcObject = gc[i];
						if type(gcObject) == 'table' and type(rawget(gcObject, 'getbodyparts')) == 'function' then
							shared.PF_Replication = gcObject;
							break
						end
					end
				end

				return
			end

			for Index, Player in pairs(Players:GetPlayers()) do
				if Player == LocalPlayer then continue end

				local Body = shared.PF_Replication.getbodyparts(Player);

				if type(Body) == 'table' and typeof(rawget(Body, 'torso')) == 'Instance' then
					Player.Character = Body.torso.Parent
					continue
				end

				Player.Character = nil;
			end
		end,

		GetHealth = function(Player)
			if type(shared.pfHud) ~= 'table' then
				return false
			end

			return shared.pfHud:getplayerhealth(Player)
		end,

		GetAliveState = function(Player)
			if type(shared.pfHud) ~= 'table' then
				local lastScan = shared.pfHudScan

				if (tick() - (lastScan or 0)) > 0.1 then
					shared.pfHudScan = tick()

					local gc = getgc(true)
					for i = 1, #gc do
						local gcObject = gc[i];
						if type(gcObject) == 'table' and type(rawget(gcObject, 'getplayerhealth')) == 'function' then
							shared.pfHud = gcObject;
							break
						end
					end
				end

				return
			end

			return shared.pfHud:isplayeralive(Player)
		end,

		CustomRootPartName = 'Torso',
	};
	[2950983942] = {
		CustomCharacter = function(Player)
			if workspace:FindFirstChild'Players' then
				return workspace.Players:FindFirstChild(Player.Name);
			end
		end
	};
	[2262441883] = {
		CustomPlayerTag = function(Player)
			return Player:FindFirstChild'Job' and (' [' .. Player.Job.Value .. ']') or '';
		end;
		CustomESP = function()
			if workspace:FindFirstChild'MoneyPrinters' then
				for i, v in pairs(workspace.MoneyPrinters:GetChildren()) do
					local Main	= v:FindFirstChild'Main';
					local Owner	= v:FindFirstChild'TrueOwner';
					local Money	= v:FindFirstChild'Int' and v.Int:FindFirstChild'Money' or nil;
					if Main and Owner and Money then
						local O = tostring(Owner.Value);
						local M = tostring(Money.Value);

						pcall(RenderList.AddOrUpdateInstance, RenderList, v, Main, string.format('Money Printer\nOwned by %s\n[%s]', O, M), Color3.fromRGB(13, 255, 227));
					end
				end
			end
		end;
	};
	-- [4581966615] = {
	-- 	CustomESP = function()
	-- 		if workspace:FindFirstChild'Entities' then
	-- 			for i, v in pairs(workspace.Entities:GetChildren()) do
	-- 				if not v.Name:match'Printer' then continue end

	-- 				local Properties = v:FindFirstChild'Properties' if not Properties then continue end
	-- 				local Main	= v:FindFirstChild'hitbox';
	-- 				local Owner	= Properties:FindFirstChild'Owner';
	-- 				local Money	= Properties:FindFirstChild'CurrentPrinted'
					
	-- 				if Main and Owner and Money then
	-- 					local O = Owner.Value and tostring(Owner.Value) or 'no one';
	-- 					local M = tostring(Money.Value);

	-- 					pcall(RenderList.AddOrUpdateInstance, RenderList, v, Main, string.format('Money Printer\nOwned by %s\n[%s]', O, M), Color3.fromRGB(13, 255, 227));
	-- 				end
	-- 			end
	-- 		end
	-- 	end;
	-- };
	[4801598506] = {
		CustomESP = function()
			if workspace:FindFirstChild'Mobs' and workspace.Mobs:FindFirstChild'Forest1' then
				for i, v in pairs(workspace.Mobs.Forest1:GetChildren()) do
					local Main	= v:FindFirstChild'Head';
					local Hum	= v:FindFirstChild'Mob';

					if Main and Hum then
						pcall(RenderList.AddOrUpdateInstance, RenderList, v, Main, string.format('[%s] [%s/%s]', v.Name, Hum.Health, Hum.MaxHealth), Color3.fromRGB(13, 255, 227));
					end
				end
			end
		end;
	};
	[2555873122] = {
		CustomESP = function()
			if workspace:FindFirstChild'WoodPlanks' then
				for i, v in pairs(workspace:GetChildren()) do
					if v.Name == 'WoodPlanks' then
						local Main = v:FindFirstChild'Wood';

						if Main then
							pcall(RenderList.AddOrUpdateInstance, RenderList, v, Main, 'Wood Planks', Color3.fromRGB(13, 255, 227));
						end
					end
				end
			end
		end;
	};
	[5208655184] = {
		CustomESP = function()
			-- if workspace:FindFirstChild'Live' then
			-- 	for i, v in pairs(workspace.Live:GetChildren()) do
			-- 		if v.Name:sub(1, 1) == '.' then
			-- 			local Main = v:FindFirstChild'Head';

			-- 			if Main then
			-- 				pcall(RenderList.AddOrUpdateInstance, RenderList, v, Main, v.Name:sub(2), Color3.fromRGB(250, 50, 40));
			-- 			end
			-- 		end
			-- 	end
			-- end
		end;
		CustomPlayerTag = function(Player)
			if game.PlaceVersion < 457 then return '' end

			local Name = '';
			local FirstName = Player:GetAttribute'FirstName'

			if typeof(FirstName) == 'string' and #FirstName > 0 then
				local Prefix = '';
				local Extra = {};
				Name = Name .. '\n[';

				if Player:GetAttribute'Prestige' > 0 then
					Name = Name .. '#' .. tostring(Player:GetAttribute'Prestige') .. ' ';
				end
				if not IsStringEmpty(Player:GetAttribute'HouseRank') then
					Prefix = Player:GetAttribute'HouseRank' == 'Owner' and (Player:GetAttribute'Gender' == 'Female' and 'Lady ' or 'Lord ') or '';
				end
				if not IsStringEmpty(FirstName) then
					Name = Name .. '' .. Prefix .. FirstName;
				end
				if not IsStringEmpty(Player:GetAttribute'LastName') then
					Name = Name .. ' ' .. Player:GetAttribute'LastName';
				end

				if not IsStringEmpty(Name) then Name = Name .. ']'; end

				local Character = GetCharacter(Player);

				if Character then
					if Character and Character:FindFirstChild'Danger' then table.insert(Extra, 'D'); end
					if Character:FindFirstChild'ManaAbilities' and Character.ManaAbilities:FindFirstChild'ManaSprint' then table.insert(Extra, 'D1'); end

					if Character:FindFirstChild'Mana'	 		then table.insert(Extra, 'M' .. math.floor(Character.Mana.Value)); end
					if Character:FindFirstChild'Vampirism' 		then table.insert(Extra, 'V'); end
					if Character:FindFirstChild'Observe'		then table.insert(Extra, 'ILL'); end
					if Character:FindFirstChild'Inferi'			then table.insert(Extra, 'NEC'); end
					if Character:FindFirstChild'World\'s Pulse' then table.insert(Extra, 'DZIN'); end
					if Character:FindFirstChild'Shift'		 	then table.insert(Extra, 'MAD'); end
					if Character:FindFirstChild'Head' and Character.Head:FindFirstChild'FacialMarking' then
						local FM = Character.Head:FindFirstChild'FacialMarking';
						if FM.Texture == 'http://www.roblox.com/asset/?id=4072968006' then
							table.insert(Extra, 'HEALER');
						elseif FM.Texture == 'http://www.roblox.com/asset/?id=4072914434' then
							table.insert(Extra, 'SEER');
						elseif FM.Texture == 'http://www.roblox.com/asset/?id=4094417635' then
							table.insert(Extra, 'JESTER');
						elseif FM.Texture == 'http://www.roblox.com/asset/?id=4072968656' then
							table.insert(Extra, 'BLADE');
						end
					end
				end
				if Player:FindFirstChild'Backpack' then
					if Player.Backpack:FindFirstChild'Observe' 			then table.insert(Extra, 'ILL');  end
					if Player.Backpack:FindFirstChild'Inferi'			then table.insert(Extra, 'NEC');  end
					if Player.Backpack:FindFirstChild'World\'s Pulse' 	then table.insert(Extra, 'DZIN'); end
					if Player.Backpack:FindFirstChild'Shift'		 	then table.insert(Extra, 'MAD'); end
				end

				if #Extra > 0 then Name = Name .. ' [' .. table.concat(Extra, '-') .. ']'; end
			end

			return Name;
		end;
	};
	[3541987450] = {
		CustomPlayerTag = function(Player)
			local Name = '';

			if Player:FindFirstChild'leaderstats' then
				Name = Name .. '\n[';
				local Prefix = '';
				local Extra = {};
				if Player.leaderstats:FindFirstChild'Prestige' and Player.leaderstats.Prestige.ClassName == 'IntValue' and Player.leaderstats.Prestige.Value > 0 then
					Name = Name .. '#' .. tostring(Player.leaderstats.Prestige.Value) .. ' ';
				end
				if Player.leaderstats:FindFirstChild'HouseRank' and Player.leaderstats:FindFirstChild'Gender' and Player.leaderstats.HouseRank.ClassName == 'StringValue' and not IsStringEmpty(Player.leaderstats.HouseRank.Value) then
					Prefix = Player.leaderstats.HouseRank.Value == 'Owner' and (Player.leaderstats.Gender.Value == 'Female' and 'Lady ' or 'Lord ') or '';
				end
				if Player.leaderstats:FindFirstChild'FirstName' and Player.leaderstats.FirstName.ClassName == 'StringValue' and not IsStringEmpty(Player.leaderstats.FirstName.Value) then
					Name = Name .. '' .. Prefix .. Player.leaderstats.FirstName.Value;
				end
				if Player.leaderstats:FindFirstChild'LastName' and Player.leaderstats.LastName.ClassName == 'StringValue' and not IsStringEmpty(Player.leaderstats.LastName.Value) then
					Name = Name .. ' ' .. Player.leaderstats.LastName.Value;
				end
				if Player.leaderstats:FindFirstChild'UberTitle' and Player.leaderstats.UberTitle.ClassName == 'StringValue' and not IsStringEmpty(Player.leaderstats.UberTitle.Value) then
					Name = Name .. ', ' .. Player.leaderstats.UberTitle.Value;
				end

				if not IsStringEmpty(Name) then Name = Name .. ']'; end

				local Character = GetCharacter(Player);

				if Character then
					if Character and Character:FindFirstChild'Danger' then table.insert(Extra, 'D'); end
					if Character:FindFirstChild'ManaAbilities' and Character.ManaAbilities:FindFirstChild'ManaSprint' then table.insert(Extra, 'D1'); end

					if Character:FindFirstChild'Mana'	 		then table.insert(Extra, 'M' .. math.floor(Character.Mana.Value)); end
					if Character:FindFirstChild'Vampirism' 		then table.insert(Extra, 'V');    end
					if Character:FindFirstChild'Observe'			then table.insert(Extra, 'ILL');  end
					if Character:FindFirstChild'Inferi'			then table.insert(Extra, 'NEC');  end
					
					if Character:FindFirstChild'World\'s Pulse' 	then table.insert(Extra, 'DZIN'); end
					if Character:FindFirstChild'Head' and Character.Head:FindFirstChild'FacialMarking' then
						local FM = Character.Head:FindFirstChild'FacialMarking';
						if FM.Texture == 'http://www.roblox.com/asset/?id=4072968006' then
							table.insert(Extra, 'HEALER');
						elseif FM.Texture == 'http://www.roblox.com/asset/?id=4072914434' then
							table.insert(Extra, 'SEER');
						elseif FM.Texture == 'http://www.roblox.com/asset/?id=4094417635' then
							table.insert(Extra, 'JESTER');
						end
					end
				end
				if Player:FindFirstChild'Backpack' then
					if Player.Backpack:FindFirstChild'Observe' 			then table.insert(Extra, 'ILL');  end
					if Player.Backpack:FindFirstChild'Inferi'			then table.insert(Extra, 'NEC');  end
					if Player.Backpack:FindFirstChild'World\'s Pulse' 	then table.insert(Extra, 'DZIN'); end
				end

				if #Extra > 0 then Name = Name .. ' [' .. table.concat(Extra, '-') .. ']'; end
			end

			return Name;
		end;
	};

	[4691401390] = { -- Vast Realm
		CustomCharacter = function(Player)
			if workspace:FindFirstChild'Players' then
				return workspace.Players:FindFirstChild(Player.Name);
			end
		end
	};

    [6032399813] = { -- Deepwoken [Etrean]
		CustomPlayerTag = function(Player)
			local Name = '';
            CharacterName = Player:GetAttribute'CharacterName'; -- could use leaderstats but lazy

            if not IsStringEmpty(CharacterName) then
                Name = ('\n[%s]'):format(CharacterName);
                local Character = GetCharacter(Player);
                local Extra = {};

                if Character then
                    local Blood, Armor = Character:FindFirstChild('Blood'), Character:FindFirstChild('Armor');

                    if Blood and Blood.ClassName == 'DoubleConstrainedValue' then
                        table.insert(Extra, ('B%d'):format(Blood.Value));
                    end

                    if Armor and Armor.ClassName == 'DoubleConstrainedValue' then
                        table.insert(Extra, ('A%d'):format(math.floor(Armor.Value / 10)));
                    end
                end

                local BackpackChildren = Player.Backpack:GetChildren()

                for index = 1, #BackpackChildren do
                    local Oath = BackpackChildren[index]
                    if Oath.ClassName == 'Folder' and Oath.Name:find('Talent:Oath') then
                        local OathName = Oath.Name:gsub('Talent:Oath: ', '')
                        table.insert(Extra, OathName);
                    end
                end

                if #Extra > 0 then Name = Name .. ' [' .. table.concat(Extra, '-') .. ']'; end
            end

			return Name;
		end;
	};

    [5735553160] = { -- Deepwoken [Depths]
    CustomPlayerTag = function(Player)
        local Name = '';
        CharacterName = Player:GetAttribute'CharacterName'; -- could use leaderstats but lazy

        if not IsStringEmpty(CharacterName) then
            Name = ('\n[%s]'):format(CharacterName);
            local Character = GetCharacter(Player);
            local Extra = {};

            if Character then
                local Blood, Armor = Character:FindFirstChild('Blood'), Character:FindFirstChild('Armor');

                if Blood and Blood.ClassName == 'DoubleConstrainedValue' then
                    table.insert(Extra, ('B%d'):format(Blood.Value));
                end

                if Armor and Armor.ClassName == 'DoubleConstrainedValue' then
                    table.insert(Extra, ('A%d'):format(math.floor(Armor.Value / 10)));
                end
            end

            local BackpackChildren = Player.Backpack:GetChildren()

            for index = 1, #BackpackChildren do
                local Oath = BackpackChildren[index]
                if Oath.ClassName == 'Folder' and Oath.Name:find('Talent:Oath') then
                    local OathName = Oath.Name:gsub('Talent:Oath: ', '')
                    table.insert(Extra, OathName);
                end
            end

            if #Extra > 0 then Name = Name .. ' [' .. table.concat(Extra, '-') .. ']'; end
        end

        return Name;
    end;
};
};

if Modules[game.PlaceId] ~= nil then
	local Module = Modules[game.PlaceId];
	CustomPlayerTag = Module.CustomPlayerTag or nil;
	CustomESP = Module.CustomESP or nil;
	CustomCharacter = Module.CustomCharacter or nil;
	GetHealth = Module.GetHealth or nil;
	GetAliveState = Module.GetAliveState or nil;
	CustomRootPartName = Module.CustomRootPartName or nil;
end

function GetCharacter(Player)
	return Player.Character or (CustomCharacter and CustomCharacter(Player));
end

function GetMouseLocation()
	return UserInputService:GetMouseLocation();
end

function MouseHoveringOver(Values)
	local X1, Y1, X2, Y2 = Values[1], Values[2], Values[3], Values[4]
	local MLocation = GetMouseLocation();
	return (MLocation.x >= X1 and MLocation.x <= (X1 + (X2 - X1))) and (MLocation.y >= Y1 and MLocation.y <= (Y1 + (Y2 - Y1)));
end

function GetTableData(t) -- basically table.foreach i dont even know why i made this
	if typeof(t) ~= 'table' then return end

	return setmetatable(t, {
		__call = function(t, func)
			if typeof(func) ~= 'function' then return end;
			for i, v in pairs(t) do
				pcall(func, i, v);
			end
		end;
	});
end
local function Format(format, ...)
	return string.format(format, ...);
end
function CalculateValue(Min, Max, Percent)
	return Min + math.floor(((Max - Min) * Percent) + .5);
end

function NewDrawing(InstanceName)
	local Instance = Drawing.new(InstanceName);
	-- pcall(Set, Instance, 'OutlineOpacity', 0.8)
	return (function(Properties)
		for i, v in pairs(Properties) do
			pcall(Set, Instance, i, v);
		end
		return Instance;
	end)
end

function Menu:AddMenuInstance(Name, DrawingType, Properties)
	local Instance;

	if shared.MenuDrawingData.Instances[Name] ~= nil then
		Instance = shared.MenuDrawingData.Instances[Name];
		for i, v in pairs(Properties) do
			pcall(Set, Instance, i, v);
		end
	else
		Instance = NewDrawing(DrawingType)(Properties);
	end

	shared.MenuDrawingData.Instances[Name] = Instance;

	return Instance;
end
function Menu:UpdateMenuInstance(Name)
	local Instance = shared.MenuDrawingData.Instances[Name];
	if Instance ~= nil then
		return (function(Properties)
			for i, v in pairs(Properties) do
				pcall(Set, Instance, i, v);
			end
			return Instance;
		end)
	end
end
function Menu:GetInstance(Name)
	return shared.MenuDrawingData.Instances[Name];
end

local Options = setmetatable({}, {
	__call = function(t, ...)
		local Arguments = {...};
		local Name = Arguments[1];
		OIndex = OIndex + 1;
		rawset(t, Name, setmetatable({
			Name			= Arguments[1];
			Text			= Arguments[2];
			Value			= Arguments[3];
			DefaultValue	= Arguments[3];
			AllArgs			= Arguments;
			Index			= OIndex;
		}, {
			__call = function(t, v, force)
				local self = t;

				if typeof(t.Value) == 'function' then
					t.Value();
				elseif typeof(t.Value) == 'EnumItem' then
					local BT = Menu:GetInstance(Format('%s_BindText', t.Name));
					if not force then
						Binding = true;
						local Val = 0
						while Binding do
							wait();
							Val = (Val + 1) % 17;
							BT.Text = Val <= 8 and '|' or '';
						end
					end
					t.Value = force and v or BindedKey;
					if BT and t.BasePosition and t.BaseSize then
						BT.Text = tostring(t.Value):match'%w+%.%w+%.(.+)';
						BT.Position = t.BasePosition + V2New(t.BaseSize.X - BT.TextBounds.X - 20, -10);
					end
				else
					local NewValue = v;
					if NewValue == nil then NewValue = not t.Value; end
					rawset(t, 'Value', NewValue);

					if Arguments[2] ~= nil and Menu:GetInstance'TopBar'.Visible then
						if typeof(Arguments[3]) == 'number' then
							local AMT = Menu:GetInstance(Format('%s_AmountText', t.Name));
							if AMT then
								AMT.Text = tostring(t.Value);
							end
						else
							local Inner = Menu:GetInstance(Format('%s_InnerCircle', t.Name));
							if Inner then Inner.Visible = t.Value; end
						end
					end
				end
			end;
		}));
	end;
})

function Load()
	local _, Result = pcall(readfile, OptionsFile);
	
	if _ then -- extremely ugly code yea i know but i dont care p.s. i hate pcall
		local _, Table = pcall(HttpService.JSONDecode, HttpService, Result);
		if _ and typeof(Table) == 'table' then
			for i, v in pairs(Table) do
				if typeof(Options[i]) == 'table' and Options[i].Value ~= nil and (typeof(Options[i].Value) == 'boolean' or typeof(Options[i].Value) == 'number') then
					Options[i].Value = v.Value;
					pcall(Options[i], v.Value);
				end
			end

			if Table.TeamColor then TeamColor = Color3.new(Table.TeamColor.R, Table.TeamColor.G, Table.TeamColor.B) end
			if Table.EnemyColor then EnemyColor = Color3.new(Table.EnemyColor.R, Table.EnemyColor.G, Table.EnemyColor.B) end

			if typeof(Table.MenuKey) == 'string' then Options.MenuKey(Enum.KeyCode[Table.MenuKey], true) end
			if typeof(Table.ToggleKey) == 'string' then Options.ToggleKey(Enum.KeyCode[Table.ToggleKey], true) end
		end
	end
end

Options('Enabled', 'ESP Enabled', true);
Options('ShowTeam', 'Show Team', true);
Options('ShowTeamColor', 'Show Team Color', false);
Options('ShowName', 'Show Names', true);
Options('ShowDistance', 'Show Distance', true);
Options('ShowHealth', 'Show Health', true);
Options('ShowBoxes', 'Show Boxes', true);
Options('ShowTracers', 'Show Tracers', true);
Options('ShowDot', 'Show Head Dot', false);
Options('VisCheck', 'Visibility Check', false);
Options('Crosshair', 'Crosshair', false);
Options('TextOutline', 'Text Outline', true);
-- Options('Rainbow', 'Rainbow Mode', false);
Options('TextSize', 'Text Size', syn and 18 or 14, 10, 24); -- cuz synapse fonts look weird???
Options('MaxDistance', 'Max Distance', 2500, 100, 25000);
Options('RefreshRate', 'Refresh Rate (ms)', 5, 1, 200);
Options('YOffset', 'Y Offset', 0, -200, 200);
Options('MenuKey', 'Menu Key', Enum.KeyCode.F4, 1);
Options('ToggleKey', 'Toggle Key', Enum.KeyCode.F3, 1);
Options('ChangeColors', SENTINEL_LOADED and 'Sentinel Unsupported' or 'Change Colors', function()
	if SENTINEL_LOADED then return end

	SubMenu:Show(GetMouseLocation(), 'Unnamed Colors', {
		{
			Type = 'Color'; Text = 'Team Color'; Color = TeamColor;

			Function = function(Circ, Position)
				if tick() - ColorPicker.LastGenerated < 1 then return; end

				if shared.CurrentColorPicker then shared.CurrentColorPicker:Dispose() end
				local ColorPicker = ColorPicker.new(Position - V2New(-10, 50));
				CurrentColorPicker = ColorPicker;
				shared.CurrentColorPicker = CurrentColorPicker;
				ColorPicker.ColorChanged:Connect(function(Color) Circ.Color = Color TeamColor = Color Options.TeamColor = Color end);
			end
		};
		{
			Type = 'Color'; Text = 'Enemy Color'; Color = EnemyColor;

			Function = function(Circ, Position)
				if tick() - ColorPicker.LastGenerated < 1 then return; end

				if shared.CurrentColorPicker then shared.CurrentColorPicker:Dispose() end
				local ColorPicker = ColorPicker.new(Position - V2New(-10, 50));
				CurrentColorPicker = ColorPicker;
				shared.CurrentColorPicker = CurrentColorPicker;
				ColorPicker.ColorChanged:Connect(function(Color) Circ.Color = Color EnemyColor = Color Options.EnemyColor = Color end);
			end
		};
		{
			Type = 'Button'; Text = 'Reset Colors';

			Function = function()
				EnemyColor = Color3.new(1, 0, 0);
				TeamColor = Color3.new(0, 1, 0);

				local C1 = Menu:GetInstance'Sub-ColorPreview.1'; if C1 then C1.Color = TeamColor end
				local C2 = Menu:GetInstance'Sub-ColorPreview.2'; if C2 then C2.Color = EnemyColor end
			end
		};
		{
			Type = 'Button'; Text = 'Rainbow Mode';

			Function = function()
				Rainbow = not Rainbow;
			end
		};
	});
end, 2);
Options('ResetSettings', 'Reset Settings', function()
	for i, v in pairs(Options) do
		if Options[i] ~= nil and Options[i].Value ~= nil and Options[i].Text ~= nil and (typeof(Options[i].Value) == 'boolean' or typeof(Options[i].Value) == 'number' or typeof(Options[i].Value) == 'EnumItem') then
			Options[i](Options[i].DefaultValue, true);
		end
	end
end, 5);
Options('LoadSettings', 'Load Settings', Load, 4);
Options('SaveSettings', 'Save Settings', function()
	local COptions = {};

	for i, v in pairs(Options) do
		COptions[i] = v;
	end
	
	if typeof(TeamColor) == 'Color3' then COptions.TeamColor = { R = TeamColor.R; G = TeamColor.G; B = TeamColor.B } end
	if typeof(EnemyColor) == 'Color3' then COptions.EnemyColor = { R = EnemyColor.R; G = EnemyColor.G; B = EnemyColor.B } end
	
	if typeof(COptions.MenuKey.Value) == 'EnumItem' then COptions.MenuKey = COptions.MenuKey.Value.Name end
	if typeof(COptions.ToggleKey.Value) == 'EnumItem' then COptions.ToggleKey = COptions.ToggleKey.Value.Name end

	writefile(OptionsFile, HttpService:JSONEncode(COptions));
end, 3);

Load(1);

Options('MenuOpen', nil, true);

local function Combine(...)
	local Output = {};
	for i, v in pairs{...} do
		if typeof(v) == 'table' then
			table.foreach(v, function(i, v)
				Output[i] = v;
			end)
		end
	end
	return Output
end

function LineBox:Create(Properties)
	local Box = { Visible = true }; -- prevent errors not really though dont worry bout the Visible = true thing

	local Properties = Combine({
		Transparency	= 1;
		Thickness		= 3;
		Visible			= true;
	}, Properties);

	if shared.am_ic3 then -- sory just my preference, dynamic boxes will be optional in unnamed esp v2
		Box['OutlineSquare']= NewDrawing'Square'(Properties);
		Box['Square'] 		= NewDrawing'Square'(Properties);
	elseif QUAD_SUPPORTED_EXPLOIT then
		Box['Quad']			= NewDrawing'Quad'(Properties);
	else
		Box['TopLeft']		= NewDrawing'Line'(Properties);
		Box['TopRight']		= NewDrawing'Line'(Properties);
		Box['BottomLeft']	= NewDrawing'Line'(Properties);
		Box['BottomRight']	= NewDrawing'Line'(Properties);
	end

	function Box:Update(CF, Size, Color, Properties, Parts)
		if not CF or not Size then return end

		if shared.am_ic3 and typeof(Parts) == 'table' then
			local AllCorners = {};
			
			for i, v in pairs(Parts) do
				-- if not v:IsA'BasePart' then continue end
				
				local CF, Size = v.CFrame, v.Size;
				-- CF, Size = v.Parent:GetBoundingBox();

				local Corners = {
					Vector3.new(CF.X + Size.X / 2, CF.Y + Size.Y / 2, CF.Z + Size.Z / 2);
					Vector3.new(CF.X - Size.X / 2, CF.Y + Size.Y / 2, CF.Z + Size.Z / 2);
					Vector3.new(CF.X - Size.X / 2, CF.Y - Size.Y / 2, CF.Z - Size.Z / 2);
					Vector3.new(CF.X + Size.X / 2, CF.Y - Size.Y / 2, CF.Z - Size.Z / 2);
					Vector3.new(CF.X - Size.X / 2, CF.Y + Size.Y / 2, CF.Z - Size.Z / 2);
					Vector3.new(CF.X + Size.X / 2, CF.Y + Size.Y / 2, CF.Z - Size.Z / 2);
					Vector3.new(CF.X - Size.X / 2, CF.Y - Size.Y / 2, CF.Z + Size.Z / 2);
					Vector3.new(CF.X + Size.X / 2, CF.Y - Size.Y / 2, CF.Z + Size.Z / 2);
				};

				for i, v in pairs(Corners) do
					table.insert(AllCorners, v);
				end

				-- break
			end

			local xMin, yMin = Camera.ViewportSize.X, Camera.ViewportSize.Y;
			local xMax, yMax = 0, 0;
			local Vs = true;

			for i, v in pairs(AllCorners) do				
				local Position, V = WorldToViewport(v);

				if VS and not V then Vs = false break end

				if Position.X > xMax then
					xMax = Position.X;
				end
				if Position.X < xMin then
					xMin = Position.X;
				end
				if Position.Y > yMax then
					yMax = Position.Y;
				end
				if Position.Y < yMin then
					yMin = Position.Y;
				end
			end

			local xSize, ySize = xMax - xMin, yMax - yMin;

			local Outline = Box['OutlineSquare'];
			local Square = Box['Square'];
			Outline.Visible = Vs;
			Square.Visible = Vs;
			Square.Position = V2New(xMin, yMin);
			Square.Color	= Color;
			Square.Thickness = math.floor(Outline.Thickness * 0.3);
			-- Square.Position = V2New(xMin, yMin);
			Square.Size = V2New(xSize, ySize);
			Outline.Position = Square.Position;
			Outline.Size = Square.Size;
			Outline.Color = Color3.new(0.12, 0.12, 0.12);
			Outline.Transparency = 0.75;

			return
		end
		
		local TLPos, Visible1	= WorldToViewport((CF * CFrame.new( Size.X,  Size.Y, 0)).Position);
		local TRPos, Visible2	= WorldToViewport((CF * CFrame.new(-Size.X,  Size.Y, 0)).Position);
		local BLPos, Visible3	= WorldToViewport((CF * CFrame.new( Size.X, -Size.Y, 0)).Position);
		local BRPos, Visible4	= WorldToViewport((CF * CFrame.new(-Size.X, -Size.Y, 0)).Position);

		local Quad = Box['Quad'];

		if QUAD_SUPPORTED_EXPLOIT then
			if Visible1 and Visible2 and Visible3 and Visible4 then
				Quad.Visible = true;
				Quad.Color	= Color;
				Quad.PointA = V2New(TLPos.X, TLPos.Y);
				Quad.PointB = V2New(TRPos.X, TRPos.Y);
				Quad.PointC = V2New(BRPos.X, BRPos.Y);
				Quad.PointD = V2New(BLPos.X, BLPos.Y);
			else
				Box['Quad'].Visible = false;
			end
		else
			Visible1 = TLPos.Z > 0 -- (commented | reason: random flashes);
			Visible2 = TRPos.Z > 0 -- (commented | reason: random flashes);
			Visible3 = BLPos.Z > 0 -- (commented | reason: random flashes);
			Visible4 = BRPos.Z > 0 -- (commented | reason: random flashes);

			-- ## BEGIN UGLY CODE
			if Visible1 then
				Box['TopLeft'].Visible		= true;
				Box['TopLeft'].Color		= Color;
				Box['TopLeft'].From			= V2New(TLPos.X, TLPos.Y);
				Box['TopLeft'].To			= V2New(TRPos.X, TRPos.Y);
			else
				Box['TopLeft'].Visible		= false;
			end
			if Visible2 then
				Box['TopRight'].Visible		= true;
				Box['TopRight'].Color		= Color;
				Box['TopRight'].From		= V2New(TRPos.X, TRPos.Y);
				Box['TopRight'].To			= V2New(BRPos.X, BRPos.Y);
			else
				Box['TopRight'].Visible		= false;
			end
			if Visible3 then
				Box['BottomLeft'].Visible	= true;
				Box['BottomLeft'].Color		= Color;
				Box['BottomLeft'].From		= V2New(BLPos.X, BLPos.Y);
				Box['BottomLeft'].To		= V2New(TLPos.X, TLPos.Y);
			else
				Box['BottomLeft'].Visible	= false;
			end
			if Visible4 then
				Box['BottomRight'].Visible	= true;
				Box['BottomRight'].Color	= Color;
				Box['BottomRight'].From		= V2New(BRPos.X, BRPos.Y);
				Box['BottomRight'].To		= V2New(BLPos.X, BLPos.Y);
			else
				Box['BottomRight'].Visible	= false;
			end
			-- ## END UGLY CODE
			if Properties and typeof(Properties) == 'table' then
				GetTableData(Properties)(function(i, v)
					pcall(Set, Box['TopLeft'],		i, v);
					pcall(Set, Box['TopRight'],		i, v);
					pcall(Set, Box['BottomLeft'],	i, v);
					pcall(Set, Box['BottomRight'],	i, v);
				end)
			end
		end
	end
	function Box:SetVisible(bool)
		if shared.am_ic3 then
			Box['Square'].Visible = bool;
			Box['OutlineSquare'].Visible = bool;
		else
			pcall(Set, Box['Quad'],				'Visible', bool);
		end
		-- pcall(Set, Box['TopLeft'],		'Visible', bool);
		-- pcall(Set, Box['TopRight'],		'Visible', bool);
		-- pcall(Set, Box['BottomLeft'],	'Visible', bool);
		-- pcall(Set, Box['BottomRight'],	'Visible', bool);
	end
	function Box:Remove()
		self:SetVisible(false);
		if shared.am_ic3 then
			Box['Square']:Remove();
			Box['OutlineSquare']:Remove();
		else
			Box['Quad']:Remove();
		end
		-- Box['TopLeft']:Remove();
		-- Box['TopRight']:Remove();
		-- Box['BottomLeft']:Remove();
		-- Box['BottomRight']:Remove();
	end

	return Box;
end

local Colors = {
	White = FromHex'ffffff';
	Primary = {
		Main	= FromHex'424242';
		Light	= FromHex'6d6d6d';
		Dark	= FromHex'1b1b1b';
	};
	Secondary = {
		Main	= FromHex'e0e0e0';
		Light	= FromHex'ffffff';
		Dark	= FromHex'aeaeae';
	};
};

function Connections:Listen(Connection, Function)
    local NewConnection = Connection:Connect(Function);
    table.insert(self.Active, NewConnection);
    return NewConnection;
end

function Connections:DisconnectAll()
    for Index, Connection in pairs(self.Active) do
        if Connection.Connected then
            Connection:Disconnect();
        end
    end
    
    self.Active = {};
end

function Signal.new()
	local self = setmetatable({ _BindableEvent = Instance.new'BindableEvent' }, Signal);
    
	return self;
end

function Signal:Connect(Callback)
    assert(typeof(Callback) == 'function', 'function expected; got ' .. typeof(Callback));

	return self._BindableEvent.Event:Connect(function(...) Callback(...) end);
end

function Signal:Fire(...)
    self._BindableEvent:Fire(...);
end

function Signal:Wait()
    local Arguments = self._BindableEvent:Wait();

    return Arguments;
end

function Signal:Disconnect()
    if self._BindableEvent then
        self._BindableEvent:Destroy();
    end
end

local function GetMouseLocation()
	return UserInputService:GetMouseLocation();
end

local function IsMouseOverDrawing(Drawing, MousePosition)
	local TopLeft = Drawing.Position;
	local BottomRight = Drawing.Position + Drawing.Size;
    local MousePosition = MousePosition or GetMouseLocation();
    
    return MousePosition.X > TopLeft.X and MousePosition.Y > TopLeft.Y and MousePosition.X < BottomRight.X and MousePosition.Y < BottomRight.Y;
end

local ImageCache = {};

local function SetImage(Drawing, Url)
	local Data = IsSynapse and game:HttpGet(Url) or Url;

	print(Drawing, IsSynapse)

	Drawing[IsSynapse and 'Data' or 'Uri'] = ImageCache[Url] or Data;
	ImageCache[Url] = Data;
    
    if not IsSynapse then repeat wait() until Drawing.Loaded; end
end

-- oh god unnamed esp needs an entire rewrite, someone make a better one pls im too lazy
-- btw the color picker was made seperately so it doesnt fit with the code of unnamed esp

local function CreateDrawingsTable()
    local Drawings = { __Objects = {} };
    local Metatable = {};

    function Metatable.__index(self, Index)
        local Object = rawget(self.__Objects, Index);
        
        if not Object or (IsSynapse and not Object.__SELF.__OBJECT_EXISTS) then
            local Type = Index:sub(1, Index:find'-' - 1);

            Success, Object = pcall(Drawing.new, Type);

            if not Object or not Success then return function() end; end

            self.__Objects[Index] = setmetatable({ __SELF = Object; Type = Type }, {
                __call = function(self, Properties)
                    local Object = rawget(self, '__SELF'); if IsSynapse and not Object.__OBJECT_EXISTS then return false, 'render object destroyed'; end

                    if Properties == false then
                        Object.Visible = false;
                        Object.Transparency = 0;
                        Object:Remove();
                        
                        return true;
                    end
                    
                    if typeof(Properties) == 'table' then
                        for Property, Value in pairs(Properties) do
                            local CanSet = true;

                            if self.Type == 'Image' and not IsSynapse and Property == 'Size' and typeof(Value) == 'Vector2' then
                                CanSet = false;

                                spawn(function()
                                    repeat wait() until Object.Loaded;
                                    if not self.DefaultSize then rawset(self, 'DefaultSize', Object.Size) end

                                    Property = 'ScaleFactor';
                                    Value = Value.X / self.DefaultSize.X;

                                    Object[Property] = Value
                                end)
                            end
                            
                            if CanSet then Object[Property] = Value end
                        end
                    end

                    return Object;
                end
            });

            Object.Visible = true;
            Object.Transparency = 1; -- Transparency is really Opacity with drawing api (1 being visible, 0 being invisible)
            
            if Type == 'Text' then
                if Drawing.Fonts then Object.Font = Drawing.Fonts.Monospace end
                Object.Size = 20;
                Object.Color = Color3.new(1, 1, 1);
                Object.Center = true;
				Object.Outline = true;
				OutlineOpacity = 0.5;
            elseif Type == 'Square' or Type == 'Rectangle' then
                Object.Thickness = 2;
                Object.Filled = false;
            end

            return self.__Objects[Index];
        end

        return Object;
    end

    function Metatable.__call(self, Delete, ...)
        local Arguments = {Delete, ...};
        
        if Delete == false then
            for Index, Drawing in pairs(rawget(self, '__Objects')) do
                Drawing(false);
            end
        end
    end

    return setmetatable(Drawings, Metatable);
end

local Images = {};

spawn(function()
	Images.Ring = 'https://i.imgur.com/q4qx26f.png';
	Images.Overlay = 'https://i.imgur.com/gOCxbsR.png';
end)

function ColorPicker.new(Position, Size, Color)
	ColorPicker.LastGenerated = tick();
	ColorPicker.Loading = true;

    local Picker = { Color = Color or Color3.new(1, 1, 1); HSV = { H = 0, S = 1, V = 1 } };
    local Drawings = CreateDrawingsTable();
    local Position = Position or V2New();
    local Size = Size or 150;
    local Padding = { 10, 10, 10, 10 };
    
    Picker.ColorChanged = Signal.new();

    local Background = Drawings['Square-Background'] {
        Color = Color3.fromRGB(33, 33, 33);
		Filled = false;
		Visible = false;
        Position = Position - V2New(Padding[4], Padding[1]);
        Size = V2New(Size, Size) + V2New(Padding[4] + Padding[2], Padding[1] + Padding[3]);
    };
    local ColorPreview = Drawings['Circle-Preview'] {
        Position = Position + (V2New(Size, Size) / 2);
        Radius = Size / 2 - 8;
        Filled = true;
        Thickness = 0;
        NumSides = 20;
        Color = Color3.new(1, 0, 0);
    };
    local Main = Drawings['Image-Main'] {
        Position = Position;
        Size = V2New(Size, Size);
    }; SetImage(Main, Images.Ring);
    local Preview = Drawings['Square-Preview'] {
        Position = Main.Position + (Main.Size / 4.5);
        Size = Main.Size / 1.75;
        Color = Color3.new(1, 0, 0);
        Filled = true;
        Thickness = 0;
    };
    local Overlay = Drawings['Image-Overlay'] {
        Position = Preview.Position;
        Size = Preview.Size;
        Transparency = 1;
    }; SetImage(Overlay, Images.Overlay);
    local CursorOutline = Drawings['Circle-CursorOutline'] {
        Radius = 4;
        Thickness = 2;
        Filled = false;
        Color = Color3.new(0.2, 0.2, 0.2);
        Position = V2New(Main.Position.X + Main.Size.X - 10, Main.Position.Y + (Main.Size.Y / 2));
    };
    local Cursor = Drawings['Circle-Cursor'] {
        Radius = 3;
        Transparency = 1;
        Filled = true;
        Color = Color3.new(1, 1, 1);
        Position = CursorOutline.Position;
    };
    local CursorOutline = Drawings['Circle-CursorOutlineSquare'] {
        Radius = 4;
        Thickness = 2;
        Filled = false;
        Color = Color3.new(0.2, 0.2, 0.2);
        Position = V2New(Preview.Position.X + Preview.Size.X - 2, Preview.Position.Y + 2);
    };
    Drawings['Circle-CursorSquare'] {
        Radius = 3;
        Transparency = 1;
        Filled = true;
        Color = Color3.new(1, 1, 1);
        Position = CursorOutline.Position;
    };
    
    function Picker:UpdatePosition(Input)
        local MousePosition = V2New(Input.Position.X, Input.Position.Y + 33);

        if self.MouseHeld then
            if self.Item == 'Ring' then
                local Main = self.Drawings['Image-Main'] ();
                local Preview = self.Drawings['Square-Preview'] ();
                local Bounds = Main.Size / 2;
                local Center = Main.Position + Bounds;
                local Relative = MousePosition - Center;
                local Direction = Relative.unit;
                local Position = Center + Direction * Main.Size.X / 2.15;
                local H = (math.atan2(Position.Y - Center.Y, Position.X - Center.X)) * 60;
                if H < 0 then H = 360 + H; end
                H = H / 360;
                self.HSV.H = H;
                local EndColor = Color3.fromHSV(H, self.HSV.S, self.HSV.V); if EndColor ~= self.Color then self.ColorChanged:Fire(self.Color); end
                local Pointer = self.Drawings['Circle-Cursor'] { Position = Position };
                self.Drawings['Circle-CursorOutline'] { Position = Pointer.Position };
                Bounds = Bounds * 2;
                Preview.Color = Color3.fromHSV(H, 1, 1);
                self.Color = EndColor;
                self.Drawings['Circle-Preview'] { Color = EndColor };
            elseif self.Item == 'HL' then
                local Preview = self.Drawings['Square-Preview'] ();
                local HSV = self.HSV;
                local Position = V2New(math.clamp(MousePosition.X, Preview.Position.X, Preview.Position.X + Preview.Size.X), math.clamp(MousePosition.Y, Preview.Position.Y, Preview.Position.Y + Preview.Size.Y));
                HSV.S = (Position.X - Preview.Position.X) / Preview.Size.X;
                HSV.V = 1 - (Position.Y - Preview.Position.Y) / Preview.Size.Y;
                local EndColor = Color3.fromHSV(HSV.H, HSV.S, HSV.V); if EndColor ~= self.Color then self.ColorChanged:Fire(self.Color); end
                self.Color = EndColor;
                self.Drawings['Circle-Preview'] { Color = EndColor };
                local Pointer = self.Drawings['Circle-CursorSquare'] { Position = Position };
                self.Drawings['Circle-CursorOutlineSquare'] { Position = Pointer.Position };
            end
        end
    end

    function Picker:HandleInput(Input, P, Type)
        if Type == 'Began' then
            if Input.UserInputType.Name == 'MouseButton1' then
                local Main = self.Drawings['Image-Main'] ();
                local SquareSV = self.Drawings['Square-Preview'] ();
                local MousePosition = V2New(Input.Position.X, Input.Position.Y + 33);
                self.MouseHeld = true;
                local Bounds = Main.Size / 2;
                local Center = Main.Position + Bounds;
                local R = (MousePosition - Center);
        
                if R.Magnitude < Bounds.X and R.Magnitude > Bounds.X - 20 then
                    self.Item = 'Ring';
                end
                
                if MousePosition.X > SquareSV.Position.X and MousePosition.Y > SquareSV.Position.Y and MousePosition.X < SquareSV.Position.X + SquareSV.Size.X and MousePosition.Y < SquareSV.Position.Y + SquareSV.Size.Y then
                    self.Item = 'HL';
                end

                self:UpdatePosition(Input, P);
            end
        elseif Type == 'Changed' then
            if Input.UserInputType.Name == 'MouseMovement' then
                self:UpdatePosition(Input, P);
            end
        elseif Type == 'Ended' and Input.UserInputType.Name == 'MouseButton1' then
            self.Item = nil;
        end
	end
	
	function Picker:Dispose()
		self.Drawings(false);
		self.UpdatePosition = nil;
		self.HandleInput = nil;
		Connections:DisconnectAll(); -- scuffed tbh
	end

	Connections:Listen(UserInputService.InputBegan, function(Input, Process)
		Picker:HandleInput(Input, Process, 'Began');
	end);
	Connections:Listen(UserInputService.InputChanged, function(Input, Process)
		if Input.UserInputType.Name == 'MouseMovement' then
			local MousePosition = V2New(Input.Position.X, Input.Position.Y + 33);
			local Cursor = Picker.Drawings['Triangle-Cursor'] {
				Filled = true;
				Color = Color3.new(0.9, 0.9, 0.9);
				PointA = MousePosition + V2New(0, 0);
				PointB = MousePosition + V2New(12, 14);
				PointC = MousePosition + V2New(0, 18);
				Thickness = 0;
			};
		end
		Picker:HandleInput(Input, Process, 'Changed');
	end);
	Connections:Listen(UserInputService.InputEnded, function(Input, Process)
		Picker:HandleInput(Input, Process, 'Ended');
		
		if Input.UserInputType.Name == 'MouseButton1' then
			Picker.MouseHeld = false;
		end
	end);

	ColorPicker.Loading = false;

    Picker.Drawings = Drawings;
    return Picker;
end

function SubMenu:Show(Position, Title, Options)
	self.Open = true;

	local Visible = true;
	local BasePosition = Position;
	local BaseSize = V2New(200, 140);
	local End = BasePosition + BaseSize;

	self.Bounds = { BasePosition.X, BasePosition.Y, End.X, End.Y };

	delay(0.025, function()
		if not self.Open then return; end

		Menu:AddMenuInstance('Sub-Main', 'Square', {
			Size		= BaseSize;
			Position	= BasePosition;
			Filled		= false;
			Color		= Colors.Primary.Main;
			Thickness	= 3;
			Visible		= Visible;
		});
	end);
	Menu:AddMenuInstance('Sub-TopBar', 'Square', {
		Position	= BasePosition;
		Size		= V2New(BaseSize.X, 10);
		Color		= Colors.Primary.Dark;
		Filled		= true;
		Visible		= Visible;
	});
	Menu:AddMenuInstance('Sub-TopBarTwo', 'Square', {
		Position 	= BasePosition + V2New(0, 10);
		Size		= V2New(BaseSize.X, 20);
		Color		= Colors.Primary.Main;
		Filled		= true;
		Visible		= Visible;
	});
	Menu:AddMenuInstance('Sub-TopBarText', 'Text', {
		Size 		= 20;
		Position	= shared.MenuDrawingData.Instances['Sub-TopBarTwo'].Position + V2New(15, -3);
		Text		= Title or '';
		Color		= Colors.Secondary.Light;
		Visible		= Visible;
	});
	Menu:AddMenuInstance('Sub-Filling', 'Square', {
		Size		= BaseSize - V2New(0, 30);
		Position	= BasePosition + V2New(0, 30);
		Filled		= true;
		Color		= Colors.Secondary.Main;
		Transparency= .75;
		Visible		= Visible;
	});

	if Options then
		for Index, Option in pairs(Options) do -- currently only supports color and button(but color is a button so), planning on fully rewriting or something
			local function GetName(Name) return ('Sub-%s.%d'):format(Name, Index) end
			local Position = shared.MenuDrawingData.Instances['Sub-Filling'].Position + V2New(20, Index * 25 - 10);
			-- local BasePosition	= shared.MenuDrawingData.Instances.Filling.Position + V2New(30, v.Index * 25 - 10);

			if Option.Type == 'Color' then
				local ColorPreview = Menu:AddMenuInstance(GetName'ColorPreview', 'Circle', {
					Position = Position;
					Color = Option.Color;
					Radius = IsSynapse and 10 or 10;
					NumSides = 10;
					Filled = true;
					Visible = true;
				});
				local Text = Menu:AddMenuInstance(GetName'Text', 'Text', {
					Text = Option.Text;
					Position = ColorPreview.Position + V2New(15, -8);
					Size = 16;
					Color = Colors.Primary.Dark;
					Visible = true;
				});
				UIButtons[#UIButtons + 1] = {
					FromSubMenu = true;
					Option = function() return Option.Function(ColorPreview, BasePosition + V2New(BaseSize.X, 0)) end;
					Instance = Menu:AddMenuInstance(Format('%s_Hitbox', GetName'Button'), 'Square', {
						Position	= Position - V2New(20, 12);
						Size		= V2New(BaseSize.X, 25);
						Visible		= false;
					});
				};
			elseif Option.Type == 'Button' then
				UIButtons[#UIButtons + 1] = {
					FromSubMenu = true;
					Option = Option.Function;
					Instance = Menu:AddMenuInstance(Format('%s_Hitbox', GetName'Button'), 'Square', {
						Size		= V2New(BaseSize.X, 20) - V2New(20, 0);
						Visible		= true;
						Transparency= .5;
						Position	= Position - V2New(10, 10);
						Color		= Colors.Secondary.Light;
						Filled		= true;
					});
				};
				local Text		= Menu:AddMenuInstance(Format('%s_Text', GetName'Text'), 'Text', {
					Text		= Option.Text;
					Size		= 18;
					Position	= Position + V2New(5, -10);
					Visible		= true;
					Color		= Colors.Primary.Dark;
				});
			end
		end
	end
end

function SubMenu:Hide()
	self.Open = false;

	for i, v in pairs(shared.MenuDrawingData.Instances) do
		if i:sub(1, 3) == 'Sub' then
			v.Visible = false;

			if i:sub(4, 4) == ':' then -- ';' = Temporary so remove
				v:Remove();
				shared.MenuDrawingData.Instance[i] = nil;
			end
		end
	end

	for i, Button in pairs(UIButtons) do
		if Button.FromSubMenu then
			UIButtons[i] = nil;
		end
	end

	spawn(function() -- stupid bug happens if i dont use this
		for i = 1, 10 do
			if shared.CurrentColorPicker then -- dont know why 'CurrentColorPicker' isnt a variable in this
				shared.CurrentColorPicker:Dispose();
			end
			wait(0.1);
		end
	end)

	CurrentColorPicker = nil;
end

function CreateMenu(NewPosition) -- Create Menu
	MenuLoaded = false;
	UIButtons  = {};
	Sliders	   = {};

	local BaseSize = V2New(300, 625);
	local BasePosition = NewPosition or V2New(Camera.ViewportSize.X / 8 - (BaseSize.X / 2), Camera.ViewportSize.Y / 2 - (BaseSize.Y / 2));

	BasePosition = V2New(math.clamp(BasePosition.X, 0, Camera.ViewportSize.X), math.clamp(BasePosition.Y, 0, Camera.ViewportSize.Y));

	Menu:AddMenuInstance('CrosshairX', 'Line', {
		Visible			= false;
		Color			= Color3.new(0, 1, 0);
		Transparency	= 1;
		Thickness		= 1;
	});
	Menu:AddMenuInstance('CrosshairY', 'Line', {
		Visible			= false;
		Color			= Color3.new(0, 1, 0);
		Transparency	= 1;
		Thickness		= 1;
	});

	delay(.025, function() -- since zindex doesnt exist
		Menu:AddMenuInstance('Main', 'Square', {
			Size		= BaseSize;
			Position	= BasePosition;
			Filled		= false;
			Color		= Colors.Primary.Main;
			Thickness	= 3;
			Visible		= true;
		});
	end);
	Menu:AddMenuInstance('TopBar', 'Square', {
		Position	= BasePosition;
		Size		= V2New(BaseSize.X, 15);
		Color		= Colors.Primary.Dark;
		Filled		= true;
		Visible		= true;
	});
	Menu:AddMenuInstance('TopBarTwo', 'Square', {
		Position 	= BasePosition + V2New(0, 15);
		Size		= V2New(BaseSize.X, 45);
		Color		= Colors.Primary.Main;
		Filled		= true;
		Visible		= true;
	});
	Menu:AddMenuInstance('TopBarText', 'Text', {
		Size 		= 25;
		Position	= shared.MenuDrawingData.Instances.TopBarTwo.Position + V2New(25, 10);
		Text		= 'Unnamed ESP';
		Color		= Colors.Secondary.Light;
		Visible		= true;
		Transparency= 1; -- proto outline fix
		Outline 	= true;
		OutlineOpacity = 0.5;
	});
	Menu:AddMenuInstance('TopBarTextBR', 'Text', {
		Size 		= 18;
		Position	= shared.MenuDrawingData.Instances.TopBarTwo.Position + V2New(BaseSize.X - 75, 25);
		Text		= 'by ic3w0lf';
		Color		= Colors.Secondary.Light;
		Visible		= true;
		Transparency= 1;
		Outline 	= true;
		OutlineOpacity = 0.5;
	});
	Menu:AddMenuInstance('Filling', 'Square', {
		Size		= BaseSize - V2New(0, 60);
		Position	= BasePosition + V2New(0, 60);
		Filled		= true;
		Color		= Colors.Secondary.Main;
		Transparency= .5;
		Visible		= true;
	});

	local CPos = 0;

	GetTableData(Options)(function(i, v)
		if typeof(v.Value) == 'boolean' and not IsStringEmpty(v.Text) and v.Text ~= nil then
			CPos 				= CPos + 25;
			local BaseSize		= V2New(BaseSize.X, 30);
			local BasePosition	= shared.MenuDrawingData.Instances.Filling.Position + V2New(30, v.Index * 25 - 10);
			UIButtons[#UIButtons + 1] = {
				Option = v;
				Instance = Menu:AddMenuInstance(Format('%s_Hitbox', v.Name), 'Square', {
					Position	= BasePosition - V2New(30, 15);
					Size		= BaseSize;
					Visible		= false;
				});
			};
			Menu:AddMenuInstance(Format('%s_OuterCircle', v.Name), 'Circle', {
				Radius		= 10;
				Position	= BasePosition;
				Color		= Colors.Secondary.Light;
				Filled		= true;
				Visible		= true;
			});
			Menu:AddMenuInstance(Format('%s_InnerCircle', v.Name), 'Circle', {
				Radius		= 7;
				Position	= BasePosition;
				Color		= Colors.Secondary.Dark;
				Filled		= true;
				Visible		= v.Value;
			});
			Menu:AddMenuInstance(Format('%s_Text', v.Name), 'Text', {
				Text		= v.Text;
				Size		= 20;
				Position	= BasePosition + V2New(20, -10);
				Visible		= true;
				Color		= Colors.Secondary.Light;
				Transparency= 1;
				Outline		= true;
				OutlineOpacity = 0.5;
			});
		end
	end)
	GetTableData(Options)(function(i, v) -- just to make sure certain things are drawn before or after others, too lazy to actually sort table
		if typeof(v.Value) == 'number' then
			CPos 				= CPos + 25;

			local BaseSize		= V2New(BaseSize.X, 30);
			local BasePosition	= shared.MenuDrawingData.Instances.Filling.Position + V2New(0, CPos - 10);

			local Line			= Menu:AddMenuInstance(Format('%s_SliderLine', v.Name), 'Square', {
				Transparency	= 1;
				Color			= Colors.Secondary.Light;
				-- Thickness		= 3;
				Filled			= true;
				Visible			= true;
				Position 		= BasePosition + V2New(15, -5);
				Size 			= BaseSize - V2New(30, 10);
				Transparency	= 0.5;
			});
			local Slider		= Menu:AddMenuInstance(Format('%s_Slider', v.Name), 'Square', {
				Visible			= true;
				Filled			= true;
				Color			= Colors.Primary.Dark;
				Size			= V2New(5, Line.Size.Y);
				Transparency	= 0.5;
			});
			local Text			= Menu:AddMenuInstance(Format('%s_Text', v.Name), 'Text', {
				Text			= v.Text;
				Size			= 20;
				Center			= true;
				Transparency	= 1;
				Outline			= true;
				OutlineOpacity  = 0.5;
				Visible			= true;
				Color			= Colors.White;
			}); Text.Position	= Line.Position + (Line.Size / 2) - V2New(0, Text.TextBounds.Y / 1.75);
			local AMT			= Menu:AddMenuInstance(Format('%s_AmountText', v.Name), 'Text', {
				Text			= tostring(v.Value);
				Size			= 22;
				Center			= true;
				Transparency	= 1;
				Outline			= true;
				OutlineOpacity  = 0.5;
				Visible			= true;
				Color			= Colors.White;
				Position		= Text.Position;
			});

			local CSlider = {Slider = Slider; Line = Line; Min = v.AllArgs[4]; Max = v.AllArgs[5]; Option = v};
			local Dummy = Instance.new'NumberValue';

			Dummy:GetPropertyChangedSignal'Value':Connect(function()
				Text.Transparency = Dummy.Value;
				-- Text.OutlineTransparency = 1 - Dummy.Value;
				AMT.Transparency = 1 - Dummy.Value;
			end);

			Dummy.Value = 1;

			function CSlider:ShowValue(Bool)
				self.ShowingValue = Bool;

				TweenService:Create(Dummy, TweenInfo.new(0.5, Enum.EasingStyle.Quart, Enum.EasingDirection.Out), { Value = Bool and 0 or 1 }):Play();
			end

			Sliders[#Sliders + 1] = CSlider;

			-- local Percent = (v.Value / CSlider.Max) * 100;
			-- local Size = math.abs(Line.From.X - Line.To.X);
			-- local Value = Size * (Percent / 100); -- this shit's inaccurate but fuck it i'm not even gonna bother fixing it

			Slider.Position = Line.Position + V2New(35, 0);
			
			v.BaseSize = BaseSize;
			v.BasePosition = BasePosition;
			-- AMT.Position = BasePosition + V2New(BaseSize.X - AMT.TextBounds.X - 10, -10)
		end
	end)
	local FirstItem = false;
	GetTableData(Options)(function(i, v) -- just to make sure certain things are drawn before or after others, too lazy to actually sort table
		if typeof(v.Value) == 'EnumItem' then
			CPos 				= CPos + (not FirstItem and 30 or 25);
			FirstItem			= true;

			local BaseSize		= V2New(BaseSize.X, FirstItem and 30 or 25);
			local BasePosition	= shared.MenuDrawingData.Instances.Filling.Position + V2New(0, CPos - 10);

			UIButtons[#UIButtons + 1] = {
				Option = v;
				Instance = Menu:AddMenuInstance(Format('%s_Hitbox', v.Name), 'Square', {
					Size		= V2New(BaseSize.X, 20) - V2New(30, 0);
					Visible		= true;
					Transparency= .5;
					Position	= BasePosition + V2New(15, -10);
					Color		= Colors.Secondary.Light;
					Filled		= true;
				});
			};
			local Text		= Menu:AddMenuInstance(Format('%s_Text', v.Name), 'Text', {
				Text		= v.Text;
				Size		= 20;
				Position	= BasePosition + V2New(20, -10);
				Visible		= true;
				Color		= Colors.Secondary.Light;
				Transparency= 1;
				Outline		= true;
				OutlineOpacity = 0.5;
			});
			local BindText	= Menu:AddMenuInstance(Format('%s_BindText', v.Name), 'Text', {
				Text		= tostring(v.Value):match'%w+%.%w+%.(.+)';
				Size		= 20;
				Position	= BasePosition;
				Visible		= true;
				Color		= Colors.Secondary.Light;
				Transparency= 1;
				Outline		= true;
				OutlineOpacity = 0.5;
			});

			Options[i].BaseSize = BaseSize;
			Options[i].BasePosition = BasePosition;
			BindText.Position = BasePosition + V2New(BaseSize.X - BindText.TextBounds.X - 20, -10);
		end
	end)
	GetTableData(Options)(function(i, v) -- just to make sure certain things are drawn before or after others, too lazy to actually sort table
		if typeof(v.Value) == 'function' then
			local BaseSize		= V2New(BaseSize.X, 30);
			local BasePosition	= shared.MenuDrawingData.Instances.Filling.Position + V2New(0, CPos + (25 * v.AllArgs[4]) - 35);

			UIButtons[#UIButtons + 1] = {
				Option = v;
				Instance = Menu:AddMenuInstance(Format('%s_Hitbox', v.Name), 'Square', {
					Size		= V2New(BaseSize.X, 20) - V2New(30, 0);
					Visible		= true;
					Transparency= .5;
					Position	= BasePosition + V2New(15, -10);
					Color		= Colors.Secondary.Light;
					Filled		= true;
				});
			};
			local Text		= Menu:AddMenuInstance(Format('%s_Text', v.Name), 'Text', {
				Text		= v.Text;
				Size		= 20;
				Position	= BasePosition + V2New(20, -10);
				Visible		= true;
				Color		= Colors.Secondary.Light;
				Transparency= 1;
				Outline		= true;
				OutlineOpacity = 0.5;
			});

			-- BindText.Position = BasePosition + V2New(BaseSize.X - BindText.TextBounds.X - 10, -10);
		end
	end)

	delay(.1, function()
		MenuLoaded = true;
	end);

	-- this has to be at the bottom cuz proto drawing api doesnt have zindex :triumph:	
	Menu:AddMenuInstance('Cursor1', 'Line', {
		Visible			= false;
		Color			= Color3.new(1, 0, 0);
		Transparency	= 1;
		Thickness		= 2;
	});
	Menu:AddMenuInstance('Cursor2', 'Line', {
		Visible			= false;
		Color			= Color3.new(1, 0, 0);
		Transparency	= 1;
		Thickness		= 2;
	});
	Menu:AddMenuInstance('Cursor3', 'Line', {
		Visible			= false;
		Color			= Color3.new(1, 0, 0);
		Transparency	= 1;
		Thickness		= 2;
	});
end

CreateMenu();
delay(0.1, function()
	SubMenu:Show(V2New()); -- Create the submenu
	SubMenu:Hide();
end);

shared.UESP_InputChangedCon = UserInputService.InputChanged:Connect(function(input)
	if input.UserInputType.Name == 'MouseMovement' and Options.MenuOpen.Value then
		for i, v in pairs(Sliders) do
			local Values = {
				v.Line.Position.X;
				v.Line.Position.Y;
				v.Line.Position.X + v.Line.Size.X;
				v.Line.Position.Y + v.Line.Size.Y;
			};
			if MouseHoveringOver(Values) then
				v:ShowValue(true);
			else
				if not MouseHeld then v:ShowValue(false); end
			end
		end
	end
end)
shared.UESP_InputBeganCon = UserInputService.InputBegan:Connect(function(input)
	if input.UserInputType.Name == 'MouseButton1' and Options.MenuOpen.Value then
		MouseHeld = true;
		local Bar = Menu:GetInstance'TopBar';
		local Values = {
			Bar.Position.X;
			Bar.Position.Y;
			Bar.Position.X + Bar.Size.X;
			Bar.Position.Y + Bar.Size.Y;
		}
		if MouseHoveringOver(Values) then
			DraggingUI = true;
			DragOffset = Menu:GetInstance'Main'.Position - GetMouseLocation();
		else
			for i, v in pairs(Sliders) do
				local Values = {
					v.Line.Position.X;
					v.Line.Position.Y;
					v.Line.Position.X + v.Line.Size.X;
					v.Line.Position.Y + v.Line.Size.Y;
					-- v.Line.From.X	- (v.Slider.Radius);
					-- v.Line.From.Y	- (v.Slider.Radius);
					-- v.Line.To.X		+ (v.Slider.Radius);
					-- v.Line.To.Y		+ (v.Slider.Radius);
				};
				if MouseHoveringOver(Values) then
					DraggingWhat = v;
					Dragging = true;
					break
				end
			end

			if not Dragging then
				local Values = {
					TracerPosition.X - 10;
					TracerPosition.Y - 10;
					TracerPosition.X + 10;
					TracerPosition.Y + 10;
				};
				if MouseHoveringOver(Values) then
					DragTracerPosition = true;
				end
			end
		end
	end
end)
shared.UESP_InputEndedCon = UserInputService.InputEnded:Connect(function(input)
	if input.UserInputType.Name == 'MouseButton1' and Options.MenuOpen.Value then
		MouseHeld = false;
		DragTracerPosition = false;
		local IgnoreOtherInput = false;

		if SubMenu.Open and not MouseHoveringOver(SubMenu.Bounds) then
			if CurrentColorPicker and IsMouseOverDrawing(CurrentColorPicker.Drawings['Square-Background']()) then IgnoreOtherInput = true; end
			if not IgnoreOtherInput then SubMenu:Hide() end
		end

		if not IgnoreOtherInput then
			for i, v in pairs(UIButtons) do
				if SubMenu.Open and MouseHoveringOver(SubMenu.Bounds) and not v.FromSubMenu then continue end

				local Values = {
					v.Instance.Position.X;
					v.Instance.Position.Y;
					v.Instance.Position.X + v.Instance.Size.X;
					v.Instance.Position.Y + v.Instance.Size.Y;
				};
				if MouseHoveringOver(Values) then
					v.Option();
					IgnoreOtherInput = true;
					break -- prevent clicking 2 options
				end
			end
			for i, v in pairs(Sliders) do
				if IgnoreOtherInput then break end

				local Values = {
					v.Line.Position.X;
					v.Line.Position.Y;
					v.Line.Position.X + v.Line.Size.X;
					v.Line.Position.Y + v.Line.Size.Y;
				};
				if not MouseHoveringOver(Values) then
					v:ShowValue(false);
				end
			end
		end
	elseif input.UserInputType.Name == 'MouseButton2' and Options.MenuOpen.Value and not DragTracerPosition then
		local Values = {
			TracerPosition.X - 10;
			TracerPosition.Y - 10;
			TracerPosition.X + 10;
			TracerPosition.Y + 10;
		}
		if MouseHoveringOver(Values) then
			DragTracerPosition = false;
			TracerPosition = V2New(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y - 135);
		end
	elseif input.UserInputType.Name == 'Keyboard' then
		if Binding then
			BindedKey = input.KeyCode;
			Binding = false;
		elseif input.KeyCode == Options.MenuKey.Value or (input.KeyCode == Enum.KeyCode.Home and UserInputService:IsKeyDown(Enum.KeyCode.LeftControl)) then
			Options.MenuOpen();
		elseif input.KeyCode == Options.ToggleKey.Value then
			Options.Enabled();
		elseif input.KeyCode.Name == 'F1' and UserInputService:IsMouseButtonPressed(1) and shared.am_ic3 then -- hehe hiden spectate feature cuz why not
			local HD, LPlayer, LCharacter = 0.95;

			for i, Player in pairs(Players:GetPlayers()) do
				local Character = GetCharacter(Player);

				if Player ~= LocalPlayer and Player ~= Spectating and Character and Character:FindFirstChild'HumanoidRootPart' then
					local Head = Character:FindFirstChild'Head';
					local Humanoid = Character:FindFirstChildOfClass'Humanoid';
					
					if Head then
						local Distance  = (Camera.CFrame.Position - Head.Position).Magnitude;
						
						if Distance > Options.MaxDistance.Value then continue; end

						local Direction = -(Camera.CFrame.Position - Mouse.Hit.Position).unit;
						local Relative  = Character.Head.Position - Camera.CFrame.Position;
						local Unit      = Relative.unit;

						local DP = Direction:Dot(Unit);

						if DP > HD then
							HD = DP;
							LPlayer = Player;
							LCharacter = Character;
						end
					end
				end
			end
			
			if LPlayer and LPlayer ~= Spectating and LCharacter then
				Camera.CameraSubject = LCharacter.Head;
				Spectating = LPlayer;
			else
				if LocalPlayer.Character and LocalPlayer.Character:FindFirstChildOfClass'Humanoid' then
					Camera.CameraSubject = LocalPlayer.Character:FindFirstChildOfClass'Humanoid';
					Spectating = nil;
				end
			end
		end
	end
end)

local function CameraCon() -- unnamed esp v1 sucks
	workspace.CurrentCamera:GetPropertyChangedSignal'ViewportSize':Connect(function()
		TracerPosition = V2New(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y - 135);
	end);
end

CameraCon();

local function ToggleMenu()
	if Options.MenuOpen.Value then
		-- GUIService:SetMenuIsOpen(true);
		GetTableData(shared.MenuDrawingData.Instances)(function(i, v)
			if OldData[v] then
				pcall(Set, v, 'Visible', true);
			end
		end)
	else
		-- GUIService:SetMenuIsOpen(false);
		GetTableData(shared.MenuDrawingData.Instances)(function(i, v)
			OldData[v] = v.Visible;
			if v.Visible then
				pcall(Set, v, 'Visible', false);
			end
		end)
	end
end

local function CheckRay(Instance, Distance, Position, Unit)
	local Pass = true;
	local Model = Instance;

	if Distance > 999 then return false; end

	if Instance.ClassName == 'Player' then
		Model = GetCharacter(Instance);
	end

	if not Model then
		Model = Instance.Parent;

		if Model.Parent == workspace then
			Model = Instance;
		end
	end

	if not Model then return false end

	local _Ray = Ray.new(Position, Unit * Distance);
	
	local List = {LocalPlayer.Character, Camera, Mouse.TargetFilter};

	for i,v in pairs(IgnoreList) do table.insert(List, v); end;

	local Hit = workspace:FindPartOnRayWithIgnoreList(_Ray, List);

	if Hit and not Hit:IsDescendantOf(Model) then
		Pass = false;
		if Hit.Transparency >= .3 or not Hit.CanCollide and Hit.ClassName ~= Terrain then -- Detect invisible walls
			IgnoreList[#IgnoreList + 1] = Hit;
		end
	end

	return Pass;
end

local function CheckTeam(Player)
	if Player.Neutral and LocalPlayer.Neutral then return true; end
	return Player.TeamColor == LocalPlayer.TeamColor;
end

local CustomTeam = CustomTeams[game.PlaceId];

if CustomTeam ~= nil then
	if CustomTeam.Initialize then ypcall(CustomTeam.Initialize) end

	CheckTeam = CustomTeam.CheckTeam;
end

local function CheckPlayer(Player, Character)
	if not Options.Enabled.Value then return false end

	local Pass = true;
	local Distance = 0;

	if Player ~= LocalPlayer and Character then
		if not Options.ShowTeam.Value and CheckTeam(Player) then
			Pass = false;
		end

		local Head = Character:FindFirstChild'Head';

		if Pass and Character and Head then
			Distance = (Camera.CFrame.Position - Head.Position).Magnitude;
			if Options.VisCheck.Value then
				Pass = CheckRay(Player, Distance, Camera.CFrame.Position, (Head.Position - Camera.CFrame.Position).unit);
			end
			if Distance > Options.MaxDistance.Value then
				Pass = false;
			end
		end
	else
		Pass = false;
	end

	return Pass, Distance;
end

local function CheckDistance(Instance)
	if not Options.Enabled.Value then return false end

	local Pass = true;
	local Distance = 0;

	if Instance ~= nil then
		Distance = (Camera.CFrame.Position - Instance.Position).Magnitude;
		if Options.VisCheck.Value then
			Pass = CheckRay(Instance, Distance, Camera.CFrame.Position, (Instance.Position - Camera.CFrame.Position).unit);
		end
		if Distance > Options.MaxDistance.Value then
			Pass = false;
		end
	else
		Pass = false;
	end

	return Pass, Distance;
end

local function UpdatePlayerData()
	if (tick() - LastRefresh) > (Options.RefreshRate.Value / 1000) then
		LastRefresh = tick();
		if CustomESP and Options.Enabled.Value then
			local a, b = pcall(CustomESP);
		end
		for i, v in pairs(RenderList.Instances) do
			if v.Instance ~= nil and v.Instance.Parent ~= nil and v.Instance:IsA'BasePart' then
				local Data = shared.InstanceData[v.Instance:GetDebugId()] or { Instances = {}; DontDelete = true };

				Data.Instance = v.Instance;

				Data.Instances['OutlineTracer'] = Data.Instances['OutlineTracer'] or NewDrawing'Line'{
					Transparency	= 0.75;
					Thickness		= 5;
					Color 			= Color3.new(0.1, 0.1, 0.1);
				}
				Data.Instances['Tracer'] = Data.Instances['Tracer'] or NewDrawing'Line'{
					Transparency	= 1;
					Thickness		= 2;
				}
				Data.Instances['NameTag'] = Data.Instances['NameTag'] or NewDrawing'Text'{
					Size			= Options.TextSize.Value;
					Center			= true;
					Outline			= Options.TextOutline.Value;
					Visible			= true;
				};
				Data.Instances['DistanceTag'] = Data.Instances['DistanceTag'] or NewDrawing'Text'{
					Size			= Options.TextSize.Value - 1;
					Center			= true;
					Outline			= Options.TextOutline.Value;
					Visible			= true;
				};

				local NameTag		= Data.Instances['NameTag'];
				local DistanceTag	= Data.Instances['DistanceTag'];
				local Tracer		= Data.Instances['Tracer'];
				local OutlineTracer	= Data.Instances['OutlineTracer'];

				local Pass, Distance = CheckDistance(v.Instance);

				if Pass then
					local ScreenPosition, Vis = WorldToViewport(v.Instance.Position);
					local Color = v.Color;
					local OPos = Camera.CFrame:pointToObjectSpace(v.Instance.Position);
					
					if ScreenPosition.Z < 0 then
						local AT = math.atan2(OPos.Y, OPos.X) + math.pi;
						OPos = CFrame.Angles(0, 0, AT):vectorToWorldSpace((CFrame.Angles(0, math.rad(89.9), 0):vectorToWorldSpace(V3New(0, 0, -1))));
					end
					
					local Position = WorldToViewport(Camera.CFrame:pointToWorldSpace(OPos));

					if Options.ShowTracers.Value then
						Tracer.Transparency = math.clamp(Distance / 200, 0.45, 0.8);
						Tracer.Visible	= true;
						Tracer.From		= TracerPosition;
						Tracer.To		= V2New(Position.X, Position.Y);
						Tracer.Color	= Color;
						OutlineTracer.Visible = true;
						OutlineTracer.Transparency = Tracer.Transparency - 0.1;
						OutlineTracer.From = Tracer.From;
						OutlineTracer.To = Tracer.To;
						OutlineTracer.Color	= Color3.new(0.1, 0.1, 0.1);
					else
						Tracer.Visible = false;
						OutlineTracer.Visible = false;
					end

					if ScreenPosition.Z > 0 then
						local ScreenPositionUpper = ScreenPosition;
						
						if Options.ShowName.Value then
							LocalPlayer.NameDisplayDistance = 0;
							NameTag.Visible		= true;
							NameTag.Text		= v.Text;
							NameTag.Size		= Options.TextSize.Value;
							NameTag.Outline		= Options.TextOutline.Value;
							NameTag.Position	= V2New(ScreenPositionUpper.X, ScreenPositionUpper.Y);
							NameTag.Color		= Color;
							if Drawing.Fonts and shared.am_ic3 then -- CURRENTLY SYNAPSE ONLY :MEGAHOLY:
								NameTag.Font	= Drawing.Fonts.Monospace;
							end
						else
							LocalPlayer.NameDisplayDistance = 100;
							NameTag.Visible = false;
						end
						if Options.ShowDistance.Value or Options.ShowHealth.Value then
							DistanceTag.Visible		= true;
							DistanceTag.Size		= Options.TextSize.Value - 1;
							DistanceTag.Outline		= Options.TextOutline.Value;
							DistanceTag.Color		= Color3.new(1, 1, 1);
							if Drawing.Fonts and shared.am_ic3 then -- CURRENTLY SYNAPSE ONLY :MEGAHOLY:
								NameTag.Font	= Drawing.Fonts.Monospace;
							end

							local Str = '';

							if Options.ShowDistance.Value then
								Str = Str .. Format('[%d] ', Distance);
							end

							DistanceTag.Text = Str;
							DistanceTag.Position = V2New(ScreenPositionUpper.X, ScreenPositionUpper.Y) + V2New(0, NameTag.TextBounds.Y);
						else
							DistanceTag.Visible = false;
						end
					else
						NameTag.Visible			= false;
						DistanceTag.Visible		= false;
					end
				else
					NameTag.Visible			= false;
					DistanceTag.Visible		= false;
					Tracer.Visible			= false;
					OutlineTracer.Visible	= false;
				end

				Data.Instances['NameTag'] 		= NameTag;
				Data.Instances['DistanceTag']	= DistanceTag;
				Data.Instances['Tracer']		= Tracer;
				Data.Instances['OutlineTracer']	= OutlineTracer;

				shared.InstanceData[v.Instance:GetDebugId()] = Data;
			end
		end
		for i, v in pairs(Players:GetPlayers()) do
			local Data = shared.InstanceData[v.Name] or { Instances = {}; };

			Data.Instances['Box'] = Data.Instances['Box'] or LineBox:Create{Thickness = 4};
			Data.Instances['OutlineTracer'] = Data.Instances['OutlineTracer'] or NewDrawing'Line'{
				Transparency	= 1;
				Thickness		= 3;
				Color			= Color3.new(0.1, 0.1, 0.1);
			}
			Data.Instances['Tracer'] = Data.Instances['Tracer'] or NewDrawing'Line'{
				Transparency	= 1;
				Thickness		= 1;
			}
			Data.Instances['HeadDot'] = Data.Instances['HeadDot'] or NewDrawing'Circle'{
				Filled			= true;
				NumSides		= 30;
			}
			Data.Instances['NameTag'] = Data.Instances['NameTag'] or NewDrawing'Text'{
				Size			= Options.TextSize.Value;
				Center			= true;
				Outline			= Options.TextOutline.Value;
				OutlineOpacity	= 1;
				Visible			= true;
			};
			Data.Instances['DistanceHealthTag'] = Data.Instances['DistanceHealthTag'] or NewDrawing'Text'{
				Size			= Options.TextSize.Value - 1;
				Center			= true;
				Outline			= Options.TextOutline.Value;
				OutlineOpacity	= 1;
				Visible			= true;
			};

			local NameTag		= Data.Instances['NameTag'];
			local DistanceTag	= Data.Instances['DistanceHealthTag'];
			local Tracer		= Data.Instances['Tracer'];
			local OutlineTracer	= Data.Instances['OutlineTracer'];
			local HeadDot		= Data.Instances['HeadDot'];
			local Box			= Data.Instances['Box'];

			local Character = GetCharacter(v);
			local Pass, Distance = CheckPlayer(v, Character);

			if Pass and Character then
				local Humanoid = Character:FindFirstChildOfClass'Humanoid';
				local Head = Character:FindFirstChild'Head';
				local HumanoidRootPart = Character:FindFirstChild(CustomRootPartName or 'HumanoidRootPart')

				local Dead = (Humanoid and Humanoid:GetState().Name == 'Dead')
				if type(GetAliveState) == 'function' then
					Dead = (not GetAliveState(v, Character))
				end

				if Character ~= nil and Head and HumanoidRootPart and not Dead then
					local ScreenPosition, Vis = WorldToViewport(Head.Position);
					local Color = Rainbow and Color3.fromHSV(tick() * 128 % 255/255, 1, 1) or (CheckTeam(v) and TeamColor or EnemyColor); Color = Options.ShowTeamColor.Value and v.TeamColor.Color or Color;
					local OPos = Camera.CFrame:pointToObjectSpace(Head.Position);
					
					if ScreenPosition.Z < 0 then
						local AT = math.atan2(OPos.Y, OPos.X) + math.pi;
						OPos = CFrame.Angles(0, 0, AT):vectorToWorldSpace((CFrame.Angles(0, math.rad(89.9), 0):vectorToWorldSpace(V3New(0, 0, -1))));
					end
					
					local Position = WorldToViewport(Camera.CFrame:pointToWorldSpace(OPos));

					if Options.ShowTracers.Value then
						if TracerPosition.X >= Camera.ViewportSize.X or TracerPosition.Y >= Camera.ViewportSize.Y or TracerPosition.X < 0 or TracerPosition.Y < 0 then
							TracerPosition = V2New(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y - 135);
						end

						Tracer.Visible	= true;
						Tracer.Transparency = math.clamp(1 - (Distance / 200), 0.25, 0.75);
						Tracer.From		= TracerPosition;
						Tracer.To		= V2New(Position.X, Position.Y);
						Tracer.Color	= Color;
						OutlineTracer.From = Tracer.From;
						OutlineTracer.To = Tracer.To;
						OutlineTracer.Transparency = Tracer.Transparency - 0.15;
						OutlineTracer.Visible = true;
					else
						Tracer.Visible = false;
						OutlineTracer.Visible = false;
					end
					
					if ScreenPosition.Z > 0 then
						local ScreenPositionUpper	= WorldToViewport((HumanoidRootPart:GetRenderCFrame() * CFrame.new(0, Head.Size.Y + HumanoidRootPart.Size.Y + (Options.YOffset.Value / 25), 0)).Position);
						local Scale					= Head.Size.Y / 2;

						if Options.ShowName.Value then
							NameTag.Visible		= true;
							NameTag.Text		= v.Name .. (CustomPlayerTag and CustomPlayerTag(v) or '');
							NameTag.Size		= Options.TextSize.Value;
							NameTag.Outline		= Options.TextOutline.Value;
							NameTag.Position	= V2New(ScreenPositionUpper.X, ScreenPositionUpper.Y) - V2New(0, NameTag.TextBounds.Y);
							NameTag.Color		= Color;
							NameTag.Color		= Color;
							NameTag.OutlineColor= Color3.new(0.05, 0.05, 0.05);
							NameTag.Transparency= 0.85;
							if Drawing.Fonts and shared.am_ic3 then -- CURRENTLY SYNAPSE ONLY :MEGAHOLY:
								NameTag.Font	= Drawing.Fonts.Monospace;
							end
						else
							NameTag.Visible = false;
						end
						if Options.ShowDistance.Value or Options.ShowHealth.Value then
							DistanceTag.Visible		= true;
							DistanceTag.Size		= Options.TextSize.Value - 1;
							DistanceTag.Outline		= Options.TextOutline.Value;
							DistanceTag.Color		= Color3.new(1, 1, 1);
							DistanceTag.Transparency= 0.85;
							if Drawing.Fonts and shared.am_ic3 then -- CURRENTLY SYNAPSE ONLY :MEGAHOLY:
								NameTag.Font	= Drawing.Fonts.Monospace;
							end

							local Str = '';

							if Options.ShowDistance.Value then
								Str = Str .. Format('[%d] ', Distance);
							end
							if Options.ShowHealth.Value then								
								if typeof(Humanoid) == 'Instance' then
									Str = Str .. Format('[%d/%d] [%s%%]', Humanoid.Health, Humanoid.MaxHealth, math.floor(Humanoid.Health / Humanoid.MaxHealth * 100));
								elseif type(GetHealth) == 'function' then
									local health, maxHealth = GetHealth(v)
									
									if type(health) == 'number' and type(maxHealth) == 'number' then
										Str = Str .. Format('[%d/%d] [%s%%]', health, maxHealth, math.floor(health / maxHealth * 100))
									end
								end
							end

							DistanceTag.Text = Str;
							DistanceTag.OutlineColor = Color3.new(0.05, 0.05, 0.05);
							DistanceTag.Position = (NameTag.Visible and NameTag.Position + V2New(0, NameTag.TextBounds.Y) or V2New(ScreenPositionUpper.X, ScreenPositionUpper.Y));
						else
							DistanceTag.Visible = false;
						end
						if Options.ShowDot.Value and Vis then
							local Top			= WorldToViewport((Head.CFrame * CFrame.new(0, Scale, 0)).Position);
							local Bottom		= WorldToViewport((Head.CFrame * CFrame.new(0, -Scale, 0)).Position);
							local Radius		= (Top - Bottom).y;

							HeadDot.Visible		= true;
							HeadDot.Color		= Color;
							HeadDot.Position	= V2New(ScreenPosition.X, ScreenPosition.Y);
							HeadDot.Radius		= Radius;
						else
							HeadDot.Visible = false;
						end
						if Options.ShowBoxes.Value and Vis and HumanoidRootPart then
							local Body = {
								Head;
								Character:FindFirstChild'Left Leg' or Character:FindFirstChild'LeftLowerLeg';
								Character:FindFirstChild'Right Leg' or Character:FindFirstChild'RightLowerLeg';
								Character:FindFirstChild'Left Arm' or Character:FindFirstChild'LeftLowerArm';
								Character:FindFirstChild'Right Arm' or Character:FindFirstChild'RightLowerArm';
							}
							Box:Update(HumanoidRootPart.CFrame, V3New(2, 3, 1) * (Scale * 2), Color, nil, shared.am_ic3 and Body);
						else
							Box:SetVisible(false);
						end
					else
						NameTag.Visible			= false;
						DistanceTag.Visible		= false;
						HeadDot.Visible			= false;
						
						Box:SetVisible(false);
					end
				else
					NameTag.Visible			= false;
					DistanceTag.Visible		= false;
					HeadDot.Visible			= false;
					Tracer.Visible			= false;
					OutlineTracer.Visible 	= false;
					
					Box:SetVisible(false);
				end
			else
				NameTag.Visible			= false;
				DistanceTag.Visible		= false;
				HeadDot.Visible			= false;
				Tracer.Visible			= false;
				OutlineTracer.Visible 	= false;

				Box:SetVisible(false);
			end

			shared.InstanceData[v.Name] = Data;
		end
	end
end

local LastInvalidCheck = 0;

local function Update()
	if tick() - LastInvalidCheck > 0.3 then
		LastInvalidCheck = tick();

		if Camera.Parent ~= workspace then
			Camera = workspace.CurrentCamera;
			CameraCon();
			WTVP = Camera.WorldToViewportPoint;
		end

		for i, v in pairs(shared.InstanceData) do
			if not Players:FindFirstChild(tostring(i)) then
				if not shared.InstanceData[i].DontDelete then
					GetTableData(v.Instances)(function(i, obj)
						obj.Visible = false;
						obj:Remove();
						v.Instances[i] = nil;
					end)
					shared.InstanceData[i] = nil;
				else
					if shared.InstanceData[i].Instance == nil or shared.InstanceData[i].Instance.Parent == nil then
						GetTableData(v.Instances)(function(i, obj)
							obj.Visible = false;
							obj:Remove();
							v.Instances[i] = nil;
						end)
						shared.InstanceData[i] = nil;
					end
				end
			end
		end
	end

	local CX = Menu:GetInstance'CrosshairX';
	local CY = Menu:GetInstance'CrosshairY';
	
	if Options.Crosshair.Value then
		CX.Visible = true;
		CY.Visible = true;

		CX.To = V2New((Camera.ViewportSize.X / 2) - 8, (Camera.ViewportSize.Y / 2));
		CX.From = V2New((Camera.ViewportSize.X / 2) + 8, (Camera.ViewportSize.Y / 2));
		CY.To = V2New((Camera.ViewportSize.X / 2), (Camera.ViewportSize.Y / 2) - 8);
		CY.From = V2New((Camera.ViewportSize.X / 2), (Camera.ViewportSize.Y / 2) + 8);
	else
		CX.Visible = false;
		CY.Visible = false;
	end

	if Options.MenuOpen.Value and MenuLoaded then
		local MLocation = GetMouseLocation();
		shared.MenuDrawingData.Instances.Main.Color = Color3.fromHSV(tick() * 24 % 255/255, 1, 1);
		local MainInstance = Menu:GetInstance'Main';
		
		local Values = {
			MainInstance.Position.X;
			MainInstance.Position.Y;
			MainInstance.Position.X + MainInstance.Size.X;
			MainInstance.Position.Y + MainInstance.Size.Y;
		};
		
		if MainInstance and (MouseHoveringOver(Values) or (SubMenu.Open and MouseHoveringOver(SubMenu.Bounds))) then
			Debounce.CursorVis = true;
			
			Menu:UpdateMenuInstance'Cursor1'{
				Visible	= true;
				From	= V2New(MLocation.x, MLocation.y);
				To		= V2New(MLocation.x + 5, MLocation.y + 6);
			}
			Menu:UpdateMenuInstance'Cursor2'{
				Visible	= true;
				From	= V2New(MLocation.x, MLocation.y);
				To		= V2New(MLocation.x, MLocation.y + 8);
			}
			Menu:UpdateMenuInstance'Cursor3'{
				Visible	= true;
				From	= V2New(MLocation.x, MLocation.y + 6);
				To		= V2New(MLocation.x + 5, MLocation.y + 5);
			}
		else
			if Debounce.CursorVis then
				Debounce.CursorVis = false;
				
				Menu:UpdateMenuInstance'Cursor1'{Visible = false};
				Menu:UpdateMenuInstance'Cursor2'{Visible = false};
				Menu:UpdateMenuInstance'Cursor3'{Visible = false};
			end
		end
		if MouseHeld then
			local MousePos = GetMouseLocation();

			if Dragging then
				DraggingWhat.Slider.Position = V2New(math.clamp(MLocation.X - DraggingWhat.Slider.Size.X / 2, DraggingWhat.Line.Position.X, DraggingWhat.Line.Position.X + DraggingWhat.Line.Size.X - DraggingWhat.Slider.Size.X), DraggingWhat.Slider.Position.Y);
				local Percent	= (DraggingWhat.Slider.Position.X - DraggingWhat.Line.Position.X) / ((DraggingWhat.Line.Position.X + DraggingWhat.Line.Size.X - DraggingWhat.Line.Position.X) - DraggingWhat.Slider.Size.X);
				local Value		= CalculateValue(DraggingWhat.Min, DraggingWhat.Max, Percent);
				DraggingWhat.Option(Value);
			elseif DraggingUI then
				Debounce.UIDrag = true;
				local Main = Menu:GetInstance'Main';
				Main.Position = MousePos + DragOffset;
			elseif DragTracerPosition then
				TracerPosition = MousePos;
			end
		else
			Dragging = false;
			DragTracerPosition = false;
			if DraggingUI and Debounce.UIDrag then
				Debounce.UIDrag = false;
				DraggingUI = false;
				CreateMenu(Menu:GetInstance'Main'.Position);
			end
		end
		if not Debounce.Menu then
			Debounce.Menu = true;
			ToggleMenu();
		end
	elseif Debounce.Menu and not Options.MenuOpen.Value then
		Debounce.Menu = false;
		ToggleMenu();
	end
end

RunService:UnbindFromRenderStep(GetDataName);
RunService:UnbindFromRenderStep(UpdateName);

RunService:BindToRenderStep(GetDataName, 300, UpdatePlayerData);
RunService:BindToRenderStep(UpdateName, 199, Update);
end)

Section:NewButton("CMD-X", "GreatZ So Gay", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/CMD-X/CMD-X/master/Source",true))()
end)

Section:NewButton("Infinite Yield", "GreatZ So Gay", function()
	loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
end)

local Tab = Window:NewTab("Teleport")
local Section = Tab:NewSection("Teleport beware 267/268")

Section:NewButton("Hospital", "GreatZ So Gay", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-694.791, 9.08201, -209.377)
end)

Section:NewButton("Gas Station", "GreatZ So Gay", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-254.115, 15.8804, 122.422)
end)

Section:NewButton("Gun Shop", "GreatZ So Gay", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-832.485, 7.98493, -609.56)
end)

Section:NewButton("Ufo", "GreatZ So Gay", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(526.085, 8.18758, 766.6826)
end)
