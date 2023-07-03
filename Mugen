---- SERVICES // TEST [MUGEN]

--- ANTI AFK?
repeat wait() until game:IsLoaded()
game:GetService("Players").LocalPlayer.Idled:connect(function()
game:GetService("VirtualUser"):ClickButton2(Vector2.new())
end)

local UIS = game:GetService("UserInputService")
local VirtualUser = game:GetService("VirtualUser")
local VIM =game:GetService("VirtualInputManager")
local ReplStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local Imput = game:GetService("UserInputService")
local COREGUI = game:GetService("CoreGui")
local LP = game:GetService("Players").LocalPlayer
local HttpService = game:GetService("HttpService")
local RunS = game:GetService("RunService")
local X, Y = 0, 0
local Mouse = LP:GetMouse()
local GetLocalName = LP.Name
local request = (syn and syn.request) or (http and http.request) or http_request
local client = game:GetService("Players").LocalPlayer
local Plr = game:GetService("Players").LocalPlayer
local Data = game:GetService("ReplicatedStorage")["Player_Data"][game.Players.LocalPlayer.Name]

local function pressKey(key)
    VIM:SendKeyEvent(true, key, false, game)
    wait()
    VIM:SendKeyEvent(false, key, false, game)
end

local function GetHuman()
    local h = LP.Character
    h = h and (h:FindFirstChild("Humanoid") or h:FindFirstChildWhichIsA("Humanoid"))
    return h or workspace.CurrentCamera.CameraSubject
end

local GramxProjectFloat = tostring(math.random(0, 100000))
local TweenFloatVelocity = Vector3.new(0,0,0)
function CreateTweenFloat()
    local BV = game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild(GramxProjectFloat) or Instance.new("BodyVelocity")
    BV.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart
    BV.Name = GramxProjectFloat
    BV.MaxForce = Vector3.new(100000, 100000, 100000)
    BV.Velocity = TweenFloatVelocity
end


local function GetDistance(Endpoint)
    if typeof(Endpoint) == "Instance" then
    Endpoint = Vector3.new(Endpoint.Position.X, game.Players.LocalPlayer.Character.HumanoidRootPart.Position.Y, Endpoint.Position.Z)
    elseif typeof(Endpoint) == "CFrame" then
    Endpoint = Vector3.new(Endpoint.Position.X, game.Players.LocalPlayer.Character.HumanoidRootPart.Position.Y, Endpoint.Position.Z)
    end
    local Magnitude = (Endpoint - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
    return Magnitude
end


function Tween(Endpoint)
    if typeof(Endpoint) == "Instance" then
    Endpoint = Endpoint.CFrame
    end
    local TweenFunc = {}
    local Distance = GetDistance(Endpoint)
    local TweenInfo = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart, TweenInfo.new(Distance/getgenv().TweenSpeed, Enum.EasingStyle.Linear), {CFrame = Endpoint * CFrame.fromAxisAngle(Vector3.new(1,0,0), math.rad(0))})
    TweenInfo:Play()
    function TweenFunc:Cancel()
    TweenInfo:Cancel()
    return false
    end
    if Distance <= 100 then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Endpoint
    TweenInfo:Cancel()
    return false
    end
    return TweenFunc
end


function RemoveDMG()
   local part  =  game:GetService("StarterPlayer").StarterPlayerScripts.Client_Modules.Modules.Extra.Damage_Text

   local part1 =  game:GetService("ReplicatedStorage").Assets.Extras.Damage_Text

   local part2 = game:GetService("Players").LocalPlayer.PlayerScripts.Client_Modules.Modules.Extra.Damage_Text

   if part then
       part:Destroy()
   end

   if part1 then
       part1:Destroy()
   end

   if part2 then
       part2:Destroy()
   end
end

function RemovePARTICLES()
   local COINS = game:GetService("ReplicatedStorage").Assets.Extras.Coin

   local PARTICLES = game:GetService("ReplicatedStorage").Assets.Particles.Parts

   if COINS then
       COINS:Destroy()
   end

   if PARTICLES then
       PARTICLES:Destroy()
   end
end

-- // AUTO CLASH - FARM
	
spawn(function()
    while task.wait() do
        pcall(function()
            if AutoClash then
                pressKey(Enum.KeyCode[game.Players.LocalPlayer.PlayerGui["universal_client_scripts"].Clashing2["Clash_Ui2"].Holder:WaitForChild('Front').Text])
            end
        end)
    end
end)

function Hop()
    local PlaceID = game.PlaceId
    local AllIDs = {}
    local foundAnything = ""
    local actualHour = os.date("!*t").hour
    local Deleted = false
    function TPReturner()
        local Site;
        if foundAnything == "" then
            Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
        else
            Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
        end
        local ID = ""
        if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
            foundAnything = Site.nextPageCursor
        end
        local num = 0;
        for i,v in pairs(Site.data) do
            local Possible = true
            ID = tostring(v.id)
            if tonumber(v.maxPlayers) > tonumber(v.playing) then
                for _,Existing in pairs(AllIDs) do
                    if num ~= 0 then
                        if ID == tostring(Existing) then
                            Possible = false
                        end
                    else
                        if tonumber(actualHour) ~= tonumber(Existing) then
                            local delFile = pcall(function()
                                AllIDs = {}
                                table.insert(AllIDs, actualHour)
                            end)
                        end
                    end
                    num = num + 1
                end
                if Possible == true then
                    table.insert(AllIDs, ID)
                    wait()
                    pcall(function()
                        wait()
                        game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
                    end)
                    wait(4)
                end
            end
        end
    end
    function Teleport() 
        while wait() do
            pcall(function()
                TPReturner()
                if foundAnything ~= "" then
                    TPReturner()
                end
            end)
        end
    end
    Teleport()
end

local function SkillBind(bind)
    pcall(function()
        VIM:SendKeyEvent(true,bind,false,game)
        task.wait()
        VIM:SendKeyEvent(false,bind,false,game)
        wait(.2)
    end)
end
--------- SERVICES // TABLES	

local TrainersCF = {
    ["Water Trainer"] = CFrame.new(705.209229, 261.426819, -2409.51587, -0.566798735, -5.48522401e-08, -0.641887605, -7.38932258e-08, 1, 2.8182352e-09, 0.641887605, 4.95921633e-08, -0.566798735),
    ["Insect Trainer"] = CFrame.new(2873.81177, 316.95871, -3917.9397, 0.40715313, 4.81208531e-08, 0.91335988, -8.85969982e-08, 1, -1.31911939e-08, -0.91335988, -7.55501048e-08, 0.40715313),
    ["Thunder Trainer"] = CFrame.new(-322.369507, 426.857788, -2384.4021, 0.361198723, -4.49157973e-08, -0.932488859, 1.14233451e-07, 1, -3.91942434e-09, 0.932488859, -1.05105727e-07, 0.361198723),
    ["Wind Trainer"] = CFrame.new(1792.31458, 334.338989, -3521.31104, 0.862527311, -5.19402583e-08, -0.506010473, 8.30083167e-08, 1, 3.88463874e-08, 0.506010473, -7.55091492e-08, 0.862527311)
}

local Locations = {
    ["Zapiwara Mountain"] = CFrame.new(-365.617981, 425.857422, -2303.92285, -0.351566792, -6.70503529e-13, 0.93616277, 9.77098068e-13, 1, 1.08316502e-12, -0.93616277, 1.2955277e-12, -0.351566792),
    ["Waroru Cave"] = CFrame.new(683.164062, 261.426819, -2401.41797, 0.137014925, -3.46316149e-08, 0.990568995, 6.38769482e-09, 1, 3.4077793e-08, -0.990568995, 1.65828595e-09, 0.137014925),
    ["Slasher Demon"] = CFrame.new(-485.866608, 274.511871, -3314.98169, -0.79503566, -1.09233929e-08, -0.606562674, 1.19430055e-09, 1, -1.95740775e-08, 0.606562674, -1.62865081e-08, -0.79503566),
    ["Ushumaru Village"] = CFrame.new(-90.0373688, 354.723511, -3170.00439, 0.817297578, -1.0121405e-08, 0.576215804, 3.12666586e-08, 1, -2.6782951e-08, -0.576215804, 3.99059843e-08, 0.817297578),
    ["Ouwbayashi Home"] = CFrame.new(1593.49072, 315.983917, -4618.15088, -0.795035839, -1.09234e-08, -0.606562734, 1.19429622e-09, 1, -1.95740828e-08, 0.606562734, -1.62865081e-08, -0.795035839),
    ["Kabiwaru Village"] = CFrame.new(2037.20203, 315.908813, -2956.77539, -0.795035839, -1.09234e-08, -0.606562734, 1.19429622e-09, 1, -1.95740828e-08, 0.606562734, -1.62865081e-08, -0.795035839),
    ["Zapiwara Cave"] = CFrame.new(-8.2838707, 275.944641, -2414.72607, -0.795035779, -1.09233964e-08, -0.606562555, 1.19429289e-09, 1, -1.95740775e-08, 0.606562555, -1.62865046e-08, -0.795035779),
    ["Dangerous Woods"] = CFrame.new(4061.43677, 342.289581, -3928.90332, -0.795035839, -1.09233973e-08, -0.606562614, 1.19429444e-09, 1, -1.95740775e-08, 0.606562614, -1.62865064e-08, -0.795035839),
    ["Final Selection"] = CFrame.new(5200.76709, 365.949982, -2425.61646, -0.795035779, -1.09233964e-08, -0.606562555, 1.19429289e-09, 1, -1.95740775e-08, 0.606562555, -1.62865046e-08, -0.795035779),
    ["Kiribating Village"] = CFrame.new(-40.3280869, 282.282745, -1623.75159, -0.795035839, -1.09233991e-08, -0.606562614, 1.19429266e-09, 1, -1.95740792e-08, 0.606562614, -1.62865046e-08, -0.795035839),
    ["Butterfly Mansion"] = CFrame.new(3022.90869, 316.075623, -3928.17261, -0.795035779, -1.09233982e-08, -0.606562555, 1.19429144e-09, 1, -1.95740775e-08, 0.606562555, -1.62865046e-08, -0.795035779),
    ["Abubu Cave"] = CFrame.new(1044.44873, 276.190704, -3483.0647, -0.795035839, -1.09233991e-08, -0.606562614, 1.19429266e-09, 1, -1.95740792e-08, 0.606562614, -1.62865046e-08, -0.795035839),
    ["Testing Place"] = CFrame.new(-32, 3, 137)
}

