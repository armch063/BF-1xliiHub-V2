
Old_World = false
New_World = false
Three_World = false

local placeId = game.PlaceId
if placeId == 2753915549 then
    Old_World = true
elseif placeId == 4442272183 then
    New_World = true
elseif placeId == 7449423635 then
	Three_World = true
end

local DINOHUB = Instance.new("ScreenGui")
local OPENCLOSE = Instance.new("TextButton")

DINOHUB.Name = "DINOHUB"
DINOHUB.Parent = game.CoreGui
DINOHUB.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

OPENCLOSE.Name = "OPENCLOSE"
OPENCLOSE.Parent = DINOHUB
OPENCLOSE.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
OPENCLOSE.BorderSizePixel = 0
OPENCLOSE.Position = UDim2.new(0.120833337, 0, 0.0952890813, 0)
OPENCLOSE.Size = UDim2.new(0.0447916649, 0, 0.0845824406, 0)
OPENCLOSE.Font = Enum.Font.DenkOne
OPENCLOSE.Text = "HappyHub"
OPENCLOSE.TextColor3 = Color3.fromRGB(96, 255, 16)
OPENCLOSE.TextScaled = true
OPENCLOSE.TextSize = 14.000
OPENCLOSE.TextWrapped = true
OPENCLOSE.MouseButton1Click:Connect(function()
    game.CoreGui:FindFirstChild("1xliiUI").Enabled = not game.CoreGui:FindFirstChild("1xliiUI").Enabled
end)
do
    if game:GetService("CoreGui"):FindFirstChild("1xliiUI") then
        game:GetService("CoreGui").DinoUI:Destroy()
    end
end

if game:GetService("CoreGui"):FindFirstChild("HappyUI") then
	game:GetService("CoreGui"):FindFirstChild("HappyUI"):Destroy()
end
do local GUI = game.CoreGui:FindFirstChild("HappyUI");if GUI then GUI:Destroy();end;if _G.Color == nil then
       _G.Color = Color3.fromRGB(255,255,255)
   end 
end

local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")

local function MakeDraggable(topbarobject, object)
	local Dragging = nil
	local DragInput = nil
	local DragStart = nil
	local StartPosition = nil

	local function Update(input)
		local Delta = input.Position - DragStart
		local pos = UDim2.new(StartPosition.X.Scale, StartPosition.X.Offset + Delta.X, StartPosition.Y.Scale, StartPosition.Y.Offset + Delta.Y)
		local Tween = TweenService:Create(object, TweenInfo.new(0.15), {Position = pos})
		Tween:Play()
	end

	topbarobject.InputBegan:Connect(
		function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				Dragging = true
				DragStart = input.Position
				StartPosition = object.Position

				input.Changed:Connect(
					function()
						if input.UserInputState == Enum.UserInputState.End then
							Dragging = false
						end
					end
				)
			end
		end
	)

	topbarobject.InputChanged:Connect(
		function(input)
			if
				input.UserInputType == Enum.UserInputType.MouseMovement or
				input.UserInputType == Enum.UserInputType.Touch
			then
				DragInput = input
			end
		end
	)

	UserInputService.InputChanged:Connect(
		function(input)
			if input == DragInput and Dragging then
				Update(input)
			end
		end
	)
end

local Update = {}

