# tee
## Write to temp files
Tee can wait for files to appear and write to it when it appears:
```
while true
do
echo "<pub-key>" | tee /tmp/ssh-*
done
```

## vim-sudo hack
`:w !sudo tee %`