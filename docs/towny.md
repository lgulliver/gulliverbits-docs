# Towny

## Introduction

Towny is the land protection plugin used on Nations. It allows you to create towns, which you can invite other players to. The owner of a town is called its mayor, whilst the members of a town are called its residents. Nations, which are a political union of multiple towns, can also be formed. Nations can go to war with each other and give their towns multiple benefits.

## Town Creation

### Creating a Town

An example of a town's information.

To create a town, type `/t new <town name>`. This will create a town on the chunk you are standing on. For example, /t new London will create a town called 'London', centered on the chunk you are standing on. This chunk is called your homeblock and you will spawn there if you die.

Once you have created a town, you can view its information by typing `/t <name of your town>`. This displays important information such as:

    Your town's residents and their ranks

    Your town's size - in other words, how many chunks you have claimed and the claim limit

    Your town's outposts and outpost limit

    Your town tax

    Your town bank balance

These will be explained later in this tutorial.

### Inviting Other Players

You can invite other players to your town using `/t add <player name>`. They will need to do `/accept <name of your town>` to join. You can privately talk to players in your town by switching to town chat by typing `/tc`. You can return to general chat by typing `/g`.

### Claiming Land

Your town has a limit on how many chunks (townblocks) it can claim. Each resident increases this limit by 8 chunks. To claim a chunk for your town, type `/t claim`. It must be next to an existing claim. This will deduct $25 from your town bank. To deposit money in your town bank, type `/t deposit <amount>`. You can view chunk borders with `/resident toggle constantplotborder`.

You can also buy additional townblocks with `/t buy bonus <amount of chunks>`. Joining or creating a nation will also increase the townblock limit.

### Outposts

If you need to claim land which is not adjacent to an existing claim, you must create an outpost through `/t claim outpost`. Outposts cost more than regular claims, and your town must be in a nation to create them. You can only have a maximum of two outposts.

### Town Upkeep

Each townblock your town claims will increase your town upkeep by $10. Town upkeep is collected from your town bank every 24 hours in real life. If your town bank does not have enough money to pay the upkeep, it will be disbanded and can be griefed.

## Plot Management

Claimed townblocks/chunks are called plots. Remember that they are simply claimed chunks, so all of them are 16x16 blocks.

### Selling Plots

Plots can be sold and given to your residents. To put a plot for sale, type `/plot forsale <price of the plot>` while standing inside it. By default, the plot price will be set 0. Residents can then buy the plot by typing `/plot claim`. If the plot has a price, the amount paid will go to the town bank.

You can change the default price for newly set-for-sale plots with `/town set plotprice <price>`.

### Plot Permissions

The owner of a plot can control who can access it by typing `/plot set perm <group> <permission> [on/off]` while standing inside it.

Groups are:

    - friend - players on your friend list. You can edit your friend list with /res friend.
    - resident - players from your town.
    - ally - players from your town, nation and allied nations.
    - outsider - players not from your town, nation or an allied nation.

Permissions are:

    - build - controls whether a group can build in your plot
    - destroy - controls whether a group can break blocks in your plot
    - switch - controls whether a group can use chests, hoppers, furnaces, doors, dispensers, etc.
    - itemuse - controls whether a group can place/destroy minecarts, use buckets and bone meal, etc.

For example,`/plot set perm build ally` on would allow players from your town, nation and allied nations to build in the plot you are standing in.

If you want to control permissions for all your owned plots, use `/resident set perm <group> <permission> [on/off]`

Mayors can control permissions for all unowned plots with `/town set perm <group> <permission> [on/off]`.

### Plot Types

Plots can be of different types, which have unique functions. You can change a plot's type by typing `/plot set <plot type>` while standing in it.

    - default - the default plot type. All plots are default when first claimed. Non-default plots can be made default again with `/plot set reset`.
    - shop - designates a player shop area. The plot will appear red on the map.
    - arena - arena plots have PvP and friendly fire enabled at all times.
    - embassy - if for sale, embassy plots can be bought by any player, even if they're not a resident of the town.
    - bank - designates a bank, which allows you to deposit and withdraw from your town and nation banks.
    - jail - designates a jail, where players will be sent to if imprisoned - see the section on ranks.
    - farm - designates a farm, where the only blocks that can be placed and destroyed are crops.
    - wilds - designates a semi-protected wilderness plot, where trees, flowers, mushrooms etc can be broken but all other blocks cannot.

## Town Management

Mayors can control various aspects of their town, including tax rates and rank assignment.
General Commands

    - `/town set name <new name>` - changes your town name.
    - `/town set mayor <player>` - allows you to transfer the mayorship of your town.
    - `/town set board <message>` - sets the town board, which is seen on the scoreboard and by players when logging in.
    - `/town set homeblock` - sets the homeblock of your town. Typing /town set spawn in a homeblock changes your town respawn point to where you are standing.
    - `/town set tag <tag>` - sets your town tag, which will be shown in chat instead of your full town name.

