---
description: This is documention for wrapper for Boticord API.
cover: .gitbook/assets/logo.png
coverY: 0
---

# Docs Boticord.Net

### • Helpful links

[<mark style="color:blue;">GitHub</mark>](https://github.com/boticord)<mark style="color:blue;"></mark>

<mark style="color:blue;"></mark>[<mark style="color:blue;">BotiCord</mark>](https://boticord.top/)

<mark style="color:blue;"></mark>[<mark style="color:blue;">BotiCord Support</mark>](https://discord.com/invite/hkHjW8a)

### • Quickstart

#### _Installation_

_`coming soon..`_

#### _Examples_

# This example uses Discord.Net to run discord bot
__

```csharp
using System.Runtime.InteropServices.ComTypes;
using Discord.WebSocket;
using Discord;
using Boticord.Net;


var boticordClient = new BoticordClient(new BoticordConfig
{
    Token = "boticord token here"
});

var botClient = new DiscordSocketClient();
botClient.Ready += BotReady;
botClient.Log += BotLog;

await botClient.LoginAsync(TokenType.Bot, "bot token here");
await botClient.StartAsync();

await Task.Delay(-1);

async Task BotReady()
{
    Console.WriteLine($"Logged into {botClient.CurrentUser}");

    _ = Task.Run(() => AutoUpdateBotStatus());

}

async Task AutoUpdateBotStatus()
{
    var timer = new PeriodicTimer(TimeSpan.FromMinutes(1));

    while (true)
    {
        await boticordClient.SendBotStatsAsync((uint)botClient.Guilds.Count,
            users: (uint)botClient.Guilds.Select(x => x.MemberCount).Sum());
        await timer.WaitForNextTickAsync();
    }
}

async Task BotLog(LogMessage message)
{
    Console.WriteLine(message.Message);
}
```

### • Api Reference

#### _Client API Reference_

coming soon...

#### _Models API Reference_

coming soon...

#### _Exceptions API Reference_

coming soon...

{% content-ref url="reference/api-reference.md" %}
[api-reference.md](reference/api-reference.md)
{% endcontent-ref %}