function Update:Window(text,logo,keybind)
	local uihide = false
	local abc = false
	local logo = logo or 0
	local currentpage = ""
	local keybind = keybind or Enum.KeyCode.RightControl
	local yoo = string.gsub(tostring(keybind),"Enum.KeyCode.","")
	
	local SOMEXHUB = Instance.new("ScreenGui")
	SOMEXHUB.Name = "SOMEXHUB"
	SOMEXHUB.Parent = game.CoreGui
	SOMEXHUB.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

	local Main = Instance.new("Frame")
	Main.Name = "Main"
	Main.Parent = SOMEXHUB
	Main.ClipsDescendants = true
	Main.AnchorPoint = Vector2.new(0.5,0.5)
	Main.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
	Main.Position = UDim2.new(0.5, 0, 0.5, 0)
	Main.Size = UDim2.new(0, 0, 0, 0)
	
	Main:TweenSize(UDim2.new(0, 656, 0, 400),"Out","Quad",0.4,true)

	local MCNR = Instance.new("UICorner")
	MCNR.Name = "MCNR"
	MCNR.Parent = Main

	local Top = Instance.new("Frame")
	Top.Name = "Top"
	Top.Parent = Main
	Top.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
	Top.Size = UDim2.new(0, 656, 0, 27)

	local TCNR = Instance.new("UICorner")
	TCNR.Name = "TCNR"
	TCNR.Parent = Top

	local Logo = Instance.new("ImageLabel")
	Logo.Name = "Logo"
	Logo.Parent = Top
	Logo.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Logo.BackgroundTransparency = 1.000
	Logo.Position = UDim2.new(0, 10, 0, 1)
	Logo.Size = UDim2.new(0, 25, 0, 25)
	Logo.Image = "rbxassetid://"..tostring(logo)

	local Name = Instance.new("TextLabel")
	Name.Name = "Name"
	Name.Parent = Top
	Name.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Name.BackgroundTransparency = 1.000
	Name.Position = UDim2.new(0.0609756112, 0, 0, 0)
	Name.Size = UDim2.new(0, 61, 0, 27)
	Name.Font = Enum.Font.GothamSemibold
	Name.Text = text
	Name.TextColor3 = Color3.fromRGB(225, 225, 225)
	Name.TextSize = 17.000

	local Hub = Instance.new("TextLabel")
	Hub.Name = "Hub"
	Hub.Parent = Top
	Hub.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Hub.BackgroundTransparency = 1.000
	Hub.Position = UDim2.new(0, 110, 0, 0)
	Hub.Size = UDim2.new(0, 81, 0, 27)
	Hub.Font = Enum.Font.GothamSemibold
	Hub.Text = "😡👽🔥"
	Hub.TextColor3 = _G.Color
	Hub.TextSize = 17.000
	Hub.TextXAlignment = Enum.TextXAlignment.Left

	local BindButton = Instance.new("TextButton")
	BindButton.Name = "BindButton"
	BindButton.Parent = Top
	BindButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	BindButton.BackgroundTransparency = 1.000
	BindButton.Position = UDim2.new(0.847561002, 0, 0, 0)
	BindButton.Size = UDim2.new(0, 100, 0, 27)
	BindButton.Font = Enum.Font.GothamSemibold
	BindButton.Text = "[ "..string.gsub(tostring(keybind),"Enum.KeyCode.","").." ]"
	BindButton.TextColor3 = Color3.fromRGB(100, 100, 100)
	BindButton.TextSize = 11.000
	
	BindButton.MouseButton1Click:Connect(function ()
		BindButton.Text = "[ ... ]"
		local inputwait = game:GetService("UserInputService").InputBegan:wait()
		local shiba = inputwait.KeyCode == Enum.KeyCode.Unknown and inputwait.UserInputType or inputwait.KeyCode

		if shiba.Name ~= "Focus" and shiba.Name ~= "MouseMovement" then
			BindButton.Text = "[ "..shiba.Name.." ]"
			yoo = shiba.Name
		end
	end)

	local Tab = Instance.new("Frame")
	Tab.Name = "Tab"
	Tab.Parent = Main
	Tab.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
	Tab.Position = UDim2.new(0, 5, 0, 30)
	Tab.Size = UDim2.new(0, 150, 0, 365)

	local TCNR = Instance.new("UICorner")
	TCNR.Name = "TCNR"
	TCNR.Parent = Tab

	local ScrollTab = Instance.new("ScrollingFrame")
	ScrollTab.Name = "ScrollTab"
	ScrollTab.Parent = Tab
	ScrollTab.Active = true
	ScrollTab.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	ScrollTab.BackgroundTransparency = 1.000
	ScrollTab.Size = UDim2.new(0, 150, 0, 365)
	ScrollTab.CanvasSize = UDim2.new(0, 0, 0, 0)
	ScrollTab.ScrollBarThickness = 0

	local PLL = Instance.new("UIListLayout")
	PLL.Name = "PLL"
	PLL.Parent = ScrollTab
	PLL.SortOrder = Enum.SortOrder.LayoutOrder
	PLL.Padding = UDim.new(0, 15)

	local PPD = Instance.new("UIPadding")
	PPD.Name = "PPD"
	PPD.Parent = ScrollTab
	PPD.PaddingLeft = UDim.new(0, 10)
	PPD.PaddingTop = UDim.new(0, 10)

	local Page = Instance.new("Frame")
	Page.Name = "Page"
	Page.Parent = Main
	Page.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
	Page.Position = UDim2.new(0.245426834, 0, 0.075000003, 0)
	Page.Size = UDim2.new(0, 490, 0, 365)

	local PCNR = Instance.new("UICorner")
	PCNR.Name = "PCNR"
	PCNR.Parent = Page

	local MainPage = Instance.new("Frame")
	MainPage.Name = "MainPage"
	MainPage.Parent = Page
	MainPage.ClipsDescendants = true
	MainPage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	MainPage.BackgroundTransparency = 1.000
	MainPage.Size = UDim2.new(0, 490, 0, 365)

	local PageList = Instance.new("Folder")
	PageList.Name = "PageList"
	PageList.Parent = MainPage

	local UIPageLayout = Instance.new("UIPageLayout")

	UIPageLayout.Parent = PageList
	UIPageLayout.SortOrder = Enum.SortOrder.LayoutOrder
	UIPageLayout.EasingDirection = Enum.EasingDirection.InOut
	UIPageLayout.EasingStyle = Enum.EasingStyle.Quad
	UIPageLayout.FillDirection = Enum.FillDirection.Vertical
	UIPageLayout.Padding = UDim.new(0, 15)
	UIPageLayout.TweenTime = 0.400
	UIPageLayout.GamepadInputEnabled = false
	UIPageLayout.ScrollWheelInputEnabled = false
	UIPageLayout.TouchInputEnabled = false
	
	MakeDraggable(Top,Main)

	UserInputService.InputBegan:Connect(function(input)
		if input.KeyCode == Enum.KeyCode[yoo] then
			if uihide == false then
				uihide = true
				Main:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0.4,true)
			else
				uihide = false
				Main:TweenSize(UDim2.new(0, 656, 0, 400),"Out","Quad",0.4,true)
			end
		end
	end)
	
	local uitab = {}
	
	function uitab:Tab(text)
		local TabButton = Instance.new("TextButton")
		TabButton.Parent = ScrollTab
		TabButton.Name = text.."Server"
		TabButton.Text = text
		TabButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		TabButton.BackgroundTransparency = 1.000
		TabButton.Size = UDim2.new(0, 130, 0, 23)
		TabButton.Font = Enum.Font.GothamSemibold
		TabButton.TextColor3 = Color3.fromRGB(225, 225, 225)
		TabButton.TextSize = 15.000
		TabButton.TextTransparency = 0.500

		local MainFramePage = Instance.new("ScrollingFrame")
		MainFramePage.Name = text.."_Page"
		MainFramePage.Parent = PageList
		MainFramePage.Active = true
		MainFramePage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		MainFramePage.BackgroundTransparency = 1.000
		MainFramePage.BorderSizePixel = 0
		MainFramePage.Size = UDim2.new(0, 490, 0, 365)
		MainFramePage.CanvasSize = UDim2.new(0, 0, 0, 0)
		MainFramePage.ScrollBarThickness = 0
		
		local UIPadding = Instance.new("UIPadding")
		local UIListLayout = Instance.new("UIListLayout")
		
		UIPadding.Parent = MainFramePage
		UIPadding.PaddingLeft = UDim.new(0, 10)
		UIPadding.PaddingTop = UDim.new(0, 10)

		UIListLayout.Padding = UDim.new(0,15)
		UIListLayout.Parent = MainFramePage
		UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
		
		TabButton.MouseButton1Click:Connect(function()
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0.5}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			for i,v in next, PageList:GetChildren() do
				currentpage = string.gsub(TabButton.Name,"Server","").."_Page"
				if v.Name == currentpage then
					UIPageLayout:JumpTo(v)
				end
			end
		end)

		if abc == false then
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0.5}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			UIPageLayout:JumpToIndex(1)
			abc = true
		end
		
		game:GetService("RunService").Stepped:Connect(function()
			pcall(function()
				MainFramePage.CanvasSize = UDim2.new(0,0,0,UIListLayout.AbsoluteContentSize.Y + 20)
				ScrollTab.CanvasSize = UDim2.new(0,0,0,PLL.AbsoluteContentSize.Y + 20)
			end)
		end)
		
		local main = {}
		function main:Button(text,callback)
			local Button = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
			local TextBtn = Instance.new("TextButton")
			local UICorner_2 = Instance.new("UICorner")
			local Black = Instance.new("Frame")
			local UICorner_3 = Instance.new("UICorner")
			
			Button.Name = "Button"
			Button.Parent = MainFramePage
			Button.BackgroundColor3 = _G.Color
			Button.Size = UDim2.new(0, 470, 0, 31)
			
			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = Button
			
			TextBtn.Name = "TextBtn"
			TextBtn.Parent = Button
			TextBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			TextBtn.Position = UDim2.new(0, 1, 0, 1)
			TextBtn.Size = UDim2.new(0, 468, 0, 29)
			TextBtn.AutoButtonColor = false
			TextBtn.Font = Enum.Font.GothamSemibold
			TextBtn.Text = text
			TextBtn.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextBtn.TextSize = 15.000
			
			UICorner_2.CornerRadius = UDim.new(0, 5)
			UICorner_2.Parent = TextBtn
			
			Black.Name = "Black"
			Black.Parent = Button
			Black.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
			Black.BackgroundTransparency = 1.000
			Black.BorderSizePixel = 0
			Black.Position = UDim2.new(0, 1, 0, 1)
			Black.Size = UDim2.new(0, 468, 0, 29)
			
			UICorner_3.CornerRadius = UDim.new(0, 5)
			UICorner_3.Parent = Black

			TextBtn.MouseEnter:Connect(function()
				TweenService:Create(
					Black,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundTransparency = 0.7}
				):Play()
			end)
			TextBtn.MouseLeave:Connect(function()
				TweenService:Create(
					Black,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundTransparency = 1}
				):Play()
			end)
			TextBtn.MouseButton1Click:Connect(function()
				TextBtn.TextSize = 0
				TweenService:Create(
					TextBtn,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextSize = 15}
				):Play()
				callback()
			end)
		end
		function main:Toggle(text,config,callback)
			config = config or false
			local toggled = config
			local Toggle = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
			local Button = Instance.new("TextButton")
			local UICorner_2 = Instance.new("UICorner")
			local Label = Instance.new("TextLabel")
			local ToggleImage = Instance.new("Frame")
			local UICorner_3 = Instance.new("UICorner")
			local Circle = Instance.new("Frame")
			local UICorner_4 = Instance.new("UICorner")

			Toggle.Name = "Toggle"
			Toggle.Parent = MainFramePage
			Toggle.BackgroundColor3 = _G.Color
			Toggle.Size = UDim2.new(0, 470, 0, 31)

			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = Toggle

			Button.Name = "Button"
			Button.Parent = Toggle
			Button.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			Button.Position = UDim2.new(0, 1, 0, 1)
			Button.Size = UDim2.new(0, 468, 0, 29)
			Button.AutoButtonColor = false
			Button.Font = Enum.Font.SourceSans
			Button.Text = ""
			Button.TextColor3 = Color3.fromRGB(0, 0, 0)
			Button.TextSize = 11.000

			UICorner_2.CornerRadius = UDim.new(0, 5)
			UICorner_2.Parent = Button

			Label.Name = "Label"
			Label.Parent = Toggle
			Label.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Label.BackgroundTransparency = 1.000
			Label.Position = UDim2.new(0, 1, 0, 1)
			Label.Size = UDim2.new(0, 468, 0, 29)
			Label.Font = Enum.Font.GothamSemibold
			Label.Text = text
			Label.TextColor3 = Color3.fromRGB(225, 225, 225)
			Label.TextSize = 15.000

			ToggleImage.Name = "ToggleImage"
			ToggleImage.Parent = Toggle
			ToggleImage.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
			ToggleImage.Position = UDim2.new(0, 415, 0, 5)
			ToggleImage.Size = UDim2.new(0, 45, 0, 20)

			UICorner_3.CornerRadius = UDim.new(0, 10)
			UICorner_3.Parent = ToggleImage

			Circle.Name = "Circle"
			Circle.Parent = ToggleImage
			Circle.BackgroundColor3 = Color3.fromRGB(227, 60, 60)
			Circle.Position = UDim2.new(0, 2, 0, 2)
			Circle.Size = UDim2.new(0, 16, 0, 16)

			UICorner_4.CornerRadius = UDim.new(0, 10)
			UICorner_4.Parent = Circle

			Button.MouseButton1Click:Connect(function()
				if toggled == false then
					toggled = true
					Circle:TweenPosition(UDim2.new(0,27,0,2),"Out","Sine",0.2,true)
					TweenService:Create(
						Circle,
						TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = _G.Color}
					):Play()
				else
					toggled = false
					Circle:TweenPosition(UDim2.new(0,2,0,2),"Out","Sine",0.2,true)
					TweenService:Create(
						Circle,
						TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(227, 60, 110)}
					):Play()
				end
				pcall(callback,toggled)
			end)

			if config == true then
				toggled = true
				Circle:TweenPosition(UDim2.new(0,27,0,2),"Out","Sine",0.4,true)
				TweenService:Create(
					Circle,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundColor3 = _G.Color}
				):Play()
				pcall(callback,toggled)
			end
		end
		function main:Dropdown(text,option,callback)
			local isdropping = false
			local Dropdown = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
			local DropTitle = Instance.new("TextLabel")
			local DropScroll = Instance.new("ScrollingFrame")
			local UIListLayout = Instance.new("UIListLayout")
			local UIPadding = Instance.new("UIPadding")
			local DropButton = Instance.new("TextButton")
			local DropImage = Instance.new("ImageLabel")
			
			Dropdown.Name = "Dropdown"
			Dropdown.Parent = MainFramePage
			Dropdown.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			Dropdown.ClipsDescendants = true
			Dropdown.Size = UDim2.new(0, 470, 0, 31)
			
			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = Dropdown
			
			DropTitle.Name = "DropTitle"
			DropTitle.Parent = Dropdown
			DropTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			DropTitle.BackgroundTransparency = 1.000
			DropTitle.Size = UDim2.new(0, 470, 0, 31)
			DropTitle.Font = Enum.Font.GothamSemibold
			DropTitle.Text = text.. " : "
			DropTitle.TextColor3 = Color3.fromRGB(225, 225, 225)
			DropTitle.TextSize = 15.000
			
			DropScroll.Name = "DropScroll"
			DropScroll.Parent = DropTitle
			DropScroll.Active = true
			DropScroll.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			DropScroll.BackgroundTransparency = 1.000
			DropScroll.BorderSizePixel = 0
			DropScroll.Position = UDim2.new(0, 0, 0, 31)
			DropScroll.Size = UDim2.new(0, 470, 0, 100)
			DropScroll.CanvasSize = UDim2.new(0, 0, 0, 0)
			DropScroll.ScrollBarThickness = 3
			
			UIListLayout.Parent = DropScroll
			UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
			UIListLayout.Padding = UDim.new(0, 5)
			
			UIPadding.Parent = DropScroll
			UIPadding.PaddingLeft = UDim.new(0, 5)
			UIPadding.PaddingTop = UDim.new(0, 5)
			
			DropImage.Name = "DropImage"
			DropImage.Parent = Dropdown
			DropImage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			DropImage.BackgroundTransparency = 1.000
			DropImage.Position = UDim2.new(0, 445, 0, 6)
			DropImage.Rotation = 180.000
			DropImage.Size = UDim2.new(0, 20, 0, 20)
			DropImage.Image = "rbxassetid://6031090990"
			
			DropButton.Name = "DropButton"
			DropButton.Parent = Dropdown
			DropButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			DropButton.BackgroundTransparency = 1.000
			DropButton.Size = UDim2.new(0, 470, 0, 31)
			DropButton.Font = Enum.Font.SourceSans
			DropButton.Text = ""
			DropButton.TextColor3 = Color3.fromRGB(0, 0, 0)
			DropButton.TextSize = 14.000

			for i,v in next,option do
				local Item = Instance.new("TextButton")

				Item.Name = "Item"
				Item.Parent = DropScroll
				Item.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Item.BackgroundTransparency = 1.000
				Item.Size = UDim2.new(0, 460, 0, 26)
				Item.Font = Enum.Font.GothamSemibold
				Item.Text = tostring(v)
				Item.TextColor3 = Color3.fromRGB(225, 225, 225)
				Item.TextSize = 13.000
				Item.TextTransparency = 0.500

				Item.MouseEnter:Connect(function()
					TweenService:Create(
						Item,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end)

				Item.MouseLeave:Connect(function()
					TweenService:Create(
						Item,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0.5}
					):Play()
				end)

				Item.MouseButton1Click:Connect(function()
					isdropping = false
					Dropdown:TweenSize(UDim2.new(0,470,0,31),"Out","Quad",0.3,true)
					TweenService:Create(
						DropImage,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{Rotation = 180}
					):Play()
					callback(Item.Text)
					DropTitle.Text = text.." : "..Item.Text
				end)
			end

			DropScroll.CanvasSize = UDim2.new(0,0,0,UIListLayout.AbsoluteContentSize.Y + 10)

			DropButton.MouseButton1Click:Connect(function()
				if isdropping == false then
					isdropping = true
					Dropdown:TweenSize(UDim2.new(0,470,0,131),"Out","Quad",0.3,true)
					TweenService:Create(
						DropImage,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{Rotation = 0}
					):Play()
				else
					isdropping = false
					Dropdown:TweenSize(UDim2.new(0,470,0,31),"Out","Quad",0.3,true)
					TweenService:Create(
						DropImage,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{Rotation = 180}
					):Play()
				end
			end)

			local dropfunc = {}
			function dropfunc:Add(t)
				local Item = Instance.new("TextButton")
				Item.Name = "Item"
				Item.Parent = DropScroll
				Item.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Item.BackgroundTransparency = 1.000
				Item.Size = UDim2.new(0, 470, 0, 26)
				Item.Font = Enum.Font.GothamSemibold
				Item.Text = tostring(t)
				Item.TextColor3 = Color3.fromRGB(225, 225, 225)
				Item.TextSize = 13.000
				Item.TextTransparency = 0.500

				Item.MouseEnter:Connect(function()
					TweenService:Create(
						Item,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end)

				Item.MouseLeave:Connect(function()
					TweenService:Create(
						Item,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0.5}
					):Play()
				end)

				Item.MouseButton1Click:Connect(function()
					isdropping = false
					Dropdown:TweenSize(UDim2.new(0,470,0,31),"Out","Quad",0.3,true)
					TweenService:Create(
						DropImage,
						TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{Rotation = 180}
					):Play()
					callback(Item.Text)
					DropTitle.Text = text.." : "..Item.Text
				end)
			end
			function dropfunc:Clear()
				DropTitle.Text = tostring(text).." : "
				isdropping = false
				Dropdown:TweenSize(UDim2.new(0,470,0,31),"Out","Quad",0.3,true)
				TweenService:Create(
					DropImage,
					TweenInfo.new(0.3,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{Rotation = 180}
				):Play()
				for i,v in next, DropScroll:GetChildren() do
					if v:IsA("TextButton") then
						v:Destroy()
					end
				end
			end
			return dropfunc
		end

		function main:Slider(text,min,max,set,callback)
			local Slider = Instance.new("Frame")
			local slidercorner = Instance.new("UICorner")
			local sliderr = Instance.new("Frame")
			local sliderrcorner = Instance.new("UICorner")
			local SliderLabel = Instance.new("TextLabel")
			local HAHA = Instance.new("Frame")
			local AHEHE = Instance.new("TextButton")
			local bar = Instance.new("Frame")
			local bar1 = Instance.new("Frame")
			local bar1corner = Instance.new("UICorner")
			local barcorner = Instance.new("UICorner")
			local circlebar = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
			local slidervalue = Instance.new("Frame")
			local valuecorner = Instance.new("UICorner")
			local TextBox = Instance.new("TextBox")
			local UICorner_2 = Instance.new("UICorner")

			Slider.Name = "Slider"
			Slider.Parent = MainFramePage
			Slider.BackgroundColor3 = _G.Color
			Slider.BackgroundTransparency = 0
			Slider.Size = UDim2.new(0, 470, 0, 51)

			slidercorner.CornerRadius = UDim.new(0, 5)
			slidercorner.Name = "slidercorner"
			slidercorner.Parent = Slider

			sliderr.Name = "sliderr"
			sliderr.Parent = Slider
			sliderr.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			sliderr.Position = UDim2.new(0, 1, 0, 1)
			sliderr.Size = UDim2.new(0, 468, 0, 49)

			sliderrcorner.CornerRadius = UDim.new(0, 5)
			sliderrcorner.Name = "sliderrcorner"
			sliderrcorner.Parent = sliderr

			SliderLabel.Name = "SliderLabel"
			SliderLabel.Parent = sliderr
			SliderLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			SliderLabel.BackgroundTransparency = 1.000
			SliderLabel.Position = UDim2.new(0, 15, 0, 0)
			SliderLabel.Size = UDim2.new(0, 180, 0, 26)
			SliderLabel.Font = Enum.Font.GothamSemibold
			SliderLabel.Text = text
			SliderLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
			SliderLabel.TextSize = 16.000
			SliderLabel.TextTransparency = 0
			SliderLabel.TextXAlignment = Enum.TextXAlignment.Left

			HAHA.Name = "HAHA"
			HAHA.Parent = sliderr
			HAHA.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			HAHA.BackgroundTransparency = 1.000
			HAHA.Size = UDim2.new(0, 468, 0, 29)

			AHEHE.Name = "AHEHE"
			AHEHE.Parent = sliderr
			AHEHE.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			AHEHE.BackgroundTransparency = 1.000
			AHEHE.Position = UDim2.new(0, 10, 0, 35)
			AHEHE.Size = UDim2.new(0, 448, 0, 5)
			AHEHE.Font = Enum.Font.SourceSans
			AHEHE.Text = ""
			AHEHE.TextColor3 = Color3.fromRGB(0, 0, 0)
			AHEHE.TextSize = 14.000

			bar.Name = "bar"
			bar.Parent = AHEHE
			bar.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
			bar.Size = UDim2.new(0, 448, 0, 5)

			bar1.Name = "bar1"
			bar1.Parent = bar
			bar1.BackgroundColor3 = _G.Color
			bar1.BackgroundTransparency = 0
			bar1.Size = UDim2.new(set/max, 0, 0, 5)

			bar1corner.CornerRadius = UDim.new(0, 5)
			bar1corner.Name = "bar1corner"
			bar1corner.Parent = bar1

			barcorner.CornerRadius = UDim.new(0, 5)
			barcorner.Name = "barcorner"
			barcorner.Parent = bar

			circlebar.Name = "circlebar"
			circlebar.Parent = bar1
			circlebar.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
			circlebar.Position = UDim2.new(1, -2, 0, -3)
			circlebar.Size = UDim2.new(0, 10, 0, 10)

			UICorner.CornerRadius = UDim.new(0, 100)
			UICorner.Parent = circlebar

			slidervalue.Name = "slidervalue"
			slidervalue.Parent = sliderr
			slidervalue.BackgroundColor3 = _G.Color
			slidervalue.BackgroundTransparency = 0
			slidervalue.Position = UDim2.new(0, 395, 0, 5)
			slidervalue.Size = UDim2.new(0, 65, 0, 18)

			valuecorner.CornerRadius = UDim.new(0, 5)
			valuecorner.Name = "valuecorner"
			valuecorner.Parent = slidervalue

			TextBox.Parent = slidervalue
			TextBox.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
			TextBox.Position = UDim2.new(0, 1, 0, 1)
			TextBox.Size = UDim2.new(0, 63, 0, 16)
			TextBox.Font = Enum.Font.GothamSemibold
			TextBox.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextBox.TextSize = 9.000
			TextBox.Text = set
			TextBox.TextTransparency = 0

			UICorner_2.CornerRadius = UDim.new(0, 5)
			UICorner_2.Parent = TextBox

			local mouse = game.Players.LocalPlayer:GetMouse()
			local uis = game:GetService("UserInputService")

			if Value == nil then
				Value = set
				pcall(function()
					callback(Value)
				end)
			end
			
			AHEHE.MouseButton1Down:Connect(function()
				Value = math.floor((((tonumber(max) - tonumber(min)) / 448) * bar1.AbsoluteSize.X) + tonumber(min)) or 0
				pcall(function()
					callback(Value)
				end)
				bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
				circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
				moveconnection = mouse.Move:Connect(function()
					TextBox.Text = Value
					Value = math.floor((((tonumber(max) - tonumber(min)) / 448) * bar1.AbsoluteSize.X) + tonumber(min))
					pcall(function()
						callback(Value)
					end)
					bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
					circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
				end)
				releaseconnection = uis.InputEnded:Connect(function(Mouse)
					if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
						Value = math.floor((((tonumber(max) - tonumber(min)) / 448) * bar1.AbsoluteSize.X) + tonumber(min))
						pcall(function()
							callback(Value)
						end)
						bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
						circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
						moveconnection:Disconnect()
						releaseconnection:Disconnect()
					end
				end)
			end)
			releaseconnection = uis.InputEnded:Connect(function(Mouse)
				if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
					Value = math.floor((((tonumber(max) - tonumber(min)) / 448) * bar1.AbsoluteSize.X) + tonumber(min))
					TextBox.Text = Value
				end
			end)

			TextBox.FocusLost:Connect(function()
				if tonumber(TextBox.Text) > max then
					TextBox.Text  = max
				end
				bar1.Size = UDim2.new((TextBox.Text or 0) / max, 0, 0, 5)
				circlebar.Position = UDim2.new(1, -2, 0, -3)
				TextBox.Text = tostring(TextBox.Text and math.floor( (TextBox.Text / max) * (max - min) + min) )
				pcall(callback, TextBox.Text)
			end)
		end

		function main:Textbox(text,disappear,callback)
			local Textbox = Instance.new("Frame")
			local TextboxCorner = Instance.new("UICorner")
			local Textboxx = Instance.new("Frame")
			local TextboxxCorner = Instance.new("UICorner")
			local TextboxLabel = Instance.new("TextLabel")
			local txtbtn = Instance.new("TextButton")
			local RealTextbox = Instance.new("TextBox")
			local UICorner = Instance.new("UICorner")

			Textbox.Name = "Textbox"
			Textbox.Parent = MainFramePage
			Textbox.BackgroundColor3 = _G.Color
			Textbox.BackgroundTransparency = 0
			Textbox.Size = UDim2.new(0, 470, 0, 31)

			TextboxCorner.CornerRadius = UDim.new(0, 5)
			TextboxCorner.Name = "TextboxCorner"
			TextboxCorner.Parent = Textbox

			Textboxx.Name = "Textboxx"
			Textboxx.Parent = Textbox
			Textboxx.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			Textboxx.Position = UDim2.new(0, 1, 0, 1)
			Textboxx.Size = UDim2.new(0, 468, 0, 29)

			TextboxxCorner.CornerRadius = UDim.new(0, 5)
			TextboxxCorner.Name = "TextboxxCorner"
			TextboxxCorner.Parent = Textboxx

			TextboxLabel.Name = "TextboxLabel"
			TextboxLabel.Parent = Textbox
			TextboxLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			TextboxLabel.BackgroundTransparency = 1.000
			TextboxLabel.Position = UDim2.new(0, 15, 0, 0)
			TextboxLabel.Text = text
			TextboxLabel.Size = UDim2.new(0, 145, 0, 31)
			TextboxLabel.Font = Enum.Font.GothamSemibold
			TextboxLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextboxLabel.TextSize = 16.000
			TextboxLabel.TextTransparency = 0
			TextboxLabel.TextXAlignment = Enum.TextXAlignment.Left

			txtbtn.Name = "txtbtn"
			txtbtn.Parent = Textbox
			txtbtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			txtbtn.BackgroundTransparency = 1.000
			txtbtn.Position = UDim2.new(0, 1, 0, 1)
			txtbtn.Size = UDim2.new(0, 468, 0, 29)
			txtbtn.Font = Enum.Font.SourceSans
			txtbtn.Text = ""
			txtbtn.TextColor3 = Color3.fromRGB(0, 0, 0)
			txtbtn.TextSize = 14.000

			RealTextbox.Name = "RealTextbox"
			RealTextbox.Parent = Textbox
			RealTextbox.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
			RealTextbox.BackgroundTransparency = 0
			RealTextbox.Position = UDim2.new(0, 360, 0, 4)
			RealTextbox.Size = UDim2.new(0, 100, 0, 24)
			RealTextbox.Font = Enum.Font.GothamSemibold
			RealTextbox.Text = ""
			RealTextbox.TextColor3 = Color3.fromRGB(225, 225, 225)
			RealTextbox.TextSize = 11.000
			RealTextbox.TextTransparency = 0

			RealTextbox.FocusLost:Connect(function()
				callback(RealTextbox.Text)
				if disappear then
					RealTextbox.Text = ""
				end
			end)

			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = RealTextbox
		end
		function main:Label(text)
			local Label = Instance.new("TextLabel")
			local PaddingLabel = Instance.new("UIPadding")
			local labelfunc = {}
	
			Label.Name = "Label"
			Label.Parent = MainFramePage
			Label.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Label.BackgroundTransparency = 1.000
			Label.Size = UDim2.new(0, 470, 0, 20)
			Label.Font = Enum.Font.GothamSemibold
			Label.TextColor3 = Color3.fromRGB(225, 225, 225)
			Label.TextSize = 16.000
			Label.Text = text
			Label.TextXAlignment = Enum.TextXAlignment.Left

			PaddingLabel.PaddingLeft = UDim.new(0,15)
			PaddingLabel.Parent = Label
			PaddingLabel.Name = "PaddingLabel"
	
			function labelfunc:Set(newtext)
				Label.Text = newtext
			end
			return labelfunc
		end

		function main:Seperator(text)
			local Seperator = Instance.new("Frame")
			local Sep1 = Instance.new("Frame")
			local Sep2 = Instance.new("TextLabel")
			local Sep3 = Instance.new("Frame")
			
			Seperator.Name = "Seperator"
			Seperator.Parent = MainFramePage
			Seperator.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Seperator.BackgroundTransparency = 1.000
			Seperator.Size = UDim2.new(0, 470, 0, 20)
			
			Sep1.Name = "Sep1"
			Sep1.Parent = Seperator
			Sep1.BackgroundColor3 = _G.Color
			Sep1.BorderSizePixel = 0
			Sep1.Position = UDim2.new(0, 0, 0, 10)
			Sep1.Size = UDim2.new(0, 80, 0, 1)
			
			Sep2.Name = "Sep2"
			Sep2.Parent = Seperator
			Sep2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Sep2.BackgroundTransparency = 1.000
			Sep2.Position = UDim2.new(0, 185, 0, 0)
			Sep2.Size = UDim2.new(0, 100, 0, 20)
			Sep2.Font = Enum.Font.GothamSemibold
			Sep2.Text = text
			Sep2.TextColor3 = Color3.fromRGB(255, 255, 255)
			Sep2.TextSize = 14.000
			
			Sep3.Name = "Sep3"
			Sep3.Parent = Seperator
			Sep3.BackgroundColor3 = _G.Color
			Sep3.BorderSizePixel = 0
			Sep3.Position = UDim2.new(0, 390, 0, 10)
			Sep3.Size = UDim2.new(0, 80, 0, 1)
		end

		function main:Line()
			local Linee = Instance.new("Frame")
			local Line = Instance.new("Frame")
			
			Linee.Name = "Linee"
			Linee.Parent = MainFramePage
			Linee.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Linee.BackgroundTransparency = 1.000
			Linee.Position = UDim2.new(0, 0, 0.119999997, 0)
			Linee.Size = UDim2.new(0, 470, 0, 20)
			
			Line.Name = "Line"
			Line.Parent = Linee
			Line.BackgroundColor3 = _G.Color
			Line.BorderSizePixel = 0
			Line.Position = UDim2.new(0, 0, 0, 10)
			Line.Size = UDim2.new(0, 470, 0, 1)
		end
		return main
	end
	return uitab
end

local Library = Update:Window("Happy HUB","",Enum.KeyCode.RightControl);
local AutoFarm = serv:Channel("AutoFarm","")
local Stats = serv:Channel("Stats","")
local Auto = serv:Channel("Auto","")
local tp = serv:Channel("Teleport","")
local Raid = serv:Channel("Raid","")
local Shop = serv:Channel("Shop","")
local Misc = serv:Channel("Misc","")
local Setting = serv:Channel("Setting","")
AutoFarm = Library:Tab("Main")

AutoFarm:Line()
AutoFarm:Label("Welcome xNero Community")
Wapon = {}
Wapon = {}
for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
    if v:IsA("Tool") then
       table.insert(Wapon ,v.Name)
    end
end
for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do  
    if v:IsA("Tool") then
       table.insert(Wapon, v.Name)
    end
end

local SelectWeapon = AutoFarm:Dropdown("Select Weapon",Wapon,function(Value)
    SelectToolWeapon = Value
    SelectToolWeaponOld = Value
end)

AutoFarm:Button("Refresh Weapon",function()
	SelectWeapon:Clear()
	for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
		if v:IsA("Tool") then
			SelectWeapon:Add(v.Name)
		end
	end
	for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do  
		if v:IsA("Tool") then
			SelectWeapon:Add(v.Name)
		end
	end
end)

AutoFarm:Line()

AutoFarm:Toggle("AutoFarm Level",false,function(vu)
    _G.AutoFarm = vu
	if _G.AutoFarm and SelectToolWeapon == "" then
        ui:Notification("AutoFarm","SelectWeapon First ",2)
	else
		Auto_Farm = vu
                Magnet = vu
		SelectMonster = ""
		if vu == false then
			wait(1)
			totarget(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)
		end
	end
end)

AutoFarm:Line()

-- Stats 

Stats:Toggle("Melee",false,function(Value)
melee = Value    
end)
Stats:Toggle("Defense",false,function(value)
defense = value
end)
Stats:Toggle("Sword",false,function(value)
sword = value
end)
Stats:Toggle("Gun",false,function(value)
gun = value
end)
Stats:Toggle("Devil Fruit",false,function(value)
demonfruit = value
end)

Stats:Line()

PointStats = 1
Stats:Slider("Point",1,100,PointStats,nil,function(value)
PointStats = value
end)

spawn(function()
		while wait() do
			if game.Players.localPlayer.Data.Points.Value >= PointStats then
				if melee then
					local args = {
						[1] = "AddPoint",
						[2] = "Melee",
						[3] = PointStats
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end 
				if defense then
					local args = {
						[1] = "AddPoint",
						[2] = "Defense",
						[3] = PointStats
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end 
				if sword then
					local args = {
						[1] = "AddPoint",
						[2] = "Sword",
						[3] = PointStats
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end 
				if gun then
					local args = {
						[1] = "AddPoint",
						[2] = "Gun",
						[3] = PointStats
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end 
				if demonfruit then
					local args = {
						[1] = "AddPoint",
						[2] = "Demon Fruit",
						[3] = PointStats
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
			end
		end
	end)

-- Auto

Auto:Toggle("Auto Superhuman",nil,function(vu)
		Superhuman = vu
		if vu then
			local args = {
				[1] = "BuyElectro"
			}
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end)
Auto:Toggle("Auto Death Step",nil,function(vu)
		DeathStep = vu
		if vu then
			local args = {
				[1] = "BuyBlackLeg"
			}
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end)
Auto:Toggle("Auto Dragon Talon",nil,function(vu)
		DargonTalon = vu
		if vu then
			local args = {
				[1] = "BlackbeardReward",
				[2] = "DragonClaw",
				[3] = "2"
			}
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end)
Auto:Toggle("Auto Electric Clow",nil,function(vu)
		Electricclow = vu
		if vu then
			local args = {
				[1] = "BuyElectro"
			}
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		end
	end)
	spawn(function()
		while wait(.25) do
			if Superhuman and game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then 
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Combat") or game.Players.LocalPlayer.Character:FindFirstChild("Combat") then
					local args = {
						[1] = "BuyElectro"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end   
				if game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") then
					SelectToolWeapon = "Superhuman"
				end  
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value <= 299  then
					SelectToolWeapon = "Black Leg"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value <= 299  then
					SelectToolWeapon = "Electro"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value <= 299  then
					SelectToolWeapon = "Fishman Karate"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value <= 299  then
					SelectToolWeapon = "Dragon Claw"
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 300  then
					local args = {
						[1] = "BuyFishmanKarate"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 300  then
					local args = {
						[1] = "BuyFishmanKarate"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 100  then
					local args = {
						[1] = "BuyBlackLeg"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 300  then
					local args = {
						[1] = "BuyBlackLeg"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 300  then
					if SuperhumanFull and game.Players.LocalPlayer.Data.Fragments.Value < 1500 then
						if game.Players.LocalPlayer.Data.Level.Value > 1100 then
							RaidsSelected = "Flame"
							AutoRaids = true
							RaidsArua = true
						end
					else
						AutoRaids = false
						RaidsArua = false
						local args = {
							[1] = "BlackbeardReward",
							[2] = "DragonClaw",
							[3] = "2"
						}
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					end
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate").Level.Value >= 300  then
					if SuperhumanFull and game.Players.LocalPlayer.Data.Fragments.Value < 1500 then
						if game.Players.LocalPlayer.Data.Level.Value > 1100 then
							RaidsSelected = "Flame"
							AutoRaids = true
							RaidsArua = true
						end
					else
						AutoRaids = false
						RaidsArua = false
						local args = {
							[1] = "BlackbeardReward",
							[2] = "DragonClaw",
							[3] = "2"
						}
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					end
				end
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value >= 300  then
					local args = {
						[1] = "BuySuperhuman"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 300  then
					local args = {
						[1] = "BuySuperhuman"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end 
			end
			if DeathStep and game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 400 then
					local args = {
						[1] = "BuyDeathStep"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					SelectToolWeapon = "Death Step"
				end  
				if game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 400 then
					local args = {
						[1] = "BuyDeathStep"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					
					SelectToolWeapon = "Death Step"
				end  
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value < 400 then
					SelectToolWeapon = "Black Leg"
				end 
			end
			if DargonTalon and game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value <= 399 and game.Players.LocalPlayer.Character.Humanoid.Health > 0 then
					SelectToolWeapon = "Dragon Claw"
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value <= 399 and game.Players.LocalPlayer.Character.Humanoid.Health > 0 then
					SelectToolWeapon = "Dragon Claw"
				end
	
				if game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 400 and game.Players.LocalPlayer.Character.Humanoid.Health > 0 then
					SelectToolWeapon = "Dragon Claw"
					if game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyDragonTalon", true) == 3 then
						local string_1 = "Bones";
						local string_2 = "Buy";
						local number_1 = 1;
						local number_2 = 1;
						local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
						Target:InvokeServer(string_1, string_2, number_1, number_2);
	
						local string_1 = "BuyDragonTalon";
						local bool_1 = true;
						local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
						Target:InvokeServer(string_1, bool_1);
					elseif game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyDragonTalon", true) == 1 then
						game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyDragonTalon")
					else
						local string_1 = "BuyDragonTalon";
						local bool_1 = true;
						local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
						Target:InvokeServer(string_1, bool_1);
						local string_1 = "BuyDragonTalon";
						local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
						Target:InvokeServer(string_1);
					end 
				end
			end
			if Electricclow and game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value < 400 then
					SelectToolWeapon = "Electro"
				end  
				if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value < 400 then
					SelectToolWeapon = "Electro"
				end  
				if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 400 then
					local v175 = game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyElectricClaw", true);
					if v175 == 4 then
						local v176 = game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyElectricClaw", "Start");
						if v176 == nil then
							game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-12548, 337, -7481)
						end
					else
						local string_1 = "BuyElectricClaw";
						local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
						Target:InvokeServer(string_1);
					end
				end
				if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 400 then
					local v175 = game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyElectricClaw", true);
					if v175 == 4 then
						local v176 = game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyElectricClaw", "Start");
						if v176 == nil then
							game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-12548, 337, -7481)
						end
					else
						local string_1 = "BuyElectricClaw";
						local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
						Target:InvokeServer(string_1);
					end
				end
			end
		end
	end)

-- tp

tp:Button("Teleport To Sea 1",function()
game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelMain")
end)
tp:Button("Teleport To Sea 2",function()
game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
end)
tp:Button("Teleport To Sea 3",function()
game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
end)

tp:Line()

tp:Button("Stop Tween",function()
Clip = false
totarget(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)
end)

tp:Line()

if Old_World then
tp:Button("Start Island",function()
    totarget(CFrame.new(1071.2832, 16.3085976, 1426.86792))
end)
tp:Button("Marine Start",function()
    totarget(CFrame.new(-2573.3374, 6.88881969, 2046.99817))
end)
tp:Button("Middle Town",function()
    totarget(CFrame.new(-655.824158, 7.88708115, 1436.67908))
end)
tp:Button("Jungle",function()
    totarget(CFrame.new(-1249.77222, 11.8870859, 341.356476))
end)
tp:Button("Pirate Village",function()
    totarget(CFrame.new(-1122.34998, 4.78708982, 3855.91992))
end)
tp:Button("Desert",function()
    totarget(CFrame.new(1094.14587, 6.47350502, 4192.88721))
end)
tp:Button("Frozen Village",function()
    totarget(CFrame.new(1198.00928, 27.0074959, -1211.73376))
end)
tp:Button("MarineFord",function()
    totarget(CFrame.new(-4505.375, 20.687294, 4260.55908))
end)
tp:Button("Colosseum",function()
    totarget(CFrame.new(-1428.35474, 7.38933945, -3014.37305))
end)
tp:Button("Sky island 1 ",function()
    totarget(CFrame.new(-4970.21875, 717.707275, -2622.35449))
end)
tp:Button("Sky island 2 ",function()
    totarget(CFrame.new(-4813.0249, 903.708557, -1912.69055))
end)
tp:Button("Sky island 3 ",function()
    totarget(CFrame.new(-7952.31006, 5545.52832, -320.704956))
end)
tp:Button("Sky island 4 ",function()
    totarget(CFrame.new(-7793.43896, 5607.22168, -2016.58362))
end)
tp:Button("Prison",function()
    totarget(CFrame.new(4854.16455, 5.68742752, 740.194641))
end)
tp:Button("Magma Village",function()
    totarget(CFrame.new(-5231.75879, 8.61593437, 8467.87695))
end)
tp:Button("UndeyWater City",function()
    totarget(CFrame.new(61163.8516, 11.7796879, 1819.78418))
end)
tp:Button("Fountain City",function()
    totarget(CFrame.new(5132.7124, 4.53632832, 4037.8562))
end)
tp:Button("House Cyborg's",function()
    totarget(CFrame.new(6262.72559, 71.3003616, 3998.23047))
end)
tp:Button("Shank's Room",function()
    totarget(CFrame.new(-1442.16553, 29.8788261, -28.3547478))
end)
tp:Button("Mob Island",function()
    totarget(CFrame.new(-2850.20068, 7.39224768, 5354.99268))
end)
elseif New_World then
tp:Button("Dock",function()
    totarget(CFrame.new(82.9490662, 18.0710983, 2834.98779))
end)
tp:Button("Kingdom of Rose",function()
    totarget(CFrame.new(-394.983521, 118.503128, 1245.8446))
end)
tp:Button("Mansion",function()
    totarget(CFrame.new(-390.096313, 331.886475, 673.464966))
end)
tp:Button("Flamingo Room",function()
    totarget(CFrame.new(2302.19019, 15.1778421, 663.811035))
end)
tp:Button("Green Zone",function()
    totarget(CFrame.new(-2372.14697, 72.9919434, -3166.51416))
end)
tp:Button("Cafe",function()
    totarget(CFrame.new(-385.250916, 73.0458984, 297.388397))
end)
tp:Button("Factroy",function()
    totarget(CFrame.new(430.42569, 210.019623, -432.504791))
end)
tp:Button("Colosseum",function()
    totarget(CFrame.new(-1836.58191, 44.5890656, 1360.30652))
end)
tp:Button("Grave Island",function()
    totarget(CFrame.new(-5411.47607, 48.8234024, -721.272522))
end)
tp:Button("Snow Mountain",function()
    totarget(CFrame.new(511.825226, 401.765198, -5380.396))
end)
tp:Button("Cold Island",function()
    totarget(CFrame.new(-6026.96484, 14.7461271, -5071.96338))
end)
tp:Button("Hot Island",function()
    totarget(CFrame.new(-5478.39209, 15.9775667, -5246.9126))
end)
tp:Button("Cursed Ship",function()
    totarget(CFrame.new(902.059143, 124.752518, 33071.8125))
end)
tp:Button("Ice Castle",function()
    totarget(CFrame.new(5400.40381, 28.21698, -6236.99219))
end)
tp:Button("Forgotten Island",function()
    totarget(CFrame.new(-3043.31543, 238.881271, -10191.5791))
end)
tp:Button("Usoapp Island",function()
    totarget(CFrame.new(4748.78857, 8.35370827, 2849.57959))
end)
tp:Button("Minisky Island",function()
    totarget(CFrame.new(-260.358917, 49325.7031, -35259.3008))
end)
elseif Three_World then
tp:Button("Port Towen",function()
    totarget(CFrame.new(-610.309692, 57.8323097, 6436.33594))
end)
tp:Button("Hydra Island",function()
    totarget(CFrame.new(5229.99561, 603.916565, 345.154022))
end)
tp:Button("Great Tree",function()
    totarget(CFrame.new(2174.94873, 28.7312393, -6728.83154))
end)
tp:Button("Castle on the Sea",function()
    totarget(CFrame.new(-5477.62842, 313.794739, -2808.4585))
end)
tp:Button("Floating Turtle",function()
    totarget(CFrame.new(-10919.2998, 331.788452, -8637.57227))
end)
tp:Button("Mansion",function()
    totarget(CFrame.new(-12553.8125, 332.403961, -7621.91748))
end)
tp:Button("Secret Temple",function()
    totarget(CFrame.new(5217.35693, 6.56511116, 1100.88159))
end)
tp:Button("Friendly Arena",function()
    totarget(CFrame.new(5220.28955, 72.8193436, -1450.86304))
end)
tp:Button("Beautiful Pirate Domain",function()
    totarget(CFrame.new(5310.8095703125, 21.594484329224, 129.39053344727))
end)
tp:Button("Teler Park",function()
    totarget(CFrame.new(-9512.3623046875, 142.13258361816, 5548.845703125))
end)
tp:Button("Peanut Island",function()
    totarget(CFrame.new(-2142, 48, -10031))
end)
tp:Button("Ice Cream Island",function()
    totarget(CFrame.new(-949, 59, -10907))
end)
end

-- Raid

Raid:Toggle("Kill Aura", false, function(vu)
    Killaura = vu
end)

Raid:Toggle("Auto Awakenr", false, function(vu)
    AutoAwakener = vu
end)

Raid:Toggle("Auto Next Island", false, function(vu)
    NextIsland = vu
end)

spawn(function()
	pcall(function()
		while wait(.1) do
			if AutoAwakener then
				local args = {
					[1] = "Awakener",
					[2] = "Check"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				local args = {
					[1] = "Awakener",
					[2] = "Awaken"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end
		end
	end)
end)

spawn(function()
    while wait() do
        if Killaura or _G.AutoRaid or RaidSuperhuman then
            for i,v in pairs(game.Workspace.Enemies:GetDescendants()) do
                if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                    pcall(function()
                        repeat wait(.1)
                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                            v.Humanoid.Health = 0
                            v.HumanoidRootPart.CanCollide = false
                            v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                            v.HumanoidRootPart.Transparency = 0.8
                        until not Killaura or not _G.AutoRaid or not RaidSuperhuman or not v.Parent or v.Humanoid.Health <= 0
                    end)
                end
            end
        end
    end
end)

spawn(function()
	pcall(function()
		while game:GetService("RunService").Heartbeat:wait() do
			if NextIsland or RaidSuperhuman or _G.AutoRaid then
				if game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Timer.Visible == true and game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
					if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") then
						totarget(game:GetService("Workspace")["_WorldOrigin"].Locations["Island 5"].CFrame*CFrame.new(0,80,0))
					elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") then
						totarget(game:GetService("Workspace")["_WorldOrigin"].Locations["Island 4"].CFrame*CFrame.new(0,80,0))
					elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") then
						totarget(game:GetService("Workspace")["_WorldOrigin"].Locations["Island 3"].CFrame*CFrame.new(0,80,0))
					elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") then
						totarget(game:GetService("Workspace")["_WorldOrigin"].Locations["Island 2"].CFrame*CFrame.new(0,80,0))
					elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
						totarget(game:GetService("Workspace")["_WorldOrigin"].Locations["Island 1"].CFrame*CFrame.new(0,80,0))
					end
				elseif New_World then
					totarget(CFrame.new(-6438.73535, 250.645355, -4501.50684))
				elseif Three_World then
					totarget(CFrame.new(-5057.146484375, 314.54132080078, -2934.7995605469))
				end
			end
		end
	end)
end)

-- Shop

Shop:Button("Random Race (3000 Fragments)",function()
		local args = {
			[1] = "BlackbeardReward",
			[2] = "Reroll",
			[3] = "2"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Reset Stats (2500 Fragments)",function()
		local args = {
			[1] = "BlackbeardReward",
			[2] = "Refund",
			[3] = "2"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end) 
Shop:Line()
   Shop:Button("Black Leg",function()
		local args = {
			[1] = "BuyBlackLeg"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Electro",function()
		local args = {
			[1] = "BuyElectro"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Fishman Karate",function()
		local args = {
			[1] = "BuyFishmanKarate"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Dragon Claw",function()
		local args = {
			[1] = "BlackbeardReward",
			[2] = "DragonClaw",
			[3] = "2"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Superhuman",function()
		local args = {
			[1] = "BuySuperhuman"
		}
		
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Death Step",function()
		local args = {
			[1] = "BuyDeathStep"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Sharkman Karate",function()
		local args = {
			[1] = "BuySharkmanKarate",
			[2] = true
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		local args = {
			[1] = "BuySharkmanKarate"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Electric Claw",function()
		local string_1 = "BuyElectricClaw";
		local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
		Target:InvokeServer(string_1);
	end)
	Shop:Button("Dragon Talon",function()
		local string_1 = "BuyDragonTalon";
		local bool_1 = true;
		local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
		Target:InvokeServer(string_1, bool_1);
		local string_1 = "BuyDragonTalon";
		local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
		Target:InvokeServer(string_1);
	end)
Shop:Line()
    Shop:Button("Katana [ $1,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Katana"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Cutlass [ $1,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Cutlass"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)  
	Shop:Button("Dual Katana [ $12,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Dual Katana"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Iron Mace [ $25,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Iron Mace"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Triple Katana [ $60,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Triple Katana"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Pipe [ $100,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Pipe"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Soul Cane [ $750,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Soul Cane"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Dual-Headed Blade [ $400,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Dual-Headed Blade"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Bisento [ $1,200,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Bisento"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Pole v.2 [ 5,000 Fragments )",function()
		game.ReplicatedStorage.Remotes.CommF_:InvokeServer("ThunderGodTalk")
	end)
Shop:Line()
    Shop:Button("Slingshot [ $5,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Slingshot"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Musket [ $8,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Musket"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Flintlock [ $10,500 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Flintlock"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Refined Slingshot [ $30,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Refined Slingshot"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Refined Flintlock [ $65,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Refined Flintlock"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Kabucha [ 1,500 Fragments)",function()
		game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BlackbeardReward", "Slingshot", "2")
	end)
Shop:Line()
	Shop:Button("Black Cape [ $50,000 Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Black Cape"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Swordsman Hat [ 150k Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Swordsman Hat"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Tomoe Ring [ $500k Beli ]",function()
		local args = {
			[1] = "BuyItem",
			[2] = "Tomoe Ring"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
Shop:Line()
    Shop:Button("Race Ghoul",function()
		local args = {
			[1] = "Ectoplasm",
			[2] = "BuyCheck",
			[3] = 4
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		local args = {
			[1] = "Ectoplasm",
			[2] = "Change",
			[3] = 4
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Shop:Button("Race Cyborg",function()
		local args = {
			[1] = "CyborgTrainer",
			[2] = "Buy"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)

-- Misc

Misc:Toggle("ESP Player",espplyer,function(a)
		ESPPlayer = a
		UpdatePlayerChams()
	end)
Misc:Toggle("ESP Chest",espchest,function(a)
		ChestESP = a
		UpdateChestChams() 
	end)
Misc:Toggle("ESP Devil Fruit",espdevilfruit,function(a)
		DevilFruitESP = a
		UpdateDevilChams() 
	end)
Misc:Toggle("ESP Flower",espflower,function(a)
		FlowerESP = a
		UpdateFlowerChams() 
	end)
    spawn(function()
		while wait() do
			if FlowerESP then
				UpdateFlowerChams() 
			end
			if DevilFruitESP then
				UpdateDevilChams() 
			end
			if ChestESP then
				UpdateChestChams() 
			end
			if ESPPlayer then
				UpdatePlayerChams()
			end
		end
	end)
	function isnil(thing)
		return (thing == nil)
	end
	local function round(n)
		return math.floor(tonumber(n) + 0.5)
	end
	Number = math.random(1, 1000000)
	function UpdatePlayerChams()
		for i,v in pairs(game:GetService'Players':GetChildren()) do
			pcall(function()
				if not isnil(v.Character) then
					if ESPPlayer then
						if not isnil(v.Character.Head) and not v.Character.Head:FindFirstChild('NameEsp'..Number) then
							local bill = Instance.new('BillboardGui',v.Character.Head)
							bill.Name = 'NameEsp'..Number
							bill.ExtentsOffset = Vector3.new(0, 1, 0)
							bill.Size = UDim2.new(1,200,1,30)
							bill.Adornee = v.Character.Head
							bill.AlwaysOnTop = true
							local name = Instance.new('TextLabel',bill)
							name.Font = "GothamBold"
							name.FontSize = "Size14"
							name.TextWrapped = true
							name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M')
							name.Size = UDim2.new(1,0,1,0)
							name.TextYAlignment = 'Top'
							name.BackgroundTransparency = 1
							name.TextStrokeTransparency = 0.5
							if v.Team == game.Players.LocalPlayer.Team then
								name.TextColor3 = Color3.new(0,255,0)
							else
								name.TextColor3 = Color3.new(255,0,0)
							end
						else
							v.Character.Head['NameEsp'..Number].TextLabel.Text = (v.Name ..' | '.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M\nHealth : ' .. round(v.Character.Humanoid.Health*100/v.Character.Humanoid.MaxHealth) .. '%')
						end
					else
						if v.Character.Head:FindFirstChild('NameEsp'..Number) then
							v.Character.Head:FindFirstChild('NameEsp'..Number):Destroy()
						end
					end
				end
			end)
		end
	end
	function UpdateChestChams() 
		for i,v in pairs(game.Workspace:GetChildren()) do
			pcall(function()
				if string.find(v.Name,"Chest") then
					if ChestESP then
						if string.find(v.Name,"Chest") then
							if not v:FindFirstChild('NameEsp'..Number) then
								local bill = Instance.new('BillboardGui',v)
								bill.Name = 'NameEsp'..Number
								bill.ExtentsOffset = Vector3.new(0, 1, 0)
								bill.Size = UDim2.new(1,200,1,30)
								bill.Adornee = v
								bill.AlwaysOnTop = true
								local name = Instance.new('TextLabel',bill)
								name.Font = "GothamBold"
								name.FontSize = "Size14"
								name.TextWrapped = true
								name.Size = UDim2.new(1,0,1,0)
								name.TextYAlignment = 'Top'
								name.BackgroundTransparency = 1
								name.TextStrokeTransparency = 0.5
								if v.Name == "Chest1" then
									name.TextColor3 = Color3.fromRGB(109, 109, 109)
									name.Text = ("Chest 1" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
								end
								if v.Name == "Chest2" then
									name.TextColor3 = Color3.fromRGB(173, 158, 21)
									name.Text = ("Chest 2" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
								end
								if v.Name == "Chest3" then
									name.TextColor3 = Color3.fromRGB(85, 255, 255)
									name.Text = ("Chest 3" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
								end
							else
								v['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
							end
						end
					else
						if v:FindFirstChild('NameEsp'..Number) then
							v:FindFirstChild('NameEsp'..Number):Destroy()
						end
					end
				end
			end)
		end
	end
	function UpdateDevilChams() 
		for i,v in pairs(game.Workspace:GetChildren()) do
			pcall(function()
				if DevilFruitESP then
					if string.find(v.Name, "Fruit") then   
						if not v.Handle:FindFirstChild('NameEsp'..Number) then
							local bill = Instance.new('BillboardGui',v.Handle)
							bill.Name = 'NameEsp'..Number
							bill.ExtentsOffset = Vector3.new(0, 1, 0)
							bill.Size = UDim2.new(1,200,1,30)
							bill.Adornee = v.Handle
							bill.AlwaysOnTop = true
							local name = Instance.new('TextLabel',bill)
							name.Font = "GothamBold"
							name.FontSize = "Size14"
							name.TextWrapped = true
							name.Size = UDim2.new(1,0,1,0)
							name.TextYAlignment = 'Top'
							name.BackgroundTransparency = 1
							name.TextStrokeTransparency = 0.5
							name.TextColor3 = Color3.fromRGB(255, 0, 0)
							name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
						else
							v.Handle['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Handle.Position).Magnitude/3) ..' M')
						end
					end
				else
					if v.Handle:FindFirstChild('NameEsp'..Number) then
						v.Handle:FindFirstChild('NameEsp'..Number):Destroy()
					end
				end
			end)
		end
	end
	function UpdateFlowerChams() 
		for i,v in pairs(game.Workspace:GetChildren()) do
			pcall(function()
				if v.Name == "Flower2" or v.Name == "Flower1" then
					if FlowerESP then 
						if not v:FindFirstChild('NameEsp'..Number) then
							local bill = Instance.new('BillboardGui',v)
							bill.Name = 'NameEsp'..Number
							bill.ExtentsOffset = Vector3.new(0, 1, 0)
							bill.Size = UDim2.new(1,200,1,30)
							bill.Adornee = v
							bill.AlwaysOnTop = true
							local name = Instance.new('TextLabel',bill)
							name.Font = "GothamBold"
							name.FontSize = "Size14"
							name.TextWrapped = true
							name.Size = UDim2.new(1,0,1,0)
							name.TextYAlignment = 'Top'
							name.BackgroundTransparency = 1
							name.TextStrokeTransparency = 0.5
							name.TextColor3 = Color3.fromRGB(255, 0, 0)
							if v.Name == "Flower1" then 
								name.Text = ("Blue Flower" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
								name.TextColor3 = Color3.fromRGB(0, 0, 255)
							end
							if v.Name == "Flower2" then
								name.Text = ("Red Flower" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
								name.TextColor3 = Color3.fromRGB(255, 0, 0)
							end
						else
							v['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
						end
					else
						if v:FindFirstChild('NameEsp'..Number) then
						v:FindFirstChild('NameEsp'..Number):Destroy()
						end
					end
				end   
			end)
		end
	end
	
Misc:Line()
Misc:Button("Rejoin",function()
		local ts = game:GetService("TeleportService")
		local p = game:GetService("Players").LocalPlayer
		ts:Teleport(game.PlaceId, p)
	end)
	local function HttpGet(url)
		return game:GetService("HttpService"):JSONDecode(htgetf(url))
	end
Misc:Button("Server Hop",function()
		local PlaceID = game.PlaceId
		local AllIDs = {}
		local foundAnything = ""
		local actualHour = os.date("!*t").hour
		local Deleted = false
		function TPReturner()
			local Site;
			if foundAnything == "" then
				Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
			else
				Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
			end
			local ID = ""
			if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
				foundAnything = Site.nextPageCursor
			end
			local num = 0;
			for i,v in pairs(Site.data) do
				local Possible = true
				ID = tostring(v.id)
				if tonumber(v.maxPlayers) > tonumber(v.playing) then
					for _,Existing in pairs(AllIDs) do
						if num ~= 0 then
							if ID == tostring(Existing) then
								Possible = false
							end
						else
							if tonumber(actualHour) ~= tonumber(Existing) then
								local delFile = pcall(function()
									-- delfile("NotSameServers.json")
									AllIDs = {}
									table.insert(AllIDs, actualHour)
								end)
							end
						end
						num = num + 1
					end
					if Possible == true then
						table.insert(AllIDs, ID)
						wait()
						pcall(function()
							-- writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
							wait()
							game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
						end)
						wait(4)
					end
				end
			end
		end
		function Teleport() 
			while wait() do
				pcall(function()
					TPReturner()
					if foundAnything ~= "" then
						TPReturner()
					end
				end)
			end
		end
		Teleport()
	end)
Misc:Line()
   Misc:Button("Join Pirates Team",function()
		local args = {
			[1] = "SetTeam",
			[2] = "Pirates"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args)) 
		local args = {
			[1] = "BartiloQuestProgress"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		local args = {
			[1] = "Buso"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Misc:Button("Join Marines Team",function()
		local args = {
			[1] = "SetTeam",
			[2] = "Marines"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		local args = {
			[1] = "BartiloQuestProgress"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		local args = {
			[1] = "Buso"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end)
	Misc:Button("Open Devil Shop",function()
		local args = {
			[1] = "GetFruits"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		game.Players.localPlayer.PlayerGui.Main.FruitShop.Visible = true
	end)
	Misc:Button("Open Inventory",function()
		local args = {
			[1] = "getInventoryWeapons"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		game.Players.localPlayer.PlayerGui.Main.Inventory.Visible = true
	end)
	Misc:Button("Open Fruit Inventory",function()
		game.Players.localPlayer.PlayerGui.Main.FruitInventory.Visible = true
	end)
	Misc:Button("Open Color Haki",function()
		game.Players.localPlayer.PlayerGui.Main.Colors.Visible = true
	end)
	Misc:Button("Open Title Name",function()
		local args = {
			[1] = "getTitles"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
		game.Players.localPlayer.PlayerGui.Main.Titles.Visible = true
	end)
Misc:Line()
	Misc:Toggle("Auto Click",autoclick,function(value)
		AuctoClick = value
	end)
	spawn(function()
		while wait() do
			if AuctoClick then
				Click()
			end
		end
	end)
	Misc:Toggle("Dodge No Cooldown",false,function(Value)
		nododgecool = Value
		NoDodgeCool()
	end)
	Misc:Toggle("Soru No Cooldown",false,function(Value)
		Sorunocool = Value
		NoSoruCool()
	end)
	Misc:Toggle("Infinits Geppo",false,function(Value)
		noGeppocool = Value
		NoGeppoCool()
	end)
Misc:Line()
    Misc:Button("Redeem All Code",function()
		function UseCode(Text)
			game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(Text)
		end
		UseCode("SUB2GAMERROBOT_EXP1")
		UseCode("StrawHatMaine")
		UseCode("Sub2OfficialNoobie")
		UseCode("FUDD10")
		UseCode("BIGNEWS")
		UseCode("THEGREATACE")
		UseCode("SUB2NOOBMASTER123")
		UseCode("Sub2Daigrock")
		UseCode("Axiore")
		UseCode("TantaiGaming")
		UseCode("STRAWHATMAINE")
	end)
	Misc:Button("Remove Lave",function()
		for i,v in pairs(game.Workspace:GetDescendants()) do
			if v.Name == "Lava" then   
				v:Destroy()
			end
		end
		for i,v in pairs(game.ReplicatedStorage:GetDescendants()) do
			if v.Name == "Lava" then   
				v:Destroy()
			end
		end
	end)
	Misc:Button("FPS Boost",function()
		local decalsyeeted = true -- Leaving this on makes games look shitty but the fps goes up by at least 20.
		local g = game
		local w = g.Workspace
		local l = g.Lighting
		local t = w.Terrain
		t.WaterWaveSize = 0
		t.WaterWaveSpeed = 0
		t.WaterReflectance = 0
		t.WaterTransparency = 0
		l.GlobalShadows = false
		l.FogEnd = 9e9
		l.Brightness = 0
		settings().Rendering.QualityLevel = "Level01"
		for i, v in pairs(g:GetDescendants()) do
			if v:IsA("Part") or v:IsA("Union") or v:IsA("CornerWedgePart") or v:IsA("TrussPart") then 
				v.Material = "Plastic"
				v.Reflectance = 0
			elseif v:IsA("Decal") or v:IsA("Texture") and decalsyeeted then
				v.Transparency = 1
			elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
				v.Lifetime = NumberRange.new(0)
			elseif v:IsA("Explosion") then
				v.BlastPressure = 1
				v.BlastRadius = 1
			elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
				v.Enabled = false
			elseif v:IsA("MeshPart") then
				v.Material = "Plastic"
				v.Reflectance = 0
				v.TextureID = 10385902758728957
			end
		end
		for i, e in pairs(l:GetChildren()) do
			if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then
				e.Enabled = false
			end
		end
	end)
	local LocalPlayer = game:GetService'Players'.LocalPlayer
	local originalstam = LocalPlayer.Character.Energy.Value
	function infinitestam()
		game:GetService'Players'.LocalPlayer.Character.Energy.Changed:connect(function()
			if InfinitsEnergy then
				LocalPlayer.Character.Energy.Value = originalstam
			end 
		end)
	end
	nododgecool = false
	function NoDodgeCool()
		if nododgecool then
			for i,v in next, getgc() do
				if game.Players.LocalPlayer.Character.Dodge then
					if typeof(v) == "function" and getfenv(v).script == game.Players.LocalPlayer.Character.Dodge then
						for i2,v2 in next, getupvalues(v) do
							if tostring(v2) == "0.4" then
								repeat wait(.1)
									setupvalue(v,i2,0)
								until not nododgecool
							end
						end
					end
				end
			end
		end
	end
	function NoGeppoCool()
		if noGeppocool then
			for i,v in next, getgc() do
				if game.Players.LocalPlayer.Character.Geppo then
					if typeof(v) == "function" and getfenv(v).script == game.Players.LocalPlayer.Character.Geppo then
						for i2,v2 in next, getupvalues(v) do
							if tostring(v2) == "0" then
								repeat wait(.1)
									setupvalue(v,i2,0)
								until not noGeppocool
							end
						end
					end
				end
			end
		end
	end
	function NoSoruCool()
		for i, v in pairs(getgc()) do
			if type(v) == "function" and getfenv(v).script == game.Players.LocalPlayer.Character:WaitForChild("Soru") then
				for i2,v2 in pairs(debug.getupvalues(v)) do
					if type(v2) == 'table' then
						if v2.LastUse then
							repeat wait()
								setupvalue(v, i2, {LastAfter = 0,LastUse = 0})
							until not Sorunocool
						end
					end
				end
			end
		end
	end

-- Setting

Setting:Toggle("Delete Attack Fx",nil,function(d)
    _G.DeleteAttackFx = d
    if _G.DeleteAttackFx == true then
    while _G.DeleteAttackFx do wait()
        for i, v in pairs(game.Workspace["_WorldOrigin"]:GetChildren()) do
            if v.Name == "CurvedRing" or v.Name == "SlashHit" or v.Name == "SwordSlash" or v.Name == "Sounds" then
                v:Destroy() 
            end
        end
    end
  end
end)

Setting:Toggle("Fast Attack",true,function(Fast)
    _G.FastAttack = Fast
end)

local Module = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
local CombatFramework = debug.getupvalues(Module)[2]
local CameraShakerR = require(game.ReplicatedStorage.Util.CameraShaker)

spawn(function()
    while true do
        if _G.FastAttack then
            pcall(function()
                CameraShakerR:Stop()
                CombatFramework.activeController.attacking = false
                CombatFramework.activeController.timeToNextAttack = 0
                CombatFramework.activeController.increment = 3
                CombatFramework.activeController.hitboxMagnitude = 100
                CombatFramework.activeController.blocking = false
                CombatFramework.activeController.timeToNextBlock = 0
                CombatFramework.activeController.focusStart = 0
                CombatFramework.activeController.humanoid.AutoRotate = true
            end)
        end
        task.wait()
    end
end)

Setting:Toggle("Bring Mob",true,function(Mag)
    Magnet = Mag
end)

Setting:Line()

Setting:Toggle("Auto Haki",true,function(d)
_G.AUTOHAKI = d
end)
spawn(function()
    while wait(.1) do
        if _G.AUTOHAKI then 
            if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                local args = {
                    [1] = "Buso"
                }
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            end
        end
    end
end)

Setting:Line()

LockLevelValue = 2300
OldLevel = game.Players.localPlayer.Data.Level.Value
Setting:Slider("Select Level Lock",1,LockLevelValue,LockLevelValue,nil,function(value)
	LockLevelValue = value
end)
Setting:Toggle("Lock Level",locklevel,function(value)
	LockLevel = value
end)
	spawn(function()
		while wait(.1) do
			if LockLevel then
				if game.Players.localPlayer.Data.Level.Value >= LockLevelValue then
					game.Players.localPlayer:Kick("Level Lock OFF")
				end
			end
		end
	end)

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

function totarget(CFgo)
    local tween_s = game:service"TweenService"
    local info = TweenInfo.new((game:GetService("Players")["LocalPlayer"].Character.HumanoidRootPart.Position - CFgo.Position).Magnitude/300, Enum.EasingStyle.Linear)
    local tween, err = pcall(function()
        tween = tween_s:Create(game.Players.LocalPlayer.Character["HumanoidRootPart"], info, {CFrame = CFgo})
        tween:Play()
    end)
    if not tween then return err end
end

spawn(function()
	game:GetService("RunService").Stepped:Connect(function()
		if farm or Auto_Farm then
			if not KRNL_LOADED and game.Players.LocalPlayer.Character:FindFirstChild("Humanoid") then
				setfflag("HumanoidParallelRemoveNoPhysics", "False")
				setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
				game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
			else
				if not game:GetService("Workspace"):FindFirstChild("LOL") then
					local LOL = Instance.new("Part")
					LOL.Name = "LOL"
					LOL.Parent = game.Workspace
					LOL.Anchored = true
					LOL.Transparency = 0.8
					LOL.Size = Vector3.new(50,0.5,50)
				elseif game:GetService("Workspace"):FindFirstChild("LOL") then
					game.Workspace["LOL"].CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.X,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Y - 3.8,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Z)
				end
			end
			for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
				if v:IsA("BasePart") then
					v.CanCollide = false
				end
			end
		end
	end)
end)

function CheckLevel()
    local Lv = game:GetService("Players").LocalPlayer.Data.Level.Value
    if Old_World then
        if Lv == 1 or Lv <= 9 or SelectMonster == "Bandit [Lv. 5]" then -- Bandit
            Ms = "Bandit [Lv. 5]"
            NameQuest = "BanditQuest1"
            QuestLv = 1
            NameMon = "Bandit"
            CFrameQ = CFrame.new(1060.9383544922, 16.455066680908, 1547.7841796875)
            CFrameMon = CFrame.new(1038.5533447266, 41.296249389648, 1576.5098876953)
        elseif Lv == 10 or Lv <= 14 or SelectMonster == "Monkey [Lv. 14]" then -- Monkey
            Ms = "Monkey [Lv. 14]"
            NameQuest = "JungleQuest"
            QuestLv = 1
            NameMon = "Monkey"
            CFrameQ = CFrame.new(-1601.6553955078, 36.85213470459, 153.38809204102)
            CFrameMon = CFrame.new(-1448.1446533203, 50.851993560791, 63.60718536377)
        elseif Lv == 15 or Lv <= 29 or SelectMonster == "Gorilla [Lv. 20]" then -- Gorilla
            Ms = "Gorilla [Lv. 20]"
            NameQuest = "JungleQuest"
            QuestLv = 2
            NameMon = "Gorilla"
            CFrameQ = CFrame.new(-1601.6553955078, 36.85213470459, 153.38809204102)
            CFrameMon = CFrame.new(-1142.6488037109, 40.462348937988, -515.39227294922)
        elseif Lv == 30 or Lv <= 39 or SelectMonster == "Pirate [Lv. 35]" then -- Pirate
            Ms = "Pirate [Lv. 35]"
            NameQuest = "BuggyQuest1"
            QuestLv = 1
            NameMon = "Pirate"
            CFrameQ = CFrame.new(-1140.1761474609, 4.752049446106, 3827.4057617188)
            CFrameMon = CFrame.new(-1201.0881347656, 40.628940582275, 3857.5966796875)
        elseif Lv == 40 or Lv <= 59 or SelectMonster == "Brute [Lv. 45]" then -- Brute
            Ms = "Brute [Lv. 45]"
            NameQuest = "BuggyQuest1"
            QuestLv = 2
            NameMon = "Brute"
            CFrameQ = CFrame.new(-1140.1761474609, 4.752049446106, 3827.4057617188)
            CFrameMon = CFrame.new(-1387.5324707031, 24.592035293579, 4100.9575195313)
        elseif Lv == 60 or Lv <= 74 or SelectMonster == "Desert Bandit [Lv. 60]" then -- Desert Bandit
            Ms = "Desert Bandit [Lv. 60]"
            NameQuest = "DesertQuest"
            QuestLv = 1
            NameMon = "Desert Bandit"
            CFrameQ = CFrame.new(896.51721191406, 6.4384617805481, 4390.1494140625)
            CFrameMon = CFrame.new(984.99896240234, 16.109552383423, 4417.91015625)
        elseif Lv == 75 or Lv <= 89 or SelectMonster == "Desert Officer [Lv. 70]" then -- Desert Officer
            Ms = "Desert Officer [Lv. 70]"
            NameQuest = "DesertQuest"
            QuestLv = 2
            NameMon = "Desert Officer"
            CFrameQ = CFrame.new(896.51721191406, 6.4384617805481, 4390.1494140625)
            CFrameMon = CFrame.new(1547.1510009766, 14.452038764954, 4381.8002929688)
        elseif Lv == 90 or Lv <= 99 or SelectMonster == "Snow Bandit [Lv. 90]" then -- Snow Bandit
            Ms = "Snow Bandit [Lv. 90]"
            NameQuest = "SnowQuest"
            QuestLv = 1
            NameMon = "Snow Bandit"
            CFrameQ = CFrame.new(1386.8073730469, 87.272789001465, -1298.3576660156)
            CFrameMon = CFrame.new(1356.3028564453, 105.76865386963, -1328.2418212891)
        elseif Lv == 100 or Lv <= 119 or SelectMonster == "Snowman [Lv. 100]" then -- Snowman
            Ms = "Snowman [Lv. 100]"
            NameQuest = "SnowQuest"
            QuestLv = 2
            NameMon = "Snowman"
            CFrameQ = CFrame.new(1386.8073730469, 87.272789001465, -1298.3576660156)
            CFrameMon = CFrame.new(1218.7956542969, 138.01184082031, -1488.0262451172)
        elseif Lv == 120 or Lv <= 149 or SelectMonster == "Chief Petty Officer [Lv. 120]" then -- Chief Petty Officer
            Ms = "Chief Petty Officer [Lv. 120]"
            NameQuest = "MarineQuest2"
            QuestLv = 1
            NameMon = "Chief Petty Officer"
            CFrameQ = CFrame.new(-5035.49609375, 28.677835464478, 4324.1840820313)
            CFrameMon = CFrame.new(-4931.1552734375, 65.793113708496, 4121.8393554688)
        elseif Lv == 150 or Lv <= 174 or SelectMonster == "Sky Bandit [Lv. 150]" then -- Sky Bandit
            Ms = "Sky Bandit [Lv. 150]"
            NameQuest = "SkyQuest"
            QuestLv = 1
            NameMon = "Sky Bandit"
            CFrameQ = CFrame.new(-4842.1372070313, 717.69543457031, -2623.0483398438)
            CFrameMon = CFrame.new(-4955.6411132813, 365.46365356445, -2908.1865234375)
        elseif Lv == 175 or Lv <= 189 or SelectMonster == "Dark Master [Lv. 175]" then -- Dark Master
            Ms = "Dark Master [Lv. 175]"
            NameQuest = "SkyQuest"
            QuestLv = 2
            NameMon = "Dark Master"
            CFrameQ = CFrame.new(-4842.1372070313, 717.69543457031, -2623.0483398438)
            CFrameMon = CFrame.new(-5148.1650390625, 439.04571533203, -2332.9611816406)
        elseif Lv == 190 or Lv <= 209 or SelectMonster == "Prisoner [Lv. 190]" then -- Prisoner
            Ms = "Prisoner [Lv. 190]"
            NameQuest = "JailKeeperQuest"
            QuestLv = 1
            NameMon = "Prisoner"
            CFrameQ = CFrame.new(5310.60547, 0.350014925, 474.946594, 0.0175017118, 0, 0.999846935, 0, 1, 0, -0.999846935, 0, 0.0175017118)
            CFrameMon = CFrame.new(4937.31885, 0.332031399, 649.574524, 0.694649816, 0, -0.719348073, 0, 1, 0, 0.719348073, 0, 0.694649816)
        elseif Lv == 210 or Lv <= 249 or SelectMonster == "Dangerous Prisoner [Lv. 210]" then -- Dangerous Prisoner
            Ms = "Dangerous Prisoner [Lv. 210]"
            NameQuest = "JailKeeperQuest"
            QuestLv = 2
            NameMon = "Dangerous Prisoner"
            CFrameQ = CFrame.new(5310.60547, 0.350014925, 474.946594, 0.0175017118, 0, 0.999846935, 0, 1, 0, -0.999846935, 0, 0.0175017118)
            CFrameMon = CFrame.new(5099.6626, 0.351562679, 1055.7583, 0.898906827, 0, -0.438139856, 0, 1, 0, 0.438139856, 0, 0.898906827)
        elseif Lv == 250 or Lv <= 274 or SelectMonster == "Toga Warrior [Lv. 250]" then -- Toga Warrior
            Ms = "Toga Warrior [Lv. 250]"
            NameQuest = "ColosseumQuest"
            QuestLv = 1
            NameMon = "Toga Warrior"
            CFrameQ = CFrame.new(-1577.7890625, 7.4151420593262, -2984.4838867188)
            CFrameMon = CFrame.new(-1872.5166015625, 49.080215454102, -2913.810546875)
        elseif Lv == 275 or Lv <= 299 or SelectMonster == "Gladiator [Lv. 275]" then -- Gladiator
            Ms = "Gladiator [Lv. 275]"
            NameQuest = "ColosseumQuest"
            QuestLv = 2
            NameMon = "Gladiator"
            CFrameQ = CFrame.new(-1577.7890625, 7.4151420593262, -2984.4838867188)
            CFrameMon = CFrame.new(-1521.3740234375, 81.203170776367, -3066.3139648438)
        elseif Lv == 300 or Lv <= 324 or SelectMonster == "Military Soldier [Lv. 300]" then -- Military Soldier
            Ms = "Military Soldier [Lv. 300]"
            NameQuest = "MagmaQuest"
            QuestLv = 1
            NameMon = "Military Soldier"
            CFrameQ = CFrame.new(-5316.1157226563, 12.262831687927, 8517.00390625)
            CFrameMon = CFrame.new(-5369.0004882813, 61.24352645874, 8556.4921875)
        elseif Lv == 325 or Lv <= 374 or SelectMonster == "Military Spy [Lv. 325]" then -- Military Spy
            Ms = "Military Spy [Lv. 325]"
            NameQuest = "MagmaQuest"
            QuestLv = 2
            NameMon = "Military Spy"
            CFrameQ = CFrame.new(-5316.1157226563, 12.262831687927, 8517.00390625)
            CFrameMon = CFrame.new(-5787.00293, 75.8262634, 8651.69922, 0.838590562, 0, -0.544762194, 0, 1, 0, 0.544762194, 0, 0.838590562)
        elseif Lv == 375 or Lv <= 399 or SelectMonster == "Fishman Warrior [Lv. 375]" then -- Fishman Warrior 
            Ms = "Fishman Warrior [Lv. 375]"
            NameQuest = "FishmanQuest"
            QuestLv = 1
            NameMon = "Fishman Warrior"
            CFrameQ = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
            CFrameMon = CFrame.new(60844.10546875, 98.462875366211, 1298.3985595703)
			if Auto_Farm and (CFrameMon.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 3000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
			end
        elseif Lv == 400 or Lv <= 449 or SelectMonster == "Fishman Commando [Lv. 400]" then -- Fishman Commando
            Ms = "Fishman Commando [Lv. 400]"
            NameQuest = "FishmanQuest"
            QuestLv = 2
            NameMon = "Fishman Commando"
            CFrameQ = CFrame.new(61122.65234375, 18.497442245483, 1569.3997802734)
            CFrameMon = CFrame.new(61738.3984375, 64.207321166992, 1433.8375244141)
			if Auto_Farm and (CFrameMon.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 3000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
			end
        elseif Lv == 450 or Lv <= 474 or SelectMonster == "God's Guard [Lv. 450]" then -- God's Guard
            Ms = "God's Guard [Lv. 450]"
            NameQuest = "SkyExp1Quest"
            QuestLv = 1
            NameMon = "God's Guard"
            CFrameQ = CFrame.new(-4721.8603515625, 845.30297851563, -1953.8489990234)
            CFrameMon = CFrame.new(-4628.0498046875, 866.92877197266, -1931.2352294922)
			if Auto_Farm and (CFrameMon.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 3000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
			end
        elseif Lv == 475 or Lv <= 524 or SelectMonster == "Shanda [Lv. 475]" then -- Shanda
            Ms = "Shanda [Lv. 475]"
            NameQuest = "SkyExp1Quest"
            QuestLv = 2
            NameMon = "Shanda"
            CFrameQ = CFrame.new(-7863.1596679688, 5545.5190429688, -378.42266845703)
            CFrameMon = CFrame.new(-7685.1474609375, 5601.0751953125, -441.38876342773)
			if Auto_Farm and (CFrameMon.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 3000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
			end
        elseif Lv == 525 or Lv <= 549 or SelectMonster == "Royal Squad [Lv. 525]" then -- Royal Squad
            Ms = "Royal Squad [Lv. 525]"
            NameQuest = "SkyExp2Quest"
            QuestLv = 1
            NameMon = "Royal Squad"
            CFrameQ = CFrame.new(-7903.3828125, 5635.9897460938, -1410.923828125)
            CFrameMon = CFrame.new(-7654.2514648438, 5637.1079101563, -1407.7550048828)
        elseif Lv == 550 or Lv <= 624 or SelectMonster == "Royal Soldier [Lv. 550]" then -- Royal Soldier
            Ms = "Royal Soldier [Lv. 550]"
            NameQuest = "SkyExp2Quest"
            QuestLv = 2
            NameMon = "Royal Soldier"
            CFrameQ = CFrame.new(-7903.3828125, 5635.9897460938, -1410.923828125)
            CFrameMon = CFrame.new(-7760.4106445313, 5679.9077148438, -1884.8112792969)
        elseif Lv == 625 or Lv <= 649 or SelectMonster == "Galley Pirate [Lv. 625]" then -- Galley Pirate
            Ms = "Galley Pirate [Lv. 625]"
            NameQuest = "FountainQuest"
            QuestLv = 1
            NameMon = "Galley Pirate"
            CFrameQ = CFrame.new(5258.2788085938, 38.526931762695, 4050.044921875)
            CFrameMon = CFrame.new(5557.1684570313, 152.32717895508, 3998.7758789063)
        elseif Lv >= 650 or SelectMonster == "Galley Captain [Lv. 650]" then -- Galley Captain
            Ms = "Galley Captain [Lv. 650]"
            NameQuest = "FountainQuest"
            QuestLv = 2
            NameMon = "Galley Captain"
            CFrameQ = CFrame.new(5258.2788085938, 38.526931762695, 4050.044921875)
            CFrameMon = CFrame.new(5677.6772460938, 92.786109924316, 4966.6323242188)
        end
    end
    if New_World then
        if Lv == 700 or Lv <= 724 or SelectMonster == "Raider [Lv. 700]" then -- Raider
            Ms = "Raider [Lv. 700]"
            NameQuest = "Area1Quest"
            QuestLv = 1
            NameMon = "Raider"
            CFrameQ = CFrame.new(-427.72567749023, 72.99634552002, 1835.9426269531)
            CFrameMon = CFrame.new(68.874565124512, 93.635643005371, 2429.6752929688)
        elseif Lv == 725 or Lv <= 774 or SelectMonster == "Mercenary [Lv. 725]" then -- Mercenary
            Ms = "Mercenary [Lv. 725]"
            NameQuest = "Area1Quest"
            QuestLv = 2
            NameMon = "Mercenary"
            CFrameQ = CFrame.new(-427.72567749023, 72.99634552002, 1835.9426269531)
            CFrameMon = CFrame.new(-864.85009765625, 122.47104644775, 1453.1505126953)
        elseif Lv == 775 or Lv <= 799 or SelectMonster == "Swan Pirate [Lv. 775]" then -- Swan Pirate
            Ms = "Swan Pirate [Lv. 775]"
            NameQuest = "Area2Quest"
            QuestLv = 1
            NameMon = "Swan Pirate"
            CFrameQ = CFrame.new(635.61151123047, 73.096351623535, 917.81298828125)
            CFrameMon = CFrame.new(1065.3669433594, 137.64012145996, 1324.3798828125)
        elseif Lv == 800 or Lv <= 874 or SelectMonster == "Factory Staff [Lv. 800]" then -- Factory Staff
            Ms = "Factory Staff [Lv. 800]"
            NameQuest = "Area2Quest"
            QuestLv = 2
            NameMon = "Factory Staff"
            CFrameQ = CFrame.new(635.61151123047, 73.096351623535, 917.81298828125)
            CFrameMon = CFrame.new(533.22045898438, 128.46876525879, 355.62615966797)
        elseif Lv == 875 or Lv <= 899 or SelectMonster == "Marine Lieutenant [Lv. 875]" then -- Marine Lieutenant
            Ms = "Marine Lieutenant [Lv. 875]"
            NameQuest = "MarineQuest3"
            QuestLv = 1
            NameMon = "Marine Lieutenant"
            CFrameQ = CFrame.new(-2440.9934082031, 73.04190826416, -3217.7082519531)
            CFrameMon = CFrame.new(-2489.2622070313, 84.613594055176, -3151.8830566406)
        elseif Lv == 900 or Lv <= 949 or SelectMonster == "Marine Captain [Lv. 900]" then -- Marine Captain
            Ms = "Marine Captain [Lv. 900]"
            NameQuest = "MarineQuest3"
            QuestLv = 2
            NameMon = "Marine Captain"
            CFrameQ = CFrame.new(-2440.9934082031, 73.04190826416, -3217.7082519531)
            CFrameMon = CFrame.new(-2335.2026367188, 79.786659240723, -3245.8674316406)
        elseif Lv == 950 or Lv <= 974 or SelectMonster == "Zombie [Lv. 950]" then -- Zombie
            Ms = "Zombie [Lv. 950]"
            NameQuest = "ZombieQuest"
            QuestLv = 1
            NameMon = "Zombie"
            CFrameQ = CFrame.new(-5494.3413085938, 48.505931854248, -794.59094238281)
            CFrameMon = CFrame.new(-5536.4970703125, 101.08577728271, -835.59075927734)
        elseif Lv == 975 or Lv <= 999 or SelectMonster == "Vampire [Lv. 975]" then -- Vampire
            Ms = "Vampire [Lv. 975]"
            NameQuest = "ZombieQuest"
            QuestLv = 2
            NameMon = "Vampire"
            CFrameQ = CFrame.new(-5494.3413085938, 48.505931854248, -794.59094238281)
            CFrameMon = CFrame.new(-5806.1098632813, 16.722528457642, -1164.4384765625)
        elseif Lv == 1000 or Lv <= 1049 or SelectMonster == "Snow Trooper [Lv. 1000]" then -- Snow Trooper
            Ms = "Snow Trooper [Lv. 1000]"
            NameQuest = "SnowMountainQuest"
            QuestLv = 1
            NameMon = "Snow Trooper"
            CFrameQ = CFrame.new(607.05963134766, 401.44781494141, -5370.5546875)
            CFrameMon = CFrame.new(535.21051025391, 432.74209594727, -5484.9165039063)
        elseif Lv == 1050 or Lv <= 1099 or SelectMonster == "Winter Warrior [Lv. 1050]" then -- Winter Warrior
            Ms = "Winter Warrior [Lv. 1050]"
            NameQuest = "SnowMountainQuest"
            QuestLv = 2
            NameMon = "Winter Warrior"
            CFrameQ = CFrame.new(607.05963134766, 401.44781494141, -5370.5546875)
            CFrameMon = CFrame.new(1234.4449462891, 456.95419311523, -5174.130859375)
        elseif Lv == 1100 or Lv <= 1124 or SelectMonster == "Lab Subordinate [Lv. 1100]" then -- Lab Subordinate
            Ms = "Lab Subordinate [Lv. 1100]"
            NameQuest = "IceSideQuest"
            QuestLv = 1
            NameMon = "Lab Subordinate"
            CFrameQ = CFrame.new(-6061.841796875, 15.926671981812, -4902.0385742188)
            CFrameMon = CFrame.new(-5720.5576171875, 63.309471130371, -4784.6103515625)
        elseif Lv == 1125 or Lv <= 1174 or SelectMonster == "Horned Warrior [Lv. 1125]" then -- Horned Warrior
            Ms = "Horned Warrior [Lv. 1125]"
            NameQuest = "IceSideQuest"
            QuestLv = 2
            NameMon = "Horned Warrior"
            CFrameQ = CFrame.new(-6061.841796875, 15.926671981812, -4902.0385742188)
            CFrameMon = CFrame.new(-6292.751953125, 91.181983947754, -5502.6499023438)
        elseif Lv == 1175 or Lv <= 1199 or SelectMonster == "Magma Ninja [Lv. 1175]" then -- Magma Ninja
            Ms = "Magma Ninja [Lv. 1175]"
            NameQuest = "FireSideQuest"
            QuestLv = 1
            NameMon = "Magma Ninja"
            CFrameQ = CFrame.new(-5429.0473632813, 15.977565765381, -5297.9614257813)
            CFrameMon = CFrame.new(-5461.8388671875, 130.36347961426, -5836.4702148438)
        elseif Lv == 1200 or Lv <= 1249 or SelectMonster == "Lava Pirate [Lv. 1200]" then -- Lava Pirate
            Ms = "Lava Pirate [Lv. 1200]"
            NameQuest = "FireSideQuest"
            QuestLv = 2
            NameMon = "Lava Pirate"
            CFrameQ = CFrame.new(-5429.0473632813, 15.977565765381, -5297.9614257813)
            CFrameMon = CFrame.new(-5251.1889648438, 55.164535522461, -4774.4096679688)
        elseif Lv == 1250 or Lv <= 1274 or SelectMonster == "Ship Deckhand [Lv. 1250]" then -- Ship Deckhand
            Ms = "Ship Deckhand [Lv. 1250]"
            NameQuest = "ShipQuest1"
            QuestLv = 1
            NameMon = "Ship Deckhand"
            CFrameQ = CFrame.new(1040.2927246094, 125.08293151855, 32911.0390625)
            CFrameMon = CFrame.new(921.12365722656, 125.9839553833, 33088.328125)
			if Auto_Farm and (CFrameMon.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 20000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
        elseif Lv == 1275 or Lv <= 1299 or SelectMonster == "Ship Engineer [Lv. 1275]" then -- Ship Engineer
            Ms = "Ship Engineer [Lv. 1275]"
            NameQuest = "ShipQuest1"
            QuestLv = 2
            NameMon = "Ship Engineer"
            CFrameQ = CFrame.new(1040.2927246094, 125.08293151855, 32911.0390625)
            CFrameMon = CFrame.new(886.28179931641, 40.47790145874, 32800.83203125)
			if Auto_Farm and (CFrameMon.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 20000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
        elseif Lv == 1300 or Lv <= 1324 or SelectMonster == "Ship Steward [Lv. 1300]" then -- Ship Steward
            Ms = "Ship Steward [Lv. 1300]"
            NameQuest = "ShipQuest2"
            QuestLv = 1
            NameMon = "Ship Steward"
            CFrameQ = CFrame.new(971.42065429688, 125.08293151855, 33245.54296875)
            CFrameMon = CFrame.new(943.85504150391, 129.58183288574, 33444.3671875)
			if Auto_Farm and (CFrameMon.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 20000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
        elseif Lv == 1325 or Lv <= 1349 or SelectMonster == "Ship Officer [Lv. 1325]" then -- Ship Officer
            Ms = "Ship Officer [Lv. 1325]"
            NameQuest = "ShipQuest2"
            QuestLv = 2
            NameMon = "Ship Officer"
            CFrameQ = CFrame.new(971.42065429688, 125.08293151855, 33245.54296875)
            CFrameMon = CFrame.new(955.38458251953, 181.08335876465, 33331.890625)
			if Auto_Farm and (CFrameMon.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 20000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
        elseif Lv == 1350 or Lv <= 1374 or SelectMonster == "Arctic Warrior [Lv. 1350]" then -- Arctic Warrior
            Ms = "Arctic Warrior [Lv. 1350]"
            NameQuest = "FrostQuest"
            QuestLv = 1
            NameMon = "Arctic Warrior"
            CFrameQ = CFrame.new(5668.1372070313, 28.202531814575, -6484.6005859375)
            CFrameMon = CFrame.new(5935.4541015625, 77.26016998291, -6472.7568359375)
			if Auto_Farm and (CFrameMon.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 20000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 89.034996032715, -132.83953857422))
			end
        elseif Lv == 1375 or Lv <= 1424 or SelectMonster == "Snow Lurker [Lv. 1375]" then -- Snow Lurker
            Ms = "Snow Lurker [Lv. 1375]"
            NameQuest = "FrostQuest"
            QuestLv = 2
            NameMon = "Snow Lurker"
            CFrameQ = CFrame.new(5668.1372070313, 28.202531814575, -6484.6005859375)
            CFrameMon = CFrame.new(5628.482421875, 57.574996948242, -6618.3481445313)
        elseif Lv == 1425 or Lv <= 1449 or SelectMonster == "Sea Soldier [Lv. 1425]" then -- Sea Soldier
            Ms = "Sea Soldier [Lv. 1425]"
            NameQuest = "ForgottenQuest"
            QuestLv = 1
            NameMon = "Sea Soldier"
            CFrameQ = CFrame.new(-3054.5827636719, 236.87213134766, -10147.790039063)
            CFrameMon = CFrame.new(-3185.0153808594, 58.789089202881, -9663.6064453125)
        elseif Lv >= 1450 or SelectMonster == "Water Fighter [Lv. 1450]" then -- Water Fighter
            Ms = "Water Fighter [Lv. 1450]"
            NameQuest = "ForgottenQuest"
            QuestLv = 2
            NameMon = "Water Fighter"
            CFrameQ = CFrame.new(-3054.5827636719, 236.87213134766, -10147.790039063)
            CFrameMon = CFrame.new(-3262.9301757813, 298.69036865234, -10552.529296875)
		end
	end
	if Three_World then
		if Lv == 1500 or Lv <= 1524 or SelectMonster == "Pirate Millionaire [Lv. 1500]" then -- Pirate Millionaire
			Ms = "Pirate Millionaire [Lv. 1500]"
			NameQuest = "PiratePortQuest"
			QuestLv = 1
			NameMon = "Pirate Millionaire"
			CFrameQ = CFrame.new(-289.61752319336, 43.819011688232, 5580.0903320313)
			CFrameMon = CFrame.new(-435.68109130859, 189.69866943359, 5551.0756835938)
		elseif Lv == 1525 or Lv <= 1574 or SelectMonster == "Pistol Billionaire [Lv. 1525]" then -- Pistol Billoonaire
			Ms = "Pistol Billionaire [Lv. 1525]"
			NameQuest = "PiratePortQuest"
			QuestLv = 2
			NameMon = "Pistol Billionaire"
			CFrameQ = CFrame.new(-289.61752319336, 43.819011688232, 5580.0903320313)
			CFrameMon = CFrame.new(-236.53652954102, 217.46676635742, 6006.0883789063)
		elseif Lv == 1575 or Lv <= 1599 or SelectMonster == "Dragon Crew Warrior [Lv. 1575]" then -- Dragon Crew Warrior
			Ms = "Dragon Crew Warrior [Lv. 1575]"
			NameQuest = "AmazonQuest"
			QuestLv = 1
			NameMon = "Dragon Crew Warrior"
			CFrameQ = CFrame.new(5833.1147460938, 51.60498046875, -1103.0693359375)
			CFrameMon = CFrame.new(6301.9975585938, 104.77153015137, -1082.6075439453)
		elseif Lv == 1600 or Lv <= 1624 or SelectMonster == "Dragon Crew Archer [Lv. 1600]" then -- Dragon Crew Archer
			Ms = "Dragon Crew Archer [Lv. 1600]"
			NameQuest = "AmazonQuest"
			QuestLv = 2
			NameMon = "Dragon Crew Archer"
			CFrameQ = CFrame.new(5833.1147460938, 51.60498046875, -1103.0693359375)
			CFrameMon = CFrame.new(6831.1171875, 441.76708984375, 446.58615112305)
		elseif Lv == 1625 or Lv <= 1649 or SelectMonster == "Female Islander [Lv. 1625]" then -- Female Islander
			Ms = "Female Islander [Lv. 1625]"
			NameQuest = "AmazonQuest2"
			QuestLv = 1
			NameMon = "Female Islander"
			CFrameQ = CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
			CFrameMon = CFrame.new(5792.5166015625, 848.14392089844, 1084.1818847656)
		elseif Lv == 1650 or Lv <= 1699 or SelectMonster == "Giant Islander [Lv. 1650]" then -- Giant Islander
			Ms = "Giant Islander [Lv. 1650]"
			NameQuest = "AmazonQuest2"
			QuestLv = 2
			NameMon = "Giant Islander"
			CFrameQ = CFrame.new(5446.8793945313, 601.62945556641, 749.45672607422)
			CFrameMon = CFrame.new(5009.5068359375, 664.11071777344, -40.960144042969)
		elseif Lv == 1700 or Lv <= 1724 or SelectMonster == "Marine Commodore [Lv. 1700]" then -- Marine Commodore
			Ms = "Marine Commodore [Lv. 1700]"
			NameQuest = "MarineTreeIsland"
			QuestLv = 1
			NameMon = "Marine Commodore"
			CFrameQ = CFrame.new(2179.98828125, 28.731239318848, -6740.0551757813)
			CFrameMon = CFrame.new(2198.0063476563, 128.71075439453, -7109.5043945313)
		elseif Lv == 1725 or Lv <= 1774 or SelectMonster == "Marine Rear Admiral [Lv. 1725]" then -- Marine Rear Admiral
			Ms = "Marine Rear Admiral [Lv. 1725]"
			NameQuest = "MarineTreeIsland"
			QuestLv = 2
			NameMon = "Marine Rear Admiral"
			CFrameQ = CFrame.new(2179.98828125, 28.731239318848, -6740.0551757813)
			CFrameMon = CFrame.new(3294.3142089844, 385.41125488281, -7048.6342773438)
		elseif Lv == 1775 or Lv <= 1799 or SelectMonster == "Fishman Raider [Lv. 1775]" then -- Fishman Raide
			Ms = "Fishman Raider [Lv. 1775]"
			NameQuest = "DeepForestIsland3"
			QuestLv = 1
			NameMon = "Fishman Raider"
			CFrameQ = CFrame.new(-10582.759765625, 331.78845214844, -8757.666015625)
			CFrameMon = CFrame.new(-10553.268554688, 521.38439941406, -8176.9458007813)
		elseif Lv == 1800 or Lv <= 1824 or SelectMonster == "Fishman Captain [Lv. 1800]" then -- Fishman Captain
			Ms = "Fishman Captain [Lv. 1800]"
			NameQuest = "DeepForestIsland3"
			QuestLv = 2
			NameMon = "Fishman Captain"
			CFrameQ = CFrame.new(-10583.099609375, 331.78845214844, -8759.4638671875)
			CFrameMon = CFrame.new(-10789.401367188, 427.18637084961, -9131.4423828125)
		elseif Lv == 1825 or Lv <= 1849 or SelectMonster == "Forest Pirate [Lv. 1825]" then -- Forest Pirate
			Ms = "Forest Pirate [Lv. 1825]"
			NameQuest = "DeepForestIsland"
			QuestLv = 1
			NameMon = "Forest Pirate"
			CFrameQ = CFrame.new(-13232.662109375, 332.40396118164, -7626.4819335938)
			CFrameMon = CFrame.new(-13489.397460938, 400.30349731445, -7770.251953125)
		elseif Lv == 1850 or Lv <= 1899 or SelectMonster == "Mythological Pirate [Lv. 1850]" then -- Mythological Pirate
			Ms = "Mythological Pirate [Lv. 1850]"
			NameQuest = "DeepForestIsland"
			QuestLv = 2
			NameMon = "Mythological Pirate"
			CFrameQ = CFrame.new(-13232.662109375, 332.40396118164, -7626.4819335938)
			CFrameMon = CFrame.new(-13508.616210938, 582.46228027344, -6985.3037109375)
		elseif Lv == 1900 or Lv <= 1924 or SelectMonster == "Jungle Pirate [Lv. 1900]" then -- Jungle Pirate
			Ms = "Jungle Pirate [Lv. 1900]"
			NameQuest = "DeepForestIsland2"
			QuestLv = 1
			NameMon = "Jungle Pirate"
			CFrameQ = CFrame.new(-12682.096679688, 390.88653564453, -9902.1240234375)
			CFrameMon = CFrame.new(-12267.103515625, 459.75262451172, -10277.200195313)
		elseif Lv == 1925 or Lv <= 1974 or SelectMonster == "Musketeer Pirate [Lv. 1925]" then -- Musketeer Pirate
			Ms = "Musketeer Pirate [Lv. 1925]"
			NameQuest = "DeepForestIsland2"
			QuestLv = 2
			NameMon = "Musketeer Pirate"
			CFrameQ = CFrame.new(-12682.096679688, 390.88653564453, -9902.1240234375)
			CFrameMon = CFrame.new(-13291.5078125, 520.47338867188, -9904.638671875)
		elseif Lv == 1975 or Lv <= 1999 or SelectMonster == "Reborn Skeleton [Lv. 1975]" then
			Ms = "Reborn Skeleton [Lv. 1975]"
			NameQuest = "HauntedQuest1"
			QuestLv = 1
			NameMon = "Reborn Skeleton"
			CFrameQ = CFrame.new(-9480.80762, 142.130661, 5566.37305, -0.00655503059, 4.52954225e-08, -0.999978542, 2.04920472e-08, 1, 4.51620679e-08, 0.999978542, -2.01955679e-08, -0.00655503059)
			CFrameMon = CFrame.new(-8761.77148, 183.431747, 6168.33301, 0.978073597, -1.3950732e-05, -0.208259016, -1.08073925e-06, 1, -7.20630269e-05, 0.208259016, 7.07080399e-05, 0.978073597)
		elseif Lv == 2000 or Lv <= 2024 or SelectMonster == "Living Zombie [Lv. 2000]" then
			Ms = "Living Zombie [Lv. 2000]"
			NameQuest = "HauntedQuest1"
			QuestLv = 2
			NameMon = "Living Zombie"
			CFrameQ = CFrame.new(-9480.80762, 142.130661, 5566.37305, -0.00655503059, 4.52954225e-08, -0.999978542, 2.04920472e-08, 1, 4.51620679e-08, 0.999978542, -2.01955679e-08, -0.00655503059)
			CFrameMon = CFrame.new(-10103.7529, 238.565979, 6179.75977, 0.999474227, 2.77547141e-08, 0.0324240364, -2.58006327e-08, 1, -6.06848474e-08, -0.0324240364, 5.98163865e-08, 0.999474227)
		elseif Lv == 2025 or Lv <= 2049 or SelectMonster == "Demonic Soul [Lv. 2025]" then
			Ms = "Demonic Soul [Lv. 2025]"
			NameQuest = "HauntedQuest2"
			QuestLv = 1
			NameMon = "Demonic Soul"
			CFrameQ = CFrame.new(-9516.9931640625, 178.00651550293, 6078.4653320313)
			CFrameMon = CFrame.new(-9712.03125, 204.69589233398, 6193.322265625)
		elseif Lv == 2050 or Lv <= 2074 or SelectMonster == "Posessed Mummy [Lv. 2050]" then
			Ms = "Posessed Mummy [Lv. 2050]"
			NameQuest = "HauntedQuest2"
			QuestLv = 2
			NameMon = "Posessed Mummy"
			CFrameQ = CFrame.new(-9516.9931640625, 178.00651550293, 6078.4653320313)
			CFrameMon = CFrame.new(-9545.7763671875, 69.619895935059, 6339.5615234375)
        elseif Lv == 2075 and Lv <= 2099 or SelectMonster == "Peanut Scout [Lv. 2075]" then
            Ms = "Peanut Scout [Lv. 2075]"
            NameQuest = "NutsIslandQuest"
            QuestLv = 1
            NameMon = "Peanut Scout"
            CFrameQ = CFrame.new(-2105.53198, 37.2495995, -10195.5088, -0.766061664, 0, -0.642767608, 0, 1, 0, 0.642767608, 0, -0.766061664)
            CFrameMon = CFrame.new(-2126.47998, 192.095154, -10204.6553, 0.0779861137, -9.29044361e-08, 0.996954441, 6.59006432e-08, 1, 8.80332109e-08, -0.996954441, 5.88345728e-08, 0.0779861137)
        elseif Lv == 2100 and Lv <= 2124 or SelectMonster == "Peanut President [Lv. 2100]" then
            Ms = "Peanut President [Lv. 2100]"
            NameQuest = "NutsIslandQuest"
            QuestLv = 2
            NameMon = "Peanut President"
            CFrameQ = CFrame.new(-2105.53198, 37.2495995, -10195.5088, -0.766061664, 0, -0.642767608, 0, 1, 0, 0.642767608, 0, -0.766061664)
            CFrameMon = CFrame.new(-2126.47998, 192.095154, -10204.6553, 0.0779861137, -9.29044361e-08, 0.996954441, 6.59006432e-08, 1, 8.80332109e-08, -0.996954441, 5.88345728e-08, 0.0779861137)
        elseif Lv == 2125 and Lv <= 2149 or SelectMonster == "Ice Cream Chef [Lv. 2125]" then
            Ms = "Ice Cream Chef [Lv. 2125]"
            NameQuest = "IceCreamIslandQuest"
            QuestLv = 1
            NameMon = "Ice Cream Chef"
            CFrameQ = CFrame.new(-819.376709, 64.9259796, -10967.2832, -0.766061664, 0, 0.642767608, 0, 1, 0, -0.642767608, 0, -0.766061664)
            CFrameMon = CFrame.new(-789.941528, 209.382889, -11009.9805, -0.0703101531, -0, -0.997525156, -0, 1.00000012, -0, 0.997525275, 0, -0.0703101456)
        elseif Lv == 2150 or Lv <= 2199 or SelectMonster == "Ice Cream Commander [Lv. 2150]" then
            Ms = "Ice Cream Commander [Lv. 2150]"
            NameQuest = "IceCreamIslandQuest"
            QuestLv = 2
            NameMon = "Ice Cream Commander"
            CFrameQ = CFrame.new(-819.376709, 64.9259796, -10967.2832, -0.766061664, 0, 0.642767608, 0, 1, 0, -0.642767608, 0, -0.766061664)
            CFrameMon = CFrame.new(-789.941528, 209.382889, -11009.9805, -0.0703101531, -0, -0.997525156, -0, 1.00000012, -0, 0.997525275, 0, -0.0703101456)
        elseif Lv == 2200 or Lv <= 2224 or SelectMonster == "Cookie Crafter [Lv. 2200]" then
            Ms = "Cookie Crafter [Lv. 2200]"
            NameQuest = "CakeQuest1"
            QuestLv = 1
            NameMon = "Cookie Crafter"
            CFrameQ = CFrame.new(-2022.29858, 36.9275894, -12030.9766, -0.961273909, 0, -0.275594592, 0, 1, 0, 0.275594592, 0, -0.961273909)
            CFrameMon = CFrame.new(-2321.71216, 36.699482, -12216.7871, -0.780074954, 0, 0.625686109, 0, 1, 0, -0.625686109, 0, -0.780074954)
        elseif Lv == 2225 or Lv <= 2249 or SelectMonster == "Cake Guard [Lv. 2225]" then
            Ms = "Cake Guard [Lv. 2225]"
            NameQuest = "CakeQuest1"
            QuestLv = 2
            NameMon = "Cake Guard"
            CFrameQ = CFrame.new(-2022.29858, 36.9275894, -12030.9766, -0.961273909, 0, -0.275594592, 0, 1, 0, 0.275594592, 0, -0.961273909)
            CFrameMon = CFrame.new(-1418.11011, 36.6718941, -12255.7324, 0.0677844882, 0, 0.997700036, 0, 1, 0, -0.997700036, 0, 0.0677844882)
        elseif Lv == 2250 or Lv <= 2274 or SelectMonster == "Baking Staff [Lv. 2250]" then
            Ms = "Baking Staff [Lv. 2250]"
            NameQuest = "CakeQuest2"
            QuestLv = 1
            NameMon = "Baking Staff"
            CFrameQ = CFrame.new(-1928.31763, 37.7296638, -12840.626, 0.951068401, -0, -0.308980465, 0, 1, -0, 0.308980465, 0, 0.951068401)
            CFrameMon = CFrame.new(-1980.43848, 36.6716766, -12983.8418, -0.254443765, 0, -0.967087567, 0, 1, 0, 0.967087567, 0, -0.254443765)
        elseif Lv >= 2275 or SelectMonster == "Head Baker [Lv. 2275]" then
            Ms = "Head Baker [Lv. 2275]"
            NameQuest = "CakeQuest2"
            QuestLv = 2
            NameMon = "Head Baker"
            CFrameQ = CFrame.new(-1928.31763, 37.7296638, -12840.626, 0.951068401, -0, -0.308980465, 0, 1, -0, 0.308980465, 0, 0.951068401)
            CFrameMon = CFrame.new(-2251.5791, 52.2714615, -13033.3965, -0.991971016, 0, -0.126466095, 0, 1, 0, 0.126466095, 0, -0.991971016)
        end
	end
end

function EquipWeapon(ToolSe)
    if game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe) then
        local tool = game.Players.LocalPlayer.Backpack:FindFirstChild(ToolSe)
        wait(.4)
        game.Players.LocalPlayer.Character.Humanoid:EquipTool(tool)
    end
end

Type = 1
spawn(function()
	while wait(.1) do
        if Type == 1 then
		    Farm_Mode = CFrame.new(0, 30, 0)
        elseif Type == 2 then
            Farm_Mode = CFrame.new(0, 30, 0)
        end
	end
end)

spawn(function()
	while wait(.1) do
		Type = 1
        wait(5)
        Type = 2
        wait(5)
	end
end)

pcall(function()
	for i,v in pairs(game:GetService("Workspace").Map.Dressrosa.Tavern:GetDescendants()) do
		if v.ClassName == "Seat" then
			v:Destroy()
		end
	end
end)

spawn(function()
	while wait() do
		if Auto_Farm then
			if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
				MagnetActive = false
				CheckLevel()
				totarget(CFrameQ)
				if (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 4 then
					wait(1.1)
					CheckLevel()
					if (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 20 then
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", NameQuest, QuestLv)
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
					else
						totarget(CFrameQ)
					end
				end
			elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
				pcall(function()
					CheckLevel()
					if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if v.Name == Ms and v:FindFirstChild("Humanoid") then
								if v.Humanoid.Health > 0 then
									repeat game:GetService("RunService").Heartbeat:wait()
										if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
											if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameMon) then
												EquipWeapon(SelectToolWeapon)
												totarget(v.HumanoidRootPart.CFrame * Farm_Mode)
												v.HumanoidRootPart.CanCollide = false
												v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
												game:GetService("VirtualUser"):CaptureController()
												game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
												PosMon = v.HumanoidRootPart.CFrame
												MagnetActive = true
											else
												MagnetActive = false    
												game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AbandonQuest")
											end
										else
											MagnetActive = false
											CheckLevel()
											totarget(CFrameMon)
										end
									until not v.Parent or v.Humanoid.Health <= 0 or Auto_Farm == false or game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == false or not game:GetService("Workspace").Enemies:FindFirstChild(v.Name)
								end
							end
						end
					else
						MagnetActive = false
						CheckLevel()
						totarget(CFrameMon)
					end
				end)
			end
		end
	end
end)

function Click()
    game:GetService'VirtualUser':CaptureController()
    game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
end

if SelectToolWeapon then
else
    SelectToolWeapon = ""
end

spawn(function()
   while wait() do
      pcall(function()
          for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
             if Auto_Farm and MagnetActive and Magnet then
                if v.Name == Ms and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                    if v.Name == "Factory Staff [Lv. 800]" then
                        if (v.HumanoidRootPart.Position - PosMon.Position).Magnitude <= 250 then
                            v.Head.CanCollide = false
                            v.HumanoidRootPart.CanCollide = false
                            v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
                            v.HumanoidRootPart.CFrame = PosMon
                            if v.Humanoid:FindFirstChild("Animator") then
                                v.Humanoid.Animator:Destroy()
                            end
                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                        end
                    elseif v.Name == Ms then
                        if (v.HumanoidRootPart.Position - PosMon.Position).Magnitude <= 400 then
                            v.Head.CanCollide = false
                            v.HumanoidRootPart.CanCollide = false
                            v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
                            v.HumanoidRootPart.CFrame = PosMon
                            if v.Humanoid:FindFirstChild("Animator") then
                                v.Humanoid.Animator:Destroy()
                            end
                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                        end
                    end
                end
                elseif _G.AutoBone and BoneMagnet and Magnet then
                if (v.Name == "Peanut Scout [Lv. 2075]" or v.Name == "Peanut President [Lv. 2100]" or v.Name == "Ice Cream Chef [Lv. 2125]" or v.Name == "Ice Cream Commander [Lv. 2150]") and (v.HumanoidRootPart.Position - MainMonBone.Position).Magnitude <= 500 then 
                    if sethiddenproperty then 
                    sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  10000)
                    end
                    v.Head.CanCollide = false
                    v.HumanoidRootPart.CanCollide = false
                    v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
                    v.HumanoidRootPart.CFrame = MainMonBone
                 end
             end
         end
      end)
   end
end)
