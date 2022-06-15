# Quick Start

#### _Installation_

_`coming soon..`_

#### _Examples_

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
