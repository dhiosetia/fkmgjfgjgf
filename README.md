local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()
-- this is banana hub!
local isHighlightActive = false

local toolhighlightactive = false

local hawktuahactive = false

local isCorruptNatureEspActive = false

local isSurvivorUtilEspActive = false

local run = false

local delay

local isSurvivorHighlightActive = false

local givepizza = false

local connections = {}

local isKillerHighlightActive = false

local hideplayerbar = false

local VirtualBallsManager = game:GetService('VirtualInputManager')

local jumppowerenabled = false

local survivorutil = {
    "007n7",
    "BuildermanSentry",
    "BuildermanDispenser",
    "Pizza",
    "BuildermanSentryEffectRange"
}





local aimbot1x1sounds = {
    "rbxassetid://79782181585087",
    "rbxassetid://128711903717226"
}

local chanceaimbotsounds = {
    "rbxassetid://201858045",
    "rbxassetid://139012439429121"
}

local johnaimbotsounds = {
    "rbxassetid://109525294317144"
}

local jasonaimbotsounds = {
    "rbxassetid://112809109188560",
    "rbxassetid://102228729296384"
}

local shedaimbotsounds = {
    "rbxassetid://12222225",
    "rbxassetid://83851356262523"
}

local guestsounds = {
    "rbxassetid://609342351"
}

local hawktuahactivatesound = {
    "rbxassetid://110759725172567"
}

local hakariactive = false

local quietactive = false

local stam = false

local connection

local chanceaim = false

local chanceaimbotLoop

local jasonaimbotloop

local genshouldloop = false

local genactive = false

local aimbot1x1loop

local johnloop

local guestloop

local shedloop

local player = game.Players.LocalPlayer

local aimbot1x1 = false

local johnaim = false

local connection

local jasonaim = false

local shedaim = false

local guestaim = false

local Window = Rayfield:CreateWindow({
   Name = "Banana Hub",
   Icon = "banana",
   LoadingTitle = "bananawave!",
   LoadingSubtitle = "by azoyona",
   Theme = "DarkBlue",
})

local Tab = Window:CreateTab("Home", "scroll-text")
local Tab1 = Window:CreateTab("ESP", "eye")
local Tab2 = Window:CreateTab("stamina", "gauge")
local Tab3 = Window:CreateTab("Killer", "axe")
local Tab4 = Window:CreateTab("Survivor", "user-round")
local Tab5 = Window:CreateTab("generator", "box")
local Tab6 = Window:CreateTab("Fun", "laugh")

local Divider = Tab:CreateDivider() -- [[this again]] 
local Divider = Tab6:CreateDivider()-- [[this again]] 
     local Divider = Tab1:CreateDivider()-- [[this again]] 
	      local Divider = Tab2:CreateDivider()-- [[this again]] 
		  local Divider = Tab3:CreateDivider()-- [[this again]] 
	 local Divider = Tab4:CreateDivider()-- [[this again]] 
local Divider = Tab5:CreateDivider()-- [[this again]] 

Rayfield:Notify({ -- this for notify then [false or true to you want then]
   Title = "welcome to banana hub!", -- fuck you fuck all fuck others so what suck all
   Content = "today i sure to this script the best!", -- best???
   Duration = 6.5, -- you own time
   Image = "banana", -- link this for icon "https://lucide.dev/icons/" or image in roblox
}) -- idk who did it?

local function discord(state) -- if state then
	setclipboard("https://discord.gg/QTpZwtmJ")
end

local function esp(state)
  isHighlightActive = state 
    
        local function applyGeneratorHighlight(generator)
            if generator.Name == "Generator" then
                local existingHighlight = generator:FindFirstChild("GeneratorHighlight")
                local progress = generator:FindFirstChild("Progress")
                
                if isHighlightActive then
                    if not existingHighlight then
                        local genhighlight = Instance.new("Highlight")
                        genhighlight.Parent = generator
                        genhighlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
                        genhighlight.Name = "GeneratorHighlight"
                    end
                else
                    if existingHighlight then
                        existingHighlight:Destroy()
                    end
                    return
                end
    
                if progress then
                    if progress.Value == 100 then
                        local highlight = generator:FindFirstChild("GeneratorHighlight")
                        if highlight then
                            highlight:Destroy()
                        end
                        return
                    end
    
                    progress:GetPropertyChangedSignal("Value"):Connect(function()
                        if progress.Value == 100 then
                            local highlight = generator:FindFirstChild("GeneratorHighlight")
                            if highlight then
                                highlight:Destroy()
                            end
                        elseif isHighlightActive and not generator:FindFirstChild("GeneratorHighlight") then
                            local genhighlight = Instance.new("Highlight")
                            genhighlight.Parent = generator
                            genhighlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
                            genhighlight.Name = "GeneratorHighlight"
                        end
                    end)
                end
            end
        end
    
        for _, v in pairs(game.Workspace.Map.Ingame.Map:GetChildren()) do
            applyGeneratorHighlight(v)
        end
    
        game.Workspace.Map.Ingame.Map.ChildAdded:Connect(function(child)
            applyGeneratorHighlight(child)
        end)
end

local function esp1(state)
	toolhighlightActive = state
        
        local function applyHighlight(tool)
            if toolhighlightActive then
                local existinghighlight = tool:FindFirstChild("ToolHighlight")
                if not existinghighlight then
                    local toolhighlight = Instance.new("Highlight")
                    toolhighlight.Name = "ToolHighlight"
                    toolhighlight.Parent = tool
                    toolhighlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
    
                    if tool.Name == "Medkit" then
                        toolhighlight.FillColor = Color3.fromRGB(0, 255, 0)
                    elseif tool.Name == "BloxyCola" then
                        toolhighlight.FillColor = Color3.fromRGB(88, 57, 39)
                    end
                end
            else
                local existinghighlight = tool:FindFirstChild("ToolHighlight")
                if existinghighlight then
                    existinghighlight:Destroy()
                end
            end
        end
        
        for _, v in pairs(game.Workspace.Map.Ingame:GetChildren()) do
            if v:IsA("Tool") then
                applyHighlight(v)
            end
        end
        
        game.Workspace.Map.Ingame.ChildAdded:Connect(function(child)
            if child:IsA("Tool") then
                applyHighlight(child)
            end
        end)
end

local function esp2(state)
	 isCorruptNatureEspActive = state
        for i, v in pairs(game.Workspace.Map.Ingame:GetChildren()) do
            if v:IsA("Model") then
                local existingHighlight = v:FindFirstChild("CorruptNatureHighlight")
                if isCorruptNatureEspActive then
                    if not existingHighlight then
                        if v.Name == "HumanoidRootProjectile" or v.Name == "PizzaDeliveryRig" or v.Name == "Bunny" or v.Name == "Mafiaso1" or v.Name == "Mafiaso2" or v.Name == "Mafiaso3" then
                            local highlight = Instance.new("Highlight")
                            highlight.Name = "CorruptNatureHighlight"
                            highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
                            highlight.Parent = v
                        end
                    end
                else
                    if existingHighlight then
                        existingHighlight:Destroy()
                    end
                end
            end
        end
end

