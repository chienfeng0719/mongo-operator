# mongo-operator
**A package for backup or cleanup mongodb.**


## Description:
A tool for backup and cleanup mongo.

This package can make you backup or cleanup mongo more earlier with python3.
## initial testing data
1. download `https://github.com/chienfeng0719/mongo-operator/tree/develop/mongo_init`
2. run command `mongo-operator -r mongo_init`

## How To Use:

You can use mongo-operator through command line for backup/restore/drop database as the following example:
### CLI
```
mongo-operator -b foo_bar -> backup foo_bar
mongo-operator -d foo_bar -> drop foo_bar
mongo-operator -r mongo_init -> restore data from mongo_init folder
```
---
You can also do some advanced operate with python:
### Backup
```python
from mongo_operator import BackupOperator

# init object
backup_operator = BackupOperator(hostname='localhost', port=27017, username='root', password='root')

# backup all database
backup_operator.backup(folder_path='./backup/')

# backup specific collection
backup_operator.backup(db_name='foo_bar', collection='foo_bar')

# backup specific collection with query
backup_operator.backup(db_name='foo_bar', collection='foo_bar', query_={'items': 'phone'})

# restore data from backup
backup_operator.restore(folder_path='./backup/', is_dropped=True)
```

### Cleanup
```python
from mongo_operator import CleanupOperator

# init object
cleanup_operator = CleanupOperator(hostname='localhost', port=27017, username='root', password='root')

# drop 'foo_bar' table in foo_bar
cleanup_operator.drop_collection(db_name='foo_bar', collection='foo_bar')

# drop foo_bar database
cleanup_operator.drop_db(db_name='foo_bar')
```
