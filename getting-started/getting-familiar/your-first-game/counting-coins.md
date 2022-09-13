# Counting coins

If we want the game to be a bit competitive, we need a scoring system. In a coin collection game, it makes sense that whoever picks up the most coins wins. Let's count how many coins we have picked up!

In `data/CoinCollection/server/coin.tscript` first add a global variable that counts the number of coins we've found at the top of the file:

```csharp
$CoinsFound = 0;
```

And then increment that number in the `onCollision` callback:

```csharp
function Coin::onCollision(%this, %obj, %col, %vec, %len) {
    %obj.delete();

    $CoinsFound++;
    if (Coins.getCount() <= 0) {
        commandToClient(%col.client, 'ShowVictory');
    }
}
```

And finally edit `data/CoinCollection/client/commands.tscript` to show the number of coins found in the message box using the `$CoinsFound` global:

```csharp
function clientCmdShowVictory()
{
    MessageBoxOK("You Win!",
            "Congratulation you found" SPC $CoinsFound SPC "coins!",
            "disconnect();" );
}
```