### Ranks

Mayors can assign ranks to residents to aid them in administrating their town with /t rank add <player> <rank name>.

    - comayor - has all the permissions of a mayor (including the ability to delete a town!). Give this rank with caution.
    - assistant - has the ability to invite and kick residents, manage plots they don't own, claim land and jail residents.
    - police - has the ability to designate outlaws (explained later in this tutorial) and jail residents through /town toggle jail <player>. Keep in mind you need to set a jail plot - for the jail command to work.
    - builder - can build in any plot, even if they don't own it.
    - planner - has full access to plot management commands.
    - treasurer - has full control over taxes (explained later in this tutorial) and can withdraw from the town bank.

### Taxation

Mayors and treasurers can set taxes to extract money from residents. They are collected every 24 hours in real-life and are automatically deposited in the town bank.

There are two modes of taxation. The default mode of taxation, flat taxes, takes a set amount of money from residents each day. If a resident cannot afford to pay the tax, they will be kicked from the town. The other mode of taxation, percentage taxes, takes a percentage of residents' money each day. If a resident is unable to pay a percentage tax, they will not 'be kicked from the town.

The percentage and flat tax can be set through `/town set taxes <amount/percentage>`. To switch between the two modes of taxation, type `/town toggle taxpercent`.

The following commands allow you to set taxes for different plot types:

    - `/town set plottax <amount>` – Set taxes collected from each resident daily, per plot that they own.
    - `/town set shoptax <amount>` – Set taxes collected from each resident daily, per shop plot that they own.
    - `/town set embassytax <amount>` – Set taxes collected from each resident daily, per embassy plot that they own.

### Outlaws and Jails

Mayors and police can jail and unjail residents by typing `/town toggle jail <player>`. Jailed residents will be sent to a jail plot if one exists. They cannot teleport and will return to the jail if they die. However, they can leave by escaping the jail plot and walking out of the town, or by paying a $10,000 bail to the town bank through the command `/resident jail paybail`.

Outlaws are players who can be attacked in a town even if it has PvP disabled. If an outlaw dies inside your town, they will automatically be jailed. You can manage outlaws through the command `/town outlaw <add/remove> <player>`. You can see the list of outlaws through `/town outlawlist`.

## Nations

Towns can form nations. Nations are political entities which multiple towns can be part of. Joining or creating a nation gives towns multiple benefits, including:

    - The ability to wage war against other nations.
    - The ability to claim outposts.
    - Bonus townblocks - the larger the nation, the larger the bonus.

### Nation Creation

If a town has more than $20,000 in its bank, its mayor can create a nation by typing `/n new <nation name>`. For example, typing `/n new USA` will create a nation called 'USA' and will take $20,000 from your town bank. The founding town will become the nation capital, and its mayor will become the nation leader ('king').

### Inviting Towns to Nations

You can invite other towns to your nation by typing `/n add <town name>`. The mayor of the town will be sent a message informing him of the invite and how to accept it. A town must be within 300 chunks of the nation capital's homeblock to be invited.

You can privately talk with players in your nation by typing `/nc` to switch to nation chat. You can return to general chat by typing `/g`.

### Nation Upkeep and Taxation

Nations have a daily upkeep of $1,000 which is taken from the nation bank. You can deposit nation

You can set taxes on your nation's towns by typing `/n set taxes <tax amount>`. Like town taxes, nation taxes are taken every 24 hours in real life and are deposited in the nation bank.

### General Nation Commands

    - `/nation set title <player> <title goes here>` - grants a nation member a title which will appear before their name in chat.
    - `/nation set surname <player> <surname goes here>` - grants a nation member a surname which will appear after their name in chat.
    - `/nation set name <new name>` - changes the nation name.
    - `/nation set capital <town>` - changes the nation's capital city and transfers nation leadership to its mayor.
    - `/nation set king <player>` - transfers nation leadership to a player in your nation.
    - `/nation set tag <tag>` - sets your nation tag, which will be shown in chat instead of your full nation name.

### Nation Ranks

Nation leaders can assign ranks to nation members. This can be done by typing `/n rank add <player> <rank name>`. Like town ranks, these give the rank holder special privileges.  

    - coleader - has all the abilities of the nation leader, including the ability to delete the nation! Give with caution.
    - chancellor - can manage nation allies and enemies, invite and kick towns, grant titles and surnames and withdraw from the nation bank.
    - treasurer - can change the tax rate and withdraw from the town bank.