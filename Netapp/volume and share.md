| Task              | Command                                                                          |
| ----------------- | -------------------------------------------------------------------------------- |
| Create volume     | `volume create -vserver svm1 -volume vol_data -aggregate aggr1 -size 100GB`      |
| Mount volume      | `volume mount -vserver svm1 -volume vol_data -junction-path /vol_data`           |
| Create CIFS share | `vserver cifs share create -vserver svm1 -share-name data_share -path /vol_data` |
