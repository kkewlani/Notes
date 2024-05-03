# Overview
Covering various Automator Scripts that can be used with Macbook

## Switching Bluetooth devices between multiple Macs

Great way to use bluetooth devices across multiple Macs : [Using blueutil based Automator Script](https://apple.stackexchange.com/a/432091/521981)

code (for my keyboard and trackpad (works with `zsh shell`):
```
res=$(/opt/homebrew/bin/blueutil --is-connected e0-eb-40-d5-12-64)
if [[ "$res" = '1' ]]
then
/opt/homebrew/bin/blueutil --unpair e0-eb-40-d5-12-64
/opt/homebrew/bin/blueutil --unpair e4-50-eb-f1-28-b3
else
/opt/homebrew/bin/blueutil --unpair e0-eb-40-d5-12-64
/opt/homebrew/bin/blueutil --unpair e4-50-eb-f1-28-b3
sleep 1
/opt/homebrew/bin/blueutil --pair e0-eb-40-d5-12-64
/opt/homebrew/bin/blueutil --pair e4-50-eb-f1-28-b3
sleep 1
/opt/homebrew/bin/blueutil --connect e0-eb-40-d5-12-64
/opt/homebrew/bin/blueutil --connect e4-50-eb-f1-28-b3
fi
```
