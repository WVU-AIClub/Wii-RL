#### Questions:
    Why does it have to be in Python 3.12?

What must be done to convert single-player to local multiplayer:
1. **Controller Routing:** The AI must inject its inputs into a specific controller port rather than defaulting to Port 1, freeing up other ports for humans.
    **Sean Note:** Try to keep AI being Port 1, always need AI.

2. **Screen Splitting:** In local multiplayer, the emilator renders a split screen. Because your AI expects a full-screen view, we must dynamically crop the screen before resizing it to (140, 75) so the AI only "sees" its own.

3. **Memory Pointers:** The memory addresses for position, speed, and race completion originally pointed stricty to Player 1's arrays. By injecting a player_index multipler, we can shift the base pointer lookups.

`savesate.load_from_file(...)` it will reset the entire emulator. So comment it out so the AI doesn't teleport the human players everytime it finishes a lap or fails.