<ins>**Transactions:**</ins>

The transaction is the group of sql operations treated as the single unit of work.

- All operations are succeed - apply changes to the DB using  COMMIT
- Any Operation fail - cancel all the changes using ROLLBACK;

&nbsp;

If any operation like in the banking systems or any other application which needs consistency of the database.

for example if Charan send money to Uday;

There should be Two operations, one is deducting money from charan and updating money for uday, this should happens simultaneously.

so to ensure that if both operation succeeds it commits  to the database and make changes, if not all operation succeeded it rollbacks and not allow the operations to complete it will undo all the changes.

example:

`update accounts set balance = balance-500 where name = 'charan';`

`update accounts set balance = balance+500 where name = 'uday';`

This are the two operations needed to be perform simultaneously.

So to perform the Complete Transaction the syntax is:

BEGIN;

`SQL queries`

COMMIT;

<ins>if any operation fails just rollback;</ins>

BEGIN;

`SQL queries`

ROLLBACK;

&nbsp;

we can't use the both COMMIT and ROLLBACK; cause once it is committed there is nothing to rollback, and if it rollback then there is no transaction is performed to commit.

in backend we use like try and catch block to apply commit and rollback;

```python
from sqlalchemy.orm import Session

def transfer_money(db: session):
    
    try:
        charan = db.query(Account).filter(Account.name == 'charan').first()
        
        uday = db.query(Account).filter(Account.name == 'uday').first()
        
        charan.balance -= 500
        uday.balance += 500
        
        db.commit()
        
        print("Transaction Successful")
        
    except Exception as e:
    
        db.rollback()
        
        print(f"Transaction Error {str(e)}")
        
        
    
```

&nbsp;