
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Skywars GUİ", "Sentinel") 
local Main = Window:NewTab("Scriptler")
local MainSection = Main:NewSection("Scriptler")
MainSection:NewButton("SkyFu", "Bunla havada yürüye bilirsiniz ", function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/xQuest13/skyfu/main/README.md", true))()
end)
MainSection:NewButton("Free Vips", "Bedavaya Vips", function()
	AdriPart = game.workspace.Lobby["Mega VIP Room"].Teleport.Enter["Teleporter B"]
	AdriPart:Clone().Parent = game.workspace.Lobby["Mega VIP Room"].Teleport.Enter
	game.workspace.Lobby["Mega VIP Room"].Teleport.Enter["Teleporter B"]:Destroy()
	wait()
	game.workspace.Lobby["Mega VIP Room"].Teleport.Enter["Teleporter B"].Touched:Connect(function(hit)
		local player = game.Players:GetPlayerFromCharacter(hit.Parent)
		player.Character.HumanoidRootPart.CFrame = CFrame.new(-1.06104672, 264, 72.2138901)
	end)

	AdriPart2 = game:GetService("Workspace").Lobby["VIP Room"].Teleport.Enter["Teleporter A"]
	AdriPart2:Clone().Parent = game:GetService("Workspace").Lobby["VIP Room"].Teleport.Enter
	game:GetService("Workspace").Lobby["VIP Room"].Teleport.Enter["Teleporter A"]:Destroy()
	wait()
	game:GetService("Workspace").Lobby["VIP Room"].Teleport.Enter["Teleporter A"].Touched:Connect(function(hit)
		local player = game.Players:GetPlayerFromCharacter(hit.Parent)
		player.Character.HumanoidRootPart.CFrame = CFrame.new(0.324219227, 264, -69.9828949)
	end)  
	venyx:Notify("Enabled", "FreeVipsRooms")
end)
MainSection:NewButton("NoCollideBlocks", "Blockların Kolizyonunu  kapatir", function()
	local Why = game:GetService("Players").LocalPlayer
	local Char = Why.Character
	local backpack = Why.Backpack

	backpack.Block.Parent =  Why.Character
	Char.Block.Left:Destroy()
	Char.Block.Parent = Why.Backpack
end)
MainSection:NewButton("Fake Axe ", "Görünmeyen kazma", function()
	local Players       = game:GetService("Players")
	local localPlayer   = Players.LocalPlayer
	local backpack      = localPlayer:WaitForChild("Backpack")
	local tool          = Instance.new("Tool")
	tool.RequiresHandle = false
	tool.CanBeDropped   = true
	tool.Parent         = backpack
	tool.Name           = "FakeAxe"
	tool.Equipped:Connect(function(mouse)
		mouse.Button1Down:Connect(function()
			if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Block") then
				if mouse.Target and mouse.Target.Parent then
					local Adrix = {
						[1] = mouse.Target
					}

					game:GetService("Players").LocalPlayer.Backpack.Axe.RemoteEvent:FireServer(unpack(Adrix))  
				end
			end
		end)
	end)
end)
MainSection:NewButton("Fake Block", "Görünmeyen blok", function()
	local Players       = game:GetService("Players")
	local localPlayer   = Players.LocalPlayer
	local backpack      = localPlayer:WaitForChild("Backpack")
	local tool          = Instance.new("Tool")
	tool.RequiresHandle = false
	tool.CanBeDropped   = true
	tool.Parent         = backpack
	tool.Name           = "FakeBlock"
	tool.Equipped:Connect(function(mouse)
		mouse.Button1Down:Connect(function()
			if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Block") then
				if mouse.Target and mouse.Target.Parent then
					game:GetService("Players").LocalPlayer.Backpack.Block.RemoteEvent:FireServer(mouse.Target,Enum.NormalId.Right)
					game:GetService("Players").LocalPlayer.Backpack.Block.RemoteEvent:FireServer(mouse.Target,Enum.NormalId.Left)
					game:GetService("Players").LocalPlayer.Backpack.Block.RemoteEvent:FireServer(mouse.Target,Enum.NormalId.Back)
					game:GetService("Players").LocalPlayer.Backpack.Block.RemoteEvent:FireServer(mouse.Target,Enum.NormalId.Front)
				end
			end
		end)
	end)
end)
MainSection:NewButton("AntiRoundFinishKill", "Round bitince ölmüyorsunuz", function()
	if game:GetService("Workspace").Terrain:FindFirstChild("Seat")==nil then
		ct    = {}
		game.StarterGui:SetCore("SendNotification", {Title = "Enabled"; Text = ""; Duration = 3;})    
		sound = Instance.new("Seat", game:GetService("Workspace").Terrain)
		table.insert(ct,game:GetService("RunService").Stepped:Connect(function()
			if game:GetService("Workspace").timer.Value < 1 or game:GetService("Workspace").plrsLeft.Value < 2 then
				game.StarterGui:SetCore("SendNotification", {
					Title    = "round finished"; 
					Text     = ""; 
					Duration = 3;
				})         
				for i,v in pairs(ct) do v:Disconnect() end
				sound:Destroy()
				wait(2.3)
				game:GetService('Players').LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-8, 268, 6)
				for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
					if v:IsA("Tool") then
						v.Parent = game.Players.LocalPlayer.Character
					end
				end
			end
		end))
	else
		game.StarterGui:SetCore("SendNotification", {Title = "Really Executed"; Text = ""; Duration = 3;})    
	end
