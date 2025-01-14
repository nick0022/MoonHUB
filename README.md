local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

 -- Primeira notificação - Menu carregando
 Rayfield:Notify({
    Title = "Loading...",
    Content = "The menu is loading. Please wait...",
    Duration = 5, -- Duração de 5 segundos
    Image = 4483362458, -- Ícone (opcional)
    Actions = {
        Ignore = {
            Name = "Okay",
            Callback = function()
                print("User acknowledged the notification.")
            end
        },
    },
})

-- Segunda notificação - Após a primeira desaparecer
task.wait(5)  -- Aguarda 5 segundos até que a primeira notificação desapareça

-- Notificação de BETA
Rayfield:Notify({
    Title = "Moon Hub (V1.4.0)",
    Content = "Thank you for choosing us!",
    Duration = 5, -- Duração de 5 segundos
    Image = 4483362458, -- Ícone (opcional)
    Actions = {
        Ignore = {
            Name = "Okay",
            Callback = function()
                print("User acknowledged the notification.")
            end
        },
    },
})

local Window = Rayfield:CreateWindow({
    Name = "Moon HUB",
    Icon = 4483362458,
    LoadingTitle = "Premium HUB",
    LoadingSubtitle = "by lk_.12",
    Theme = "Default",

    DisableRayfieldPrompts = false,
    DisableBuildWarnings = false,

    ConfigurationSaving = {
        Enabled = true,
        FolderName = nil,
        FileName = "configsave"
    },
    Discord = {
        Enabled = true,
        Invite = "4VZtWGmp4g",
        RememberJoins = true
    },
    KeySystem = true,
    KeySettings = {
        Title = "Moon HUB - V1.4.0",
        Subtitle = "Key System",
        Note = "• Buy your key on the official HUB discord",
        FileName = "keymoonhub",
        SaveKey = true,
        GrabKeyFromSite = false,
        Key = {"devtest2025"},
        Actions = {
            [1] = {
                Text = 'Click here to copy the discord link (Mandatory) <--',
                OnPress = function()
                    setclipboard("https://discord.gg/4VZtWGmp4g")
                    Rayfield:Notify({
                        Title = "🔗 Discord Copied",
                        Content = "The Discord link has been copied to your clipboard!",
                        Duration = 5,
                        Image = 4483362458,
                        Actions = {
                            Ignore = {
                                Name = "Ok",
                                Callback = function()
                                    print("User acknowledged the notification.")
                                end
                            }
                        }
                    })
                end
            }
        }
    }
})

Window:Prompt({
    Title = 'Terms of use',
    SubTitle = '',
    Content = '• Forbidden to sell the key without being a reseller.\n• Forbidden to pass your key to other people\n• Mandatory to be on the official HUB discord\n• By clicking on accept the terms of use and breaking a rule you can lose your key or be blacklisted from the HUB forever',
    Actions = {
        Accept = {
            Name = 'Accept',
            Callback = function()
                print('Pressed')
            end,
        }
    }
})

local Tabcredits = Window:CreateTab("Credits", 4483362458)
local Tabupdates = Window:CreateTab("Updates", 4483362458)
local Tabfarm = Window:CreateTab("Farm", 4483362458)
local Tabpvp = Window:CreateTab("PVP", 4483362458)
local Tabskins = Window:CreateTab("Skins", 4483362458)
local Tabscripts = Window:CreateTab("Scripts", 4483362458)
local Tabteleports = Window:CreateTab("Teleports", 4483362458)
local Tabmisc = Window:CreateTab("Misc", 4483362458)

local SectionCredits = Tabcredits:CreateSection("Credits", false)
local SectionUpdates = Tabupdates:CreateSection("Updates", false)
local SectionFarm = Tabfarm:CreateSection("Key farm functions", false)
local SectionPVP = Tabpvp:CreateSection("Main functions of pvp", false)
local SectionSkins = Tabskins:CreateSection("Unlock skins with one click", false)
local SectionScripts = Tabscripts:CreateSection("Recommended Scripts", false)
local SectionTeleports = Tabteleports:CreateSection("Teleport locations for easy locomotion", false)
local SectionMisc = Tabmisc:CreateSection("Other extra functions", false)

