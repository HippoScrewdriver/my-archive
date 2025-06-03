
## 🧭 Git Branch Tracking: `--set-upstream-to`

### 🎯 What Does `--set-upstream-to` Do?

It sets a **correspondence** (upstream tracking) between:
- A **local branch**
- And a **remote branch**, possibly with a different name

---

## 🧱 Default Setup via Push

### 🔹 The usual way to create tracking:
```bash
git push -u origin my-feature
```

This:
- Pushes `my-feature` to `origin`
- Sets `origin/my-feature` as upstream for local `my-feature`

🧠 Useful when you’re pushing **for the first time**

---

## 🔧 Manual Setup with `--set-upstream-to`

If branches already exist but aren't linked:

### ✅ Example 1: Same name
```bash
git checkout my-feature
git branch --set-upstream-to=origin/my-feature
```

### ✅ Example 2: Different names
```bash
git checkout ui-redesign
git branch --set-upstream-to=origin/frontend-overhaul
```

🔁 Now `ui-redesign` (local) tracks `origin/frontend-overhaul` (remote)

---

## 🧪 Checking the Setup

```bash
git status
```
> `Your branch is up to date with 'origin/frontend-overhaul'.`

```bash
git branch -vv
```
> Shows all branches and tracking info

---

## 🔄 Summary Table

| Use case                              | Command                                                           |
|---------------------------------------|--------------------------------------------------------------------|
| First push and track                  | `git push -u origin branch-name`                                   |
| Already pushed; set tracking manually | `git branch -u origin/remote-name local-branch` *(in checkout)*    |
| Rename local but track remote         | `git branch -u origin/remote-name` *(while on local)*              |

---

## 🔥 Pro Tip: You *don’t* need names to match

| Local Branch     | Remote Branch          | Works? |
|------------------|------------------------|--------|
| `dev`            | `origin/development`   | ✅     |
| `my-feature`     | `origin/feature-v2`    | ✅     |

Just connect them explicitly.
