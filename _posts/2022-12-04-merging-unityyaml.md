
## Merging Unity yaml files with SmartMerge
For some reason, i was alway annoyed by the way unity yaml files (mostly scenes) often failed to merge automatiaclly in git, but never spend any time looking into solutions. 
I was aware that the repository solution provided by unity has some way of merging the yaml files in a smart way, but i never questioned if that could be available for git. 

At least until recently, when i stumbled upon [Smart Merge in the Unity Manual](https://docs.unity3d.com/Manual/SmartMerge.html). The setup is a bit clunky, and you need to call in for files specificly with ``git mergetool -t unityyamlmerge file-with.conflicts``, but it solves most of the stuff. Only real propblem i had was that with unsolvable conflicts, it calls FileMerge on mac to let the user decide, and either i'm to stupid to work with filemerge, or it never stored the resolved file. Changing the Merge tool to VS-Code by adding 

```
* use "/usr/local/bin/code" --wait --merge %r %l %b %d
```
to ```/Applications/Unity/Hub/Editor/2021.3.5f1/Unity.app/Contents/Tools/mergespecfile.txt``` let me have my go to merge conflict editor, whose response seemed to satisfy unityyamlmerge and finaly let me have relativly easy merges of .unity and .prefab files.