local BossessTable = {"Sabito", "Susamaru", "Zanegutsu Kuuchie", "Yahaba", "Bandit Kaden", "Bandit Zoku", "Shiron", "Nezuko", "Slasher", "Giyu", "Sanemi"}
local bosCFTable = {
    ["Susamaru"] = CFrame.new(1415.65686, 315.908813, -4571.56445, 0.546769679, 9.56999102e-08, -0.837283075, -3.89699188e-08, 1, 8.88496885e-08, 0.837283075, -1.59514606e-08, 0.546769679),
    ["Sabito"] = CFrame.new(1257.60046, 275.351685, -2834.26611, -0.999906898, 0, 0.0136531433, 0, 1, 0, -0.0136531433, 0, -0.999906898),
    ["Zanegutsu Kuuchie"] = CFrame.new(-336.3461, 425.857422, -2271.75513, -0.698250651, 1.51218398e-08, 0.715853333, -2.08847464e-08, 1, -4.1495408e-08, -0.715853333, -4.39246115e-08, -0.698250651),
    ["Yahaba"] = CFrame.new(1415.65686, 315.908813, -4571.56445, 0.546769679, 9.56999102e-08, -0.837283075, -3.89699188e-08, 1, 8.88496885e-08, 0.837283075, -1.59514606e-08, 0.546769679),
    ["Bandit Kaden"] = CFrame.new(-569.584351, 304.46698, -2827.55371, 0.480675608, -1.73434103e-08, 0.876898468, 1.14556499e-07, 1, -4.30165024e-08, -0.876898468, 1.21131407e-07, 0.480675608),
    ["Shiron"] = CFrame.new(3203.10229, 370.884155, -3953.36035, 0.839348018, 3.06273158e-08, -0.54359442, -9.09106301e-09, 1, 4.23049826e-08, 0.54359442, -3.05667527e-08, 0.839348018),
    ["Nezuko"] = CFrame.new(3549.86816, 342.214478, -4595.73145, 0.869256139, 6.38721716e-08, -0.494362026, -6.77404373e-08, 1, 1.00905426e-08, 0.494362026, 2.47170338e-08, 0.869256139),
    ["Bandit Zoku"] = CFrame.new(174.656708, 283.257355, -1969.98572, -0.814278841, -6.32300328e-08, 0.5804739, -9.84254598e-08, 1, -2.91412618e-08, -0.5804739, -8.08625273e-08, -0.814278841),
    ["Slasher"] =  CFrame.new(4355.59082, 342.214478, -4386.90527, -0.943093359, 9.45450722e-08, -0.332528085, 7.62970487e-08, 1, 6.79336054e-08, 0.332528085, 3.86968253e-08, -0.943093359),
    ["Giyu"] = CFrame.new(3013.30884, 316.95871, -2916.32202, 0.76092875, 3.55993954e-08, 0.648835421, -1.75982926e-08, 1, -3.4228016e-08, -0.648835421, 1.46266848e-08, 0.76092875),
    ["Sanemi"] = CFrame.new(1619.91357, 348.461884, -3717.00464, 0.995524168, -1.20393835e-07, 0.0945073739, 1.19773844e-07, 1, 1.22327712e-08, -0.0945073739, -8.58508931e-10, 0.995524168)
}

--------- SERVICES // KA

local function attack(method)

    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, 919, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, math.huge, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, 919, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, math.huge, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, 919, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, math.huge, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, 919, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, math.huge, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, 919, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, math.huge, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, 919, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, math.huge, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, 919, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, math.huge, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, 919, "ground_slash")
    wait()
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(method, client, client.Character, client.Character.HumanoidRootPart, client.Character.Humanoid, math.huge, "ground_slash")

end

local attackMethods = {
    ["Combat"] = 'fist_combat',
    ["Sword"] = 'Sword_Combat_Slash',
    ["Scythe"] = 'Scythe_Combat_Slash',
    ["Claw"] = 'claw_Combat_Slash',
    ["Fans"] = 'fans_combat_slash'
}

if game.ReplicatedStorage:FindFirstChild("Remotes"):FindFirstChild("getclientping") then 
    game.ReplicatedStorage:FindFirstChild("Remotes"):FindFirstChild("getclientping").OnClientInvoke = function() 
        task.wait(5)
        return true 
    end 
end 

-- // FARM METHOD
spawn(function()
   while wait() do
       pcall(function()
           SkillActive = AutoUseSkills and (FarmBoss and NearestMobs) or AutoUseSkills and (FarmQuest and NearestMobs) or AutoUseSkills and (FarmMob and NearestMobs) or AutoUseSkills and (AllBosses and NearestMobs)
           if FarmMethod == "Above" then
               FarmModes = CFrame.new(0,getgenv().Distance,0) * CFrame.Angles(math.rad(-90),0,0) 
           elseif FarmMethod == "Below" then
               FarmModes = CFrame.new(0,-getgenv().Distance,0) * CFrame.Angles(math.rad(90),0,0)
           elseif FarmMethod == "Behind" then
               FarmModes = CFrame.new(0,0,getgenv().Distance)
           elseif FarmMethod == "Front" then
               FarmModes = CFrame.new(0,0,-getgenv().Distance)
           end
           for i,v in pairs(LP.PlayerGui.MainGuis.Items.Scroll:GetChildren()) do
               Insert = true
               if v.ClassName == "Frame" and v.Name ~= "Health Elixir" and v.Name ~= "Health Regen Elixir" and v.Name ~= "Stamina Elixir" and v.Name ~= "Bandage" then
                   for i,v2 in pairs(invTable) do if v2 == v.Name then Insert = false end end
                   if Insert == true then table.insert(invTable, v.Name) end
               end
           end
       end)
   end
  end)

-- // NO CLIP

spawn(function()
   game:GetService("RunService").Stepped:Connect(function()
       if getgenv().AllBosses or TPtoLocation or TPtoTrainer or getgenv().GotoMuzan or FarmBoss then
           for _, v in pairs(game:GetService("Players").LocalPlayer.Character:GetDescendants()) do
               if v:IsA("BasePart") then
                   v.CanCollide = false    
               end
               if v:IsA("Humanoid") then
                   v:ChangeState(11)
               end
           end
       end
   end)
end)


--------- SERVICES // ANTI AFK

local vu = game:GetService("VirtualUser")
game:GetService("Players").LocalPlayer.Idled:connect(function()
   vu:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
   wait(1)
   vu:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
end)
game.NetworkClient.ChildRemoved:Connect(function()
  game:GetService("TeleportService"):Teleport(5956785391)
end)
game:GetService("CoreGui").RobloxPromptGui.promptOverlay.ChildAdded:Connect(function(child)
    if child.Name == 'ErrorPrompt' and child:FindFirstChild('MessageArea') and child.MessageArea:FindFirstChild("ErrorFrame") then
        game:GetService("TeleportService"):Teleport(5956785391)
    end
end)

-- // KILL AURA - FARM
	
local killAuraWait = 1.25  -- Initial value for Kill Aura wait time

task.spawn(function()
    while task.wait() do
        pcall(function()
            if getgenv().KillAura then
                attack(attackMethods[Method])
                task.wait(killAuraWait)  -- Use the updated Kill Aura wait time
                repeat
                    wait()
                until game.Players.LocalPlayer:WaitForChild("combotangasd123").Value == 0
            end
        end)
    end
end)

local function GetNearestBoss()
        
   local Bosses = game:GetService("Workspace").Mobs:GetDescendants()
   local BossesTable = {}

   for i,v in pairs(Bosses) do
       if v:IsA("Model") and v:FindFirstChild("Humanoid") then
           if v.Humanoid.Health > 0 then
               table.insert(BossesTable, v)
           end
       end
   end

   local NearestBoss = nil
   local NearestBossDistance = math.huge

   for i,v in pairs(BossesTable) do
       local Distance = GetDistance(v:GetModelCFrame() * FarmModes)
       if Distance < NearestBossDistance then
           NearestBoss = v
           NearestBossDistance = Distance
       end
   end

   return NearestBoss
end

-- // AUTO ALL BOSSES - FARM
	
spawn(function()
   while task.wait() do
      pcall(function()
         if getgenv().AllBosses then

            if not LP.Character.HumanoidRootPart:FindFirstChild("BodyVelocity") then
               antifall3 = Instance.new("BodyVelocity", LP.Character.HumanoidRootPart)
               antifall3.Velocity = Vector3.new(0, 0, 0)
               antifall3.MaxForce = Vector3.new(9e9, 9e9, 9e9)
            elseif LP.Character.HumanoidRootPart:FindFirstChild("BodyVelocity") then
               local v = GetNearestBoss()
               
                     if v then
                        repeat task.wait()                                      
                           if GetDistance(v:GetModelCFrame() * FarmModes) < 25 and GetDistance(v:GetModelCFrame() * FarmModes) < 150 then
                              if TweenFa then
                              TweenFa:Cancel()
                              wait(.1)
                              end
                              LP.Character.HumanoidRootPart.CFrame = v:GetModelCFrame() * FarmModes
                           else
                              TweenFa = Tween(v:GetModelCFrame() * FarmModes)
                           end
                           if v.Humanoid.Health > 0 and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and GetDistance(v:GetModelCFrame() * FarmModes) < 10 then
                              NearestMobs = true
                           elseif v.Humanoid.Health <= 0 or not v:FindFirstChild("Humanoid") and GetDistance(v:GetModelCFrame() * FarmModes) > 10 then
                              NearestMobs = false
                           end
                        until not getgenv().AllBosses or not v.Parent or v.Humanoid.Health <= 0 or not v:IsDescendantOf(workspace)
                        NearestMobs = false
               end
            end
         else
            antifall3:Destroy()
         end
         if getgenv().AllBosses == false then
            TweenFa:Cancel()
         end
      end)
   end
end)

-- // AUTO COLLECT CHESTS - FARM
	
