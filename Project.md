# Applied Activity 4: The Case of the Vanishing Voyageur Compass (Individual)

**Name:** Matt Pheaton
**GitHub username:** Matt120056
**Repository URL:** https://github.com/...

> This report is my own individual work. I built my own repository, my own pages and my own report.

---

## Mission 0: Workstation
```text
(git --version and git config --global -l)

git version 2.55.0

filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
user.name=Matt Pheaton
user.email=matthew.pheaton16@gmail.com
credential.helper=store
init.defaultbranch=main
```

## Mission 1: Read the Crime Scene
```text
(git log --oneline)
83df583 (HEAD -> main) Add images and starter stylesheet
1e0d155 Tidy repo: remove old notes
72f5d74 Add a note about the suspicious listing
0f7026f Move Display Case 7 styling note
23e8437 Add exhibit list
d8166b0 Start museum site
```
```text
(git log --oneline --all --graph)

* 660ace9 (feature/gold-accent) Try a gold accent colour
* 83df583 (HEAD -> main) Add images and starter stylesheet
* 1e0d155 Tidy repo: remove old notes
* 72f5d74 Add a note about the suspicious listing
| * 629628b (archive/night-shift) Upload security log export
|/  
* 0f7026f Move Display Case 7 styling note
* 23e8437 Add exhibit list
* d8166b0 Start museum site

```
```text
(git branch -a)
  archive/night-shift
  feature/gold-accent
* main
```
```text
(git ls-tree -r archive/night-shift --name-only)

README.md
legacy/old-index.html
legacy/old-style.css
security-log.txt
staff-notes.txt
```
**Explain (why did the second log command show more commits than the first?):**

The second command showed more commits because --all tells Git to include commits from every branch, not just the current main branch. It revealed two additional commits on the feature/gold-accent and archive/night-shift branches that were not part of the main branch history. The --graph option also displays how the branches split off from the main history.

## Mission 2: Dig Through the Evidence
```text
(git log --diff-filter=D --summary)

commit 1e0d1555e048c87b3031b16c0d6d780dc4038c7c
Author: Odile Marchand <odile.marchand@nlhm.example>
Date:   Sat Oct 17 11:05:00 2026 -0400

    Tidy repo: remove old notes

 delete mode 100644 staff-notes.txt
```
```text
(git show HASH~1:staff-notes.txt)

STAFF NOTES (internal, do not publish)

After-hours alarm codes
  2210  G. Lavoie (night security)
  3305  O. Marchand (curator)
  4471  W. Henderson (donor liaison; after-hours key issued in September, to be reviewed)

Reminder: change the Wi-Fi password before the winter gala.
```
```text
(git show archive/night-shift:security-log.txt)

NORTHERN LIGHTS HERITAGE MUSEUM  -  SECURITY EXPORT  -  NIGHT OF 14-15 OCT

18:30  Loading dock : courier delivery (M. Brisebois), supervised
18:45  Loading dock : door locked after delivery
21:58  Lobby        : G. Lavoie begins night shift
22:30  CCTV lobby   : Lavoie seen at front desk
23:12  East Wing    : badge 07 (P. Nandakumar) entry, approved inventory work
23:50  East Wing    : badge 07 exit
23:52  Main door    : badge 07 exits building
00:15  ALARM        : East Wing panel DISARMED with code 4471
00:19  Loading dock : door opened, no badge swipe
00:41  Loading dock : door closed
06:00  Lobby        : Lavoie finds Display Case 7 empty
```
```text
(grep -n "<!--" legacy/old-index.html)

    11:  <!-- Oct 16: an online auction listing for "a 1790s voyageur compass"
```
```text
(grep -n "/\*" legacy/old-style.css)
1:/* Old museum stylesheet. Replaced by the new site. */
11:/* Oct 12: W. Henderson asked for Display Case 7 to be moved
```
```text
(git log --oneline)

83df583 (HEAD -> main) Add images and starter stylesheet
1e0d155 Tidy repo: remove old notes
72f5d74 Add a note about the suspicious listing
0f7026f Move Display Case 7 styling note
23e8437 Add exhibit list
d8166b0 Start museum site
```
**My four clues** (what it says, and exactly where it is):

| # | What it says | Where (commit hash plus file, or file plus line) |
|---|---|---|
| 1 | Text from deleted staff notes | Commit 1e0d155~1, staff-notes.txt |
| 2 | Text from security log | Branch archive/night-shift, security-log.txt |
| 3 | HTML ccommit clue | legacy/old-index.html |
| 4 | CSS commit clue | legacy/old-style.css |

**Explain (what does `~1` mean, and why did I use it instead of the hash of the deleting commit itself?):**
~1 means the first parent of a commit, or the commit immediately before it in that branch's history. I used it because the file was deleted in the commit itself, so I needed to look at the previous commit where the file still existed.

```text
(git remote -v and git branch -vv)
  archive/night-shift 629628b Upload security log export
  feature/gold-accent 660ace9 Try a gold accent colour
* main                ffcbe95 Recover security log from archive branch
```
- Repository: https://github.com/Matt120056/voyageur-museum.git

