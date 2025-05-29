Easy Difficulty
1. List All Products in the "Electronics" Category:
•	Task: Write an aggregation query to find all documents where the category is "Electronics".
•	Hint: Use the $match stage.
•	Expected Output (structure, _id will vary):
Command:

db.products.aggregate([
  {
    $match: { category: "Electronics" }
  }
]);

gives records which has category as Electronics
 
 
{
  _id: ObjectId('683839e622f6a1f56dd6e4f0'),
  name: 'Laptop Pro',
  category: 'Electronics',
  price: 1200,
  quantity: 10,
  tags: [
    'computer',
    'portable',
    'work'
  ],
  date_added: 2023-01-15T10:00:00.000Z,
  supplier: {
    name: 'TechGlobe',
    location: 'USA'
  }
}
{
  _id: ObjectId('683839e622f6a1f56dd6e4f1'),
  name: 'Wireless Mouse',
  category: 'Electronics',
  price: 25,
  quantity: 100,
  tags: [
    'peripheral',
    'computer',
    'wireless'
  ],
  date_added: 2023-02-01T11:30:00.000Z,
  supplier: {
    name: 'GadgetPro',
    location: 'China'
  }
}
{
  _id: ObjectId('683839e622f6a1f56dd6e4f2'),
  name: 'Mechanical Keyboard',
  category: 'Electronics',
  price: 75,
  quantity: 50,
  tags: [
    'peripheral',
    'computer',
    'mechanical'
  ],
  date_added: 2023-01-20T14:00:00.000Z,
  supplier: {
    name: 'TechGlobe',
    location: 'USA'
  }
}
{
  _id: ObjectId('683839e622f6a1f56dd6e4f6'),
  name: 'Smartwatch',
  category: 'Electronics',
  price: 199,
  quantity: 25,
  tags: [
    'wearable',
    'gadget',
    'portable'
  ],
  date_added: 2023-04-01T12:00:00.000Z,
  supplier: {
    name: 'GadgetPro',
    location: 'China'
  }
}
{
  _id: ObjectId('683839e622f6a1f56dd6e4f6'),
  name: 'Smartwatch',
  category: 'Electronics',
  price: 199,
  quantity: 25,
  tags: [
    'wearable',
    'gadget',
    'portable'
  ],
  date_added: 2023-04-01T12:00:00.000Z,
  supplier: {
    name: 'GadgetPro',
    location: 'China'
  }
}
2. Count Products per Category:
•	Task: Write an aggregation query to count how many products belong to each category.
•	Hint: Use the $group stage with the $sum accumulator.
Command
db.products.aggregate([
  {
    $group: {
      _id: "$category",          
      totalProducts: { $sum: 1 }     }
  }
]);


 
we get no.of field for each categories

{
  _id: 'Sports',
  totalProducts: 1
}
{
  _id: 'Electronics',
  totalProducts: 5
}
{
  _id: 'Accessories',
  totalProducts: 1
}
{
  _id: 'Apparel',
  totalProducts: 2
}
{
  _id: 'Home Goods',
  totalProducts: 1
}






3. Product Names and Prices, Sorted by Price (Descending):
•	Task: Write an aggregation query to display only the name and price of each product, sorted by price from highest to lowest. Do not include the _id field.
•	Hint: Use $project and $sort.
Command
db.products.aggregate([
  {
    $project: {
      _id: 0,      
      name: 1,     
      price: 1     
    }
  },
  {
    $sort: { price: -1 }  
  }
]);


{
  name: 'Laptop Pro',
  price: 1200
}
{
  name: 'Espresso Machine',
  price: 250
}
{
  name: 'Smartwatch',
  price: 199
}
{
  name: 'Bluetooth Speaker',
  price: 80
}

{
  name: 'Mechanical Keyboard',
  price: 75
}
{
  name: 'Denim Jeans',
  price: 60
}
{
  name: 'Leather Wallet',
  price: 45
}
{
  name: 'Yoga Mat',
  price: 30
}
{
  name: 'Wireless Mouse',
  price: 25
}
{
  name: 'Cotton T-Shirt',
  price: 20
}