spawn(function()
   while task.wait() do
      if AutoCollectChest then
         for _, v in pairs(game:GetService("Workspace").Debree:GetChildren()) do
            if v.Name == "Loot_Chest" then
               for _, c in pairs(v:FindFirstChild("Drops"):GetChildren()) do
                  v["Add_To_Inventory"]:InvokeServer(c.Name)
                  delay(0.1, function()
                     c:Destroy()
                  end)
               end
         end
      end
   end
   end
end)

 spawn(function()
     while task.wait() do
         if AutoCollectChestv2 then
             for _, v in pairs(game:GetService("Workspace").Debree:GetChildren()) do
                 if v.Name == "Loot_Chest" and v:FindFirstChild("Drops") then
                     if #v.Drops:GetChildren() == 0 then
                         v:Destroy()
                     else
                         for _, drop in pairs(v.Drops:GetChildren()) do
                             local args = {
                                 [1] = drop.Name
                             }
 
                             v.Add_To_Inventory:InvokeServer(unpack(args))
                             if #v.Drops:GetChildren() == 0 then
                                 v:Destroy()
                             end
                         end
                     end
                 end
             end
         end
     end
 end)    

 local function sendWebhook(itemName)
   local payload = {
       ["content"] = "",
       ["embeds"] = {{
           ["title"] = "**Item Obtained!**",
           ["description"] = game.Players.LocalPlayer.DisplayName .. " obtained the item: " .. itemName,
           ["type"] = "rich",
           ["color"] = tonumber(0xffffff),
           ["fields"] = {
               {
                   ["name"] = "Hardware ID:",
                   ["value"] = "Unknown", -- Replace with the hardware ID retrieval method suitable for Fluxus
                   ["inline"] = true
               }
           }
       }}
   }

   local headers = {
       ["Content-Type"] = "application/json"
   }

   local requestBody = game:GetService("HttpService"):JSONEncode(payload)

   local response = http_request({
       Url = WebhookURL,
       Method = "POST",
       Headers = headers,
       Body = requestBody
   })
end

spawn(function()
   while true do
       if AutoCollectChestv3 then
           for _, v in pairs(game:GetService("Workspace").Debree:GetChildren()) do
               if v.Name == "Loot_Chest" and v:FindFirstChild("Drops") then
                   if #v.Drops:GetChildren() == 0 then
                       v:Destroy()
                   else
                       for _, drop in pairs(v.Drops:GetChildren()) do
                           local args = {
                               [1] = drop.Name
                           }

                           v.Add_To_Inventory:InvokeServer(unpack(args))
                           if #v.Drops:GetChildren() == 0 then
                               v:Destroy()
                           end

                           sendWebhook(drop.Name)
                       end
                   end
               end
           end
       end
       wait()
   end
end)

-- // AUTO EAT SOULS - FARM

spawn(function()
   while task.wait() do
      if AutoEatSouls then
         for i,v in pairs(game:GetService("Workspace").Debree:GetChildren()) do
            if v.Name == "Soul" then
               pcall(function()
                  workspace.Debree.Soul.Handle.Eatthedamnsoul:FireServer()
               end)
            end
         end
      end
   end
end)

------ LIBRARY
local repo = 'https://raw.githubusercontent.com/wally-rblx/LinoriaLib/main/'
local Library = loadstring(game:HttpGet(repo .. 'Library.lua'))()
local ThemeManager = loadstring(game:HttpGet('https://raw.githubusercontent.com/NovazUwU/SharkHub/main/Theme'))()
local SaveManager = loadstring(game:HttpGet(repo .. 'addons/SaveManager.lua'))()

local Window = Library:CreateWindow({
    Title = 'Shark Hub v2 PREMIUM // By ImperorLegend // Mugen',
    Center = true,
    AutoShow = true,
})


local Tabs = {
   Main = Window:AddTab('Project Slayers'),
   Misc = Window:AddTab('Misc'),
   Teleports = Window:AddTab('Teleports'),
   Mugen = Window:AddTab('Mugen'),
   ['Settings'] = Window:AddTab('Settings'),

}

local Mugen = Tabs.Mugen:AddLeftGroupbox('        [Mugen]')
local Test = Tabs.Misc:AddLeftGroupbox('              [Misc]')
local LeftGroupBox = Tabs.Main:AddLeftGroupbox('           [Auto Farms]')
local RightGroupBox = Tabs.Main:AddRightGroupbox('            [Status]')
local RightGroupBox2 = Tabs.Main:AddRightGroupbox('            [ Webhook ]')
local LeftGroupBox2 = Tabs.Main:AddLeftGroupbox('           [Auto Farms]')
local LeftGroupBox5 = Tabs.Main:AddLeftGroupbox('           [Auto Gourd]')
local RightGroupBox3 = Tabs.Main:AddRightGroupbox('           [Auto Skills]')
local RightGroupBox4 = Tabs.Main:AddRightGroupbox('            [Other]')
local Test2 = Tabs.Misc:AddLeftGroupbox('            [Training]')
local Test3 = Tabs.Misc:AddLeftGroupbox('             [Modes]')
local Test4 = Tabs.Misc:AddRightGroupbox('        [God Modes (DEMON)]')
local Test5 = Tabs.Misc:AddRightGroupbox('  [God Modes (SLAYER/HUMAN)]')
local Shark1 = Tabs.Teleports:AddLeftGroupbox('            [TELEPORTS]')
local Sharky1 = Tabs.Teleports:AddRightGroupbox('            [SERVERS]')
local Shark2 = Tabs.Misc:AddRightGroupbox('       [Auto Collect Lily]')
local Shark3 = Tabs.Misc:AddRightGroupbox('       [Some Stuffs]')

LeftGroupBox:AddButton("Cracked By Novaz | gg/EEzVUN35R", function()
    setclipboard("https://discord.gg/EEzVUN35R") 
end)

getgenv().Method = "Sword"
LeftGroupBox:AddDropdown('KillAura', {
    Values = { 'Sword', 'Combat', 'Scythe', 'Claw', 'Fans' },
    Default = 1, -- number index of the value / string
    Multi = false, -- true / false, allows multiple choices to be selected
    Text = 'Kill Aura Method',
    Tooltip = 'Select Kill Aura Method', -- Information shown when you hover over the textbox
    Callback = function(self)
		getgenv().Method = self
    end
 })
 
 getgenv().FarmMethod = "Above"
 LeftGroupBox:AddDropdown('FarmMethod', {
    Values = { 'Above', 'Below', 'Behind', 'Front' },
    Default = 1, -- number index of the value / string
    Multi = false, -- true / false, allows multiple choices to be selected
    Text = 'Farm Method',
    Tooltip = 'Select Farm Method', -- Information shown when you hover over the textbox
    Callback = function(self)
		getgenv().FarmMethod = self
    end
 })

 getgenv().TweenSpeed = 100
 LeftGroupBox:AddSlider('MySlider', {
    Text = 'Tween Speed',
    Default = 100,
    Min = 10,
    Max = 500,
    Rounding = 10,
    Compact = false,
    Callback = function(self)
		getgenv().TweenSpeed = self
    end
})

getgenv().Distance = 5
LeftGroupBox:AddSlider('MySlider2', {
    Text = 'Farm Distance',
    Default = 5,
    Min = 1,
    Max = 10,
    Rounding = 1,
    Compact = false,
    Callback = function(self)
		getgenv().Distance = self
    end
})

LeftGroupBox:AddDivider()

LeftGroupBox:AddToggle('RemoveDMG', {
   Text = 'Remove Damage Text',
   Default = false, -- Default value (true / false)
   Tooltip = 'Remove Damage Text', -- Information shown when you hover over the toggle
   Callback = function()
      RemoveDMG()
   end
})

LeftGroupBox:AddToggle('RemovePARTICLES', {
   Text = 'Remove Particles',
   Default = false, -- Default value (true / false)
   Tooltip = 'Remove Particles', -- Information shown when you hover over the toggle
   Callback = function()
      RemovePARTICLES()
   end
})

LeftGroupBox2:AddToggle('FarmBosses', {
    Text = 'Farm Mugen',
    Default = false, -- Default value (true / false)
    Tooltip = 'Kill Aura', -- Information shown when you hover over the toggle
    Callback = function(value)
        getgenv().AllBosses = value
    end
})

local UserInputService = game:GetService("UserInputService")
local ContextActionService = game:GetService("ContextActionService")
local mouseEnabled = true

-- Function to disable the mouse clicks
local function DisableMouseClicks()
    mouseEnabled = false
    ContextActionService:BindAction("DisableMouseClicks", function() end, false, Enum.UserInputType.MouseButton1, Enum.UserInputType.MouseButton2)
end

-- Function to enable the mouse clicks
local function EnableMouseClicks()
    mouseEnabled = true
    ContextActionService:UnbindAction("DisableMouseClicks")
end

LeftGroupBox2:AddToggle('Ignore', {
    Text = 'Disable Mouse',
    Default = false, -- Default value (true / false)
    Tooltip = 'Disable Mouse [Use this before using Kill Aura]', -- Information shown when you hover over the toggle
    Callback = function(value)
        if value then
            DisableMouseClicks()
        else
            EnableMouseClicks()
        end
    end
})

-- Check mouse input and allow or deny based on mouseEnabled variable
UserInputService.InputBegan:Connect(function(input)
    if not mouseEnabled and (input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.MouseButton2) then
        return
    end
    -- Handle other input events as desired
end)

LeftGroupBox2:AddToggle('KillAura', {
   Text = 'Kill Aura',
   Default = false, -- Default value (true / false)
   Tooltip = 'Kill Aura', -- Information shown when you hover over the toggle
   Callback = function(value)
       getgenv().KillAura = value
   end
})


local firing = false -- Variable to track the state

LeftGroupBox2:AddToggle('BypassGKA', {
    Text = 'Bypass GKA (ARROW) [USE THIS FIRST]',
    Default = false,
    Tooltip = 'Bypass GKA',
    Callback = function(state)
        firing = state -- Update the firing state

        if firing then -- Start the loop only if firing is true
            while firing do -- Loop while firing is true
                local Handle_Initiate_S_ = game.ReplicatedStorage.Remotes.To_Server.Handle_Initiate_S_
                Handle_Initiate_S_:InvokeServer("skil_ting_asd", game.Players.LocalPlayer, "arrow_knock_back", 5)
                wait(14)
            end
        end
    end
})

local running = false -- Variable to track the state