-- Toggle para Free Radio
SectionMisc:CreateToggle({
    Name = "🎵 Free Radio",
    CurrentValue = false, -- Valor inicial: desligado
    Flag = "FreeRadioToggle", -- Identificador único
    Callback = function(state)
        -- Ativar ou desativar o Free Radio
        if state then
            game.Players.LocalPlayer.PlayerGui.DRadio_Gui.Enabled = true
            Rayfield:Notify({
                Title = "🎵 Free Radio Activated!",
                Content = "Free Radio has been activated!",
                Duration = 5,
                Image = 4483362458 -- Ícone opcional
            })
        else
            game.Players.LocalPlayer.PlayerGui.DRadio_Gui.Enabled = false
            Rayfield:Notify({
                Title = "🎵 Free Radio Deactivated",
                Content = "Free Radio has been deactivated!",
                Duration = 5,
                Image = 4483362458 -- Ícone opcional
            })
        end
    end
})

-- Toggle para Free 13x Exp
SectionMisc:CreateToggle({
    Name = "🧬 Visual 13x Exp",
    CurrentValue = false, -- Valor inicial: desligado
    Flag = "Free13xExpToggle", -- Identificador único
    Callback = function(state)
        -- Ativar ou desativar o Free 13x Exp
        if state then
            game.Players.LocalPlayer.PlayerGui.LevelBar.gamepassText.Visible = true
            game.Players.LocalPlayer.PlayerGui.LevelBar.gamepassText.Text = "13x exp"
            Rayfield:Notify({
                Title = "🧬 Free 13x Exp activated",
                Content = "13x Exp has been activated!",
                Duration = 5,
                Image = 4483362458 -- Ícone opcional
            })
        else
            game.Players.LocalPlayer.PlayerGui.LevelBar.gamepassText.Visible = false
            Rayfield:Notify({
                Title = "🧬 Free 13x Exp deactivated",
                Content = "13x Exp has been deactivated!",
                Duration = 5,
                Image = 4483362458 -- Ícone opcional
            })
        end
    end
})

SectionScripts:CreateButton({
    Name = "💻 Moon Yield",
    Callback = function()
        -- Carrega e executa o script
        loadstring(game:HttpGet('https://raw.githubusercontent.com/nick0022/moonyield/main/README.md', true))()
        -- Exibe uma notificação usando Rayfield
        Rayfield:Notify({
            Title = "💻 Moon Yield",
            Content = "The Moon Yield has been executed!", -- Corrigido o texto da mensagem
            Duration = 5, -- Tempo da notificação em segundos
            Image = 4483362458, -- Opcional: Ícone da notificação
            Actions = {
                Ignore = {
                    Name = "Ok", -- Nome do botão
                    Callback = function()
                        print("User acknowledged the notification.")
                    end
                }
            }
        })
    end
})

SectionTeleports:CreateParagraph({
    Title = "Teleport Locations",
    Content = "Teleport locations for easy locomotion",
    BackgroundColor = Color3.fromRGB(51, 51, 51),  -- Cor de fundo da seção
    TextColor = Color3.fromRGB(255, 255, 255),      -- Cor do texto
    Icon = "rbxassetid://4483362458",                -- Ícone de créditos, você pode alterar o ID
    TextSize = 16,                                  -- Tamanho da fonte
})

SectionTeleports:CreateButton({
    Name = "🛡️ Safe Zone",
    Callback = function()
        local targetPosition = Vector3.new(-105.29137420654297, 642.4719848632812, 514.2374877929688) -- Coordenadas da Safe Zone
        if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(targetPosition)
            Rayfield:Notify({
                Title = "🛡️ Safe Zone",
                Content = "You have been teleported successfully!",
                Duration = 5,
                Image = 4483362458
            })
        end
    end
})

