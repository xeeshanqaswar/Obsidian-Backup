
## Normal Build

For every normal build, the generated `Catalog.json` and `addressables.bin` files are stored inside the `BundleRecords` folder, organized by:

- **Build Environment**
- **Build Version**
- **Build Code**

### Example

Run the following command to create a normal build:

```
/buildios 1.4.2 39 dev-true-incremental $Branch_Name
```

This will generate the following folder structure:

```
BundleRecords
 └── dev
     └── 1.4.2
         └── 39
             ├── catalog.json
             └── addressables.bin
```

---

## Incremental Build

To create an incremental build, use the **same Build Version and Build Code** as the existing build and include the `incremental` flag.

### Example Command

```
/buildios 1.4.2 39 dev-true-incremental $Branch_Name
```

The build process will use the existing build records associated with:

```
Build Version: 1.4.2
Build Code: 39
```

and generate the incremental update.

**Note:** `Catalog.json` and `addressables.bin` files are currently stored locally.

