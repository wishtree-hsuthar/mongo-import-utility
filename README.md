# MongoDB Import 

**Follow below given steps to import master data into the MongoDB using a single command.*

---

### Steps
1. Create `JSON` files per collection which contains all your records
2. Create a `.sh` file with an arbitary name
3. Write the `mongoimport` query for all collections using the JSON files
   - The number of `mongoimport` commands in this file depends upon the total number of collections
4. Execute `sh <file-name>.sh` in the terminal to import all master records 

---

### Demo
1. Clone this repository
2. Open the terminal in the cloned directory
3. Execute `sh import_masters.json`

---

***roles.json***

```
[
    {
        "name": "Super Admin",
        "description": "Super Admin Role",
        "isActive": true,
        "isDeleted": false,
        "createdAt": "2023-04-06T13:26:17.639Z",
        "privileges": {
            "users": ["ALL"],
            "roles": ["ALL"]
        }
    },
    ...
]
```

***countries.json***

```
[
    {
        "name": "Anguilla",
        "countryCode": "+1264",
        "region": "Americas",
        "subRegion": "Caribbean",
        "initial": "AIA",
        "flag": "🇦🇮",
        "states": []
    },
    ...
]
```

***mongo_import.sh***
```
# Eg. mongoimport --db <database-name> --collection <collection-name> --file <file-path> --jsonArray

mongoimport --db cgf_hrdd --collection roles --file roles.json --jsonArray
mongoimport --db cgf_hrdd --collection countries --file countries.json --jsonArray
```

**Execute command -** ```sh mongo_import.sh```

---

#### Note:
- Your json file's content should be an array containing multiple objects/documents.
- Executing the same shellscript for multiple times will append the new records insteading or rewriting