SectionTeleports:CreateButton({
    Name = "🏜️ Desert",
    Callback = function()
        local targetPosition = Vector3.new(-672.6334838867188, 642.568603515625, 1115.691162109375) -- Coordenadas do Desert
        if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(targetPosition)
            Rayfield:Notify({
                Title = "🏜️ Desert",
                Content = "You have been teleported successfully!",
                Duration = 5,
                Image = 4483362458
            })
        end
    end
})

SectionTeleports:CreateButton({
    Name = "🌋 Volcano",
    Callback = function()
        local targetPosition = Vector3.new(120.21180725097656, 685.631103515625, 1570.7666015625) -- Coordenadas do Volcano
        if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(targetPosition)
            Rayfield:Notify({
                Title = "🌋 Volcano",
                Content = "You have been teleported successfully!",
                Duration = 5,
                Image = 4483362458
            })
        end
    end
})

SectionTeleports:CreateButton({
    Name = "🏖️ Beach",
    Callback = function()
        local targetPosition = Vector3.new(-29.751022338867188, 644.6039428710938, -70.5428695678711) -- Coordenadas da Beach
        if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(targetPosition)
            Rayfield:Notify({
                Title = "🏖️ Beach",
                Content = "You have been teleported successfully!",
                Duration = 5,
                Image = 4483362458
            })
        end
    end
})

SectionTeleports:CreateButton({
    Name = "☁️ Cloud Arena",
    Callback = function()
        local targetPosition = Vector3.new(-1173.7010498046875, 1268.14404296875, 766.4228515625) -- Coordenadas do Cloud Arena
        if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(targetPosition)
            Rayfield:Notify({
                Title = "☁️ Cloud Arena",
                Content = "You have been teleported successfully!",
                Duration = 5,
                Image = 4483362458
            })
        end
    end
})

-- Coin Farm
local isFarming = false

local function coinFarmLoop()
    while isFarming do
        pcall(function()
            game:GetService("ReplicatedStorage").Events.CoinEvent:FireServer()
        end)
        task.wait(0.1)
    end
end

SectionFarm:CreateToggle({
    Name = "💰 Coin Farm",
    CurrentValue = false,
    Flag = "Farm",
    Callback = function(Value)
        isFarming = Value
        
        if isFarming then
            task.spawn(coinFarmLoop)
            -- Notificação quando ativado
            Rayfield:Notify({
                Title = "💰 Coin Farm Activated",
                Content = "Coin Farm has been activated.",
                Duration = 5, -- Duração de 5 segundos
                Image = 4483362458, -- Ícone (opcional)
                Actions = {
                    Ignore = {
                        Name = "Okay",
                        Callback = function()
                            print("User acknowledged the notification.")
                        end
                    }
                }
            })
        else
            -- Notificação quando desativado
            Rayfield:Notify({
                Title = "💰 Coin Farm Deactivated",
                Content = "Coin Farm has been deactivated.",
                Duration = 5, -- Duração de 5 segundos
                Image = 4483362458, -- Ícone (opcional)
                Actions = {
                    Ignore = {
                        Name = "Okay",
                        Callback = function()
                            print("User acknowledged the notification.")
                        end
                    }
                }
            })
        end
    end
})

SectionFarm:CreateToggle({
    Name = "👹 Boss Farm",
    CurrentValue = false,
    Flag = "BossFarmToggle", -- Identificador único para a configuração
    Callback = function(Value)
        _G.attackAllNPCToggle = Value

        if Value then
            spawn(function()
                while _G.attackAllNPCToggle do
                    if not _G.attackAllNPCToggle then 
                        break 
                    end
                    
                    local npcsWithHealth = {}
                    for _, npc in ipairs(workspace.NPC:GetDescendants()) do
                        if npc:IsA("Humanoid") and npc.Health > 0 then
                            table.insert(npcsWithHealth, {
                                humanoid = npc,
                                health = npc.Health
                            })
                        end
                    end
                    
                    table.sort(npcsWithHealth, function(a, b)
                        return a.health < b.health
                    end)
                    
                    for _, npcData in ipairs(npcsWithHealth) do
                        if _G.attackAllNPCToggle then
                            local args = {
                                [1] = npcData.humanoid,
                                [2] = 1
                            }
                            game:GetService("ReplicatedStorage").jdskhfsIIIllliiIIIdchgdIiIIIlIlIli:FireServer(unpack(args))
                        end
                    end
                    
                    task.wait(0.01)
                end
            end)

            Rayfield:Notify({
                Title = "👹 Boss Farm Activated",
                Content = "Boss farming is now active.",
                Duration = 5,
                Image = 4483362458,
                Actions = {
                    Ignore = {
                        Name = "Stop",
                        Callback = function()
                            _G.attackAllNPCToggle = false
                            print("Boss farm has been stopped.")
                        end
                    }
                }
            })
        else
            Rayfield:Notify({
                Title = "👹 Boss Farm Deactivated",
                Content = "Boss farming has been stopped.",
                Duration = 5,
                Image = 4483362458
            })
        end
    end
})