end)
MainSection:NewButton("Fling all rounds", "Her rounda adamları ucurma", function()
	local Adrix        = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
	wait(0.01)
	ZZ = game:GetService('RunService').Stepped:connect(function()
		for i,v in pairs(game:GetService("Players").LocalPlayer.Character:GetChildren()) do
			if v:IsA("BasePart") then 
				v.CanCollide = false
			end
		end
	end)
	local BG = Instance.new('BodyGyro', game:GetService("Players").LocalPlayer.Character.Torso)
	local BV     = Instance.new('BodyVelocity', game:GetService("Players").LocalPlayer.Character.Torso)
	BG.P         = 9e4
	BG.maxTorque = Vector3.new(9e9, 9e9, 9e9)
	BG.cframe    = game:GetService("Players").LocalPlayer.Character.Torso.CFrame
	BV.velocity  = Vector3.new(0, 3.75, 0)
	BV.maxForce  = Vector3.new(9e9, 9e9, 9e9)
	wait()
	NoLol = game:GetService('RunService').Heartbeat:connect(function()
		for i,v in next, game:GetService("Players").LocalPlayer.Character:GetDescendants() do
			if v:IsA("BasePart") and v.Name ~="Torso" then 
				v.Velocity = Vector3.new(0,-2333333,0)
			end
		end
	end)
	XD = game:GetService("Players").LocalPlayer

	for i,v in pairs(game:GetService("Players"):GetPlayers()) do
		if v.Name ~= XD.Name then
			if v.Character:FindFirstChild('Role') and v.Character:FindFirstChild('Torso') then
				wait(0.1)
				XD.Character:FindFirstChild('HumanoidRootPart').CFrame = v.Character:FindFirstChild('HumanoidRootPart').CFrame + Vector3.new(0,-3.9,0)
				wait(0.1)
				XD.Character:FindFirstChild('HumanoidRootPart').CFrame = v.Character:FindFirstChild('HumanoidRootPart').CFrame + Vector3.new(0,4,0)
				wait(0.1)
			end 
		end    
	end
	wait(0.2)
	ZZ:Disconnect()

	NoLol:Disconnect()
	wait(0.1)
	BG:Destroy()
	BV:Destroy()
	game.Players.LocalPlayer.Character:FindFirstChild('HumanoidRootPart').CFrame = Adrix
	game.Players.LocalPlayer.Character:FindFirstChild('Humanoid').PlatformStand = true
	wait()
	game.Players.LocalPlayer.Character:FindFirstChild('Humanoid').PlatformStand = false
end)
MainSection:NewButton("Auto farm", "1 saniyede mademleri kırar", function()
	game.Players.LocalPlayer.Character.Humanoid:UnequipTools()
	if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Axe") then
		local Adrix = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
		game.Players.LocalPlayer.Character.Humanoid:UnequipTools()
		game.Players.LocalPlayer.Backpack["Axe"].Parent = game:GetService("Players").LocalPlayer


		local BG = Instance.new('BodyGyro', game:GetService("Players").LocalPlayer.Character.Torso)
		local BV     = Instance.new('BodyVelocity', game:GetService("Players").LocalPlayer.Character.Torso)
		BG.P         = 9e4
		BG.maxTorque = Vector3.new(9e9, 9e9, 9e9)
		BG.cframe    = game:GetService("Players").LocalPlayer.Character.Torso.CFrame
		BV.velocity  = Vector3.new(0, 0, 0)
		BV.maxForce  = Vector3.new(9e9, 9e9, 9e9)

		function onTouched(part)       
			local h = part
			if h.Name == "Block" and h.Parent.Name == "Ores" then
				game.Players.LocalPlayer["Axe"].RemoteEvent:FireServer(h)  
			end
		end

		function AdriIsABaby()
			Partz              = Instance.new("Part")
			Partz.Parent       = workspace
			Partz.Transparency = 1
			Partz.CanCollide   = false
			Partz.Massless     = true
			Partz.Position     = game.Players.LocalPlayer.Character.Head.Position
			Partz.Size         = Vector3.new(34,38,34)

			local bruh = Partz.Touched:connect(onTouched)
			wait()
			bruh:Disconnect()
			Partz:Destroy()
		end

		function ban()
			AdriIsABaby()
		end
		game:GetService('Players').LocalPlayer.Character.Humanoid.CameraOffset = Vector3.new(0,10,0)
		function Time()
			wait(0.0019)  
		end
		ct = {}
		for i,v in pairs(game:GetService("Players").LocalPlayer.Character:GetChildren()) do
			if v:IsA("BasePart") then 
				table.insert(ct,game:GetService('RunService').Stepped:connect(function()
					v.CanCollide = false
				end))
			end
		end
		local plr = game.Players.LocalPlayer

		function ah()
			BG:Destroy()
			BV:Destroy()
			plr.Character.Humanoid.PlatformStand = false
			for i,v in pairs(ct) do v:Disconnect() end
		end

		for i,v in next,workspace:GetDescendants() do
			if v.Name == "Block" and v.Parent.Name == "Ores" then
				plr.Character.Humanoid.PlatformStand = true
				repeat
					Time()
					ban()
					plr.Character.HumanoidRootPart.CFrame = v.CFrame + Vector3.new(0,1,0)
				until v.Name ~= "Block" or not plr:FindFirstChild("Axe") 
				Time()
			end
		end


		plr:FindFirstChild("Axe").Parent = plr.Backpack
		game.StarterGui:SetCore("SendNotification", {
			Title    = "No blocks in game.."; 
			Text     = ""; 
			Duration = 3;
		})  
		ah()
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Adrix
		game:GetService('Players').LocalPlayer.Character.Humanoid.CameraOffset = Vector3.new(0,0,0)
		plr:FindFirstChild("Axe").Parent = plr.Backpack
		---
	else
		game.StarterGui:SetCore("SendNotification", {
			Title    = "Ok.";
			Text     = "";
			Duration = 0.5;
		})
	end
end)
MainSection:NewButton("toxic", "Chat trolleme", function()
	game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer("kürt ","All")
	game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer("totalin 0 ","All")
	game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer("Sen amk","All")
	game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer("nub","All")
	game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer("Hala 31 Cekiliyor","All")
end)
MainSection:NewButton("Rejoin server", "Servere bidaha girmek", function()
	local ts = game:GetService("TeleportService")
	local p = game:GetService("Players").LocalPlayer
	ts:Teleport(game.PlaceId, p)
end)
MainSection:NewButton("Hat spin", "Hatlar dönüyo", function()
	local plr = game.Players.LocalPlayer;
	local chr = plr.Character;
	local hum = chr.Humanoid;
	local mov = {};
	local mov2 = {};

	--sub to me_ozoneYT

	for i,v in next, game:GetService("Players").LocalPlayer.Character:GetDescendants() do
		if v:IsA("BasePart") and v.Name ~="HumanoidRootPart" then 
			game:GetService("RunService").Heartbeat:connect(function()
				v.Velocity = Vector3.new(0,300,0)
			end)
		end
	end


	function ftp(str)
		local pt = {};
		if str ~= 'me' and str ~= 'random' then
			for i, v in pairs(game.Players:GetPlayers()) do
				if v.Name:lower():find(str:lower()) then
					table.insert(pt, v);
				end
			end
		elseif str == 'me' then
			table.insert(pt, plr);
		elseif str == 'random' then
			table.insert(pt, game.Players:GetPlayers()[math.random(1, #game.Players:GetPlayers())]);
		end
		return pt;
	end

	for _, v in pairs(hum:GetAccessories()) do
		local b = v.Handle;
		b.CustomPhysicalProperties = PhysicalProperties.new(0, 0, 0, 0, 0);
		b.CanCollide = false;
		b:BreakJoints();
		for _, k in pairs(v:GetChildren()) do
			if not k:IsA'SpecialMesh' and not k:IsA'Part' then
				k:Destroy();
			end
		end
		local still = Instance.new('BodyAngularVelocity', b);
		still.MaxTorque = Vector3.new(math.huge, math.huge, math.huge);
		still.AngularVelocity = Vector3.new(0, 0, 0);
		local align = Instance.new('AlignPosition', b);
		align.MaxForce = 1000000;
		align.MaxVelocity = math.huge;
		align.RigidityEnabled = false;
		align.ApplyAtCenterOfMass = true;
		align.Responsiveness = 200;
		local a0 = Instance.new('Attachment', b);
		local a1 = Instance.new('Attachment', chr.Head);
		align.Attachment0 = a0;
		align.Attachment1 = a1;
		table.insert(mov, a1);
		table.insert(mov2, still);
	end

	local par = {};
	for _, v in pairs(mov) do
		local parr = Instance.new('Part', workspace);
		parr.Anchored = true;
		parr.Size = Vector3.new(1, 1, 1);
		parr.Transparency = 1;
		parr.CanCollide = false;
		table.insert(par, parr);
	end

	local rotx = 0;
	local rotz = math.pi / 2;
	local height = 0;
	local heighti = 1;
	local offset = 10;
	local speed = 10;
	local mode = 4;
	local angular = Vector3.new(0, 0, 0);
	local l = 1;
	game['Run Service'].RenderStepped:Connect(function()
		rotx = rotx + speed / 100;
		rotz = rotz + speed / 100;
		l = (l >= 360 and 1 or l + speed);

		for i, v in pairs(par) do
			v.CFrame = CFrame.new(chr.HumanoidRootPart.Position) * CFrame.fromEulerAnglesXYZ(0, math.rad(l + (360 / #par) * i + speed), 0) * CFrame.new(offset, 0, 0);
		end

		if heighti == 1 then
			height = height + speed / 100;
		elseif heighti == 2 then
			height = height - speed / 100;
		end
		if height > 2 then
			heighti = 2;
		end
		if height < -1 then
			heighti = 1;
		end

		if mode == 1 then
			for _, v in pairs(mov) do
				v.Position = Vector3.new(math.sin(rotx) * offset, 0, math.sin(rotz) * offset);
			end
		elseif mode == 2 then
			for _, v in pairs(mov) do
				v.Position = Vector3.new(offset, height, offset);
			end
		elseif mode == 3 then
			for _, v in pairs(mov) do
				v.Position = Vector3.new(math.sin(rotx) * offset, height, math.sin(rotz) * offset);
			end
		elseif mode == 4 then
			for i, v in pairs(mov) do
				v.Position = Vector3.new(chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).X, chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).Y, chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).Z);
			end
		elseif mode == 5 then
			for i, v in pairs(mov) do
				v.Position = Vector3.new((math.sin(rotx)) * offset, height, (math.cos(rotz) - i) * offset);
			end
		elseif mode == 6 then
			for i, v in pairs(mov) do
				v.Position = Vector3.new((math.sin(rotx)) * offset, height, (math.tan(rotz) - i) * offset);
			end
		elseif mode == 7 then
			for i, v in pairs(mov) do
				v.Position = Vector3.new(math.cos(rotx * i) * offset, 0, math.cos(rotz * i) * offset);
			end
		elseif mode == 8 then
			for i, v in pairs(mov) do
				v.Position = Vector3.new(math.sin(rotx) * i * offset, 0, math.sin(rotz) * i * offset);
			end
		elseif mode == 9 then
			pcall(function()
				local so = nil;
				for k, b in pairs(chr:GetChildren()) do
					if b:IsA'Tool' then
						for h, j in pairs(b:GetDescendants()) do
							if j:IsA'Sound' then
								so = j;
							end
						end
					end
				end
				if so ~= nil then
					offset = so.PlaybackLoudness / 35;
					speed = so.PlaybackLoudness / 500;
					angular = Vector3.new(0, so.PlaybackLoudness / 75, 0);
				end
			end)
			for i, v in pairs(mov) do
				v.Position = Vector3.new(chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).X, chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).Y, chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).Z);
			end
		elseif mode == 10 then
			offset = height * 15;
			for i, v in pairs(mov) do
				v.Position = Vector3.new(chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).X, chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).Y, chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).Z);
			end
		elseif mode == 11 then
			for i, v in pairs(mov) do
				v.Position = Vector3.new(chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(plr:GetMouse().Hit.p)).X, chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(plr:GetMouse().Hit.p)).Y, chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(plr:GetMouse().Hit.p)).Z) + Vector3.new(chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).X, chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).Y, chr.HumanoidRootPart.CFrame:ToObjectSpace(CFrame.new(par[i].Position)).Z);
			end
		end
		for _, v in pairs(mov2) do
			v.AngularVelocity = angular;
		end
	end)
	game.Players.LocalPlayer.Chatted:Connect(function(c)
		if c:split(' ')[1] == '/o' then
			for _, v in pairs(mov) do
				chr = ftp(c:split(' ')[2])[1].Character;
				v.Parent = ftp(c:split(' ')[2])[1].Character.HumanoidRootPart;
			end
		end
		if c:split(' ')[1] == '/s' then --speed
			speed = tonumber(c:split(' ')[2]);
		end
		if c:split(' ')[1] == '/m' then --mode
			mode = tonumber(c:split(' ')[2]);
		end
		if c:split(' ')[1] == '/' then --offset big small
			offset = tonumber(c:split(' ')[2]);
		end
		if c:split(' ')[1] == '/a' then --angular angle
			angular = Vector3.new(tonumber(c:split(' ')[2]), tonumber(c:split(' ')[3]), tonumber(c:split(' ')[4]));
		end
	end)
