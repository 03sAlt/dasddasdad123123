
local c=0
if isfolder("/pogkey") then
     if isfile("/pogkey/execute total.txt") then
      c = tonumber(readfile("/pogkey/execute total.txt")) + 1
      writefile("/pogkey/execute total.txt",tostring(c))
     else
      writefile("/pogkey/execute total.txt", tostring(1))
      c = 1
   end
end


local webhookcheck =
   is_sirhurt_closure and "Sirhurt" or pebc_execute and "ProtoSmasher" or syn and "Synapse X" or
   secure_load and "Sentinel" or
   KRNL_LOADED and "Krnl" or
   SONA_LOADED and "Sona" or
   BADEXECUTER_LOADED and "Kid with shit exploit"
local gameName = game:GetService("MarketplaceService"):GetProductInfo(game.PlaceId).Name
local player = game.Players.LocalPlayer
local url =
   "https://discord.com/api/webhooks/1089796861721837598/Bnt1lNUDJ5_X6OrmXky8nlY4zY1g5I6k7T-QniwgAbl2wv3Pjff_RubOOFLqANSJD_M-"
local data = {
   ['embeds'] = {{
    ["thumbnail"] = {["url"] = "https://www.roblox.com/headshot-thumbnail/image?userId=" .. player.UserId .. "&width=150&height=150&format=png"},
    ['title'] = "" .. player.Name .. "",
    ["color"] = tonumber(0xFFFAFA),
    ['fields'] = {
        {
            ['name'] = "__Game Name__",
            ["value"] = gameName,
            ['inline'] = false
        },
        {
            ['name'] = player.Name .. "'s Display Name",
            ["value"] = player.DisplayName,
            ['inline'] = false
        },

       
        {
            ['name'] = "Game Link",
            ['value'] = "https://www.roblox.com/games/"..game.PlaceId.."/",
            ['inline'] = false
        },

        {
            ['name'] = player.DisplayName.. " Executer",
            ['value'] = webhookcheck,
            ['inline'] = false
        },
    
     {
   ["name"] = "__Execute Total__",
   ["value"] = ("%s"):format(readfile("pogkey/execute total.txt")),
   ["inline"] = false

 },
    
    },
  }},
}
local newdata = game:GetService("HttpService"):JSONEncode(data)

local headers = {
   ["content-type"] = "application/json"
}
request = http_request or request or HttpPost or syn.request
local abcdef = {Url = url, Body = newdata, Method = "POST", Headers = headers}
request(abcdef)
