# Adding a win-condition

Our game wouldn't be particularly interesting if we couldn't win it. Let's make it so that when all coins are picked up we tell the player it has won.

Since we gathered all of our coins inside the `SimGroup` called `Coins` we can check if there's any left after a coin has been picked and if not tell the client they have won.\
Implement this logic in the `onCollision` callback in the file `data/CoinCollection/server/coin.tscript:`

```csharp
function Coin::onCollision(%this, %obj, %col, %vec, %len) {
    %obj.delete();
    if (Coins.getCount() <= 0) {
        commandToClient(%col.client, 'ShowVictory');
    }
}
```

Do you remember that we set the `client` variable on the Player object when we spawned it in [`spawnControlObject`](adding-a-player.md)? We had the line `%player.client = %client` which we can use now to get the client from the player (`%col`) object.

So what's happening here? `if (Coins.getCount() <=0)`, if there are no more coins `commandToClient(%col.client, 'ShowVictory')` instruct the client to show the victory screen. Please read [client-and-server-commands.md](../../../for-programmers/networking/client-and-server-commands.md "mention")for more information about the `commandToClient` system, but the gist of it is we want to call the command `'ShowVictory'` on the `%col.client` client. The `'ShowVictory'` is **not** a regular string, it is a "tag" and writing `"ShowVictory"` instead won't work. Tag's are essentially strings that are stored in a networked  database with an ID such that we don't have to send the full `"ShowVictory"` string to the client but instead can send e.g. `42`.

Now we need to add our first client-side script! Create a file in a new `client`folder called `data/CoinCollection/client/commands.tscript` with the contents:

```csharp
function clientCmdShowVictory()
{
    MessageBoxOK("You Win!",
            "Congratulations you found all the coins!",
            "disconnect();" );
}
```

We indicate that it's a network-command by prefixing it with `clientCmd` and then all it does is it shows a message box and when the player clicks OK we will run `disconnect();` which will end the game.

#### A short note on client vs server scripts

There is no requirement that all server-side scripts are placed in the `server` folder and all client-side scripts are placed in the `client` folder. So why make the distinction?

Well in Torque3D, the server and client are actually completely separate instances so it helps to keep an overview if we split the scripts into different folders as well. If you want to release a multiplayer game in the future, you might want to avoid delivering the server scripts to your players because you don't want them create private servers. In this case you can simply delete the `server`folder before zip'ing and sending the file to your players.

Also, since it's completely separate instances it helps keep an overview of what objects you have created on the server on what objects you created on the client. It's a very common source of mistakes that developers try to access server objects from the client and vice versa.
