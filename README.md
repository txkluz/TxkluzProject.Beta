local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Txkluz[เเจก]", "DarkTheme")
local Tab = Window:NewTab("Teleport Map")
local Section = Tab:NewSection("Teleport")
Section:NewLabel("ไม่เเนะนำให้กดไวๆเเนะนำรอ 2-3วิ")
Section:NewButton("PVP ZONE", "ไปที่ตรงกลางเเมพปะวะที่เเม่งชอบต่อยกันอะ" , function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-512.4988403320312, -31.185962677001953, 1650.567626953125)
end)
Section:NewButton("Library", "ไปห้องสมุด", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-40.15901565551758, -116.26957702636719, 363.89556884765625)
end)
Section:NewButton("Guild", "ไปกิลด์", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-688.3067016601562, -31.074766159057617, 1661.07470703125)
end)
Section:NewButton("Unrented office", "ออฟฟิศ", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-226.49122619628906, -30.83466148376465, 1569.4678955078125)
end)
Section:NewButton("Side Park", "ไปสวนสาธารณะ", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-47.1435661315918, -32.01328659057617, 1660.532958984375)
end)
Section:NewButton("Park", "ไปสวนสาธารณะ", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-531.9849853515625, -32.05134201049805, 1399.5308837890625)
end)
Section:NewButton("Forest", "ไปป่า", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-636.5037841796875, -31.8912296295166, 1201.9981689453125)
end)

-- teleport npc
Section:NewLabel("Teleport NPCS")
Section:NewButton("Luna", "ร้านที่เราขายของได้", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-620.1856689453125, -32.49291229248047, 1916.7098388671875)
end)
Section:NewButton("Asakura", "ไปที่คาเฟ่ไปสุ่มสกินได้มั้ง", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-202.75535583496094, -32.10871124267578, 1450.9720458984375)
end)
Section:NewButton("AUDDY", "ร้านที่ไปซื้อของ shop", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-377.2036437988281, -31.704181671142578, 1816.7396240234375)
end)
Section:NewButton("Sakura Wanderer", "เควส", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-386.2707214355469, -32.792152404785156, 1467.6619873046875)
end)
Section:NewButton("Fate", "วาร์ปไปหาสาวในกิลด์", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-691.20947265625, -31.074769973754883, 1651.97998046875)
end)
Section:NewButton("Hika", "วาร์ปไปหาพ่อหนุ่มทำดาบ", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-508.42230224609375, -32.792152404785156, 1511.215087890625)
end)
Section:NewButton("Simple", "ไปหาพ่อหนุ่มสลับสเเตน", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-396.5972595214844, -31.704181671142578, 1821.718017578125)
end)
Section:NewButton("True Swordman", "ไปหาพ่อหนุ่มรีสกิน", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(53.27326202392578, -33.015357971191406, 1572.9500732421875)
end)
-- event
Section:NewLabel("Event TL")
Section:NewButton("Quest Event Deliver", "วาร์ปไปหน้ารับเควส", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-379.7237854003906, -32.97041320800781, 1484.1832275390625)
end)
-- ฟาร์มitem
local Tab = Window:NewTab("FARM ITEM")
local Section = Tab:NewSection("Box")
Section:NewButton("BOX", "อยากกดก็กดปิดไปไม่รู้จะเขียนไร", function()
getgenv().loop = true
local finditems = {"Box"} 
 
while getgenv().loop do
    task.wait()
    pcall(function()
        local folder = game:GetService("Workspace").Item
        local items = folder:GetChildren()
        local closestItem = nil
        local minDistance = math.huge
 
        local tweenService = game:GetService("TweenService")
        local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear)
 
        local lp = game.Players.LocalPlayer
 
        function teleport(v, speed)
            if lp.Character and lp.Character:FindFirstChild('HumanoidRootPart') then
                local cf = CFrame.new(v)
                local tweenTime = ((lp.Character.HumanoidRootPart.Position - cf.p).Magnitude) / speed
                local tweenInfo = TweenInfo.new(tweenTime, Enum.EasingStyle.Linear)
                local a = tweenService:Create(lp.Character.HumanoidRootPart, tweenInfo, {CFrame = cf})
                a:Play()
                a.Completed:Connect(function()
                    fireproximityprompt(closestItem.ProximityPrompt)
                end)
            end
        end
 
        for i, item in pairs(items) do
            for j, finditem in pairs(finditems) do
                if item.Name == finditem then
                    local distance = (item.Position - lp.Character.HumanoidRootPart.Position).Magnitude
                    if distance < minDistance then
                        minDistance = distance
                        closestItem = item
                    end
                end
            end
        end
 
        if closestItem then
            teleport(closestItem.Position, 60)
        end
    end)
