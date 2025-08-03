![Platform](https://img.shields.io/badge/KWGT%20v.3.79b51413-green)
![Device](https://img.shields.io/badge/moto%20G85-blue)
![System](https://img.shields.io/badge/Android%2015-blueviolet)



# KWGT – Missing Globals – workaround using “Shared” variables

## Introduction

This guide is intended for KWGT users who are missing the ability to add global variables (Globals) in the editor. This issue may appear on some phones running Android 15 (e.g., Motorola Moto G85). The following workaround allows you to effectively use “Shared” variables as a replacement.

---

## What are Globals?

Global variables (GV) in KWGT are user-defined values (e.g., color, text, number) that can be used across the entire widget. They allow centralized control over the widget's appearance and behavior.

## The Problem

On some devices, the **Globals** tab is not visible at all in the KWGT editor.

## The Workaround

An alternative is to use the **Shared** tab, where you can create so-called **Shared Globals**. However, these only work **within the current widget**, not across multiple ones.

### Tip

Create a template (an empty widget with all your needed Shared variables) and use it as a starting point for each new widget.

---

## How to Create a Text Variable

1. Open a new widget
2. Go to the `Shared` tab
3. Tap the `+` icon and set:
   - **Title:** `ram perc`
   - **Type:** `text`
   - **Description:** `RAM in percent`
4. Open the menu (three dots) and select `Formula`
5. Enter the formula:

```
$mu(round, (rm(mused)*100)/rm(mtot))$
```

6. Confirm by tapping the checkmark.

---

## How to Use the Variable in Text

1. In the `Items` tab, add a new `Text` element
2. In the formula field, enter:

```
Ram used: $gv(ram perc)$ %
```

The result will display something like:

```
Ram used: 58 %
```

---

## More Examples

### RAM Size in GB

```
Total:   $mu(round, (rm(mtot)/1000), 1)$
Free:    $mu(round, (rm(mfree)/1000), 1)$
Used:    $mu(round, (rm(mused)/1000), 1)$
```

### Internal Storage in GB

```
Total:   $mu(round, (rm(fstot)/1000), 0)$
Free:    $mu(round, (rm(fsfree)/1000), 0)$
Used:    $mu(round, (rm(fsused)/1000), 0)$
```

### Used Storage Percentage (for progress bar):

```
$mu(round, (rm(fsused, int)*100)/rm(fstot, int))$
```

---

## Conclusion

This method allows you to replace missing Globals functionality and continue customizing your widgets in KWGT.
Hopefully, it saves you time and effort if you run into the same issue.

© 2025 n4zz


