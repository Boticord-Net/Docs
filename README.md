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

__

```csharp
using Discord.WebSocket;
using Discord;
using Boticord.Net;
using Boticord.Net.Services;

var botClient = new DiscordSocketClient();
botClient.Ready += BotReady;

var boticordClient = new BoticordClient(new BoticordConfig
{
    Token = "boticord token here"
});

await botClient.LoginAsync(TokenType.Bot, "bot token here");
await botClient.StartAsync();

await Task.Delay(-1);

async Task BotReady()
{
    Console.WriteLine($"Logged into {botClient.CurrentUser}");
    return Task.CompletedTask;
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
