class Product:
    def __init__(self, name, price):
        self.name = name
        self.price = price


class Cart:
    def __init__(self):
        self.items = []

    def add(self, product):
        self.items.append(product)
        print(product.name + " was added to the cart.")

    def remove(self, product_name):
        found = False
        for p in self.items:
            if p.name.lower() == product_name.lower():
                self.items.remove(p)
                print(product_name + " removed from cart.")
                found = True
                break
        if not found:
            print("Item not found.")

    def show_cart(self):
        if len(self.items) == 0:
            print("Cart is empty.")
        else:
            print("\nItems in your cart:")
            total = 0
            for p in self.items:
                print(p.name, "- ₱", p.price)
                total += p.price
            print("Total price: ₱", total)

    def checkout(self):
        if len(self.items) == 0:
            print("Nothing to checkout.")
        else:
            total = 0
            for p in self.items:
                total += p.price
            print("\nChecking out...")
            print("Total amount to pay: ₱", total)
            print("Thank you for shopping!")
            self.items.clear()


# main program
mycart = Cart()

while True:
    print("\n===== Shopping Cart Simulator =====")
    print("1 - Add Item")
    print("2 - Remove Item")
    print("3 - View Cart")
    print("4 - Checkout")
    print("5 - Exit")

    choice = input("Choose option: ")

    if choice == "1":
        item_name = input("Enter item name: ")
        item_price = float(input("Enter price: "))
        new_product = Product(item_name, item_price)
        mycart.add(new_product)

    elif choice == "2":
        item_name = input("Item to remove: ")
        mycart.remove(item_name)

    elif choice == "3":
        mycart.show_cart()

    elif choice == "4":
        mycart.checkout()

    elif choice == "5":
        print("Program ended.")
        break

    else:
        print("Invalid input, try again.")
