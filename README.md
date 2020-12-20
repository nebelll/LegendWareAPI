Have fun on your lw paste if you actually learn from this
Edit: Imma update it in a few days this isnt the whole API



          Client

-loads the script test and outputs "i loaded script!" in eventlogs

Syntax: client.log

```ruby
client.load_script("test")
client.log("i loaded script!")
```

-unloads the script test

Syntax: client.unload_script

```ruby
client.unload_script("test")
```

-loads script test

Syntax: client.load_script

```ruby
client.load_script("test")
```

-Adds a Callback to the function
CallbackList:
on_shot - when aimbot is firing
on_paint - hook to draw something..
on_createmove - tick processing hook

Syntax: client.add_callback

```ruby
local function test()
  -- func
end
client.add_callback("on_createmove", test)
```


          Events

-Registers a valve event

Syntax: events.register_event

```ruby
local function hurt(event)
-- random
end

events.register_event("player_hurt", hurt)
```
Some extra information:
```
game_event:get_bool
game_event:get_int
game_event:get_float
game_event:get_string
game_event:set_bool
game_event:set_int
game_event:set_float
game_event:set_string
```


          Console

-Sets a convar value(string)

Syntax: console.set_string
```ruby
console.set_string("name", "noname")
```
-Sets a convar value(float)

Syntax: console.set_float
```ruby
console.set_float("zoom_sensitivity_ratio_mouse", 0.0)
```
-Sets a convar state(Int)

Syntax: console.set_int
```ruby
console.set_int("custom_var", 2)
```
-Sets a convar state(bool)

Syntax: console.set_bool
```ruby
console.set_bool("crosshair", false)
```
-Returns convar value(string)

Syntax: console.get_string
```ruby
local lc_name = console.get_string("name")
```
-Returns convar value(float)

Syntax: console.get_float
```ruby
local volume = console.get_float("volume")
```
-Returns convar value(int)

Syntax: console.get_int
```ruby
local bomb_time = console.get_int("mp_c4timer")
```
-Returns convar state(bool)

Syntax: console.get_bool
```ruby
local can_drop = console.get_bool("mp_drop_knife_enable")
```

-Executes a client command to say 1 after killing someone

Syntax: console.execute
```ruby
local function shot(shot_info)
    local result = shot_info.result
    if result == "Hit" and shot_info.server_damage >= 100 then
       console.execute("say 1")
    end
end
client.add_callback("on_shot", shot)
```


          Globals

-Returns max clients

Syntax: globals.get_maxclients
```ruby
local max_clients = globals.get_maxclients()
```
-Returns interval per tick

Syntax: globals.get_intervalpertick
```ruby
local ipt = globals.get_intervalpertick()
```
-Returns frame count

Syntax: globals.get_framecount
```ruby
local framecount = globals.get_framecount()
```
-Returns tick count

Syntax: globals.get_tickcount
```ruby
local ticks = globals.get_tickcount()
```
-Returns frame time

Syntax: globals.get_frametime
```ruby
local frametime = globals.get_frametime()
```
-Returns curtime

Syntax: globals.get_curtime
```ruby
local curtime_float = globals.get_curtime()
```
-Returns real time

Syntax: globals.get_realtime
```ruby
local realtime_float = globals.get_realtime()
```
-Returns your username

Syntax: globals.get_username
```ruby
local user = globals.get_username()
```
-Returns time(string)

Syntax: globals.get_time
```ruby
local time = globals.get_time()
```
-Returns server ip

Syntax: globals.get_server_address
```ruby
local address = globals.get_server_address()
```
-Returns ping

Syntax: globals.get_ping
```ruby
local ping = globals.get_ping()
```
-Returns framerate

Syntax: globals.get_framerate
```ruby
local framerate = globals.get_framerate()
```


          CMD

-Sets button state

Syntax: cmd.set_button_state
```ruby
local function duck()
  cmd.set_button_state(buttons.in_duck, true)
end

client.add_callback("on_createmove", duck)
```
-Returns button state

Syntax: cmd.get_button_statelocal function draw()
  local font =  render.create_font("Verdana", 12, 600, true, true, true)
  render.draw_text(font, 100, 100, color.new(255, 0, 0), tostring(cmd.get_choke()))
end

client.add_callback("on_paint", draw)
```ruby
local function draw()
  if cmd.get_button_state(buttons.in_use) then
    render.draw_triangle(100, 100,  120, 90, 80, 90, color.new(255, 0, 0))
  end
end

client.add_callback("on_paint", draw)
```
-Returns current choke

Syntax: cmd.get_choke
```ruby
local function draw()
  local font =  render.create_font("Verdana", 12, 600, true, true, true)
  render.draw_text(font, 100, 100, color.new(255, 0, 0), tostring(cmd.get_choke()))
end

client.add_callback("on_paint", draw)
```
-Returns current sendpacket state

