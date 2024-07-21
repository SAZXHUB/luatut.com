<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Roblox Lua Tutorial</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #23272a;
            color: white;
            padding: 10px 0;
            text-align: center;
        }
        nav {
            background-color: #2c2f33;
            padding: 10px;
            text-align: center;
        }
        nav a {
            color: white;
            text-decoration: none;
            margin: 0 10px;
        }
        .container {
            display: flex;
            flex-wrap: wrap;
        }
        .sidebar {
            width: 100%;
            max-width: 200px;
            background-color: #99aab5;
            padding: 10px;
        }
        .content {
            flex: 1;
            padding: 20px;
        }
        .section {
            background-color: white;
            padding: 20px;
            margin-bottom: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .section h2 {
            margin-top: 0;
        }
        .code {
            background-color: #e6e6e6;
            padding: 10px;
            border-radius: 5px;
            font-family: "Courier New", Courier, monospace;
            overflow-x: auto;
        }
        .code code {
            white-space: pre;
        }
        @media (min-width: 600px) {
            .sidebar {
                width: 20%;
            }
            .content {
                width: 80%;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>Roblox Lua Tutorial</h1>
    </header>
    <nav>
        <a href="#introduction">Introduction</a>
        <a href="#basics">Basics</a>
        <a href="#advanced">Advanced</a>
        <a href="#examples">Examples</a>
        <a href="#gui">GUI</a>
        <a href="#global">Using _G</a>
        <a href="#require">Using require</a>
    </nav>
    <div class="container">
        <aside class="sidebar">
            <h3>Contents</h3>
            <ul>
                <li><a href="#introduction">Introduction to Lua</a></li>
                <li><a href="#basics">Lua Basics</a></li>
                <li><a href="#advanced">Advanced Lua</a></li>
                <li><a href="#examples">Examples</a></li>
                <li><a href="#gui">GUI Tutorial</a></li>
                <li><a href="#global">Using _G</a></li>
                <li><a href="#require">Using require</a></li>
            </ul>
        </aside>
        <main class="content">
            <div id="introduction" class="section">
                <h2>Introduction to Lua</h2>
                <p>Lua is a lightweight, high-level, multi-paradigm programming language designed primarily for embedded systems and clients. It is used in Roblox to control the behavior of objects in games.</p>
            </div>
            <div id="basics" class="section">
                <h2>Lua Basics</h2>
                <p>Here are some basic concepts of Lua:</p>
                <h3>Variables</h3>
                <div class="code">
                    <code>
local x = 5
local y = "Hello"
                    </code>
                </div>
                <h3>Functions</h3>
                <div class="code">
                    <code>
function greet(name)
    print("Hello, " .. name)
end

greet("Player")
                    </code>
                </div>
                <h3>Local Functions</h3>
                <div class="code">
                    <code>
local function add(a, b)
    return a + b
end

print(add(5, 3))
                    </code>
                </div>
                <h3>While Loop</h3>
                <div class="code">
                    <code>
local count = 0
while count < 5 do
    print("Count is: " .. count)
    count = count + 1
end
                    </code>
                </div>
                <h3>Task Scheduling</h3>
                <div class="code">
                    <code>
task.wait(1)
print("This runs after 1 second")
                    </code>
                </div>
            </div>
            <div id="advanced" class="section">
                <h2>Advanced Lua</h2>
                <h3>Tables</h3>
                <p>Tables are the main data structuring mechanism in Lua.</p>
                <div class="code">
                    <code>
local player = {
    name = "Player1",
    score = 100
}

print(player.name)
                    </code>
                </div>
                <h3>Metatables</h3>
                <div class="code">
                    <code>
local mt = {
    __index = function(table, key)
        return "Key not found"
    end
}

local t = setmetatable({}, mt)
print(t.someKey)
                    </code>
                </div>
            </div>
            <div id="examples" class="section">
                <h2>Examples</h2>
                <h3>Creating a Part</h3>
                <div class="code">
                    <code>
local part = Instance.new("Part")
part.Position = Vector3.new(0, 10, 0)
part.Parent = game.Workspace
                    </code>
                </div>
                <h3>Connecting to an Event</h3>
                <div class="code">
                    <code>
game.Players.PlayerAdded:Connect(function(player)
    print(player.Name .. " has joined the game!")
end)
                    </code>
                </div>
            </div>
            <div id="gui" class="section">
                <h2>GUI Tutorial</h2>
                <h3>Creating a Simple GUI</h3>
                <div class="code">
                    <code>
local screenGui = Instance.new("ScreenGui")
local textLabel = Instance.new("TextLabel")

screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
textLabel.Parent = screenGui

textLabel.Size = UDim2.new(0, 200, 0, 50)
textLabel.Position = UDim2.new(0.5, -100, 0.5, -25)
textLabel.Text = "Hello, Roblox!"
                    </code>
                </div>
                <h3>Button with Function</h3>
                <div class="code">
                    <code>
local button = Instance.new("TextButton")

button.Size = UDim2.new(0, 200, 0, 50)
button.Position = UDim2.new(0.5, -100, 0.5, 50)
button.Text = "Click Me"
button.Parent = screenGui

button.MouseButton1Click:Connect(function()
    print("Button clicked!")
end)
                    </code>
                </div>
            </div>
            <div id="global" class="section">
                <h2>Using _G</h2>
                <p>The <code>_G</code> table in Lua is a special table that holds global variables. You can use <code>_G</code> to share variables and functions between different scripts.</p>
                <h3>Setting Global Variables</h3>
                <div class="code">
                    <code>
-- Setting a global variable
_G.globalVar = "Hello, World!"

-- Accessing the global variable in another script
print(_G.globalVar)
                    </code>
                </div>
                <h3>Using Global Functions</h3>
                <div class="code">
                    <code>
-- Defining a global function
_G.globalFunction = function()
    print("This is a global function!")
end

-- Calling the global function in another script
_G.globalFunction()
                    </code>
                </div>
                <h3>When to Use _G</h3>
                <p>Use <code>_G</code> when you need to share data or functions between scripts. However, use it sparingly to avoid unexpected behavior due to the global nature of the variables and functions.</p>
            </div>
            <div id="require" class="section">
                <h2>Using require</h2>
                <p>The <code>require</code> function in Lua is used to include and run code from another module. This is useful for organizing and reusing code across different parts of your project.</p>
                <h3>Loading a Module</h3>
                <div class="code">
                    <code>
-- Loading a module and storing it in a variable
local module = require(game.Players.LocalPlayer.Character:FindFirstChildOfClass("Name").Name)

module = type settings
</code>
</div>
<div id="require" class="section">
                <h2>what is require?</h2>
                <p>The <code>require</code> ,It can do many things such as changing values in modules or changing script commands And it is responsible for managing settings in the workspace..</p>
                </div>
                        </main>
    </div>
</body>
</html>
