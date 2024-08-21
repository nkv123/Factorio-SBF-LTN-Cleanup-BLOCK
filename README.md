# Factorio-SBF-LTN-Cleanup-BLOCK
Requires mod https://mods.factorio.com/mod/ltn-cleanup
Optional mods:
 * (is in blueprint, you will have an unknown entity when importing the BP:  logistic-train-stop-announcer, can be ignored if you want) https://mods.factorio.com/mod/glutenfree-ltn-announcer 
 * (is just cool to see what train wants to pick up on locomotive) https://mods.factorio.com/mod/glutenfree-ltn-thought-bubble
 
adapted from https://www.factorio.school/view/-NbhhuOwP1MxqyfjzOqH

in setting> mod setting > map > enable cleanup deliveries so trains will try to dump stuff on clean up stations.

Works for any solid item; If connected with logic network of a mall bots will deliver unwanted exess items;  Usefull to get rid of unwanted ores in mall storage or when removing a block and ore gets into the mall storage.
This is a solution for that problem, ... hopefully better than setting each train to a destination when with cargo in LTN Depot manually.
On north or south side add/leave a Construction station or just roboports of a station to connect logistic networks of left and right side.

2 CLEANUP LOADER work with LTN networks 255,4096 and 16. Network 16 for delivery to a requster station (that can be setup anywhere with brians trains book) if you want a item out of the CLEANUP LOADER storage only. It fills items a bit slower than usual in last cargo wagon first regadles of train size 2 - 11. CLEANUP LOADER works as a provider for any item in its storage with priority of 100 so trains will do their best to clear items in CLEANUP LOADER storage. 
A negative thing It can fill worng item into the train if a inseter hand hangs from previous delivery, so that train will visit the cleanup station after failed delivery that misstake which is a extra train ride is better than a train cloged in LTN depot, system will work it self out.

Each of 8 cleanup stations cleanup station has a constant combinator hooked to 48 buffer boxes. constant combinator sets up to 5 differnt item requests for buffer boxes on that cleanup station only. so you can request (8x5) 40 different items from mall at one time.
Each Buffer box will request items from mall connected via logistic bots so there is no need to ask for a big number of items from connected mall best stack size signal (for example 50 iron ore on constant combinator is a request for 48x50 iron ore which is 2400 iron ore from the mall bots go crazy). I recomend not to have more than 2k logistic bots in mall. my fast solution is https://mods.factorio.com/mod/robot-recall.
Each cleanup station constant combinator programed to request 50 iron ore, 50 copper ore, 50 uranium ore to be delivered with bots at the time of blueprint placement.

For automatic build best way is:
1. Place rail block 1x1 blueprint
2. Place construction on blueprint
3. add rail signals at start and end of added track
4. Place general contruction station from brian city book>construction.
5. turn it on
