Credits to Rolanmen1, Vykan12, and TR143 for the development of the original GBA Fire Emblem RNG script and the search function. Below is the original README from TR143's script with additional commands from my modifications to their script. The BizHawk one is the primary one being updated, and so this Readme will reflect that script. The VBA one has most of the features, but will not be updated as the emulator is effectively outdated for TAS purposes.

INSTRUCTIONS
There are a bunch of buttons that you can press to do things:
'Q' - decrement RNG
'W' - advance RNG
'E' - turn on AI phase script
'R' - turn off AI phase script
'U' - RNG display on/off
'I' - READ IN INPUT FILE
'O' - search result display on/off
'H' - display help
'F/G' - Skip to left/right match
'V' - Print Data
'Y' - Print Total Exp
'L' - Debug Functions
'M + Arrows' - Skip Larger RNG Amounts
'N' - Lock RNG in place
'J + Arrows' - Minimal Search
'K' - Return to 0 RN

SEARCH FUNCTION
To use the search function, open SearchInputs.txt
This file is how you will tell the script what to search for.
There's a small template in there already, it should look like this:
-200,500
h<48
<7
>=0
or
h>=90
end

The first line sets the left and right bound of the search.
The first number is how far back to look from your current position,
and the second number is how far to look right.
After that you put in the conditions you're looking for.

h signifies that you want to calculate a hit.

This means the script will compare your number to the average of the next two random numbers.
Without one it will only look at the next RN.
There must be a comparator and the number you are going to compare to.

You can use any of the following comparators: < <= > >= =

Putting in an "or" means that the search will include any positions 
that match any of the entered lists in its results.

If you want to put things in the file that aren't part of the search, you can type "end"
at the bottom of the file. Anything after that will be ignored. (you could use this to store
frequently used sequences in the same file for easy access!) An "end" is not required to be 
in your file as long as there is nothing after your search inputs.

When you're done writing your input file, just save it and press 'I'
If you want to change the search later, just modify SearchInputs.txt, save it,
and press 'I' again, there's no need to stop or restart the script.
As the RNG changes in game the search will automatically update, finding more matches as you go.
It will always show you 5 matches around your current position, 2 behind and 3 ahead or at your 
position, unless there are less than 5 total matches. (if you set one of the bounds to 0, 
you'll get 5 in one direction)

AI PHASE SCRIPT
This script uses save state 9 to brute force what the fastest enemy phase is for TAS purposes.

You can press 'E' to enable the script and 'R' to disable the script at any time.

Once enabled, whenever the game next gives the AI control the script will begin.
If the AI already has control the script will begin immediately from that point.

The script will cycle through phases from the starting point. Whenever a phase ends
the script will print information to the console about that phase. Then, the script will 
return to the starting point and start another phase from there, from 1 position in the 
RNG after where it was last time.

Just a quick reminder that you can use the emulator's pause function at any time 
and it won't interupt the script.

Loading a savestate while the AI phase script is on will advance to the next phase immediately.
This can be used to speed up your search significantly, however bear in mind that if you do
this the amount of time the phase took that gets posted will not be accurate for the skipped phase.

USEFUL INFORMATION
I made a guide for the RNG a while ago, here it is:
https://docs.google.com/document/d/19nUk3G6REiEvksmO47CudbMWi7YihQGDVPn23SwJyn8/edit

It starts with an explanation of how the RNG works, then goes into stuff like battle
calculations and picking up desert items, which is probably the stuff more useful for 
someone just trying to use this script.