local function esp3(state)
				    isSurvivorHighlightActive = state
    
        local function applySurvivorHighlight(model)
            if model:IsA("Model") and model:FindFirstChild("Head") then
                local existingBillboard = model.Head:FindFirstChild("billboard")
                local existingHighlight = model:FindFirstChild("HiThere")
                
                if isSurvivorHighlightActive then
                    if not existingBillboard then
                        local billboard = Instance.new("BillboardGui")
                        billboard.Name = "billboard"
                        billboard.Size = UDim2.new(0, 100, 0, 50)
                        billboard.StudsOffset = Vector3.new(0, 2, 0)
                        billboard.AlwaysOnTop = true
                        billboard.Parent = model.Head
                        
                        local textLabel = Instance.new("TextLabel", billboard)
                        textLabel.Size = UDim2.new(1, 0, 1, 0)
                        textLabel.Text = model.Name
                        textLabel.TextColor3 = Color3.new(1, 1, 1)
                        textLabel.TextStrokeTransparency = 0
                        textLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
                        textLabel.BackgroundTransparency = 1
                    end
    
                    if not existingHighlight then
                        local highlight = Instance.new("Highlight")
                        highlight.Name = "HiThere"
                        highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
                        highlight.FillColor = Color3.fromRGB(0, 355, 0)
                        highlight.Parent = model
                    end
                else
                    if existingBillboard then
                        existingBillboard:Destroy()
                    end
                    if existingHighlight then
                        existingHighlight:Destroy()
                    end
                end
            end
        end
    
        for _, v in pairs(game.Workspace.Players.Survivors:GetChildren()) do
            applySurvivorHighlight(v)
        end
    
        game.Workspace.Players.Survivors.ChildAdded:Connect(function(child)
            applySurvivorHighlight(child)
        end)
end

local function esp4(state)
	   isKillerHighlightActive = state
    
        local function applyKillerHighlight(model)
            if model:IsA("Model") and model:FindFirstChild("Head") then
                local existingBillboard = model.Head:FindFirstChild("billboard")
                local existingHighlight = model:FindFirstChild("HiThere")
                
                if isKillerHighlightActive then
                    if not existingBillboard then
                        local billboard = Instance.new("BillboardGui")
                        billboard.Name = "billboard"
                        billboard.Size = UDim2.new(0, 100, 0, 50)
                        billboard.StudsOffset = Vector3.new(0, 2, 0)
                        billboard.AlwaysOnTop = true
                        billboard.Parent = model.Head
                        
                        local textLabel = Instance.new("TextLabel", billboard)
                        textLabel.Size = UDim2.new(1, 0, 1, 0)
                        textLabel.Text = model.Name
                        textLabel.TextColor3 = Color3.new(1, 0, 0)
                        textLabel.TextStrokeTransparency = 0
                        textLabel.TextStrokeColor3 = Color3.new(0, 0, 0)
                        textLabel.BackgroundTransparency = 1
                    end
    
                    if not existingHighlight then
                        local highlight = Instance.new("Highlight")
                        highlight.Name = "HiThere"
                        highlight.DepthMode = Enum.HighlightDepthMode.AlwaysOnTop
                        highlight.FillColor = Color3.fromRGB(355, 0, 0)
                        highlight.Parent = model
                    end
                else
                    if existingBillboard then
                        existingBillboard:Destroy()
                    end
                    if existingHighlight then
                        existingHighlight:Destroy()
                    end
                end
            end
        end
    
        for _, v in pairs(game.Workspace.Players.Killers:GetChildren()) do
            applyKillerHighlight(v)
        end
    
        game.Workspace.Players.Killers.ChildAdded:Connect(function(child)
            applyKillerHighlight(child)
        end)
end

local function staminaloss(Value)
	local Sprinting = game:GetService("ReplicatedStorage").Systems.Character.Game.Sprinting
local m = require(Sprinting)
m.StaminaLoss = Value
end

local function staminagain(state)
		local Sprinting = game:GetService("ReplicatedStorage").Systems.Character.Game.Sprinting
local m = require(Sprinting)
m.StaminaGain = Value
end

local function staminamax(state)
		local Sprinting = game:GetService("ReplicatedStorage").Systems.Character.Game.Sprinting
local m = require(Sprinting)
m.StaminaMax = Value
end

local function staminamin(state)
		local Sprinting = game:GetService("ReplicatedStorage").Systems.Character.Game.Sprinting
local m = require(Sprinting)
m.StaminaMin = Value
end

local function staminaspeed(state)
		local Sprinting = game:GetService("ReplicatedStorage").Systems.Character.Game.Sprinting
local m = require(Sprinting)
m.StaminaSpeed = Value
end

local function loss(state)
	local Sprinting = game:GetService("ReplicatedStorage").Systems.Character.Game.Sprinting
local m = require(Sprinting)
m.StaminaLoss = PlaceholderText
end

local function inf(state)
	  stam = state
        local stamscript = require(game.ReplicatedStorage.Systems.Character.Game.Sprinting)
        
        local connection
        connection = game:GetService("RunService").Heartbeat:Connect(function()
            if not stam then
                connection:Disconnect()
                stamscript.StaminaLossDisabled = nil
                return
            end
            stamscript.StaminaLossDisabled = function() 
			end
			end)
end

local function meme(state)
	local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

local player = Players.LocalPlayer

local function setupAnimations(character)
    local humanoid = character:WaitForChild("Humanoid")

    -- Disable Animate if present
    local animate = character:FindFirstChild("Animate")
    if animate then
        animate.Disabled = true
    end

    -- Load custom animations
    local idleAnim = Instance.new("Animation")
    idleAnim.AnimationId = "rbxassetid://18886066950"

    local moveAnim = Instance.new("Animation")
    moveAnim.AnimationId = "rbxassetid://18886064499"

    local idleTrack = humanoid:LoadAnimation(idleAnim)
    local moveTrack = humanoid:LoadAnimation(moveAnim)

    idleTrack.Priority = Enum.AnimationPriority.Action  -- Higher than Core
    moveTrack.Priority = Enum.AnimationPriority.Movement

    idleTrack:Play()

    RunService.Heartbeat:Connect(function()
        local speed = humanoid.MoveDirection.Magnitude

        -- Force-stop other idle animations
        for _, track in pairs(humanoid:GetPlayingAnimationTracks()) do
            if track.Animation.AnimationId ~= idleAnim.AnimationId
                and track.Animation.AnimationId ~= moveAnim.AnimationId then
                if track.Priority == Enum.AnimationPriority.Core
                    or track.Name == "idle"
                    or track.Animation.AnimationId:lower():find("idle") then
                    track:Stop()
                end
            end
        end

        if speed > 0.01 then
            if not moveTrack.IsPlaying then
                idleTrack:Stop()
                moveTrack:Play()
            end
        else
            if not idleTrack.IsPlaying then
                moveTrack:Stop()
                idleTrack:Play()
            end
        end
    end)
end

-- Support for current and future character loads
if player.Character then
    setupAnimations(player.Character)
end

player.CharacterAdded:Connect(setupAnimations)
end

local function meme1(state)
	--[[
	WARNING: Heads up! This script has not been verified by ScriptBlox. Use at your own risk!
]]
local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

