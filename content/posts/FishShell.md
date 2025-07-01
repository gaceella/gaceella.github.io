
+++
date = '2025-06-29'
title = 'Fish Shell'
+++



# Fish Shell

> "Fish doesn’t just run commands, it makes the shell feel like home, with clarity and smartness in every keystroke."

## FISH Shell (Friendly Interactive Shell)

### What is FISH Shell?
A modern shell with helpful features like suggestions and colors. Made for interactive use, not scripting.

### Why do we use the FISH Shell?
To get a smooth, user-friendly terminal experience. Makes typing commands easier and faster.

### Role in Shell Scripting?
It is not ideal for scripting because it does not follow POSIX standards. Scripts written in Fish would not work in other shells.

### Advantages:
- It performs smart auto suggestions.
- It performs syntax highlighting.
- It is easy to use.

### Disadvantages:
- It is not POSIX-compliant.
- It is limited for scripting.
- It is not pre-installed on all systems.

### Example

Here is the simplest code for understanding the concept of the FISH Shell:

```fish
#!/usr/bin/env fish

echo "Welcome to FISH SHELL."
mkdir -p fish_folder
touch fish_folder/hello.txt
```

The line `#!/usr/bin/env fish` tells the system to locate and run the script using the Fish shell via the `env` command. This makes the script more portable, as it works even if Fish is not installed in a fixed path like `/usr/bin/fish`.

### Commands to run the code

```bash
chmod +x fish_script.fish
./fish_script.fish
```

In the code, we create the folder with the name `fish_folder` and this folder contains one file named `hello.txt`.

### Installing the FISH Shell

To use the Fish shell, it must first be installed (as it is not pre-installed on most systems).

```bash
sudo apt install fish
```

After installation, run the command:

```bash
fish
```

This switches your terminal to use the Fish shell.

### Features of the FISH Terminal

- Displays commands in colorful format.
- Enhances readability and user experience.
- Makes learning and navigating the shell easier.

### How to Exit

```bash
exit
```

This returns the shell back to your default shell.

---

The Fish shell offers an intuitive and user-friendly experience with features like auto suggestions, syntax highlighting, and sane defaults. It's designed for interactive use, making the command line faster and more enjoyable.

> “In a sea of shells, Fish stands out elegant, helpful, and always a step ahead."