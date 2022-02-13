---
title: Feedback on quiz1
---

## FoodDiary

If the constructor doesn't work, then all the tests fail, so you got no credit. Sorry.

```python
class FoodDiary(Food):     # Error: FoodDiary is not a Food

    def __init__(self, name, weight, calories, carbs): # Error: too many parameters
        super().__init__(name, weight, calories, carbs)
        self.foods = {}
```


## Scoring of Unit Tests

* 1 point for a good, complete test
* 0.5 for incomplete test such as this (must test cases where == is True and where == is False):
  ```python
  def test_equals(self):
      food1 = Food("Tofu", 100, 110, 4)
      food2 = Food("Rice", 200, 180, 16)
      self.assertNotEqual(food1, food2)
  ```
* 0.5 for using inappropriate assert:
  ```python
  def test_equals(self):
      food1 = Food("Tofu", 100, 110, 4)
      food2 = Food("Rice", 200, 180, 16)
      # if assert fails, you don't get any useful info
      self.assertFalse(food1 == food2)
  ```
  Even **worse**:
  ```python
      self.assertEqual(False, food1 == food2)
  ```
  Even **worse than that**:
  ```python
      eq = (food1 == food2)
      self.assertEqual(False, eq)
  ```
* 0.5 testing result using strings instead of directly testing attributes
  ```python
  def test_equals(self):
      food1 = Food("Tofu", 100, 110, 4)
      food2 = Food("Tofu", 200, 190, 6)
      # don't use built-in functions as variable names
      sum   = food1 + food2
      # don't compare via str.  Directly test the attributes or use ==
      self.assertEqual("Tofu (300g)", str(sum))
  ```

## Poor Test Structure

Test fixtures should be defined in `setUp`, not as global variables.

```python
food1 = Food('Eggs', 10, 100, 1)
food2 = Food('Eggs', 10, 100, 1)
food3 = Food('Eggs', 20, 200, 5)


class TestFood(unittest.TestCase):

    def test_equals(self): 
        self.assertEqual(food1, food2)
        self.assertNotEqual(food1, food3)
```

Should be:

```python
class TestFood(unittest.TestCase):

    def setUp(self):
        """Create test fixures."""
        self.food1 = Food('Eggs', 10, 100, 1)
        self.food2 = Food('Eggs', 10, 100, 1)
        self.food3 = Food('Eggs', 20, 200, 5)

    def test_equals(self): 
        self.assertEqual(self.food1, self.food2)
```