local player = Players.LocalPlayer

local function setupAnimations(character)
    local humanoid = character:WaitForChild("Humanoid")

    -- Disable Animate if present
    local animate = character:FindFirstChild("Animate")
    if animate then
        animate.Disabled = true
    end

    -- Load custom animations
    local idleAnim = Instance.new("Animation")
    idleAnim.AnimationId = "rbxassetid://18885903667"

    local moveAnim = Instance.new("Animation")
    moveAnim.AnimationId = "rbxassetid://18885906143"

    local idleTrack = humanoid:LoadAnimation(idleAnim)
    local moveTrack = humanoid:LoadAnimation(moveAnim)

    idleTrack.Priority = Enum.AnimationPriority.Action  -- Higher than Core
    moveTrack.Priority = Enum.AnimationPriority.Movement

    idleTrack:Play()

    RunService.Heartbeat:Connect(function()
        local speed = humanoid.MoveDirection.Magnitude

        -- Force-stop other idle animations
        for _, track in pairs(humanoid:GetPlayingAnimationTracks()) do
            if track.Animation.AnimationId ~= idleAnim.AnimationId
                and track.Animation.AnimationId ~= moveAnim.AnimationId then
                if track.Priority == Enum.AnimationPriority.Core
                    or track.Name == "idle"
                    or track.Animation.AnimationId:lower():find("idle") then
                    track:Stop()
                end
            end
        end

        if speed > 0.01 then
            if not moveTrack.IsPlaying then
                idleTrack:Stop()
                moveTrack:Play()
            end
        else
            if not idleTrack.IsPlaying then
                moveTrack:Stop()
                idleTrack:Play()
            end
        end
    end)
end

-- Support for current and future character loads
if player.Character then
    setupAnimations(player.Character)
end

player.CharacterAdded:Connect(setupAnimations)
end

local function c00lkidd(state)
	print("Don't have c00lkidd?")
end

local function johndoe(state)
	 if state then
                johnloop = game.Players.LocalPlayer.Character.HumanoidRootPart.ChildAdded:Connect(function(child)
                    if not johnaim then return end
                    for _, v in pairs(johnaimbotsounds) do
                        if child.Name == v then
                           
                            local survivors = {}
                            for _, player in pairs(game.Players:GetPlayers()) do
                                if player ~= game.Players.LocalPlayer then
                                    local character = player.Character
                                    if character and character:FindFirstChild("HumanoidRootPart") then
                                        table.insert(survivors, character)
                                    end
                                end
                            end
        
                           
                            local nearestSurvivor = nil
                            local shortestDistance = math.huge  
                            
                            for _, survivor in pairs(survivors) do
                                local survivorHRP = survivor.HumanoidRootPart
                                local playerHRP = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                                
                                if playerHRP then
                                    local distance = (survivorHRP.Position - playerHRP.Position).Magnitude
                                    if distance < shortestDistance then
                                        shortestDistance = distance
                                        nearestSurvivor = survivor
                                    end
                                end
                            end
                            
                          
                            if nearestSurvivor then
                                local nearestHRP = nearestSurvivor.HumanoidRootPart
                                local playerHRP = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                                local maxIterations = 330
                                if playerHRP then
                                    local direction = (nearestHRP.Position - playerHRP.Position).Unit
                                    local num = 1
                                   
                                        
                                        while num <= maxIterations do
                                            task.wait(0.01)
                                            num = num + 1
                                            workspace.CurrentCamera.CFrame = CFrame.new(workspace.CurrentCamera.CFrame.Position, nearestHRP.Position)
                                            playerHRP.CFrame = CFrame.lookAt(playerHRP.Position, Vector3.new(nearestHRP.Position.X, nearestHRP.Position.Y, nearestHRP.Position.Z))
                    
                                    end
                                end
                            end
                        end
                    end
                end)
            else
                if johnloop then
                    johnloop:Disconnect()
                    johnloop = nil
                end
            end
end

local function johndoe1(state)
	   johnaim = state
        if game.Players.LocalPlayer.Character.Name ~= "JohnDoe" and state then
            Rayfield:Notify{Title = "Oops..", Content = "No Aurizoyd join this exploiters", image = "error", Duration = 5}
            return 
        end
end

local function p1x1(state)
	  if state then
            aimbot1x1loop = game.Players.LocalPlayer.Character.HumanoidRootPart.ChildAdded:Connect(function(child)
                if not aimbot1x1 then return end
                for _, v in pairs(aimbot1x1sounds) do
                    if child.Name == v then
                        local survivors = {}
                        for _, player in pairs(game.Players:GetPlayers()) do
                            if player ~= game.Players.LocalPlayer then
                                local character = player.Character
                                if character and character:FindFirstChild("HumanoidRootPart") then
                                    table.insert(survivors, character)
                                end
                            end
                        end
    
                        local nearestSurvivor = nil
                        local shortestDistance = math.huge  
                        
                        for _, survivor in pairs(survivors) do
                            local survivorHRP = survivor.HumanoidRootPart
                            local playerHRP = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                            
                            if playerHRP then
                                local distance = (survivorHRP.Position - playerHRP.Position).Magnitude
                                if distance < shortestDistance then
                                    shortestDistance = distance
                                    nearestSurvivor = survivor
                                end
                            end
                        end
                        
                        if nearestSurvivor then
                            local nearestHRP = nearestSurvivor.HumanoidRootPart
                            local playerHRP = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                            
                            if playerHRP then
                                local direction = (nearestHRP.Position - playerHRP.Position).Unit
                                local num = 1
                                local maxIterations = 100 
    
                                
                                    if child.Name == "rbxassetid://79782181585087" then
                                        maxIterations = 220  
                                    end
    
                                while num <= maxIterations do
                                    task.wait(0.01)
                                    num = num + 1
                                    workspace.CurrentCamera.CFrame = CFrame.new(workspace.CurrentCamera.CFrame.Position, nearestHRP.Position)
                                    playerHRP.CFrame = CFrame.lookAt(playerHRP.Position, Vector3.new(nearestHRP.Position.X, nearestHRP.Position.Y, nearestHRP.Position.Z))
                                end
                            
                            end
                        end
                    end
                end
            end)
        else
            if aimbot1x1loop then
                aimbot1x1loop:Disconnect()
                aimbot1x1loop = nil
            end
        end
end

local function p1x1v1()
	  while true do
            if Do1x1PopupsLoop then
                local player = game:GetService("Players").LocalPlayer
                local popups = player.PlayerGui.TemporaryUI:GetChildren()
    
                for _, i in ipairs(popups) do
                    if i.Name == "1x1x1x1Popup" then
                        local centerX = i.AbsolutePosition.X + (i.AbsoluteSize.X / 2)
                        local centerY = i.AbsolutePosition.Y + (i.AbsoluteSize.Y / 2)
        
                        VirtualBallsManager:SendMouseButtonEvent(centerX, centerY, Enum.UserInputType.MouseButton1.Value, true, player.PlayerGui, 1)
                        VirtualBallsManager:SendMouseButtonEvent(centerX, centerY, Enum.UserInputType.MouseButton1.Value, false, player.PlayerGui, 1)
                    end
                end
            end
            task.wait(0.1)
        end