end)
MainSection:NewButton("HealthNotification", "Canınızı gösterir", function()
	local z = game.Players.LocalPlayer.Character.Humanoid


	game.StarterGui:SetCore("SendNotification", {
		Title    = "YourHealth is: "..z.Health; 
		Text     = "MaxHealth: "..z.MaxHealth; 
		Duration = 3;
	})  
end)
-- LOCAL PLAYER
local Main = Window:NewTab("Local Player")
local MainSection = Main:NewSection("Local player script")
MainSection:NewKeybind("Wall block", "Önüne block koyması", Enum.KeyCode.F, function()
	function onTouched(part)       
		local h = part
		if h.Name == "Block" then
			game:GetService("Players").LocalPlayer.Backpack.Block.RemoteEvent:FireServer(h,Enum.NormalId.Top)
		end
	end
	Partz              = Instance.new("Part")
	Partz.Parent       = workspace
	Partz.Transparency = 1
	Partz.CanCollide   = false
	Partz.Massless     = true
	Partz.Position     = game.Players.LocalPlayer.Character.HumanoidRootPart.Position + Vector3.new(0,51,0)
	Partz.Size         = Vector3.new(8,27,1)
	Partz.CFrame       = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame + game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.lookVector*3.5

	local light         = Instance.new("SelectionBox")
	light.Adornee       = Partz
	light.LineThickness = 0.05
	light.Color3        = Color3.fromRGB(17, 17, 257)
	light.Parent        = Partz
	light.Name          = "SelectBox"



	local bruh = Partz.Touched:connect(onTouched)
	wait()
	bruh:Disconnect()
	Partz:Destroy()
end)

