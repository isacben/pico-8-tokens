## Player horizontal movement with friction:

This is a simple way to implement horizontal movement with acceleration and friction for the player. This implementation works better in 60 fps (this is, using `_update60()`).

In the `_init()` function, add:

```lua
--just the player initial position
p_x=20
p_y=100

--the player's horizontal speed
p_dx=0
```

The player movement function `p_move()` will be part of the `_update()` function somehow. The following lines are for acceleration:

```lua
function p_move()
	p_x+=p_dx
	
	if btn(0) then
		p_dx=max(p_dx-0.2,-1.5) --max() for acceleration to move left
	elseif btn(1) then
		p_dx=min(p_dx+0.2,1.5) --min() for acceleration to move right
	else
        --a lerp function:
        --lerp(a, b, t) = a + (b — a) * t
        --which would be: p_dx = p_dx + (0 - p_dx) * percentage
		p_dx=p_dx-p_dx*0.1
		
        --to prevent adding really small values that in the end
        --will move the player one more unit the last minute
		if abs(p_dx)<0.4 then
			p_dx=0
		end
	end
end
```