end

local function jason(state)
	 if state then
                jasonaimbotloop = game.Players.LocalPlayer.Character.HumanoidRootPart.ChildAdded:Connect(function(child)
                    if not jasonaim then return end
                    for _, v in pairs(jasonaimbotsounds) do
                        if child.Name == v then
                           
                            local survivors = {}
                            for _, player in pairs(game.Players:GetPlayers()) do
                                if player ~= game.Players.LocalPlayer then
                                    local character = player.Character
                                    if character and character:FindFirstChild("HumanoidRootPart") then
                                        table.insert(survivors, character)
                                    end
                                end
                            end
        
                           
                            local nearestSurvivor = nil
                            local shortestDistance = math.huge  
                            
                            for _, survivor in pairs(survivors) do
                                local survivorHRP = survivor.HumanoidRootPart
                                local playerHRP = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                                
                                if playerHRP then
                                    local distance = (survivorHRP.Position - playerHRP.Position).Magnitude
                                    if distance < shortestDistance then
                                        shortestDistance = distance
                                        nearestSurvivor = survivor
                                    end
                                end
                            end
                            
                          
                            if nearestSurvivor then
                                local nearestHRP = nearestSurvivor.HumanoidRootPart
                                local playerHRP = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                                local maxIterations = 70
                                if playerHRP then
                                    local direction = (nearestHRP.Position - playerHRP.Position).Unit
                                    local num = 1
                                   
                                        
                                        while num <= maxIterations do
                                            task.wait(0.01)
                                            num = num + 1
                                            
                                            playerHRP.CFrame = CFrame.lookAt(playerHRP.Position, Vector3.new(nearestHRP.Position.X, nearestHRP.Position.Y, nearestHRP.Position.Z))
                    
                                    end
                                end
                            end
                        end
                    end
                end)
            else
                if jasonaimbotloop then
                    jasonaimbotloop:Disconnect()
                    jasonaimbotloop = nil
                end
            end
end

local function baby(state)
 jasonaim = state
        if game.Players.LocalPlayer.Character.Name ~= "Jason" and state then
            return 
        end
	if state then
		game.Players.LocalPlayer:kick("                                                               Auto Jason Killers")
	end
end

local function twotime(state)
	 if player.Character.Name ~= "TwoTime" then
            Rayfield:Notify{Title = "Oops..", Content = "you are isn't two time please you using is two time and you got aimbot for killer!", Duration = 5}
            return end
			if state then
local module = {
	DisplayName = "Two Time";
	Quote = "\"Shadows die twice.\"";
	Credits = "";
	Class = "Sentinel";
	RenderImage = "rbxassetid://100794675544132";
	Price = 500;
	Exclusive = false;
	Health = 800000;
	Speed = 12;
	DaggerCooldown = 30;
	DaggerDamage = 25;
	DaggerBackstabDamage = 35;
	DaggerLungeForce = 110;
	DaggerUncrouchedLungeForce = 35;
	DaggerBackstabThreshold = 90;
	DaggerLookDirectionAngle = 70;
	DaggerStatusTime = 2;
	DaggerBackstabStatusTime = 4;
	DaggerLifestealFromFront = 10;
	DaggerLifestealFromBack = 20;
	DaggerResLevel = 3;
	DaggerResDuration = 0.7;
	BloodReqIncreasePerTwoTime = 1;
	CrouchCooldown = 50;
	CrouchMinCooldown = 35;
	CrouchSpeed = 9;
	CrouchRunSpeed = 15;
	CrouchInvisibilityLevel = 3;
	CrouchUndetectableLevel = 1;
	CrouchSpeedCloseTime = 1;
	CrouchStabAmplifyTime = 5;
	CrouchRevealTime = 2;
	CrouchDistances = {
		CLOSE = {0, 15};
		DEBUFF_SLOWNESS = {75, -1};
		DEBUFF_HIGHLIGHT = {125, -1};
	};
	CrouchSlownessDebuffMax = 150;
	Lives = 2;
	BloodRequiredForRespawn = 8;
	BloodFromFront = 3;
	BloodFromBack = 4.5;
	RespawnLocationDistance = 10;
	NextLifeHealthDivisor = 2;
	InvincibilityDuration = 2;
	LastSurvivorMaxHealth = 110;
	LastSurvivorHealthBonus = 50;
	RespawnLocation = script.Spawn;
	HealthBar = script.Sidebar;
	AudioReplication = script.AudioReplication;
	VFX = script.TwoTimeVFX;
	LifeAppearances = {script.Life1, script.Life2};
	DaggerTemplate = script.GhostFire;
	Animations = {
		CrouchStart = "rbxassetid://98606150731314";
		CrouchIdle = "rbxassetid://74530436512522";
		CrouchWalk = "rbxassetid://94721495253171";
		CrouchRun = "rbxassetid://93499989310243";
		Stab = "rbxassetid://86545133269813";
		LungeStart = "rbxassetid://89448354637442";
		LungeLoop = "rbxassetid://115194624791339";
		LungeEnd = "rbxassetid://119434518007321";
		Ritual = "rbxassetid://117339039533356";
	};
	Sounds = {
		Crouch = "rbxassetid://93315212708186";
		Stand = "rbxassetid://112995614541035";
		Mark = "rbxassetid://100981628806546";
		Hit = "rbxassetid://96032371062643";
		Stab = "rbxassetid://86710781315432";
		CrouchStab = "rbxassetid://99820161736138";
		Respawn = "rbxassetid://84260460113659";
	};
	ExpressionsTable = {{
		Happy = "rbxassetid://81896815825257";
		Default = "rbxassetid://73483634925418";
		Hurt = "rbxassetid://93421870784694";
		Injured = "rbxassetid://133089396665213";
		Dead = "rbxassetid://133611309054814";
		Drinking = "rbxassetid://99335439385081";
	}, {
		Happy = "rbxassetid://79565455816327";
		Default = "rbxassetid://131136664195288";
		Hurt = "rbxassetid://120830873592415";
		Injured = "rbxassetid://104452353265078";
		Dead = "rbxassetid://123221349342396";
		Drinking = "rbxassetid://127552301758353";
	}};
	Expressions = module.ExpressionsTable[1];
	TextInteractions = {
		Requests = {
			ElliotPizza = {"Hey, hey. Pizza, pizza please.", "Pizza’s something I haven’t tried much, mind if I get a slice?", "I must ask for a pizza.", "Do you have pizza? I could use one!", "May I have a pizza slice?", "I really want a pizza! May I have one?"};
			BuildermanSentry = {"Your turrets may be of use over here.", "A sentry here should be put to use. Place it here.", "Place your sentry over here. It will help against the foes.", "Put down a sentry here.", "Your sentry will be of use over here."};
			BuildermanDispenser = {"I’m in need of a dispenser in my position.", "I require a dispenser to be placed here.", "Dispenser here, please.", "Put down one of your dispensers here.", "Your dispenser is needed here."};
			DusekkarProtection = {"Divine pumpkin, I humbly request your divine ability.", "Divine pumpkin, I implore you to cast your ability onto me.", "Divine pumpkin, I ask of thee to be blessed.", "Divine pumpkin, blessed be thy heart should you cast a spell unto me.", "Divine pumpkin, I ask for thy divine intervention."};
		};
		Thanks = {
			Regular = {"Much appreciated.", "Very thankful for your service.", "May good fortune come your way for your generosity.", "The Spawn would be pleased with your acts of kindness.", "I thank you for your service.", "Oh give thanks to the Spawn, for he is good; for their steadfast love endures forever."};
		};
	};
	Information = {{
		Separator = "GENERAL INFO";
	}, {
		Header = "TWO TIME";
		Text = "A fragile cultist that holds a terrible secret. Bearing nothing other than a sleek dagger and manic smile, they're able to earn a second life through risk and sacrifice.\n";
	}, {
		Header = "STATS";
		Text = "Difficulty: ★★★★☆\n"..`Health: {module.Health or 100}\n`..`Regular Speed: {module.Speed or 12}\n`..`Sprinting Speed: {module.SprintSpeed or 24}\n`..`Max Stamina: {module.MaxStamina or 100}\n`..`Stamina Loss per sec: {module.StaminaLoss or 10}\n`..`Stamina Gain per sec: {module.StaminaGain or 20}\n`;
	}, {
		Separator = "PASSIVES";
	}, {
		Header = "OBLATION";
		Quote = "\"You both shall set out on the grand step to rebirth.\" - ██████";
		Text = `{"Two Time"} has a bar on the right side of the screen that, when filled, grants them a second life.\n`.."The only way to fill this bar is by dealing damage to the Killer.\n".."In their second life, they only have <b>half</b> as much health (40) as they usually do (80).\n".."Upon activation:\n".." * Stamina is restored by 40%\n".." * All status effects are removed\n"..` * {"Two Time"} is made invincible for {module.InvincibilityDuration} seconds \n`.." * <b>Speed II</b> is applied for 6 seconds\n".." * <b>Weakness V</b> is applied for 12 seconds\n";
	}, {
		Header = "SACRIFICIAL DAGGER";
		Quote = "\"Lookie, █████—they gave us this cool knife!\" - Two Time";
		Text = `{"Two Time"} instantly stabs forward and gains Resistance {module.DaggerResLevel} for {module.DaggerResDuration} seconds.\n`..`Landing a stab to the front will do {module.DaggerDamage} damage, and heal Two Time for {module.DaggerLifestealFromFront}.\n`..`Landing a stab to the back will instead do {module.DaggerBackstabDamage} damage, stun the killer for {module.DaggerBackstabStatusTime}, and heal Two Time for {module.DaggerLifestealFromBack}.\n`.."Using this ability while crouched lunges you forward with a quicker stab.\n";
	}, {
		Header = "CROUCH";
		Quote = "\"Quiet, Two Time! They're not supposed to see us in here, hehe!\" - █████";
		Text = `{"Two Time"} crouches down to silence their footsteps & become stealthier.\n`..`{"Two Time"} remains crouched for at most {module.CrouchCooldown - module.CrouchMinCooldown} seconds, but can uncrouch whenever they need to.\n`..`Crouching applies Undetectable I and Invisibility III for at most {module.CrouchCooldown - module.CrouchMinCooldown} seconds. Uncrouching manually will forcibly remove these statuses.\n`;
	}, {
		Header = "RITUAL";
		Quote = "\"Spawn will be eternally pleased at our devotion!\" - ██████";
		Text = `{"Two Time"} places down a respawn location.\n`..`Dying with a full oblation bar will instantly teleport {"Two Time"} to this point.\n`;
	}};
}
else
	moudie:Destroy()
	if moudie then
	all:Destroy()
	end
			end