**Checkpoint 1: output of git log --oneline | wc -l**
```text
(base) ➜  voyageur-museum git:(main) ✗ git log --oneline | wc -l
       8
```

## Mission 3: Home Page
```text
(git log --oneline, after my three commits)
14035ef (HEAD -> main, origin/main) Write alt text and validate index.html
be6679c Add welcome section, exhibit cards and visitor tips
c7165fd Added home page skeleton and landmarks
ffcbe95 Recover security log from archive branch
e128e3a Recover deleted staff notes as evidence
83df583 Add images and starter stylesheet
1e0d155 Tidy repo: remove old notes
72f5d74 Add a note about the suspicious listing
0f7026f Move Display Case 7 styling note
23e8437 Add exhibit list
d8166b0 Start museum site
```
Validator screenshot saved as `screenshots/index-validation.png`: yes / no
Yes

## Mission 4: Case File Page
```text
(the Duplicate ID error text from the "break it on purpose" test)
<input type="checkbox" id="reasoning" name="confirmEvidence" value="yes" required>
```
```text
(git log --oneline)
61f4538 (HEAD -> main, origin/main) Validate case-file.html with no errors
4fad239 Add timeline and report form
d455e9d Add case file page with suspects table
14035ef Write alt text and validate index.html
be6679c Add welcome section, exhibit cards and visitor tips
c7165fd Added home page skeleton and landmarks
ffcbe95 Recover security log from archive branch
e128e3a Recover deleted staff notes as evidence
83df583 Add images and starter stylesheet
1e0d155 Tidy repo: remove old notes
72f5d74 Add a note about the suspicious listing
0f7026f Move Display Case 7 styling note
23e8437 Add exhibit list
d8166b0 Start museum site
```
Validator screenshot saved as `screenshots/case-file-validation.png`: yes / no YES

**Explain (why does `placeholder` not replace a `label`?):** 
Label = What is this field for?
Placeholder = What could I enter here?

**Checkpoint 2: output of git log --oneline | wc -l**
```text
(base) ➜  voyageur-museum git:(main) ✗ git log --oneline | wc -l
      14
```

## Mission 5: Style the Basics
**What DevTools showed for the active link (which line was crossed out, and which rule won):**

**Specificity weights (IDs, classes, types):**

| Selector | Weight |
|---|---|
| `a` | |
| `nav a` | |
| `.active` | |
| `.btn:hover` | |
| `#welcome a` | |

## Mission 6: Flexbox and Grid
```css
(my nav and .showcase rules)
```
**Explain (what does `1fr` mean?):**

## Mission 7: Phone Test and Mobile-First
**What the page looked like without the viewport tag at 375px:**

**What happened to the page before I fixed the table:**

```css
(my @media queries and the .table-wrap rule)
```
Screenshots at 375px, 800px and 1280px saved in `screenshots/`: yes / no

**Explain (what does `min-width: 768px` mean?):**

## Mission 8: Variables, Classes and Contrast
```css
(my final :root block)
```
**What the CSS validator said (and whether any warning matters):**

- Issue #1: https://github.com/...

**The gold trap: ratio of white on #c9a227:**

**My contrast table:**

| Text colour | On | What it is | Ratio | Passes 4.5 : 1? |
|---|---|---|---|---|
| `#f3efe6` | `#0f1b2d` | Body text | | |
| `#e9c46a` | `#0f1b2d` | Gold heading on the page | | |
| `#e9c46a` | `#1b2a41` | Gold heading inside a card | | |
| `#ffffff` | `#a63d2f` | Button text | | |
| `#ffffff` | `#7d2c21` | Button text on hover | | |
| `#6b7a90` | `#1b2a41` | Photo caption on a card | | |

**Which pair failed, and does it count as large text?**

**Checkpoint 3: output of git log --oneline | wc -l**
```text
(paste)
```

## Mission 9: Git and GitHub Like a Team
```text
(the conflict block exactly as Git wrote it, with the markers, before I fixed it)
```
```css
(my resolved :root block)
```
```text
(git log --oneline --all --graph after the merge)
```
**Explain (what made these two changes conflict, and what did Git need from me?):**

- Issue #1 (now closed): https://github.com/...
- Merged Pull Request: https://github.com/...
- Release v1.0.0: https://github.com/...

**Explain (git pull is a shortcut for which two commands?):**

**Checkpoint 4: git log --oneline | wc -l  and  git log --oneline --all | wc -l**
```text
(paste)
```

## Mission 10: Case Report and Reflection
```text
(cat case-report.md)
```
```text
(git log --oneline | wc -l   and   git log --oneline --all | wc -l   and   git status)
```
1. **History:**
2. **My conflict:**
3. **Pick the right tool:** (a) ... (b) ... (c) ...
4. **The GitHub workflow:**
5. **One source of truth:**
6. **Beyond class:**

## Bonus (optional)
**The Git Detective (+3):**
```text
(git log -S4471 --all --oneline, and git blame output)
```
**The Live Site (+2):** https://...