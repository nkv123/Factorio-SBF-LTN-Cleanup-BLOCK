# Factorio-SBF-LTN-Cleanup-BLOCK
Requires mod https://mods.factorio.com/mod/ltn-cleanup
Optional mods:
 * (is in blueprint, you will have an unknown entity when importing the BP:  logistic-train-stop-announcer, can be ignored if you want) https://mods.factorio.com/mod/glutenfree-ltn-announcer 
 * (is just cool to see what train wants to pick up on locomotive) https://mods.factorio.com/mod/glutenfree-ltn-thought-bubble
 
adapted from https://www.factorio.school/view/-NbhhuOwP1MxqyfjzOqH

in setting> mod setting > map > enable cleanup deliveries so trains will try to dump stuff on clean up stations.

Works for any solid item; If connected with logic network of a mall via roboports bots will deliver unwanted or exess items to buffer chests;  Usefull to get rid of unwanted ores in mall storage or when removing a block and ore gets into the mall storage.
This is a solution for that problem, ... hopefully better than setting each train to a destination when with cargo in LTN Depot manually.
On north or south side add/leave a Construction station or just roboports of a station to connect logistic networks of left and right side.

2 CLEANUP LOADER work with LTN networks 255 and 16. Network 16 for delivery to a requster station (named Something @ Red Mall). CLEANUP LOADER fills items a bit slower than usual stations in last cargo wagon first regadles of train size 2 - 11. CLEANUP LOADER works as a LTN provider for any item in its storage with priority of 100 so trains will do their best to clear items in CLEANUP LOADER storage. There is a negative thing, it can fill wrong item into the train if a inserter hand hangs from previous delivery, this has been recified with 1 stack filter inserter that blacklists given signal from memory cell, which take out any wrong item, and do not take items out when train is leaving.
No more extra train ride.
No more cargo flickering.
Each CLEANUP LOADER has constant combinator that is emiting signals of items so that Something @ Red Mall station should ignore (its configured to ignore coal,stone,iron ore,copper ore, uranium ore since we do not want ores back in the mall, so that other station in network 255 pick those up). Any other signal can be given to constant combinator to be ignored. Rest of the inventory is transmitted via channel 5 to wire network to station Something @ Red Mall.

Each of 8 cleanup stations cleanup station has a constant combinator hooked to 48 buffer boxes. constant combinator sets up to 5 differnt item requests for buffer boxes on that cleanup station only. so you can request (8x5) 40 different items from mall at one time.
Each Buffer box will request items from mall connected via logistic bots so there is no need to ask for a big number of items from connected mall best stack size signal (for example 50 iron ore on constant combinator is a request for 48x50 iron ore which is 2400 iron ore from the mall bots go crazy). I recomend not to have more than 2k logistic bots in mall. my fast solution is https://mods.factorio.com/mod/robot-recall.
Each cleanup station constant combinator is already programmed to request 50 iron ore, 50 copper ore, 50 uranium ore to be delivered with bots at the time of blueprint placement.

Some rewiring has been done on CLEANUP LOADER stations, best to rebuild them.

Something @ Red Mall station is configured to extract items from cleanup station that are not ignored with a constant combinator on each of the CLEANUP LOADER stations. 
It does so with <LCCL> train one item type at a time in order of crafting list (to see crafting list press E). 
It has 2 constant combinators not included in requster station:
    first is off combinator located near constant combinator that has signals for LTN. If its on station is offline.
    Second is reset combinator located on the other side of rail from off and signal combinators. if its on it will reset memory cell for current request. After reset turn it off to enable normal operation. 
For me best place for this station is before recycle station at mall. 
When last of item type is extracted from CLEANUP LOADERS, in case of multiple Cleanup Extactor stations it will show an error on with LTN to the console "some item can not be found in network 10f". this message can be ignored.
This station can be placed in any/every mall and renamed as you wish.


For automatic build best way is:
1. Place rail block 1x1 blueprint
2. Place construction on blueprint
3. add rail signals at start and end of added track
4. Place general contruction station from brian city book>construction.
5. turn it on
6. add Something @ Red Mall station to a Red Mall, be sure to connect green and red wires of all big power poles at station to the wire network.
7. add Something @ Blue Mall station to a Blue Mall, be sure to connect green and red wires of all big power poles at station to the wire network.