end

local function chance(state)
	 if state then
            chanceaimbotLoop = game.Players.LocalPlayer.Character.HumanoidRootPart.ChildAdded:Connect(function(child)
                if not chanceaim then return end
                for _, v in pairs(chanceaimbotsounds) do
                    if child.Name == v  then
                        local killer = game.Workspace.Players:FindFirstChild("Killers"):FindFirstChildOfClass("Model")
                        if killer and killer:FindFirstChild("HumanoidRootPart") then
                            local killerHRP = killer.HumanoidRootPart
                            local playerHRP = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                            if playerHRP then
                                local direction = (killerHRP.Position - playerHRP.Position).Unit
                                local num = 1
                                local maxIterations = 100
                            
                                
                                    while num <= maxIterations do
                                        task.wait(0.01)
                                        num = num + 1
                                        workspace.CurrentCamera.CFrame = CFrame.new(workspace.CurrentCamera.CFrame.Position, killerHRP.Position)
                                        playerHRP.CFrame = CFrame.lookAt(playerHRP.Position, Vector3.new(killerHRP.Position.X, killerHRP.Position.Y, killerHRP.Position.Z))
                                    end
                                
                            
                            end
                        end
                    end
                end
            end)
        else
            if chanceaimbotLoop then
                chanceaimbotLoop:Disconnect()
                chanceaimbotLoop = nil
            end
        end
end

local function shed(state)
	 if state then
            shedloop = game.Players.LocalPlayer.Character.Sword.ChildAdded:Connect(function(child)
                if not shedaim then return end
                for _, v in pairs(shedaimbotsounds) do
                    if child.Name == v then
                        local killersFolder = game.Workspace.Players:FindFirstChild("Killers")
                        if killersFolder then
                            local killer = killersFolder:FindFirstChildOfClass("Model")
                            if killer and killer:FindFirstChild("HumanoidRootPart") then
                                local killerHRP = killer.HumanoidRootPart
                                local playerHRP = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                                if playerHRP then
                                    local num = 1
                                    local maxIterations = 100
    
                                    while num <= maxIterations do
                                        task.wait(0.01)
                                        num = num + 1
                                        workspace.CurrentCamera.CFrame = CFrame.new(workspace.CurrentCamera.CFrame.Position, killerHRP.Position)
                                        playerHRP.CFrame = CFrame.lookAt(playerHRP.Position, killerHRP.Position)
                                    end
                                end
                            end
                        end
                    end
                end
            end)
        else
            if shedloop then
                shedloop:Disconnect()
                shedloop = nil
            end
        end
end

local function guest(state)
	 if state then
            shedloop = game.Players.LocalPlayer.Character.HumanoidRootPart.ChildAdded:Connect(function(child)
                if not shedaim then return end
                for _, v in pairs(guestsounds) do
                    if child.Name == v then
                        local killersFolder = game.Workspace.Players:FindFirstChild("Killers")
                        if killersFolder then
                            local killer = killersFolder:FindFirstChildOfClass("Model")
                            if killer and killer:FindFirstChild("HumanoidRootPart") then
                                local killerHRP = killer.HumanoidRootPart
                                local playerHRP = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                                if playerHRP then
                                    local num = 1
                                    local maxIterations = 100
    
                                    while num <= maxIterations do
                                        task.wait(0.01)
                                        num = num + 1
                                        workspace.CurrentCamera.CFrame = CFrame.new(workspace.CurrentCamera.CFrame.Position, killerHRP.Position)
                                        playerHRP.CFrame = CFrame.lookAt(playerHRP.Position, killerHRP.Position)
                                    end
                                end
                            end
                        end
                    end
                end
            end)
        else
            if guestloop then
                guestloop:Disconnect()
                guestloop = nil
            end
        end
