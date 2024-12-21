
inventory = {}

def display_inventory():
    if not inventory:
        print("Inventory is empty.")
    else:
        print("\nCurrent Inventory:")
        for item, quantity in inventory.items():
            print(f"{item}: {quantity}")
    print()

def add_item():
    item = input("Enter the item name: ").strip()
    quantity = int(input("Enter the quantity: ").strip())
    
    if item in inventory:
        inventory[item] += quantity
    else:
        inventory[item] = quantity
    print(f"{quantity} {item}(s) added to inventory.\n")

def remove_item():
    item = input("Enter the item name to remove: ").strip()
    
    if item in inventory:
        quantity = int(input(f"Enter the quantity of {item} to remove: ").strip())
        if quantity <= inventory[item]:
            inventory[item] -= quantity
            if inventory[item] == 0:
                del inventory[item]
            print(f"{quantity} {item}(s) removed from inventory.\n")
        else:
            print(f"Not enough {item} in stock.\n")
    else:
        print(f"{item} not found in inventory.\n")

def check_item():
    item = input("Enter the item name to check: ").strip()
    if item in inventory:
        print(f"{item}: {inventory[item]} in stock.\n")
    else:
        print(f"{item} not found in inventory.\n")

def update_quantity():
    item = input("Enter the item name to update: ").strip()
    if item in inventory:
        quantity = int(input(f"Enter the new quantity for {item}: ").strip())
        inventory[item] = quantity
        print(f"{item} quantity updated to {quantity}.\n")
    else:
        print(f"{item} not found in inventory.\n")

def menu():
    while True:
        print("Inventory Tracker Menu:")
        print("1. Display Inventory")
        print("2. Add Item")
        print("3. Remove Item")
        print("4. Check Item")
        print("5. Update Item Quantity")
        print("6. Exit")
        
        choice = input("Choose an option (1-6): ").strip()
        
        if choice == "1":
            display_inventory()
        elif choice == "2":
            add_item()
        elif choice == "3":
            remove_item()
        elif choice == "4":
            check_item()
        elif choice == "5":
            update_quantity()
        elif choice == "6":
            print(("Exiting the program. Goodbye!"))
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 6.\n")

if __name__ == "__main__":
 menu()
