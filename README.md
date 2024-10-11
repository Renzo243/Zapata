
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

-- Função para atacar inimigos próximos
local function attackEnemies()
    for _, enemy in pairs(game.Workspace.Enemies:GetChildren()) do
        if enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 then
            character.HumanoidRootPart.CFrame = enemy.HumanoidRootPart.CFrame
            wait(0.5) -- Tempo de espera entre os ataques
            character.Humanoid:MoveTo(enemy.HumanoidRootPart.Position)
        end
    end
end

-- Loop para continuar atacando inimigos
while true do
    attackEnemies()
    wait(1) -- Tempo de espera entre cada ciclo de ataque
end