end

local function twotime1(state)
	if state then
            twoaimbot = game.Players.LocalPlayer.Character.RightBandages.ChildAdded:Connect(function(child)
                if not twoaimbot then return end
                for _, v in pairs(twotimesounds) do
                    if child.Name == v then
                        local killersFolder = game.Workspace.Players:FindFirstChild("Killers")
                        if killersFolder then
                            local killer = killersFolder:FindFirstChildOfClass("Model")
                            if killer and killer:FindFirstChild("HumanoidRootPart") then
                                local killerHRP = killer.HumanoidRootPart
                                local playerHRP = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                                if playerHRP then
                                    local num = 1
                                    local maxIterations = 100
    
                                    while num <= maxIterations do
                                        task.wait(0.01)
                                        num = num + 1
                                        workspace.CurrentCamera.CFrame = CFrame.new(workspace.CurrentCamera.CFrame.Position, killerHRP.Position)
                                        playerHRP.CFrame = CFrame.lookAt(playerHRP.Position, killerHRP.Position)
                                    end
                                end
                            end
                        end
                    end
                end
            end)
        else
            if twoaimbot then
                twoaimbot:Disconnect()
                twoaimbot = nil
            end
        end
end

local function second1(parameters)
	run = state
        
        local debounce = {}
        


        while run do
            task.wait(15)
            for _, v in pairs(game.Workspace.Map.Ingame.Map:GetChildren()) do
                if v.Name == "Generator" then
                    
                    if not debounce[v] then
                        debounce[v] = true
                        v:WaitForChild("Remotes"):WaitForChild("RE"):FireServer()
                        task.delay(delay, function() debounce[v] = nil end)
                    end
                end
            end
        end
end

local function second2(parameters)
	run = state
        
        local debounce = {}
        


        while run do
            task.wait(10)
            for _, v in pairs(game.Workspace.Map.Ingame.Map:GetChildren()) do
                if v.Name == "Generator" then
                    
                    if not debounce[v] then
                        debounce[v] = true
                        v:WaitForChild("Remotes"):WaitForChild("RE"):FireServer()
                        task.delay(delay, function() debounce[v] = nil end)
                    end
                end
            end
        end
end

local function second3(parameters)
	run = state
        
        local debounce = {}
        


        while run do
            task.wait(5)
            for _, v in pairs(game.Workspace.Map.Ingame.Map:GetChildren()) do
                if v.Name == "Generator" then
                    
                    if not debounce[v] then
                        debounce[v] = true
                        v:WaitForChild("Remotes"):WaitForChild("RE"):FireServer()
                        task.delay(delay, function() debounce[v] = nil end)
                    end
                end
            end
        end
end

local function hell()
 for i, v in pairs(game.Workspace.Map.Ingame.Map.Generators:GetChildren()) do
            if v:IsA("Model") then
                local num = 0
                repeat
                num += 1
                v:WaitForChild("Remotes"):WaitForChild("RE"):FireServer()
                until num == 4
            end
        end
	end

	local function Value1(Value)
		delay = Value
	end

	local function givemesomepizza(state)
            if not state then

            for _, v in pairs(connections) do
                v:Disconnect()
            end
            table.clear(connections)
            return
        end
    
        
        local function tp(child)
            if child:IsA("BasePart") and child.Name == "Pizza" then
                local player = game.Players.LocalPlayer
                if player and player.Character then
                    local hrp = player.Character:FindFirstChild("HumanoidRootPart")
                    if hrp then
                        child.CFrame = hrp.CFrame
                    end
                end
				end
				end
	end

	local function free(state)
		   local clone = game.Players.LocalPlayer.PlayerData.Equipped.Skins:Clone()
        clone.Parent = game.Players.LocalPlayer.PlayerData.Purchased.Killers
        for i, v in pairs(clone:GetChildren()) do
            v.Parent = game.Players.LocalPlayer.PlayerData.Purchased.Killers
            end
        local clone2 = game.Players.LocalPlayer.PlayerData.Equipped.Skins:Clone()
        clone2.Parent = game.Players.LocalPlayer.PlayerData.Purchased.Survivors
        
            for i, v in pairs(clone2:GetChildren()) do
            v.Parent = game.Players.LocalPlayer.PlayerData.Purchased.Survivors
            end
	end

	local function health(Value)
		local Player = game.Players.LocalPlayer
local Character = Player.Character
local Humanoid = Character.Humanoid
 
print('Godmode working.')
 
Humanoid.MaxHealth = Value
Humanoid.Health = Humanoid.MaxHealth / 2
 
