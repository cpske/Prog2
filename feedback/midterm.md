---
title: Feedback on Midterm Exam
---

## Scoring of Part 1

Problems 1-3 were tested using unit tests. Problem 4 was evaluated by inspecting the output. Problem 5 evaluated by running your tests and inspecting the test code.

1. **LineItem** (6 tests)
   - `product` is a read-only property that returns the Product. You cannot set the Product (`lineitem.product = something` fails).
   - `quantity` is a read-write property that gets/sets the quantity
   - `get_price()` returns correct price
   - `__eq__` is true only if two line items have same product & quantity
   - `__eq__` is false if the argument is not a lineitem
   - `__str__` returns product description

2. **Sale** (6 tests)
   - `add_item` updates sale correctly for a product not already in the Sale. Test this using `sale.get_total()` after adding items.
   - `add_item` for a product already in the sale updates the quantity of that item, and sale total is correct
   - `remove_item` removes requested quantity of a product from the sale
   - `remove_item` raises ValueError if you try to remove something not in the sale or remove a quantity that exceeds quantity of item in Sale.
   - Sale is iterable. `iter(sale)` is an iterator over LineItems.  Not an iterator over (key,value) pairs for a dict used by Sale.
   - test that Sale creates a TwoForOneItem if product\_id is a product that is on sale.  Sale should call `store.is_sale_item(id)` and not directly acccess `Store.SALE_ITEMS`.

3. **TwoForOneItem** (2 tests)
   - `get_price` is correct for a quantity of 1, 2, 3, 4, 10, 11, 54, and 55.
   - `__str__` is correct. Appends " (2-for-1)" if quantity is more than 1.
   - Common Error:
     - No space between description and suffix: "Banana(2-for-1)". No deduction for this, but you should test your own code for details. In English there is always a space before left-parenthesis at word boundaries (like this).

4. **print\_sale** (2 points)
   - graded by running main and viewing the output.
   - 1 point: displays a list of product id, description, quantity, and LineItem prices
   - 1 point: the output is neatly formatted in columns, as stated on exam sheet

5. **Unit Tests of Sale** (5 points)
   - verify that your tests actually test the 5 things specified on exam sheet
   - I ran the tests using your Sale class and a reference Sale class where all methods work correctly. If your tests access some attribute of Sale, I added an attribute to the reference code that provides what you need (such as a list or dictionary of Lineitems).
   - no point for tests of LineItem instead of Sale.
   - **Common Error: wrong filename**. This is a test of the Sale class so the filename should be `test_sale.py` or `sale_test.py`. These names are incorrect:
     ```
     test_lineitem.py  - its not a test of LineItem
     unittest.py       
     test.py
     unit test.py      - never use a space in source code filenames
     ```



## Scoring of Part 2 (BMI Calculator UI)
