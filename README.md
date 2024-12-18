# MongoDB Backup and Restore Guide (Mac)

## Preparation
Before starting, ensure you have the following:
- **MongoDB Credentials**: `<username>`, `<password>`, and `<clusterId>`.
- **Folder Path**: The directory where you want to save the backup.

## How to Copy Folder Path on Mac
1. Navigate to the folder in Finder.
2. Press and hold the `<Control>` button.
3. Click on the folder to open a dialog menu.
4. Press and hold the `<Option>` button.
5. From the dialog, select **Copy "folder" as Pathname**.

## Steps to Take a MongoDB Backup on Mac

### 1. Install Homebrew or Update It
Ensure Homebrew is installed and up-to-date:
```bash
brew update
```

### 2. Install MongoDB Tools
Install the MongoDB database tools for backup and restore:
```bash
brew tap mongodb/brew
brew install mongodb-database-tools
```

Verify the installation by checking the version:
```bash
mongodump --version
```

### 3. Install MongoDB Shell (mongosh)
Install the MongoDB shell for connecting to your database:
```bash
brew install mongosh
```

Check the installed version:
```bash
mongosh --version
```

### 4. Test Your MongoDB Connection
Test the connection to your MongoDB Atlas cluster:
```bash
mongosh "mongodb+srv://<username>:<password>@<clusterId>.mongodb.net/<database>"
```
- Replace `<username>` and `<password>` with your MongoDB Atlas credentials.
- Replace `<clusterId>` with your cluster's ID.
- Replace `<database>` with the name of your database.

### 5. Disconnect the Connection
Once tested, close your terminal or disconnect the session.

### 6. Take a Backup
Run the following command to back up your database:
```bash
mongodump --uri="mongodb+srv://<username>:<password>@<clusterId>.mongodb.net/<database>" --out=<backup-directory>
```
- Replace `<backup-directory>` with the folder path where you want to store the backup.
- Replace `<username>`, `<password>`, `<clusterId>`, and `<database>` with the appropriate values from MongoDB Atlas.

### Example Command
```bash
mongodump --uri="mongodb+srv://admin:password@cluster0.mongodb.net/inventoryDB" --out=/Users/username/backups/mongo-backup
```

## Restoring the Backup (if needed)
If you need to restore the database, use the following command:
```bash
mongorestore --uri="mongodb+srv://<username>:<password>@<clusterId>.mongodb.net/<database>" <backup-directory>
```
- Replace `<backup-directory>` with the folder path where the backup is stored.
- Replace `<username>`, `<password>`, `<clusterId>`, and `<database>` with the appropriate values.

### Example Command
```bash
mongorestore --uri="mongodb+srv://admin:password@cluster0.mongodb.net/inventoryDB" /Users/username/backups/mongo-backup
```