end
end)
Section:NewButton("STOP", "หยุดหา", function()
getgenv().loop = false
local finditems = {"Box"} 
 
while getgenv().loop do
    task.wait()
    pcall(function()
        local folder = game:GetService("Workspace").Item
        local items = folder:GetChildren()
        local closestItem = nil
        local minDistance = math.huge
 
        local tweenService = game:GetService("TweenService")
        local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear)
 
        local lp = game.Players.LocalPlayer
 
        function teleport(v, speed)
            if lp.Character and lp.Character:FindFirstChild('HumanoidRootPart') then
                local cf = CFrame.new(v)
                local tweenTime = ((lp.Character.HumanoidRootPart.Position - cf.p).Magnitude) / speed
                local tweenInfo = TweenInfo.new(tweenTime, Enum.EasingStyle.Linear)
                local a = tweenService:Create(lp.Character.HumanoidRootPart, tweenInfo, {CFrame = cf})
                a:Play()
                a.Completed:Connect(function()
                    fireproximityprompt(closestItem.ProximityPrompt)
                end)
            end
        end
 
        for i, item in pairs(items) do
            for j, finditem in pairs(finditems) do
                if item.Name == finditem then
                    local distance = (item.Position - lp.Character.HumanoidRootPart.Position).Magnitude
                    if distance < minDistance then
                        minDistance = distance
                        closestItem = item
                    end
                end
            end
        end
 
        if closestItem then
            teleport(closestItem.Position, 60)
        end
    end)
end
end)
Section:NewLabel("SukunaFinger")
Section:NewButton("SukunaFinger", "หานิ้วสุคุนะ", function()
getgenv().loop = true 
local finditems = {"SukunaFinger"}
 
while getgenv().loop do
    task.wait()
    pcall(function()
        local folder = game:GetService("Workspace").Item
        local items = folder:GetChildren()
        local closestItem = nil
        local minDistance = math.huge
 
        local tweenService = game:GetService("TweenService")
        local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear)
 
        local lp = game.Players.LocalPlayer
 
        function teleport(v, speed)
            if lp.Character and lp.Character:FindFirstChild('HumanoidRootPart') then
                local cf = CFrame.new(v)
                local tweenTime = ((lp.Character.HumanoidRootPart.Position - cf.p).Magnitude) / speed
                local tweenInfo = TweenInfo.new(tweenTime, Enum.EasingStyle.Linear)
                local a = tweenService:Create(lp.Character.HumanoidRootPart, tweenInfo, {CFrame = cf})
                a:Play()
                a.Completed:Connect(function()
                    fireproximityprompt(closestItem.ProximityPrompt)
                end)
            end
        end
 
        for i, item in pairs(items) do
            for j, finditem in pairs(finditems) do
                if item.Name == finditem then
                    local distance = (item.Position - lp.Character.HumanoidRootPart.Position).Magnitude
                    if distance < minDistance then
                        minDistance = distance
                        closestItem = item
                    end
                end
            end
        end
 
        if closestItem then
            teleport(closestItem.Position, 60)
        end
    end)
end
end)
Section:NewButton("STOP", "หยุดหานิ้วสุคุนะ", function()
getgenv().loop = false 
local finditems = {"SukunaFinger"}
 
while getgenv().loop do
    task.wait()
    pcall(function()
        local folder = game:GetService("Workspace").Item
        local items = folder:GetChildren()
        local closestItem = nil
        local minDistance = math.huge
 
        local tweenService = game:GetService("TweenService")
        local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear)
 
        local lp = game.Players.LocalPlayer
 
        function teleport(v, speed)
            if lp.Character and lp.Character:FindFirstChild('HumanoidRootPart') then
                local cf = CFrame.new(v)
                local tweenTime = ((lp.Character.HumanoidRootPart.Position - cf.p).Magnitude) / speed
                local tweenInfo = TweenInfo.new(tweenTime, Enum.EasingStyle.Linear)
                local a = tweenService:Create(lp.Character.HumanoidRootPart, tweenInfo, {CFrame = cf})
                a:Play()
                a.Completed:Connect(function()
                    fireproximityprompt(closestItem.ProximityPrompt)
                end)
            end
        end
 
        for i, item in pairs(items) do
            for j, finditem in pairs(finditems) do
                if item.Name == finditem then
                    local distance = (item.Position - lp.Character.HumanoidRootPart.Position).Magnitude
                    if distance < minDistance then
                        minDistance = distance
                        closestItem = item
                    end
                end
            end
        end
 
        if closestItem then
            teleport(closestItem.Position, 60)
        end
    end)