-- Dummy Farm
local dummyFarmActive = false
local dummyFarmConnection

SectionFarm:CreateToggle({
    Name = "🎃 Dummy Farm",
    CurrentValue = false,
    Flag = "DummyFarm",
    Callback = function(Value)
        dummyFarmActive = Value
        if dummyFarmActive then
            dummyFarmConnection = game:GetService("RunService").Heartbeat:Connect(function()
                local targetDummy = workspace.MAP.dummies:GetChildren()[1]
                if targetDummy and game.Players.LocalPlayer.Character then
                    local humanoid = targetDummy:FindFirstChild("Humanoid")
                    local rootPart = targetDummy:FindFirstChild("HumanoidRootPart")
                    local playerRoot = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")

                    if humanoid and rootPart and playerRoot then
                        playerRoot.CFrame = rootPart.CFrame * CFrame.new(0, 8, 0)
                        game:GetService("ReplicatedStorage").jdskhfsIIIllliiIIIdchgdIiIIIlIlIli:FireServer(humanoid, 1)
                    end
                end
            end)
            -- Notificação quando ativado
            Rayfield:Notify({
                Title = "🎃 Dummy Farm Activated",
                Content = "Dummy Farm has been activated.",
                Duration = 5, -- Duração de 5 segundos
                Image = 4483362458, -- Ícone (opcional)
                Actions = {
                    Ignore = {
                        Name = "Okay",
                        Callback = function()
                            print("User acknowledged the notification.")
                        end
                    }
                }
            })
        else
            if dummyFarmConnection then
                dummyFarmConnection:Disconnect()
                dummyFarmConnection = nil
            end
            -- Notificação quando desativado
            Rayfield:Notify({
                Title = "🎃 Dummy Farm Deactivated",
                Content = "Dummy Farm has been deactivated.",
                Duration = 5, -- Duração de 5 segundos
                Image = 4483362458, -- Ícone (opcional)
                Actions = {
                    Ignore = {
                        Name = "Okay",
                        Callback = function()
                            print("User acknowledged the notification.")
                        end
                    }
                }
            })
        end
    end
})

-- Dummy 5k Farm
_G.dummyFarm5kEnabled = false

