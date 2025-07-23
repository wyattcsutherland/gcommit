# gcommit

A lightweight Bash script to simplify Git commits with [co-authors](https://docs.github.com/en/github/committing-changes-to-your-project/creating-and-editing-commits/creating-a-commit-with-multiple-authors).  
It reads a `.team_members` file and automatically appends properly formatted `Co-authored-by:` lines to your commit messages.
Ideal for pair or mob programming.

---

## ✅ Features

- **Simple usage** – Add co-authors by their initials.
- **All-team commits** – Use `-a` to add all team members automatically.
- **Debug mode** – Use `-d` to preview what will be committed (implies `-a`, no changes are made).
- **Duplicate protection** – Co-authors are deduplicated automatically.
- **Friendly warnings** – Unknown initials are skipped with a clear warning.

---

## 📦 Installation

1. Save the script as `gcommit` in your project root or in a directory on your `$PATH`.
2. Make it executable:

   ```bash
   chmod 755 gcommit
   ```

3. Create a `.team_members` file in the same directory as the script.

---

## 📝 `.team_members` Format

Each line maps initials to a Git author in the format:

```
# Comments and blank lines are ignored
ab=Alice Brown <alice@example.com>
ef=Eric Foo <eric@example.com>
```

- **Initials** are case-insensitive (`AB`, `ab`, or `Ab` are all valid).
- **Email format** should match Git’s author format (`Name <email>`).

---

## 🚀 Usage

### Basic Commit

```bash
gcommit "Fix controller logic" ab ef
```

Resulting commit message:

```
Fix controller logic

Co-authored-by: Alice Brown <alice@example.com>
Co-authored-by: Eric Foo <eric@example.com>
```

---

### Commit With All Team Members

```bash
gcommit "Initial commit" -a
```

Adds **all authors** from `.team_members`.

---

### Debug Mode (No Commit)

```bash
gcommit "Testing debug" -d
```

Outputs the team members and the final commit message **without committing**:

```
==== DEBUG MODE (no commit) ====
Team members in .team_members:
  ab = Alice Brown <alice@example.com>
  ef = Eric Foo <eric@example.com>

Commit message to be used:
--------------------------
git commit -m "Testing debug"
Co-authored-by: Alice Brown <alice@example.com>
Co-authored-by: Eric Foo <eric@example.com>
============================
```

---

### Other Examples

- **Show help**:

  ```bash
  gcommit -h
  ```

- **Single co-author**:

  ```bash
  gcommit "Update README" ab
  ```

- **Commit without co-authors** (just omit initials):

  ```bash
  gcommit "Quick typo fix"
  ```

---

## ⚠️ Warnings & Notes

- If an unknown initial is provided:

  ```
  Warning: Unknown initials 'zz' — skipping
  ```

- The script will exit if `.team_members` is missing.
- Commit message **must** be the first argument.

---

## 📌 Future Improvements

- Support for `-v` verbose mode.
- Allow `-d` with specific initials (debug only selected co-authors).
- Sort authors alphabetically in `-a` mode.

---

## 🌐 Optional Global Installation

To use `gcommit` anywhere:

1. Move the script to `/usr/local/bin`:

   ```bash
   sudo mv gcommit /usr/local/bin/
   ```

2. Ensure it’s executable:

   ```bash
   sudo chmod 755 /usr/local/bin/gcommit
   ```

3. Now you can run `gcommit` in any Git repository.

---
