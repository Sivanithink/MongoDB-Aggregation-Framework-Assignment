# MongoDB Aggregation - Easy Difficulty

## 1. List All Products in the "Electronics" Category

- **Task:** Write an aggregation query to find all documents where the category is `"Electronics"`.
- **Hint:** Use the `$match` stage.
- **Expected Output (structure, `_id` will vary):**

### 🔹 Command:
```js
db.products.aggregate([
  {
    $match: { category: "Electronics" }
  }
]);
{
  _id: ObjectId('683839e622f6a1f56dd6e4f0'),
  name: 'Laptop Pro',
  category: 'Electronics',
  price: 1200,
  quantity: 10,
  tags: ['computer', 'portable', 'work'],
  date_added: ISODate('2023-01-15T10:00:00Z'),
  supplier: { name: 'TechGlobe', location: 'USA' }
}
{
  _id: ObjectId('683839e622f6a1f56dd6e4f1'),
  name: 'Wireless Mouse',
  category: 'Electronics',
  price: 25,
  quantity: 100,
  tags: ['peripheral', 'computer', 'wireless'],
  date_added: ISODate('2023-02-01T11:30:00Z'),
  supplier: { name: 'GadgetPro', location: 'China' }
}
{
  _id: ObjectId('683839e622f6a1f56dd6e4f2'),
  name: 'Mechanical Keyboard',
  category: 'Electronics',
  price: 75,
  quantity: 50,
  tags: ['peripheral', 'computer', 'mechanical'],
  date_added: ISODate('2023-01-20T14:00:00Z'),
  supplier: { name: 'TechGlobe', location: 'USA' }
}
{
  _id: ObjectId('683839e622f6a1f56dd6e4f6'),
  name: 'Smartwatch',
  category: 'Electronics',
  price: 199,
  quantity: 25,
  tags: ['wearable', 'gadget', 'portable'],
  date_added: ISODate('2023-04-01T12:00:00Z'),
  supplier: { name: 'GadgetPro', location: 'China' }
}



## 2. Count Products per Category

- **Task:** Write an aggregation query to count how many products belong to each category.
- **Hint:** Use the `$group` stage with the `$sum` accumulator.
- **Expected Output (order might vary):**

###  🔹 Command:
```js
db.products.aggregate([
  {
    $group: {
      _id: "$category",
      totalProducts: { $sum: 1 }
    }
  }
]);

