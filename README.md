-- Configurações
local team = "Pirates" -- Opções: "Pirates", "Marines"
local autoFarm = true
local autoQuest = true

-- Função para mudar de time
local function changeTeam()
    if game.Players.LocalPlayer.Team.Name ~= team then
        local Teams = game:GetService("Teams")
        if team == "Pirates" then
            game.Players.LocalPlayer.Team = Teams.Pirates
        elseif team == "Marines" then
            game.Players.LocalPlayer.Team = Teams.Mariners
        end
    end
end

-- Função para auto farmar inimigos
local function farmEnemies()
    while autoFarm do
        for i, v in pairs(workspace.Enemies:GetChildren()) do
            if v.Humanoid and v.Humanoid.Health > 0 then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame
                firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Head, 0)
                firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Head, 1)
                wait(0.5)
            end
        end
        wait()
    end
end

-- Função para aceitar e entregar quests automaticamente
local function autoCompleteQuest()
    while autoQuest do
        local questGiver = workspace.QuestGivers:FindFirstChild("DefaultQuestGiver") -- Ajustar nome
        if questGiver then
            local dist = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - questGiver.HumanoidRootPart.Position).magnitude
            if dist > 10 then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = questGiver.HumanoidRootPart.CFrame
            end
            -- Comprar ou entregar quest via RemoteEvent
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", questGiver.Name)
            wait(1)
        end
        wait(5)
    end
end

-- Executar funções
changeTeam()
if autoFarm then
    spawn(farmEnemies)
end
if autoQuest then
    spawn(autoCompleteQuest)
end-- Configurações
local team = "Pirates" -- Opções: "Pirates", "Marines"
local autoFarm = true
local autoQuest = true

-- Função para mudar de time
local function changeTeam()
    if game.Players.LocalPlayer.Team.Name ~= team then
        local Teams = game:GetService("Teams")
        if team == "Pirates" then
            game.Players.LocalPlayer.Team = Teams.Pirates
        elseif team == "Marines" then
            game.Players.LocalPlayer.Team = Teams.Mariners
        end
    end
end

-- Função para auto farmar inimigos
local function farmEnemies()
    while autoFarm do
        for i, v in pairs(workspace.Enemies:GetChildren()) do
            if v.Humanoid and v.Humanoid.Health > 0 then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame
                firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Head, 0)
                firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, v.Head, 1)
                wait(0.5)
            end
        end
        wait()
    end
end

-- Função para aceitar e entregar quests automaticamente
local function autoCompleteQuest()
    while autoQuest do
        local questGiver = workspace.QuestGivers:FindFirstChild("DefaultQuestGiver") -- Ajustar nome
        if questGiver then
            local dist = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - questGiver.HumanoidRootPart.Position).magnitude
            if dist > 10 then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = questGiver.HumanoidRootPart.CFrame
            end
            -- Comprar ou entregar quest via RemoteEvent
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", questGiver.Name)
            wait(1)
        end
        wait(5)
    end
end

-- Executar funções
changeTeam()
if autoFarm then
    spawn(farmEnemies)
end
if autoQuest then
    spawn(autoCompleteQuest)
end