end
end)
Section:NewLabel("Chest")
Section:NewButton("Chest", "หากล่อง", function()
getgenv().loop = true
local finditems = {"Chest"}
 
while getgenv().loop do
    task.wait()
    pcall(function()
        local folder = game:GetService("Workspace").Item
        local items = folder:GetChildren()
        local closestItem = nil
        local minDistance = math.huge
 
        local tweenService = game:GetService("TweenService")
        local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear)
 
        local lp = game.Players.LocalPlayer
 
        function teleport(v, speed)
            if lp.Character and lp.Character:FindFirstChild('HumanoidRootPart') then
                local cf = CFrame.new(v)
                local tweenTime = ((lp.Character.HumanoidRootPart.Position - cf.p).Magnitude) / speed
                local tweenInfo = TweenInfo.new(tweenTime, Enum.EasingStyle.Linear)
                local a = tweenService:Create(lp.Character.HumanoidRootPart, tweenInfo, {CFrame = cf})
                a:Play()
                a.Completed:Connect(function()
                    fireproximityprompt(closestItem.ProximityPrompt)
                end)
            end
        end
 
        for i, item in pairs(items) do
            for j, finditem in pairs(finditems) do
                if item.Name == finditem then
                    local distance = (item.Position - lp.Character.HumanoidRootPart.Position).Magnitude
                    if distance < minDistance then
                        minDistance = distance
                        closestItem = item
                    end
                end
            end
        end
 
        if closestItem then
            teleport(closestItem.Position, 60)
        end
    end)
end
end)
Section:NewButton("STOP", "หยุดหาหีบ", function()
getgenv().loop = false
local finditems = {"Chest"}
 
while getgenv().loop do
    task.wait()
    pcall(function()
        local folder = game:GetService("Workspace").Item
        local items = folder:GetChildren()
        local closestItem = nil
        local minDistance = math.huge
 
        local tweenService = game:GetService("TweenService")
        local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear)
 
        local lp = game.Players.LocalPlayer
 
        function teleport(v, speed)
            if lp.Character and lp.Character:FindFirstChild('HumanoidRootPart') then
                local cf = CFrame.new(v)
                local tweenTime = ((lp.Character.HumanoidRootPart.Position - cf.p).Magnitude) / speed
                local tweenInfo = TweenInfo.new(tweenTime, Enum.EasingStyle.Linear)
                local a = tweenService:Create(lp.Character.HumanoidRootPart, tweenInfo, {CFrame = cf})
                a:Play()
                a.Completed:Connect(function()
                    fireproximityprompt(closestItem.ProximityPrompt)
                end)
            end
        end
 
        for i, item in pairs(items) do
            for j, finditem in pairs(finditems) do
                if item.Name == finditem then
                    local distance = (item.Position - lp.Character.HumanoidRootPart.Position).Magnitude
                    if distance < minDistance then
                        minDistance = distance
                        closestItem = item
                    end
                end
            end
        end
 
        if closestItem then
            teleport(closestItem.Position, 60)
        end
    end)