LeftGroupBox2:AddToggle('GKAareroWeeW', {
    Text = 'Global Kill Aura (HELL MODE)',
    Default = false,
    Tooltip = 'Global Kill Aura (SAFEST)',
    Callback = function(state)
        running = state -- Update the running state

        if running then -- Start the loop only if running is true
            while running do -- Loop while running is true
                local success, error = pcall(function()
                    local hitCounter = {} -- Counter for each model

                    for i, v in next, workspace.Mobs:GetDescendants() do
                        if v:IsA("Model") and v:FindFirstChild("HumanoidRootPart") then
                            local modelId = v:GetFullName()

                            -- Check if the model has a counter and initialize it if not present
                            if not hitCounter[modelId] then
                                hitCounter[modelId] = 0
                            end

                            -- Check if the model has been hit less than 2 times
                            if hitCounter[modelId] < 2 then
                                local humanoid = v:FindFirstChildOfClass("Humanoid")
                                if humanoid and humanoid.Health > 0 then
                                    local Handle_Initiate_S_ = game.ReplicatedStorage.Remotes.To_Server.Handle_Initiate_S_
                                    Handle_Initiate_S_:InvokeServer("arrow_knock_back_damage", game.Players.LocalPlayer.Character, v.HumanoidRootPart.CFrame, v, 500, 500)
                                    hitCounter[modelId] = hitCounter[modelId] + 1
                                else
                                    -- The humanoid health is 0, change to another model
                                    -- Replace the code below with the logic to change the model
                                    print("Model with health 0:", modelId)
                                end
                            end

                            -- Check if we hit two mobs/models
                            local hitCount = 0
                            for _, count in pairs(hitCounter) do
                                hitCount = hitCount + count
                            end
                            if hitCount >= 2 then
                                break -- Exit the loop if we hit two mobs/models
                            end
                        end
                    end
                end)

                if not success then
                    print("An error occurred:", error)
                end

                -- Add a delay between iterations to prevent excessive server load
                wait() -- Adjust the delay time as desired
            end
        end
    end
})


LeftGroupBox2:AddToggle('BypassTGKA', {
    Text = 'Bypass THUNDER KA [USE THIS FIRST]',
    Default = false,
    Tooltip = 'Bypass GKA',
    Callback = function(state)
        firing = state -- Update the firing state
        if firing then -- Start the loop only if firing is true
            while firing do -- Loop while firing is true
                local args = {
                    [1] = "skil_ting_asd",
                    [2] = game:GetService("Players").LocalPlayer,
                    [3] = "Thunderbreathingrapidslashes",
                    [4] = 5
                }
                
                game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(unpack(args))                 
                wait(14)
            end
        end
    end
})

local TKA = false

LeftGroupBox2:AddToggle('TKA', {
    Text = 'Thunder Kill Aura',
    Default = false,
    Callback = function(state)
        TKA = state
        while TKA do
            local args = {
                [1] = "ricespiritdamage",
                [2] = game:GetService("Players").LocalPlayer.Character,
                [3] = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame,
                [4] = 300
            }

            game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S_:InvokeServer(unpack(args))
            wait(0.85)
        end
    end
})

LeftGroupBox:AddSlider('KASlider', {
    Text = 'Kill Aura',
    Default = 1.25,
    Min = 0.25,
    Max = 5,
    Rounding = 1,
    Compact = false,
    Callback = function(self)
        killAuraWait = self.Value 
    end
})

LeftGroupBox2:AddToggle('AutoCollectChestv1', {
    Text = 'Auto Collect Chest v1',
    Default = false, -- Default value (true / false)
    Tooltip = 'Auto Collect Chest (Will Not Remove Chest After Collecting)', -- Information shown when you hover over the toggle
    Callback = function(value)
      getgenv().AutoCollectChest = value
    end
})

LeftGroupBox2:AddToggle('AutoCollectChestv2', {
   Text = 'Auto Collect Chest v2',
   Default = false, -- Default value (true / false)
   Tooltip = 'Auto Collect Chest (Will Remove Chest After Collecting)', -- Information shown when you hover over the toggle
   Callback = function(value)
     getgenv().AutoCollectChestv2 = value
   end
})



spawn(function()
    while task.wait() do
        if getgenv().AutoBlock then
            local args = {
                [1] = "add_blocking",
                [3] = 11565.6265117,
                [4] = game:GetService("ReplicatedStorage").PlayerValues[game.Players.LocalPlayer.Name],
                [5] = math.huge
            }
            game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(unpack(args))
        end
    end
end)