Humanoid.HealthChanged:connect(function()
    if Humanoid.Health < 10 then
        Humanoid.Health = Humanoid.MaxHealth
    end
end)
	end

	local function walkspeed(Value)
		game.Players.LocalPlayer.Character.SpeedMultipliers.Sprinting.Value = Value
	end

	local function jumppower(Value)
		game.Players.LocalPlayer.Character.Humanoid.JumpPower = Value
	end

	local function fov(Value)
	game.Players.LocalPlayer.Character.FOVMultipliers.FOVSetting.Value = Value	
	end

	local function newspxhakari(state)
		 local char = player.Character or player.CharacterAdded:Wait()
        local humanoid = char:WaitForChild("Humanoid")
        local rootPart = char:WaitForChild("HumanoidRootPart")
    
        hakariactive = state
    
        if hakariactive then
            humanoid.PlatformStand = true
            humanoid.JumpPower = 0
    
            local bodyVelocity = Instance.new("BodyVelocity")
            bodyVelocity.MaxForce = Vector3.new(100000, 100000, 100000)
            bodyVelocity.Velocity = Vector3.zero
            bodyVelocity.Parent = rootPart
    
            local animation = Instance.new("Animation")
            animation.AnimationId = "rbxassetid://138019937280193"
            local animationTrack = humanoid:LoadAnimation(animation)
            animationTrack:Play()
    
            local sound = Instance.new("Sound")
            sound.SoundId = "rbxassetid://109474987384441"
            sound.Parent = rootPart
            sound.Volume = 1
            sound.Looped = true
            sound:Play()
    
            local effect = game.ReplicatedStorage.Assets.Emotes.HakariDance.HakariBeamEffect:Clone()
            effect.Name = "PlayerEmoteVFX"
            effect.CFrame = char.PrimaryPart.CFrame * CFrame.new(0, -1, -0.3)
            effect.WeldConstraint.Part0 = char.PrimaryPart
            effect.WeldConstraint.Part1 = effect
            effect.Parent = char
            effect.CanCollide = false
    
            local args = {
                [1] = "PlayEmote",
                [2] = "Animations",
                [3] = "HakariDance"
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Modules"):WaitForChild("Network"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    
            animationTrack.Stopped:Connect(function()
                humanoid.PlatformStand = false
                if bodyVelocity and bodyVelocity.Parent then
                    bodyVelocity:Destroy()
                end
            end)
        else
            humanoid.PlatformStand = false
            humanoid.JumpPower = 0 
    
            local bodyVelocity = rootPart:FindFirstChildOfClass("BodyVelocity")
            if bodyVelocity then
                bodyVelocity:Destroy()
            end
    
            local sound = rootPart:FindFirstChildOfClass("Sound")
            if sound then
                sound:Stop()
                sound:Destroy()
            end
    
            local effect = char:FindFirstChild("PlayerEmoteVFX")
            if effect then
                effect:Destroy()
            end
    
            for _, track in ipairs(humanoid:GetPlayingAnimationTracks()) do
                if track.Animation.AnimationId == "rbxassetid://138019937280193" then
                    track:Stop()
                end
            end
        end
	end

	local function shuck(state)
		   local char = player.Character or player.CharacterAdded:Wait()
        local humanoid = char:WaitForChild("Humanoid")
        local rootPart = char:WaitForChild("HumanoidRootPart")
    
        sillyactive = state
    
        if sillyactive then
            humanoid.PlatformStand = true
            humanoid.JumpPower = 0
    
            local bodyVelocity = Instance.new("BodyVelocity")
            bodyVelocity.MaxForce = Vector3.new(100000, 100000, 100000)
            bodyVelocity.Velocity = Vector3.zero
            bodyVelocity.Parent = rootPart
    
    
            local animation = Instance.new("Animation")
            animation.AnimationId = "rbxassetid://74238051754912"
            local animationTrack = humanoid:LoadAnimation(animation)
            animationTrack:Play()
    
            local sound = Instance.new("Sound")
            sound.SoundId = "rbxassetid://123236721947419"
            sound.Parent = rootPart
            sound.Volume = 1
            sound.Looped = false
            sound:Play()
    
            local args = {
                [1] = "PlayEmote",
                [2] = "Animations",
                [3] = "Shucks"
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Modules"):WaitForChild("Network"):WaitForChild("RemoteEvent"):FireServer(unpack(args))
    
            animationTrack.Stopped:Connect(function()
                humanoid.PlatformStand = false
                if bodyVelocity and bodyVelocity.Parent then
                    bodyVelocity:Destroy()
                end
            end)
        else
            humanoid.PlatformStand = false
            humanoid.JumpPower = 0
    
            local bodyVelocity = rootPart:FindFirstChildOfClass("BodyVelocity")
            if bodyVelocity then
                bodyVelocity:Destroy()
            end
    
            local sound = rootPart:FindFirstChildOfClass("Sound")
            if sound then
                sound:Stop()
                sound:Destroy()
            end
    
            for _, track in ipairs(humanoid:GetPlayingAnimationTracks()) do
                if track.Animation.AnimationId == "rbxassetid://74238051754912" then
                    track:Stop()
                end
            end
        end
	end

	local function jumplol(state)
		if state then
		game.Players.LocalPlayer.Character.Humanoid.JumpPower = 50
			else
			game.Players.LocalPlayer.Character.Humanoid.JumpPower = 0
		end
	end

	local function invi(state)
	 game.StarterGui:SetCore("SendNotification", {
                Title = "Welcome to Banana invisible Hub!";
                Duration = 5;
                Text = "there you nope";
            })
					local key = Enum.KeyCode.X -- key to toggle invisibility

--// dont edit script below
local invis_on = false
function onKeyPress(inputObject, chat)
    if chat then return end
    if inputObject.KeyCode == key then
	    invis_on = not invis_on
    	if invis_on then
            local savedpos = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
            wait()
            game.Players.LocalPlayer.Character:MoveTo(Vector3.new(-25.95, 84, 3537.55))
            wait(.15)
            local Seat = Instance.new('Seat', game.Workspace)
            Seat.Anchored = false
            Seat.CanCollide = false
            Seat.Name = 'invischair'
            Seat.Transparency = 1
            Seat.Position = Vector3.new(-25.95, 84, 3537.55)
            local Weld = Instance.new("Weld", Seat)
            Weld.Part0 = Seat
            Weld.Part1 = game.Players.LocalPlayer.Character:FindFirstChild("Torso") or game.Players.LocalPlayer.Character.UpperTorso
            wait()
            Seat.CFrame = savedpos
            game.StarterGui:SetCore("SendNotification", {
                Title = "Invis On";
                Duration = 1;
                Text = "";
            })
        else
            workspace:FindFirstChild('invischair'):Remove()
            game.StarterGui:SetCore("SendNotification", {
                Title = "Invis Off";
                Duration = 1;
                Text = "";
            })
        end
    end
end

game:GetService("UserInputService").InputBegan:connect(onKeyPress)
	end

local Button = Tab:CreateButton({
   Name = "copy discord",
   Callback = function(state)
   discord(state)
   end,
})

local Paragraph = Tab:CreateParagraph({Title = "banana hub", Content = "wow how to knife two knife, this look likes good for script, No a isn't, becuase is so good this our script here, to you want this my script :)?, wow how to knife two knife, this look likes good for script, No a isn't, becuase is so good this our script here, to you want this my script :)?, wow how to knife two knife, this look likes good for script, No a isn't, becuase is so good this our script here, to you want this my script :)?, wow how to knife two knife, this look likes good for script, No a isn't, becuase is so good this our script here, to you want this my script :)?, PLEASE JOIN FOR DISCORD NOW!"})

local Toggle = Tab1:CreateToggle({
   Name = "ESP Generator",
   CurrentValue = false,
   --flag = "Toggle1",
   Callback = function(state)
  esp(state)
   end,
})

local Toggle = Tab1:CreateToggle({
   Name = "ESP Item",
   CurrentValue = false,
   --flag = "Toggle1",
   Callback = function(state)
  esp1(state)
   end,
})

local Toggle = Tab1:CreateToggle({
   Name = "ESP c00lkidd",
   CurrentValue = false,
   --flag = "Toggle1",
   Callback = function(state)
  esp2(state)
   end,
})

local Toggle = Tab1:CreateToggle({
   Name = "ESP survivor",
   CurrentValue = false,
   --flag = "Toggle1",
   Callback = function(state)
  esp3(state)
   end,
})

local Toggle = Tab1:CreateToggle({
   Name = "ESP Killers",
   CurrentValue = false,
   --flag = "Toggle1",
   Callback = function(state)
  esp4(state)
   end,
})

local Input = Tab2:CreateInput({
   Name = "Loss Stamina",
   CurrentValue = "",
   PlaceholderText = "10",
   RemoveTextAfterFocusLost = false,
   Callback = function(Value)
   staminaloss(Value)
   end,
})



local Toggle = Tab2:CreateToggle({
   Name = "Loss stamina",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   loss(state)
   end,
})

local Input = Tab2:CreateInput({
   Name = "gain Stamina",
   CurrentValue = "",
   PlaceholderText = "8",
   RemoveTextAfterFocusLost = false,
   Callback = function(Value)
   staminagain(Value)
   end,
})

local Toggle = Tab2:CreateToggle({
   Name = "gain stamina",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   loss(state)
   end,
})

local Input = Tab2:CreateInput({
   Name = "speed Stamina",
   CurrentValue = "",
   PlaceholderText = "26",
   RemoveTextAfterFocusLost = false,
   Callback = function(Value)
   staminaspeed(Value)
   end,
})

local Toggle = Tab2:CreateToggle({
   Name = "speed stamina",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   loss(state)
   end,
})

local Input = Tab2:CreateInput({
   Name = "max Stamina",
   CurrentValue = "",
   PlaceholderText = "50",
   RemoveTextAfterFocusLost = false,
   Callback = function(Value)
   staminamax(Value)
   end,
})

local Toggle = Tab2:CreateToggle({
   Name = "max stamina",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   loss(state)
   end,
})

local Input = Tab2:CreateInput({
   Name = "min Stamina",
   CurrentValue = "",
   PlaceholderText = "100",
   RemoveTextAfterFocusLost = false,
   Callback = function(Value)
   staminaspeed(Value)
   end,
})

local Toggle = Tab2:CreateToggle({
   Name = "min stamina",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   loss(state)
   end,
})

local Divider = Tab2:CreateDivider()
local Section = Tab2:CreateSection("infinite stamina")

local Toggle = Tab2:CreateToggle({
   Name = "infinite stamina",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   inf(state)
   end,
})

local Section = Tab3:CreateSection("c00lkidd")

local Toggle = Tab3:CreateToggle({
   Name = "c00lkidd pizza Animations",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   meme(state)
   end,
})

local Toggle = Tab3:CreateToggle({
   Name = "c00lkidd Animations",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   meme1(state)
   end,
})

local Toggle = Tab3:CreateToggle({
   Name = "killer c00lkidd",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   c00lkidd(state)
   end,
})

local Divider = Tab3:CreateDivider()
local Section = Tab3:CreateSection("John Doe")

local Toggle = Tab3:CreateToggle({
   Name = "killer john doe",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   johndoe(state)
   end,
})

local Toggle = Tab3:CreateToggle({
   Name = "Baby John Doe",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   johndoe1(state)
   end,
})

local Divider = Tab3:CreateDivider()
local Section = Tab3:CreateSection("1x1x1x1")

local Toggle = Tab3:CreateToggle({
   Name = "killer 1x1x1x1",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   p1x1(state)
   end,
})

local Button = Tab3:CreateButton({
   Name = "1x1x1x1 Popups",
   Callback = function()
   p1x1v1()
   end,
})

local Divider = Tab3:CreateDivider()
local Section = Tab3:CreateSection("Jason")

local Toggle = Tab3:CreateToggle({
   Name = "killer jason",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   jason(state)
   end,
})

local Toggle = Tab3:CreateToggle({
   Name = " Auto killer jason",
   CurrentValue = false,
   Flag = "Toggle1",
   Callback = function(state)
   baby(state)
   end,
})

local Section = Tab4:CreateSection("Players Aimbot")

local Dropdown = Tab4:CreateDropdown({
   Name = "Aimbot",
   Options = {"Shedletsky","Two Time","chance","guest1334"},
   CurrentOption = {"Aimbot for Survivor"},
   MultipleOptions = false,
   Callback = function(Options)
 print("you are number =", Options)
   end,
})

local Section = Tab4:CreateSection("This Nomral Players Aimbot")

local Toggle = Tab4:CreateToggle({
   Name = "Sword Shedletsky",
   CurrentValue = false,
   Callback = function(state)
shed(state)
   end,
})

local Toggle = Tab4:CreateToggle({
   Name = "Aimbot Chance",
   CurrentValue = false,
   Callback = function(state)
 chance(state)
   end,
})

local Toggle = Tab4:CreateToggle({
   Name = "Punch Guest1334",
   CurrentValue = false,
   Callback = function(state)
 guest(state)
   end,
})

local Toggle = Tab4:CreateToggle({
   Name = "Knife Two Time",
   CurrentValue = false,
   Callback = function(state)
 twotime1(state)
   end,
})

local Toggle = Tab6:CreateToggle({
   Name = "Update Two Time",
   CurrentValue = false,
   Callback = function(state)
 twotime(state)
   end,
})

local Button = Tab5:CreateButton({
   Name = "Generator 15 seconds",
   Callback = function(state)
second1(state)
   end,
})

local Button = Tab5:CreateButton({
   Name = "Generator 10 seconds",
   Callback = function(state)
second2(state)
   end,
})

local Button = Tab5:CreateButton({
   Name = "Generator 5 seconds",
   Callback = function(state)
second3(state)
   end,
})

local Paragraph = Tab5:CreateParagraph({Title = "Warning Generator", Content = "To not seconds is 2.5 and this is you got banned!"})

local Button = Tab5:CreateButton({
   Name = "instant solvet generator hell",
   Callback = function()
   hell()
   end,
})

local Slider = Tab5:CreateSlider({
   Name = "Generator Seconds",
   Range = {0, 20},
   Increment = 1,
   Suffix = "generator",
   CurrentValue = 1,
  -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
  Value1(Value)
   end,
})

local Button = Tab6:CreateButton({
   Name = "auto tp pizza",
   Callback = function(state)
   givemesomepizza(state)
   end,
})

local Button = Tab6:CreateButton({
   Name = "client unlock all",
   Callback = function(state)
   free(state)
   end,
})

local Divider = Tab6:CreateDivider()

local Input = Tab6:CreateInput({
   Name = "You Heatlh",
   CurrentValue = "",
   PlaceholderText = "who gonna tell bro",
   RemoveTextAfterFocusLost = false,
   --Flag = "Input1",
   Callback = function(Value)
  health(Value)
   end,
})

local Slider = Tab6:CreateSlider({
   Name = "Walkspeed",
   Range = {0, 100},
   Increment = 1,
   Suffix = "speed",
   CurrentValue = 10,
  -- Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
  walkspeed(Value)
   end,
})

local Slider = Tab6:CreateSlider({
   Name = "JumpPower",
   Range = {0, 100},
   Increment = 1,
   Suffix = "jump",
   CurrentValue = 10,
  -- Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
  jumppower(Value)
   end,
})

local Slider = Tab6:CreateSlider({
   Name = "Fov Murit",
   Range = {0, 10},
   Increment = 1,
   Suffix = "fov",
   CurrentValue = 10,
  -- Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
  fov(Value)
   end,
})

local Divider = Tab6:CreateDivider()

local Toggle = Tab6:CreateToggle({
   Name = "shucks Dance",
   CurrentValue = false,
   --Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(state)
  shuck(state)
   end,
})

local Toggle = Tab6:CreateToggle({
   Name = "Hakari Dance",
   CurrentValue = false,
   --Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(state)
  newspxhakari(state)
   end,
})

local Divider = Tab6:CreateDivider()

local Toggle = Tab6:CreateToggle({
   Name = "Jump [Free in Forsaken]",
   CurrentValue = false,
   --Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(state)
  jumplol(state)
   end,
})

local Button = Tab6:CreateButton({
   Name = "FE invisible [KeyBind X]",
   Callback = function(state)
   invi(state)
   end,
})

local Button = Tab6:CreateButton({
   Name = "Anti Ban",
   Callback = function()
   print("ok unban")
   wait(1)
   warn("You are isn't VIP! please using VIP ad you buy this for VIP!")
   end,
})

local Button = Tab6:CreateButton({
   Name = "Anti Kick",
   Callback = function()
   print("ok unkick")
   wait(1)
   warn("You are isn't VIP! please using VIP ad you buy this for VIP!")
   end,
})
