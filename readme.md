#Explorer Mode

How many users are there?
- **50**
- `SELECT COUNT(*) FROM users;`

---

What are the 5 most expensive items?
- **Small Cotton Gloves**
- **Small Wooden Computer**
- **Awesome Granite Pants**
- **Sleek Wooden Hat**
- **Ergonomic Steel Car**
- `SELECT title FROM items ORDER BY price DESC LIMIT 5;`

---

What's the cheapest book? (Does that change for "category is exactly 'book'" versus "category contains 'book'"?)
- **Ergonomic Granite Chair**
- `SELECT title FROM items WHERE category LIKE '%book%' ORDER BY price;`
- **No**
- `SELECT title FROM items WHERE category = 'Books' ORDER BY price;`

---

Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?
- **Corrine Little**
- `SELECT users.first_name, users.last_name, addresses.street FROM users INNER JOIN addresses WHERE users.id = addresses.user_id AND addresses.street = '6439 Zetta Hills';`
- **Yes, 54369 Wolff Forges, Lake Bryon, CA**
- `SELECT addresses.street, addresses.city, addresses.state FROM users INNER JOIN addresses WHERE users.id = addresses.user_id AND users.first_name = 'Corrine' AND users.last_name = 'Little';`

---

Correct Virginie Mitchell's address to "New York, NY, 10108".
- `UPDATE addresses SET city = 'New York', zip = '10108' WHERE state = 'NY' AND user_id IN (SELECT id FROM users WHERE first_name = 'Virginie' AND last_name = 'Mitchell');`

---

How much would it cost to buy one of each tool?
- **$46,477**
- `SELECT SUM(price) FROM items WHERE category LIKE '%tools%';`

---

How many total items did we sell?
- **2125**
- `SELECT SUM(quantity) FROM orders;`

---

How much was spent on books?
- **$1,081,352**
- `SELECT SUM(items.price * orders.quantity) FROM items INNER JOIN orders WHERE items.id = orders.item_id AND items.category LIKE '%book%';`

---

Simulate buying an item by inserting a User for yourself and an Order for that User.
- `INSERT INTO users VALUES (null, 'Jason', 'Lestina', 'me@gmail.com');`
- `INSERT INTO orders VALUES (null, 51, 19, 19, '2016-07-11 15:30:30.324325');`
---

#Adventure Mode

What item was ordered most often? Grossed the most money?

---

What user spent the most?

---

What were the top 3 highest grossing categories?
