-- Super Speed GUI by quanlaocai

-- Bảng tốc độ
local currentSpeed = 50

-- Tạo GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "SuperSpeedGUI"
ScreenGui.ResetOnSpawn = false
ScreenGui.Parent = game.CoreGui

local Frame = Instance.new("Frame")
Frame.Size = UDim2.new(0, 200, 0, 140)
Frame.Position = UDim2.new(0.05, 0, 0.05, 0)
Frame.BackgroundColor3 = Color3.fromRGB(255, 225, 0)
Frame.BorderSizePixel = 0
Frame.Active = true
Frame.Draggable = true
Frame.Parent = ScreenGui

local Title = Instance.new("TextLabel")
Title.Text = "🏃 Super Speed - by quanlaocai"
Title.Size = UDim2.new(1, 0, 0, 30)
Title.BackgroundTransparency = 1
Title.Font = Enum.Font.SourceSansBold
Title.TextSize = 16
Title.TextColor3 = Color3.fromRGB(0, 0, 0)
Title.Parent = Frame

local SpeedLabel = Instance.new("TextLabel")
SpeedLabel.Text = "Tốc độ: " .. currentSpeed
SpeedLabel.Position = UDim2.new(0, 0, 0, 30)
SpeedLabel.Size = UDim2.new(1, 0, 0, 30)
SpeedLabel.BackgroundTransparency = 1
SpeedLabel.Font = Enum.Font.SourceSans
SpeedLabel.TextSize = 16
SpeedLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
SpeedLabel.Parent = Frame

-- Nút tăng tốc
local IncreaseBtn = Instance.new("TextButton")
IncreaseBtn.Text = "🔼 Tăng"
IncreaseBtn.Position = UDim2.new(0.05, 0, 0, 65)
IncreaseBtn.Size = UDim2.new(0.4, 0, 0, 30)
IncreaseBtn.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
IncreaseBtn.Font = Enum.Font.SourceSans
IncreaseBtn.TextSize = 16
IncreaseBtn.TextColor3 = Color3.fromRGB(0, 0, 0)
IncreaseBtn.Parent = Frame

-- Nút giảm tốc
local DecreaseBtn = Instance.new("TextButton")
DecreaseBtn.Text = "🔽 Giảm"
DecreaseBtn.Position = UDim2.new(0.55, 0, 0, 65)
DecreaseBtn.Size = UDim2.new(0.4, 0, 0, 30)
DecreaseBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
DecreaseBtn.Font = Enum.Font.SourceSans
DecreaseBtn.TextSize = 16
DecreaseBtn.TextColor3 = Color3.fromRGB(0, 0, 0)
DecreaseBtn.Parent = Frame

-- Nút đóng/mở GUI
local ToggleBtn = Instance.new("TextButton")
ToggleBtn.Text = "👁 Ẩn/Hiện"
ToggleBtn.Position = UDim2.new(0.25, 0, 1, -30)
ToggleBtn.Size = UDim2.new(0.5, 0, 0, 25)
ToggleBtn.BackgroundColor3 = Color3.fromRGB(200, 200, 0)
ToggleBtn.Font = Enum.Font.SourceSans
ToggleBtn.TextSize = 16
ToggleBtn.TextColor3 = Color3.fromRGB(0, 0, 0)
ToggleBtn.Parent = Frame

-- Điều chỉnh tốc độ
local function updateSpeed()
    local char = game.Players.LocalPlayer.Character
    if char and char:FindFirstChild("Humanoid") then
        char.Humanoid.WalkSpeed = currentSpeed
        SpeedLabel.Text = "Tốc độ: " .. currentSpeed
    end
end

IncreaseBtn.MouseButton1Click:Connect(function()
    currentSpeed = currentSpeed + 10
    updateSpeed()
end)

DecreaseBtn.MouseButton1Click:Connect(function()
    currentSpeed = math.max(16, currentSpeed - 10)
    updateSpeed()
end)

ToggleBtn.MouseButton1Click:Connect(function()
    for _, obj in pairs(Frame:GetChildren()) do
        if obj ~= ToggleBtn and obj:IsA("GuiObject") then
            obj.Visible = not obj.Visible
        end
    end
end)

-- Khởi đầu
updateSpeed()
