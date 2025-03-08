# IndexedDB BoilerPlate

Easiest way to get started with indexedDB.

## Indexed DB Visualizer

```bash
                                              dbName
                                                |
          --------------------------------------------------------------------------
          |                         |                      |                       |
      ObjectStore              ObjectStore            ObjectStore             ObjectStore
          |                         |                      |                       |
  _________________         _________________       _________________       _________________
  | key |  value  |         | key |  value  |       | key |  value  |       | key |  value  |
  -----------------         -----------------       -----------------       -----------------
  | 0   |  val 0  |         | 0   |  val 0  |       | 0   |  val 0  |       | 0   |  val 0  |
  -----------------         -----------------       -----------------       -----------------
  | 1   |  val 1  |         | 1   |  val 1  |       | 1   |  val 1  |       | 1   |  val 1  |
  -----------------         -----------------       -----------------       -----------------
  | 2   |  val 2  |         | 2   |  val 2  |       | 2   |  val 2  |       | 2   |  val 2  |
  -----------------         -----------------       -----------------       -----------------
  | 3   |  val 3  |         | 3   |  val 3  |       | 3   |  val 3  |       | 3   |  val 3  |
  -----------------         -----------------       -----------------       -----------------
```

### Analogy

  1. Think of indexedDB as a director or folder and named it "projects" (dbName).

  2. Inside our root, we have first level files, and that would be our (ObjectStore or Table in SQL).
      - Objectstore or a Table contains COLUMNS and ROWS.

  3. A COLUMN is a key-value pair inside a record.

  4. A ROW is a single piece of data. See the table above starting at 2nd row.
      - You can see 2nd row.
          - first column of 2nd row is "key" and the value is "0"
          - second column of 2nd row is "value" and the value is "val 0"

### Methods

createObjectStore:
> Implementation:
  ```javascript
    // Create object store
    let store = db.createObjectStore("users", { keyPath: "id" });
  ```
> Pre-requisite: browser supports window.indexedDB
------------------------------------------------------------------------
createIndex:
> Implementation:
  ```javascript
    // Create object store
    let store = db.createObjectStore("users", { keyPath: "id" });

    // Create an index on "email" field
    store.createIndex("emailIndex", "email", { unique: true });
  ```

> Sample in JSON Terms:
  ```json
    objectstore: {
      "emailIndex": {
        "alice@example.com": 1,
        "bob@example.com": 2
      }
    };
  ```

> Takeaway: In layman's term is it creates a new object inside object store.
> Pre-requisite: objectStore