SectionFarm:CreateToggle({
    Name = "🎃 Dummy 5k Farm",
    CurrentValue = false,
    Flag = "DummyFarm5k",
    Callback = function(Value)
        _G.dummyFarm5kEnabled = Value

        if _G.dummyFarm5kEnabled then
            spawn(function()
                while _G.dummyFarm5kEnabled do
                    local dummies = workspace.MAP["5k_dummies"]:GetChildren()
                    local targetDummy = nil
                    local shortestDistance = math.huge

                    -- Seleção de dummy específico (Dummy2)
                    for _, dummy in pairs(dummies) do
                        if dummy.Name == "Dummy2" then -- Aqui você pode mudar para outros nomes específicos de Dummy
                            if dummy:FindFirstChild("Humanoid") and dummy:FindFirstChild("HumanoidRootPart") then
                                local isOccupied = false
                                local dummyRoot = dummy.HumanoidRootPart

                                -- Verifica se algum jogador está perto do dummy
                                for _, player in pairs(game.Players:GetPlayers()) do
                                    if player.Character and player ~= game.Players.LocalPlayer then
                                        local playerRoot = player.Character:FindFirstChild("HumanoidRootPart")
                                        if playerRoot and (playerRoot.Position - dummyRoot.Position).Magnitude < 10 then
                                            isOccupied = true
                                            break
                                        end
                                    end
                                end

                                -- Se não estiver ocupado, calcula a distância e seleciona o melhor alvo
                                if not isOccupied then
                                    local distance = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - dummyRoot.Position).Magnitude
                                    if distance < shortestDistance then
                                        shortestDistance = distance
                                        targetDummy = dummy
                                    end
                                end
                            end
                        end
                    end

                    -- Ataca o dummy alvo
                    if targetDummy and game.Players.LocalPlayer.Character then
                        local humanoid = targetDummy:FindFirstChild("Humanoid")
                        local rootPart = targetDummy:FindFirstChild("HumanoidRootPart")
                        local playerRoot = game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart")

                        if humanoid and rootPart and playerRoot then
                            playerRoot.CFrame = rootPart.CFrame * CFrame.new(0, 8, 0)
                            game:GetService("ReplicatedStorage").jdskhfsIIIllliiIIIdchgdIiIIIlIlIli:FireServer(humanoid, 1)
                        end
                    end

                    task.wait() -- Espera antes de verificar novamente
                end
            end)
            -- Notificação quando ativado
            Rayfield:Notify({
                Title = "🎃 Dummy 5k Farm Activated",
                Content = "Dummy 5k Farm has been activated.",
                Duration = 5, -- Duração de 5 segundos
                Image = 4483362458, -- Ícone (opcional)
                Actions = {
                    Ignore = {
                        Name = "Okay",
                        Callback = function()
                            print("User acknowledged the notification.")
                        end
                    }
                }
            })
        else
            -- Notificação quando desativado
            Rayfield:Notify({
                Title = "🎃 Dummy 5k Farm Deactivated",
                Content = "Dummy 5k Farm has been deactivated.",
                Duration = 5, -- Duração de 5 segundos
                Image = 4483362458, -- Ícone (opcional)
                Actions = {
                    Ignore = {
                        Name = "Okay",
                        Callback = function()
                            print("User acknowledged the notification.")
                        end
                    }
                }
            })
        end
    end
})

-- Auto Comer
-- Função de clique na tela (PC e Celular)
local VirtualInputManager = game:GetService("VirtualInputManager")
local function clickAtScreenPosition(x, y)
    -- Envia o clique de forma eficiente
    VirtualInputManager:SendMouseButtonEvent(x, y, 0, true, game, 0)
    task.wait(0.05)
    VirtualInputManager:SendMouseButtonEvent(x, y, 0, false, game, 0)
end

-- Função de Auto Comer
local autoEat = false
local function autoEatLoop()
    while autoEat do
        pcall(function()
            -- Seleciona o slot de comida (tecla "1")
            VirtualInputManager:SendKeyEvent(true, "One", false, game)
            task.wait(0.1)
            VirtualInputManager:SendKeyEvent(false, "One", false, game)

            -- Aguarda para garantir que a comida foi selecionada
            task.wait(0.1)

            -- Verifica se é celular ou PC e realiza o clique na tela de forma segura
            local userInputService = game:GetService("UserInputService")
            local screenCenterX = workspace.CurrentCamera.ViewportSize.X * 0.5 -- Centro X
            local screenCenterY = workspace.CurrentCamera.ViewportSize.Y * 0.7 -- Posição Y ajustável

            if userInputService.TouchEnabled then
                -- Se for celular, realiza o clique em uma posição ajustada para o celular
                clickAtScreenPosition(screenCenterX, screenCenterY)
            else
                -- Se for PC, realiza o clique em uma posição ajustada para o PC
                clickAtScreenPosition(screenCenterX, screenCenterY)
            end
        end)
        task.wait(1) -- Intervalo entre as ações
    end
end

