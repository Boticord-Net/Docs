---
description: How to install and start
---

# Quick Start

### _Installation_

#### Package Manager

```
Install-Package Boticord.Net -Version 1.0.1
```

.NET CLI

```
dotnet add package Boticord.Net --version 1.0.1
```

[**Nuget packages**](https://www.nuget.org/packages/Boticord.Net/)****

### _Example usage_

This example uses [Discord.Net](https://github.com/discord-net/Discord.Net) to run discord bot

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