LeftGroupBox2:AddToggle('AutoBlock', {
    Text = 'Auto Block [No Skills]',
    Default = false,
    Tooltip = 'Auto Block [No Skills]',
    Callback = function(value)
        if value then
            getgenv().AutoBlock = true
        else
            getgenv().AutoBlock = false
            local args = {
                [1] = "remove_blocking",
                [2] = game:GetService("ReplicatedStorage"):WaitForChild("PlayerValues"):WaitForChild(game.Players.LocalPlayer.Name)
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S_"):InvokeServer(unpack(args))
        end
    end
})

LeftGroupBox2:AddToggle('AutoEatSouls', {
   Text = 'Auto Eat Souls [Demon]',
   Default = false, -- Default value (true / false)
   Tooltip = 'Auto Eat Souls [Demon]', -- Information shown when you hover over the toggle
   Callback = function(value)
      getgenv().AutoEatSouls = value
   end
})

LeftGroupBox5:AddToggle('ToggleGourd', {
   Text = 'Enable Auto Gourd',
   Default = false, -- Default value (true / false)
   Callback = function(v)
       getgenv().AutoBlowGourd = v
   end
})

getgenv().GourdSelect = "Small Gourd"
LeftGroupBox5:AddDropdown('Gourd', {
   Values = { 'Small Gourd', 'Medium Gourd', 'Big Gourd' },
   Default = 1, -- number index of the value / string
   Multi = false, -- true / false, allows multiple choices to be selected
   Text = 'Auto Gourd',
   Tooltip = 'Auto Gourd [MUST NOT HAVE ANY GOURDS IN THE INVENTORY]', -- Information shown when you hover over the textbox
   Callback = function(v)
       getgenv().GourdSelect = v
   end
})

-- AUTO GOURD - GOURDS
task.spawn(function()
   while true do
       if getgenv().AutoBlowGourd then
           local Players = game:GetService("Players")
           local ReplicatedStorage = game:GetService("ReplicatedStorage")

           local function invokeServer(...)
               return ReplicatedStorage.Remotes.To_Server.Handle_Initiate_S_:InvokeServer(...)
           end

           local LocalPlayer = Players.LocalPlayer
           local Data = ReplicatedStorage.Player_Data[LocalPlayer.Name]

           if getgenv().GourdSelect == "Big Gourd" and Data.Yen.Value >= 700 then
               invokeServer("buysomething", LocalPlayer.Name, "Big Gourd", Data.Yen, Data.Inventory)
               wait(1)
               invokeServer("change_equip_for_item", LocalPlayer.Name, Data.Inventory, Data.Inventory.Items:FindFirstChild("Big Gourd"))
               wait(1)
               for _, v in pairs(LocalPlayer.Backpack:GetChildren()) do
                   if v.Name == "Big Gourd" then
                       v.Parent = LocalPlayer.Character
                   end
               end
               wait(1)

               while true do
                   local BigGourd = LocalPlayer.Character:FindFirstChild("Big Gourd")
                   if BigGourd then
                       invokeServer("blow_in_gourd_thing", LocalPlayer, BigGourd, 1)
                   else
                       break
                   end
                   wait()
               end
           elseif getgenv().GourdSelect == "Medium Gourd" and Data.Yen.Value >= 450 then
               invokeServer("buysomething", LocalPlayer.Name, "Medium Gourd", Data.Yen, Data.Inventory)
               wait(1)
               invokeServer("change_equip_for_item", LocalPlayer.Name, Data.Inventory, Data.Inventory.Items:FindFirstChild("Medium Gourd"))
               wait(1)
               for _, v in pairs(LocalPlayer.Backpack:GetChildren()) do
                   if v.Name == "Medium Gourd" then
                       v.Parent = LocalPlayer.Character
                   end
               end
               wait(1)

               while true do
                   local MediumGourd = LocalPlayer.Character:FindFirstChild("Medium Gourd")
                   if MediumGourd then
                       invokeServer("blow_in_gourd_thing", LocalPlayer, MediumGourd, 1)
                   else
                       break
                   end
                   wait()
               end
           elseif getgenv().GourdSelect == "Small Gourd" and Data.Yen.Value >= 200 then
               invokeServer("buysomething", LocalPlayer.Name, "Small Gourd", Data.Yen, Data.Inventory)
               wait(1)
               invokeServer("change_equip_for_item", LocalPlayer.Name, Data.Inventory, Data.Inventory.Items:FindFirstChild("Small Gourd"))
               wait(1)
               for _, v in pairs(LocalPlayer.Backpack:GetChildren()) do
                   if v.Name == "Small Gourd" then
                       v.Parent = LocalPlayer.Character
                   end
               end
               wait(1)

               while true do
                   local SmallGourd = LocalPlayer.Character:FindFirstChild("Small Gourd")
                   if SmallGourd then
                       invokeServer("blow_in_gourd_thing", LocalPlayer, SmallGourd, 1)
                   else
                       break
                   end
                   wait()
               end
           end
       end
       wait()
   end
end)


local playerName = game.Players.LocalPlayer.Name
local RightGroupBox = RightGroupBox

local clanLabel = RightGroupBox:AddLabel("Clan: N/A")
RightGroupBox:AddDropdown('SelectClan', {
    Values = { 'Kamado', 'Uzui', 'Rengoku', 'Agatsuma', 'Tomioka', 'Tokito', 'Hashibira', 'Soyama', 'Shinazugawa', 'Kocho', 'Sabito', 'Tamayo', 'Kuwajima', 'Makamo' },
    Default = 1, -- number index of the value / string
    Multi = false, -- true / false, allows multiple choices to be selected
    Text = 'Select Clan',
    Callback = function(v)
        local localplayer = game:GetService("Players").LocalPlayer
        local clanValue = v
        game:GetService("ReplicatedStorage").Player_Data[localplayer.Name].Clan.Value = clanValue
    end
})
local raceLabel = RightGroupBox:AddLabel("Race: N/A")
RightGroupBox:AddDropdown('SelectRace', {
    Values = { 'Human', 'Slayer', 'Demon', 'Hybrid'},
    Default = 1, -- number index of the value / string
    Multi = false, -- true / false, allows multiple choices to be selected
    Text = 'Select Race',
    Callback = function(v)
        local localplayer = game:GetService("Players").LocalPlayer
        local raceValue
        if v == 'Human' then
            raceValue = 1
        elseif v == 'Slayer' then
            raceValue = 2
        elseif v == 'Demon' then
            raceValue = 3
        else
            raceValue = 4 -- or any value for Hybrid race
        end
        game:GetService("ReplicatedStorage").Player_Data[localplayer.Name].Race.Value = raceValue
    end
})

local BreathingLabel = RightGroupBox:AddLabel("Breathing: N/A")
local ArtLabel = RightGroupBox:AddLabel("Art: N/A")


local function updateLabel()
    local localplayer = game:GetService("Players").LocalPlayer
    local clanValue = game:GetService("ReplicatedStorage").Player_Data[localplayer.Name].Clan.Value
    local raceValue = game:GetService("ReplicatedStorage").Player_Data[localplayer.Name].Race.Value
    local BreathingValue = game:GetService("ReplicatedStorage").Player_Data[localplayer.Name].Power.Value
    local ArtValue = game:GetService("ReplicatedStorage").Player_Data[localplayer.Name].Demon_Art.Value
    
    clanLabel:SetText("Clan: " .. clanValue)
    if raceValue == 1 then
        raceLabel:SetText("Race: Human")
    elseif raceValue == 2 then
        raceLabel:SetText("Race: Slayer")
    elseif raceValue == 3 then
        raceLabel:SetText("Race: Demon")
    else
        raceLabel:SetText("Race: Hybrid")
    end
    BreathingLabel:SetText("Breathing: " .. BreathingValue)
    ArtLabel:SetText("Art: " .. ArtValue)
end
game:GetService("RunService").Heartbeat:Connect(updateLabel)

local demonProgressLabel = RightGroupBox:AddLabel("Demon Progress: N/A")
local breathingProgressLabel = RightGroupBox:AddLabel("Breathing Progress: N/A")

local function updateLabel()
    local demonProgress = game:GetService("ReplicatedStorage").Player_Data[playerName].DemonProgress
    local breathingProgress = game:GetService("ReplicatedStorage").Player_Data[playerName].BreathingProgress
    local demonText = demonProgress["1"].Value .. "/" .. demonProgress["2"].Value
    local breathingText = breathingProgress["1"].Value .. "/" .. breathingProgress["2"].Value
    
    demonProgressLabel:SetText("Demon Progress: " .. demonText)
    breathingProgressLabel:SetText("Breathing Progress: " .. breathingText)
end

game:GetService("RunService").Heartbeat:Connect(updateLabel)

local startTime = os.time()

local timeLabel = RightGroupBox:AddLabel("Elapsed Time: 0s")

local function updateLabel()
    local elapsedTime = os.time() - startTime
    local formattedTime = string.format("%02d:%02d:%02d", elapsedTime / 3600, (elapsedTime / 60) % 60, elapsedTime % 60)
    timeLabel:SetText("Elapsed Time: " .. formattedTime)
end

game:GetService("RunService").Heartbeat:Connect(updateLabel)

RightGroupBox:AddButton("SPIN DEMON ART", function()
    local args = {
       [1] = "check_can_spin_demon_art"
   }
   
   game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S_"):InvokeServer(unpack(args))    
end)


RightGroupBox2:AddInput('MyTextbox', {
    Default = 'Webhook URL',
    Numeric = false,
    Finished = false,
    Text = 'Enter Webhook URL',
    Placeholder = 'Enter Webhook URL',
    Callback = function(value)
        WebhookURL = value
    end
})

RightGroupBox2:AddToggle('AutoCollectChestv3', {
    Text = 'Auto Collect Chest v3',
    Default = false,
    Tooltip = 'Auto Collect Chest [Webhook (BETA)]',
    Callback = function(value)
        getgenv().AutoCollectChestv3 = value
    end
})

RightGroupBox3:AddToggle('AutoSkill', {
   Text = 'Auto Skill',
   Default = false, -- Default value (true / false)
   Callback = function(t)
         getgenv().AutoUseSkills = t
   end
})

RightGroupBox3:AddToggle('[Z] Move', {
   Text = '[Z] Move',
   Default = false, -- Default value (true / false)
   Callback = function(t)
         getgenv().ZMove = t
   end
})

RightGroupBox3:AddToggle('[X] Move', {
   Text = '[X] Move',
   Default = false, -- Default value (true / false)
   Callback = function(t)
         getgenv().XMove = t
   end
})

RightGroupBox3:AddToggle('[C] Move', {
   Text = '[C] Move',
   Default = false, -- Default value (true / false)
   Callback = function(t)
         getgenv().CMove = t
   end
})

RightGroupBox3:AddToggle('[V] Move', {
   Text = '[V] Move',
   Default = false, -- Default value (true / false)
   Callback = function(t)
         getgenv().VMove = t
   end
})

RightGroupBox3:AddToggle('[B] Move', {
   Text = '[B] Move',
   Default = false, -- Default value (true / false)
   Callback = function(t)
         getgenv().BMove = t
   end
})

RightGroupBox3:AddToggle('[N] Move', {
   Text = '[N] Move',
   Default = false, -- Default value (true / false)
   Callback = function(t)
         getgenv().NMove = t
   end
})

-- // AUTO USE SKILLS - SKILLS
	
spawn(function()
   while task.wait() do
      pcall(function()
         if SkillActive then
            if AutoUseSkills and getgenv().ZMove and not UsingSkill then
               for i = 1,7 do
                  UsingSkill = true
                  SkillBind("Z")
               end              
               UsingSkill = false
            end
         end
      end)
   end
end)


spawn(function()
   while task.wait() do
      pcall(function()
         if SkillActive then
            if AutoUseSkills and getgenv().XMove and not UsingSkill then
               for i = 1,7 do
                  UsingSkill = true
                  SkillBind("X")
               end              
               UsingSkill = false
            end
         end
      end)
   end
end)

spawn(function()
   while task.wait() do
      pcall(function()
         if SkillActive then
            if AutoUseSkills and getgenv().CMove and not UsingSkill then
               for i = 1,7 do
                  UsingSkill = true
                  SkillBind("C")
               end              
               UsingSkill = false
            end
         end
      end)
   end
end)

spawn(function()
   while task.wait() do
      pcall(function()
         if SkillActive then
            if AutoUseSkills and getgenv().VMove and not UsingSkill then
               for i = 1,7 do
                  UsingSkill = true
                  SkillBind("V")
               end              
               UsingSkill = false
            end
         end
      end)
   end
end)

spawn(function()
   while task.wait() do
      pcall(function()
         if SkillActive then
            if AutoUseSkills and getgenv().BMove and not UsingSkill then
               for i = 1,7 do
                  UsingSkill = true
                  SkillBind("B")
               end              
               UsingSkill = false
            end
         end
      end)
   end
end)

spawn(function()
   while task.wait() do
      pcall(function()
         if SkillActive then
            if AutoUseSkills and getgenv().NMove and not UsingSkill then
               for i = 1,7 do
                  UsingSkill = true
                  SkillBind("N")
               end              
               UsingSkill = false
            end
         end
      end)
   end
end)

-- // WALK SPEED - MISCELLANEOUS

spawn(function()
   while task.wait() do
      if getgenv().WalkSpeedEnabled then
         local h = GetHuman()
         local oldws = h and h.WalkSpeed
         if oldws then
            pcall(function()
               h.WalkSpeed = getgenv().WalkSpeedValue or oldws or 16
               while task.wait() and getgenv().WalkSpeedEnabled do
                  h.WalkSpeed = getgenv().WalkSpeedValue or oldws or 16
               end
            end)
            h.WalkSpeed = oldws or 16
         end
      end
   end
end)

-- // JUMP POWER - MISCELLANEOUS

spawn(function()
   while task.wait() do
      if getgenv().JumpPowerEnabled then
         local h = GetHuman()
         local oldjp = h and h.JumpPower
         if oldjp then
            pcall(function()
               h.JumpPower = getgenv().JumpPowerValue or oldjp or 50
               while task.wait() and getgenv().JumpPowerEnabled do
                  h.JumpPower = getgenv().JumpPowerValue or oldjp or 50
               end
            end)
            h.JumpPower = oldjp or 50
         end
      end
   end
end)	

RightGroupBox4:AddToggle('WalkSpeedT', {
   Text = 'Enable Walk Speed',
   Default = false, -- Default value (true / false)
   Callback = function(t)
      getgenv().WalkSpeedEnabled = t
   end
})

RightGroupBox4:AddSlider('WalkSpeedS', {
    Text = 'Walk Speed',
    Default = 16,
    Min = 16,
    Max = 500,
    Rounding = 1,
    Compact = false,
    Callback = function(v)
		getgenv().WalkSpeedValue = v
    end
})

RightGroupBox4:AddToggle('JumpPowerT', {
   Text = 'Enable Jump Power',
   Default = false, -- Default value (true / false)
   Callback = function(t)
      getgenv().JumpPowerEnabled = t
   end
})

RightGroupBox4:AddSlider('JumpPowerS', {
    Text = 'Jump Power',
    Default = 50,
    Min = 50,
    Max = 500,
    Rounding = 10,
    Compact = false,
    Callback = function(v)
		getgenv().JumpPowerValue = v
    end
})


Test:AddToggle('InfStamina', {
   Text = 'Infinite Stamina',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         getgenv().infstuff = true
         while getgenv().infstuff do
            task.wait()
            getrenv()._G:Stamina(-100)
         end
      else
         getgenv().infstuff = false
      end
   end
})

Test:AddToggle('InfBreathing', {
   Text = 'Infinite Breathing',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         getgenv().infstuff = true
         while getgenv().infstuff do
            task.wait()
            getrenv()._G:Breath(-100)
         end
      else
         getgenv().infstuff = false
      end
   end
})

-- // NO DROWN - MISCELLANEOUS

task.spawn(function()
   for i,v in next, getgc(true) do
      if type(v) == "table" and rawget(v, "swim_bar") then
         while task.wait() do
            if getgenv().NoDrown then
               rawset(v, "swim_bar", {
                  [1] = 2,
                  [2] = 2
               })
            end
         end
      end
   end
end)

Test:AddToggle('No Drown', {
   Text = 'No Drown',
   Default = false, -- Default value (true / false)
   Callback = function(t)
      getgenv().NoDrown = t
   end
})


local oldindex
Test:AddToggle('NoCD', {
   Text = 'No Cooldown [Can Kick]',
   Default = false,
   Callback = function(state)
      if state then
         getgenv().NoCdMoves = true
         oldindex = hookmetamethod(game, "__index", function(index, value)
            if tostring(index) == "LastUsed" and getgenv().NoCdMoves then
               return 0
            end
            return oldindex(index, value)
         end)
      else
         getgenv().NoCdMoves = false
         hookmetamethod(game, "__index", oldindex)
      end
   end
})

Test:AddToggle('NoSunDMG', {
   Text = 'No Sun Damage [DEMON]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         game:GetService("Players").LocalPlayer.PlayerScripts["Small_Scripts"].Gameplay["Sun_Damage"].Disabled = true
      else
         game:GetService("Players").LocalPlayer.PlayerScripts["Small_Scripts"].Gameplay["Sun_Damage"].Disabled = false
      end
   end
})

Test:AddToggle('WhiteScreen', {
   Text = 'White Screen [FPS Boost]',
   Default = false,
   Callback = function(state)
      if state then
         game:GetService("RunService"):Set3dRenderingEnabled(false)
      else
         game:GetService("RunService"):Set3dRenderingEnabled(true)
      end
   end
})


Test2:AddToggle('AutoSplitBoulder', {
   Text = 'Auto Split Boulder',
   Default = false,
   Callback = function(t)
      getgenv().AutoSplitBoulder = t
   end
})

Test2:AddToggle('AutoPushUps', {
   Text = 'Auto Push-Ups',
   Default = false,
   Callback = function(t)
      getgenv().AutoPushUps = t
   end
})

Test2:AddToggle('AutoMeditate', {
   Text = 'Auto Meditate',
   Default = false,
   Callback = function(t)
      getgenv().AutoMeditate = t
   end
})

Test2:AddToggle('AutoCupGame', {
   Text = 'Auto Cup Game',
   Default = false,
   Callback = function(t)
      getgenv().AutoCupGame = t
   end
})

Test2:AddToggle('AutoTarget', {
   Text = 'Auto Target',
   Default = false,
   Callback = function(t)
      getgenv().AutoTarget = t
   end
})

-- // AUTO SPLIT BOULDER - TRAININGS

spawn(function()
   while task.wait() do
       if getgenv().AutoSplitBoulder then
           pcall(function()
               game:GetService("Players").LocalPlayer.PlayerGui.ExcessGuis["boulder_split_ui"].Holder.LocalScript.Value.Value = 10000
           end)
       end
   end
  end)

-- // AUTO MEDITATE - TRAININGS

  spawn(function()
   while task.wait() do
       if getgenv().AutoMeditate then
           pcall(function()
               game:GetService("Players").LocalPlayer.PlayerGui.ExcessGuis["Meditate_gui"].Holder.LocalScript.Value.Value = 100
           end)
       end
   end
  end)

-- // AUTO PUSH UPS - TRAININGS

  spawn(function()
   while task.wait() do
       if getgenv().AutoPushUps then
           pcall(function()
               game:GetService("Players").LocalPlayer.PlayerGui.ExcessGuis["Push_Up_Gui"].Holder.push_up_mat_local_script.Value.Value = 1000
           end)
       end
   end
  end)

-- // AUTO CUP GAME - TRAININGS

  spawn(function()
   while task.wait() do
       if getgenv().AutoCupGame then
           pcall(function()
               game:GetService("Players").LocalPlayer.PlayerGui.ExcessGuis["cup_game_gui"].Holder.cup_game_script123.Value.Value = 1000
           end)
       end
   end
  end)

-- // AUTO TARGET - TRAININGS	

  spawn(function()
   while task.wait() do
       if getgenv().AutoTarget then
           pcall(function()
               game:GetService("Players").LocalPlayer.PlayerGui.ExcessGuis["chairui"].Holder.LocalScript.Value.Value = 1000
           end)
       end
   end
  end)

Test3:AddToggle('UniGodMode', {
   Text = 'Universal God Mode',
   Default = false, -- Default value (true / false)
Tooltip = '[Must Have All Sword and Scythe Equipped in Inventory and All Have Mastery 35+]',
   Callback = function(state)
      if state then
         _G.godmode2 = true
   while _G.godmode2 do
   local args = {
      [1] = "skil_ting_asd",
      [2] = game:GetService("Players").LocalPlayer,
      [3] = "scythe_asteroid_reap",
      [4] = 1
   }
   
   game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
   wait(0.1)
   end
      else
         _G.godmode2 = false
         while _G.godmode2 do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "scythe_asteroid_reap",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(0.1)
         end
      end
   end    
})

  Test3:AddToggle('SemiGodMode', {
   Text = 'Semi God Mode [Kamado]',
   Default = false, -- Default value (true / false)
   Tooltip = 'Infinite Heals With Kamado Regeneration', -- Information shown when you hover over the toggle
   Callback = function(state)
       if state then
           game:GetService("ReplicatedStorage").Remotes.heal_tang123asd:FireServer(true)
       else
           game:GetService("ReplicatedStorage").Remotes.heal_tang123asd:FireServer(false)
       end
   end
})

Test3:AddToggle('SemiGodMode2', {
   Text = 'Semi God Mode [ALL RACES]',
   Default = false, -- Default value (true / false)
   Tooltip = 'Infinite Heals', -- Information shown when you hover over the toggle
   Callback = function(state)
       if state then
           game:GetService("ReplicatedStorage").Remotes.regeneration_breathing_remote:FireServer(true)
       else
           game:GetService("ReplicatedStorage").Remotes.regeneration_breathing_remote:FireServer(false)
       end
   end
})

Test3:AddToggle('RengokuMode', {
   Text = 'Rengoku Mode [Human/Slayer]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         game:GetService("ReplicatedStorage").Remotes.heart_ablaze_mode_remote:FireServer(true)
      else
         game:GetService("ReplicatedStorage").Remotes.heart_ablaze_mode_remote:FireServer(false)
      end
   end
})

Test3:AddToggle('GodSpeedMode', {
   Text = 'God Speed Mode [Human/Slayer]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         game:GetService("ReplicatedStorage").Remotes.thundertang123:FireServer(true)
      else
         game:GetService("ReplicatedStorage").Remotes.thundertang123:FireServer(false)
      end
   end
})

Test3:AddToggle('WarDrumsMode', {
   Text = 'War Drums Mode [All Races]',
   Default = false, -- Default value (true / false)
   Callback = function(Value)
      getgenv().infWD = Value
		while getgenv().infWD do 
		local args = {
    	[1] = true
		}

		game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("war_Drums_remote"):FireServer(unpack(args))
		wait(3)
      end
   end
})

Test3:AddToggle('Chatlogs', {
    Text = 'Enable Chat Logs',
    Default = false, -- Default value (true / false)
    Tooltip = 'Enable/Disable Chatlogs', -- Information shown when you hover over the toggle
    Callback = function(state)
        if state then
             game:GetService("Players").LocalPlayer.PlayerGui.Chat.Frame.ChannelsBarParentFrame.Visible = true
             game:GetService("Players").LocalPlayer.PlayerGui.Chat.Frame.ChatBarParentFrame.Visible = true
             game:GetService("Players").LocalPlayer.PlayerGui.Chat.Frame.ChatChannelParentFrame.Visible = true
 
        else
             game:GetService("Players").LocalPlayer.PlayerGui.Chat.Frame.ChannelsBarParentFrame.Visible = false
             game:GetService("Players").LocalPlayer.PlayerGui.Chat.Frame.ChatBarParentFrame.Visible = false
             game:GetService("Players").LocalPlayer.PlayerGui.Chat.Frame.ChatChannelParentFrame.Visible = false
        end
    end
 })

Test3:AddButton("Remote Spy", function()
   loadstring(game:HttpGet("https://pastebin.com/raw/66NjbMN7",true))()
end)

Test3:AddButton("Infinite Yield", function()
   loadstring(game:HttpGet(('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'),true))()
end)


Test3:AddButton("Title Buffs", function()
local folderPath = game:GetService("Players").LocalPlayer.Player_Titles_List

    -- Loop through each child in the folder
    for _, child in ipairs(folderPath:GetChildren()) do
    if child:IsA("IntValue") then
   child.Value = 9999999999
   end
end
end)

Test3:AddButton("Remove Block For Mobs (TEST)", function()
    game.Workspace.Mobs.DescendantAdded:Connect(function(c)
        if c.Name == "Blocking" then 
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer("remove_blocking", c.Parent)
        end
    end)
end)

Test3:AddButton("FORCE RESET", function()
    local args = {
        [1] = "Add_Knockedout"
    }
    
    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("water_damage"):FireServer()
    wait()
    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("water_damage"):FireServer()
    wait()
    game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("water_damage"):FireServer()
end)

Test4:AddToggle('ShockGM', {
   Text = 'God Mode [Shockwave 50 + Demon]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         _G.godmode = true
   while _G.godmode do
   local args = {
      [1] = "skil_ting_asd",
      [2] = game:GetService("Players").LocalPlayer,
      [3] = "akaza_bda_compass_needle",
      [4] = 1
   }
   
   game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
   wait(0.1)
   end
      else
         _G.godmode = false
         while _G.godmode do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "akaza_bda_compass_needle",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(0.1)
         end
      end
   end    
})

Test4:AddToggle('DreamGM', {
   Text = 'God Mode [Dream ULT + Demon]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         _G.DREAMgodmode = true
   while _G.DREAMgodmode do
   local args = {
      [1] = "skil_ting_asd",
      [2] = game:GetService("Players").LocalPlayer,
      [3] = "dream_bda_flesh_monster",
      [4] = 1
   }
   
   game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
   wait(0.1)
   end
      else
         _G.DREAMgodmode = false
         while _G.DREAMgodmode do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "dream_bda_flesh_monster",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(0.1)
         end
      end
   end    
})

Test4:AddToggle('SwampGM', {
   Text = 'God Mode [Swamp ULT + Demon]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         _G.SWAMPgodmode = true
   while _G.SWAMPgodmode do
   local args = {
      [1] = "skil_ting_asd",
      [2] = game:GetService("Players").LocalPlayer,
      [3] = "swamp_bda_swamp_domain",
      [4] = 1
   }
   
   game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
   wait(0.1)
   end
      else
         _G.SWAMPgodmode = false
         while _G.SWAMPgodmode do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "swamp_bda_swamp_domain",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(0.1)
         end
      end
   end    
})


Test4:AddToggle('IceGM', {
   Text = 'God Mode [Ice ULT + Demon]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         _G.ICEgodmode = true
   while _G.ICEgodmode do
   local args = {
      [1] = "skil_ting_asd",
      [2] = game:GetService("Players").LocalPlayer,
      [3] = "ice_demon_art_bodhisatva",
      [4] = 1
   }
   
   game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
   wait(0.1)
   end
      else
         _G.ICEgodmode = false
         while _G.ICEgodmode do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "ice_demon_art_bodhisatva",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(0.1)
         end
      end
   end    
})

Test4:AddToggle('BloodGM', {
   Text = 'God Mode [Blood ULT + Demon]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         _G.BloodGM = true
   while _G.BloodGM do
   local args = {
      [1] = "skil_ting_asd",
      [2] = game:GetService("Players").LocalPlayer,
      [3] = "explosive_demon_art_blood_burst",
      [4] = 1
   }
   
   game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
   wait(0.1)
   end
      else
         _G.BloodGM = false
         while _G.BloodGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "explosive_demon_art_blood_burst",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(0.1)
         end
      end
   end    
})

Test5:AddToggle('SoundGM', {
   Text = 'God Mode [Sound 50+]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         _G.SoundGM = true
         while _G.SoundGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "sound_breathing_smoke_screen",
            [4] = 1
          }
   
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
      wait(0.1)
         end
      else
         _G.SoundGM = false
         while _G.SoundGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "sound_breathing_smoke_screen",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(1)
         end
      end
   end    
})

