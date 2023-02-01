## Animate a sprite (for example, a character) in PICO-8:

```lua
t=0 --frames counter, increases while the game is running
playerAnimation = {spr1, spr2, spr3, spr4} --array with IDs of the sprites for each frame

spr(getFrame(playerAnimation), x, y)

--function to get the current frame of the animation
function getFrame(animationArr)
    --8 is to slow down the counter t
    --#animationArr is the length of the animation array
    return animationArr[flr(t/8) % #animationArr + 1]
end
```