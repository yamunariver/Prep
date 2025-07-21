Sure! Let’s do this practically:

Here are the **NetApp ONTAP CLI commands** you can run to check **whether SnapMirror is configured** and what volumes / LUNs / relationships exist — directly on your NetApp system.

---

## ✅ **Step 1: Check if SnapMirror is licensed and running**

```bash
system license show | grep -i snapmirror
```

If you see `snapmirror` in the output → licensed.

Check SnapMirror status:

```bash
snapmirror show
```

---

## ✅ **Step 2: List all SnapMirror relationships**

```bash
snapmirror show
```

Example output:

```
Source Path                   Destination Path             Status       Policy Type
----------------------------  --------------------------- ----------   -----------
SVM_internet:vol_external     SVM_intranet:vol_internal    Snapmirrored XDP
```

If you see something here → SnapMirror is configured.

---

## ✅ **Step 3: Find destination volumes / their type**

SnapMirror creates destination volumes with type `DP` (data protection).

```bash
volume show -vserver SVM_intranet -type DP
```

Example:

```
Vserver        Volume          Aggregate    State      Type
-------------- --------------- ----------- ---------- -----
SVM_intranet   vol_internal    aggr_intra   online     DP
```

---

## ✅ **Step 4: Check which LUNs exist in these volumes**

```bash
lun show -vserver SVM_intranet
```

---

## ✅ **Step 5: Check if LUN is mapped to a server (igroup)**

```bash
lun mapping show -vserver SVM_intranet
```

If you see the destination LUN mapped to an igroup → your server might be mounting the SnapMirror destination (which is risky).

---

## ✅ **Step 6: Find FlexClone volumes (if created)**

```bash
volume show -volume *clone*
```

Cloned volumes usually have `clone` in the name.

---

## 🧰 **Quick checklist:**

|                   What |                       Command |                      |
| ---------------------: | ----------------------------: | -------------------- |
|              Licensed? |         \`system license show | grep -i snapmirror\` |
|        Show SnapMirror |             `snapmirror show` |                      |
|        Find DP volumes |        `volume show -type DP` |                      |
|              Show LUNs |                    `lun show` |                      |
|      Show LUN mappings |            `lun mapping show` |                      |
| Find FlexClone volumes | `volume show -volume *clone*` |                      |

---

## 🚀 **If you'd like next:**

✅ I can help you **interpret your output**:

> Copy-paste the output here → I’ll explain what’s configured.

Just say:

> **"here’s my output – what does it mean?"**

Ready when you are!
