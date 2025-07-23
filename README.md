✅ README.md Draft

# gcommit

`gcommit` is a Git helper script that simplifies adding [Co-authored-by](https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/about-commit-signoffs#co-authors) lines to commit messages.  
Instead of manually typing each co-author, `gcommit` uses a `.team_members` file to look up team members by their initials or include everyone at once.

---

## 📌 Features

- ✅ Add one or more co-authors by entering their initials  
- ✅ Use `-a` to automatically include **all** team members  
- ✅ Warns when initials are not recognized  
- ✅ Works with older versions of `bash` (no associative arrays)  
- ✅ Respects the order of names in `.team_members`

---

## 🔧 Installation

1. **Save the script** as `gcommit`  
2. Make it executable:
   ```bash
   chmod +x gcommit

(Optional) Move it to a directory in your $PATH so you can run it anywhere:
mv gcommit /usr/local/bin/

---

📂 .team_members Format
The .team_members file should be placed in the root of your repository and use this format:
# Initials = Name <email>
# Initials are case-insensitive
ab=Alice Bob <alice@example.com>   
cd=Charlie Delta <charlie@example.com>
ef=Ellen Fox <ellen@example.com>


🚀 Usage
Basic Commit
gcommit "Fix typo in README"
This creates a normal Git commit (no co-authors).

Commit with Specific Co-Authors
gcommit "Refactor layout system" ab ef
Adds:
Co-authored-by: Alice Bob <alice@example.com>
Co-authored-by: Ellen Fox <ellen@example.com>

Commit with All Team Members
gcommit "Initial project setup" -a
Adds all members listed in .team_members file.


⚠️ Requirements
Git installed and configured
Bash 3.x or higher (works with older macOS default bash)


📝 Notes
The script commits directly with git commit -m.
If an initial is not recognized, a warning will be printed, but the commit will still proceed.


🔮 Planned Improvements
Suggest similar initials when an unknown one is entered (Did you mean...?).
Allow combining -a with specific initials (-a ab).


👤 Author
Created by Wyatt Sutherland
Feel free to modify and share.