Syntax: cmd.get_send_packet
```ruby
local function draw()
  if cmd.get_send_packet() then
    render.draw_triangle(100, 100,  120, 90, 80, 90, color.new(255, 0, 0))
  end
end

client.add_callback("on_paint", draw)
```


          Engine

-Returns hltv state

Syntax: engine.is_hltv
```ruby
local function draw()
  if engine.is_hltv() then
    render.draw_triangle(100, 100,  120, 90, 80, 90, color.new(255, 0, 0))
  end
end

client.add_callback("on_paint", draw)
```

-Returns taking steam-screenshot state

Syntax: engine.is_taking_screenshot
```ruby
local function draw()
  if not engine.is_taking_screenshot() then
    render.draw_triangle(100, 100,  120, 90, 80, 90, color.new(255, 0, 0))
  end
end

client.add_callback("on_paint", draw)
```

-Returns pause state

Syntax: engine.is_paused
```ruby
local function draw()
  if engine.is_paused then
    render.draw_triangle(100, 100,  120, 90, 80, 90, color.new(255, 0, 0))
  end
end

client.add_callback("on_paint", draw)
```

-Returns recording demo state

Syntax: engine.is_recording_demo
```ruby
local function draw()
  if engine.is_recording_demo() then
    render.draw_triangle(100, 100,  120, 90, 80, 90, color.new(255, 0, 0))
  end
end

client.add_callback("on_paint", draw)
```

-Returns playing demo state

Syntax: engine.is_playing_demo
```ruby
local function draw()
  if engine.is_playing_demo() then
    render.draw_triangle(100, 100,  120, 90, 80, 90, color.new(255, 0, 0))
  end
end

client.add_callback("on_paint", draw)
```

-Returns current map group name

Syntax: engine.get_map_group_name
```ruby
local function draw()
  local font =  render.create_font("Verdana", 12, 600, true, true, true)
  render.draw_text(font, 100, 100, color.new(255, 0, 0), tostring(engine.get_map_group_name()))
end

client.add_callback("on_paint", draw)
```

-Returns current short map name

Syntax: engine.get_level_name_short
```ruby
local function draw()
  local font =  render.create_font("Verdana", 12, 600, true, true, true)
  render.draw_text(font, 100, 100, color.new(255, 0, 0), tostring(engine.get_level_name_short()))
end

client.add_callback("on_paint", draw)
```

-Returns current map name

Syntax: engine.get_level_name
```ruby
local function draw()
  local font =  render.create_font("Verdana", 12, 600, true, true, true)
  render.draw_text(font, 100, 100, color.new(255, 0, 0), tostring(engine.get_level_name()))
end

client.add_callback("on_paint", draw)
```

-Returns connected state

Syntax: engine.is_connected
```ruby
local function draw()
  if engine.is_connected() then
      render.draw_triangle(100, 100,  120, 90, 80, 90, color.new(255, 0, 0))
  end
end

client.add_callback("on_paint", draw)
```

-Returns in-game state

Syntax: engine.is_in_game
```ruby
local function draw()
  if engine.is_in_game() then
      render.draw_triangle(100, 100,  120, 90, 80, 90, color.new(255, 0, 0))
  end
end

client.add_callback("on_paint", draw)
```

-Sets new view angle

Syntax: engine.set_view_angles
```ruby
local function cm()
  local viewangles = engine.get_view_angles()
  engine.set_view_angles(vector.new(viewangles.x, viewangles.y + 180.0, viewangles.z))
end

client.add_callback("on_createmove", cm)
```

-Returns current view angles

Syntax: engine.get_view_angles
```ruby
local function cm()
  local viewangles = engine.get_view_angles()
end

client.add_callback("on_createmove", cm)
```

-Returns local player index

Syntax: engine.get_local_player_index
```ruby
local function draw()
  local player = engine.get_player_for_user_id(1)
  local me = engine.get_local_player_index()
  if player ~= me then
      -- something
  end
end

client.add_callback("on_paint", draw)
```

-Returns player for user ID

Syntax: engine.get_player_for_user_id
```ruby
local function draw()
  local player = engine.get_player_for_user_id(1)
  local me = engine.get_local_player_index()
  if player ~= me then
      -- something
  end
end

client.add_callback("on_paint", draw)
```

-Returns screen width

Syntax: render.get_screen_width
```ruby
local function screen_sizes()
    local screen_width = render.get_screen_width()
    local screen_height = render.get_screen_height()
end

client.add_callback("on_paint", screen_sizes)
```

-Returns screen height

Syntax: render.get_screen_height
```ruby
local function screen_sizes()
    local screen_width = render.get_screen_width()
    local screen_height = render.get_screen_height()
end

client.add_callback("on_paint", screen_sizes)
```
