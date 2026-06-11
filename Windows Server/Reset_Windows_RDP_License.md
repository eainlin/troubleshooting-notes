## Check the remaining days with the powershell

```sh
PS C:\Users\Administrator> (invoke-cimmethod -inputobject (get-ciminstance -namespace root/CIMV2/TerminalServices -classname Win32_TerminalServiceSetting) -methodname GetGracePeriodDays).DaysLeft
>>
XX
PS C:\Users\Administrator>
```

### Next, let’s dive into solving the problem.

- Start / Start typing randomly / Run / regedit, then:

- Find Computer\HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Terminal Server\RCM\GracePeriod

- NETWORK SERVICE – Change – Assign Administrators

- Delete the key.