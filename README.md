chuyển đổi font sang gfx

Installation
Clone this repository.
Download luvit (Lua JIT Compiler, i.e. NodeJS of Lua) from here and place the executables in the cloned folder.
Execute the following command(s):
lit install creationix/coro-spawn

Download the swfmill.exe CLI/CLT from here and place the executable in the cloned folder.
Download gfxexport.exe CLI/CLT from here and the required dynamic link libraries. You must find this yourself as it is apparently illegal to inform you of such information. Use your preferred search engine.
How to use
Simple place all your .ttf files in the cloned folder.
Using your command line run the command: luvit s.lua
With informative output you should see .gfx files popup up as the .ttf files are converted.
Stream them to FiveM as you would and register these fonts via a script, here's an example in Lua (original):
local fontId

Citizen.CreateThread(function()
    RegisterFontFile('out') -- the name of your .gfx, without .gfx
    fontId = RegisterFontId('Fira Sans') -- the name from the .xml

    while true do
        Wait(0)
        SetTextFont(fontId)
        BeginTextCommandDisplayText('STRING')
        AddTextComponentString('Hello, world!')
        EndTextCommandDisplayText(0.5, 0.5)
    end
end)
