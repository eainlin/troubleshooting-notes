# Windows Icon Cache Reset Script

This PowerShell script stops Explorer, clears icon and thumbnail caches, and restarts Explorer.

```powershell
# Stop Windows Explorer
Stop-Process -Name explorer -Force

# Remove Icon Cache
Remove-Item "$env:LOCALAPPDATA\IconCache.db" -ErrorAction SilentlyContinue
Remove-Item "$env:LOCALAPPDATA\Microsoft\Windows\Explorer\iconcache*" -Force -ErrorAction SilentlyContinue
Remove-Item "$env:LOCALAPPDATA\Microsoft\Windows\Explorer\thumbcache*" -Force -ErrorAction SilentlyContinue

# Restart Windows Explorer
Start-Process explorer.exe
```

✅ This can help resolve missing or corrupted icons on Windows desktops.