-- Toggle de Auto Comer
SectionPVP:CreateToggle({
    Name = "🦐 Auto Eat (PC)",
    CurrentValue = false,
    Flag = "AutoEat",
    Callback = function(Value)
        autoEat = Value
        if autoEat then
            task.spawn(autoEatLoop) -- Inicia o loop de Auto Comer

            -- Notificação ao ativar
            Rayfield:Notify({
                Title = "🦐 Auto Eat Activated",
                Content = "Auto Eat has been activated.",
                Duration = 5, -- Duração de 5 segundos
                Image = 4483362458, -- Ícone (opcional)
                Actions = {
                    Ignore = {
                        Name = "Okay",
                        Callback = function()
                            print("User acknowledged the notification.")
                        end
                    }
                }
            })
        else
            -- Notificação ao desativar
            Rayfield:Notify({
                Title = "🦐 Auto Eat Deactivated",
                Content = "Auto Eat has been deactivated.",
                Duration = 5, -- Duração de 5 segundos
                Image = 4483362458, -- Ícone (opcional)
                Actions = {
                    Ignore = {
                        Name = "Okay",
                        Callback = function()
                            print("User acknowledged the notification.")
                        end
                    }
                }
            })
        end
    end
})

-- Adicionando Kill Aura na aba PVP
SectionPVP:CreateToggle({
    Name = "💥 Kill Aura",
    CurrentValue = false,
    Flag = "KillAura",
    Callback = function(Value)
        _G.killAura = Value

        local Players = game:GetService("Players")
        local ReplicatedStorage = game:GetService("ReplicatedStorage")
        local localPlayer = Players.LocalPlayer

        if _G.killAura then
            -- Notificação ao ativar Kill Aura
            Rayfield:Notify({
                Title = "💥 Kill Aura Activated",
                Content = "Kill Aura is now active.",
                Duration = 5, -- Duração de 5 segundos
                Image = 4483362458, -- Ícone (opcional)
                Actions = {
                    Ignore = {
                        Name = "Okay",
                        Callback = function()
                            print("User acknowledged the notification.")
                        end
                    }
                }
            })

            spawn(function()
                while _G.killAura do
                    for _, player in ipairs(Players:GetPlayers()) do
                        if player ~= localPlayer and 
                           player.Character and 
                           player.Character:FindFirstChildOfClass("Humanoid") and
                           player.Character:FindFirstChildOfClass("Humanoid").Health > 0 and
                           not player.Character:FindFirstChild("SafeZoneShield") then
                            
                            local args = {
                                [1] = player.Character:FindFirstChildOfClass("Humanoid"),
                                [2] = 5
                            }
                            ReplicatedStorage.jdskhfsIIIllliiIIIdchgdIiIIIlIlIli:FireServer(unpack(args))
                        end
                    end
                    task.wait()  
                end
            end)
        else
            -- Notificação ao desativar Kill Aura
            Rayfield:Notify({
                Title = "💥 Kill Aura Deactivated",
                Content = "Kill Aura is now inactive.",
                Duration = 5, -- Duração de 5 segundos
                Image = 4483362458, -- Ícone (opcional)
                Actions = {
                    Ignore = {
                        Name = "Okay",
                        Callback = function()
                            print("User acknowledged the notification.")
                        end
                    }
                }
            })
        end
    end
})

-- Christmas Skins
SectionSkins:CreateButton({
    Name = "🎅 Christmas Skins",
    Callback = function()
        local skinCodes = {
            "XM24Fr", "XM24Bear", "XM24Eag",
            "XM24Br", "XM24Cr", "XM24Sq"
        }

        local skinEvent = game:GetService("ReplicatedStorage").Events.SkinClickEvent

        -- Notification saying the skins have been unlocked
        Rayfield:Notify({
            Title = "🎅 Christmas Skins",
            Content = "The Christmas skins have been unlocked.",
            Duration = 5, -- Duration of 5 seconds
            Image = 4483362458, -- Icon (optional)
            Actions = {
                Ignore = {
                    Name = "Okay",
                    Callback = function()
                        print("User acknowledged the notification.")
                    end
                }
            }
        })

        spawn(function()
            while true do
                for _, skinCode in ipairs(skinCodes) do
                    skinEvent:FireServer(skinCode, "v2")
                    task.wait(0.1) -- Interval between events
                end
                task.wait(1) -- Interval between cycles
            end
        end)
    end,
})


