# 💽 Eject All Disks – macOS Shortcut

A macOS Shortcut that ejects all connected external disks using a shell script and `diskutil`. I liketo put this one on my [Stream Deck](https://www.elgato.com/us/en/s/welcome-to-stream-deck)

## 🛠 How It Works

This shortcut uses the built-in **Run Shell Script** action in the Shortcuts app to detect and eject all mounted external disks.

### Shell Script Used

```bash
IFS=$'\n'
disks=$(diskutil list external | grep -o -E '/dev/disk[0-9]*')
for disk in $disks; do
  diskutil unmountDisk $disk
done
```

- diskutil list external — lists all connected external disks.
-	grep filters the output to extract only the disk identifiers (e.g., /dev/disk4).
-	Each disk is safely unmounted using diskutil unmountDisk.

### 🚀 Installation

1. Open the Shortcuts app.
2.	Create a new shortcut and add a Run Shell Script action.
3.	Paste the script above into the action.
4.	Optionally:
   - Set the shell to bash
   - Set input to “None”
   - Set “Pass Input” to “to stdin”
5. Name your shortcut something like Eject All Disks.
6. (Optional) Add it to your menu bar or assign a keyboard shortcut for quick access

### ⚠️ Notes

- You may be prompted to give the Shortcuts app or Terminal full disk access or permissions to control your Mac.
- This shortcut only affects external disks. Internal drives are unaffected.

### 📎 License

This project is released under the MIT License.
