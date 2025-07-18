Absolutely! Here’s a **clear ASCII diagram** showing:
✅ Your **MetroCluster** design with:

* 2 sites (Site A & Site B)
* NetApp controllers with 2 SVMs each (vs1 and vs2)
* Backend fabrics (4 Brocade FC switches)
* Frontend fabrics (for server access): Site A → 2 Brocade + 2 EMC; Site B → 4 EMC
  ✅ Which physical FC ports / adapters on the NetApp nodes are used by each SVM

---

## 🖼 **ASCII diagram:**

```
============================  SITE A  ============================

         NetApp MetroCluster controllers (Node A1 and Node A2)
         +--------------------------------------------+
         | Node A1              Node A2               |
         |                                            |
         | +-------+            +-------+             |
         | | SVM1  |            | SVM1  |             |
         | | vs1_0a|            | vs1_0b|             |
         | | (0a)  |            | (0b)  |             |
         | +-------+            +-------+             |
         |                                            |
         | +-------+            +-------+             |
         | | SVM2  |            | SVM2  |             |
         | | vs2_0c|            | vs2_0d|             |
         | | (0c)  |            | (0d)  |             |
         | +-------+            +-------+             |
         +--------------------------------------------+

            |         |           |         |
            |         |           |         |
            v         v           v         v

-------------------- FRONTEND FABRICS (servers) ------------------

        +------------+ +------------+ +------------+ +------------+
        | Brocade 5  | | Brocade 6  | | EMC 7      | | EMC 8      |
        +------------+ +------------+ +------------+ +------------+
              |              |              |              |
              +-----+--------+--------------+--------------+
                    | 
             Servers with dual/quad FC HBAs
                    |
                    v
      Servers see SVM1 and/or SVM2 LIFs as targets for LUNs

============================================================

============================  SITE B  ============================

         NetApp MetroCluster controllers (Node B1 and Node B2)
         +--------------------------------------------+
         | Node B1              Node B2               |
         |                                            |
         | +-------+            +-------+             |
         | | SVM1  |            | SVM1  |             |
         | | vs1_0a|            | vs1_0b|             |
         | +-------+            +-------+             |
         |                                            |
         | +-------+            +-------+             |
         | | SVM2  |            | SVM2  |             |
         | | vs2_0c|            | vs2_0d|             |
         | +-------+            +-------+             |
         +--------------------------------------------+

            |         |           |         |
            |         |           |         |
            v         v           v         v

-------------------- FRONTEND FABRICS (servers) ------------------

        +------------+ +------------+ +------------+ +------------+
        | EMC 1      | | EMC 2      | | EMC 3      | | EMC 4      |
        +------------+ +------------+ +------------+ +------------+
              |              |              |              |
              +-----+--------+--------------+--------------+
                    |
             Servers see SVM1 and/or SVM2 LIFs as targets for LUNs

============================================================


================= MetroCluster BACKEND FABRICS ===================

+---------------------+                   +---------------------+
| Brocade backend A1  |===================| Brocade backend B1  |
+---------------------+        ISL        +---------------------+

+---------------------+                   +---------------------+
| Brocade backend A2  |===================| Brocade backend B2  |
+---------------------+        ISL        +---------------------+

These carry only:
- MetroCluster mirroring
- Disk shelf connections (via FC-to-SAS bridges if needed)
- NO servers connect here

============================================================
```

---

## ✅ **Explanation:**

* Each SVM has its own LIFs placed on physical adapters:

  * vs1\_0a, vs1\_0b (SVM1)
  * vs2\_0c, vs2\_0d (SVM2)
* Each LIF = unique WWPN, appears as FC target to servers
* Frontend fabrics (Brocade & EMC FC switches) provide multipath, redundancy
* MetroCluster backend fabrics are separate, only carry mirroring & shelf traffic

---

## 🚀 **If you'd like next:**

✅ Full zoning script for:

* SVM1 & SVM2 LIFs
* Server HBAs
* On both Brocade & EMC switches

Just say:

> **"yes, share zoning script for 2 SVMs"**

Want me to?