-- PIG Skins
SectionSkins:CreateButton({
    Name = "🐖 PIG Skins",
    Callback = function()
        local pigs = {"PIG7", "PIG6", "PIG5", "PIG4", "PIG3", "PIG2", "PIG1", "PIG8"}

        -- Notification saying the skins have been unlocked
        Rayfield:Notify({
            Title = "🐖 PIG Skins",
            Content = "The PIG skins have been unlocked.",
            Duration = 5, -- Duration of 5 seconds
            Image = 4483362458, -- Icon (optional)
            Actions = {
                Ignore = {
                    Name = "Okay",
                    Callback = function()
                        print("User acknowledged the notification.")
                    end
                }
            }
        })

        spawn(function()
            while true do
                for _, pigName in ipairs(pigs) do
                    local args = {
                        [1] = pigName,
                        [2] = "v2"
                    }
                    game:GetService("ReplicatedStorage").Events.SkinClickEvent:FireServer(unpack(args))
                    task.wait(0.1) -- Interval between events
                end
                task.wait(1) -- Interval between cycles
            end
        end)
    end,
})

SectionCredits:CreateParagraph({
    Title = "",
    Content = "Developed by lk_.12 and Special hug to GolddeathNinja who helped me create the hub",
    BackgroundColor = Color3.fromRGB(51, 51, 51),  -- Cor de fundo da seção
    TextColor = Color3.fromRGB(255, 255, 255),      -- Cor do texto
    Icon = "rbxassetid://4483362458",                -- Ícone de créditos, você pode alterar o ID
    TextSize = 16,                                  -- Tamanho da fonte
})


SectionCredits:CreateButton({
    Name = "🔗 Copy Discord",
    Callback = function()
        setclipboard("https://discord.gg/xtPvBmWUNh") -- Substitua pelo seu link do Discord
        Rayfield:Notify({
            Title = "🔗 Discord Copied",
            Content = "The Discord link has been copied to your clipboard!",
            Duration = 5, -- Duração em segundos
            Image = 4483362458, -- Opcional: Ícone da notificação
            Actions = { -- Opcional: Adicionar botões na notificação
                Ignore = {
                    Name = "Ok",
                    Callback = function()
                        print("User acknowledged the notification.")
                    end
                }
            }
        })
    end
})

SectionCredits:CreateParagraph({
    Title = "Official Partners",
    Content = "HUB Partners:",
    BackgroundColor = Color3.fromRGB(51, 51, 51),  -- Cor de fundo da seção
    TextColor = Color3.fromRGB(255, 255, 255),      -- Cor do texto
    Icon = "rbxassetid://4483362458",                -- Ícone de créditos, você pode alterar o ID
    TextSize = 16,                                  -- Tamanho da fonte
})

SectionCredits:CreateButton({
    Name = "🤝 Rankalf",
    Callback = function()
        setclipboard("https://discord.gg/4VZtWGmp4g") -- Substitua pelo seu link do Discord
        Rayfield:Notify({
            Title = "🤝 Discord Partner",
            Content = "The Discord Partner link has been copied to your clipboard!",
            Duration = 5, -- Duração em segundos
            Image = 4483362458, -- Opcional: Ícone da notificação
            Actions = { -- Opcional: Adicionar botões na notificação
                Ignore = {
                    Name = "Ok",
                    Callback = function()
                        print("User acknowledged the notification.")
                    end
                }
            }
        })
    end
})

SectionCredits:CreateParagraph({
    Title = "Official Resellers",
    Content = "HUB Resellers:",
    BackgroundColor = Color3.fromRGB(51, 51, 51),  -- Cor de fundo da seção
    TextColor = Color3.fromRGB(255, 255, 255),      -- Cor do texto
    Icon = "rbxassetid://4483362458",                -- Ícone de créditos, você pode alterar o ID
    TextSize = 16,                                  -- Tamanho da fonte
})

