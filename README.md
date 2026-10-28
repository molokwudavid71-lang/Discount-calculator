# Discount-calculator

A Python project that calculates the best price for a product using the **Strategy design pattern**. Different discount strategies are applied to a product, and the engine picks the lowest price.

## Features

- **`Product` class** that stores a product's name and price
- **`DiscountStrategy` abstract base class** (using `ABC` and `@abstractmethod`) that defines the interface every discount must follow:
  - `is_applicable(product, user_tier)` checks whether the discount can be used
  - `apply_discount(product)` returns the discounted price
- **Discount strategies**
  - `PercentageDiscount` takes a percentage off the price
  - `FixedAmountDiscount` subtracts a fixed amount from the price
  - `PremiumUserDiscount` gives Premium users 20% off
- **`DiscountEngine` class** that takes a list of strategies, applies every applicable one, and returns the lowest price

## Concepts Practised

- Abstract classes and abstract methods
- The Strategy design pattern
- Inheritance and polymorphism
- Type hints (`-> float`, `list[DiscountStrategy]`)
- Instantiating classes and calling methods
- List building and the `min()` function
- The `if __name__ == '__main__':` entry point

## Usage

1. Save the code as `discount_calculator.py`.
2. Run it from your terminal:

   ```bash
   python discount_calculator.py
   ```

3. The script creates a product, a user tier, and a list of discount strategies. The engine then prints the best price.

Example from the script:

```python
product = Product('Wireless Mouse', 50.0)
user_tier = 'Premium'

strategies = [
    PercentageDiscount(10),
    FixedAmountDiscount(5),
    PremiumUserDiscount()
]

engine = DiscountEngine(strategies)
best_price = engine.calculate_best_price(product, user_tier)
print(f'Best price for {product.name} for {user_tier} user: ${best_price:.2f}')
```

Output:

```
Best price for Wireless Mouse for Premium user: $40.00
```

Here the 10% discount gives $45.00, the $5 discount gives $45.00, and the Premium discount gives $40.00, so $40.00 wins.

To add a new discount, create a class that inherits from `DiscountStrategy`, implement both methods, and add it to the `strategies` list.

## Requirements

- Python 3.9 or later
- No external libraries

## Acknowledgements

This project was built as part of the [freeCodeCamp](https://www.freecodecamp.org/) Python certification. Thank you to freeCodeCamp for providing free, high-quality coding education. The project brief comes from freeCodeCamp's curriculum, and the solution was written by me while working through the course.
