local Gui = Instance.new("ScreenGui")
local Background = Instance.new("Frame")
local ScrollingFrame = Instance.new("ScrollingFrame")  -- Scrolling frame to allow scrolling
local SpeedButton = Instance.new("TextButton")
local InvisibleButton = Instance.new("TextButton")
local HideButton = Instance.new("TextButton")
local OpenButton = Instance.new("TextButton")
local FlingButton = Instance.new("TextButton")
local FlyButton = Instance.new("TextButton")
local TargetAssistButton = Instance.new("TextButton")  -- New Button for Target Assist

Gui.Name = "Admin Commands"
Gui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
Gui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
Gui.ResetOnSpawn = false

Background.Name = "Background"
Background.Parent = Gui
Background.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
Background.Position = UDim2.new(0.330477357, 0, 0.222664014, 0)
Background.Size = UDim2.new(0, 169, 0, 198)
Background.Active = true
Background.Draggable = true

-- Create a ScrollingFrame to hold the buttons
ScrollingFrame.Name = "ScrollingFrame"
ScrollingFrame.Parent = Background
ScrollingFrame.BackgroundTransparency = 1
ScrollingFrame.Position = UDim2.new(0, 0, 0, 50)
ScrollingFrame.Size = UDim2.new(1, 0, 1, -50)
ScrollingFrame.CanvasSize = UDim2.new(0, 0, 0, 400)
ScrollingFrame.ScrollBarThickness = 8
ScrollingFrame.ScrollBarImageTransparency = 0.7

-- Speed Button
SpeedButton.Name = "SpeedButton"
SpeedButton.Parent = ScrollingFrame
SpeedButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
SpeedButton.BackgroundTransparency = 0.900
SpeedButton.Size = UDim2.new(0, 112, 0, 38)
SpeedButton.Font = Enum.Font.PatrickHand
SpeedButton.Text = "Speed 50"
SpeedButton.TextColor3 = Color3.fromRGB(255, 255, 255)
SpeedButton.TextSize = 30.000
SpeedButton.TextWrapped = true

-- Invisible Me Button
InvisibleButton.Name = "InvisibleButton"
InvisibleButton.Parent = ScrollingFrame
InvisibleButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
InvisibleButton.BackgroundTransparency = 0.900
InvisibleButton.Position = UDim2.new(0, 0, 0, 50)
InvisibleButton.Size = UDim2.new(0, 112, 0, 38)
InvisibleButton.Font = Enum.Font.PatrickHand
InvisibleButton.Text = "Invisible Me"
InvisibleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
InvisibleButton.TextSize = 30.000
InvisibleButton.TextWrapped = true

-- Fling Button
FlingButton.Name = "FlingButton"
FlingButton.Parent = ScrollingFrame
FlingButton.BackgroundColor3 = Color3.fromRGB(0, 0, 255)
FlingButton.BackgroundTransparency = 0.600
FlingButton.Position = UDim2.new(0, 0, 0, 100)
FlingButton.Size = UDim2.new(0, 112, 0, 38)
FlingButton.Font = Enum.Font.PatrickHand
FlingButton.Text = "Fling!"
FlingButton.TextColor3 = Color3.fromRGB(255, 255, 255)
FlingButton.TextSize = 30.000
FlingButton.TextWrapped = true

-- Fly Button
FlyButton.Name = "FlyButton"
FlyButton.Parent = ScrollingFrame
FlyButton.BackgroundColor3 = Color3.fromRGB(0, 255, 255)
FlyButton.BackgroundTransparency = 0.600
FlyButton.Position = UDim2.new(0, 0, 0, 150)
FlyButton.Size = UDim2.new(0, 112, 0, 38)
FlyButton.Font = Enum.Font.PatrickHand
FlyButton.Text = "Fly"
FlyButton.TextColor3 = Color3.fromRGB(255, 255, 255)
FlyButton.TextSize = 30.000
FlyButton.TextWrapped = true

