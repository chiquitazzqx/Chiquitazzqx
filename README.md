-- Steal a Brainrot - Script Open Source Simplificado
-- Feito por: Chiquitazzqx

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UIS = game:GetService("UserInputService")
local player = Players.LocalPlayer

-- Cria GUI
local screenGui = Instance.new("ScreenGui", game:GetService("CoreGui"))
screenGui.Name = "StealABrainrotGUI"

local mainFrame = Instance.new("Frame", screenGui)
mainFrame.Size = UDim2.new(0, 300, 0, 400)
mainFrame.Position = UDim2.new(0.5, -150, 0.5, -200)
mainFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
mainFrame.Active = true
mainFrame.Draggable = true

local title = Instance.new("TextLabel", mainFrame)
title.Size = UDim2.new(1, 0, 0, 50)
title.BackgroundTransparency = 1
title.TextColor3 = Color3.new(1, 1, 1)
title.Font = Enum.Font.GothamBold
title.TextSize = 24
title.Text = "Chiquitazzqx Script"
title.TextScaled = true

-- Função para criar botões
local function createButton(text, posY)
    local btn = Instance.new("TextButton", mainFrame)
    btn.Size = UDim2.new(0, 260, 0, 40)
    btn.Position = UDim2.new(0, 20, 0, posY)
    btn.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    btn.TextColor3 = Color3.new(1, 1, 1)
    btn.Font = Enum.Font.Gotham
    btn.TextSize = 20
    btn.Text = text
    btn.AutoButtonColor = true
    return btn
end

-- Variáveis de controle
local autoSteal = false
local autoCollect = false
local speedHack = false

-- Botão Auto Steal
local btnAutoSteal = createButton("Auto Steal: OFF", 70)
btnAutoSteal.MouseButton1Click:Connect(function()
    autoSteal = not autoSteal
    btnAutoSteal.Text = "Auto Steal: " .. (autoSteal and "ON" or "OFF")
end)

-- Botão Auto Collect
local btnAutoCollect = createButton("Auto Collect: OFF", 120)
btnAutoCollect.MouseButton1Click:Connect(function()
    autoCollect = not autoCollect
    btnAutoCollect.Text = "Auto Collect: " .. (autoCollect and "ON" or "OFF")
end)

-- Botão Speed Hack
local btnSpeedHack = createButton("Speed Hack: OFF", 170)
btnSpeedHack.MouseButton1Click:Connect(function()
    speedHack = not speedHack
    btnSpeedHack.Text = "Speed Hack: " .. (speedHack and "ON" or "OFF")
    if not speedHack and player.Character and player.Character:FindFirstChildOfClass("Humanoid") then
        player.Character:FindFirstChildOfClass("Humanoid").WalkSpeed = 16
    end
end)

-- Lógica do script em loop
RunService.Heartbeat:Connect(function()
    if autoSteal then
        -- Código para roubar Brainrot automaticamente
        for _, plr in pairs(Players:GetPlayers()) do
            if plr ~= player and plr.Character and plr.Character:FindFirstChild("Brainrot") then
                local brainrot = plr.Character.Brainrot
                -- Teleportar para a base do jogador para roubar (exemplo)
                player.Character.HumanoidRootPart.CFrame = brainrot.CFrame + Vector3.new(0,5,0)
                wait(0.5)
            end
        end
    end
    
    if autoCollect then
        -- Código para coletar dinheiro automático
        for _, obj in pairs(workspace:GetChildren()) do
            if obj.Name == "Cash" and (obj.Position - player.Character.HumanoidRootPart.Position).Magnitude < 30 then
                player.Character.HumanoidRootPart.CFrame = obj.CFrame
                wait(0.2)
            end
        end
    end
    
    if speedHack and player.Character and player.Character:FindFirstChildOfClass("Humanoid") then
        player.Character:FindFirstChildOfClass("Humanoid").WalkSpeed = 40
    end
end)## Hi there 👋

<!--
**chiquitazzqx/Chiquitazzqx** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