MainSection:NewSlider("Speed walk ", "speed ayari", 500, 16, function(s) -- 500 (MaxValue) | 0 (MinValue)
	game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
end)

MainSection:NewSlider("Jump Power", "SliderInfo", 500, 0, function(s) -- 500 (MaxValue) | 0 (MinValue)
	game.Players.LocalPlayer.Character.Humanoid.JumpPower = s
end)

MainSection:NewButton("Hitbox", "Hitbox scirpti", function()
	loadstring(game:HttpGet('https://raw.githubusercontent.com/2dgeneralspam1/scripts-and-stuff/master/shit%20script%20pack/CheatX'))()
end)

MainSection:NewButton("Force Field ", "200 Coine  force field alınca calışır", function()
	local Why      = game:GetService("Players").LocalPlayer
	local Char     = Why.Character
	local backpack = Why.Backpack

	Char.Humanoid:UnequipTools()
	wait()
	for i,v in next, backpack:GetDescendants() do
		if v:IsA("Tool") and v.Name =="Shield" then
			v.GripPos         = Vector3.new(0,10000,0)
			v.Handle.Massless = true
			v.Parent          = Char
			v:Activate()
			v.ShieldPotion:Destroy()
			v:Destroy()
		end
	end
end)

MainSection:NewButton("Rtx", "grafikleri düzenliyo", function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/xQuest13/rtx/main/README.md", true))()
end)

MainSection:NewButton("under mine aura", "Blcokları kırıyo", function()
	while true do
		function onTouched(part)       
			local h = part
			if h.Name == "Block" then
				game:GetService("Players").LocalPlayer.Backpack.Axe.RemoteEvent:FireServer(h)  
			end
		end
		Partz              = Instance.new("Part")
		Partz.Parent       = workspace
		Partz.Transparency = 1
		Partz.CanCollide   = false
		Partz.Massless     = true
		Partz.Position     = game.Players.LocalPlayer.Character.HumanoidRootPart.Position + Vector3.new(0,9,0)
		Partz.Size         = Vector3.new(15,20,15)

		local light         = Instance.new("SelectionBox")
		light.Adornee       = Partz
		light.LineThickness = 0.05
		light.Color3        = Color3.fromRGB(0, 255, 0)
		light.Parent        = Partz
		light.Name          = "SelectBox"

		local bruh = Partz.Touched:connect(onTouched)

		wait()
		bruh:Disconnect()
		Partz:Destroy()
		wait()

	end
end)
