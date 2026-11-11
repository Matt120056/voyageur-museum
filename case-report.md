# Case Report: The Case of the Vanishing Voyageur Compass

## 1. The Culprit

Walt Henderson (W. Henderson), the museum's donor liaison, is responsible for the disappearance of the Voyageur Compass.

## 2. Evidence

**Evidence 1 — After-hours alarm code**

The internal staff notes identify alarm code `4471` as belonging to W. Henderson and mention that he received an after-hours key in September.

Location: Commit `e128e3a`, file `staff-notes.txt`.

**Evidence 2 — Security alarm and loading dock activity**

The security log records that the East Wing alarm was disarmed at 00:15 using code `4471`. Four minutes later, the loading dock door was opened without a badge swipe.

Location: Commit `ffcbe95`, file `security-log.txt`.

**Evidence 3 — Suspicious auction listing**

A comment on the old museum website mentions an online auction listing for a 1790s voyageur compass. The seller account is named "WH Antiquities", which connects to Walt Henderson's initials.

Location: Commit `72f5d74`, file `legacy/old-index.html`, lines 11–12.

## 3. Means, Motive and Opportunity

**Means:** Henderson had an after-hours key and access to alarm code 4471, which was used to disarm the East Wing alarm.

**Motive:** The suspicious auction listing for a voyageur compass under the seller name "WH Antiquities" suggests a possible financial motive.

**Opportunity:** The alarm was disarmed at 00:15 and the loading dock door opened at 00:19 without a badge swipe, providing an opportunity to remove the compass.

## 4. Other Suspects Cleared

**Gaston Lavoie:** The security log shows Lavoie at the front desk at 22:30, and the alarm was disarmed using Henderson's code rather than Lavoie's assigned code.

**Priya Nandakumar:** The security log records Priya leaving the East Wing at 23:50 and exiting the building at 23:52, before the alarm was disarmed.

**Marcel Brisebois:** The security log records Marcel's courier delivery as supervised at 18:30 and confirms the loading dock door was locked at 18:45.

## 5. Reflection

**1. History:**

I was surprised that Git remembered files and changes even after they were removed from the working project. In a real job, I could use Git history to recover deleted files, investigate an earlier version of a website, or find out who introduced a problem.

**2. My conflict:**

Git needed me to decide which changes to keep because both branches had modified the same section of `styles.css`. I reviewed both versions, kept my accessible colour palette, removed the conflict markers, and committed the resolved file.

**3. Pick the right tool:**

(a) I would use responsive CSS and media queries to fix a page that scrolls sideways on a phone.

(b) I would use a colour contrast checker and adjust the CSS text or background colour to make a button easier to read.

(c) I would use the W3C Markup Validator to find HTML errors and correct the typo.

**4. The GitHub workflow:**

Using an Issue, branch, and Pull Request keeps even a small change organized and makes it easier to review what was changed. The Issue describes the problem, the branch isolates the fix, and the Pull Request allows the change to be reviewed before merging. The `Closes #1` reference automatically closed Issue #1 when the Pull Request was merged.

**5. One source of truth:**

The `:root` CSS variables allowed me to change the colours in one place and have those changes apply to both HTML pages. If I had typed individual colour values into every CSS rule, updating the theme would have taken longer and could have resulted in inconsistent colours.

**6. Beyond class:**

I could use this workflow when developing my Guidance counselor toolkit. I would create Issues for bugs and new features, use separate branches for changes, and review Pull Requests before merging. I would also add automated tests and more frequent code reviews to catch problems earlier.