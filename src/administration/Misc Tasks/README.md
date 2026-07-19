# Other tasks

Here are various how-tos for specific things you may wish to do, that don't fit into other categories. 


## Scaling the size of an entity's sprite

- Open the VV window for the entity,
- Go to the 'Client Components' tab,
- Scroll down or search for the `SpriteComponent` component. Click on it,
- Scroll down the new window to find `Scale` (capital S) line, with two input boxes for X (horizontal) and Y (vertical) scale,
- Update the numbers as you wish,
- Note that these are multipliers, a scale of `2` will make it twice as wide as default,
- Note that this does not impact the collisions hitbox. 


## Editing movement speed

- While hovering over the target mob you wish to change the speed of, hit ALT + V to open view variables (right clicking a mob to open VV will work too).
- Click on the Server Components tab, and either search for or scroll down to find the MovementSpeedModifier component. Click on it.
- As sprinting is the default mode of movement, edit the BaseSprintSpeed variable by typing in the box next to it. Be sure to hit the Enter key when you are done editing.
The movement speed of the mob, while sprinting at least, should now be changed.

```admonish note
As with many numeric variables, you should be cautious setting them too high. A high movement speed can cause significant client-side lag due to chunk loading.
```


## Moving VGroid (it sometimes spawns very, very far away)

- Go to any shuttle console on the station's map.
- Open the MAP tab, and hit Scan for objects.
- VGroid will have a randomly generated name, it should be obvious among the list.
- Once you know this name, hit F7 and click on the Objects tab. Search the name you got in objects with Grids selected.
- Note the entity ID of VGroid, ghost warp back to the station, and fly out into open space (VV editing your movement speed can help here). Once you find a sufficiently open area run the command tpgrid EntID X Y where EntID is VGroid's ID, X and Y are coordinates of the space you flew to, obtainable via F3.

_If you do accidentally overlap another grid with VGroid due to its sheer size, don't worry. Grids will not cause destruction to one-another unless they move, which is not normally possible if one is embedded in another. You can move further away and try tp'ing VGroid again._


## Adding hands to mobs (DOES NOT WORK WITH INANIMATE OBJECTS)

- Open the VV window for the mob,
- Click on the `Server Components` tab, and click `Add Component`,
- Search first for `ComplexInteraction`, highlight it, then hit `select`. Do the same process with the `Hands` component. (Some entities will also need the `Body` component, but this is rather rare.)
- Depending on how much you care, there are two ways to then finish the process of adding hands:
  - First, you can simply run the `addhands EntID` command in console twice, where `EntID` is the ID of the mob. This method will give the mob two left hands, which may not be desirable.
  - The second method allows you to add a right and left hand. First, go into the entity spawn menu and search for `right human hand` (or any other racial counterpart), and spawn it in. Then run the command `attachbodypart MobID HandID`, where the MobID is the ID of the target mob, and the HandID is the ID of the right hand you spawned in. Once you have attached the right hand, you can simply run the `addhands` command mentioned earlier once to add the left hand.

_Inanimate objects cannot have hands, at least with my current understanding, however you can still give them the `ComplexInteraction` component, allowing them to do simple tasks such as opening UI's or opening airlocks._
