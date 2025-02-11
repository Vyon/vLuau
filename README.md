# vLuau
vLuau is a Luau VM with compiler which can be ran in Roblox.<br>
Like vLua but with Fully Luau Support.<br>
You can use this module instead of loadstring in roblox but with sandboxed bytecode.
## Credits
- [vLuau](https://github.com/kosuke14/vLuau) - [me (kosuke14)](https://github.com/kosuke14)
- [Fiu](https://github.com/TheGreatSageEqualToHeaven/Fiu) (Luau Bytecode Interpreter) - [TheGreatSageEqualToHeaven](https://github.com/TheGreatSageEqualToHeaven) and [Rerumu](https://github.com/Rerumu)
- [LuauCeption](https://github.com/RadiatedExodus/LuauCeption) (Running Luau inside Luau) - [RadiatedExodus](https://github.com/RadiatedExodus) and [phoria](https://github.com/phoria)
## Usage
```lua
local loadstring = require(path.to.MainModule) -- requiring vLuau MainModule

loadstring(<string:(source or bytecode)>[, table:env, string:chunkname]): function
-- compile code and build function
loadstring.luau_execute(...)
-- same as above

loadstring.luau_compile(<string:source>[, string:chunkname]): string
-- compile code and return bytecode

loadstring.luau_load(<string:bytecode>[, table:env]): function
-- build function with provided compiled bytecode

-- Examples:
loadstring("print('hello world!')", getfenv(0))()
-- (OUTPUT) hello world!
loadstring("a", nil, 'syntaxTest')()
-- (ERROR) syntaxTest:1: Incomplete statement: expected assignment or a function call
```
Roblox Model is available at [here](https://create.roblox.com/store/asset/108059886578663) (trolled rblx fr)
## Building
1. Go [LuauCeption](https://github.com/RadiatedExodus/LuauCeption) and build them as compiler with latest Luau
2. Replace Ception.luau with the built version.
3. Place Instances in Roblox like this:
```
├── <ModuleScript> MainModule (init.lua)
|   ├── <ModuleScript> Ception (Ception.luau)
└── └── <ModuleScript> Fiu (Fiu.luau)
```
### Tips to add large 'ModuleScript' into Roblox Studio
Roblox Studio could be crashed when you try to paste the large script into Roblox Studio.<br>
This tips may solve that problem.
1. Open some place on Studio.
2. Right click somewhere in Explorer, and click on 'Insert from file'.
3. Find the large script to insert.
4. Name the script to something to locate it easily.
5. Save place or the script as XML format (place: .rbxlx, model: .rbxmx)
6. Open the saved file with your text editor.
7. Find the script item.
8. Change `<Item class="Script"` to `<Item class="ModuleScript"` then save it.
9. Open the file as Studio and the script is now ModuleScript.