end
end)
Section:NewLabel("Barrel")
Section:NewButton("Barrel", "หาถัง", function()
getgenv().loop = true
local finditems = {"Barrel"}
 
while getgenv().loop do
    task.wait()
    pcall(function()
        local folder = game:GetService("Workspace").Item
        local items = folder:GetChildren()
        local closestItem = nil
        local minDistance = math.huge
 
        local tweenService = game:GetService("TweenService")
        local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear)
 
        local lp = game.Players.LocalPlayer
 
        function teleport(v, speed)
            if lp.Character and lp.Character:FindFirstChild('HumanoidRootPart') then
                local cf = CFrame.new(v)
                local tweenTime = ((lp.Character.HumanoidRootPart.Position - cf.p).Magnitude) / speed
                local tweenInfo = TweenInfo.new(tweenTime, Enum.EasingStyle.Linear)
                local a = tweenService:Create(lp.Character.HumanoidRootPart, tweenInfo, {CFrame = cf})
                a:Play()
                a.Completed:Connect(function()
                    fireproximityprompt(closestItem.ProximityPrompt)
                end)
            end
        end
 
        for i, item in pairs(items) do
            for j, finditem in pairs(finditems) do
                if item.Name == finditem then
                    local distance = (item.Position - lp.Character.HumanoidRootPart.Position).Magnitude
                    if distance < minDistance then
                        minDistance = distance
                        closestItem = item
                    end
                end
            end
        end
 
        if closestItem then
            teleport(closestItem.Position, 60)
        end
    end)
end
end)
Section:NewButton("STOP", "หยุดหา", function()
getgenv().loop = false
local finditems = {"Barrel"}
 
while getgenv().loop do
    task.wait()
    pcall(function()
        local folder = game:GetService("Workspace").Item
        local items = folder:GetChildren()
        local closestItem = nil
        local minDistance = math.huge
 
        local tweenService = game:GetService("TweenService")
        local tweenInfo = TweenInfo.new(1, Enum.EasingStyle.Linear)
 
        local lp = game.Players.LocalPlayer
 
        function teleport(v, speed)
            if lp.Character and lp.Character:FindFirstChild('HumanoidRootPart') then
                local cf = CFrame.new(v)
                local tweenTime = ((lp.Character.HumanoidRootPart.Position - cf.p).Magnitude) / speed
                local tweenInfo = TweenInfo.new(tweenTime, Enum.EasingStyle.Linear)
                local a = tweenService:Create(lp.Character.HumanoidRootPart, tweenInfo, {CFrame = cf})
                a:Play()
                a.Completed:Connect(function()
                    fireproximityprompt(closestItem.ProximityPrompt)
                end)
            end
        end
 
        for i, item in pairs(items) do
            for j, finditem in pairs(finditems) do
                if item.Name == finditem then
                    local distance = (item.Position - lp.Character.HumanoidRootPart.Position).Magnitude
                    if distance < minDistance then
                        minDistance = distance
                        closestItem = item
                    end
                end
            end
        end
 
        if closestItem then
            teleport(closestItem.Position, 60)
        end
    end)
end
end)
Section:NewLabel("Fixbug")
Section:NewButton("เเก้บัคติดเเมพ", "เเก้บัคติดเเมพ", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-332.18096923828125, -33.014976501464844, 1418.3851318359375)
end)
-- Event
local Tab = Window:NewTab("Event")
local Section = Tab:NewSection("Event Deliver")
Plr = {}
Section:NewButton("Quest Event Deliver", "วาร์ปไปหน้ารับเควส", function()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-379.7237854003906, -32.97041320800781, 1484.1832275390625)
end)
Section:NewLabel("Teleport Present Player")
for i,v in pairs(game:GetService("Players"):GetChildren()) do
    table.insert(Plr,v.Name) 
end
local drop = Section:NewDropdown("Select Player!", "Click To Select", Plr, function(t)
   PlayerTP = t
end)
Section:NewButton("Click To TP", "", function()
    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[PlayerTP].Character.HumanoidRootPart.CFrame
end)
Section:NewToggle("Auto Tp", "", function(t)
_G.TPPlayer = t
while _G.TPPlayer do wait()
game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players[PlayerTP].Character.HumanoidRootPart.CFrame
end
end)
local Tab = Window:NewTab("Setting")
local Section = Tab:NewSection("Setting")
Section:NewKeybind("Select Keybind", "กดเพื่อพับสคริป", Enum.KeyCode.F, function()
	Library:ToggleUI()
end)
--setting
Section:NewButton("Noclip", "bypass", function()
local Noclip = nil
local Clip = nil

function noclip()
	Clip = false
	local function Nocl()
		if Clip == false and game.Players.LocalPlayer.Character ~= nil then
			for _,v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
				if v:IsA('BasePart') and v.CanCollide and v.Name ~= floatName then
					v.CanCollide = false
				end
			end
		end
		wait(0.21) 
	end
	Noclip = game:GetService('RunService').Stepped:Connect(Nocl)
end

function clip()
	if Noclip then Noclip:Disconnect() end
	Clip = true
end

noclip() 
end)

