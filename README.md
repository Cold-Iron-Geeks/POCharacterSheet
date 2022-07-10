# POCharacterSheet
CIG's repository for Character sheets.<br>
We have a LOT to go through here, obviously this is just a lot of information to try and commit to a team of about 2, thinking it's just Bryant and Myself.
If we get more, fuckin' great. Love it, we're really happy you're here, more help is always good.<br>

Below I'll be writing out what we'll be needing to code into the game, this should help with how we structure the code and work on things. I will be trying
to put these in the order of operations as to what we will need before the next step is implemented, so that we work progressively, expounding upon the previous
code we create. Anything under the Numerical can be taken in separate parts, as they will eventually add on to one another. (i.e figuring out how something like
Drop down menus work, then using that knowledge to help set up for when Hunter inevitably goes in the exact order due to his autisim brain, we contribute all
together to make a masterpiece here.<br><br>
(Keeping in mind that the Android Studio we download is able to Execute both Java, Javascript, and C/C++. Java is able to look for other java files and
execute them so we can sub-section code into specific Java files for security if we have to. This can allow us to make files only visible to Java, and not
end users.)<br><br>

1. **Engine work. We need a base engine that:**<br>
  a. Can accept information and be readily changed at any point when the user wants<br>
  b. Allow multiple parts of the code that is dedicated to simple things like, Name, Player name, etc. (The rest may be done in HTML with Java Integration)<br>
  c. Button that allows the additon of more visuals on the screen (i.e. Feats, Spell Additions, etc. Also, leveling up and initial character creation)<br>
  d. Boxes to check (True/False statements with user interaction)<br>
  e. Drop down menus with multiple options to choose from (Gods, Lords, Feats, Spells(Upon pressing Add spell button, Spells have special interactions at
      level 1)  
   f. Drop down menus that display Primary Race, Secondary Race, Dieties, Lords, Temperament, Traits, Detriments, Size, Class, Armor Type, Armor Tier, Armor
      slots (Head, Chest, etc.), Weapons, Weapon Tier, Tattoos (Tattoo Slots based on Size), Inventory (Item Integration), Enchantments on Gear, Feat Type,
      Feats
  g. Boxes to check for: Level 0 Hardcore Rule, Tertiary "Undead" Race, Once per day abilities if they can apply (Devotion, Lords), Generational Characters
  h. Areas for user input for the Point-Buy system (Attributes) (Expound upon this later with working with Jacob to make Standard Arrays for people to take,
       consensus is that people HATE Point-Buy: I know Jake won't budge on that one likely. Rolling for stats in Orredon would be BONKERS. Maybe allow it to
       be a Hardcore Rule?) display used/unused points
  i. Skill Point Investment, Attribute Adjustments, Total, display used/unused points
  j. HP Config that is Automatic based on race (Just level 1 for now, Leveling up Code Integration for later. Config/Auto is done AFTER Attribute and Feat 
       assignments.)
  k. AC Calculator
  l. Save Calculator, "Derrived Attributes" (Phys. Power, Phys. Acc. etc.)
  m. Feat per level, skill point per level calculator, display used/unused points (Based on Class and feats (Feat implementation later, focus on class
        first)) Also create a Level one: "Current Skill points, Current Feat Points." Armsman gain an additional Feat point (ONCE PER LEVEL) for Weap.
  n. Resource display and calculations Psions and Mancers have unique resources (Riftmaker/Divine Ardent included if we want)
  o. Feat integration (Effecting other parts of the system (Affects: Granted Attributes, Skill points per level, Extra Feat points on certain levels,
        Resources, Granted Skills, Current Feat points available (Limited as how it's spent (Backstory: Monk's Child)), Current points available to Invest
        (Limted to how it's spent (Backstory:Mancer's Child)). Based on a Rank system, integration with Current Feat points available.
  p. Feat Pre-Requisites( Affected by: Other Feats( Some at rank 5), Attribute Totals, Skill Totals, Current Level, Class)
  q. Additional Feats automatically for Attribute Capstone or other things you gain.
  r. Ability to Undo Feat Levels, Entire Feats, Levels, Attribute Assignment, Automatically take away feats that you don't qualify for anymore if applicable.
        Warn the user of their actions if the change will affect other things on the character sheet, and as them if that's what they want. This allows them
        to acknowledge the action they are taking is going to change key parts of their character sheet and they can search for it.
  s. Each level needs to be recorded when Current Feat Points, Current Skill Points, Attribute Points, and other events are recorded. To do this we'll likely
        have to create a function at the end that checks for those points to be 0. If it's not, point to another Function that all it does it literally point
        back to the Function before it, or perhaps there is an actual Loop Function that can do this to save on lines? Either way, once it's 0 we activate
        a function at the _very end_ that goes through and runs the calculations for everything a second time to make sure everything is _perfect_, then
        allow a function to Record everything and commit it to a "Level 1 Stats" Document (Likely Java) and so on up to however many Stats we have. This can
        help us code how many Levels we allow per character sheet later. The reason each Stat is recorded at the end is for feats like "Acolyte of Study" 
        which is based on what level you take it that it goes into affect (Also feats like Power Overwhelming, Battlemage, etc.) This also includes HP per
        level, which is affected by What your Con is at the _end of your level up period_.
  t. Button that activates events: Level up, Spell Activations (Resource Drain), Item Uses if avaialble to use them (Potions), Once per Days, Tattoo Effects,
        Anything that affects other values temporarily, Magic Item charge Uses. (Other suggestions available if I'm forgetting anything)
  u. Generational Character Integration: These can only be activated by looking for a CName-20 character, then allowing them to choose from the feat list.  
      
        
After everything in the system is able to be: **Displayed**, **Interacted with**, **Properly displaying correct information**, **You can level up**, **You
can Redo actions you took during Character Assignments**,**Allowing Level Restorations** (Go back to what we had recorded at levels 1, 2, etc.), **Explain to
the users that the app takes a "Save State" of each level so that they may restore back to a previous level if they don't like the direction they took or
wants to just create characters and check out their different levels**,
        
        _Maybe allow them to do Backwards Compatability on redos? If they want to make a character sheet just to test builds they can create it, then go
        back to level 1 to play in the campaign. When they hit level 2, they can just load level 2-characterX However, if they want to do a "Branching path"
        for the characters they need to make a new sheet or return to level 1 so they can edit their characters name to make a "new" character entry, which
        allows for the creation of new java sheets behind closed doors. We'd need to subsection the code like: 1. Main Java -> User can "Create new" or load 
        a "Character-CName.java" -> Create new makes a "Character-CName.java" CName is the input the user gives, it also creates a new folder for that java
        file to be in. Naming scheme for each folder is Character, allowing it self to be renamed to Character(1), Character(2), if the name is already taken
        etc. Users won't see that unless they are diving through files. This will let the users to make multiple characters with the same name thus 
        "Branching" them._ We can also create code that generates a string of numbers based on your choice and using that information to Cross refference
        with the first sheet they saved/made if they go to level X, then press "Level up", when they press the button to Finish Level up, it returns with 
        "This file is different than the current Level 2 CName, did you want to replace it or make a new iteration?" Iterations
**Give proper explanations on how to use the app**, **Deletion of Character Sheets**, **End User Licenses agreements written up**, **Permissions asked for the Phone's File System use (To Create, Delete, Move, Modify it's own files)**, **Disclaimer Written up**, **"Finish Level up" Button for Users**, **A Button to go back to level 0 with the character details put in, essentially allowing for the users to undo their level 1**, **Ability to go back to previous levels and make iterations**, and **A working Heritage system**, We'll start caring more about the next step.

2.**Visual Cycle, what things should look like**
  This part is more free form and based on prefference and ideas, but basically we need the ability to: **Display Prompts/Buttons, Display information on the screen in a clean and concise manner, Display the information in a way that is pleasing, Using the app and features needs to be Easy to do along with being Intuitive. You just need to understand what you're seeing by looking at it.** 
  
  It is apparent what each thing does and you instantly know what you want from it. Colors are attractive, perhaps allowing people to change colors, We can think about where everything goes, etc. This is heavy on marketting and just working to see what we can do and how crisp it is. Lots of code to learn how to create windows/displays etc.
  
  
  
  