SectionCredits:CreateButton({
    Name = "🤝 Rankalf",
    Callback = function()
        setclipboard("https://discord.gg/4VZtWGmp4g") -- Substitua pelo seu link do Discord
        Rayfield:Notify({
            Title = "🤝 Discord Partner",
            Content = "The Discord Reseller link has been copied to your clipboard!",
            Duration = 5, -- Duração em segundos
            Image = 4483362458, -- Opcional: Ícone da notificação
            Actions = { -- Opcional: Adicionar botões na notificação
                Ignore = {
                    Name = "Ok",
                    Callback = function()
                        print("User acknowledged the notification.")
                    end
                }
            }
        })
    end
})

SectionUpdates:CreateParagraph({
    Title = "Version 1.0.0",
    Content = "Initial release of Moon Hub\n\n• Added Coin Farm\n• Added Dummy Farm\n• Added Auto Eat\n• Added PVP features\n• Implemented skins and Misc functionality.",
    BackgroundColor = Color3.fromRGB(51, 51, 51),  -- Cor de fundo da seção
    TextColor = Color3.fromRGB(255, 255, 255),      -- Cor do texto
    Icon = "rbxassetid://4483362458",                -- Ícone de atualização, você pode alterar o ID
    TextSize = 16,                                  -- Tamanho da fonte
})

SectionUpdates:CreateParagraph({
    Title = "Version 1.1.0",
    Content = "New features added!\n\n• Implemented Kill Aura in PVP\n• Fixed bugs in Dummy Farm\n• Added new skins: Natal Skins and PIG Skins",
    BackgroundColor = Color3.fromRGB(60, 60, 60),
    TextColor = Color3.fromRGB(255, 255, 255),
    Icon = "rbxassetid://4483362458",
    TextSize = 16,
})

SectionUpdates:CreateParagraph({
    Title = "Version 1.2.0",
    Content = "Bug fixes and optimizations\n\n• Fixed issues with Auto Eat\n• Enhanced performance of Coin Farm\n• Improved UI experience for mobile users.",
    BackgroundColor = Color3.fromRGB(51, 51, 51),
    TextColor = Color3.fromRGB(255, 255, 255),
    Icon = "rbxassetid://4483362458",
    TextSize = 16,
})

SectionUpdates:CreateParagraph({
    Title = "Version 1.2.5",
    Content = "Design improvements and new tabs!\n\n• Added new Credits tab\n• Added new Updates tab\n• Improved hub design.",
    BackgroundColor = Color3.fromRGB(51, 51, 51),
    TextColor = Color3.fromRGB(255, 255, 255),
    Icon = "rbxassetid://4483362458",
    TextSize = 16,
})

SectionUpdates:CreateParagraph({
    Title = "Version 1.3.0",
    Content = "New functions and tabs added!\n\n• Added new Scripts tab\n• Added new Teleport tab\n• Improved design\n• Added Boss Farm \n• Added new teleport locations.",
    BackgroundColor = Color3.fromRGB(51, 51, 51),
    TextColor = Color3.fromRGB(255, 255, 255),
    Icon = "rbxassetid://4483362458",
    TextSize = 16,
})

SectionUpdates:CreateParagraph({
    Title = "Version 1.4.0",
    Content = "Improved design and added new functions and tabs!\n\n• Added new Trool tab\n• Added new Visual 13x exp\n• Added Free Radio\n• Added New Library.",
    BackgroundColor = Color3.fromRGB(51, 51, 51),
    TextColor = Color3.fromRGB(255, 255, 255),
    Icon = "rbxassetid://4483362458",
    TextSize = 16,
})

SectionUpdates:CreateSeparator({
    Name = "--- New Updates Coming Soon ---",  -- Adiciona uma linha divisória
    Color = Color3.fromRGB(255, 255, 255),   -- Cor da linha divisória
    LineThickness = 2,                        -- Espessura da linha
})

Rayfield:LoadConfiguration()