Test5:AddToggle('FlameGM', {
   Text = 'God Mode [Flame 32+]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         _G.FlameGM = true
         while _G.FlameGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "flame_breathing_flaming_eruption",
            [4] = 1
          }
   
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
      wait(0.1)
         end
      else
         _G.FlameGM = false
         while _G.FlameGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "flame_breathing_flaming_eruption",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(0.1)
         end
      end
   end    
})

Test5:AddToggle('BeastGM', {
   Text = 'God Mode [Beast 40+]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         _G.BeastGM = true
         while _G.BeastGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "Beast_breathing_devouring_slash",
            [4] = 1
          }
   
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
      wait(0.5)
         end
      else
         _G.BeastGM = false
         while _G.BeastGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "Beast_breathing_devouring_slash",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(0.5)
         end
      end
   end    
})

Test5:AddToggle('InsectGM', {
   Text = 'God Mode [Insect 28+]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         _G.InsectGM = true
         while _G.InsectGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "insect_breathing_dance_of_the_centipede",
            [4] = 1
          }
   
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
      wait(0.5)
         end
      else
         _G.InsectGM = false
         while _G.InsectGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "insect_breathing_dance_of_the_centipede",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(0.5)
         end
      end
   end    
})

Test5:AddToggle('WindGM', {
   Text = 'God Mode [Wind 30+]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         _G.WindGM = true
         while _G.WindGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "Wind_breathing_black_wind_mountain_mist",
            [4] = 1
          }
   
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
      wait(0.5)
         end
      else
         _G.WindGM = false
         while _G.WindGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "Wind_breathing_black_wind_mountain_mist",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(0.5)
         end
      end
   end    
})

