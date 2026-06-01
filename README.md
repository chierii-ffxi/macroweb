# FFXI Macro Viewer – Setup Guide

This guide helps you build your own **FFXI Macro Viewer** website from scratch.  
You will extract your macro and equipset data from your local FFXI installation, convert it to YAML, and then publish the site (e.g., on GitHub Pages).

---

## 🧱 What you need

- Windows PC with **FINAL FANTASY XI** installed and logged in at least once
- **Python 3** installed (with `pip`)
- **Git** (command line or GUI)
- A **GitHub account** (if you want to publish online)

---

## 1️⃣ Clone the two required repositories

We use two tools:

- [`print_macrobook`](https://github.com/chierii-ffxi/print_macrobook) – extracts macro books
- [`print_equipset`](https://github.com/chierii-ffxi/print_equipset) – extracts equipment sets

Open a terminal and run:

```bash
git clone https://github.com/chierii-ffxi/print_macrobook.git
git clone https://github.com/chierii-ffxi/print_equipset.git
```

> 💡 These are **my forks** of the original tools.  
> I changed **one file** in each to make the `git submodule` command work (see troubleshooting below).

---

## 2️⃣ Fix the submodule (if needed)

Inside each cloned folder, run:

```bash
git submodule update --init --recursive
```

---

## 3️⃣ Locate your FFXI user data folder

On Windows, go to:

```
C:\Program Files (x86)\PlayOnline\SquareEnix\FINAL FANTASY XI\USER
```

Inside, you will see **one or more folders with long hex names** (`<your-folder>`).  
Pick the one that belongs to the character you want to export.

---

## 4️⃣ Generate the YAML files

From the terminal, run the two scripts **from their respective folders**:

```bash
cd print_macrobook
python print_macrobook.py <your-folder>

cd ../print_equipset
python print_equipset.py <your-folder>
```

After each command, a `.yaml` file will be created in the same folder.  
For example:
- macrobook: `mc.yaml`
- equipsets: `eq.yaml`

---

## 5️⃣ Copy the YAML files to the web viewer

Copy the two YAML files into the `src/data/` folder:

> ⚠️ The viewer expects the files to be named exactly `mc.yaml` and `eq.yaml`.  
> Rename them if necessary.

---

## 6️⃣ Deploy to GitHub Pages

1. **Push your changes** to a GitHub repository:

2. **Enable GitHub Pages**:
   - Go to your repository on GitHub → **Settings** → **Pages**
   - Under “Branch”, select `main` and the `/ (root)` folder
   - Click **Save**

3. After a minute, your site will be live at:  
   `https://<your-username>.github.io/<repository-name>/`

---

## 🙏 Credits

- Tools by [hamham-fenrir](https://github.com/hamham-fenrir)  
- FFXI © Square Enix
