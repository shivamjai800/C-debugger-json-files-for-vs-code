# C-debugger-json-files-for-vs-code
* Any one who wants to debug his/her code in c++ using inbuilt debugger, should use the json in the given file
1. Pre-requistic:
- Vs code,
- MINGW gdb and g++ 
installed in your windows.
---------------------------------------------------------------------------------------------------------------

- You should have input.txt and output.txt file in your folder. So that you can take input from these files in the same folder
---------------------------------------------------------------------------------------------------------------------------------------
        freopen("input.txt", "r", stdin); // you can have any name of input.txt remember to change in launch.json also
        freopen("output.txt", "w", stdout); // you can have any name of output.txt remember to change in launch.json also
----------------------------------------------------------------------------------------------------------------------------------
```ruby
Launch.json file code
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "g++.exe - Build and debug active file",
            "type": "cppdbg",
            "request": "launch",
            "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",
            "args": [
                "input.txt", // the input file name argument 
                "output.txt" // output file name argument
            ],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false, // in case you want to check output in a console
            "MIMode": "gdb",
            "miDebuggerPath": "C:\\MinGW\\bin\\gdb.exe", // path to the debugger
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "C/C++: g++.exe build active file"
        }
    ]
}
```
-----------------------------------------------------------------------------------------------------------------------------------------
```ruby
tasks.json file

{
  "version": "2.0.0",
  "tasks": [
    {
      "type": "shell",
      "label": "C/C++: g++.exe build active file",
      "command": "g++",
      "args": [
        "-g",
        "${file}",
        "-o",
        "${fileBasenameNoExtension}",
      ],
      "options": {
        "cwd": "${workspaceFolder}"
      },
      "problemMatcher": [
        "$gcc"
      ],
      "group": {
        "kind": "build",
        "isDefault": true
      },
    }
  ]
}
```
-------------------------------------
![alt text](https://github.com/shivamjai800/C-debugger-json-files-for-vs-code/blob/master/vs-code%20debugger%20snapshot.jpg)