Test5:AddToggle('WaterGM', {
   Text = 'God Mode [Water 30+]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
      if state then
         _G.WaterGM = true
         while _G.WaterGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "Water_fall_basin",
            [4] = 1
          }
   
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
      wait(0.5)
         end
      else
         _G.WaterGM = false
         while _G.WaterGM do
         local args = {
            [1] = "skil_ting_asd",
            [2] = game:GetService("Players").LocalPlayer,
            [3] = "Water_fall_basin",
            [4] = 1
         }
         
         game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("To_Server"):WaitForChild("Handle_Initiate_S"):FireServer(unpack(args))
         wait(0.5)
         end
      end
   end    
})

Shark1:AddToggle('TPtoTrainer', {
   Text = 'TP to Trainer',
   Default = false, -- Default value (true / false)
   Tooltip = 'TP to Trainer', -- Information shown when you hover over the toggle
   Callback = function(v)
      getgenv().TPtoTrainer = v
   end
})

getgenv().TrainerSelected = "Water Traine"
Shark1:AddDropdown('TPToTrainerr', {
    Values = { 'Water Trainer', 'Thunder Trainer', 'Insect Trainer', 'Wind Trainer' },
    Default = 1, -- number index of the value / string
    Multi = false, -- true / false, allows multiple choices to be selected
    Text = 'Select Trainer',
    Callback = function(v)
		getgenv().TrainerSelected = v
    end
 })

 Shark1:AddToggle('TPtoLocation', {
   Text = 'Teleport to Location',
   Default = false, -- Default value (true / false)
   Tooltip = 'Teleport to Location', -- Information shown when you hover over the toggle
   Callback = function(v)
      getgenv().TPtoLocation = v
   end
})

getgenv().AreaSelected = "Zapiwara Mountain"
Shark1:AddDropdown('TPtoLocation', {
    Values = { 'Zapiwara Mountain', 'FWaroru Cave', 'Slasher Demon', 'Ushumaru Village', 'Ouwbayashi Home', 'Kabiwaru Village', 'Zapiwara Cave', 'Dangerous Woods', 'Final Selection', 'Kiribating Village', 'Butterfly Mansion', 'Abubu Cave', 'Testing Place' },
    Default = 1, -- number index of the value / string
    Multi = false, -- true / false, allows multiple choices to be selected
    Text = 'Teleport to Location',
    Callback = function(v)
		getgenv().AreaSelected = v
    end
 })

 local TweenService = game:GetService("TweenService")
 local function TPtoMuzan()
     local Muzan = workspace:FindFirstChild("Muzan")
     if Muzan then
         local SpawnPos = Muzan:FindFirstChild("SpawnPos")
         if SpawnPos then
             local targetPosition = SpawnPos.Value
         
             -- Perform CFrame Tween using TweenService
             local humanoidRootPart = LP.Character.HumanoidRootPart
             local tweenInfo = TweenInfo.new(
                 10, -- Duration
                 Enum.EasingStyle.Quad, -- EasingStyle
                 Enum.EasingDirection.Out -- EasingDirection
             )
             local tween = TweenService:Create(humanoidRootPart, tweenInfo, { CFrame = CFrame.new(targetPosition) })
             tween:Play()
         end
     end
 end

Shark1:AddButton("Teleport to Muzan", TPtoMuzan)

Shark1:AddButton("Reset To Void", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(755, -498, 892)
end)

 -- // LOCATIONS - TELEPORTS

spawn(function()
    while task.wait() do
        pcall(function()
            if TPtoTrainer then
                if not LP.Character.HumanoidRootPart:FindFirstChild("BodyVelocity") then
                    antifall4 = Instance.new("BodyVelocity", LP.Character.HumanoidRootPart)
                    antifall4.Velocity = Vector3.new(0, 0, 0)
                    antifall4.MaxForce = Vector3.new(9e9, 9e9, 9e9)
                elseif LP.Character.HumanoidRootPart:FindFirstChild("BodyVelocity") then
                    repeat task.wait()
                        if GetDistance(TrainersCF[TrainerSelected]) < 50 and GetDistance(TrainersCF[TrainerSelected]) < 150 then
                            if TweenFa then
                                TweenFa:Cancel()
                                wait(.1)
                            end
                            LP.Character.HumanoidRootPart.CFrame = TrainersCF[TrainerSelected]
                        else
                            TweenFa = Tween(TrainersCF[TrainerSelected])
                        end
                    until not TPtoTrainer
                end
            else
                antifall4:Destroy()
            end
        end)
    end
    end)
    
    spawn(function()
    while task.wait() do
        pcall(function()
            if TPtoLocation then
                if not LP.Character.HumanoidRootPart:FindFirstChild("BodyVelocity") then
                    antifall5 = Instance.new("BodyVelocity", LP.Character.HumanoidRootPart)
                    antifall5.Velocity = Vector3.new(0, 0, 0)
                    antifall5.MaxForce = Vector3.new(9e9, 9e9, 9e9)
                elseif LP.Character.HumanoidRootPart:FindFirstChild("BodyVelocity") then
                    repeat task.wait()
                        if GetDistance(Locations[AreaSelected]) < 50 and GetDistance(Locations[AreaSelected]) < 150 then
                            if TweenFa then
                                TweenFa:Cancel()
                                wait(.1)
                            end
                            LP.Character.HumanoidRootPart.CFrame = Locations[AreaSelected]
                        else
                            TweenFa = Tween(Locations[AreaSelected])
                        end
                    until not TPtoLocation
                end
            else
                antifall5:Destroy()
            end
        end)
    end
    end)


   Shark2:AddToggle('AutoCollectLily', {
      Text = 'Auto Collect Lily',
      Default = false, 
      Callback = function(value)
         TP = value
        if TP then
            getgenv().speed = 270
            getgenv().AutoRejoin = true -- Automatically rejoins when you're kicked
            getgenv().delay = 1

            game.Players.PlayerRemoving:Connect(function(player)
                if player.Name == game.Players.LocalPlayer.Name and getgenv().AutoRejoin then
                    local ts = game:GetService("TeleportService")
                    ts:Teleport(game.PlaceId)
                    autoload()
                end
            end)

            local RunService = game:GetService("RunService")
            local Players = game:GetService("Players")
            local Player = Players.LocalPlayer
            local chr = Player.Character
            local root = chr.HumanoidRootPart

            local TeleportSpeed = getgenv().speed or 250
            local NextFrame = RunService.Heartbeat

            local function fireproximityprompt(ProximityPrompt, Amount, Skip)
                assert(ProximityPrompt, "Argument #1 Missing or nil")
                assert(
                    typeof(ProximityPrompt) == "Instance" and ProximityPrompt:IsA("ProximityPrompt"),
                    "Attempted to fire a Value that is not a ProximityPrompt"
                )
                local HoldDuration = ProximityPrompt.HoldDuration
                if Skip then
                    ProximityPrompt.HoldDuration = 0
                end
                for i = 1, Amount or 1 do
                    ProximityPrompt:InputHoldBegin()
                    if Skip then
                        local RunService = game:GetService("RunService")
                        local Start = tick()
                        repeat
                            RunService.Heartbeat:Wait(0.1)
                        until tick() - Start > HoldDuration
                    end
                    ProximityPrompt:InputHoldEnd()
                end
                ProximityPrompt.HoldDuration = HoldDuration
            end

            local function ImprovedTeleport(Target)
                if typeof(Target) == "Instance" and Target:IsA("BasePart") then
                    Target = Target.Position
                end
                if typeof(Target) == "CFrame" then
                    Target = Target.p
                end
                local HRP = Player.Character and Player.Character:FindFirstChild("HumanoidRootPart")
                if not HRP then
                    return
                end
                local StartingPosition = HRP.Position
                local PositionDelta = Target - StartingPosition -- Calculating the difference between the start and end positions.
                local StartTime = tick()
                local TotalDuration = (StartingPosition - Target).magnitude / TeleportSpeed
                repeat
                    NextFrame:Wait()
                    local Delta = tick() - StartTime
                    local Progress = math.min(Delta / TotalDuration, 1) -- Getting the percentage of completion of the teleport (between 0-1, not 0-100)
                    -- We also use math.min to maximize it at 1 in case the player gets an FPS drop, so it doesn't go past the target.
                    local MappedPosition = StartingPosition + (PositionDelta * Progress)
                    HRP.Velocity = Vector3.new() -- Resetting the effect of gravity so it doesn't get too much and drag the player below the ground.
                    HRP.CFrame = CFrame.new(MappedPosition)
                until (HRP.Position - Target).magnitude <= TeleportSpeed / 2
                HRP.Anchored = false
                HRP.CFrame = CFrame.new(Target)
            end

            local flowers = game:GetService("Workspace").Demon_Flowers_Spawn

            local function getFlower()
                local dist, flower = math.huge
                for i, v in next, flowers:GetChildren() do
                    if v:IsA("Model") then
                        local mag = (root.Position - v.WorldPivot.Position).magnitude
                        if mag < dist then
                            dist = mag
                            flower = v
                        end
                    end
                end
                return flower
            end

            oldasdqw = coroutine.wrap(function()
                while TP do
                    task.wait()
                    ImprovedTeleport(getFlower().WorldPivot.Position)
                    task.wait(getgenv().delay)
                    for i, v in next, getFlower():GetDescendants() do
                        if v:IsA("ProximityPrompt") then
                            local try = 0
                            repeat
                                wait(0.01)
                                try += 1
                                fireproximityprompt(v, 1, true)
                                if not getFlower() or not TP then
                                    oldasdqw()
                                    break
                                end
                            until try == 10
                            getFlower():Destroy()
                        end
                    end
                end
            end)

            oldasdqw()
        else
            TP = false
            if oldasdqw then
                oldasdqw()
            end
        end
      end    
   })

