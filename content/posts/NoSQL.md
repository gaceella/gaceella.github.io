
+++
date = '2025-07-01'
title = 'NoSQL(MongoDB)'
+++



# NoSQL (MongoDB)

> "NoSQL is not about throwing away SQL — it is about choosing the right tool for the right job."

## What is NoSQL?

NoSQL stands for "Not Only SQL".  
It is a type of database system that is different from traditional SQL databases. NoSQL does not store data in rows and columns (tables). Instead, it stores data in a more flexible and modern way such as documents, key-value pairs, graphs, or wide-column formats.  
NoSQL databases are especially useful when working with large, complex, or changing data.

## What is the Difference Between NoSQL and SQL?

| SQL | NoSQL |
|-----|-------|
| Stores data in tables (rows/columns) | Stores data in flexible formats (like documents) |
| Uses a fixed schema | Uses a dynamic schema (no need to predefine) |
| Good for structured data | Good for unstructured or semi-structured data |
| Best for relational data | Best for fast, flexible, large-scale data |
| Uses SQL language to query data | Uses different query methods depending on the NoSQL type |

## Why Do We Use NoSQL?

We use NoSQL because:

- It is more flexible and can handle many types of data.
- It works better for big data, real-time apps, and cloud systems.
- It is faster and easier to scale when your data grows.
- It helps in modern applications like social media, online stores, chat apps, etc.

## Advantages of NoSQL

- **Flexible Data Storage**: No fixed structure, so you can store data in any format.
- **Scalable**: Easily handles huge amounts of data and traffic.
- **Fast Performance**: Very quick to read/write data, especially in real-time apps.
- **Handles Complex Data**: Can store varied and large-size data like documents or media.
- **Easy to Update**: No need to redesign the whole database when structure changes.

## Disadvantages of NoSQL

- **Less Structured**: Not suitable for data with complex relationships like banking.
- **No Standard Language**: Unlike SQL, every NoSQL system has its own syntax.
- **Data Consistency**: May not be as strong as SQL in ensuring consistent data.
- **Less Support for Transactions**: Not ideal for apps that need secure, step-by-step operations.

## Best Platforms Used for NoSQL

- **MongoDB** (most popular)
- Redis (for key-value data)
- Cassandra (for wide-column data)
- Neo4j (for graph data)
- CouchDB, Firebase, DynamoDB (by Amazon)

## What is MongoDB?

MongoDB is a document-based NoSQL database.

- It stores data in a flexible document format, usually using JSON-like structures.
- MongoDB is widely used in modern web and mobile apps, and it's known for speed, simplicity, and scalability.

MongoDB is a real-world example of how NoSQL databases work and why they are powerful in modern development.

## Example: Using MongoDB

### Step 1: Install MongoDB (Ubuntu example)

Install MongoDB packages:

```bash
curl -fsSL https://pgp.mongodb.com/server-7.0.asc | \
sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg --dearmor
```

```bash
echo "deb [ signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | \
sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
```

Install MongoDB:

```bash
sudo apt update
sudo apt install -y mongodb-org
```

Start MongoDB:

```bash
sudo systemctl start mongodb
```

### Step 2: Enable MongoDB to start on boot

```bash
sudo systemctl enable mongod
```

### Step 3: Check MongoDB status

```bash
sudo systemctl status mongod
```

### Step 4: Start the MongoDB shell

```bash
mongosh
```

### Step 5: Create a database

```javascript
use chatapp
```

Explanation:

- `use chatapp`: This switches to (or creates) a database called `chatapp`

### Step 6: Insert a chat message

```javascript
db.messages.insertOne({
  from: "Ayesha",
  to: "Ali",
  message: "Hello Ali!",
  time: "2025-06-01 10:00"
})
```

Explanation:

- `db`: Refers to the current database (`chatapp`)
- `messages`: This is a collection (like a table)
- `insertOne({})`: Adds one new document (record) to the collection

### Step 7: Display stored messages

```javascript
db.messages.find().pretty()
```

Explanation:

- `find()`: Find and show all the documents (messages)
- `pretty()`: Format the result in a readable way

### Step 8: Exit MongoDB shell

```bash
exit
```

## Conclusion

MongoDB is a great tool because it stores data in a flexible, easy-to-understand way like JSON. It works really well with big amounts of data and lets developers build apps faster. If you want a smart and modern way to manage data, MongoDB is a strong choice.

> "MongoDB lets your data grow with your ideas — fast, flexible, and ready for anything."

**THANK YOU!**