-- Target Assist Button
TargetAssistButton.Name = "TargetAssistButton"
TargetAssistButton.Parent = ScrollingFrame
TargetAssistButton.BackgroundColor3 = Color3.fromRGB(255, 255, 0)
TargetAssistButton.BackgroundTransparency = 0.600
TargetAssistButton.Position = UDim2.new(0, 0, 0, 200)
TargetAssistButton.Size = UDim2.new(0, 112, 0, 38)
TargetAssistButton.Font = Enum.Font.PatrickHand
TargetAssistButton.Text = "Target Assist"
TargetAssistButton.TextColor3 = Color3.fromRGB(255, 255, 255)
TargetAssistButton.TextSize = 30.000
TargetAssistButton.TextWrapped = true

-- Hide GUI Button at top-right corner
HideButton.Name = "HideButton"
HideButton.Parent = Background
HideButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
HideButton.BackgroundTransparency = 0.600
HideButton.Position = UDim2.new(1, -40, 0, 10)
HideButton.Size = UDim2.new(0, 30, 0, 30)
HideButton.Font = Enum.Font.SourceSans
HideButton.Text = "X"
HideButton.TextColor3 = Color3.fromRGB(255, 255, 255)
HideButton.TextSize = 20.000
HideButton.TextWrapped = true

-- Open GUI Button
OpenButton.Name = "OpenButton"
OpenButton.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
OpenButton.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
OpenButton.BackgroundTransparency = 0.600
OpenButton.Position = UDim2.new(0.5, -50, 0.5, -25)
OpenButton.Size = UDim2.new(0, 100, 0, 50)
OpenButton.Font = Enum.Font.SourceSans
OpenButton.Text = "Open GUI"
OpenButton.TextColor3 = Color3.fromRGB(255, 255, 255)
OpenButton.TextSize = 30.000
OpenButton.TextWrapped = true

-- Initially, set OpenButton to be visible
OpenButton.Visible = true

-- Targeting Assist System
local Player = game.Players.LocalPlayer
local Mouse = Player:GetMouse()
local Target = nil
local MaxDistance = 500  -- Maximum targeting distance
local assistActive = false  -- Variable to track if assist is active

-- Function to find the nearest target
local function getNearestTarget()
    local nearestTarget = nil
    local shortestDistance = MaxDistance

    -- Loop through all players
    for _, otherPlayer in pairs(game.Players:GetPlayers()) do
        if otherPlayer ~= Player and otherPlayer.Character and otherPlayer.Character:FindFirstChild("HumanoidRootPart") then
            local character = otherPlayer.Character
            local distance = (character.HumanoidRootPart.Position - Mouse.Hit.p).magnitude
            
            -- Check if the player is within range
            if distance < shortestDistance then
                nearestTarget = character
                shortestDistance = distance
            end
        end
    end

    return nearestTarget
end

-- Function to assist in aiming (snap towards target)
local function aimAssist()
    local target = getNearestTarget()

    if target then
        -- Snap the camera towards the target's position
        local direction = (target.HumanoidRootPart.Position - Mouse.Hit.p).unit
        game.Workspace.CurrentCamera.CFrame = CFrame.lookAt(game.Workspace.CurrentCamera.CFrame.Position, target.HumanoidRootPart.Position)
    end
end

-- Toggle Target Assist
TargetAssistButton.MouseButton1Click:Connect(function()
    assistActive = not assistActive  -- Toggle the assist state

    if assistActive then
        -- Start assisting with aiming
        TargetAssistButton.Text = "Target Assist (ON)"  -- Update button text to show it's active
        game:GetService("RunService").RenderStepped:Connect(function()
            if assistActive then
                aimAssist()
            end
        end)
    else
        -- Stop assisting with aiming
        TargetAssistButton.Text = "Target Assist (OFF)"  -- Update button text to show it's inactive
    end
end)