local isAutoBuyEnabled = false
local autoBuyLoop

local function buyBandage()
    local args = {
        [1] = "buysomething",
        [2] = game:GetService("Players").LocalPlayer,
        [3] = "Bandage",
        [4] = game:GetService("ReplicatedStorage").Player_Data[game:GetService("Players").LocalPlayer.Name].Yen,
        [5] = game:GetService("ReplicatedStorage").Player_Data[game:GetService("Players").LocalPlayer.Name].Inventory,
        [6] = 10
    }
    
    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(unpack(args))
end

Shark3:AddToggle('AutoBuy', {
    Text = 'Auto Buy Bandage',
    Default = false,
    Tooltip = 'Auto Buy',
    Callback = function(state)
        isAutoBuyEnabled = state
        
        if isAutoBuyEnabled then
            autoBuyLoop = spawn(function()
                while isAutoBuyEnabled do
                    buyBandage()
                    wait(0.1)
                end
            end)
        else
            if autoBuyLoop then
                autoBuyLoop:Destroy()
                autoBuyLoop = nil
            end
        end
    end
})


local player = game:GetService("Players").LocalPlayer
local itemName = ""

Shark3:AddInput('ItemName', {
    Default = 'Put FULL Item Name',
    Numeric = false,
    Finished = false,
    Text = 'Put FULL Item Name',
    Placeholder = 'Put FULL Item Name',
    Callback = function(value)
        itemName = value
    end
})
Shark3:AddButton("Sell 100 Items With That Name", function()
    if itemName == "" then
        print("Please input an item name.")
        return
    end
    local inventory = game:GetService("ReplicatedStorage").Player_Data[player.Name].Inventory.Items
    local itemFound = false
    for _, item in ipairs(inventory:GetDescendants()) do
        if item.Name == itemName then

            itemFound = true
            print("Item Found:", item.Name)

            local settings = item.Settings
            local id = settings.Id.Value
            print("ID:", id)
            local args = {
                [1] = {
                    [id] = 100
                },
                [2] = 0,
                [3] = 0
            }
            game:GetService("ReplicatedStorage").Sell_Items_tang:InvokeServer(unpack(args))
            
            break 
        end
    end
    if not itemFound then
        print("Item not found:", itemName)
    end
end)

Shark3:AddButton("Sell 50 Items With That Name", function()
    if itemName == "" then
        print("Please input an item name.")
        return
    end
    local inventory = game:GetService("ReplicatedStorage").Player_Data[player.Name].Inventory.Items
    local itemFound = false
    for _, item in ipairs(inventory:GetDescendants()) do
        if item.Name == itemName then

            itemFound = true
            print("Item Found:", item.Name)

            local settings = item.Settings
            local id = settings.Id.Value
            print("ID:", id)
            local args = {
                [1] = {
                    [id] = 50
                },
                [2] = 0,
                [3] = 0
            }
            game:GetService("ReplicatedStorage").Sell_Items_tang:InvokeServer(unpack(args))
            
            break 
        end
    end
    if not itemFound then
        print("Item not found:", itemName)
    end
end)

Shark3:AddButton("Sell 10 Items With That Name", function()
    if itemName == "" then
        print("Please input an item name.")
        return
    end
    local inventory = game:GetService("ReplicatedStorage").Player_Data[player.Name].Inventory.Items
    local itemFound = false
    for _, item in ipairs(inventory:GetDescendants()) do
        if item.Name == itemName then

            itemFound = true
            print("Item Found:", item.Name)

            local settings = item.Settings
            local id = settings.Id.Value
            print("ID:", id)
            local args = {
                [1] = {
                    [id] = 10
                },
                [2] = 0,
                [3] = 0
            }
            game:GetService("ReplicatedStorage").Sell_Items_tang:InvokeServer(unpack(args))
            
            break 
        end
    end
    if not itemFound then
        print("Item not found:", itemName)
    end
end)


Shark3:AddDivider()


   Shark3:AddInput('DisplayName', {
      Default = 'Change Display Name',
      Numeric = false,
      Finished = false,
      Text = 'Change Display Name',
      Placeholder = 'Change Display Name',
      Callback = function(value)
         game:GetService("Players").LocalPlayer.DisplayName = value
      end
  })
   
Shark3:AddButton("Destroy Damage Logs", function()
   local playerGui = game:GetService("Players").LocalPlayer.PlayerGui
   if playerGui:FindFirstChild("Pop_Ups") then
       local bossHp = playerGui.Pop_Ups:FindFirstChild("Bosshp")
       if bossHp then
           local damageLog = bossHp:FindFirstChild("Damage_Log")
           if damageLog then
               damageLog:Destroy()
           end
       end
   end
end)

Sharky1:AddButton("Server Hop", function()
   Hop()
end)

Sharky1:AddButton("Join Lowest Server", function()
   local PlaceID = game.PlaceId
local AllIDs = {}
local foundAnything = ""
local actualHour = os.date("!*t").hour
local Deleted = false
local File = pcall(function()
    AllIDs = game:GetService('HttpService'):JSONDecode(readfile("NotSameServers.json"))
end)
if not File then
    table.insert(AllIDs, actualHour)
    writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
end
function TPReturner()
    local Site;
    if foundAnything == "" then
        Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
    else
        Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
    end
    local ID = ""
    if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
        foundAnything = Site.nextPageCursor
    end
    local num = 0;
    for i,v in pairs(Site.data) do
        local Possible = true
        ID = tostring(v.id)
        if tonumber(v.maxPlayers) > tonumber(v.playing) then
            for _,Existing in pairs(AllIDs) do
                if num ~= 0 then
                    if ID == tostring(Existing) then
                        Possible = false
                    end
                else
                    if tonumber(actualHour) ~= tonumber(Existing) then
                        local delFile = pcall(function()
                            delfile("NotSameServers.json")
                            AllIDs = {}
                            table.insert(AllIDs, actualHour)
                        end)
                    end
                end
                num = num + 1
            end
            if Possible == true then
                table.insert(AllIDs, ID)
                wait()
                pcall(function()
                    writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
                    wait()
                    game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
                end)
                wait(4)
            end
        end
    end
end

function Teleport()
    while wait() do
        pcall(function()
            TPReturner()
            if foundAnything ~= "" then
                TPReturner()
            end
        end)
    end
end

-- If you'd like to use a script before server hopping (Like a Automatic Chest collector you can put the Teleport() after it collected everything.
Teleport()
end)

Sharky1:AddButton("Rejoin", function()
   game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").LocalPlayer)
end)

Sharky1:AddButton("Teleport To Hub", function()
   game:GetService('TeleportService'):Teleport(9321822839)
end)

Sharky1:AddButton("Teleport To Map 1", function()
   game:GetService('TeleportService'):Teleport(6152116144)
end)

Sharky1:AddButton("Teleport To Map 2", function()
   game:GetService('TeleportService'):Teleport(11468159863)
end)

Sharky1:AddButton("Teleport To Trading", function()
   game:GetService('TeleportService'):Teleport(13489082242)
end)

Mugen:AddToggle('Clash', {
   Text = 'Auto Clash [NOT INSTANT]',
   Default = false, -- Default value (true / false)
   Callback = function(state)
       getgenv().AutoClash = state
   end
})

Mugen:AddButton("INSTANT Auto Clash (Use in 7 secs)", function()
    local playerName = game:GetService("Players").LocalPlayer.Name

    local args = {
        [1] = "Change_Value",
        [2] = workspace.Debree.clash_folder[playerName.."vsEnmu"][playerName],
        [3] = 200,  -- Change the value of index 3 to 200
    }

    game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(unpack(args))
end) -- Add the closing parentheses here

 Mugen:AddButton("GLOBAL INSTANT Clash (Use in 7 secs)", function()
    local players = game:GetService("Players"):GetPlayers()

    for _, player in ipairs(players) do
        local playerName = player.Name

        local clashFolder = workspace.Debree.clash_folder
        local playerFolder = clashFolder:FindFirstChild(playerName.."vsEnmu")

        if playerFolder then
            local targetPlayer = playerFolder:FindFirstChild(playerName)
            if targetPlayer then
                local args = {
                    [1] = "Change_Value",
                    [2] = targetPlayer,
                    [3] = 200,  -- Change the value of index 3 to 200
                }

                game:GetService("ReplicatedStorage").Remotes.To_Server.Handle_Initiate_S:FireServer(unpack(args))
            end
        end
    end
end) -- Add the closing parentheses here

Library:OnUnload(function()
   print('Unloaded!')
   Library.Unloaded = true
end)

-- UI Settings
local MenuGroup = Tabs['Settings']:AddLeftGroupbox('Menu')

-- I set NoUI so it does not show up in the keybinds menu
MenuGroup:AddButton('Unload', function() Library:Unload() end)
MenuGroup:AddLabel('Menu bind'):AddKeyPicker('MenuKeybind', { Default = 'LeftControl', NoUI = true, Text = 'Menu keybind' })

Library.ToggleKeybind = Options.MenuKeybind -- Allows you to have a custom keybind for the menu

ThemeManager:SetLibrary(Library)
SaveManager:SetLibrary(Library)

SaveManager:IgnoreThemeSettings()

SaveManager:SetIgnoreIndexes({ 'MenuKeybind' })

ThemeManager:SetFolder('SharkHubv1Linoria')
SaveManager:SetFolder('SharkHub/ProjectSlayers')
SaveManager:BuildConfigSection(Tabs['Settings'])
ThemeManager:ApplyToTab(Tabs['Settings'])
