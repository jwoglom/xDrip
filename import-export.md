## Export Database
```
adb pull /sdcard/xdrip/export20201116-153543.zip .
unzip export20201116-153543.zip

adb exec-out com.eveningoutpost.dexdrip cat databases/DexDrip.db > DexDrip.db
```

## Import Database
```
$ adb forward tcp:8888 tcp:8888
$ nc localhost 8888 < export20201116-153543.sqlite
```

```
$ adb shell
run-as com.eveningoutpost.dexdrip
rm -rf /data/user/0/com.eveningoutpost.dexdrip/databases/DexDrip.db*
nc -l -p 8888 > /data/user/0/com.eveningoutpost.dexdrip/databases/DexDrip.db
```